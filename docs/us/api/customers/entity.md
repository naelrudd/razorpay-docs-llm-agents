> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Customers Entity

> Entity parameters and sample code for Customers API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

The Customers entity has the following parameters:

```json Entity theme={null}
{
  "id": "cust_JbRkXMROZUMCVq",
  "entity": "customer",
  "name": "<name>",
  "email": "<email>",
  "contact": "<phone>",
  "gstin": null,
  "notes": [],
  "created_at": 1653915355
}
```

**id** `string`

Unique identifier of the customer. For example, `cust_1Aa00000000004`.

**name** `string`

Customer's name. Alphanumeric, with period (.), apostrophe ('), forward slash (/), at (@) and parentheses allowed. The name must be between 3-50 characters in length. For example, `John Smith`.

**contact** `string`

The customer's phone number. A maximum length of 15 characters including country code. For example, `+1123567890`.

**email** `string`

The customer's email address. A maximum length of 64 characters. For example, `john.smith@example.com`.

**notes** `json object`

This is a key-value pair that can be used to store additional information about the entity. It can hold a maximum of 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

**created\_at** `integer`

UNIX timestamp, when the customer was created. For example, `1234567890`.
