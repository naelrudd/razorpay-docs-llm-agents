# Fetch Document Content

**GET** `/v1/documents/:id/content`

Use this endpoint to download an earlier uploaded document. The response is the **raw file content** (binary) with the original `Content-Type` header (for example, `image/jpeg` for an uploaded image), not a JSON object.

### Request

```curl: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X GET https://api.razorpay.com/v1/documents/:id/content

```bash: CLI 
#Download document content (save to file)

razorpay documents fetch-content doc_1234567890abcd --output /path/to/output.jpg

#Download document content (stream to stdout)

razorpay documents fetch-content doc_1234567890abcd > /path/to/output.jpg
```

### Response

```json: Failure
{
  "error":{
    "status_code": 401,
    "description":"The API `` provided is invalid.",
    "code":"BAD_REQUEST_ERROR"
  }
}
```

### Parameters

`id` _mandatory_
: `string` The unique identifier of the document.

### Errors

The API `` provided is invalid.
* code: 400
* description: The API credentials passed in the API call differ from the ones generated on the Dashboard.- Different keys for test mode and live modes.
- Expired API key.

* solution: The API keys must be active and entered correctly with no whitespace before or after the keys.

_id is not a valid id.
* code: 400
* description: - The id is not 14 characters long.
- The id is not alphanumeric.

* solution: Use a valid document id.

Invalid file id provided or merchant is unauthorized to access the fileId(s) provided.
* code: 400
* description: The `id` does not exist, or it belongs to a different merchant. The API returns the same error for both cases for security reasons (so callers cannot enumerate other merchants' document ids).
* solution: Pass a valid `id` that was created by this merchant account.
