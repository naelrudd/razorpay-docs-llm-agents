> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create an Account

> Create a sub-merchant account using Razorpay Accounts API.

Available in
🇮🇳 India

Use this endpoint to create a sub-merchant account with its owner user and request the products in `products`.

> [!NOTE]
>
> **Handy Tips**
>
> * Authenticate with the key and secret of your test pair or live pair. In the API playground, enter the test key as the username and its secret as the password. Use the live pair in live mode.
> * Only `country` and `user` are mandatory in this call. Every KYC object is optional here. Each field the product needs is still due before submission, and the product's `requirements` list it. Send it now or later with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md).
> * Razorpay applies the values in the order onboarding needs them and verifies each one.
> * The response returns within 5 sec. A check still running shows `verification.status` as `in_progress`. Its outcome follows on the account.
> * The PAN of an individual, a proprietor or a company's authorised person can have a Central KYC Records Registry (CKYC) record. When the PAN verifies and a record exists, `ckyc_fetch` is due. Skip the record or run `send_ckyc_otp`.
> * An unverified phone or email makes `send_phone_otp` or `send_email_otp` due. These actions send a One-Time Password (OTP).
> * Send each document as a `url`: a pre-signed https link, valid for at least 15 min, that Razorpay downloads once. Create does not take a document `id`, because the account does not exist yet. Sending a link is coming soon. Until then, [upload the file](https://razorpay.com/docs/api/partners/accounts/upload-document.md) and send its `id` with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md).
> * Razorpay maps the new account to your app. Only that app can act on it.

> [!WARNING]
>
> **Watch Out!**
>
> * A value in the wrong format, such as a malformed PAN, fails the whole request with `400`. Razorpay creates nothing.
> * Razorpay saves a well-formed value that fails verification, such as a bank name mismatch. Its `verification` shows the failure and its requirement stays due.
> * Create never submits the product. Send the sub-merchant's acceptance of the terms of service with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md) to submit it.
> * Create always makes a new account, even when the owner already has one. To continue an existing account, [fetch the owner's accounts](https://razorpay.com/docs/api/partners/accounts/fetch.md) first.

```bash Curl theme={null}
curl -X POST https://api.razorpay.com/v1/accounts \
-u rzp_test_partner_[CLIENT_ID]:[CLIENT_SECRET] \
-H "Content-Type: application/json" \
-H "X-Idempotency-Key: [UNIQUE_KEY]" \
-d '{
  "user": {
    "email": "gaurav.kumar@example.com",
    "phone": "+919611752201",
    "name": "Gaurav Kumar"
  },
  "country": "IN",
  "statement_descriptor": {
    "value": "Gaurav Kumar"
  },
  "business_profile": {
    "business_type": "individual",
    "identity_numbers": {
      "individual_pan": {
        "value": "ABCPD1234A"
      }
    },
    "business_category": {
      "category": "ecommerce",
      "subcategory": "fashion_and_lifestyle",
      "business_model_clarifications": {
        "bmc_question_2": {
          "answer": [
            "bmc_question_2_option_1"
          ]
        }
      }
    }
  },
  "bank_accounts": {
    "settlements_primary": {
      "account_number": "001234567890",
      "routing_code": "ICIC0000009",
      "routing_code_type": "IFSC"
    }
  },
  "products": {
    "payment_gateway": {
      "payment_channels": {
        "website": {
          "primary": "https://www.example.com"
        }
      }
    }
  }
}'
```

```json Success theme={null}
{
  "id": "acc_U1dH90oryt1Amt",
  "country": "IN",
  "user": {
    "email": "gaurav.kumar@example.com",
    "phone": "+919611752201",
    "name": "Gaurav Kumar",
    "is_email_verified": false,
    "is_phone_verified": false,
    "role": "owner"
  },
  "is_mfa_enabled": false,
  "statement_descriptor": {
    "value": "Gaurav Kumar",
    "verification": {
      "status": "rejected",
      "error_code": "name_mismatch",
      "error_description": "The brand name must match the business name, the PAN name or the website."
    },
    "metadata": {}
  },
  "business_profile": {
    "business_type": "individual",
    "business_name": "Rzp Test QA Merchant",
    "identity_numbers": {
      "individual_pan": {
        "type": "individual_pan",
        "value": "ABCPD1234A",
        "verification": {
          "status": "verified"
        },
        "is_skipped": false
      }
    },
    "documents": {},
    "business_category": {
      "category": "ecommerce",
      "subcategory": "fashion_and_lifestyle",
      "mcc": "5651",
      "business_model_clarifications": {
        "bmc_question_2": {
          "bmc_input_type": "single_select",
          "question": "What is your average delivery time after receiving an order?",
          "options": [
            {
              "label": "0-7 days",
              "value": "bmc_question_2_option_1"
            },
            {
              "label": "8-14 days",
              "value": "bmc_question_2_option_2"
            },
            {
              "label": "15-21 days",
              "value": "bmc_question_2_option_3"
            },
            {
              "label": "22-35 days",
              "value": "bmc_question_2_option_4"
            },
            {
              "label": "35+ days",
              "value": "bmc_question_2_option_5"
            },
            {
              "label": "No shipping required",
              "value": "bmc_question_2_option_6"
            }
          ],
          "answer": [
            "bmc_question_2_option_1"
          ]
        }
      }
    },
    "shareholders": {},
    "addresses": [],
    "clarification_responses": {}
  },
  "bank_accounts": {
    "settlements_primary": {
      "type": "settlements_primary",
      "account_number": "001234567890",
      "routing_code": "ICIC0000009",
      "routing_code_type": "IFSC",
      "verification": {
        "status": "verified"
      }
    }
  },
  "products": {
    "payment_gateway": {
      "type": "payment_gateway",
      "status": "in_progress",
      "requirements": [
        {
          "id": "req_U1cRDy9xYeEDS7",
          "requirement_code": "verify_owner_phone",
          "requirement_level": "mandatory",
          "requirement_type": "composite",
          "description": "Verify the owner's phone: run send_phone_otp, then send the code.",
          "fulfillment_criteria": "all_of",
          "sub_requirements": [
            {
              "id": "req_U1cRDxEnaqAuOU",
              "requirement_code": "send_phone_otp",
              "requirement_level": "mandatory",
              "requirement_type": "action",
              "description": "Send the code to the owner."
            },
            {
              "id": "req_U1cRDvvEsishdC",
              "requirement_code": "phone_otp",
              "requirement_level": "mandatory",
              "requirement_type": "input",
              "description": "The 6-digit code.",
              "field_path": "phone_otp",
              "value_type": "text",
              "metadata": {
                "constraints": {
                  "pattern": "^[0-9]{6}$"
                }
              }
            }
          ]
        },
        {
          "id": "req_U1cRDy5AzYtdu7",
          "requirement_code": "verify_owner_email",
          "requirement_level": "mandatory",
          "requirement_type": "composite",
          "description": "Verify the owner's email: run send_email_otp, then send the code.",
          "fulfillment_criteria": "all_of",
          "sub_requirements": [
            {
              "id": "req_U1cRDxA2qeYFZ8",
              "requirement_code": "send_email_otp",
              "requirement_level": "mandatory",
              "requirement_type": "action",
              "description": "Send the code to the owner."
            },
            {
              "id": "req_U1cRDuqM9wbUWi",
              "requirement_code": "email_otp",
              "requirement_level": "mandatory",
              "requirement_type": "input",
              "description": "The 6-digit code.",
              "field_path": "email_otp",
              "value_type": "text",
              "metadata": {
                "constraints": {
                  "pattern": "^[0-9]{6}$"
                }
              }
            }
          ]
        },
        {
          "id": "req_U1cRDuNgK83rBi",
          "requirement_code": "ckyc_fetch",
          "requirement_level": "mandatory",
          "requirement_type": "composite",
          "description": "Fetch the owner's CKYC record with the code sent to the mobile linked to it (XXXXXX6638). Or skip CKYC.",
          "fulfillment_criteria": "one_of",
          "sub_requirements": [
            {
              "id": "req_U1cRDxOKe0vlFc",
              "requirement_code": "skip_ckyc",
              "requirement_level": "conditional",
              "requirement_type": "input",
              "description": "Skip CKYC.",
              "field_path": "business_profile.identity_numbers.individual_ckyc.is_skipped",
              "value_type": "boolean"
            },
            {
              "id": "req_U1cRDuXGUqfd2c",
              "requirement_code": "ckyc_otp_verification",
              "requirement_level": "conditional",
              "requirement_type": "composite",
              "description": "Run send_ckyc_otp, then send the code with its request id.",
              "fulfillment_criteria": "all_of",
              "sub_requirements": [
                {
                  "id": "req_U1cRDx5GHYUfiA",
                  "requirement_code": "send_ckyc_otp",
                  "requirement_level": "mandatory",
                  "requirement_type": "action",
                  "description": "Send an OTP to the mobile linked to the owner's CKYC record."
                },
                {
                  "id": "req_U1cRDuc1VAHyoM",
                  "requirement_code": "ckyc_request_id",
                  "requirement_level": "mandatory",
                  "requirement_type": "input",
                  "description": "The request_id send_ckyc_otp returned.",
                  "field_path": "business_profile.identity_numbers.individual_ckyc.request_id",
                  "value_type": "text"
                },
                {
                  "id": "req_U1cRDuSUi8WJjq",
                  "requirement_code": "ckyc_otp",
                  "requirement_level": "mandatory",
                  "requirement_type": "input",
                  "description": "The code sent to the CKYC-linked mobile.",
                  "field_path": "business_profile.identity_numbers.individual_ckyc.otp",
                  "value_type": "text"
                }
              ]
            }
          ]
        },
        {
          "id": "req_U1cRDxccRMtqvv",
          "requirement_code": "statement_descriptor",
          "requirement_level": "mandatory",
          "requirement_type": "input",
          "description": "The brand name must match the business name, the PAN name or the website.",
          "field_path": "statement_descriptor.value",
          "value_type": "text",
          "options": [
            {
              "label": "Rzp Test QA Merchant",
              "value": "Rzp Test QA Merchant"
            },
            {
              "label": "Example",
              "value": "Example"
            }
          ],
          "metadata": {
            "constraints": {
              "maxLength": 255
            }
          }
        }
      ],
      "payment_channels": {
        "website": {
          "primary": "https://www.example.com",
          "additional": []
        },
        "whatsapp_sms_email": false,
        "offline_store": false
      },
      "created_at": 1795003653,
      "updated_at": 1795003654
    }
  },
  "created_at": 1795003653,
  "updated_at": 1795003654
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "The PAN must be 10 characters: 5 letters, 4 digits and a letter.",
    "source": "business",
    "step": "validation",
    "reason": "invalid_format",
    "field": "business_profile.authorized_person.identity_numbers.individual_pan",
    "metadata": {
      "pattern": "^[A-Z]{5}[0-9]{4}[A-Z]$"
    }
  }
}
```

## Request Parameters

Only `country` and `user` are mandatory at the top level of this call. The other top-level fields are optional here and due before submission when the product's `requirements` list them. A nested field marked required applies only when you send its parent object.

**X-Idempotency-Key** `string` *required*

A unique key you generate for each write, 16-64 printable ASCII characters long. A Universally Unique Identifier (UUID) works. A retry with the same key within 24 h returns the original response instead of acting twice. Know more about [idempotency](https://razorpay.com/docs/api/partners/accounts#idempotency).

**country** `string` *required*

ISO 3166-1 alpha-2 country of the business, `IN`. Possible value: `IN`.

**user** `object` *required*

A person who signs in to the Razorpay Dashboard. The same user can own accounts on several platforms.

**user.email** `string` *required*

The user's email. Maximum length: 255 characters.

**user.phone** `string` *required*

The user's phone: +91 followed by 10 digits. Pattern: `^\+91[0-9]{10}$`.

**user.name** `string` *required*

The name of the person completing the onboarding. Length: 2-127 characters.

**is\_mfa\_enabled** `boolean`

Turns on 2-factor authentication for the owner on the Razorpay Dashboard. Default: `false`.

**statement\_descriptor** `object`

The brand name customers see on their bank statements and receipts.

**statement\_descriptor.value** `string` *required*

The brand name customers see on their bank statements and receipts, so they recognise the charge. Maximum length: 255 characters.

**business\_profile** `object`

The business's KYC identity on this account.

**business\_profile.business\_type** `string` *required*

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

**business\_profile.identity\_numbers.business\_pan** `object`

The PAN of the business.

**business\_profile.identity\_numbers.business\_pan.value** `string`

The business PAN, 10 characters long: 5 letters, 4 digits and a letter.

**business\_profile.identity\_numbers.gstin** `object`

The Goods and Services Tax Identification Number (GSTIN). One per account: the GSTIN this account trades under. A business registered for GST in several states sends the GSTIN for this account. It sends that registration's address as `operational_address`.

**business\_profile.identity\_numbers.gstin.value** `string`

The GSTIN of the business.

**business\_profile.identity\_numbers.udyam\_registration** `object`

The Udyam registration number.

**business\_profile.identity\_numbers.udyam\_registration.value** `string`

The Udyam registration number of the business.

**business\_profile.identity\_numbers.cin** `object`

The Corporate Identification Number (CIN).

**business\_profile.identity\_numbers.cin.value** `string`

The CIN of the company.

**business\_profile.documents** `object`

The business's KYC documents, keyed by document type. Send each document as a `url`. Sending a link is coming soon. Until then, [upload the file](https://razorpay.com/docs/api/partners/accounts/upload-document.md) and send its `id` with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md).

**business\_profile.documents.business\_pan** `object`

Business PAN.

**business\_profile.documents.certificate\_of\_incorporation** `object`

Certificate of incorporation.

**business\_profile.documents.gst\_certificate** `object`

GST certificate.

**business\_profile.documents.udyam\_registration\_certificate** `object`

Udyam registration certificate.

**business\_profile.documents.shop\_establishment** `object`

Shop and establishment certificate.

**business\_profile.documents.\<document\_type>** `object`

Any other document the `business_documents` requirement asks for, keyed by its type, such as `fssai_certificate`. Know more about [document types](https://razorpay.com/docs/api/partners/accounts/document-entity.md).

**business\_profile.documents.\<document\_type>.url** `string`

A link Razorpay downloads the file from, in place of an upload. Send a pre-signed https link, valid for at least 15 min and never a public object. Razorpay downloads it once and keeps its own copy. Sending a link is coming soon. Until then, [upload the file](https://razorpay.com/docs/api/partners/accounts/upload-document.md) and send its `id` with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md).

**business\_profile.business\_category** `object`

How the business is classified. Send the category and its subcategory together. Razorpay derives the Merchant Category Code (MCC) from the subcategory.

**business\_profile.business\_category.category** `string` *required*

The business category, from the requirement's `options`.

**business\_profile.business\_category.subcategory** `string` *required*

The subcategory of the category. Send it with `category`. Razorpay derives the `mcc` from it. Know more about [business categories and subcategories](https://razorpay.com/docs/api/partners/accounts/business-categories.md).

**business\_profile.business\_category.mcc** `string`

The MCC. Razorpay derives it from the subcategory when you send the category and subcategory. Pattern: `^[0-9]{4}$`.

**business\_profile.business\_category.business\_description** `string`

What the business sells, such as `Clothing and accessories for men, women and children, sold online`. Maximum length: 100 characters.

**business\_profile.business\_category.business\_model\_clarifications** `object`

Answers to the business-model questions, keyed by question ID. Know more about the [business model questions](https://razorpay.com/docs/api/partners/accounts/business-model-questions.md).

**business\_profile.business\_category.business\_model\_clarifications.\<question\_id>** `object`

One business-model question and its answer.

**business\_profile.business\_category.business\_model\_clarifications.\<question\_id>.question\_id** `string` *required*

The question's ID, the same as its key.

**business\_profile.business\_category.business\_model\_clarifications.\<question\_id>.answer** `array` *required*

The answer. One value for single-select and text questions.

**business\_profile.authorized\_person** `object`

The person authorised to act for the business on this account. They need not hold a share of it. For an individual or a proprietor, this is the owner. Send the owner's personal PAN at `business_profile.authorized_person.identity_numbers.individual_pan`. The business name comes from that PAN.

**business\_profile.authorized\_person.name** `string`

The person's full name.

**business\_profile.authorized\_person.identity\_numbers** `object` *required*

The person's identifiers keyed by type.

**business\_profile.authorized\_person.identity\_numbers.individual\_pan** `object`

The PAN of a person: the authorised person, a stakeholder, an individual or a proprietor.

**business\_profile.authorized\_person.identity\_numbers.individual\_pan.value** `string`

The person's PAN, 10 characters long: 5 letters, 4 digits and a letter.

**business\_profile.authorized\_person.identity\_numbers.individual\_ckyc** `object`

The person's CKYC record. Its `value` is `null`. Send the code from `send_ckyc_otp` in `otp` and its request ID in `request_id`.

**business\_profile.authorized\_person.identity\_numbers.individual\_ckyc.is\_skipped** `boolean`

Send `true` to skip the CKYC record. The proof of address is then due instead. Default: `false`.

**business\_profile.authorized\_person.identity\_numbers.individual\_ckyc.otp** `string`

The code that `send_ckyc_otp` sent to the mobile on the CKYC record. Send it with `request_id`. Responses do not return it. Pattern: `^[0-9]{6}$`.

**business\_profile.authorized\_person.identity\_numbers.individual\_ckyc.request\_id** `string`

The request ID that came with the code, in the `request_id` output of `send_ckyc_otp`. Send it with `otp`. Responses do not return it.

**business\_profile.authorized\_person.documents** `object` *required*

The person's KYC documents keyed by document type.

**business\_profile.authorized\_person.documents.individual\_pan\_document** `object`

Personal PAN.

**business\_profile.authorized\_person.documents.aadhaar\_front** `object`

Aadhaar front.

**business\_profile.authorized\_person.documents.aadhaar\_back** `object`

Aadhaar back.

**business\_profile.authorized\_person.documents.passport\_front** `object`

Passport front.

**business\_profile.authorized\_person.documents.passport\_back** `object`

Passport back.

**business\_profile.authorized\_person.documents.voter\_id\_front** `object`

Voter ID front.

**business\_profile.authorized\_person.documents.voter\_id\_back** `object`

Voter ID back.

**business\_profile.authorized\_person.documents.\<document\_type>.url** `string`

A link Razorpay downloads the file from, in place of an upload. Send a pre-signed https link, valid for at least 15 min and never a public object. Razorpay downloads it once and keeps its own copy. Sending a link is coming soon. Until then, [upload the file](https://razorpay.com/docs/api/partners/accounts/upload-document.md) and send its `id` with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md).

**business\_profile.authorized\_person.address** `object`

The person's own address.

**business\_profile.authorized\_person.address.line1** `string` *required*

First line of the address.

**business\_profile.authorized\_person.address.line2** `string`

Second line of the address.

**business\_profile.authorized\_person.address.city** `string` *required*

City or district.

**business\_profile.authorized\_person.address.state** `string` *required*

State, as an ISO 3166-2 subdivision code such as `KA`.

**business\_profile.authorized\_person.address.postal\_code** `string` *required*

The 6-digit PIN code. Pattern: `^[0-9]{6}$`.

**business\_profile.authorized\_person.address.country** `string` *required*

ISO 3166-1 alpha-2, for example `IN`.

**business\_profile.authorized\_person.date\_of\_birth** `string`

The person's date of birth. Format: `YYYY-MM-DD`.

**business\_profile.authorized\_person.additional\_data** `object`

Other attributes of the person, such as gender or title.

**business\_profile.stakeholders** `object`

The business's stakeholders, the people who hold a share of it, keyed by stakeholder ID. To add a stakeholder, use any new key.

**business\_profile.stakeholders.\<stakeholder\_id>** `object`

A stakeholder: a person who holds a share of the business.

**business\_profile.stakeholders.\<stakeholder\_id>.name** `string`

The person's full name.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers** `object` *required*

The person's identifiers keyed by type.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.individual\_pan** `object`

The PAN of a person: the authorised person, a stakeholder, an individual or a proprietor.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.individual\_pan.value** `string`

The person's PAN, 10 characters long: 5 letters, 4 digits and a letter.

**business\_profile.stakeholders.\<stakeholder\_id>.documents** `object` *required*

The person's KYC documents keyed by document type.

**business\_profile.stakeholders.\<stakeholder\_id>.documents.\<document\_type>** `object`

A KYC document of the stakeholder, keyed by its type, such as `aadhaar_front`.

**business\_profile.stakeholders.\<stakeholder\_id>.documents.\<document\_type>.url** `string`

A link Razorpay downloads the file from, in place of an upload. Send a pre-signed https link, valid for at least 15 min and never a public object. Razorpay downloads it once and keeps its own copy. Sending a link is coming soon. Until then, [upload the file](https://razorpay.com/docs/api/partners/accounts/upload-document.md) and send its `id` with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md).

**business\_profile.stakeholders.\<stakeholder\_id>.address** `object`

The person's own address.

**business\_profile.stakeholders.\<stakeholder\_id>.address.line1** `string` *required*

First line of the address.

**business\_profile.stakeholders.\<stakeholder\_id>.address.line2** `string`

Second line of the address.

**business\_profile.stakeholders.\<stakeholder\_id>.address.city** `string` *required*

City or district.

**business\_profile.stakeholders.\<stakeholder\_id>.address.state** `string` *required*

State, as an ISO 3166-2 subdivision code such as `KA`.

**business\_profile.stakeholders.\<stakeholder\_id>.address.postal\_code** `string` *required*

The 6-digit PIN code. Pattern: `^[0-9]{6}$`.

**business\_profile.stakeholders.\<stakeholder\_id>.address.country** `string` *required*

ISO 3166-1 alpha-2, for example `IN`.

**business\_profile.stakeholders.\<stakeholder\_id>.date\_of\_birth** `string`

The person's date of birth. Format: `YYYY-MM-DD`.

**business\_profile.stakeholders.\<stakeholder\_id>.additional\_data** `object`

Other attributes of the person, such as gender or title.

**business\_profile.stakeholders.\<stakeholder\_id>.percentage\_ownership** `number` *required*

Ownership as a decimal from 0 to 100. Send `25.5`, not `25.5%`.

**business\_profile.addresses** `array`

The business's addresses, one of each `type`. Razorpay merges the list by `type`, so an update sends only the address that changed, with its `type`.

**business\_profile.addresses\[].type** `string` *required*

Which address this is. Possible values:

* `registered_address`: The registered business address. For an individual, Razorpay fills it from the CKYC record or the proof of address when you do not send it.
* `operational_address`: Where the business operates for this account. One per account. With a GSTIN, it is the place of business on that GST registration.

**business\_profile.addresses\[].line1** `string` *required*

First line of the address.

**business\_profile.addresses\[].line2** `string`

Second line of the address.

**business\_profile.addresses\[].city** `string` *required*

City or district.

**business\_profile.addresses\[].state** `string` *required*

State, as an ISO 3166-2 subdivision code such as `KA`.

**business\_profile.addresses\[].postal\_code** `string` *required*

The 6-digit PIN code. Pattern: `^[0-9]{6}$`.

**business\_profile.addresses\[].country** `string` *required*

ISO 3166-1 alpha-2, for example `IN`.

**business\_profile.metadata** `object`

Up to 15 key-value pairs for your own reference, such as your store ID, as in `notes` on other Razorpay entities. Razorpay does not read these.

**business\_profile.metadata.\<key>** `string`

The value under one key you choose. Maximum length: 256 characters.

**bank\_accounts** `object`

The business's bank accounts, keyed by purpose. `settlements_primary` receives settlements. A new account sent under the same key takes the old one's place. Settlements move to it once it is verified.

**bank\_accounts.settlements\_primary** `object`

The bank account that receives settlements.

**bank\_accounts.settlements\_primary.account\_number** `string` *required*

The bank account number, 5 to 35 digits.

**bank\_accounts.settlements\_primary.routing\_code** `string` *required*

The bank's routing code: the Indian Financial System Code (IFSC) in India, as in the Payouts APIs.

**bank\_accounts.settlements\_primary.routing\_code\_type** `string` *required*

The kind of `routing_code`. Send it with every account number and routing code. Possible value: `IFSC`.

**bank\_accounts.settlements\_primary.supporting\_document** `object`

Optional. No requirement asks for it, since no document type is a bank proof.

**bank\_accounts.settlements\_primary.supporting\_document.url** `string`

A link Razorpay downloads the file from, in place of an upload. Send a pre-signed https link, valid for at least 15 min and never a public object. Razorpay downloads it once and keeps its own copy.

**products** `object`

The products to request, keyed by product type, each with its starting values. Each product gets its own status and requirements.

**products.payment\_gateway** `object`

Payment Gateway, to accept payments on websites and apps.

**products.payment\_gateway.payment\_channels** `object` *required*

The channels the business accepts payments on.

**products.payment\_gateway.payment\_channels.website** `object`

The business's website.

**products.payment\_gateway.payment\_channels.website.primary** `string`

The live website, on https. Razorpay checks liveness, content and MCC from it.

**products.payment\_gateway.payment\_channels.website.additional** `array`

Other websites of the business.

**products.payment\_gateway.payment\_channels.app\_android** `object`

The Android app.

**products.payment\_gateway.payment\_channels.app\_android.url** `string`

The Play Store link.

**products.payment\_gateway.payment\_channels.app\_ios** `object`

The iOS app.

**products.payment\_gateway.payment\_channels.app\_ios.url** `string`

The App Store link.

**notes** `object`

Up to 15 key-value pairs for your own reference, such as your store ID, as in `notes` on other Razorpay entities. Razorpay does not read these.

**notes.\<key>** `string`

The value of one note, under a key you choose. Maximum length: 256 characters.

## Response Parameters

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
* `gstin`: The GSTIN. One per account: the GSTIN this account trades under. A business registered for GST in several states sends the GSTIN for this account. It sends that registration's address as `operational_address`.
* `udyam_registration`: The Udyam registration number.
* `cin`: The CIN.
* `individual_ckyc`: The person's CKYC record. Its `value` is `null`. Send the code from `send_ckyc_otp` in `otp` and its request ID in `request_id`.

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

The business's KYC documents, keyed by document type.

**business\_profile.documents.\<document\_type>** `object`

One KYC document, keyed by its type. Know more about the [Document entity](https://razorpay.com/docs/api/partners/accounts/document-entity.md).

**business\_profile.business\_category** `object`

How the business is classified. Razorpay derives the MCC from the subcategory.

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
* `udyam_registration`: The Udyam registration number.
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
* `udyam_registration`: The Udyam registration number.
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

The bank's routing code: the IFSC in India, as in the Payouts APIs.

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
* `clarification_not_answered`: Rejected: a reviewer asked for clarification and got no answer in time.
* `identity_not_verified`: Rejected: Razorpay could not verify the owner or signatory, for example after failed video KYC calls.
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

The sub-merchant's acceptance of Razorpay's terms of service, as Razorpay recorded it. Razorpay keeps the full record for at least 5 years after the account closes and returns only these fields.

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

> [accordion] A required header is missing.
>
> **Code:** `400`
>
> **Reason:** `missing_header`
>
> `X-Idempotency-Key` is missing or is not 16-64 printable ASCII characters.
>
> **Solution:** Send the header named in `metadata.header`. On a write, send `X-Idempotency-Key` with 16-64 printable ASCII characters.

> [accordion] The request is missing a required field.
>
> **Code:** `400`
>
> **Reason:** `invalid_request`
>
> The request has one of these problems:
>
> * The body is not JSON.
> * `user`, with `email`, `phone` and `name`, is missing.
> * A key is not one that Create takes, such as a misspelled field or a read-only one like `verification`.
> * The body sends a document by `id`. Create does not take an `id`, because the account does not exist yet. Send a `url`.
>
> **Solution:** Send valid JSON with every required field. Remove any key the endpoint does not take, such as a misspelled or read-only field.

> [accordion] The PAN must be 10 characters: 5 letters, 4 digits and a letter.
>
> **Code:** `400`
>
> **Reason:** `invalid_format`
>
> A value does not match its format, and Razorpay creates nothing. The value is one of these:
>
> * An email
> * A phone that is not +91 and 10 digits
> * A PAN, GSTIN, CIN, IFSC or Udyam number
> * An account number that is not 5-35 digits
> * A PIN code or a date
> * An MCC that is not 4 digits
> * A `statement_descriptor` or `business_description` over its length
>
> **Solution:** Correct the value named in `error.field` and send it again. `metadata.pattern` shows the expected format. `metadata.minimum` and `metadata.maximum` show the range.

> [accordion] Choose one of the allowed values.
>
> **Code:** `400`
>
> **Reason:** `invalid_option`
>
> A value is not one of its options. The value is one of these:
>
> * `country` other than `IN`
> * `business_type` or `routing_code_type`
> * A key under `products` that is not a product or is not in your contract
> * A business-model question or answer ID that is not one of the MCC's questions or options
>
> **Solution:** Send one of the allowed values. `metadata.allowed_values` lists them when the list is short.

> [accordion] The document couldn't be downloaded from the link.
>
> **Code:** `400`
>
> **Reason:** `invalid_document_url`
>
> A document `url` has one of these problems:
>
> * It is not https.
> * It points at, or redirects to, a private, loopback or cloud-metadata address.
> * Razorpay could not download it.
> * The file fails the upload checks.
>
> **Solution:** Send a pre-signed https link that Razorpay can download, valid for at least 15 min. Or create the account first. Then upload the file with [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md) and attach its ID with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md).

> [accordion] This request conflicts with an earlier one.
>
> **Code:** `400`
>
> **Reason:** `idempotency_key_reused`
>
> You used this `X-Idempotency-Key` in the last 24 h with a different body.
>
> **Solution:** Send a new `X-Idempotency-Key` for a different request. Reuse a key only to retry the same request.

> [accordion] The credentials aren't valid.
>
> **Code:** `401`
>
> **Reason:** `invalid_credentials`
>
> The `Authorization` header is missing or is not Basic. Other causes are a key that is not a partner key or a wrong secret. A secret also stops working when you revoke it or its rotation window ends.
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

> [accordion] The earlier request is still being processed.
>
> **Code:** `409`
>
> **Reason:** `idempotency_in_progress`
>
> A request with this `X-Idempotency-Key` is still running. Razorpay stores its result only when it finishes.
>
> **Solution:** Wait for the time in the `Retry-After` header, then retry with the same key.

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
> **Solution:** Retry the request. A write retried with the same `X-Idempotency-Key` does not act twice.
