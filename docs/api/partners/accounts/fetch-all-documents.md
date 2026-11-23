> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch All Documents

> Fetch all KYC documents of a sub-merchant account using Razorpay Accounts API.

Available in
🇮🇳 India

Use this endpoint to fetch the stored files of an account, newest first. Filter by document type if you need one type only.

> [!NOTE]
>
> **Handy Tips**
>
> * Authenticate with the key and secret of your test pair or live pair. In the API playground, enter the test key as the username and its secret as the password. Use the live pair in live mode.
> * Pass `type` to return one document type. No match returns `200` with `count` as `0`.
> * The list has no pagination. It returns every file you can see.
> * `url` is always `null` in the list. [Fetch one document](https://razorpay.com/docs/api/partners/accounts/fetch-document.md) for its download link.
> * You see only the files you uploaded and the Aadhaar that Razorpay downloaded from the Central KYC Records Registry (CKYC). Other files never appear.
> * Responses carry `Cache-Control: private, no-store`. Do not cache them.

```bash Curl theme={null}
curl -X GET "https://api.razorpay.com/v1/accounts/acc_TcdGEzmfKQzEl1/documents?type=aadhaar_front" \
-u rzp_test_partner_[CLIENT_ID]:[CLIENT_SECRET]
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
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
    },
    {
      "id": "file_Rb3Nc8Pw1Yv6Ef",
      "entity": "document",
      "type": "aadhaar_front",
      "url": null,
      "metadata": {
        "source": "ckyc",
        "file_name": "aadhaar_front",
        "mime_type": "image/jpeg",
        "size_bytes": 96410
      }
    }
  ]
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "Choose one of the allowed values.",
    "source": "business",
    "step": "validation",
    "reason": "invalid_option",
    "field": "type",
    "metadata": {}
  }
}
```

## Path Parameters

**account\_id** `string` *required*

The unique identifier of the account, `acc_`-prefixed. For example, `acc_TcdGEzmfKQzEl1`.

## Query Parameters

**type** `string`

Return only files of this document type. Default: all types. Know more about [document types](https://razorpay.com/docs/api/partners/accounts/document-entity.md).

## Response Parameters

**entity** `string`

Always `collection`.

**count** `integer`

Number of files in `items`.

**items** `array`

The files, newest first. Each has the parameters below.

**items\[].id** `string`

Unique identifier for the file, `file_` followed by 14 letters or digits.

**items\[].entity** `string`

Always `document`.

**items\[].type** `string`

The document type of the file. Know more about the [document types](https://razorpay.com/docs/api/partners/accounts/document-entity.md#document-types).

**items\[].url** `string`

Always `null` in the list. Fetch one file with `include_signed_url=true` for its link.

**items\[].metadata** `object`

About the stored file.

**items\[].metadata.source** `string`

Where the file came from. Possible values:

* `upload`: You uploaded it.
* `ckyc`: Razorpay downloaded it from the CKYC record.

**items\[].metadata.file\_name** `string`

The file name as you sent it.

**items\[].metadata.mime\_type** `string`

The format Razorpay detected from the file content, such as `image/jpeg`. It can be `null`.

**items\[].metadata.size\_bytes** `integer`

File size in bytes. It can be `null`.

## Errors

> [accordion] Choose one of the allowed values.
>
> **Code:** `400`
>
> **Reason:** `invalid_option`
>
> `type` is not a supported document type.
>
> **Solution:** Send a supported document type. Know more about [document types](https://razorpay.com/docs/api/partners/accounts/document-entity.md).

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
