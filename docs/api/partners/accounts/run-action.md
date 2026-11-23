> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Run an Action

> Run a verification action on a sub-merchant account using Razorpay Accounts API.

Available in
🇮🇳 India

Use this endpoint to run an action on an account: send a One-Time Password (OTP) or create a link for the sub-merchant.

> [!NOTE]
>
> **Handy Tips**
>
> * Authenticate with the key and secret of your test pair or live pair. In the API playground, enter the test key as the username and its secret as the password. Use the live pair in live mode.
> * `metadata` returns the action's outputs as type and value pairs, such as the link or the masked number the OTP went to. `requirements` returns what is due next.
> * Razorpay returns the link only in this response. To get a new link, run the action again.
> * An action runs only while something it serves is due. Running the same action again sends a new OTP, up to 5 per hour per action.

> [!WARNING]
>
> **Watch Out!**
>
> * `status: failed` returns `200`. The action ran, but the registry or bank answered that it cannot be done. For example, `ckyc_mobile` is not the mobile on the Central KYC Records Registry (CKYC) record.
> * When the action fails, `error` says why and `requirements` lists what is due instead.
> * A registry or bank that does not answer returns `503`. Nothing ran, so retry later.

```bash Curl theme={null}
curl -X POST https://api.razorpay.com/v1/accounts/acc_TcdGEzmfKQzEl1/actions/send_ckyc_otp \
-u rzp_test_partner_[CLIENT_ID]:[CLIENT_SECRET] \
-H "Content-Type: application/json" \
-H "X-Idempotency-Key: [UNIQUE_KEY]" \
-d '{
  "metadata": {
    "ckyc_mobile": "+919845098450"
  }
}'
```

```json Success theme={null}
{
  "action": "send_ckyc_otp",
  "status": "completed",
  "metadata": [
    {
      "type": "sent_to",
      "value": "XXXXXX8450"
    },
    {
      "type": "expires_at",
      "value": 1792433590
    },
    {
      "type": "request_id",
      "value": "CKYCREQ20261115000123"
    }
  ],
  "requirements": [
    {
      "id": "req_57W5G6wcHziGOP",
      "requirement_code": "ckyc_otp",
      "requirement_level": "mandatory",
      "requirement_type": "input",
      "description": "Enter the code sent to the mobile on your CKYC record.",
      "field_path": "business_profile.authorized_person.identity_numbers.individual_ckyc.otp",
      "value_type": "text",
      "status": "created"
    },
    {
      "id": "req_mKVNnArZtTaL0M",
      "requirement_code": "ckyc_request_id",
      "requirement_level": "mandatory",
      "requirement_type": "input",
      "description": "The request ID that came with the code.",
      "field_path": "business_profile.authorized_person.identity_numbers.individual_ckyc.request_id",
      "value_type": "text",
      "status": "created"
    }
  ],
  "error": null
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "This isn't an action. Choose one of the allowed values.",
    "source": "business",
    "step": "validation",
    "reason": "invalid_option",
    "field": "action",
    "metadata": {
      "allowed_values": [
        "send_ckyc_otp",
        "send_phone_otp",
        "send_email_otp",
        "create_aadhaar_digilocker_link",
        "create_upi_link",
        "create_video_kyc_link"
      ]
    }
  }
}
```

## Path Parameters

**account\_id** `string` *required*

The unique identifier of the account, `acc_`-prefixed. For example, `acc_TcdGEzmfKQzEl1`.

**action** `string` *required*

The action to run. Possible values:

* `send_ckyc_otp`: Sends the CKYC code to the mobile on the person's CKYC record. `metadata.ckyc_mobile` is optional. A mobile that is not the one on the record returns `status: failed`. Due in the `ckyc_fetch` composite requirement once the PAN is verified and a CKYC record is found. The response's `requirements` list `ckyc_otp` and `ckyc_request_id`. Send the code as `otp` and the request ID as `request_id` on `business_profile.authorized_person.identity_numbers.individual_ckyc`. Running it again sends a new code and the open code stops working.
* `send_phone_otp`: Sends an OTP to the user's phone. The response's `requirements` list `phone_otp`, where you send the code. Not due if the account was created with `user.is_phone_verified`.
* `send_email_otp`: Sends an OTP to the user's email. The response's `requirements` list `email_otp`, where you send the code. Not due if the account was created with `user.is_email_verified`.
* `create_aadhaar_digilocker_link`: Creates a DigiLocker link to fetch the Aadhaar record as a proof of address. Needs `metadata.return_url`. The link is in the response's `metadata`. At the link, the sub-merchant signs in to DigiLocker and shares their Aadhaar. The response's `requirements` list `create_aadhaar_digilocker_link`, due until Razorpay has the Aadhaar.
* `create_upi_link`: Creates a ₹1 UPI link that verifies the settlement bank account, in place of a penny drop. The link is in the response's `metadata`. The sub-merchant pays ₹1 from the account and Razorpay refunds it. The response's `requirements` list `create_upi_link`, due until the payment settles.
* `create_video_kyc_link`: Creates a video KYC link while the product is `edd_pending`. The link is in the response's `metadata`. At the link, the sub-merchant completes a short video call with an agent. The response's `requirements` list `create_video_kyc_link`, due until the call is done.

## Request Parameters

**X-Idempotency-Key** `string` *required*

A unique key you generate for each write, 16-64 printable ASCII characters long. A Universally Unique Identifier (UUID) works. A retry with the same key within 24 h returns the original response instead of acting twice. Know more about [idempotency](https://razorpay.com/docs/api/partners/accounts#idempotency).

**metadata** `object`

Inputs some actions take.

**metadata.ckyc\_mobile** `string`

Optional, with `send_ckyc_otp`. The mobile on the CKYC record, +91 followed by 10 digits. A mobile that is not the one on the record returns `status: failed`. Pattern: `^\+91[0-9]{10}$`.

**metadata.return\_url** `string`

Required with `create_aadhaar_digilocker_link`. Your https page that the sub-merchant returns to.

## Response Parameters

**action** `string`

The action that ran. Possible values:

* `send_ckyc_otp`: Sends the CKYC code to the mobile on the person's CKYC record. `metadata.ckyc_mobile` is optional. A mobile that is not the one on the record returns `status: failed`. Due in the `ckyc_fetch` composite requirement once the PAN is verified and a CKYC record is found. The response's `requirements` list `ckyc_otp` and `ckyc_request_id`. Send the code as `otp` and the request ID as `request_id` on `business_profile.authorized_person.identity_numbers.individual_ckyc`. Running it again sends a new code and the open code stops working.
* `send_phone_otp`: Sends an OTP to the user's phone. The response's `requirements` list `phone_otp`, where you send the code. Not due if the account was created with `user.is_phone_verified`.
* `send_email_otp`: Sends an OTP to the user's email. The response's `requirements` list `email_otp`, where you send the code. Not due if the account was created with `user.is_email_verified`.
* `create_aadhaar_digilocker_link`: Creates a DigiLocker link to fetch the Aadhaar record as a proof of address. Needs `metadata.return_url`. The link is in the response's `metadata`. At the link, the sub-merchant signs in to DigiLocker and shares their Aadhaar. The response's `requirements` list `create_aadhaar_digilocker_link`, due until Razorpay has the Aadhaar.
* `create_upi_link`: Creates a ₹1 UPI link that verifies the settlement bank account, in place of a penny drop. The link is in the response's `metadata`. The sub-merchant pays ₹1 from the account and Razorpay refunds it. The response's `requirements` list `create_upi_link`, due until the payment settles.
* `create_video_kyc_link`: Creates a video KYC link while the product is `edd_pending`. The link is in the response's `metadata`. At the link, the sub-merchant completes a short video call with an agent. The response's `requirements` list `create_video_kyc_link`, due until the call is done.

**status** `string`

Whether the action ran. Possible values:

* `completed`: The OTP was sent or the link created.
* `failed`: The action ran, but the registry or bank answered that it cannot be done. For example, `ckyc_mobile` is not the mobile on the CKYC record. `error` says why.

**metadata** `array`

The action's outputs as type and value pairs.

**metadata\[].type** `string`

What the value is. Possible values:

* `sent_to`: The masked mobile or email the OTP went to.
* `url`: For link actions, the link to show the sub-merchant. Razorpay returns it only here, and a requirement never carries it. Run the action again for a new link.
* `expires_at`: When the OTP or link expires, as a Unix timestamp in seconds.
* `request_id`: With `send_ckyc_otp`, the CKYC request ID to send back with the code, in `individual_ckyc.request_id`.

**metadata\[].value** `string`

The value.

**requirements** `array`

What is due next because of the action, in full, as in the account's `requirements`. After an OTP, it is the code to send back: `phone_otp`, `email_otp` or `ckyc_otp`. For a link, it is the same action, due until the sub-merchant completes it. After a failed action, it is what is due instead. Know more about the [Requirement entity](https://razorpay.com/docs/api/partners/accounts/requirement-entity.md).

**error** `object`

Why the action failed. It is `null` when the action ran.

**error.code** `string`

`BAD_REQUEST_ERROR` or `SERVER_ERROR`.

**error.description** `string`

A sentence to show the sub-merchant.

**error.reason** `string`

A stable, machine-readable reason.

**error.field** `string`

The account path the error is about.

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

> [accordion] This isn't an action. Choose one of the allowed values.
>
> **Code:** `400`
>
> **Reason:** `invalid_option`
>
> The `action` in the path is not an action.
>
> **Solution:** Send one of the allowed values. `metadata.allowed_values` lists them when the list is short.

> [accordion] The request is missing a required field.
>
> **Code:** `400`
>
> **Reason:** `invalid_request`
>
> `metadata` has a key the action does not take or lacks a key it needs. For example, `create_aadhaar_digilocker_link` needs `return_url`.
>
> **Solution:** Send only the `metadata` keys the action takes, including every key it needs.

> [accordion] The value isn't in the right format.
>
> **Code:** `400`
>
> **Reason:** `invalid_format`
>
> `ckyc_mobile` is not +91 and 10 digits or `return_url` is not an https URL.
>
> **Solution:** Correct the value named in `error.field` and send it again. `metadata.pattern` shows the expected format.

> [accordion] This detail isn't needed yet.
>
> **Code:** `400`
>
> **Reason:** `step_not_due`
>
> Nothing the action serves is due. The action is one of these:
>
> * `send_phone_otp` or `send_email_otp` for a verified contact
> * `send_ckyc_otp` before the PAN is verified
> * `create_upi_link` with no bank account due
> * `create_video_kyc_link` while the product is not `edd_pending`
> * Any action on a `rejected` product
>
> **Solution:** Send only what the requirements list. `metadata.due` lists what is due now.

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

> [accordion] Too many requests. Try again shortly.
>
> **Code:** `429`
>
> **Reason:** `rate_limited`
>
> The same action ran more than 5 times in an hour on the account. Every OTP send counts.
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

> [accordion] The verification service is busy. Try again in a few minutes.
>
> **Code:** `503`
>
> **Reason:** `provider_unavailable`
>
> The registry, bank or provider behind the action did not answer. Nothing ran. The provider is the CKYC registry for `send_ckyc_otp`, DigiLocker for `create_aadhaar_digilocker_link` and the SMS or email provider for OTPs. An answer that the step cannot be done is a `200` with `status: failed` instead.
>
> **Solution:** Retry after the time in the `Retry-After` header. Nothing is wrong with the request.
