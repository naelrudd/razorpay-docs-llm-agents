> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Orders Entity

> Entity parameters and sample code for Orders API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

The Orders entity has the following parameters:

```json Entity theme={null}
{
  "id": "order_DaZlswtdcn9UNV",
  "entity": "order",
  "amount": 50000,
  "amount_paid": 0,
  "amount_due": 50000,
  "currency": "SGD",
  "receipt": "Receipt #20",
  "status": "created",
  "attempts": 0,
  "notes": {
    "key1": "value1",
    "key2": "value2"
  },
  "created_at": 1572502745
}
```

**id** `string`

The unique identifier of the order.

**amount** `integer` *required*

Payment amount in the smallest currency sub-unit. For example, if the amount to be charged is , then pass `29900` in this field.

**partial\_payment** `boolean`

Indicates whether the customer can make a partial payment. Possible values:

* `true`: The customer can make partial payments.
* `false` (default): The customer cannot make partial payments.

**amount\_paid** `integer`

The amount paid against the order.

**amount\_due** `integer`

The amount pending against the order.

**currency** `string` *required*

ISO code for the currency in which you want to accept the payment. The default length is 3 characters.

**receipt** `string`

Receipt number that corresponds to this order. Can have a maximum length of 40 characters and has to be unique.

**status** `string`

The status of the order. Possible values:

* `created`: When you create an order it is in the `created` state. It stays in this state till a payment is attempted on it.
* `attempted`: An order moves from `created` to `attempted` state when a payment is first attempted on it. It remains in the `attempted` state till one payment associated with that order is captured.
* `paid`: After the successful capture of the payment, the order moves to the `paid` state. No further payment requests are permitted once the order moves to the `paid` state. The order stays in the `paid` state even if the payment associated with the order is refunded.

**attempts** `integer`

The number of payment attempts, successful and failed, that have been made against this order.

**notes** `json object`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

**created\_at** `integer`

Indicates the Unix timestamp when this order was created.
