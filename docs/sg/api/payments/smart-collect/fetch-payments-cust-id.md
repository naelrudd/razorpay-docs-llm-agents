> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Payments for a Customer Identifier

> Fetch payments for a Customer Identifier using the Razorpay API

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve payment details for a single Customer Identifier by id.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET \
https://api.razorpay.com/v1/virtual_accounts/va_CminDKtoToBGmd/payments \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String virtualId = "va_DlGmm7jInLudH9";

JSONObject params = new JSONObject();
params.put("count","1");

List<VirtualAccount> virtualaccounts = instance.virtualAccounts.fetchPayments(virtualId,params);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.virtual_account.payments(virtualId,options)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('key_id', 'key_secret')

virtualId = "va_IDDYE8gYTLJCEH"

options = {"count":1}

Razorpay::VirtualAccount.fetch(virtualId).payments(options)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->virtualAccount->fetch($virtualId)->payments($options);
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.virtualAccounts.fetchPayments(virtualId,options)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.VirtualAccount.Payments("<virtualId>", nil, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

virtualId = "va_IDDYE8gYTLJCEH"

options = {"count":1}

Razorpay::VirtualAccount.fetch(virtualId).payments(options)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]

string virtualId = "va_Z6t7VFTb9xHeOs";

Dictionary<string, object> param = new Dictionary<string, object>();
param.Add("count","1");

List<Payment> virtualaccount = client.VirtualAccount.Fetch(virtualId).Payments(param);
```

```bash CLI theme={null}
razorpay smart-collect payments va_DlGmm7jInLudH8
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 1,
  "items": [
    {
      "id": "pay_JGmL38CqCHTyZZ",
      "entity": "payment",
      "amount": 1000,
      "currency": "SGD",
      "status": "captured",
      "order_id": null,
      "invoice_id": null,
      "international": false,
      "method": "upi",
      "amount_refunded": 0,
      "refund_status": null,
      "captured": true,
      "description": null,
      "card_id": null,
      "bank": null,
      "wallet": null,
      "vpa": "gaurav.kumar@exampleupi",
      "email": "alex.lim@example.com",
      "contact": "+919000090000",
      "customer_id": "cust_HWj3MjySAHSjtq",
      "notes": [],
      "fee": 12,
      "tax": 2,
      "error_code": null,
      "error_description": null,
      "error_source": null,
      "error_step": null,
      "error_reason": null,
      "acquirer_data": {
        "rrn": "209817848101"
      },
      "created_at": 1649402719
    }
  ]
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

The unique identifier of the Customer Identifier for which the payment details are to be fetched.

## Query Parameters

**from** `integer`

Timestamp, in seconds, from when payments are to be fetched.

**to** `integer`

Timestamp, in seconds, till when payments are to be fetched.

**count** `integer`

Number of payments to be fetched. The default value is 10 and the maximum value is 100. This can be used for pagination, in combination with `skip`.

**skip** `integer`

Number of records to be skipped while fetching the payments. This can be used for pagination, in combination with `count`.

## Response Parameters

**id** `string`

Unique identifier of the payment.

**entity** `string`

Indicates the type of entity.

**amount** `integer`

The payment amount in currency subunits. For example, for an amount of S\$1 enter 100.

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

The card issuer. The 4-character code denotes the issuing bank. \\

> [!NOTE]
>
> **Handy Tips**
>
> This attribute will not be set for the card issued by a foreign bank.

**emi** `boolean`

Indicates whether the card can be used for EMI payment method. Possible values:

* `true`: Card can be used for EMI payments.
* `false`: Card cannot be used for EMI payments.

**sub\_type** `string`

The sub-type of the customer's card. Possible values:

* `customer`
* `business`

> [!NOTE]
>
> **Handy Tips**
>
> Know how to accept payments made by customers using [corporate cards](https://razorpay.com/docs/payments/payment-methods/cards/corporate-cards).

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

The type of UPI flow. Possible value `in_app`.

> [!NOTE]
>
> **Handy Tips**
>
> The field `flow` is present only in the case of Turbo UPI Payments.

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

## Errors

> [accordion] The API `\<key/secret\>
> ` provided is invalid.
>
> **Code:** `4xx`
>
> Occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the dashboard.
>
> **Solution:** Make sure that the API keys are active and entered correctly. Also, make sure there are no whitespaces before or after the keys.
