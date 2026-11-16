> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Document Content

> Fetch Document Content using Razorpays API.

Available in
🇮🇳 India
🇺🇸 United States

Use this endpoint to download an earlier uploaded document. The response is the **raw file content** (binary) with the original `Content-Type` header (for example, `image/jpeg` for an uploaded image), not a JSON object.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X GET https://api.razorpay.com/v1/documents/:id/content
```

```bash CLI theme={null}
#Download document content (save to file)

razorpay documents fetch-content doc_1234567890abcd --output /path/to/output.jpg

#Download document content (stream to stdout)

razorpay documents fetch-content doc_1234567890abcd > /path/to/output.jpg
```

```json Failure theme={null}
{
  "error":{
    "status_code": 401,
    "description":"The API `<key/secret>` provided is invalid.",
    "code":"BAD_REQUEST_ERROR"
  }
}
```

## Path Parameters

**id** `string` *required*

The unique identifier of the document.

## Errors

> [accordion] The API `\<key/secret\>
> ` provided is invalid.
>
> **Code:** `400`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard.
>
> * Different keys for test mode and live modes.
> * Expired API key.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after the keys.

> [accordion] \_id is not a valid id.
>
> **Code:** `400`
>
> * The id is not 14 characters long.
> * The id is not alphanumeric.
>
> **Solution:** Use a valid document id.

> [accordion] Invalid file id provided or merchant is unauthorized to access the fileId(s) provided.
>
> **Code:** `400`
>
> The `id` does not exist, or it belongs to a different merchant. The API returns the same error for both cases for security reasons (so callers cannot enumerate other merchants' document ids).
>
> **Solution:** Pass a valid `id` that was created by this merchant account.
