> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Update an Account

> Update a sub-merchant account using Razorpay Accounts API.

Available in
🇮🇳 India

Use this endpoint to update an account with the information a requirement asks for.

> [!NOTE]
>
> **Handy Tips**
>
> * Authenticate with the key and secret of your test pair or live pair. In the API playground, enter the test key as the username and its secret as the password. Use the live pair in live mode.
> * Every top-level body field is optional in this call. Send what the product's `requirements` list, and only what is changing. Keyed objects (`identity_numbers`, `documents`, `stakeholders` and `bank_accounts`) merge by key. `addresses` merges by `type`.
> * `business_category` merges by attribute. Its `business_model_clarifications` merge by question ID. Any other node, such as a bank account, is replaced whole.
> * The response is the account, as [Fetch Accounts](https://razorpay.com/docs/api/partners/accounts/fetch.md) returns it, within 3 sec. Writes to one account run one at a time, in the order they arrive.
> * A saved value that fails verification still returns `200`. Its `verification` shows `rejected` with an `error_code`. Its requirement is due again.
> * A wrong One-Time Password (OTP) also returns `200`, with the code still due.
> * A check still running shows `verification.status` as `in_progress`. Fetch the account or wait for the `account.requirements.updated` webhook.

> [!WARNING]
>
> **Watch Out!**
>
> * Sending `products.<product_type>.terms_of_service_acceptance` submits the product. Most products come back `activated` in the same response.
> * A product moves to `under_review` when a check was deferred or a review starts. It moves to `edd_pending` when video KYC is needed.
> * From submission on, the KYC details are locked: the business profile, the authorised person, the stakeholders and the bank account. Changing one returns `409` with `field_locked`.
> * During `needs_clarification`, only the fields in `requirements` can change. After activation, a few details can change after a manual review by Razorpay. Know more about [account management](https://razorpay.com/docs/partners/aggregators/onboarding-api/account-management.md).

```bash Curl theme={null}
curl -X PATCH https://api.razorpay.com/v1/accounts/acc_TcdGEzmfKQzEl1 \
-u rzp_test_partner_[CLIENT_ID]:[CLIENT_SECRET] \
-H "Content-Type: application/json" \
-H "X-Idempotency-Key: [UNIQUE_KEY]" \
-d '{
  "business_profile": {
    "authorized_person": {
      "identity_numbers": {
        "individual_pan": {
          "value": "ABCPD1234A"
        }
      }
    }
  }
}'
```

```json Success theme={null}
{
  "id": "acc_TcdGEzmfKQzEl1",
  "country": "IN",
  "statement_descriptor": null,
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
        }
      },
      "documents": {},
      "address": null,
      "date_of_birth": null,
      "additional_data": {},
      "created_at": 1792433280,
      "updated_at": 1792433290
    },
    "stakeholders": {},
    "addresses": [],
    "metadata": {}
  },
  "bank_accounts": {},
  "products": {
    "payment_gateway": {
      "type": "payment_gateway",
      "status": "in_progress",
      "status_reason": null,
      "created_at": 1792433135,
      "updated_at": 1792433290,
      "requirements": [
        {
          "id": "req_hocykxcAkjCdtB",
          "requirement_code": "ckyc_fetch",
          "requirement_level": "mandatory",
          "requirement_type": "composite",
          "description": "The person's CKYC record, fetched with a code or skipped.",
          "fulfillment_criteria": "one_of",
          "sub_requirements": [
            {
              "id": "req_2KRiIGIhuAPNW6",
              "requirement_code": "skip_ckyc",
              "requirement_level": "conditional",
              "requirement_type": "input",
              "description": "Skip CKYC.",
              "field_path": "business_profile.authorized_person.identity_numbers.individual_ckyc.is_skipped",
              "value_type": "boolean",
              "status": "created"
            },
            {
              "id": "req_L3rskP8gX6YVHh",
              "requirement_code": "send_ckyc_otp",
              "requirement_level": "conditional",
              "requirement_type": "action",
              "description": "A Central KYC record was found for your PAN. Get a code on the mobile on your CKYC record to fetch it.",
              "status": "created"
            }
          ],
          "status": "created"
        },
        {
          "id": "req_yD8JfNtIoWXmu4",
          "requirement_code": "statement_descriptor",
          "requirement_level": "mandatory",
          "requirement_type": "input",
          "description": "The name shown on customers' receipts and statements.",
          "field_path": "statement_descriptor.value",
          "value_type": "text",
          "status": "created"
        },
        {
          "id": "req_VgRHb7QJNtMyj2",
          "requirement_code": "settlement_bank_account",
          "requirement_level": "mandatory",
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
  "updated_at": 1792433290
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

## Path Parameters

**account\_id** `string` *required*

The unique identifier of the account, `acc_`-prefixed. For example, `acc_TcdGEzmfKQzEl1`.

## Request Parameters

Every top-level body field is optional in this call. A field that a requirement lists is due before submission. A nested field marked required applies only when you send its parent object.

**X-Idempotency-Key** `string` *required*

A unique key you generate for each write, 16-64 printable ASCII characters long. A Universally Unique Identifier (UUID) works. A retry with the same key within 24 h returns the original response instead of acting twice. Know more about [idempotency](https://razorpay.com/docs/api/partners/accounts#idempotency).

**statement\_descriptor** `object`

The brand name customers see on their bank statements and receipts.

**statement\_descriptor.value** `string` *required*

The brand name customers see on their bank statements and receipts, so they recognise the charge. Maximum length: 255 characters.

**user** `object`

Corrects the owner's email or phone while it is unverified.

**user.email** `string`

The corrected email. Maximum length: 255 characters.

**user.phone** `string`

The corrected phone: +91 followed by 10 digits. Pattern: `^\+91[0-9]{10}$`.

**phone\_otp** `string`

The code from `send_phone_otp`, which verifies the phone. A wrong code returns `200`, and `phone_otp` stays due. An expired code or 3 wrong tries bring `send_phone_otp` back. Pattern: `^[0-9]{6}$`.

**email\_otp** `string`

The code from `send_email_otp`, which verifies the email. A wrong code returns `200`, and `email_otp` stays due. An expired code or 3 wrong tries bring `send_email_otp` back. Pattern: `^[0-9]{6}$`.

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

**business\_profile.identity\_numbers.business\_pan** `object`

The PAN of the business.

**business\_profile.identity\_numbers.business\_pan.value** `string`

The business PAN, 10 characters long: 5 letters, 4 digits and a letter.

**business\_profile.identity\_numbers.gstin** `object`

The Goods and Services Tax Identification Number (GSTIN). One per account: the GSTIN this account trades under. A business registered for GST in several states sends the GSTIN for this account. It sends that registration's address as `operational_address`.

**business\_profile.identity\_numbers.gstin.value** `string`

The GSTIN of the business.

**business\_profile.identity\_numbers.udyam\_registration** `object`

Udyam registration number.

**business\_profile.identity\_numbers.udyam\_registration.value** `string`

The Udyam registration number of the business.

**business\_profile.identity\_numbers.cin** `object`

The Corporate Identification Number (CIN).

**business\_profile.identity\_numbers.cin.value** `string`

The CIN of the company.

**business\_profile.documents** `object`

The business's KYC documents, keyed by document type. Attach each document by its `id` or `url`.

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

**business\_profile.documents.\<document\_type>.id** `string`

The ID of a document uploaded with [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md), once the account exists. Send either `id` or `url`.

**business\_profile.documents.\<document\_type>.url** `string`

A link Razorpay downloads the file from, in place of an upload. Send a pre-signed https link, valid for at least 15 min and never a public object. Razorpay downloads it once and keeps its own copy. Sending a link is coming soon. Until then, [upload the file](https://razorpay.com/docs/api/partners/accounts/upload-document.md) and send its `id` with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md).

**business\_profile.business\_category** `object`

How the business is classified. Send the category and its subcategory together. Razorpay derives the Merchant Category Code (MCC) from the subcategory.

**business\_profile.business\_category.category** `string`

The business category, from the requirement's `options`.

**business\_profile.business\_category.subcategory** `string`

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

**business\_profile.authorized\_person.identity\_numbers** `object`

The person's identifiers keyed by type.

**business\_profile.authorized\_person.identity\_numbers.individual\_pan** `object`

The PAN of a person: the authorised person, a stakeholder, an individual or a proprietor.

**business\_profile.authorized\_person.identity\_numbers.individual\_pan.value** `string`

The person's PAN, 10 characters long: 5 letters, 4 digits and a letter.

**business\_profile.authorized\_person.identity\_numbers.individual\_ckyc** `object`

The person's Central KYC Records Registry (CKYC) record. Its `value` is `null`. Send the code from `send_ckyc_otp` in `otp` and its request ID in `request_id`.

**business\_profile.authorized\_person.identity\_numbers.individual\_ckyc.is\_skipped** `boolean`

Send `true` to skip the CKYC record. The proof of address is then due instead. Default: `false`.

**business\_profile.authorized\_person.identity\_numbers.individual\_ckyc.otp** `string`

The code that `send_ckyc_otp` sent to the mobile on the CKYC record. Send it with `request_id`. Responses do not return it. Pattern: `^[0-9]{6}$`.

**business\_profile.authorized\_person.identity\_numbers.individual\_ckyc.request\_id** `string`

The request ID that came with the code, in the `request_id` output of `send_ckyc_otp`. Send it with `otp`. Responses do not return it.

**business\_profile.authorized\_person.documents** `object`

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

**business\_profile.authorized\_person.documents.\<document\_type>.id** `string`

The ID of a document uploaded with [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md), once the account exists. Send either `id` or `url`.

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

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers** `object`

The person's identifiers keyed by type.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.individual\_pan** `object`

The PAN of a person: the authorised person, a stakeholder, an individual or a proprietor.

**business\_profile.stakeholders.\<stakeholder\_id>.identity\_numbers.individual\_pan.value** `string`

The person's PAN, 10 characters long: 5 letters, 4 digits and a letter.

**business\_profile.stakeholders.\<stakeholder\_id>.documents** `object`

The person's KYC documents keyed by document type.

**business\_profile.stakeholders.\<stakeholder\_id>.documents.\<document\_type>** `object`

A KYC document of the stakeholder, keyed by its type, such as `aadhaar_front`.

**business\_profile.stakeholders.\<stakeholder\_id>.documents.\<document\_type>.id** `string`

The ID of a document uploaded with [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md), once the account exists. Send either `id` or `url`.

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

**bank\_accounts.settlements\_primary.supporting\_document.id** `string`

The ID of a document uploaded with [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md), once the account exists. Send either `id` or `url`.

**bank\_accounts.settlements\_primary.supporting\_document.url** `string`

A link Razorpay downloads the file from, in place of an upload. Send a pre-signed https link, valid for at least 15 min and never a public object. Razorpay downloads it once and keeps its own copy.

**products** `object`

Changes to products, keyed by product type.

**products.payment\_gateway** `object`

Changes to the `payment_gateway` product, which accepts payments on websites and apps.

**products.payment\_gateway.payment\_channels** `object`

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

**products.payment\_gateway.terms\_of\_service\_acceptance** `object`

The sub-merchant's acceptance of Razorpay's terms of service. Sending it submits the product. Show Razorpay's terms of service to the sub-merchant and let the sub-merchant accept in your user interface. Then send the IP address and device fingerprint of that acceptance.

**products.payment\_gateway.terms\_of\_service\_acceptance.ip** `string` *required*

The IP address the sub-merchant accepted from.

**products.payment\_gateway.terms\_of\_service\_acceptance.device\_fingerprint\_id** `string` *required*

The device fingerprint of the sub-merchant's device.

**products.payment\_gateway.clarification\_responses** `object`

The sub-merchant's text replies to the points a reviewer flagged in `needs_clarification`. A point that takes a reply lists a `clarify_…` sub-requirement. Send each reply under the path of what it answers, which is that sub-requirement's `field_path` without the `products.payment_gateway.clarification_responses.` prefix. For example, `{ "products": { "payment_gateway": { "clarification_responses": { "bank_accounts.settlements_primary": "…" } } } }`. The account returns the replies in this field.

**products.payment\_gateway.clarification\_responses.\<field\_path>** `string`

One reply, under the path of what it answers. Length: 50-300 characters.

**products.payment\_gateway.submit\_clarification** `boolean`

Send `true` in a call of its own to return the product to review. Send it once every flagged point on this product is answered and `submit_clarification` is due.

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
* `udyam_registration`: Udyam registration number.
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

The business's KYC documents, keyed by document type. Attach each document by its `id` or `url`.

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

> [accordion] A required header is missing.
>
> **Code:** `400`
>
> **Reason:** `missing_header`
>
> `X-Idempotency-Key` is missing or is not 16-64 printable ASCII characters.
>
> **Solution:** Send `X-Idempotency-Key` with 16-64 printable ASCII characters. `metadata.header` names the header.

> [accordion] The request is missing a required field.
>
> **Code:** `400`
>
> **Reason:** `invalid_request`
>
> The request has one of these problems:
>
> * The body is empty or is not JSON.
> * A key is not one that this endpoint takes, such as a misspelled field or a read-only one like `verification`.
> * `terms_of_service_acceptance` lacks `ip` or `device_fingerprint_id`.
> * `terms_of_service_acceptance` has a key other than `ip` and `device_fingerprint_id`.
> * `business_name` is sent for an individual, whose name comes from the PAN.
>
> **Solution:** Send valid JSON with only the keys this endpoint takes. Send `ip` and `device_fingerprint_id` in `terms_of_service_acceptance`. Do not send `business_name` for an individual.

> [accordion] The value isn't in the right format.
>
> **Code:** `400`
>
> **Reason:** `invalid_format`
>
> A value does not match its format. The value is one of these:
>
> * An identifier, account number, IFSC, PIN code or date
> * An OTP that is not 6 digits
> * A `clarification_responses` reply under 50 or over 300 characters
> * A `percentage_ownership` outside 0-100
>
> A well-formed code that is wrong or expired is not an error. It returns `200`. A wrong code stays due. An expired code brings its send action back.
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
> * `business_type`, `routing_code_type` or a business-model answer
> * A document key that is not a document type
> * A key under `products` for a product the account does not hold
> * An uploaded document attached under a key of another type, named in `metadata.expected_type`
>
> **Solution:** Send one of the allowed values. `metadata.allowed_values` lists them when the list is short.

> [accordion] This detail isn't needed yet.
>
> **Code:** `400`
>
> **Reason:** `step_not_due`
>
> The value is not due yet or is not due at all. The value is one of these:
>
> * A bank account sent before the business type
> * A value that depends on one not verified yet
> * `phone_otp` or `email_otp` for a contact that is verified
> * A reply in `clarification_responses` to a point that does not offer one
> * `submit_clarification` while points are still open
>
> Razorpay applies values in order, so it saves the earlier ones in the body. `metadata.due` lists what is due.
>
> **Solution:** Send only what the requirements list. `metadata.due` lists what is due now.

> [accordion] The document couldn't be downloaded from the link.
>
> **Code:** `400`
>
> **Reason:** `invalid_document_url`
>
> A document `url` has one of these problems:
>
> * It is not https.
> * It points or redirects to a private, loopback or cloud-metadata address.
> * Razorpay could not download it.
> * The file failed the upload checks.
>
> **Solution:** Send a pre-signed https link that Razorpay can download, valid for at least 15 min. Alternatively, upload the file with [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md) and send its ID.

> [accordion] This request conflicts with an earlier one.
>
> **Code:** `400`
>
> **Reason:** `idempotency_key_reused`
>
> You used this `X-Idempotency-Key` in the last 24 h with a different body or file.
>
> **Solution:** Send a new `X-Idempotency-Key` for a different request. Reuse a key only to retry the same request.

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

> [accordion] The requested resource doesn't exist.
>
> **Code:** `404`
>
> **Reason:** `not_found`
>
> A document `id` is not a document of this account or was deleted.
>
> **Solution:** Check the ID in `error.field`. Use the ID of a document on this account that is not deleted.

> [accordion] The earlier request is still being processed.
>
> **Code:** `409`
>
> **Reason:** `idempotency_in_progress`
>
> A request with this `X-Idempotency-Key` is still running. Razorpay stores its result only when it finishes.
>
> **Solution:** Wait for the time in the `Retry-After` header, then retry with the same key.

> [accordion] This detail can't be changed at this stage.
>
> **Code:** `409`
>
> **Reason:** `field_locked`
>
> The value cannot change at this stage. The value is one of these:
>
> * The KYC details while a product is in review (`under_review` or `edd_pending`) or activated
> * Anything not listed in `requirements` during `needs_clarification`
> * `business_type` once the PAN is verified
> * The owner's email or phone once verified
> * Anything on a `rejected` product
>
> The KYC details are the business profile, the authorised person, the stakeholders and the bank account. After activation, a few details can change after a manual review. Know more about [account management](https://razorpay.com/docs/partners/aggregators/onboarding-api/account-management.md).
>
> **Solution:** Tell the sub-merchant that this detail cannot change now. `metadata.status` names the status that locks it.

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
