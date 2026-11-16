> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Documents Entity

> Know about documents entity parameters and their description.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

The Documents entity has the following parameters:

```json Entity theme={null}
{
  "id":"doc_EsyWjHrfzb59Re",
  "entity":"document",
  "purpose":"dispute_evidence",
  "name":"file_19_18_2020.jpg",
  "mime_type":"image/png",
  "size":2863,
  "created_at":1590604200
}
```

**id** `string`

The unique identifier of the document uploaded.

**entity** `string`

Indicates the type of entity. In this case, it is `document`.

**purpose** `string`

The reason you are uploading this document. Here, it is `dispute_evidence`.

**size** `integer`

Indicates the size of the document in bytes.

**mime\_type** `string`

Indicates the nature and format in which the document is uploaded. Possible values are:

* image/jpg
* image/jpeg
* image/png
* application/pdf

**created\_at** `integer`

Unix timestamp at which the document was uploaded.
