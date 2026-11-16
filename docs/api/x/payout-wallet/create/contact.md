> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Contact

> Create a Contact via API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create a Contact using the Contact details of the Amazon Pay wallet holder.

```bash Curl theme={null}
curl -u <YOUR_KEY>:<YOUR_SECRET> \
-X POST https://api.razorpay.com/v1/contacts \
-H "Content-Type: application/json" \
-d '{
  "name":"Gaurav Kumar",
  "email":"gaurav.kumar@example.com",
  "contact":"9000090000",
  "type":"employee",
  "reference_id":"Acme Contact ID 12345",
  "notes":{
    "notes_key_1":"Tea, Earl Grey, Hot",
    "notes_key_2":"Tea, Earl Grey… decaf."
  }
}'
```

```json Success theme={null}
{
  "id": "cont_00000000000001",
  "entity": "contact",
  "name": "Gaurav Kumar",
  "contact": "9000090000",
  "email": "gaurav.kumar@example.com",
  "type": "employee",
  "reference_id": "Acme Contact ID 12345",
  "batch_id": null,
  "active": true,
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  },
  "created_at": 1545320320
}
```

## Request Parameters

**name** `string` *required*

The contact's name. This field is case-sensitive. A minimum of 3 characters and a maximum of 50 characters are allowed. Name cannot end with a special character, except `.`. Supported characters: `a-z`, `A-Z`, `0-9`, `space`, `’` , `-` , `_` , `/` , `(` , `)` and , `.`. For example, `Gaurav Kumar`.

**email** `string`

The contact's email address. For example, `gaurav.kumar@example.com`.

**contact** `string`

The contact's phone number. For example, `9000090000`.

**type** `string`

Maximum 40 characters. Classification for the contact being created. For example, `employee`. The following classifications are available by default:

* `vendor`
* `customer`
* `employee`
* `self`

Additional classifications can be created via the [Dashboard](https://x.razorpay.com/) and then used in APIs. It is not possible to create new classifications via API.

**reference\_id** `string`

Maximum 40 characters. A user-entered reference for the contact. For example, `Acme Contact ID 12345`.

**notes** `object`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

## Response Parameters

**id** `string`

The unique identifier linked to the contact. For example, `cont_00000000000001`.

**entity** `string`

The entity being created. Here, it is `contact`.

**name** `string`

The contact's name. For example, `Gaurav Kumar`.

**contact** `string`

The contact's phone number. For example, `9000090000`.

**email** `string`

The contact's email address. For example, `gaurav.kumar@example.com`.

**type** `string`

A classification for the contact being created. For example, `employee`.

**reference\_id** `string`

A user-entered reference for the contact. For example, `Acme Contact ID 12345`.

**batch\_id** `string`

This value is returned if the contact was created as part of a bulk upload. For example, `batch_00000000000001`.

**active** `boolean`

Possible values:

* `true` (default) : active
* `false` : inactive

**notes** `object`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

**created\_at** `integer`

Timestamp, in Unix, when the contact was created. For example, `1545320320`.

## Errors

> [accordion] The `name` field is required.
>
> **Code:** `4xx`
>
> The `name` field is missing in the request body.
>
> **Solution:** Enter the details in the recommended format as per the request body.

> [accordion] The `name` field is invalid.
>
> **Code:** `4xx`
>
> There are special characters used in the `name` field.
>
> **Solution:** Enter details as per the format recommended for Create a Contact request for `name` field.

> [accordion] Invalid type: `contact_typeA`
>
> **Code:** `4xx`
>
> * There are special characters in the `type` field.
> * Casing does not match as per the `type`. `type` is case-sensitive.
> * Contact type sent in the request does not match the types present in the Dashboard.
>
> **Solution:** Enter the correct contact type in the request body. You cannot create new contact types via API. You must create them via the [RazorpayX Dashboard](http://x.razorpay.com/auth).
