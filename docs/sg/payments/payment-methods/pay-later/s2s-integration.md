> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Atome Pay Later - S2S Integration

> Integrate Atome Buy Now Pay Later via Server-to-Server (S2S) for Singapore businesses. Pass product and shipping details for best Atome success rates.

Available in
🇸🇬 Singapore

Secure Server-to-Server (S2S) integration that enables seamless processing of Atome Buy Now, Pay Later (BNPL) payments in Singapore. Atome splits the purchase into 3 interest-free installments for the customer while you receive full settlement upfront.

## Prerequisites

1. [Sign up](https://dashboard.razorpay.com/#/access/signup) for a Razorpay account.
2. Generate API Keys.
3. Follow the [Razorpay S2S Integration documentation](https://razorpay.com/docs/sg/payments/payment-gateway/s2s-integration/json/v2).

## Integrate Atome on S2S

Create an order and pass `method=paylater` and `provider=atome` in the payment object.

> [!WARNING]
>
> **Watch Out!**
>
> Passing real product details (`line_items`) and `customer_details.shipping_address` in the Orders API request is strongly recommended for Atome transactions in Singapore. If these are not provided, fallback values will be used. This may negatively impact payment approval (success) rates and could risk account suspension by Atome.

### Create an Order and a Payment

Use the consolidated order and payment API to create a single API call that combines order and payment creation.

**POST** `/v1/orders`

```bash Request theme={null}
curl -X POST https://api.razorpay.com/v1/orders \
-U [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-H 'content-type:application/json' \
-d '{
  "amount": 50000,
  "currency": "SGD",
  "receipt": "receipt#1111",
  "customer_details": {
    "name": "John Doe",
    "contact": "+6580001500",
    "email": "john@example.com",
    "shipping_address": {
      "line1": "16 Sandilands Road",
      "line2": "#05-01",
      "city": "Singapore",
      "country": "SGP",
      "state": "Singapore",
      "zipcode": "546080"
    }
  },
  "line_items": [
    {
      "name": "iPhone 15 Pro",
      "quantity": 1,
      "price": 50000
    }
  ],
  "payment": {
    "contact": "+6580001500",
    "email": "john@example.com",
    "method": "paylater",
    "provider": "atome"
  }
}'
```

```json Success theme={null}
{
  "amount": 50000,
  "amount_due": 50000,
  "amount_paid": 0,
  "attempts": 1,
  "created_at": 1706507580,
  "currency": "SGD",
  "entity": "order",
  "id": "order_NUJs9C1Luflzts",
  "receipt": "receipt#1111",
  "status": "attempted",
  "payment_workflow": {
    "razorpay_payment_id": "pay_O0NSBQgY0BbC4b",
    "next": [
      {
        "action": "redirect",
        "url": "https://api.razorpay.com/v1/payments/pay_O0NSBQgY0BbC4b/authenticate"
      }
    ]
  }
}
```

### Handle the Redirect

After successful order and payment creation, redirect the customer to the `url` returned in `payment_workflow.next`. The customer will be taken to the Atome authentication page to log in and approve the installment plan, then redirected back to your return URL.

> [accordion] Request Parameters
>
> **amount** `integer` *required*
>
> Payment amount in the smallest currency sub-unit. For SGD 500.00, pass `50000`.
>
> **currency** `string` *required*
>
> Must be `SGD` for Singapore Atome transactions.
>
> **receipt** `string`
>
> Your receipt id for this order. Maximum length 40 characters.
>
> **customer\_details** `json object` *required*
>
> Customer details.
>
> **properties**
>
> **name** `string` *required*
>
> The customer's name.
>
> **contact** `string` *required*
>
> Customer's phone number in E.164 format (e.g. `+6580001500`).
>
> **email** `string` *required*
>
> Customer's email address.
>
> **shipping\_address** `json object`
>
> *optional (strongly recommended)*
> Shipping address for the order. Strongly recommended for Atome success rates. If not provided, a default address is sent to Airwallex, which may reduce approval rates.
>
> **properties**
>
> **line1** `string`
>
> Street address line 1. Concatenated with `line2` and sent to Atome.
>
> **line2** `string`
>
> Street address line 2.
>
> **city** `string`
>
> City name.
>
> **country** `string`
>
> ISO 3-letter country code. Use `SGP` for Singapore.
>
> **state** `string`
>
> State or province.
>
> **zipcode** `string`
>
> Postal code.
>
> **line\_items** `array`
>
> *optional (strongly recommended)*
> Product line items in the cart. Strongly recommended for Atome success rates. If not provided, a single generic item is sent to Atome, which may reduce approval rates.
>
> **properties**
>
> **name** `string`
>
> *mandatory per item*
> Product name.
>
> **quantity** `integer`
>
> *mandatory per item*
> Number of units.
>
> **price** `integer`
>
> *mandatory per item*
> Unit price in the smallest currency sub-unit (e.g. cents). For SGD 500.00, pass `50000`.
>
> **payment** `json object` *required*
>
> Payment details.
>
> **properties**
>
> **contact** `string` *required*
>
> Customer's phone number in E.164 format.
>
> **email** `string` *required*
>
> Customer's email address.
>
> **method** `string` *required*
>
> Must be `paylater`.
>
> **provider** `string` *required*
>
> Must be `atome`.

> [accordion] Response Parameters
>
> **id** `string`
>
> Unique identifier of the order.
>
> **amount** `integer`
>
> The transaction amount in smallest currency sub-unit.
>
> **currency** `string`
>
> The currency of the transaction. Here, `SGD`.
>
> **status** `string`
>
> Order status. Will be `attempted` after the payment is initiated.
>
> **payment\_workflow\.razorpay\_payment\_id** `string`
>
> Unique identifier of the payment.
>
> **payment\_workflow\.next\[].action** `string`
>
> Next action to complete the payment. Will be `redirect`.
>
> **payment\_workflow\.next\[].url** `string`
>
> URL to redirect the customer to the Atome authentication page.

## Constraints and Limitations

* Maximum transaction amount: **SGD 3,000** (Atome-imposed limit).
* Only **SGD** is supported for Atome transactions in Singapore.
* Customer phone number should be in E.164 format (e.g. `+6580001500`).
* Refunds follow the standard Razorpay [refunds](https://razorpay.com/docs/sg/payments/refunds) process.
