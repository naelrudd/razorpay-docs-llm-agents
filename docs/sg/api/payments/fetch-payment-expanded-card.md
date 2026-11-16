> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch a Payment (With Expanded Card Details)

> Fetch a Payment with Expanded Card Details using Razorpay Payments API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve the details of all the payments that you created, with the `card` parameter expanded in the payments object.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X GET https://api.razorpay.com/v1/payments/pay_DG4a4vAWvKrh79/?expand[]=card
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_JqLHMVryzMEafT";

JSONObject request = new JSONObject();
request.put("expand[]","card");

Entity payment = razorpay.payments.get("payments/"+paymentId, request);
```

```python Python theme={null}
import razorpay

client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.fetch("pay_JqLHMVryzMEafT",{"expand[]":"card"})
```

```ruby Ruby theme={null}
require "razorpay"

Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymentId = "pay_JLcbRwKkgDlWWJ"

para_attr = {
    "expand[]": "card"
}

Razorpay::Payment.request.get paymentId , para_attr
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
    "expand[]":"card",
}

paymentId := "pay_JqLHMVryzMEafT"

body, err := client.Payment.Fetch(paymentId, data, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$paymentId = "pay_MLzFlOC98cJmHQ";

$api->payment->fetch($paymentId)->expandedDetails(["expand[]"=> "card"]);
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

paymentId = "pay_JqLHMVryzMEafT"  

instance.payments.fetch(paymentId,{"expand[]":"card"})
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> paramRequest = new Dictionary<string, object>();
paramRequest.Add("expand[]","card");

List<Payment> payment = client.Payment.All(paramRequest);
```

```bash CLI theme={null}
razorpay payments fetch pay_ABC123 --expand card
```

```json Success theme={null}
{
  "id": "pay_H9oR0gLCaVlV6m",
  "entity": "payment",
  "amount": 100,
  "currency": "SGD",
  "status": "failed",
  "order_id": "order_H9o58N6qmLYQKC",
  "invoice_id": null,
  "terminal_id": "term_G5kJnYM9GhhLYT",
  "international": false,
  "method": "card",
  "amount_refunded": 0,
  "refund_status": null,
  "captured": false,
  "description": null,
  "card_id": "card_H9oR0ocen1cmZq",
  "card": {
    "id": "card_H9oR0ocen1cmZq",
    "entity": "card",
    "name": "Gaurav",
    "last4": "1213",
    "network": "RuPay",
    "type": "credit",
    "issuer": "UTIB",
    "international": false,
    "emi": false,
    "sub_type": "business"
  },
  "bank": null,
  "wallet": null,
  "vpa": null,
  "email": "alex.lim@example.com",
  "contact": "+919000090000",
  "notes": {
    "email": "alex.lim@example.com",
    "phone": "09000090000"
  },
  "fee": null,
  "tax": null,
  "error_code": "BAD_REQUEST_ERROR",
  "error_description": "Card issuer is invalid",
  "error_source": "customer",
  "error_step": "payment_authentication",
  "error_reason": "incorrect_card_details",
  "acquirer_data": {
    "auth_code": null,
    "authentication_reference_number": "100222021120200000000742753928" // Pass AEVV as the value for AMEX card transactions.
  },
  "created_at": 1620807547
}
```

```json Failure theme={null}
{
    "error": {
        "code": "BAD_REQUEST_ERROR",
        "description": "The api key provided is invalid",
        "source": "NA",
        "step": "NA",
        "reason": "NA",
        "metadata": {}
    }
}
```

## Path Parameters

**id** `string` *required*

Unique identifier of the payment to be retrieved.

## Query Parameters

**expand\[]=card** `string`

Use to expand the card details when the payment method is `card`.

## Response Parameters

**id** `string`

Unique identifier of the payment.

**entity** `string`

Indicates the type of entity.

**amount** `integer`

The payment amount in currency subunits. For example, for an amount of S\$1 enter 100.

**currency** `string`

The currency in which the payment is made. Refer to the list of [international currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies) that we support.

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
* `netbanking`
* `wallet`
* `emi`
* `upi`

**order\_id** `string`

Order id, if provided. Know more about [Orders](https://razorpay.com/docs/sg/payments/orders).

**description** `string`

Description of the payment, if any.

**international** `boolean`

Indicates whether the payment is done via an international card or a domestic one. Possible values:

* `true`: Payment made using international card.
* `false`: Payment not made using international card.

**refund\_status** `string`

The refund status of the payment. Possible values:

* `null`
* `partial`
* `full`

**amount\_refunded** `integer`

The amount refunded in currency subunits. For example, if `amount_refunded = 100`, it is equal to S\$1.

**captured** `boolean`

Indicates if the payment is captured. Possible values:

* `true`: Payment has been captured.
* `false`: Payment has not been captured.

**email** `string`

Customer email address used for the payment.

**contact** `string`

Customer contact number used for the payment.

**fee** `integer`

Fee (including GST) charged by Razorpay.

**tax** `integer`

GST charged for the payment.

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

> [!WARNING]
>
> **Watch Out!**
>
> Cardholder names for domestic cards are considered sensitive information and are not populated.

**last4** `integer`

The last 4 digits of the card number.

**network** `string`

The card network. Possible values:

* `American Express`
* `Diners Club` (Only available for private limited and registered businesses)
* `Maestro`
* `MasterCard`
* `RuPay`
* `Unknown`
* `Visa`

**type** `string`

The card type. Possible values:

* `credit`
* `debit`
* `prepaid`
* `unknown`

**issuer** `string`

The card issuer. The 4-character code denotes the issuing bank. This attribute will not be set for the card issued by a foreign bank.

**emi** `boolean`

Indicates whether the card can be used for EMI payment method. Possible values:

* `true`: Card can be used for EMI payments.
* `false`: Card cannot be used for EMI payments.

**sub\_type** `string`

The sub-type of the customer's card. Possible values:

* `customer`
* `business`\\

Know how to accept payments made by customers using [corporate cards](https://razorpay.com/docs/payments/payment-methods/cards/corporate-cards).

**upi** `object`

Details of the UPI payment received. Only applicable if `method` is `upi`.

**payer\_account\_type** `string`

The payment method used for making the payment. Possible values:

* `bank_account`
* `credit_card`
* `wallet`

**vpa** `string`

The customer's VPA (Virtual Payment Address) or UPI id used to make the payment. For example, `gauravkumar@exampleupi`.

**flow** `string`

The type of UPI flow. Possible value `in_app`. The field `flow` is present only in the case of Turbo UPI Payments.

**bank** `string`

The 4-character bank code which the customer's account is associated with. For example, `UTIB` for Axis Bank.

**vpa** `string`

The customer's VPA (Virtual Payment Address) or UPI id used to make the payment. For example, `gauravkumar@exampleupi`.

**wallet** `string`

The name of the wallet used by the customer to make the payment. For example, `payzapp`.

**acquirer\_data** `object`

An object containing unique reference numbers.

**rrn** `string`

A unique bank reference number provided by the banking partner when a refund is processed. This reference number can be used by the customer to track the status of the refund with the bank.

**authentication\_reference\_number** `string`

A unique reference number generated for RuPay card payments.

**bank\_transaction\_id** `string`

A unique reference number provided by the banking partner in case of netbanking payments.

**amount\_captured** `integer`

The amount captured for this payment, in the smallest currency unit (cents for SGD).

**provider** `string`

The payment provider used for cardless EMI, PayLater, or app-based payment methods.

**reward** `object`

Reward details applied to this payment, when an offer of type `reward` was redeemed.

**terminal\_id** `string`

Unique identifier of the terminal associated with this payment.

**invoice\_id** `string`

Unique identifier of the invoice associated with this payment.

## Errors

> [accordion] The API \{key/secret} provided is invalid.
>
> **Code:** `4xx`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after.
