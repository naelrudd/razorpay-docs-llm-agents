> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch All Payments (With Expanded EMI Details)

> Fetch all Payments (With Expanded EMI Details) using Razorpay Payments API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve the expanded EMI plan details of the payments, in which the payment method is `emi`.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X GET https://api.razorpay.com/v1/payments?expand[]=emi
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject params = new JSONObject();
params.put("expand[]","emi");

List<Payment> payment = razorpay.payments.fetchAll(params);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.all({'expand[]':'emi'})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
      "expand[]":"emi",
    }

body, err := client.Payment.All(data, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->all(array('expand[]'=>'emi')
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay::Payment.all({'expand[]':'emi'})
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.all({'expand[]':'emi'})
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> paramRequest = new Dictionary<string, object>();
paramRequest.Add("expand[]","emi");

List<Payment> payment = client.Payment.All(paramRequest);
```

```bash CLI theme={null}
razorpay payments list --expand emi
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "pay_KbCVlLqUbb3VhA",
      "entity": "payment",
      "amount": 400000,
      "currency": "INR",
      "status": "authorized",
      "order_id": null,
      "invoice_id": null,
      "international": false,
      "method": "emi",
      "amount_refunded": 0,
      "refund_status": null,
      "captured": false,
      "description": "Test Transaction",
      "card_id": "card_KbCVlPnxWRlOpH",
      "bank": "HDFC",
      "wallet": null,
      "vpa": null,
      "email": "gaurav.kumar@example.com",
      "contact": "+919000090000",
      "notes": {
        "address": "Razorpay Corporate Office"
      },
      "fee": null,
      "tax": null,
      "error_code": null,
      "error_description": null,
      "error_source": null,
      "error_step": null,
      "error_reason": null,
      "acquirer_data": {
        "auth_code": "205480"
      },
      "emi": {
        "issuer": "HDFC",
        "type": "credit",
        "rate": 1500,
        "duration": 24
      },
      "created_at": 1667398779
    },
    {
      "id": "pay_KbCUSPzYZdEVGA",
      "entity": "payment",
      "amount": 300000,
      "currency": "INR",
      "status": "authorized",
      "order_id": null,
      "invoice_id": null,
      "international": false,
      "method": "emi",
      "amount_refunded": 0,
      "refund_status": null,
      "captured": false,
      "description": "Test Transaction",
      "card_id": "card_KbCUSTVRUci85O",
      "bank": "HDFC",
      "wallet": null,
      "vpa": null,
      "email": "gaurav.kumar@example.com",
      "contact": "+919000090000",
      "notes": {
        "address": "Razorpay Corporate Office"
      },
      "fee": null,
      "tax": null,
      "error_code": null,
      "error_description": null,
      "error_source": null,
      "error_step": null,
      "error_reason": null,
      "acquirer_data": {
        "auth_code": "102251"
      },
      "emi": {
        "issuer": "HDFC",
        "type": "credit",
        "rate": 1500,
        "duration": 12
      },
      "created_at": 1667398705
    }
  ]
}
```

```json Failure theme={null}
{
    "error": {
        "code": "BAD_REQUEST_ERROR",
        "description": "Value of each expand must be one of following types: card, emi, transaction, transaction.settlement, refunds, offers, token",
        "source": "business",
        "step": "payment_initiation",
        "reason": "input_validation_failed",
        "metadata": {},
        "field": "expand.0"
    }
}
```

## Query Parameters

**from** `integer`

UNIX timestamp, in seconds, from when payments are to be fetched.

**to** `integer`

UNIX timestamp, in seconds, till when payments are to be fetched.

**count** `integer`

Number of payments to be fetched. \
&#x20;Default value is 10. Maximum value is 100. This can be used for pagination, in combination with the `skip` parameter.

**skip** `integer`

Number of records to be skipped while fetching the payments.

**expand\[]** `array`

Used to retrieve additional information about the payment, the method used to make the payment. The response will include a sub-entity if this parameter is used. \
Possible values:

* `card`: Expanded card details, usable for card and EMI payments.
* `emi`: Expanded EMI plan details, usable for EMI payments.

## Response Parameters

**id** `string`

Unique identifier of the payment.

**entity** `string`

Indicates the type of entity.

**amount** `integer`

The payment amount in currency subunits. For example, for an amount of ₹1 enter 100.

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

Order id, if provided. Know more about [Orders](https://razorpay.com/docs/payments/orders).

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

The amount refunded in currency subunits. For example, if `amount_refunded = 100`, it is equal to ₹1.

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

**token\_id** `string`

Unique identifier of the token associated with this payment.

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

> [accordion] Value of each expand must be one of following types: card, emi, transaction, refunds, offers, token, transaction.settlement.
>
> **Code:** `400`
>
> The value for the `expand` parameter is incorrect.
>
> **Solution:** Enter the correct value for the `expand` parameter. Here it is `emi`.
