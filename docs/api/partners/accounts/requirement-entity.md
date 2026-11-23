> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Requirement Entity

> Know about requirement entity parameters and their description.

Available in
🇮🇳 India

A requirement is something a product still needs from the sub-merchant. Each product lists its requirements in `products.<product_type>.requirements`. Razorpay computes them on every call. Show each requirement's `description` to the sub-merchant. Answer it as its `requirement_type` says.

```json Entity theme={null}
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
}
```

The Requirement entity has the following parameters:

**id** `string`

Unique identifier of this requirement node, `req_`-prefixed.

**requirement\_code** `string`

A stable, machine-readable identifier that names what a requirement is. For an `action`, it is the action's name. See [Requirement Codes](#requirement-codes).

**requirement\_level** `string`

How much the product needs it. Possible values:

* `mandatory`: You cannot submit the product without it. A sub-requirement of an `all_of` is `mandatory` unless it is `optional`.
* `conditional`: Needed only in some cases and specific business type. For example, for business type Trust, if the merchant has Trust Registration Certificate, the Trust Registration Certificate must be uploaded during onboarding.
* `optional`: Not needed to submit the product, such as an address's second line.

**requirement\_type** `string`

What the requirement is, which decides the other keys it carries. Possible values:

* `input`: Send a value or a document at `field_path` with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md). Carries `field_path` and `value_type`.
* `action`: Run the action named in `requirement_code` with [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md), such as `send_ckyc_otp`.
* `composite`: A requirement that groups other requirements in `sub_requirements`. It is fulfilled when its child requirements satisfy its `fulfillment_criteria` (`one_of`, `any_of` or `all_of`). It collects no value of its own.

**description** `string`

A sentence to show the sub-merchant.

**requirement\_reason** `string`

Why the requirement was raised, such as a reviewer's reason in `needs_clarification` or a failed check. Present only when a review or a check raised the requirement.

**field\_path** `string`

Only on `input`. Where to send the value in an update, as a dot path, such as `business_profile.authorized_person.identity_numbers.individual_pan`. For a stakeholder, the path names the stakeholder: `business_profile.stakeholders.<stakeholder_id>.…`. For an address, the path picks the list item by its `type`: `business_profile.addresses[type=registered_address].line1`.

**value\_type** `string`

Only on `input`. What the input takes. Possible values:

* `text`: A value, such as a PAN number.
* `enum`: One of `options`, such as a business type.
* `multi_select`: One or more of `options`, sent as an array, such as the answer to a business-model question.
* `boolean`: `true` or `false`, such as `is_skipped` to skip the Central KYC Records Registry (CKYC) record.
* `document`: A file: an uploaded document's `id` or a `url` for Razorpay to download.

**response** `object`

The response submitted for this requirement.

**response.text** `string`

The answer to a `text` input.

**response.documents** `array`

The files that answer a `document` input. Know more about the [Document entity](https://razorpay.com/docs/api/partners/accounts/document-entity.md).

**response.created\_at** `integer`

Time at which the response was first submitted, as a Unix timestamp in seconds.

**response.updated\_at** `integer`

Time at which the response last changed, as a Unix timestamp in seconds.

**response.metadata** `object`

Details of the response. `{}` when it has none.

**options** `array`

Only on an `input` with `value_type` `enum` or `multi_select`. The choices.

**options\[].label** `string`

The text to show.

**options\[].value** `string`

The value to send.

**fulfillment\_criteria** `string`

Only on `composite`. How its `sub_requirements` answer it. Possible values:

* `one_of`: Answer any one sub-requirement, such as one proof of address.
* `any_of`: Answer one or more sub-requirements.
* `all_of`: Answer every `mandatory` sub-requirement, such as both sides of a document.

**sub\_requirements** `array`

Only on `composite`. The requirements that answer it. A sub-requirement can itself be a `composite`, so each item has the same keys as this entity.

**status** `string`

Where the requirement stands. Possible values:

* `created`: The requirement has been raised.
* `needs_clarification`: A reviewer needs more information to validate the requirement.
* `under_review`: The response is submitted and Razorpay is evaluating it.
* `resolved`: The requirement is satisfied and closed.
* `overdue`: The requirement was not fulfilled by its `due_at` deadline.
* `rejected`: The submitted response was reviewed and not accepted.
* `expired`: The requirement lapsed and is no longer actionable.
* `cancelled`: The requirement was withdrawn. No response is needed.

**due\_at** `integer`

The deadline to fulfil the requirement, as a Unix timestamp in seconds. Present only when the requirement has a deadline.

**metadata** `object`

An optional, free-form object of key-value pairs for extensibility on any requirement. It carries more context or configuration, such as what an action needs on an action requirement, without changing the requirement schema.

## Keys per Requirement Type

A requirement carries only the keys its `requirement_type` uses. Every requirement carries `id`, `requirement_code`, `requirement_level`, `requirement_type`, `description` and `status`. It adds `requirement_reason` when a review or a check raised it and `due_at` when it has a deadline.

The table below lists the keys each type adds and how to answer it:

| `requirement_type` | Keys it adds | How to answer it |
| - | - | - |
| `input` | `field_path` and `value_type`. Also `response` once answered, `options` for a choice and `metadata` when it has any. | Send a value or a document at `field_path` with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md). |
| `action` | `metadata` when it has any. A link the action creates is only in the [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md) response. | Run the action named in `requirement_code`, such as `send_ckyc_otp`, with [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md). |
| `composite` | `fulfillment_criteria` and `sub_requirements`. Also `metadata` when it has any. | Answer its `sub_requirements` as `fulfillment_criteria` says. A sub-requirement can itself be a composite. |

## Composite Requirements

A composite requirement is fulfilled when its child requirements satisfy the node's `fulfillment_criteria` (`one_of`, `any_of` or `all_of`). With `one_of`, answer any one sub-requirement. With `any_of`, answer one or more. With `all_of`, answer every `mandatory` sub-requirement.

The table below lists the inputs and actions inside each composite requirement, with the path to send each input at:

| Composite | `requirement_code` | `value_type` | `field_path` |
| - | - | - | - |
| `ckyc_fetch` | `skip_ckyc` | `boolean` | `business_profile.authorized_person.identity_numbers.individual_ckyc.is_skipped` |
| `ckyc_fetch` | `send_ckyc_otp` | None. It is an action. | Run the action. |
| `individual_pan` | `individual_pan_number` | `text` | `business_profile.authorized_person.identity_numbers.individual_pan` |
| `individual_pan` | `individual_pan_card` | `document` | `business_profile.authorized_person.documents.individual_pan_document` |
| `business_pan` | `business_pan_number` | `text` | `business_profile.identity_numbers.business_pan` |
| `business_pan` | `business_pan_card` | `document` | `business_profile.documents.business_pan` |
| `proof_of_address_for_individual` | `create_aadhaar_digilocker_link` | None. It is an action. | Run the action. |
| `proof_of_address_for_individual` | `poa_aadhaar_front` | `document` | `business_profile.authorized_person.documents.aadhaar_front` |
| `proof_of_address_for_individual` | `poa_aadhaar_back` | `document` | `business_profile.authorized_person.documents.aadhaar_back` |
| `proof_of_address_for_individual` | `poa_passport_front` | `document` | `business_profile.authorized_person.documents.passport_front` |
| `proof_of_address_for_individual` | `poa_passport_back` | `document` | `business_profile.authorized_person.documents.passport_back` |
| `proof_of_address_for_individual` | `poa_voter_id_front` | `document` | `business_profile.authorized_person.documents.voter_id_front` |
| `proof_of_address_for_individual` | `poa_voter_id_back` | `document` | `business_profile.authorized_person.documents.voter_id_back` |
| `business_identity` | `cin` | `text` | `business_profile.identity_numbers.cin` |
| `business_identity` | `certificate_of_incorporation` | `document` | `business_profile.documents.certificate_of_incorporation` |
| `proof_of_business` | `gst_certificate` | `document` | `business_profile.documents.gst_certificate` |
| `proof_of_business` | `udyam_registration_certificate` | `document` | `business_profile.documents.udyam_registration_certificate` |
| `proof_of_business` | `shop_establishment` | `document` | `business_profile.documents.shop_establishment` |
| `proof_of_business` | `gstin` | `text` | `business_profile.identity_numbers.gstin` |
| `proof_of_business` | `udyam_registration` | `text` | `business_profile.identity_numbers.udyam_registration` |
| `bank_account` | `bank_account_number` | `text` | `bank_accounts.settlements_primary.account_number` |
| `bank_account` | `bank_routing_code` | `text` | `bank_accounts.settlements_primary.routing_code` |
| `bank_account` | `bank_routing_code_type` | `enum` | `bank_accounts.settlements_primary.routing_code_type` |
| `bank_account` | `create_upi_link` | None. It is an action. | Run the action. |
| `bank_account` | `clarify_bank_account` | `text` | `products.payment_gateway.clarification_responses.bank_accounts.settlements_primary` |
| `settlement_bank_account` | `bank_account_number` | `text` | `bank_accounts.settlements_primary.account_number` |
| `settlement_bank_account` | `bank_routing_code` | `text` | `bank_accounts.settlements_primary.routing_code` |
| `settlement_bank_account` | `bank_routing_code_type` | `enum` | `bank_accounts.settlements_primary.routing_code_type` |
| `website` | `website_url` | `text` | `products.payment_gateway.payment_channels.website.primary` |
| `website` | `clarify_website` | `text` | `products.payment_gateway.clarification_responses.products.payment_gateway.payment_channels.website.primary` |
| `payment_channels` | `website_url` | `text` | `products.payment_gateway.payment_channels.website.primary` |
| `payment_channels` | `app_android_url` | `text` | `products.payment_gateway.payment_channels.app_android.url` |
| `payment_channels` | `app_ios_url` | `text` | `products.payment_gateway.payment_channels.app_ios.url` |
| `accept_terms_of_service` | `acceptance_ip` | `text` | `products.payment_gateway.terms_of_service_acceptance.ip` |
| `accept_terms_of_service` | `acceptance_device_fingerprint_id` | `text` | `products.payment_gateway.terms_of_service_acceptance.device_fingerprint_id` |
| `business_model_clarifications` | `<question_id>` | Set by the question's `bmc_input_type`. | `business_profile.business_category.business_model_clarifications.<question_id>.answer` |
| `registered_address` | `address_line1` | `text` | `business_profile.addresses[type=registered_address].line1` |
| `registered_address` | `address_line2` (optional) | `text` | `business_profile.addresses[type=registered_address].line2` |
| `registered_address` | `address_city` | `text` | `business_profile.addresses[type=registered_address].city` |
| `registered_address` | `address_state` | `text` | `business_profile.addresses[type=registered_address].state` |
| `registered_address` | `address_postal_code` | `text` | `business_profile.addresses[type=registered_address].postal_code` |
| `registered_address` | `address_country` | `enum` | `business_profile.addresses[type=registered_address].country` |
| `operational_address` | `address_line1` | `text` | `business_profile.addresses[type=operational_address].line1` |
| `operational_address` | `address_line2` (optional) | `text` | `business_profile.addresses[type=operational_address].line2` |
| `operational_address` | `address_city` | `text` | `business_profile.addresses[type=operational_address].city` |
| `operational_address` | `address_state` | `text` | `business_profile.addresses[type=operational_address].state` |
| `operational_address` | `address_postal_code` | `text` | `business_profile.addresses[type=operational_address].postal_code` |
| `operational_address` | `address_country` | `enum` | `business_profile.addresses[type=operational_address].country` |
| `authorized_person` | `authorized_person_name` | `text` | `business_profile.authorized_person.name` |
| `authorized_person` | `individual_pan_number` | `text` | `business_profile.authorized_person.identity_numbers.individual_pan` |
| `authorized_person` | `individual_pan_card` | `document` | `business_profile.authorized_person.documents.individual_pan_document` |

## Requirement Codes

`requirement_code` comes from a closed list. Branch on it. For an `action`, it is the action's name. Each business-model question adds one code, the question's ID, such as `bmc_question_31` or the follow-up `bmc_question_13_1_1`, that matches `^bmc_question_[0-9_]+$`. Its `description` is the question.

Codes are unique among the sub-requirements of one composite. The same input can sit under 2 composites with the same code, such as `gstin`.

The table below lists requirement codes and the description each requirement carries:

| `requirement_code` | Description |
| - | - |
| `date_of_establishment` | The date your business was established. |
| `proof_of_address_for_individual` | Verify the proof of address for an individual. It can be done through one of the multiple ways. |
| `poa_via_document_upload` | Upload both sides of the proof of address document. |
| `poa_via_aadhaar_documents` | Aadhaar: front and back. |
| `poa_aadhaar_front` | Front side of Aadhaar. |
| `poa_aadhaar_back` | Back side of Aadhaar. |
| `poa_via_passport_documents` | Passport: front and back. |
| `poa_passport_front` | Front side of the passport. |
| `poa_passport_back` | Back side of the passport. |
| `poa_via_voter_id_documents` | Voter ID: front and back. |
| `poa_voter_id_front` | Front side of the voter ID. |
| `poa_voter_id_back` | Back side of the voter ID. |
| `send_ckyc_otp` | A Central KYC record was found for your PAN. Get a code on the mobile on your CKYC record to fetch it. |
| `create_video_kyc_link` | Complete a short video call with a Razorpay agent to verify your identity and address. Keep your PAN card on hand. |
