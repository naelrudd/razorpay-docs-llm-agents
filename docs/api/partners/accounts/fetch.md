> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Accounts

> Fetch all sub-merchant accounts, or one account with its ID, using Razorpay Accounts API.

Available in
🇮🇳 India

Use this endpoint to fetch the accounts mapped to your app, newest first. Add an account ID to the path to fetch only that account, with its requirements and the status of each element and product.

> [!NOTE]
>
> **Handy Tips**
>
> * Authenticate with the key and secret of your test pair or live pair. In the API playground, enter the test key as the username and its secret as the password. Use the live pair in live mode.
> * With an `account_id`, the response is that account. Without one, the response is a list.
> * Filter the list by `email` or `phone` to find the owner's existing accounts, including ones not activated yet or only partly filled in. Let the sub-merchant continue one of them or create a new account.
> * Accounts on other platforms never appear. Neither do accounts held with Razorpay directly.
> * An email or phone with no account is not an error. The response returns `count` as `0`.
> * Razorpay computes the requirements on every call. A `GET` never sends a One-Time Password (OTP), creates a link or changes state.
> * Identifiers come back in full, each with its `verification`. Documents come back with their `url`.
> * Razorpay does not return the addresses it fills from a registry or the bank's name for the account holder. The name on the PAN comes back as `business_name`. Documents Razorpay fetches from a registry come back in `documents`.

```bash Fetch One theme={null}
curl -X GET https://api.razorpay.com/v1/accounts/acc_TcdGEzmfKQzEl1 \
-u rzp_test_partner_[CLIENT_ID]:[CLIENT_SECRET]
```

```bash Fetch All theme={null}
curl -X GET "https://api.razorpay.com/v1/accounts?email=gaurav.kumar@example.com" \
-u rzp_test_partner_[CLIENT_ID]:[CLIENT_SECRET]
```

```json Fetch One theme={null}
{
  "id": "acc_TcdGEzmfKQzEl1",
  "country": "IN",
  "statement_descriptor": {
    "value": "Acme Corp",
    "verification": {
      "status": "verified",
      "verified_at": 1792433135
    }
  },
  "is_mfa_enabled": false,
  "user": {
    "role": "owner",
    "email": "gaurav.kumar@example.com",
    "phone": "+919611752201",
    "name": "Gaurav Kumar",
    "is_email_verified": true,
    "is_phone_verified": true
  },
  "business_profile": {
    "business_type": "individual",
    "business_name": "GAURAV KUMAR",
    "date_of_establishment": null,
    "identity_numbers": {},
    "documents": {},
    "business_category": null,
    "authorized_person": {
      "name": "GAURAV KUMAR",
      "identity_numbers": {
        "individual_pan": {
          "type": "individual_pan",
          "value": "ABCPD1234A",
          "verification": {
            "status": "verified",
            "error_code": null,
            "error_description": null,
            "verified_at": 1792433290,
            "metadata": {},
            "created_at": 1792433290
          },
          "metadata": {},
          "is_skipped": false,
          "created_at": 1792433280,
          "updated_at": 1792433290
        },
        "individual_ckyc": {
          "type": "individual_ckyc",
          "value": null,
          "verification": {
            "status": "verified",
            "error_code": null,
            "error_description": null,
            "verified_at": 1792433340,
            "metadata": {},
            "created_at": 1792433340
          },
          "metadata": {
            "ckyc_mobile": "+919845098450"
          },
          "is_skipped": false,
          "created_at": 1792433340,
          "updated_at": 1792433340
        }
      },
      "documents": {
        "aadhaar_front": {
          "id": "file_Hx7Ui2kQe9Zf3A",
          "type": "aadhaar_front",
          "url": "https://files.razorpay.com/documents/file_Hx7Ui2kQe9Zf3A",
          "metadata": {
            "source": "ckyc",
            "file_name": "aadhaar-front.jpg",
            "mime_type": "image/jpeg",
            "size_bytes": 187342
          },
          "verification": {
            "status": "verified",
            "error_code": null,
            "error_description": null,
            "verified_at": 1792433340,
            "metadata": {},
            "created_at": 1792433340
          },
          "created_at": 1792433340
        }
      },
      "address": null,
      "date_of_birth": null,
      "additional_data": {},
      "created_at": 1792433280,
      "updated_at": 1792433340
    },
    "stakeholders": {},
    "addresses": [],
    "metadata": {}
  },
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
  "notes": {
    "shop_id": "60291847"
  },
  "created_at": 1792433135,
  "updated_at": 1792435025
}
```

```json Fetch All theme={null}
{
  "entity": "collection",
  "count": 1,
  "items": [
    {
      "id": "acc_TcdGEzmfKQzEl1",
      "country": "IN",
      "statement_descriptor": {
        "value": "Acme Corp",
        "verification": {
          "status": "verified",
          "verified_at": 1792433135
        }
      },
      "is_mfa_enabled": false,
      "user": {
        "role": "owner",
        "email": "gaurav.kumar@example.com",
        "phone": "+919611752201",
        "name": "Gaurav Kumar",
        "is_email_verified": true,
        "is_phone_verified": true
      },
      "business_profile": {
        "business_type": "individual",
        "business_name": "GAURAV KUMAR",
        "date_of_establishment": null,
        "identity_numbers": {},
        "documents": {},
        "business_category": null,
        "authorized_person": {
          "name": "GAURAV KUMAR",
          "identity_numbers": {
            "individual_pan": {
              "type": "individual_pan",
              "value": "ABCPD1234A",
              "verification": {
                "status": "verified",
                "error_code": null,
                "error_description": null,
                "verified_at": 1792433290,
                "metadata": {},
                "created_at": 1792433290
              },
              "metadata": {},
              "is_skipped": false,
              "created_at": 1792433280,
              "updated_at": 1792433290
            },
            "individual_ckyc": {
              "type": "individual_ckyc",
              "value": null,
              "verification": {
                "status": "verified",
                "error_code": null,
                "error_description": null,
                "verified_at": 1792433340,
                "metadata": {},
                "created_at": 1792433340
              },
              "metadata": {
                "ckyc_mobile": "+919845098450"
              },
              "is_skipped": false,
              "created_at": 1792433340,
              "updated_at": 1792433340
            }
          },
          "documents": {
            "aadhaar_front": {
              "id": "file_Hx7Ui2kQe9Zf3A",
              "type": "aadhaar_front",
              "url": "https://files.razorpay.com/documents/file_Hx7Ui2kQe9Zf3A",
              "metadata": {
                "source": "ckyc",
                "file_name": "aadhaar-front.jpg",
                "mime_type": "image/jpeg",
                "size_bytes": 187342
              },
              "verification": {
                "status": "verified",
                "error_code": null,
                "error_description": null,
                "verified_at": 1792433340,
                "metadata": {},
                "created_at": 1792433340
              },
              "created_at": 1792433340
            }
          },
          "address": null,
          "date_of_birth": null,
          "additional_data": {},
          "created_at": 1792433280,
          "updated_at": 1792433340
        },
        "stakeholders": {},
        "addresses": [],
        "metadata": {}
      },
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
      "notes": {
        "shop_id": "60291847"
      },
      "created_at": 1792433135,
      "updated_at": 1792435025
    }
  ]
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "The requested resource doesn't exist.",
    "source": "business",
    "step": null,
    "reason": "not_found",
    "field": "account_id",
    "metadata": {}
  }
}
```

## Path Parameters

Optional. Add the account ID to the path to fetch one account: `GET /v1/accounts/{account_id}`.

**account\_id** `string`

The unique identifier of the account, `acc_`-prefixed. For example, `acc_TcdGEzmfKQzEl1`. Send it to fetch only this account. Without it, the endpoint returns a list of accounts.

## Query Parameters

The query parameters filter the list and apply only when the path has no `account_id`. Every query parameter is optional. With none, the endpoint returns the accounts mapped to your app, 10 at a time.

**email** `string`

Return only the accounts with this user email.

**phone** `string`

Return only the accounts with this user phone, +91 followed by 10 digits. Pattern: `^\+91[0-9]{10}$`.

**product** `string`

Return only accounts holding this product. `payment_gateway` accepts payments on websites and apps. Possible values:

* `payment_gateway`
* `pos`
* `billing`
* `business_banking`
* `payroll`
* `agent_studio`
* `optimizer`

**from** `integer`

Return accounts created at or after this time, as Unix time, in seconds.

**to** `integer`

Return accounts created at or before this time, as Unix time, in seconds.

**count** `integer`

Number of accounts to return. Range: 1-100. Default: `10`.

**skip** `integer`

Number of accounts to skip. Minimum: 0. Default: `0`.

## Response Parameters

With an `account_id`, the response is the account. Without one, the response is a collection with these parameters:

**entity** `string`

Always `collection`.

**count** `integer`

Number of accounts in this page.

**items** `array`

The accounts, newest first.

Each account has the parameters below. Know more about the [Account entity](https://razorpay.com/docs/api/partners/accounts/entity.md).

**id** `string`

Unique identifier for the account, `acc_`-prefixed.

**country** `string`

ISO 3166-1 alpha-2 country of the business, `IN`.

**statement\_descriptor** `object`

The brand name customers see on their bank statements and receipts, with its verification.

**statement\_descriptor.value** `string`

The brand name customers see on their bank statements and receipts, so they recognise the charge. Up to 255 characters.

**statement\_descriptor.verification** `object`

The outcome of a verification check.

**statement\_descriptor.verification.status** `string`

Where the check is. Possible values:

* `in_progress`: The check is running.
* `deferred`: The check could not conclude, so a reviewer decides after the product is submitted. The requirement clears and `error_code` is `null`.
* `verified`: The check passed.
* `rejected`: The check failed. `error_code` says why.
* `collected`: Razorpay has received the value and has not checked it yet.

**statement\_descriptor.verification.error\_code** `string`

A stable code for the failure, such as `bank_name_mismatch`, `pan_not_found` or `otp_invalid`. Razorpay never returns the bank's or registry's own record, such as the account holder's name. The code says what did not match. Know more about [failed-check codes](https://razorpay.com/docs/api/partners/accounts/errors.md#failed-check-codes).

**statement\_descriptor.verification.error\_description** `string`

A sentence to show the sub-merchant. The wording can change. It never repeats the value sent.

**statement\_descriptor.verification.verified\_at** `integer`

Time at which the check passed, as a Unix timestamp in seconds.

**statement\_descriptor.verification.metadata** `object`

Details of the check, where it has any. `{}` when the check has none.

**statement\_descriptor.verification.created\_at** `integer`

Time at which the check started, as a Unix timestamp in seconds.

**statement\_descriptor.metadata** `object`

Details of the statement descriptor. `{}` when it has none.

**statement\_descriptor.created\_at** `integer`

Time at which the statement descriptor was added, as a Unix timestamp in seconds.

**statement\_descriptor.updated\_at** `integer`

Time at which the statement descriptor last changed, as a Unix timestamp in seconds.

**is\_mfa\_enabled** `boolean`

Whether the owner must complete 2-factor authentication on the Razorpay Dashboard.

**user** `object`

The user who creates and operates the account and signs in to the Razorpay Dashboard, returned with `role` as `owner`. This is the person behind the account, not the company's owner. The email and phone belong to the user, not the account. One user can own several accounts.

**user.role** `string`

The user's role on the account. The user who creates the account is its `owner`. Do not send it in a request. Possible values:

* `owner`
* `admin`

**user.email** `string`

The user's email. Maximum length: 255 characters.

**user.phone** `string`

The user's phone: +91 followed by 10 digits.

**user.name** `string`

The name of the person completing the onboarding. Length: 2-127 characters.

**user.is\_email\_verified** `boolean`

Whether the user has verified the email with an OTP. Razorpay sends no OTP to a verified email.

**user.is\_phone\_verified** `boolean`

Whether the user has verified the phone with an OTP. Razorpay sends no OTP to a verified phone.

**business\_profile** `object`

The business's KYC identity on this account.

**business\_profile.business\_type** `string`

The legal form of the business. It decides which requirements apply and cannot change after the PAN is verified. Possible values:

* `individual`: An individual without a registered business.
* `proprietorship`: A sole proprietorship.
* `private_limited`: A private limited company.
* `public_limited`: A public limited company.
* `section_8_company`: A not-for-profit company under Section 8 of the Companies Act.
* `llp`: A limited liability partnership.
* `partnership`: A partnership firm.
* `trust`: A trust.
* `society`: A registered society.
* `huf`: A Hindu undivided family.
* `government`: A government body or undertaking.
* `judicial_person`: An artificial judicial person, such as a university or a fund.
* `local_authority`: A local authority, such as a municipal corporation.

**business\_profile.business\_name** `string`

The legal name. For an individual, it comes from the verified PAN and cannot be set. A proprietorship sends the name it trades under.

**business\_profile.date\_of\_establishment** `string`

The date the business was established. Format: `YYYY-MM-DD`.

**business\_profile.identity\_numbers** `object`

Government identifiers keyed by type.

**business\_profile.identity\_numbers.\<type>** `object`

One identifier and its verification, keyed by its type.

**business\_profile.identity\_numbers.\<type>.type** `string`

The kind of identifier, the same as its key. Possible values:

* `individual_pan`: The PAN of a person: the authorised person, a stakeholder, an individual or a proprietor.
* `business_pan`: The PAN of the business.
* `gstin`: The Goods and Services Tax Identification Number (GSTIN). One per account: the GSTIN this account trades under. A business registered for GST in several states sends the GSTIN for this account. It sends that registration's address as `operational_address`.
* `udyam_registration`: Udyam registration number.
* `cin`: The Corporate Identification Number (CIN).
* `individual_ckyc`: The person's Central KYC Records Registry (CKYC) record. Its `value` is `null`. Send the code from `send_ckyc_otp` in `otp` and its request ID in `request_id`.

**business\_profile.identity\_numbers.\<type>.value** `string`

The identifier, as sent. `null` for `individual_ckyc`.

**business\_profile.identity\_numbers.\<type>.verification** `object`

The outcome of a verification check.

**business\_profile.identity\_numbers.\<type>.verification.status** `string`

Where the check is. Possible values:

* `in_progress`: The check is running.
* `deferred`: The check could not conclude, so a reviewer decides after the product is submitted. The requirement clears and `error_code` is `null`.
* `verified`: The check passed.
* `rejected`: The check failed. `error_code` says why.
* `collected`: Razorpay has received the value and has not checked it yet.

**business\_profile.identity\_numbers.\<type>.verification.error\_code** `string`

A stable code for the failure, such as `bank_name_mismatch`, `pan_not_found` or `otp_invalid`. Razorpay never returns the bank's or registry's own record, such as the account holder's name. The code says what did not match. Know more about [failed-check codes](https://razorpay.com/docs/api/partners/accounts/errors.md#failed-check-codes).

**business\_profile.identity\_numbers.\<type>.verification.error\_description** `string`

A sentence to show the sub-merchant. The wording can change. It never repeats the value sent.

**business\_profile.identity\_numbers.\<type>.verification.verified\_at** `integer`

Time at which the check passed, as a Unix timestamp in seconds.

**business\_profile.identity\_numbers.\<type>.verification.metadata** `object`

Details of the check, where it has any. `{}` when the check has none.

**business\_profile.identity\_numbers.\<type>.verification.created\_at** `integer`

Time at which the check started, as a Unix timestamp in seconds.

**business\_profile.identity\_numbers.\<type>.metadata** `object`

Details of the identifier. For `individual_ckyc`, it holds `ckyc_mobile`, the mobile on the CKYC record.

**business\_profile.identity\_numbers.\<type>.is\_skipped** `boolean`

Whether the sub-merchant chose to skip this identifier, such as the CKYC record.

**business\_profile.identity\_numbers.\<type>.created\_at** `integer`

Time at which the identifier was added, as a Unix timestamp in seconds.

**business\_profile.identity\_numbers.\<type>.updated\_at** `integer`

Time at which the identifier last changed, as a Unix timestamp in seconds.

**business\_profile.documents** `object`

The business's KYC documents, keyed by document type. Attach each document by its `id` or `url`.

**business\_profile.documents.\<document\_type>** `object`

One KYC document, keyed by its type. Know more about the [Document entity](https://razorpay.com/docs/api/partners/accounts/document-entity.md).

**business\_profile.business\_category** `object`

How the business is classified. Razorpay derives the Merchant Category Code (MCC) from the subcategory.

**business\_profile.business\_category.category** `string`

The business category, from the requirement's `options`.

**business\_profile.business\_category.subcategory** `string`

The subcategory of the category. Send it with `category`. Razorpay derives the `mcc` from it. Know more about [business categories and subcategories](https://razorpay.com/docs/api/partners/accounts/business-categories.md).

**business\_profile.business\_category.mcc** `string`

The MCC. Razorpay derives it from the subcategory when you send the category and subcategory.

**business\_profile.business\_category.business\_description** `string`

What the business sells, such as `Clothing and accessories for men, women and children, sold online`. Maximum length: 100 characters.

**business\_profile.business\_category.business\_model\_clarifications** `object`

Answers to the business-model questions, keyed by question ID. Know more about the [business model questions](https://razorpay.com/docs/api/partners/accounts/business-model-questions.md).

**business\_profile.business\_category.business\_model\_clarifications.\<question\_id>** `object`

One business-model question and its answer.

**business\_profile.business\_category.business\_model\_clarifications.\<question\_id>.question\_id** `string`

The question's ID, the same as its key.

**business\_profile.business\_category.business\_model\_clarifications.\<question\_id>.question** `string`

The question text.

**business\_profile.business\_category.business\_model\_clarifications.\<question\_id>.options** `array`

The allowed answers.

**business\_profile.business\_category.business\_model\_clarifications.\<question\_id>.options\[].label** `string`

The text to show.

**business\_profile.business\_category.business\_model\_clarifications.\<question\_id>.options\[].value** `string`

The value to send.

**business\_profile.business\_category.business\_model\_clarifications.\<question\_id>.bmc\_input\_type** `string`

How the question is answered. Possible values:

* `single_select`
* `multi_select`
* `free_text`

**business\_profile.business\_category.business\_model\_clarifications.\<question\_id>.answer** `array`

The answer. One value for single-select and text questions.

**business\_profile.authorized\_person** `object`

The person authorised to act for the business on this account. They need not hold a share of it. For an individual or a proprietor, this is the owner. Send the owner's personal PAN at `business_profile.authorized_person.identity_numbers.individual_pan`. The business name comes from that PAN.

**business\_profile.authorized\_person.name** `string`

The person's full name.

**business\_profile.authorized\_person.identity\_numbers** `object`

The person's identifiers keyed by type.

**business\_profile.authorized\_person.identity\_numbers.\<type>** `object`

One identifier and its verification, keyed by its type.

**business\_profile.authorized\_person.identity\_numbers.\<type>.type** `string`

The kind of identifier, the same as its key. Possible values:

* `individual_pan`: The PAN of a person: the authorised person, a stakeholder, an individual or a proprietor.
* `business_pan`: The PAN of the business.
* `gstin`: The GSTIN. One per account: the GSTIN this account trades under. A business registered for GST in several states sends the GSTIN for this account. It sends that registration's address as `operational_address`.
* `udyam_registration`: Udyam registration number.
* `cin`: The CIN.
* `individual_ckyc`: The person's CKYC record. Its `value` is `null`. Send the code from `send_ckyc_otp` in `otp` and its request ID in `request_id`.

**business\_profile.authorized\_person.identity\_numbers.\<type>.value** `string`

The identifier, as sent. `null` for `individual_ckyc`.

**business\_profile.authorized\_person.identity\_numbers.\<type>.verification** `object`

The outcome of a verification check.

**business\_profile.authorized\_person.identity\_numbers.\<type>.verification.status** `string`

Where the check is. Possible values:

* `in_progress`: The check is running.
* `deferred`: The check could not conclude, so a reviewer decides after the product is submitted. The requirement clears and `error_code` is `null`.
* `verified`: The check passed.
* `rejected`: The check failed. `error_code` says why.
* `collected`: Razorpay has received the value and has not checked it yet.

**business\_profile.authorized\_person.identity\_numbers.\<type>.verification.error\_code** `string`

A stable code for the failure, such as `bank_name_mismatch`, `pan_not_found` or `otp_invalid`. Razorpay never returns the bank's or registry's own record, such as the account holder's name. The code says what did not match. Know more about [failed-check codes](https://razorpay.com/docs/api/partners/accounts/errors.md#failed-check-codes).

**business\_profile.authorized\_person.identity\_numbers.\<type>.verification.error\_description** `string`

A sentence to show the sub-merchant. The wording can change. It never repeats the value sent.

**business\_profile.authorized\_person.identity\_numbers.\<type>.verification.verified\_at** `integer`

Time at which the check passed, as a Unix timestamp in seconds.

**business\_profile.authorized\_person.identity\_numbers.\<type>.verification.metadata** `object`

Details of the check, where it has any. `{}` when the check has none.

**business\_profile.authorized\_person.identity\_numbers.\<type>.verification.created\_at** `integer`

Time at which the check started, as a Unix timestamp in seconds.

**business\_profile.authorized\_person.identity\_numbers.\<type>.metadata** `object`

Details of the identifier. For `individual_ckyc`, it holds `ckyc_mobile`, the mobile on the CKYC record.

**business\_profile.authorized\_person.identity\_numbers.\<type>.is\_skipped** `boolean`

Whether the sub-merchant chose to skip this identifier, such as the CKYC record.

**business\_profile.authorized\_person.identity\_numbers.\<type>.created\_at** `integer`

Time at which the identifier was added, as a Unix timestamp in seconds.

**business\_profile.authorized\_person.identity\_numbers.\<type>.updated\_at** `integer`

Time at which the identifier last changed, as a Unix timestamp in seconds.

**business\_profile.authorized\_person.documents** `object`

The person's KYC documents keyed by document type.

**business\_profile.authorized\_person.documents.\<document\_type>** `object`

One KYC document, keyed by its type. Know more about the [Document entity](https://razorpay.com/docs/api/partners/accounts/document-entity.md).

**business\_profile.authorized\_person.address** `object`

The person's own address. It is `null` unless you sent it.

**business\_profile.authorized\_person.address.type** `string`

Which address this is, the same as its key. Possible values:

* `registered_address`: The registered business address. For an individual, Razorpay fills it from the CKYC record or the proof of address when you do not send it.
* `operational_address`: Where the business operates for this account. One per account. With a GSTIN, it is the place of business on that GST registration.

**business\_profile.authorized\_person.address.line1** `string`

First line of the address.

**business\_profile.authorized\_person.address.line2** `string`

Second line of the address.

**business\_profile.authorized\_person.address.city** `string`

City or district.

**business\_profile.authorized\_person.address.state** `string`

State, as an ISO 3166-2 subdivision code such as `KA`.

**business\_profile.authorized\_person.address.postal\_code** `string`

The 6-digit PIN code.

**business\_profile.authorized\_person.address.country** `string`

ISO 3166-1 alpha-2, for example `IN`.

**business\_profile.authorized\_person.date\_of\_birth** `string`

The person's date of birth. It is `null` unless you sent it. Format: `YYYY-MM-DD`.

**business\_profile.authorized\_person.additional\_data** `object`

Other attributes of the person, such as gender or title. `{}` when the person has none.

**business\_profile.authorized\_person.created\_at** `integer`

Time at which the person was added, as a Unix timestamp in seconds.

**business\_profile.authorized\_person.updated\_at** `integer`

Time at which the person last changed, as a Unix timestamp in seconds.

**business\_profile.stakeholders** `object`

The business's stakeholders, the people who hold a share of it, keyed by stakeholder ID. To add a stakeholder, use any new key.

**business\_profile.stakeholders.\<stakeholder\_id>** `object`

A stakeholder: a person who holds a share of the business.

**business\_profile.stakeholders.\<stakeholder\_id>.name** `string`

The person's full name.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers** `object`

The person's identifiers keyed by type.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>** `object`

One identifier and its verification, keyed by its type.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>.type** `string`

The kind of identifier, the same as its key. Possible values:

* `individual_pan`: The PAN of a person: the authorised person, a stakeholder, an individual or a proprietor.
* `business_pan`: The PAN of the business.
* `gstin`: The GSTIN. One per account: the GSTIN this account trades under. A business registered for GST in several states sends the GSTIN for this account. It sends that registration's address as `operational_address`.
* `udyam_registration`: Udyam registration number.
* `cin`: The CIN.
* `individual_ckyc`: The person's CKYC record. Its `value` is `null`. Send the code from `send_ckyc_otp` in `otp` and its request ID in `request_id`.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>.value** `string`

The identifier, as sent. `null` for `individual_ckyc`.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>.verification** `object`

The outcome of a verification check.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>.verification.status** `string`

Where the check is. Possible values:

* `in_progress`: The check is running.
* `deferred`: The check could not conclude, so a reviewer decides after the product is submitted. The requirement clears and `error_code` is `null`.
* `verified`: The check passed.
* `rejected`: The check failed. `error_code` says why.
* `collected`: Razorpay has received the value and has not checked it yet.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>.verification.error\_code** `string`

A stable code for the failure, such as `bank_name_mismatch`, `pan_not_found` or `otp_invalid`. Razorpay never returns the bank's or registry's own record, such as the account holder's name. The code says what did not match. Know more about [failed-check codes](https://razorpay.com/docs/api/partners/accounts/errors.md#failed-check-codes).

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>.verification.error\_description** `string`

A sentence to show the sub-merchant. The wording can change. It never repeats the value sent.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>.verification.verified\_at** `integer`

Time at which the check passed, as a Unix timestamp in seconds.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>.verification.metadata** `object`

Details of the check, where it has any. `{}` when the check has none.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>.verification.created\_at** `integer`

Time at which the check started, as a Unix timestamp in seconds.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>.metadata** `object`

Details of the identifier. For `individual_ckyc`, it holds `ckyc_mobile`, the mobile on the CKYC record.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>.is\_skipped** `boolean`

Whether the sub-merchant chose to skip this identifier, such as the CKYC record.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>.created\_at** `integer`

Time at which the identifier was added, as a Unix timestamp in seconds.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.\<type>.updated\_at** `integer`

Time at which the identifier last changed, as a Unix timestamp in seconds.

**business\_profile.stakeholders.\<stakeholder\_id>.documents** `object`

The person's KYC documents keyed by document type.

**business\_profile.stakeholders.\<stakeholder\_id>.documents.\<document\_type>** `object`

One KYC document, keyed by its type. Know more about the [Document entity](https://razorpay.com/docs/api/partners/accounts/document-entity.md).

**business\_profile.stakeholders.\<stakeholder\_id>.address** `object`

The person's own address. It is `null` unless you sent it.

**business\_profile.stakeholders.\<stakeholder\_id>.address.type** `string`

Which address this is, the same as its key. Possible values:

* `registered_address`: The registered business address. For an individual, Razorpay fills it from the CKYC record or the proof of address when you do not send it.
* `operational_address`: Where the business operates for this account. One per account. With a GSTIN, it is the place of business on that GST registration.

**business\_profile.stakeholders.\<stakeholder\_id>.address.line1** `string`

First line of the address.

**business\_profile.stakeholders.\<stakeholder\_id>.address.line2** `string`

Second line of the address.

**business\_profile.stakeholders.\<stakeholder\_id>.address.city** `string`

City or district.

**business\_profile.stakeholders.\<stakeholder\_id>.address.state** `string`

State, as an ISO 3166-2 subdivision code such as `KA`.

**business\_profile.stakeholders.\<stakeholder\_id>.address.postal\_code** `string`

The 6-digit PIN code.

**business\_profile.stakeholders.\<stakeholder\_id>.address.country** `string`

ISO 3166-1 alpha-2, for example `IN`.

**business\_profile.stakeholders.\<stakeholder\_id>.date\_of\_birth** `string`

The person's date of birth. It is `null` unless you sent it. Format: `YYYY-MM-DD`.

**business\_profile.stakeholders.\<stakeholder\_id>.additional\_data** `object`

Other attributes of the person, such as gender or title. `{}` when the person has none.

**business\_profile.stakeholders.\<stakeholder\_id>.created\_at** `integer`

Time at which the person was added, as a Unix timestamp in seconds.

**business\_profile.stakeholders.\<stakeholder\_id>.updated\_at** `integer`

Time at which the person last changed, as a Unix timestamp in seconds.

**business\_profile.stakeholders.\<stakeholder\_id>.percentage\_ownership** `number`

Ownership as a decimal from 0 to 100. Send `25.5`, not `25.5%`.

**business\_profile.addresses** `array`

The business's addresses, one of each `type`. Razorpay merges the list by `type`, so an update sends only the address that changed, with its `type`.

**business\_profile.addresses\[].type** `string`

Which address this is. Possible values:

* `registered_address`: The registered business address. For an individual, Razorpay fills it from the CKYC record or the proof of address when you do not send it.
* `operational_address`: Where the business operates for this account. One per account. With a GSTIN, it is the place of business on that GST registration.

**business\_profile.addresses\[].line1** `string`

First line of the address.

**business\_profile.addresses\[].line2** `string`

Second line of the address.

**business\_profile.addresses\[].city** `string`

City or district.

**business\_profile.addresses\[].state** `string`

State, as an ISO 3166-2 subdivision code such as `KA`.

**business\_profile.addresses\[].postal\_code** `string`

The 6-digit PIN code.

**business\_profile.addresses\[].country** `string`

ISO 3166-1 alpha-2, for example `IN`.

**business\_profile.metadata** `object`

Up to 15 key-value pairs for your own reference, such as your store ID, as in `notes` on other Razorpay entities. Razorpay does not read these.

**business\_profile.metadata.\<key>** `string`

The value under one key you chose. Maximum length: 256 characters.

**bank\_accounts** `object`

The account's bank accounts, keyed by purpose. `settlements_primary` receives settlements.

**bank\_accounts.\<bank\_account\_type>** `object`

One bank account and its verification, keyed by its purpose. The only key is `settlements_primary`.

**bank\_accounts.\<bank\_account\_type>.type** `string`

The purpose of the bank account, the same as its key. Possible value: `settlements_primary`.

**bank\_accounts.\<bank\_account\_type>.account\_number** `string`

The bank account number, 5 to 35 digits.

**bank\_accounts.\<bank\_account\_type>.routing\_code** `string`

The bank's routing code: the Indian Financial System Code (IFSC) in India, as in the Payouts APIs.

**bank\_accounts.\<bank\_account\_type>.routing\_code\_type** `string`

The kind of `routing_code`. Send it with every account number and routing code. Possible value: `IFSC`.

**bank\_accounts.\<bank\_account\_type>.supporting\_document** `object`

Optional. It is `null` unless a document is attached. No requirement asks for it, since no document type is a bank proof. Know more about the [Document entity](https://razorpay.com/docs/api/partners/accounts/document-entity.md).

**bank\_accounts.\<bank\_account\_type>.verification** `object`

The outcome of a verification check.

**bank\_accounts.\<bank\_account\_type>.verification.status** `string`

Where the check is. Possible values:

* `in_progress`: The check is running.
* `deferred`: The check could not conclude, so a reviewer decides after the product is submitted. The requirement clears and `error_code` is `null`.
* `verified`: The check passed.
* `rejected`: The check failed. `error_code` says why.
* `collected`: Razorpay has received the value and has not checked it yet.

**bank\_accounts.\<bank\_account\_type>.verification.error\_code** `string`

A stable code for the failure, such as `bank_name_mismatch`, `pan_not_found` or `otp_invalid`. Razorpay never returns the bank's or registry's own record, such as the account holder's name. The code says what did not match. Know more about [failed-check codes](https://razorpay.com/docs/api/partners/accounts/errors.md#failed-check-codes).

**bank\_accounts.\<bank\_account\_type>.verification.error\_description** `string`

A sentence to show the sub-merchant. The wording can change. It never repeats the value sent.

**bank\_accounts.\<bank\_account\_type>.verification.verified\_at** `integer`

Time at which the check passed, as a Unix timestamp in seconds.

**bank\_accounts.\<bank\_account\_type>.verification.metadata** `object`

Details of the check, where it has any. `{}` when the check has none.

**bank\_accounts.\<bank\_account\_type>.verification.created\_at** `integer`

Time at which the check started, as a Unix timestamp in seconds.

**products** `object`

The products the account holds, keyed by product type, such as `payment_gateway`.

**products.\<product\_type>** `object`

One product, keyed by its type, with its status and the requirements still due.

**products.\<product\_type>.type** `string`

A Razorpay product, the same as its key. `payment_gateway` accepts payments on websites and apps. Possible values:

* `payment_gateway`
* `pos`
* `billing`
* `business_banking`
* `payroll`
* `agent_studio`
* `optimizer`

**products.\<product\_type>.status** `string`

Where the product is in onboarding. Activation needs the business's KYC verified and the product's own checks passed, such as the subcategory and any website sent. Razorpay checks the website again every year. Possible values:

* `created`: The product is on the account. Nothing is submitted yet.
* `in_progress`: Information is being collected.
* `under_review`: Submitted. Razorpay is reviewing it. The KYC details are locked.
* `needs_clarification`: A reviewer asked for clarification. Only the requirements listed can change.
* `edd_pending`: Submitted. Razorpay needs enhanced due diligence first, usually a video KYC call because no CKYC record exists. The requirements hold `create_video_kyc_link`. The KYC details are locked.
* `activated`: The product is live. Live payments API keys are available.
* `rejected`: Razorpay rejected the application. `status_reason` says why. Razorpay accepts no further changes.
* `suspended`: Suspended after activation, for example when the yearly website check fails and is not resolved. `status_reason` says why. `requirements` lists what would resolve it.

**products.\<product\_type>.status\_reason** `object`

Why the product is `rejected` or `suspended`. It is `null` in every other status. Branch on `code` and show `description`.

**products.\<product\_type>.status\_reason.code** `string`

A stable code for the reason. Possible values:

* `category_not_allowed`: Rejected: what the business sells is on Razorpay's restricted list.
* `clarification_not_answered`: Rejected: a reviewer's clarification was not answered in time.
* `identity_not_verified`: Rejected: the owner or signatory could not be verified, for example after failed video KYC calls.
* `risk_review_failed`: Rejected or suspended after Razorpay's risk review. It never says which check failed, because Razorpay does not disclose screening outcomes.
* `website_review_failed`: Suspended: the yearly website check failed and was not resolved.

**products.\<product\_type>.status\_reason.description** `string`

A sentence to show the sub-merchant. The wording can change.

**products.\<product\_type>.created\_at** `integer`

Time at which the product was requested, as a Unix timestamp in seconds.

**products.\<product\_type>.updated\_at** `integer`

Time at which the product last changed, as a Unix timestamp in seconds.

**products.\<product\_type>.requirements** `array`

The information still due for this product, in any status, computed on every request. `[]` when nothing is due. Know more about the [Requirement entity](https://razorpay.com/docs/api/partners/accounts/requirement-entity.md).

**products.\<product\_type>.terms\_of\_service\_acceptance** `object`

The sub-merchant's acceptance of Razorpay's terms of service, as Razorpay recorded it. Razorpay keeps the full record for at least 5 years after the account closes. Razorpay returns only these fields.

**products.\<product\_type>.terms\_of\_service\_acceptance.ip** `string`

The IP address the sub-merchant accepted from.

**products.\<product\_type>.terms\_of\_service\_acceptance.device\_fingerprint\_id** `string`

The device fingerprint of the sub-merchant's device.

**products.\<product\_type>.terms\_of\_service\_acceptance.metadata** `object`

Details of the acceptance. `{}` when the acceptance has none.

**products.\<product\_type>.terms\_of\_service\_acceptance.accepted\_at** `integer`

Time at which the sub-merchant accepted, as a Unix timestamp in seconds.

**products.\<product\_type>.payment\_channels** `object`

For `payment_gateway`: the channels the business accepts payments on.

**products.\<product\_type>.payment\_channels.website** `object`

The business's website.

**products.\<product\_type>.payment\_channels.website.primary** `string`

The live website, on https. Razorpay checks liveness, content and MCC from it.

**products.\<product\_type>.payment\_channels.website.additional** `array`

Other websites of the business.

**products.\<product\_type>.payment\_channels.website.verification** `object`

The website check. It is `null` until the check starts, then `in_progress`. It ends as `verified` or as `rejected` with `website_unreachable`.

**products.\<product\_type>.payment\_channels.website.verification.status** `string`

Where the check is. Possible values:

* `in_progress`: The check is running.
* `deferred`: The check could not conclude, so a reviewer decides after the product is submitted. The requirement clears and `error_code` is `null`.
* `verified`: The check passed.
* `rejected`: The check failed. `error_code` says why.
* `collected`: Razorpay has received the value and has not checked it yet.

**products.\<product\_type>.payment\_channels.website.verification.error\_code** `string`

A stable code for the failure, such as `bank_name_mismatch`, `pan_not_found` or `otp_invalid`. Razorpay never returns the bank's or registry's own record, such as the account holder's name. The code says what did not match. Know more about [failed-check codes](https://razorpay.com/docs/api/partners/accounts/errors.md#failed-check-codes).

**products.\<product\_type>.payment\_channels.website.verification.error\_description** `string`

A sentence to show the sub-merchant. The wording can change. It never repeats the value sent.

**products.\<product\_type>.payment\_channels.website.verification.verified\_at** `integer`

Time at which the check passed, as a Unix timestamp in seconds.

**products.\<product\_type>.payment\_channels.website.verification.metadata** `object`

Details of the check, where it has any. `{}` when the check has none.

**products.\<product\_type>.payment\_channels.website.verification.created\_at** `integer`

Time at which the check started, as a Unix timestamp in seconds.

**products.\<product\_type>.payment\_channels.app\_android** `object`

The Android app.

**products.\<product\_type>.payment\_channels.app\_android.url** `string`

The Play Store link.

**products.\<product\_type>.payment\_channels.app\_ios** `object`

The iOS app.

**products.\<product\_type>.payment\_channels.app\_ios.url** `string`

The App Store link.

**products.\<product\_type>.clarification\_responses** `object`

The sub-merchant's text replies to the points a reviewer flagged in `needs_clarification`. Each reply is keyed by the path of what it answers, such as `bank_accounts.settlements_primary`.

**products.\<product\_type>.clarification\_responses.\<field\_path>** `string`

One reply, under the path of what it answers.

**notes** `object`

Up to 15 key-value pairs for your own reference, such as your store ID, as in `notes` on other Razorpay entities. Razorpay does not read these.

**notes.\<key>** `string`

The value of one note, under a key you chose. Maximum length: 256 characters.

**created\_at** `integer`

Time at which the account was created, as a Unix timestamp in seconds.

**updated\_at** `integer`

Time at which the account last changed, as a Unix timestamp in seconds.

## Errors

> [accordion] The phone must be +91 followed by 10 digits.
>
> **Code:** `400`
>
> **Reason:** `invalid_format`
>
> A query parameter does not match its format:
>
> * `email` is not an email.
> * `phone` is not +91 and 10 digits.
> * `from` or `to` is not a Unix time.
> * `count` is outside 1-100.
> * `skip` is negative.
>
> An email or phone with no account is not an error. It returns `count: 0`.
>
> **Solution:** Correct the value named in `error.field` and send it again. `metadata.pattern` shows the expected format. `metadata.minimum` and `metadata.maximum` show the range.

> [accordion] Choose one of the allowed values.
>
> **Code:** `400`
>
> **Reason:** `invalid_option`
>
> `product` is not a product.
>
> **Solution:** Send one of the allowed values. `metadata.allowed_values` lists them when the list is short.

> [accordion] The start time is after the end time.
>
> **Code:** `400`
>
> **Reason:** `invalid_request`
>
> `from` is after `to`.
>
> **Solution:** Send a `from` that is at or before `to`.

> [accordion] The credentials aren't valid.
>
> **Code:** `401`
>
> **Reason:** `invalid_credentials`
>
> The `Authorization` header is missing or is not Basic. Other causes are a key that is not a partner key or a wrong secret. A secret also stops working when it is revoked or its rotation window ends.
>
> **Solution:** Send your partner key and secret as HTTP Basic credentials. Check that the secret is current for the key.

> [accordion] Onboarding isn't enabled for this platform.
>
> **Code:** `403`
>
> **Reason:** `onboarding_not_enabled`
>
> Your app does not have access to the Onboarding APIs in this mode. Razorpay may also have turned off your app's access.
>
> **Solution:** Contact Razorpay to get access to the Onboarding APIs for your app in this mode.

> [accordion] Requests from this address aren't allowed.
>
> **Code:** `403`
>
> **Reason:** `ip_not_allowed`
>
> The request came from an IP address outside your app's allowlist for its mode. Test mode checks the allowlist once it has an entry.
>
> **Solution:** Send requests from an IP range on your app's allowlist for this mode. To use another range, add it to the allowlist on the Partner Dashboard.

> [accordion] The business has withdrawn this platform's access to its Razorpay account.
>
> **Code:** `403`
>
> **Reason:** `consent_withdrawn`
>
> Through Razorpay, the sub-merchant withdrew your permission to act on the account. Calls on this account never succeed again for your platform.
>
> **Solution:** Stop calling this account and update your records.

> [accordion] The requested resource doesn't exist.
>
> **Code:** `404`
>
> **Reason:** `not_found`
>
> No account with this ID is mapped to your app in this mode. The account does not exist, belongs to another platform or belongs to a direct Razorpay merchant. It can also be a test account called in live mode.
>
> **Solution:** Check the ID in `error.field`. Use the ID of an account mapped to your app, in the same mode as your key.

> [accordion] Too many requests. Try again shortly.
>
> **Code:** `429`
>
> **Reason:** `rate_limited`
>
> Your app sent more requests than its rate limit allows.
>
> **Solution:** Wait for the time in the `Retry-After` header, then retry.

> [accordion] Something went wrong on our side. Try again.
>
> **Code:** `500`
>
> **Reason:** `internal_error`
>
> Something went wrong inside Razorpay.
>
> **Solution:** Retry the request.
