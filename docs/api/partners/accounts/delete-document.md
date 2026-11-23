> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Delete a Document

> Delete a KYC document of a sub-merchant account using Razorpay Accounts API.

Available in
🇮🇳 India

Use this endpoint to delete one file you uploaded, or the CKYC Aadhaar, from an account. The file no longer appears when you fetch or list documents.

> [!NOTE]
>
> **Handy Tips**
>
> * Authenticate with the key and secret of your test pair or live pair. In the API playground, enter the test key as the username and its secret as the password. Use the live pair in live mode.
> * The call takes no `X-Idempotency-Key`. Deleting the same file again returns `404` with `not_found`.
> * Razorpay does not check whether the account uses the file. A file attached to the account can still be deleted.
> * You see only the files you uploaded and the Aadhaar that Razorpay downloaded from the Central KYC Records Registry (CKYC). Any other file returns `404` with `not_found`.

```bash Curl theme={null}
curl -X DELETE https://api.razorpay.com/v1/accounts/acc_TcdGEzmfKQzEl1/documents/file_Qx7Lm2Kd9Tz4Ab \
-u rzp_test_partner_[CLIENT_ID]:[CLIENT_SECRET]
```

```json Success theme={null}
{
  "id": "file_Qx7Lm2Kd9Tz4Ab",
  "entity": "document",
  "deleted": true
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

## Response Parameters

**id** `string`

The ID of the deleted file.

**entity** `string`

Always `document`.

**deleted** `boolean`

Always `true` on success.

## Errors

> [accordion] The value isn't in the right format.
>
> **Code:** `400`
>
> **Reason:** `invalid_format`
>
> The `file_id` is not `file_` followed by 14 letters or digits.
>
> **Solution:** Use the `file_id` from the upload or the list.

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
