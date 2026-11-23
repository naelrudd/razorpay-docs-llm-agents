> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Upload a Document

> Upload a KYC document for a sub-merchant account using Razorpay Accounts API.

Available in
🇮🇳 India

Use this endpoint to store one KYC file for an account and get its file ID. Send that ID in the account's `documents` with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md) to attach the file.

> [!NOTE]
>
> **Handy Tips**
>
> * Authenticate with the key and secret of your test pair or live pair. In the API playground, enter the test key as the username and its secret as the password. Use the live pair in live mode.
> * Send the request as `multipart/form-data`, with 1 `file` and its `type`. The endpoint takes a file only, never a link.
> * To share a document as a link instead, send its `url` in the account's `documents` with [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md). Razorpay downloads it from there.
> * The upload alone does not attach the file. Razorpay verifies a document when you attach it to the account.
> * Razorpay keeps its own copy as the data fiduciary. Delete your copy once the upload succeeds, as your agreement with Razorpay requires.
> * Responses carry `Cache-Control: private, no-store`. Do not cache them.

> [!WARNING]
>
> **Watch Out!**
>
> A retry with the same `X-Idempotency-Key`, `type` and file returns the first response for up to 1 h, without storing a second file. The same key with a different `type` or file returns `400` with `idempotency_key_reused`. A refused or failed upload does not hold the key.

```bash Curl theme={null}
curl -X POST https://api.razorpay.com/v1/accounts/acc_TcdGEzmfKQzEl1/documents \
-u rzp_test_partner_[CLIENT_ID]:[CLIENT_SECRET] \
-H "X-Idempotency-Key: [UNIQUE_KEY]" \
-F "type=aadhaar_front" \
-F "file=@aadhaar-front.jpg"
```

```json Success theme={null}
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

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "The file format is not accepted for this document type.",
    "source": "business",
    "step": "validation",
    "reason": "unsupported_media_type",
    "field": "file",
    "metadata": {
      "detected_type": "image/heic",
      "accept": "application/pdf,image/jpeg,image/png"
    }
  }
}
```

## Path Parameters

**account\_id** `string` *required*

The unique identifier of the account, `acc_`-prefixed. For example, `acc_TcdGEzmfKQzEl1`.

## Request Parameters

Send `file` and `type` as `multipart/form-data` parts.

**X-Idempotency-Key** `string` *required*

A unique key you generate for each upload, 16-64 printable ASCII characters long. A Universally Unique Identifier (UUID) works. Know more about [idempotency](https://razorpay.com/docs/api/partners/accounts#idempotency).

**file** `file` *required*

The file, sent with its file name. Exactly 1 file of up to 20 MB:

* **Format:** PDF, JPEG or PNG. Razorpay detects the format from the file content. `cancelled_cheque_video` takes a video instead: MP4, MOV, M4V, MKV, AVI, WMV, FLV or MPEG.
* **PDF:** Up to 20 pages, without a password.
* **Image:** Up to 50 megapixels.
* **File name:** Up to 255 bytes, with no path separator or control character.

**type** `string` *required*

The document type of the file, sent once. The account's `requirements` list the types each product needs. Know more about [document types](https://razorpay.com/docs/api/partners/accounts/document-entity.md).

## Response Parameters

**id** `string`

Unique identifier for the file, `file_` followed by 14 letters or digits.

**entity** `string`

Always `document`.

**type** `string`

The document type of the file. Know more about the [document types](https://razorpay.com/docs/api/partners/accounts/document-entity.md#document-types).

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

## Errors

> [accordion] A required header is missing.
>
> **Code:** `400`
>
> **Reason:** `missing_header`
>
> `X-Idempotency-Key` is missing.
>
> **Solution:** Send `X-Idempotency-Key` with 16-64 printable ASCII characters. `error.field` names the header.

> [accordion] The value isn't in the right format.
>
> **Code:** `400`
>
> **Reason:** `invalid_format`
>
> `X-Idempotency-Key` is not 16-64 printable ASCII characters.
>
> **Solution:** Send a key of 16-64 printable ASCII characters.

> [accordion] The request is missing a required field.
>
> **Code:** `400`
>
> **Reason:** `invalid_request`
>
> The body does not have exactly 1 `file` part and a `type`. `error.field` names the missing part.
>
> **Solution:** Send a `multipart/form-data` body with 1 `file` and its `type`.

> [accordion] Choose one of the allowed values.
>
> **Code:** `400`
>
> **Reason:** `invalid_option`
>
> `type` is not a supported document type.
>
> **Solution:** Send a supported document type. Know more about [document types](https://razorpay.com/docs/api/partners/accounts/document-entity.md).

> [accordion] The file can't be read. Upload it again.
>
> **Code:** `400`
>
> **Reason:** `invalid_file`
>
> The file is empty or Razorpay cannot read it.
>
> **Solution:** Check that the file is complete and readable, then upload it again.

> [accordion] The file name isn't allowed.
>
> **Code:** `400`
>
> **Reason:** `invalid_file_name`
>
> The file name has a path separator or a control character.
>
> **Solution:** Rename the file without path separators or control characters, then upload it again.

> [accordion] The file name is too long.
>
> **Code:** `400`
>
> **Reason:** `file_name_too_long`
>
> The file name is longer than 255 bytes, including the extension.
>
> **Solution:** Shorten the file name, then upload it again. `metadata.max_bytes` is the limit.

> [accordion] Upload the file without a password.
>
> **Code:** `400`
>
> **Reason:** `password_protected_file`
>
> The PDF is password protected.
>
> **Solution:** Upload a copy without the password.

> [accordion] This request conflicts with an earlier one.
>
> **Code:** `400`
>
> **Reason:** `idempotency_key_reused`
>
> You already used this `X-Idempotency-Key` for a different upload. A key is bound to its `type` and the exact file.
>
> **Solution:** Send a new `X-Idempotency-Key` for a different upload. Reuse a key only to retry the same upload.

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
> An upload with this `X-Idempotency-Key` is still running.
>
> **Solution:** Wait for the time in the `Retry-After` header, then retry with the same key.

> [accordion] The file is too large.
>
> **Code:** `413`
>
> **Reason:** `file_too_large`
>
> The file is larger than 20 MB.
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
> * The body is not `multipart/form-data`. `error.field` is `Content-Type`.
> * The file format is not accepted for this document type. `error.field` is `file`.
>
> **Solution:** Send the body as `multipart/form-data`. For the file, use a format in `metadata.accept`. `metadata.detected_type` shows the format found.

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
