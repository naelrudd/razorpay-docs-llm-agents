> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Update a Payment

> Update a Payment using Razorpay Payments API.

Available in
🇮🇳 India
🇺🇸 United States

Use this endpoint to modify the `notes` field for a particular payment.

You can modify an existing payment to update the `Notes` field **only**. Notes can be used to record additional information about the payment. You can add up to 15 key-value pairs with each value of the key not exceeding 256 characters.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X PATCH https://api.razorpay.com/v1/payments/pay_CBYy6tLmJTzn3Q/
-d '{
	"notes": {
		"key1": "value1",
		"key2": "value2"
	}
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_CBYy6tLmJTzn3Q";

JSONObject paymentRequest = new JSONObject();
JSONObject notes = new JSONObject();
notes.put("key1","value1");
notes.put("key2","value2");
paymentRequest.put("notes",notes);

Payment payment = razorpay.payments.edit(paymentId,paymentRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.edit(paymentId,{
	"notes": {
		"key1": "value1",
		"key2": "value2"
	}
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

paymentId := "pay_CBYy6tLmJTzn3Q"

data := map[string]interface{}{
        "notes": map[string]interface{}{
            "key1": "value1",
            "key2": "value2",
        },
    }

body, err := client.Payment.Edit(paymentId, data, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetch($paymentId)->edit(array('notes'=> array('key_1'=> 'value1','key_2'=> 'value2')));
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymentId = "pay_CBYy6tLmJTzn3Q"

para_attr = {
	"notes": {
		"key1": "value1",
		"key2": "value2"
	}
}
Razorpay::Payment.fetch(paymentId).edit(para_attr)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.edit(paymentId,{
	"notes": {
		"key1": "value1",
		"key2": "value2"
	}
})
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
string paymentId = "pay_Z6t7VFTb9xHeOs";

Dictionary<string, object> paymentRequest = new Dictionary<string, object>();
Dictionary<string, string> notes= new Dictionary<string, string>();
notes.Add("key1", "value1");
notes.Add("key2", "value2");
paymentRequest.Add("notes", notes);

Payment payment = client.Payment.Fetch(paymentId).Edit(paymentRequest);
```

```bash CLI theme={null}
razorpay payments update pay_ABC123 --note key1="Test payment" --note key2="Another note"
```

```json Success theme={null}
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
		"key1": "value1",
		"key2": "value2"
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
  "emi_plan": {
    "issuer": "HDFC",
    "type": "credit",
    "rate": 1500,
    "duration": 24
  },
  "created_at": 1667398779,
  "upi": {
      "payer_account_type": "credit_card",
      "vpa": "gaurav.kumar@examplebank",
      "flow": "intent"
  }
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

Unique identifier of the payment for which the `Notes` field should be updated.

## Request Parameters

**notes** `json object` *required*

Contains user-defined fields and is stored for reference purposes. Know more about [notes](https://razorpay.com/docs/us/api/understand.md#notes).

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

Order id, if provided. Know more about [Orders](https://razorpay.com/docs/us/payments/orders).

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
* `credit_line`

**vpa** `string`

The customer's VPA (Virtual Payment Address) or UPI id used to make the payment. For example, `gauravkumar@exampleupi`.

**flow** `string`

The type of UPI flow. Possible values:

* `intent`: When a UPI app is selected and user is redirected to it.
* `collect`: The user enters their UPI ID and receives a notification from the UPI app. They open the app and complete the payment.
* `in_app`: In case of Turbo UPI Payments.

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

The amount captured for this payment, in the smallest currency unit (paise for INR).

**provider** `string`

The payment provider used for cardless EMI, PayLater, or app-based payment methods.

**reward** `object`

Reward details applied to this payment, when an offer of type `reward` was redeemed.

**invoice\_id** `string`

Unique identifier of the invoice associated with this payment.

**base\_amount** `integer`

The base amount for this payment, in the smallest currency unit (paise for INR).

**emi\_plan** `object`

EMI plan details for this payment when it was made via EMI. Contains the issuer, duration, and rate.

## Errors

> [accordion] The API \{key/secret} provided is invalid.
>
> **Code:** `4xx`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after.

> [accordion] amount is/are not required and should not be sent.
>
> **Code:** `400`
>
> Fields other than `notes` (such as `amount`) were sent in the PATCH request body. The Update Payment endpoint only accepts the `notes` field.
>
> **Solution:** Restrict the PATCH body to the `notes` object. Other fields on a payment are immutable after creation.

> [accordion] Notes value cannot be greater than 512 characters.
>
> **Code:** `400`
>
> One of the values inside the `notes` object exceeds the 512-character limit per value.
>
> **Solution:** Each value inside `notes` must be 512 characters or fewer. The object can hold up to 15 key-value pairs.

> [accordion] Notes key cannot be greater than 255 characters.
>
> **Code:** `400`
>
> One of the keys inside the `notes` object exceeds the 255-character limit.
>
> **Solution:** Keep each `notes` key under 256 characters.

> [accordion] Number of fields in notes should be less than or equal to 15.
>
> **Code:** `400`
>
> The `notes` object contains more than 15 key-value pairs.
>
> **Solution:** Limit `notes` to at most 15 key-value pairs.

> [accordion] Notes values themselves should not be an array.
>
> **Code:** `400`
>
> A value inside `notes` was passed as a JSON array. Only scalar values (string, number, boolean) are accepted as values.
>
> **Solution:** Convert array values into strings (for example, a comma-separated list) before sending.
