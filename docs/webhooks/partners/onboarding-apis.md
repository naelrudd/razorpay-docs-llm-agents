> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Onboarding APIs Webhook Events

> List of the webhook events the Razorpay Onboarding APIs send about sub-merchant accounts, along with sample payloads.

Available in
🇮🇳 India

The **Onboarding APIs** let partner platforms create and manage sub-merchant accounts. These webhook events tell your server when something changes on an account, so you do not need to poll. Subscribe to them on the Partner Dashboard, once for each mode. Know more about the [Onboarding APIs](https://razorpay.com/docs/partners/aggregators/onboarding-api).

> [!WARNING]
>
> **Watch Out!**
>
> Razorpay delivers webhooks asynchronously, and an event can arrive more than once or out of order. Fetching the account stays the source of truth. If a flow needs the current state and the event has not arrived, [fetch the account](https://razorpay.com/docs/api/partners/accounts/fetch.md). Know more about [validating webhooks](https://razorpay.com/docs/webhooks/validate-test.md).

## List of Onboarding APIs Webhook Events

The table below lists the webhook events available for the Onboarding APIs:

| Webhook Event | Description |
| - | - |
| `account.product.under_review` | A product was submitted, its video KYC call finished or it was resubmitted after a clarification. |
| `account.product.edd_pending` | A submitted product needs a video KYC call first. |
| `account.product.needs_clarification` | A reviewer asked for clarification. |
| `account.product.activated` | A product went live. |
| `account.product.rejected` | A product was rejected. Its `status_reason` says why. |
| `account.product.suspended` | An activated product was suspended, for example after a failed yearly website check. Its `status_reason` says why. |
| `account.requirements.updated` | A product's requirements changed without a call from you, for example after an asynchronous verification. |
| `account.consent.withdrawn` | The sub-merchant withdrew your platform's access through Razorpay. Every later call on the account returns `403`. |

## Sample Payloads

Each event carries what changed, not the whole account. `payload.account` has the account's `id` and `updated_at`, plus each part that changed. A product event carries the complete product, with its `status` and `requirements`.

### Account Product Under Review

Razorpay sends `account.product.under_review` when the update that accepts the terms of service submits a product, or when `submit_clarification` resubmits it after a clarification. It also fires when the product's video KYC call finishes. The KYC details stay locked from submission on. Changing one returns `409 field_locked`. Tell the sub-merchant that Razorpay is reviewing their details. Nothing is due from them. Most products skip this state and go straight to `account.product.activated`.

```json account.product.under_review theme={null}
{
  "id": "evt_Ru7Np3Xc8LqW2m",
  "entity": "event",
  "event": "account.product.under_review",
  "mode": "live",
  "account_id": "acc_TcdGEzmfKQzEl1",
  "product": "payment_gateway",
  "payload": {
    "account": {
      "id": "acc_TcdGEzmfKQzEl1",
      "products": {
        "payment_gateway": {
          "type": "payment_gateway",
          "status": "under_review",
          "status_reason": null,
          "created_at": 1792433135,
          "updated_at": 1792495200,
          "requirements": [],
          "terms_of_service_acceptance": {
            "ip": "203.0.113.42",
            "device_fingerprint_id": "df_9Hq4Lt2Vb5Ks8Zp",
            "metadata": {},
            "accepted_at": 1792435100
          },
          "payment_channels": {
            "website": {
              "primary": "https://www.example.com",
              "additional": [],
              "verification": {
                "status": "verified",
                "error_code": null,
                "error_description": null,
                "verified_at": 1792433250,
                "metadata": {},
                "created_at": 1792433220
              }
            },
            "app_android": null,
            "app_ios": null
          },
          "clarification_responses": {}
        }
      },
      "updated_at": 1792495200
    }
  },
  "created_at": 1792495201
}
```

### Account Product EDD Pending

Razorpay sends `account.product.edd_pending` when it needs enhanced due diligence (EDD) after submission before it can activate the product. This usually happens because the sub-merchant has no Central KYC Records Registry (CKYC) record. The product's `requirements` hold one item, `create_video_kyc_link`, an action. Run it and show the sub-merchant the link. Know more about [video KYC](https://razorpay.com/docs/partners/aggregators/onboarding-api/verification-actions.md#4-3-complete-video-kyc).

```json account.product.edd_pending theme={null}
{
  "id": "evt_Qe2Hn7Vb4KsW9p",
  "entity": "event",
  "event": "account.product.edd_pending",
  "mode": "live",
  "account_id": "acc_TcdGEzmfKQzEl1",
  "product": "payment_gateway",
  "payload": {
    "account": {
      "id": "acc_TcdGEzmfKQzEl1",
      "products": {
        "payment_gateway": {
          "type": "payment_gateway",
          "status": "edd_pending",
          "status_reason": null,
          "created_at": 1792433135,
          "updated_at": 1792435105,
          "requirements": [
            {
              "id": "req_bmOw79SOmj6jEj",
              "requirement_code": "create_video_kyc_link",
              "requirement_level": "mandatory",
              "requirement_type": "action",
              "description": "Complete a short video call with a Razorpay agent to verify your identity and address. Keep your PAN card on hand.",
              "status": "created"
            }
          ],
          "terms_of_service_acceptance": {
            "ip": "203.0.113.42",
            "device_fingerprint_id": "df_9Hq4Lt2Vb5Ks8Zp",
            "metadata": {},
            "accepted_at": 1792435100
          },
          "payment_channels": {
            "website": {
              "primary": "https://www.example.com",
              "additional": [],
              "verification": {
                "status": "verified",
                "error_code": null,
                "error_description": null,
                "verified_at": 1792433250,
                "metadata": {},
                "created_at": 1792433220
              }
            },
            "app_android": null,
            "app_ios": null
          },
          "clarification_responses": {}
        }
      },
      "updated_at": 1792435105
    }
  },
  "created_at": 1792435106
}
```

### Account Product Needs Clarification

Razorpay sends `account.product.needs_clarification` when a reviewer needs more information before the product can be activated. The product's `requirements` list only the flagged points. Each is usually a `composite` requirement with `fulfillment_criteria: one_of`, with the reviewer's reason in its `requirement_reason`. Show them to the sub-merchant and send the answers with an update. Once every flagged point is answered, send `products.<product_type>.submit_clarification: true` in its own call. Know more about [clarifications](https://razorpay.com/docs/partners/aggregators/onboarding-api/needs-clarification.md).

```json account.product.needs_clarification theme={null}
{
  "id": "evt_Wc5Hk2Tq9ZrB4n",
  "entity": "event",
  "event": "account.product.needs_clarification",
  "mode": "live",
  "account_id": "acc_TcdGEzmfKQzEl1",
  "product": "payment_gateway",
  "payload": {
    "account": {
      "id": "acc_TcdGEzmfKQzEl1",
      "products": {
        "payment_gateway": {
          "type": "payment_gateway",
          "status": "needs_clarification",
          "status_reason": null,
          "created_at": 1792433135,
          "updated_at": 1792565490,
          "requirements": [
            {
              "id": "req_4Z9yuuKZQXabvX",
              "requirement_code": "bank_account",
              "requirement_level": "mandatory",
              "requirement_type": "composite",
              "description": "Your settlement bank account.",
              "requirement_reason": "A reviewer couldn't confirm that the payout account is held in your name. Share an account in your name, pay ₹1 from it, or reply.",
              "fulfillment_criteria": "one_of",
              "sub_requirements": [
                {
                  "id": "req_VgRHb7QJNtMyj2",
                  "requirement_code": "settlement_bank_account",
                  "requirement_level": "conditional",
                  "requirement_type": "composite",
                  "description": "The bank account that receives settlements, in the name on your PAN.",
                  "fulfillment_criteria": "all_of",
                  "sub_requirements": [
                    {
                      "id": "req_4rY5OIDnOHtA2z",
                      "requirement_code": "bank_account_number",
                      "requirement_level": "mandatory",
                      "requirement_type": "input",
                      "description": "The account number.",
                      "field_path": "bank_accounts.settlements_primary.account_number",
                      "value_type": "text",
                      "status": "created"
                    },
                    {
                      "id": "req_mOTextgE1uJfFK",
                      "requirement_code": "bank_routing_code",
                      "requirement_level": "mandatory",
                      "requirement_type": "input",
                      "description": "The bank's IFSC.",
                      "field_path": "bank_accounts.settlements_primary.routing_code",
                      "value_type": "text",
                      "status": "created"
                    },
                    {
                      "id": "req_GNDdQcckulAU4g",
                      "requirement_code": "bank_routing_code_type",
                      "requirement_level": "mandatory",
                      "requirement_type": "input",
                      "description": "The kind of routing code.",
                      "field_path": "bank_accounts.settlements_primary.routing_code_type",
                      "value_type": "enum",
                      "options": [
                        {
                          "label": "IFSC",
                          "value": "IFSC"
                        }
                      ],
                      "status": "created"
                    }
                  ],
                  "status": "created"
                },
                {
                  "id": "req_8mFTjW5RY4heOw",
                  "requirement_code": "create_upi_link",
                  "requirement_level": "conditional",
                  "requirement_type": "action",
                  "description": "Or verify the account with a ₹1 UPI payment from it, refunded at once.",
                  "status": "created"
                },
                {
                  "id": "req_tRydtFXps2ERyP",
                  "requirement_code": "clarify_bank_account",
                  "requirement_level": "conditional",
                  "requirement_type": "input",
                  "description": "Or reply with a comment if the account is yours.",
                  "field_path": "products.payment_gateway.clarification_responses.bank_accounts.settlements_primary",
                  "value_type": "text",
                  "status": "created"
                }
              ],
              "status": "created"
            }
          ],
          "terms_of_service_acceptance": {
            "ip": "203.0.113.42",
            "device_fingerprint_id": "df_9Hq4Lt2Vb5Ks8Zp",
            "metadata": {},
            "accepted_at": 1792435100
          },
          "payment_channels": {
            "website": {
              "primary": "https://www.example.com",
              "additional": [],
              "verification": {
                "status": "verified",
                "error_code": null,
                "error_description": null,
                "verified_at": 1792433250,
                "metadata": {},
                "created_at": 1792433220
              }
            },
            "app_android": null,
            "app_ios": null
          },
          "clarification_responses": {}
        }
      },
      "updated_at": 1792565490
    }
  },
  "created_at": 1792565491
}
```

### Account Product Activated

Razorpay sends `account.product.activated` when the product is live and the account takes payments. From then on, the KYC details are locked. A few details can still change after a manual review. Know more about [account management](https://razorpay.com/docs/partners/aggregators/onboarding-api/account-management.md).

```json account.product.activated theme={null}
{
  "id": "evt_Kq3Lm8Zp2RtV1x",
  "entity": "event",
  "event": "account.product.activated",
  "mode": "live",
  "account_id": "acc_TcdGEzmfKQzEl1",
  "product": "payment_gateway",
  "payload": {
    "account": {
      "id": "acc_TcdGEzmfKQzEl1",
      "products": {
        "payment_gateway": {
          "type": "payment_gateway",
          "status": "activated",
          "status_reason": null,
          "created_at": 1792433135,
          "updated_at": 1792435105,
          "requirements": [],
          "terms_of_service_acceptance": {
            "ip": "203.0.113.42",
            "device_fingerprint_id": "df_9Hq4Lt2Vb5Ks8Zp",
            "metadata": {},
            "accepted_at": 1792435100
          },
          "payment_channels": {
            "website": {
              "primary": "https://www.example.com",
              "additional": [],
              "verification": {
                "status": "verified",
                "error_code": null,
                "error_description": null,
                "verified_at": 1792433250,
                "metadata": {},
                "created_at": 1792433220
              }
            },
            "app_android": null,
            "app_ios": null
          },
          "clarification_responses": {}
        }
      },
      "updated_at": 1792435105
    }
  },
  "created_at": 1792435106
}
```

### Account Product Rejected

Razorpay sends `account.product.rejected` when it turns the product down. The product's `status_reason` says why. The product accepts no further changes. To try again, the sub-merchant starts a new account.

```json account.product.rejected theme={null}
{
  "id": "evt_Pz8Lm1Vd4KsX6c",
  "entity": "event",
  "event": "account.product.rejected",
  "mode": "live",
  "account_id": "acc_TcdGEzmfKQzEl1",
  "product": "payment_gateway",
  "payload": {
    "account": {
      "id": "acc_TcdGEzmfKQzEl1",
      "products": {
        "payment_gateway": {
          "type": "payment_gateway",
          "status": "rejected",
          "status_reason": {
            "code": "clarification_not_answered",
            "description": "We didn't get answers to the review's questions in time, so we couldn't approve this application. Start a new application to try again."
          },
          "created_at": 1792433135,
          "updated_at": 1793170200,
          "requirements": [],
          "terms_of_service_acceptance": {
            "ip": "203.0.113.42",
            "device_fingerprint_id": "df_9Hq4Lt2Vb5Ks8Zp",
            "metadata": {},
            "accepted_at": 1792435100
          },
          "payment_channels": {
            "website": {
              "primary": "https://www.example.com",
              "additional": [],
              "verification": {
                "status": "verified",
                "error_code": null,
                "error_description": null,
                "verified_at": 1792433250,
                "metadata": {},
                "created_at": 1792433220
              }
            },
            "app_android": null,
            "app_ios": null
          },
          "clarification_responses": {}
        }
      },
      "updated_at": 1793170200
    }
  },
  "created_at": 1793170201
}
```

### Account Product Suspended

Razorpay sends `account.product.suspended` when it suspends an activated product, for example when the yearly website check fails and the sub-merchant does not resolve it. Payments stop until the sub-merchant resolves it. The product's `status_reason` says why, and what would resolve it is in its `requirements`. Answer them like any other requirement.

```json account.product.suspended theme={null}
{
  "id": "evt_Hb4Qs7Rn2YtM9k",
  "entity": "event",
  "event": "account.product.suspended",
  "mode": "live",
  "account_id": "acc_TcdGEzmfKQzEl1",
  "product": "payment_gateway",
  "payload": {
    "account": {
      "id": "acc_TcdGEzmfKQzEl1",
      "products": {
        "payment_gateway": {
          "type": "payment_gateway",
          "status": "suspended",
          "status_reason": {
            "code": "website_review_failed",
            "description": "Your website didn't pass the yearly check. Fix what's listed to start taking payments again."
          },
          "created_at": 1792433135,
          "updated_at": 1823971200,
          "requirements": [
            {
              "id": "req_N0fo3L9LVzHpZQ",
              "requirement_code": "website_url",
              "requirement_level": "mandatory",
              "requirement_type": "input",
              "description": "Your website's address.",
              "requirement_reason": "Your website did not pass the yearly check.",
              "field_path": "products.payment_gateway.payment_channels.website.primary",
              "value_type": "text",
              "status": "created"
            }
          ],
          "terms_of_service_acceptance": {
            "ip": "203.0.113.42",
            "device_fingerprint_id": "df_9Hq4Lt2Vb5Ks8Zp",
            "metadata": {},
            "accepted_at": 1792435100
          },
          "payment_channels": {
            "website": {
              "primary": "https://www.example.com",
              "additional": [],
              "verification": {
                "status": "rejected",
                "error_code": "website_unreachable",
                "error_description": "We couldn't open your website. Check that it's live, or share another one.",
                "verified_at": null,
                "metadata": {},
                "created_at": 1823970600
              }
            },
            "app_android": null,
            "app_ios": null
          },
          "clarification_responses": {}
        }
      },
      "updated_at": 1823971200
    }
  },
  "created_at": 1823971201
}
```

### Account Requirements Updated

Razorpay sends `account.requirements.updated` when a product's `requirements` change without a call from you. For example:

```json account.requirements.updated theme={null}
{
  "id": "evt_Ld6Zx3Cv8NpQ1r",
  "entity": "event",
  "event": "account.requirements.updated",
  "mode": "live",
  "account_id": "acc_TcdGEzmfKQzEl1",
  "product": "payment_gateway",
  "payload": {
    "account": {
      "id": "acc_TcdGEzmfKQzEl1",
      "bank_accounts": {
        "settlements_primary": {
          "type": "settlements_primary",
          "account_number": "001234567890",
          "routing_code": "ICIC0000009",
          "routing_code_type": "IFSC",
          "supporting_document": null,
          "verification": {
            "status": "verified",
            "error_code": null,
            "error_description": null,
            "verified_at": 1792435025,
            "metadata": {},
            "created_at": 1792435011
          }
        }
      },
      "products": {
        "payment_gateway": {
          "type": "payment_gateway",
          "status": "in_progress",
          "status_reason": null,
          "created_at": 1792433135,
          "updated_at": 1792435025,
          "requirements": [
            {
              "id": "req_7zAE2YmS5MDUhG",
              "requirement_code": "business_category",
              "requirement_level": "mandatory",
              "requirement_type": "input",
              "description": "Select your business category, and send its subcategory with it.",
              "field_path": "business_profile.business_category.category",
              "value_type": "enum",
              "options": [
                {
                  "label": "Ecommerce",
                  "value": "ecommerce"
                },
                {
                  "label": "Food and beverage",
                  "value": "food"
                }
              ],
              "status": "created"
            },
            {
              "id": "req_0HAQYzBrDRNnEM",
              "requirement_code": "accept_terms_of_service",
              "requirement_level": "mandatory",
              "requirement_type": "composite",
              "description": "Show the sub-merchant Razorpay's terms of service and record their acceptance.",
              "fulfillment_criteria": "all_of",
              "sub_requirements": [
                {
                  "id": "req_CTW6xxsQmygIDU",
                  "requirement_code": "acceptance_ip",
                  "requirement_level": "mandatory",
                  "requirement_type": "input",
                  "description": "The IP address the terms were accepted from.",
                  "field_path": "products.payment_gateway.terms_of_service_acceptance.ip",
                  "value_type": "text",
                  "status": "created"
                },
                {
                  "id": "req_gXg6igx2STKrZA",
                  "requirement_code": "acceptance_device_fingerprint_id",
                  "requirement_level": "mandatory",
                  "requirement_type": "input",
                  "description": "The device fingerprint of the device the terms were accepted on.",
                  "field_path": "products.payment_gateway.terms_of_service_acceptance.device_fingerprint_id",
                  "value_type": "text",
                  "status": "created"
                }
              ],
              "status": "created"
            }
          ],
          "terms_of_service_acceptance": null,
          "payment_channels": {
            "website": {
              "primary": "https://www.example.com",
              "additional": [],
              "verification": {
                "status": "verified",
                "error_code": null,
                "error_description": null,
                "verified_at": 1792433250,
                "metadata": {},
                "created_at": 1792433220
              }
            },
            "app_android": null,
            "app_ios": null
          },
          "clarification_responses": {}
        }
      },
      "updated_at": 1792435025
    }
  },
  "created_at": 1792435026
}
```

### Account Consent Withdrawn

Razorpay sends `account.consent.withdrawn` when the sub-merchant withdraws, through Razorpay, your permission to act on its account, or asks Razorpay to delete its data. From then on, every call you make on the account returns `403 consent_withdrawn`. Stop acting on the account and delete what you still hold about it. The payload carries only the account's `id` and `updated_at`. `product` is `null`.

```json account.consent.withdrawn theme={null}
{
  "id": "evt_Mk8Rt3Zq1VnB6c",
  "entity": "event",
  "event": "account.consent.withdrawn",
  "mode": "live",
  "account_id": "acc_TcdGEzmfKQzEl1",
  "product": null,
  "payload": {
    "account": {
      "id": "acc_TcdGEzmfKQzEl1",
      "updated_at": 1801209600
    }
  },
  "created_at": 1801209601
}
```
