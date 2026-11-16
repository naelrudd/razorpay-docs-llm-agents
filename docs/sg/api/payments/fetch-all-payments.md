> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch All Payments

> Fetch all Payments using Razorpay Payments API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve details of all the payments. By default, only the last 10 records are displayed. You can use the `count` and `skip` parameters to retrieve the specific number of records that you need.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X GET https://api.razorpay.com/v1/payments?from=1593320020&to=1624856020&count=2&skip=1
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject params = new JSONObject();
params.put("count","2");

List<Payment> payment = razorpay.payments.fetchAll(params);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.all(option)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
  "count": 2,
}

body, err := client.Payment.All(data, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->all($options)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

option = {"count":2}

Razorpay::Payment.all(option)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.all(option)
```

```csharp .NET theme={null}
Dictionary<`string`, object> options = new Dictionary<`string`, object>();

//supported option filters (from, to, count, skip)
options.Add("count", 2);
options.Add("skip", 1000);

RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
List<Payment> result = client.Payment.All(options);

import java.util.List;
import org.json.JSONObject;
import com.razorpay.Payment;
import com.razorpay.RazorpayClient;
import com.razorpay.RazorpayException;
```

```bash CLI theme={null}
razorpay payments list --count 10 --skip 0 --from 1776754530 --to 1776758130
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "pay_KbCFyQ0t9Lmi1n",
      "entity": "payment",
      "amount": 1000,
      "currency": "SGD",
      "status": "authorized",
      "order_id": null,
      "invoice_id": null,
      "international": false,
      "method": "netbanking",
      "amount_refunded": 0,
      "refund_status": null,
      "captured": false,
      "description": "Test Transaction",
      "card_id": null,
      "bank": "IBKL",
      "wallet": null,
      "vpa": null,
      "email": "gaurav.kumar@gmail.com",
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
        "bank_transaction_id": "5733649"
      },
      "created_at": 1667397881
    },
    {
      "id": "pay_KbCEDHh1IrU4RJ",
      "entity": "payment",
      "amount": 1000,
      "currency": "SGD",
      "status": "authorized",
      "order_id": null,
      "invoice_id": null,
      "international": false,
      "method": "upi",
      "amount_refunded": 0,
      "refund_status": null,
      "captured": false,
      "description": "Test Transaction",
      "card_id": null,
      "bank": null,
      "wallet": null,
      "vpa": "gaurav.kumar@okhdfcbank",
      "upi": {
      "payer_account_type": "credit_card",
      "vpa": "gaurav.kumar@examplebank",
      "flow": "intent"
      }
      "email": "gaurav.kumar@gmail.com",
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
        "rrn": "230901495295",
        "upi_transaction_id": "6935B87A72C2A7BC83FA927AA264AD53"
      },
      "created_at": 1667397781
    }
  ]
}
```

```json Failure theme={null}
{
    "error": {
        "code": "BAD_REQUEST_ERROR",
        "description": "from must be between 946684800 and 4765046400",
        "source": "business",
        "step": "payment_initiation",
        "reason": "input_validation_failed",
        "metadata": {}
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

**issuer** `string`

The card issuer. The 4-character code denotes the issuing bank. This attribute will not be set for the card issued by a foreign bank.

**emi** `boolean`

Indicates whether the card can be used for EMI payment method. Possible values:

* `true`: Card can be used for EMI payments.
* `false`: Card cannot be used for EMI payments.

**sub\_type** `string`

The sub-type of the customer's card. Possible values:

* `customer`
* `business`
  Know how to accept payments made by customers using [corporate cards](https://razorpay.com/docs/payments/payment-methods/cards/corporate-cards).

**bank** `string`

The 4-character bank code which the customer's account is associated with. For example, `UTIB` for Axis Bank.

**vpa** `string`

The customer's VPA (Virtual Payment Address) or UPI id used to make the payment. For example, `gauravkumar@exampleupi`.

**wallet** `string`

The name of the wallet used by the customer to make the payment. For example, `payzapp`.

**acquirer\_data** `array`

A dynamic array consisting of a unique reference numbers.

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

> [accordion] from must be between 946684800 and 4765046400
>
> **Code:** `400`
>
> The time range entered is invalid.
>
> **Solution:** Enter a valid time range between `946684800` and `4765046400`.

> [accordion] The count must be at least 1.
>
> **Code:** `400`
>
> `count=0` (or otherwise less than 1) passed in the query string.
>
> **Solution:** Pass `count` as a positive integer between 1 and 100.

> [accordion] The count may not be greater than 100.
>
> **Code:** `400`
>
> `count` value above 100 in the query string. The Payments list endpoint caps per-page results at 100.
>
> **Solution:** Use a `count` of 100 or fewer. For larger datasets, paginate using the `skip` parameter.

> [accordion] The count must be an integer.
>
> **Code:** `400`
>
> `count` query parameter is non-numeric (for example, `count=abc`).
>
> **Solution:** Pass `count` as a positive integer.

> [accordion] from must be an integer.
>
> **Code:** `400`
>
> `from` query parameter is not a UNIX-epoch integer (for example, an ISO date string was passed).
>
> **Solution:** Pass `from` as a UNIX-epoch integer (for example, `1700000000`), not a human-readable date.

> [accordion] to must be an integer.
>
> **Code:** `400`
>
> `to` query parameter is not a UNIX-epoch integer.
>
> **Solution:** Pass `to` as a UNIX-epoch integer.

> [accordion] The skip must be at least 0.
>
> **Code:** `400`
>
> `skip` query parameter was passed as a negative integer.
>
> **Solution:** Pass `skip` as a non-negative integer (0 or higher).

> [accordion] The skip must be an integer.
>
> **Code:** `400`
>
> `skip` query parameter is non-numeric.
>
> **Solution:** Pass `skip` as a non-negative integer.
