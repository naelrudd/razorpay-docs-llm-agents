> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Errors

> Know about the Accounts API errors and how to resolve them.

Available in
🇮🇳 India

The Accounts APIs use conventional HTTP status codes:

* `2xx`: Success
* `4xx`: A problem with the request or the sub-merchant's data
* `5xx`: A problem on Razorpay's side

Each endpoint page lists the errors it returns.

A value that fails verification is not an error. The call succeeds, the element's `verification` shows `rejected` with an `error_code` and its requirement is due again. See [Failed-Check Codes](#failed-check-codes).

## Error Object

Every error response carries the same envelope. Branch on `reason`, show `description` to the sub-merchant and use `field` to point at the value. Errors never repeat a value you sent.

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

The error object has the following parameters:

**error** `object`

The error details.

**error.code** `string`

The error class. Possible values:

* `BAD_REQUEST_ERROR`: Fix the request or the sub-merchant's data. Do not retry unchanged.
* `SERVER_ERROR`: A problem on Razorpay's side or a verification provider's. Retry the same request. It does not act twice.

**error.description** `string`

A sentence to show the sub-merchant. It never repeats a value you sent or anything Razorpay holds about the business. Neither does `metadata`. `field` names the value instead.

**error.source** `string`

Where the error came from, which decides what to do next. Possible values:

* `business`: Your request or the sub-merchant's data: a missing field or a bad format, such as `reason: invalid_format` at `step: validation`. Fix the request or ask the sub-merchant to correct the value, then send it again. Retrying unchanged fails the same way.
* `verification_provider`: A registry or bank that Razorpay calls did not answer. For example, the Central KYC Records Registry (CKYC) may not answer when an action sends a code. The call then returns `503` with `provider_unavailable`. Nothing is wrong with the data, so retry later. A check inside an update does not fail the call. Razorpay saves the value, and its `verification` shows `rejected` with a code such as `pan_check_unavailable`.
* `internal`: A problem inside Razorpay (`reason: internal_error`). Retry. A write retried with the same `X-Idempotency-Key` does not act twice.

**error.step** `string`

The onboarding step, such as `validation` (the request's own checks), `document_upload` or `ckyc_otp`.

**error.reason** `string`

A stable, machine-readable reason. Each endpoint page lists the reasons the endpoint returns and when. See [API Errors](#api-errors).

**error.field** `string`

The request field or account path the error is about.

**error.metadata** `object`

Structured hints, such as `allowed_values` on `invalid_option`. `{}` when the error has no hints.

## API Errors

Razorpay can add new reasons. Handle an unknown reason by its HTTP status.

> [accordion] The request is missing a required field.
>
> **Code:** `400`
>
> **Reason:** `invalid_request`
>
> The request has one of these problems:
>
> * The body is not valid JSON.
> * A required field is missing.
> * A key is not one the endpoint takes, such as a misspelled or read-only field.
>
> **Returned by:**
>
> * [Create an Account](https://razorpay.com/docs/api/partners/accounts/create.md)
> * [Fetch Accounts](https://razorpay.com/docs/api/partners/accounts/fetch.md)
> * [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md)
> * [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md)
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
>
> **Solution:** Send valid JSON with every required field. Remove any key the endpoint does not take, such as a misspelled or read-only field.

> [accordion] The value isn't in the right format.
>
> **Code:** `400`
>
> **Reason:** `invalid_format`
>
> A value does not match its format or range, such as:
>
> * A PAN that does not match its pattern
> * A phone that is not +91 and 10 digits
> * A count above 100
> * A `file_id` that is not `file_` followed by 14 letters or digits
> * An `X-Idempotency-Key` that is not 16-64 printable ASCII characters
>
> **Returned by:**
>
> * [Create an Account](https://razorpay.com/docs/api/partners/accounts/create.md)
> * [Fetch Accounts](https://razorpay.com/docs/api/partners/accounts/fetch.md)
> * [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md)
> * [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md)
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
> * [Fetch One Document](https://razorpay.com/docs/api/partners/accounts/fetch-document.md)
> * [Delete a Document](https://razorpay.com/docs/api/partners/accounts/delete-document.md)
>
> **Solution:** Correct the value named in `error.field` and send it again. `metadata.pattern` shows the expected format. `metadata.minimum` and `metadata.maximum` show the range.

> [accordion] Choose one of the allowed values.
>
> **Code:** `400`
>
> **Reason:** `invalid_option`
>
> A value is not one of the allowed options.
>
> **Returned by:**
>
> * [Create an Account](https://razorpay.com/docs/api/partners/accounts/create.md)
> * [Fetch Accounts](https://razorpay.com/docs/api/partners/accounts/fetch.md)
> * [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md)
> * [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md)
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
> * [Fetch All Documents](https://razorpay.com/docs/api/partners/accounts/fetch-all-documents.md)
>
> **Solution:** Send one of the allowed values. `metadata.allowed_values` lists them when the list is short.

> [accordion] A required header is missing.
>
> **Code:** `400`
>
> **Reason:** `missing_header`
>
> A required header is missing or malformed. `metadata.header` names it.
>
> **Returned by:**
>
> * [Create an Account](https://razorpay.com/docs/api/partners/accounts/create.md)
> * [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md)
> * [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md)
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
>
> **Solution:** Send the header named in `metadata.header`. On a write, send `X-Idempotency-Key` with 16-64 printable ASCII characters.

> [accordion] This detail isn't needed yet.
>
> **Code:** `400`
>
> **Reason:** `step_not_due`
>
> The value or action is not due yet or not due at all. An example is a bank account sent before the business type.
>
> **Returned by:**
>
> * [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md)
> * [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md)
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
> * It points at, or redirects to, a private, loopback or cloud-metadata address.
> * Razorpay could not download it.
> * The file fails the upload checks.
>
> **Returned by:**
>
> * [Create an Account](https://razorpay.com/docs/api/partners/accounts/create.md)
> * [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md)
>
> **Solution:** Send a pre-signed https link that Razorpay can download, valid for at least 15 min. Or upload the file with [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md) and attach its ID with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md).

> [accordion] The file can't be read. Upload it again.
>
> **Code:** `400`
>
> **Reason:** `invalid_file`
>
> Razorpay cannot read the file. For example, the PDF is truncated or corrupt.
>
> **Returned by:**
>
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
>
> **Solution:** Check that the file is complete and readable, then upload it again.

> [accordion] The file name isn't allowed.
>
> **Code:** `400`
>
> **Reason:** `invalid_file_name`
>
> The file name has characters that are not allowed, such as a path separator or a control character.
>
> **Returned by:**
>
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
>
> **Solution:** Rename the file without path separators or control characters, then upload it again.

> [accordion] The file name is too long.
>
> **Code:** `400`
>
> **Reason:** `file_name_too_long`
>
> The file name is longer than 255 characters.
>
> **Returned by:**
>
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
>
> **Solution:** Shorten the file name to 255 characters or fewer, then upload it again.

> [accordion] Upload the file without a password.
>
> **Code:** `400`
>
> **Reason:** `password_protected_file`
>
> The file is password protected.
>
> **Returned by:**
>
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
>
> **Solution:** Remove the password from the file, then upload it again.

> [accordion] This request conflicts with an earlier one.
>
> **Code:** `400`
>
> **Reason:** `idempotency_key_reused`
>
> You used this `X-Idempotency-Key` in the last 24 h with a different body. For an upload, the key is bound to its `type` and file for 1 h.
>
> **Returned by:**
>
> * [Create an Account](https://razorpay.com/docs/api/partners/accounts/create.md)
> * [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md)
> * [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md)
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
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
> **Returned by:** Every endpoint.
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
> **Returned by:** Every endpoint.
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
> **Returned by:** Every endpoint.
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
> **Returned by:**
>
> * [Fetch Accounts](https://razorpay.com/docs/api/partners/accounts/fetch.md)
> * [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md)
> * [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md)
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
> * [Fetch All Documents](https://razorpay.com/docs/api/partners/accounts/fetch-all-documents.md)
> * [Fetch One Document](https://razorpay.com/docs/api/partners/accounts/fetch-document.md)
> * [Delete a Document](https://razorpay.com/docs/api/partners/accounts/delete-document.md)
>
> **Solution:** Stop calling this account and update your records. Calls on it never succeed again for your platform.

> [accordion] The requested resource doesn't exist.
>
> **Code:** `404`
>
> **Reason:** `not_found`
>
> The resource does not exist or the account is not mapped to your app in this mode. Both look the same, so an ID cannot reveal who banks with Razorpay. `field` names the ID.
>
> **Returned by:**
>
> * [Fetch Accounts](https://razorpay.com/docs/api/partners/accounts/fetch.md)
> * [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md)
> * [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md)
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
> * [Fetch All Documents](https://razorpay.com/docs/api/partners/accounts/fetch-all-documents.md)
> * [Fetch One Document](https://razorpay.com/docs/api/partners/accounts/fetch-document.md)
> * [Delete a Document](https://razorpay.com/docs/api/partners/accounts/delete-document.md)
>
> **Solution:** Check the ID in `error.field`. Use the ID of an account or document of your app, in the same mode as your key.

> [accordion] This detail can't be changed at this stage.
>
> **Code:** `409`
>
> **Reason:** `field_locked`
>
> The value cannot change in the product's current status. `field` names it and `metadata.status` is the status that locks it.
>
> **Returned by:**
>
> * [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md)
>
> **Solution:** Tell the sub-merchant that this detail cannot change now. `metadata.status` names the status that locks it.

> [accordion] The earlier request is still being processed.
>
> **Code:** `409`
>
> **Reason:** `idempotency_in_progress`
>
> A request with this `X-Idempotency-Key` is still running. Razorpay stores its result only when it finishes.
>
> **Returned by:**
>
> * [Create an Account](https://razorpay.com/docs/api/partners/accounts/create.md)
> * [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md)
> * [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md)
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
>
> **Solution:** Wait for the time in the `Retry-After` header, then retry with the same key.

> [accordion] The file is too large.
>
> **Code:** `413`
>
> **Reason:** `file_too_large`
>
> The file is larger than 20 MB. `metadata.max_bytes` is the limit.
>
> **Returned by:**
>
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
>
> **Solution:** Upload a file of 20 MB or less. `metadata.max_bytes` is the limit in bytes.

> [accordion] The file format is not accepted for this document type.
>
> **Code:** `415`
>
> **Reason:** `unsupported_media_type`
>
> The request has one of these problems:
>
> * The upload body is not `multipart/form-data`. `error.field` is `Content-Type`.
> * The file format is not accepted for its document type. Razorpay detects the format from the file content, not its name. `error.field` is `file`.
>
> **Returned by:**
>
> * [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
>
> **Solution:** Send the body as `multipart/form-data`. Upload the file in a format listed in `metadata.accept`. `metadata.detected_type` shows the format found.

> [accordion] Too many requests. Try again shortly.
>
> **Code:** `429`
>
> **Reason:** `rate_limited`
>
> Your app sent more requests than its rate limit allows.
>
> **Returned by:** Every endpoint.
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
> **Returned by:** Every endpoint.
>
> **Solution:** Retry the request. A write retried with the same `X-Idempotency-Key` does not act twice.

> [accordion] The verification service is busy. Try again in a few minutes.
>
> **Code:** `503`
>
> **Reason:** `provider_unavailable`
>
> A registry, bank or SMS or email provider that an action calls did not answer. Nothing ran and nothing is wrong with the request. Checks inside an update never fail the call this way.
>
> **Returned by:**
>
> * [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md)
>
> **Solution:** Retry after the time in the `Retry-After` header. Nothing is wrong with the request.

## Failed-Check Codes

A failed check does not fail the call. The element's `verification.status` is `rejected` with the code in `verification.error_code`. Its requirement comes back due, with a `requirement_reason`. Branch on the code and show `verification.error_description` to the sub-merchant.

Keep these points in mind:

* The link codes `link_expired`, `video_kyc_failed`, `digilocker_failed` and `upi_payment_failed` have no element to carry them. The action comes back due. Running it creates a new link.
* A phone or email One-Time Password (OTP) carries no failed-check code. After a wrong code, `phone_otp` or `email_otp` stays due. An expired code or 3 wrong tries bring back `send_phone_otp` or `send_email_otp`.
* Razorpay never returns the bank's or registry's own record, such as the account holder's name. The code says what did not match.

> [accordion] We couldn't find this PAN. Check the number, or upload the PAN card.
>
> **Error code:** `pan_not_found`
>
> **Check:** PAN
>
> The PAN registry has no such PAN or rejected it as invalid.
>
> **Fields:**
>
> * `business_profile.authorized_person.identity_numbers.individual_pan`
> * `business_profile.identity_numbers.business_pan`
> * `business_profile.stakeholders.<stakeholder_id>.identity_numbers.individual_pan`
>
> **Next step:** The PAN again, or the PAN card, as the options of one composite requirement.

> [accordion] This PAN belongs to someone other than the signatory. Send the signatory's own PAN.
>
> **Error code:** `pan_name_mismatch`
>
> **Check:** PAN
>
> The PAN exists, but its holder is not the signatory named for the company.
>
> **Fields:**
>
> * `business_profile.authorized_person.identity_numbers.individual_pan`
>
> **Next step:** The signatory's name and PAN again.

> [accordion] We couldn't check this PAN at the moment. Upload the PAN card instead.
>
> **Error code:** `pan_check_unavailable`
>
> **Check:** PAN
>
> The PAN registry did not answer or answered with an error. Nothing is wrong with the PAN.
>
> **Fields:**
>
> * `business_profile.authorized_person.identity_numbers.individual_pan`
> * `business_profile.identity_numbers.business_pan`
>
> **Next step:** The PAN card; or send the PAN again later.

> [accordion] Based on the date of birth linked to this PAN, you must be 18 years or older to register with Razorpay. If you believe this is an error, contact Razorpay support.
>
> **Error code:** `promoter_underage`
>
> **Check:** PAN
>
> The PAN holder is under 18.
>
> **Fields:**
>
> * `business_profile.authorized_person.identity_numbers.individual_pan`
> * `business_profile.authorized_person.documents.individual_pan_document`
>
> **Next step:** Nothing the platform can send clears it; the sub-merchant contacts Razorpay.

> [accordion] The PAN on this card doesn't match the PAN you entered. Upload the card for that PAN.
>
> **Error code:** `pan_card_mismatch`
>
> **Check:** PAN card
>
> The PAN printed on the card is not the PAN sent.
>
> **Fields:**
>
> * `business_profile.authorized_person.documents.individual_pan_document`
>
> **Next step:** The PAN card again.

> [accordion] The name on this PAN card doesn't match. Upload your own PAN card.
>
> **Error code:** `pan_card_name_mismatch`
>
> **Check:** PAN card
>
> The name on the card is not the owner's or signatory's.
>
> **Fields:**
>
> * `business_profile.authorized_person.documents.individual_pan_document`
>
> **Next step:** The PAN card again.

> [accordion] We couldn't read this PAN card. Upload a clear photo or scan of the front.
>
> **Error code:** `pan_card_name_unreadable`
>
> **Check:** PAN card
>
> Razorpay could not read a name or number off the card.
>
> **Fields:**
>
> * `business_profile.authorized_person.documents.individual_pan_document`
>
> **Next step:** The PAN card again.

> [accordion] This doesn't look like a PAN card. Upload the front of your PAN card.
>
> **Error code:** `not_a_pan_card`
>
> **Check:** PAN card
>
> The file is not a PAN card.
>
> **Fields:**
>
> * `business_profile.authorized_person.documents.individual_pan_document`
>
> **Next step:** The PAN card again.

> [accordion] The code didn't match. Try again, or request a new code.
>
> **Error code:** `otp_invalid`
>
> **Check:** CKYC code
>
> The CKYC code does not match the one sent.
>
> **Fields:**
>
> * `business_profile.authorized_person.identity_numbers.individual_ckyc`
>
> **Next step:** The corrected code in `otp`, with the same `request_id`: `ckyc_otp` and `ckyc_request_id` stay due.

> [accordion] This code has expired. Request a new code.
>
> **Error code:** `otp_expired`
>
> **Check:** CKYC code
>
> The CKYC code was right but has expired. A wrong code tried 3 times also expires.
>
> **Fields:**
>
> * `business_profile.authorized_person.identity_numbers.individual_ckyc`
>
> **Next step:** `send_ckyc_otp` again, for a new code: the send action is due again.

> [accordion] We couldn't fetch your KYC record. Upload a proof of address instead.
>
> **Error code:** `ckyc_unavailable`
>
> **Check:** CKYC
>
> Razorpay could not download the CKYC record, for a system reason.
>
> **Fields:**
>
> * `business_profile.authorized_person.identity_numbers.individual_ckyc`
>
> **Next step:** The proof of address (Aadhaar, passport or voter ID).

> [accordion] The name on this document doesn't match. Upload an address proof in your own name.
>
> **Error code:** `poa_name_mismatch`
>
> **Check:** Proof of address
>
> The address proof is not in the person's name.
>
> **Fields:**
>
> * `business_profile.authorized_person.documents.aadhaar_front`
> * `business_profile.authorized_person.documents.voter_id_front`
> * `business_profile.authorized_person.documents.passport_front`
> * `business_profile.stakeholders.<stakeholder_id>.documents.aadhaar_front`
> * `business_profile.stakeholders.<stakeholder_id>.documents.voter_id_front`
> * `business_profile.stakeholders.<stakeholder_id>.documents.passport_front`
>
> **Next step:** The proof of address again.

> [accordion] We couldn't read this document. Upload a clear photo or scan.
>
> **Error code:** `poa_unreadable`
>
> **Check:** Proof of address
>
> Razorpay could not read the address proof.
>
> **Fields:**
>
> * `business_profile.authorized_person.documents.aadhaar_front`
> * `business_profile.authorized_person.documents.voter_id_front`
> * `business_profile.authorized_person.documents.passport_front`
> * `business_profile.stakeholders.<stakeholder_id>.documents.aadhaar_front`
> * `business_profile.stakeholders.<stakeholder_id>.documents.voter_id_front`
> * `business_profile.stakeholders.<stakeholder_id>.documents.passport_front`
>
> **Next step:** The proof of address again.

> [accordion] The account must be in the name of your business. Please use a different account.
>
> **Error code:** `bank_name_mismatch`
>
> **Check:** Bank account
>
> The account holder's name does not match the PAN name or the business name.
>
> **Fields:**
>
> * `bank_accounts.settlements_primary`
>
> **Next step:** Another account, or a ₹1 UPI payment from it, as the options of one composite requirement.

> [accordion] The account number or IFSC is incorrect. Check the details and try again.
>
> **Error code:** `bank_details_incorrect`
>
> **Check:** Bank account
>
> The account number or Indian Financial System Code (IFSC) is wrong.
>
> **Fields:**
>
> * `bank_accounts.settlements_primary`
>
> **Next step:** The account again, or a ₹1 UPI payment from it.

> [accordion] This account cannot receive payments. Please use a different bank account.
>
> **Error code:** `bank_account_unusable`
>
> **Check:** Bank account
>
> The bank reported the account frozen, blocked, closed or Non-Resident External (NRE).
>
> **Fields:**
>
> * `bank_accounts.settlements_primary`
>
> **Next step:** A different account, or a ₹1 UPI payment from one.

> [accordion] We could not reach your bank to verify the account. Verify it with a ₹1 UPI payment from the account.
>
> **Error code:** `bank_check_unavailable`
>
> **Check:** Bank account
>
> Razorpay could not reach the bank. Nothing is wrong with the account.
>
> **Fields:**
>
> * `bank_accounts.settlements_primary`
>
> **Next step:** The `bank_account` composite requirement again: the account, or a ₹1 UPI payment from it.

> [accordion] We could not verify this account. Check the details and try again.
>
> **Error code:** `bank_not_verified`
>
> **Check:** Bank account
>
> Any other failure. Razorpay does not say why.
>
> **Fields:**
>
> * `bank_accounts.settlements_primary`
>
> **Next step:** The account again, or a ₹1 UPI payment from it.

> [accordion] This GSTIN is registered to a different business. Check the GSTIN, or send your Udyam number instead.
>
> **Error code:** `gstin_name_mismatch`
>
> **Check:** Goods and Services Tax Identification Number (GSTIN)
>
> The GSTIN is registered to another business.
>
> **Fields:**
>
> * `business_profile.identity_numbers.gstin`
>
> **Next step:** The GSTIN again, or the Udyam number.

> [accordion] We couldn't find this GSTIN. Check the number, or send your Udyam number instead.
>
> **Error code:** `gstin_not_found`
>
> **Check:** GSTIN
>
> The GST registry has no such GSTIN or the GSTIN is cancelled.
>
> **Fields:**
>
> * `business_profile.identity_numbers.gstin`
>
> **Next step:** The GSTIN again, or the Udyam number.

> [accordion] This Udyam number is registered to a different business. Check the number, or send your GSTIN instead.
>
> **Error code:** `udyam_name_mismatch`
>
> **Check:** Udyam number
>
> The Udyam registration is in another business's name.
>
> **Fields:**
>
> * `business_profile.identity_numbers.udyam_registration`
>
> **Next step:** The Udyam number again, or the GSTIN.

> [accordion] We couldn't find this Udyam number. Check the number, or send your GSTIN instead.
>
> **Error code:** `udyam_not_found`
>
> **Check:** Udyam number
>
> The Udyam registry has no such number.
>
> **Fields:**
>
> * `business_profile.identity_numbers.udyam_registration`
>
> **Next step:** The Udyam number again, or the GSTIN.

> [accordion] We couldn't open your website. Check that it's live, or share another one.
>
> **Error code:** `website_unreachable`
>
> **Check:** Website
>
> Razorpay could not open the website, or it is not live.
>
> **Fields:**
>
> * `products.payment_gateway.payment_channels.website.primary`
>
> **Next step:** The website again.

> [accordion] This link has expired. Run the action again for a new link.
>
> **Error code:** `link_expired`
>
> **Check:** Link
>
> The sub-merchant did not complete the step before `metadata.expires_at`.
>
> **Actions:**
>
> * `create_video_kyc_link`
> * `create_aadhaar_digilocker_link`
> * `create_upi_link`
>
> **Next step:** The action is due again: run it for a new link.

> [accordion] We couldn't complete your video KYC. Start a new call when you're ready.
>
> **Error code:** `video_kyc_failed`
>
> **Check:** Video KYC
>
> The agent could not verify the person on the call. For example, the face did not match the PAN photo or the call dropped.
>
> **Actions:**
>
> * `create_video_kyc_link`
>
> **Next step:** The action is due again: run it for a new call.

> [accordion] We didn't get your Aadhaar from DigiLocker. Try again, or upload a proof of address.
>
> **Error code:** `digilocker_failed`
>
> **Check:** DigiLocker
>
> The sub-merchant declined to share the Aadhaar in DigiLocker or DigiLocker returned no Aadhaar.
>
> **Actions:**
>
> * `create_aadhaar_digilocker_link`
>
> **Next step:** The action is due again: run it for a new link, or send a proof-of-address document, another option of the same composite requirement.

> [accordion] We couldn't verify the account from this payment. Pay from an account in your business's name, or share the account details.
>
> **Error code:** `upi_payment_failed`
>
> **Check:** UPI ₹1 payment
>
> The ₹1 payment failed or did not come from an account in the business's or owner's name.
>
> **Actions:**
>
> * `create_upi_link`
>
> **Next step:** The action is due again: run it for a new link, or send the account.

## Review Reasons

In `needs_clarification`, each point a reviewer flags comes back as a requirement, with the reviewer's reason in `requirement_reason`. Answer the requirements listed. Then send `submit_clarification` in a call of its own with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md).

> [accordion] A reviewer couldn't confirm that the payout account is held in your name. Share an account in your name, pay ₹1 from it, or reply.
>
> **Reason:** `bank_account_ownership_unconfirmed`
>
> **Flagged requirement:** `bank_account`
>
> The reviewer could not confirm that the business or its owner holds the settlement account.
>
> **Fields:**
>
> * `bank_accounts.settlements_primary`

> [accordion] The website doesn't list any products or prices yet. Share a website with your products and prices, or explain how customers will buy from you.
>
> **Reason:** `website_no_products`
>
> **Flagged requirement:** `website`
>
> The website does not list products or prices.
>
> **Fields:**
>
> * `products.payment_gateway.payment_channels.website.primary`

> [accordion] The website needs refund, cancellation and contact details. Add them, or explain how customers reach you.
>
> **Reason:** `website_policies_missing`
>
> **Flagged requirement:** `website`
>
> The website has no refund, cancellation or contact policy.
>
> **Fields:**
>
> * `products.payment_gateway.payment_channels.website.primary`

> [accordion] We couldn't confirm your business from this document. Upload a clear, current registration in the business's name.
>
> **Reason:** `business_proof_unclear`
>
> **Flagged requirement:** `proof_of_business`
>
> The registration document is unreadable, expired or in another name.
>
> **Fields:**
>
> * `business_profile.documents.<type>`

> [accordion] We couldn't read your proof of address. Upload both sides of an Aadhaar, voter ID or passport in your name, or use DigiLocker.
>
> **Reason:** `address_proof_unclear`
>
> **Flagged requirement:** `proof_of_address_for_individual`
>
> The proof of address is unreadable, cropped or in another name.
>
> **Fields:**
>
> * `business_profile.authorized_person.documents.<type>`

> [accordion] What your business sells doesn't match the category you chose. Pick the category that fits.
>
> **Reason:** `category_mismatch`
>
> **Flagged requirement:** None. The reviewer flags the business category.
>
> What the business sells does not match its category.
>
> **Fields:**
>
> * `business_profile.business_category`
