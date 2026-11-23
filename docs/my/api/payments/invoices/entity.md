> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Invoices Entity

> Entity parameters and sample code for Invoices API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

The Invoices entity has the following parameters:

```json Entity theme={null}
{
  "id": "inv_E7q0tqkxBRzdau",
  "entity": "invoice",
  "receipt": null,
  "invoice_number": null,
  "customer_id": "cust_E7q0trFqXgExmT",
  "customer_details": {
    "id": "cust_E7q0trFqXgExmT",
    "name": "<name>",
    "email": "<email>",
    "contact": "<phone>",
    "gstin": null,
    "billing_address": {
      "id": "addr_E7q0ttqh4SGhAC",
      "type": "billing_address",
      "primary": true,
      "line1": "Bakers Street",
      "line2": "Country Road",
      "zipcode": "560068",
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "in"
    },
    "shipping_address": {
      "id": "addr_E7q0ttKwVA1h2V",
      "type": "shipping_address",
      "primary": true,
      "line1": "Bakers Street",
      "line2": "Country Road",
      "zipcode": "560068",
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "in"
    },
    "customer_name": "<name>",
    "customer_email": "<email>",
    "customer_contact": "<phone>"
  },
  "order_id": "order_E7q0tvRpC0WJwg",
  "line_items": [
    {
      "id": "li_E7q0tuPNg84VbZ",
      "item_id": null,
      "ref_id": null,
      "ref_type": null,
      "name": "Master Cloud Computing in 30 Days",
      "description": "Book by Ravena Ravenclaw",
      "amount": 399,
      "unit_amount": 399,
      "gross_amount": 399,
      "tax_amount": 0,
      "taxable_amount": 399,
      "net_amount": 399,
      "currency": "MYR",
      "type": "invoice",
      "tax_inclusive": false,
      "hsn_code": null,
      "sac_code": null,
      "tax_rate": null,
      "unit": null,
      "quantity": 1,
      "taxes": []
    }
  ],
  "payment_id": null,
  "status": "issued",
  "expire_by": null,
  "issued_at": 1579765167,
  "paid_at": null,
  "cancelled_at": null,
  "expired_at": null,
  "sms_status": "pending",
  "email_status": "pending",
  "date": 1579765167,
  "terms": null,
  "partial_payment": false,
  "gross_amount": 399,
  "tax_amount": 0,
  "taxable_amount": 399,
  "amount": 399,
  "amount_paid": 0,
  "amount_due": 399,
  "currency": "MYR",
  "description": null,
  "notes": [],
  "comment": null,
  "short_url": "https://rzp.io/i/2wxV8Xs",
  "view_less": true,
  "billing_start": null,
  "billing_end": null,
  "type": "invoice",
  "group_taxes_discounts": false,
  "created_at": 1579765167
}
```

**id** `string`

The unique identifier of the invoice.

**entity** `string`

Indicates the type of entity. Here, it is `invoice`.

**type** `string`

Here, it should be `invoice`.

**invoice\_number** `string`

Unique number you added for internal reference. The minimum character length is 1 and maximum is 40.

**customer\_id** `string`

The unique identifier of the customer. You can create `customer_id` using the [Customers API](https://razorpay.com/docs/my/api/customers.md). Alternatively, you can pass the customer object described in the below fields.

**customer\_details** `object`

Details of the customer.

**id** `string`

Unique identifier of the customer. For example, `cust_1Aa00000000004`.

**name** `string`

Customer's name. Alphanumeric, with period (.), apostrophe (') and parentheses allowed. The name must be between 3-50 characters in length. For example, `Gaurav Kumar`.

**email** `string`

The customer's email address. A maximum length of 64 characters. For example, `gaurav.kumar@example.com`.

**contact** `string`

The customer's phone number. A maximum length of 15 characters including country code. For example, `+919876543210`.

**billing\_address** `object`

Details of the customer's billing address.

**id** `string`

The unique identifier generated for the customer's billing address.

**type** `string`

The customer address type. Here it is `billing_address`.

**primary** `boolean`

Defines if this is the primary address.

* `true`: It is the customer's primary address.
* `false`: It is not the customer's primary address.

**line1** `string`

The first line of the customer's address.

**line2** `string`

The second line of the customer's address.

**city** `string`

The city.

**zipcode** `string`

The zipcode.

**state** `string`

The state.

**country** `string`

The country.

**shipping\_address** `object`

Details of the customer's shipping address.

**id** `string`

The unique identifier generated for the customer's shipping address.

**type** `string`

The customer address type. Here it is `shipping_address`.

**primary** `boolean`

Defines if this is the primary address.

* `true`: It is the customer's primary address.
* `false`: It is not the customer's primary address.

**line1** `string`

The first line of the customer's address.

**line2** `string`

The second line of the customer's address.

**city** `string`

The city.

**zipcode** `string`

The zipcode.

**state** `string`

The state.

**country** `string`

The country.

**order\_id** `string`

The unique identifier of the order associated with the invoice.

**line\_items** `object`

Details of the line item that is billed in the invoice. Maximum of 50 line items.

**id** `string`

Unique identifier that is generated if a new item has been created while creating the invoice.

**item\_id** `string`

Unique identifier of the item generated using Items API that has been billed in the invoice.

**name** `string`

The item's name.

**description** `string`

A brief description of the item.

**amount** `integer`

The price of the item.

**currency** `string`

The currency associated with the item. Possible value: `MYR`.

**type** `string`

Here, it is `invoice`.

**quantity** `integer`

The quantity of the item billed in the invoice. Defaults to `1`.

**payment\_id** `string`

Unique identifier of a payment made against this invoice.

**status** `string`

The status of the invoice. Know more about [Invoice States](https://razorpay.com/docs/my/payments/invoices/states.md). Possible values:

* `draft`
* `issued`
* `partially_paid`
* `paid`
* `cancelled`
* `expired`
* `deleted`

**expire\_by** `integer`

Timestamp, in Unix format, at which the invoice will expire.

**issued\_at** `integer`

Timestamp, in Unix format, at which the invoice was issued to the customer.

**paid\_at** `integer`

Timestamp, in Unix format, at which the payment was made.

**cancelled\_at** `integer`

Timestamp, in Unix format, at which the invoice was cancelled.

**expired\_at** `integer`

Timestamp, in Unix format, at which the invoice expired.

**sms\_status** `string`

The delivery status of the SMS notification for the invoice sent to the customer. Possible values:

* `pending`
* `sent`

**email\_status** `string`

The delivery status of the email notification for the invoice sent to the customer. Possible values:

* `pending`
* `sent`

**partial\_payment** `boolean`

Indicates whether the customer can make a partial payment on the invoice. Possible values:

* `true`: The customer can make partial payments.
* `false` (default): The customer cannot make partial payments.

**amount** `integer`

Amount to be paid using the invoice. Must be in the smallest unit of the currency. For example, if the amount to be received from the customer is ₹300, pass the value as `30000`. In the case of three decimal currencies, such as KWD, BHD and OMR, to refund a payment of 295.991, pass the value as 295990. And in the case of zero decimal currencies such as JPY, to refund a payment of 295, pass the value as 295.

> [!WARNING]
>
> **Watch Out!**
>
> As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to refund a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.

**amount\_paid** `integer`

Amount paid by the customer against the invoice.

**amount\_due** `integer`

The remaining amount to be paid by the customer for the issued invoice.

**currency** `string`

The currency associated with the invoice. Possible value is `MYR`.

**description** `string`

A brief description of the invoice. The maximum character length is 2048.

**notes** `object`

Any custom notes added to the invoice. Maximum of 2048 characters.

**short\_url** `string`

The short URL that is generated. Share this link with customers to accept payments.

**date** `integer`

Timestamp, in Unix format, that indicates the issue date of the invoice.

**terms** `string`

Any terms to be included in the invoice. Maximum of 2048 characters.

**comment** `string`

Any comments to be added in the invoice. Maximum of 2048 characters.
