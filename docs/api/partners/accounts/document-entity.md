> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Document Entity

> Know about document entity parameters and their description.

Available in
🇮🇳 India

A document is a KYC file stored for an account. The Documents APIs return it as below. It is either a file you uploaded with [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md) or the Aadhaar that Razorpay downloaded from the Central KYC Records Registry (CKYC).

```json Entity theme={null}
{
  "id": "file_Qx7Lm2Kd9Tz4Ab",
  "entity": "document",
  "type": "aadhaar_front",
  "url": null,
  "metadata": {
    "source": "upload",
    "file_name": "aadhaar-front.jpg",
    "mime_type": "image/jpeg",
    "size_bytes": 183422
  }
}
```

The Document entity has the following parameters:

**id** `string`

Unique identifier for the file, `file_` followed by 14 letters or digits.

**entity** `string`

Always `document`.

**type** `string`

The document type of the file. See [Document Types](#document-types).

**url** `string`

A signed link to download the file. Set only by [Fetch One Document](https://razorpay.com/docs/api/partners/accounts/fetch-document.md) with `include_signed_url=true`. Otherwise `null`. It is also `null` when Razorpay could not create the link.

**metadata** `object`

About the stored file.

**metadata.source** `string`

Where the file came from. Possible values:

* `upload`: You uploaded it.
* `ckyc`: Razorpay downloaded it from the CKYC record.

**metadata.file\_name** `string`

The file name as you sent it.

**metadata.mime\_type** `string`

The format Razorpay detected from the file content, such as `image/jpeg`. It can be `null`.

**metadata.size\_bytes** `integer`

File size in bytes. It can be `null`.

## Document Types

[Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md) accepts these 186 values for `type`. The person's PAN card is `individual_pan_document`. `individual_pan` is the PAN number, sent in `identity_numbers`.

| | | |
| - | - | - |
| `aadhaar_back` | `aadhaar_front` | `aadhaar_xml` |
| `aadhaar_zip` | `address_proof_url` | `affiliation_certificate` |
| `ajl_license_or_proof_of_membership_with_dsam` | `alcohol_doc` | `alcohol_license` |
| `amfi_certificate` | `aoa` | `article_of_association` |
| `authorized_signatory_credence_report` | `ayush_certificate` | `bank_statement` |
| `bank_statement_inward_remittance` | `bank_verification_letter` | `bar_council_certificate` |
| `bar_council_document` | `bbps_document` | `bis_certificate` |
| `bmc_question_10_2_doc` | `bmc_question_10_3_doc` | `bmc_question_10_4_doc` |
| `bmc_question_10_5_doc` | `bmc_question_11_3_doc` | `bmc_question_12_2_doc` |
| `bmc_question_13_1_1_3_doc` | `bmc_question_19_1_1_1_doc` | `bmc_question_24_1_doc` |
| `bmc_question_29_2_doc` | `bmc_question_34_1_doc` | `bmc_question_34_2_doc` |
| `bmc_question_36_1_doc` | `bmc_question_37_2_doc` | `bmc_question_4_1_doc` |
| `bmc_question_7_1_doc` | `bmc_question_7_2_doc` | `bmc_question_7_4_1_1_doc` |
| `bmc_question_7_4_doc` | `bmc_question_9_3_doc` | `bnm_license` |
| `bnm_or_sc_license` | `board_resolution` | `board_resolution_letter` |
| `brand_tie_up_document` | `business_correspondent` | `business_correspondent_document` |
| `business_operation_proof_url` | `business_pan_url` | `business_proof_url` |
| `cancelled_cheque` | `cancelled_cheque_video` | `coi_document` |
| `copywrite_license` | `cpv_report` | `current_payment_partner_settlement_record` |
| `custom_device_charges_proof` | `custom_pricing_proof` | `dealership_rights_certificate` |
| `dgca_certificate` | `domain_ownership_document` | `dot_certificate` |
| `driver_license_back` | `driver_license_front` | `emerchantpay_aadhaar` |
| `emerchantpay_gst_certificate` | `emerchantpay_pan` | `emerchantpay_passport` |
| `emerchantpay_proof_of_ownership` | `epf_scheme_certificate` | `experian_bi_report` |
| `experian_bp_report` | `experian_ci_report` | `experian_cp_report` |
| `experian_ocrfro_face_image` | `experian_ocrfro_id_image` | `fda_certificate` |
| `fda_license` | `ffmc_license` | `fimm_or_bnm_registration_form` |
| `fimm_or_sc_registration_form` | `firc` | `firs_file` |
| `firs_firstdata_file` | `firs_firstdata_sum_file` | `firs_icici_file` |
| `firs_icici_zip` | `firs_zip` | `form_10ac` |
| `form_12a_url` | `form_20_20b_21_21b` | `form_80g_url` |
| `form_8a` | `fssai_certificate` | `fssai_license` |
| `gaming_addendum` | `gazette_notification` | `gia_certificate` |
| `gii_certificate` | `govt_authorisation_letter` | `gst_certificate` |
| `huf_deed` | `iata_certificate` | `iato_license` |
| `ic_document_back` | `ic_document_front` | `iec_license` |
| `import_export_certificate` | `individual_pan_document` | `invoice` |
| `invoices` | `irctc_agent_agreement` | `irda_certificate` |
| `irdai_registration_certificate` | `lba_certificate` | `legal_opinion` |
| `legal_opinion_document` | `lesen_pemegang_pajak_gadai` | `letter_of_authorization` |
| `license_from_ministry_of_education` | `license_from_ministry_of_housing_and_local_government` | `license_or_permit_from_ministry_of_health` |
| `license_or_permit_under_the_poisons_act_1952` | `liquor_license` | `listing_on_ministry_of_healths_website` |
| `manufacturing_license` | `memorandum_of_association` | `merchant_agreement` |
| `merchant_service_agreement` | `mmtc_pamp_license` | `moa` |
| `motac_license` | `mso_document` | `nach` |
| `national_housing_bank_certificate` | `nbfc_registration_certificate` | `other` |
| `partnership_deed` | `partnership_registration_certificate` | `passport_back` |
| `passport_front` | `pci_dss_certificate` | `peso_license` |
| `pgi_certificate` | `pharmacy_drug_license` | `pm_wani_certificate` |
| `power_of_attorney` | `ppi_license` | `practicing_certificate` |
| `promoter_address_url` | `promoter_pan_url` | `promoter_proof_url` |
| `proof_of_profession` | `public_or_beer_house_license` | `rbi_certificate` |
| `registered_market_operator_screenshot` | `rera_license` | `reseller_agreement` |
| `safegold_partnership_document` | `sc_capital_markets_services_license` | `sebi_registration_certificate` |
| `shop_establishment` | `shop_front` | `shop_interior` |
| `sla_amfi_certificate` | `sla_dealership_agreement` | `sla_document` |
| `sla_ffmc_license` | `sla_iata_certificate` | `sla_irdai_registration_certificate` |
| `sla_nbfc_registration_certificate` | `sla_sebi_registration_certificate` | `society_registration_certificate` |
| `trade_license` | `trai_certificate` | `trust_deed` |
| `trust_registration_certificate` | `udyam_registration_certificate` | `undertaking` |
| `undertaking_document` | `utility_bill` | `voter_id_back` |
| `voter_id_front` | `website_screenshot` | `website_screenshots_additional` |

## Documents on the Account

An upload alone does not attach the file. To attach it, send its `id` in the matching `documents` key with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md), such as `{ "id": "file_Qx7Lm2Kd9Tz4Ab" }`. To share a document as a link instead, send its `url` in that key. Razorpay downloads the file and keeps its own copy. The Documents APIs never take a link.

Once attached, the document appears in the account's `documents` maps, such as `business_profile.documents`. It also appears in `supporting_document`. There, Razorpay also returns its check:

**business\_profile.documents.\<document\_type>.verification** `object`

The document's check. It is `null` until Razorpay checks the attached document.

**business\_profile.documents.\<document\_type>.verification.status** `string`

Where the check is. Possible values:

* `in_progress`: The check is running.
* `deferred`: The check could not conclude, so a reviewer decides after the product is submitted. The requirement clears and `error_code` is `null`.
* `verified`: The check passed.
* `rejected`: The check failed. `error_code` says why.
* `collected`: Razorpay has received the value and has not checked it yet.

**business\_profile.documents.\<document\_type>.verification.error\_code** `string`

A stable code for the failure, such as `bank_name_mismatch`, `pan_not_found` or `otp_invalid`. Razorpay never returns the bank's or registry's own record, such as the account holder's name. The code says what did not match. Know more about [failed-check codes](https://razorpay.com/docs/api/partners/accounts/errors.md#failed-check-codes).

**business\_profile.documents.\<document\_type>.verification.error\_description** `string`

A sentence to show the sub-merchant. The wording can change. It never repeats the value sent.

**business\_profile.documents.\<document\_type>.verification.verified\_at** `integer`

Time at which the check passed, as a Unix timestamp in seconds.

**business\_profile.documents.\<document\_type>.verification.metadata** `object`

Details of the check, where it has any. `{}` when the check has none.

**business\_profile.documents.\<document\_type>.verification.created\_at** `integer`

Time at which the check started, as a Unix timestamp in seconds.
