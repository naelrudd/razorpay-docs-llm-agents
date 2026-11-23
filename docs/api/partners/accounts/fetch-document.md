> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch One Document by ID

> Fetch a KYC document of a sub-merchant account with its ID using Razorpay Accounts API.

Available in
🇮🇳 India

Use this endpoint to fetch one stored file of an account: its type, name, format and size. Ask for a signed link to download it.

> [!NOTE]
>
> **Handy Tips**
>
> * Authenticate with the key and secret of your test pair or live pair. In the API playground, enter the test key as the username and its secret as the password. Use the live pair in live mode.
> * Pass `include_signed_url=true` for a signed download link in `url`.
> * You see only the files you uploaded and the Aadhaar that Razorpay downloaded from the Central KYC Records Registry (CKYC). Any other file returns `404` with `not_found`.
> * Responses carry `Cache-Control: private, no-store`. Do not cache them.

```bash Curl theme={null}
curl -X GET "https://api.razorpay.com/v1/accounts/acc_TcdGEzmfKQzEl1/documents/file_Qx7Lm2Kd9Tz4Ab?include_signed_url=true" \
-u rzp_test_partner_[CLIENT_ID]:[CLIENT_SECRET]
```

```json Success theme={null}
{
  "id": "file_Qx7Lm2Kd9Tz4Ab",
  "entity": "document",
  "type": "aadhaar_front",
  "url": "https://[SIGNED_DOWNLOAD_LINK]",
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
    "description": "The requested resource doesn't exist.",
    "source": "business",
    "step": "validation",
    "reason": "not_found",
    "field": "file_id",
    "metadata": {}
  }
}
```

## Path Parameters

**account\_id** `string` *required*

The unique identifier of the account, `acc_`-prefixed. For example, `acc_TcdGEzmfKQzEl1`.

**file\_id** `string` *required*

The unique identifier of the file, as the upload or the list returned it. `file_` followed by 14 letters or digits. For example, `file_Qx7Lm2Kd9Tz4Ab`.

## Query Parameters

**include\_signed\_url** `boolean`

Adds a signed download link as `url`. Default: `false`.

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

> [accordion] The value isn't in the right format.
>
> **Code:** `400`
>
> **Reason:** `invalid_format`
>
> The request has one of these problems:
>
> * The `file_id` is not `file_` followed by 14 letters or digits.
> * `include_signed_url` is not `true` or `false`.
>
> **Solution:** Correct the value named in `error.field`.

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
> No file with this ID is visible on the account. The file does not exist, was deleted or belongs to another account. Files that Razorpay holds for the account other than your uploads and the CKYC Aadhaar are not visible either. `error.field` is `file_id`.
>
> **Solution:** Check the `file_id`. Use an ID from [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md) or [Fetch All Documents](https://razorpay.com/docs/api/partners/accounts/fetch-all-documents.md).

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
