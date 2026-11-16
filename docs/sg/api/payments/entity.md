> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payments Entity

> Know about payment entities and their description.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

The Payments entity has the following parameters:

```json Success theme={null}
{
  "id": "pay_L0nSsccovt6zyp",
  "entity": "payment",
  "amount": 9900,
  "currency": "SGD",
  "status": "captured",
  "order_id": "order_L0nS83FfCHaWqV",
  "invoice_id": "inv_L0nS7JIyuX6Lyb",
  "international": false,
  "method": "card",
  "amount_refunded": 0,
  "refund_status": null,
  "captured": true,
  "description": "#L0nS7JIyuX6Lyb",
  "card_id": "card_L0nSsfPv1LjA20",
  "card": {
    "id": "card_L0nSsfPv1LjA20",
    "entity": "card",
    "name": "",
    "last4": "0153",
    "network": "Visa",
    "type": "debit",
    "issuer": null,
    "international": false,
    "sub_type": "consumer",
    "token_iin": null
  },
  "bank": null,
  "wallet": null,
  "email": "<email>",
  "contact": "<phone>",
  "notes": [],
  "fee": 198,
  "tax": 0,
  "error_code": null,
  "error_description": null,
  "error_source": null,
  "error_step": null,
  "error_reason": null,
  "acquirer_data": {
    "auth_code": "299196"
  },
  "created_at": 1672987417
}
```

```json Failure theme={null}
{
  "id": "pay_Kb8P4crStfXJea",
  "entity": "payment",
  "amount": 10000,
  "currency": "SGD",
  "status": "failed",
  "order_id": null,
  "invoice_id": null,
  "international": false,
  "method": "card",
  "amount_refunded": 0,
  "refund_status": null,
  "captured": false,
  "description": "Test Transaction",
  "card_id": "card_Kb8P4eO7zAsjQJ",
  "card": {
    "id": "card_Kb8P4eO7zAsjQJ",
    "entity": "card",
    "name": "",
    "last4": "0153",
    "network": "Visa",
    "type": "debit",
    "issuer": null,
    "international": false,
    "sub_type": "consumer",
    "token_iin": null
  },
  "bank": null,
  "wallet": null,
  "email": "<email>",
  "contact": "<phone>",
  "notes": {
    "address": "Corporate Office"
  },
  "fee": null,
  "tax": null,
  "error_code": "BAD_REQUEST_ERROR",
  "error_description": "Your payment has been cancelled. Try again or complete the payment later.",
  "error_source": "customer",
  "error_step": "payment_authentication",
  "error_reason": "payment_cancelled",
  "acquirer_data": {
    "auth_code": null
  },
  "created_at": 1667384312
}
```

**id** `string`

Unique identifier of the payment.

**entity** `string`

Indicates the type of entity.

**amount** `integer`

Payment amount in the smallest currency sub-unit. For example, if the amount to be charged is S\$299, then pass `29900` in this field.

**currency** `string`

The currency in which the payment is made.

**status** `string`

The status of the payment. Possible values:

* `created`
* `authorized`
* `captured`
* `refunded`
* `failed`

**method** `string`

The payment method used for making the payment. Possible values:

* `card`
* `paynow`

**order\_id** `string`

Order id, if provided. Know more about [Orders](https://razorpay.com/docs/sg/payments/orders).

**description** `string`

Description of the payment, if any.

**international** `boolean`

Indicates whether the payment is done via an international card or a domestic one.

**refund\_status** `string`

The refund status of the payment. Possible values:

* `null`
* `partial`
* `full`

**amount\_refunded** `integer`

The amount refunded in currency subunits. For example, if `amount_refunded = 100`, it is equal to S\$1.

**captured** `boolean`

Indicates if the payment is captured.

**email** `string`

Customer email address used for the payment.

**contact** `string`

Customer contact number used for the payment.

**fee** `integer`

Fee  charged by Razorpay.

**tax** `integer`

Tax charged for the payment.

**error\_code** `string`

Error that occurred during payment. For example, `BAD_REQUEST_ERROR`.

**error\_description** `string`

Description of the error that occurred during payment. For example, `Payment processing failed because of incorrect OTP`.

**error\_source** `string`

The point of failure. For example, `customer`.

**error\_step** `string`

The stage where the transaction failure occurred. The stages can vary depending on the payment method used to complete the transaction. For example, `payment_authentication`.

**error\_reason** `string`

The exact error reason. For example, `incorrect_otp`.

**notes** `json object`

Contains user-defined fields, stored for reference purposes.

**created\_at** `integer`

Timestamp, in UNIX format, on which the payment was created.

**card\_id** `string`

The unique identifier of the card used by the customer to make the payment.

**card** `object`

Details of the card used to make the payment.

**id** `string`

The unique identifier of the card used by the customer to make the payment.

**entity** `string`

The name of the entity. Here, it is `card`.

**name** `string`

Name of the cardholder.

**last4** `integer`

The last 4 digits of the card number.

**network** `string`

The card network. Possible values:

* `MasterCard`
* `Visa`
* `Amex`
* `UnionPay`

**type** `string`

The card type. Possible values:

* `credit`
* `debit`
* `prepaid`
* `unknown`

**issuer** `string`

The card issuer. The 4-character code denotes the issuing bank. \\

> [!NOTE]
>
> **Handy Tips**
>
> This attribute will not be set for the card issued by a foreign bank.

**sub\_type** `string`

The sub-type of the customer's card. Possible values:

* `customer`
* `business`

> [!NOTE]
>
> **Handy Tips**
>
> Know how to accept payments made by customers using [corporate cards](https://razorpay.com/docs/payments/payment-methods/cards/corporate-cards).

**bank** `string`

The 4-character bank code which the customer's account is associated with. In case of PayNow, the value will be `null`.

**acquirer\_data** `array`

A dynamic array consisting of a unique reference numbers.

**rrn** `string`

A unique bank reference number provided by the banking partner when a refund is processed. This reference number can be used by the customer to track the status of the refund with the bank.

**bank\_transaction\_id** `string`

A unique reference number provided by the banking partner.
