> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Document Information

> Fetch Document Information using Razorpays API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve the details of any document that was uploaded earlier.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET https://api.razorpay.com/v1/documents/doc_EsyWjHrfzb59Re
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String documentId = "doc_EsyWjHrfzb59Re";

Document document = instance.document.fetch(documentId);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

documentId = "doc_NiyXWXXXXXXXXX"

client.document.fetch(documentId)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$documentId = "";

$api->document->fetch($documentId);
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

documentId = "doc_NiyXWXXXXXXXXX"

Razorpay::Document.fetch(documentId)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

var documentId = "doc_EsyWjHrfzb59Re";

instance.documents.fetch(documentId);
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

documentId = "doc_NiyXWXXXXXXXXX"

body, err := client.Document.Fetch(documentId, nil, nil)
```

```bash CLI theme={null}
razorpay documents fetch doc_1234567890abcd
```

```json Success theme={null}
{
  "id": "doc_EsyWjHrfzb59Re",
  "entity": "document",
  "purpose": "dispute_evidence",
  "name": "file_19_18_2020.jpg",
  "mime_type": "image/png",
  "size": 2863,
  "created_at": 1590604200
}
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

## Response Parameters

**id** `string`

The unique identifier of the document uploaded.

**entity** `string`

Indicates the type of entity. In this case, it is `document`.

**purpose** `string`

The reason you are uploading this document. Here, it is `dispute_evidence`.

**size** `integer`

Indicates the size of the document in bytes.

**mime\_type** `string`

Indicates the nature and format in which the document is uploaded. Possible values include:

* image/jpg
* image/jpeg
* image/png
* application/pdf

**created\_at** `integer`

Unix timestamp at which the document was uploaded.

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
