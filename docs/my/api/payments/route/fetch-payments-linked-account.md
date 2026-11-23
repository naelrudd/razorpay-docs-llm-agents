> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Payments of a Linked Account

> Fetch Payments of a Linked Account using the Razorpay Curlec API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to fetch a list of all the payments received by a Linked Account. For this, you should send the Linked Account id in the `X-Razorpay-Account` API request header, as shown in the Curl example.

```bash Curl theme={null}
curl -X GET https://api.razorpay.com/v1/payments \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-H 'X-Razorpay-Account: acc_IRQWUleX4BqvYn' \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Map<String, String> headers = new HashMap<String, String>();
headers.put("X-Razorpay-Account","acc_IRQWUleX4BqvYn");
instance.addHeaders(headers);

List<Payment> payments = razorpay.payments.fetchAll();
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->all(array('X-Razorpay-Account'=> $linkedAccountId));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.all({
  'X-Razorpay-Account':  linkedAccountId
})
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.all({
   "X-Razorpay-Account":"linkedAccountId"
})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay.headers = {"X-Razorpay-Account" => "linkedAccountId"}

Razorpay::Payment.all
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

extraHeaders:= map[string]string{
  "X-Razorpay-Account": "<linkedAccountId>",
}
body, err := client.Payment.All(nil, extraHeaders)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]
");

client.addHeader("X-Razorpay-Account","acc_CPRsN1LkFccllA");

List<Payment> transfer = client.Payment.All();
```

```bash CLI theme={null}
razorpay route accounts payments acc_IEIkSOM5VJb2Lm
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "pay_JJCqynf4fQS0N1",
      "entity": "payment",
      "amount": 10000,
      "currency": "INR",
      "status": "captured",
      "order_id": "order_JJCqnZG8f3754z",
      "invoice_id": null,
      "international": false,
      "method": "netbanking",
      "amount_refunded": 0,
      "refund_status": null,
      "captured": true,
      "description": "#JJCqaOhFihfkVE",
      "card_id": null,
      "bank": "YESB",
      "wallet": null,
      "vpa": null,
      "email": "john.example@example.com",
      "contact": "+919820958250",
      "notes": [],
      "fee": 236,
      "tax": 36,
      "error_code": null,
      "error_description": null,
      "error_source": null,
      "error_step": null,
      "error_reason": null,
      "acquirer_data": {
        "bank_transaction_id": "2118867"
      },
      "created_at": 1649932775
    },
    {
      "id": "pay_JHAe1Zat55GbZB",
      "entity": "payment",
      "amount": 5000,
      "currency": "INR",
      "status": "captured",
      "order_id": "order_IluGWxBm9U8zJ8",
      "invoice_id": null,
      "international": false,
      "method": "netbanking",
      "amount_refunded": 0,
      "refund_status": null,
      "captured": true,
      "description": "Test Transaction",
      "card_id": null,
      "bank": "KKBK",
      "wallet": null,
      "vpa": null,
      "email": "gaurav.kumar@example.com",
      "contact": "+919000090000",
      "notes": {
        "address": "Razorpay Corporate Office"
      },
      "fee": 118,
      "tax": 18,
      "error_code": null,
      "error_description": null,
      "error_source": null,
      "error_step": null,
      "error_reason": null,
      "acquirer_data": {
        "bank_transaction_id": "7003347"
      },
      "created_at": 1649488316
    }
  ]
}
```

```json Failure theme={null}
{
   "error":{
      "code":"BAD_REQUEST_ERROR",
      "description":"The api key provided is invalid",
      "source":"NA",
      "step":"NA",
      "reason":"NA",
      "metadata":{

      }
   }
}
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "pay_JJCqynf4fQS0N1",
      "entity": "payment",
      "amount": 10000,
      "currency": "MYR",
      "status": "captured",
      "order_id": "order_JJCqnZG8f3754z",
      "invoice_id": null,
      "international": false,
      "method": "netbanking",
      "amount_refunded": 0,
      "refund_status": null,
      "captured": true,
      "description": "#JJCqaOhFihfkVE",
      "card_id": null,
      "bank": "YESB",
      "wallet": null,
      "vpa": null,
      "email": "nur.aisyah@example.com",
      "contact": "+60748901142",
      "notes": [],
      "fee": 236,
      "tax": 36,
      "error_code": null,
      "error_description": null,
      "error_source": null,
      "error_step": null,
      "error_reason": null,
      "acquirer_data": {
        "bank_transaction_id": "2118867"
      },
      "created_at": 1649932775
    },
    {
      "id": "pay_JHAe1Zat55GbZB",
      "entity": "payment",
      "amount": 5000,
      "currency": "MYR",
      "status": "captured",
      "order_id": "order_IluGWxBm9U8zJ8",
      "invoice_id": null,
      "international": false,
      "method": "netbanking",
      "amount_refunded": 0,
      "refund_status": null,
      "captured": true,
      "description": "Test Transaction",
      "card_id": null,
      "bank": "KKBK",
      "wallet": null,
      "vpa": null,
      "email": "siti.aisyah@example.com",
      "contact": "+60713614124",
      "notes": {
        "address": "Razorpay Corporate Office"
      },
      "fee": 118,
      "tax": 18,
      "error_code": null,
      "error_description": null,
      "error_source": null,
      "error_step": null,
      "error_reason": null,
      "acquirer_data": {
        "bank_transaction_id": "7003347"
      },
      "created_at": 1649488316
    }
  ]
}
```

```json Failure theme={null}
{
   "error":{
      "code":"BAD_REQUEST_ERROR",
      "description":"The api key provided is invalid",
      "source":"NA",
      "step":"NA",
      "reason":"NA",
      "metadata":{

      }
   }
}
```

## Response Parameters

**id** `string`

Unique identifier of the payment.

**entity** `string`

Indicates the type of entity.

**amount** `string`

The payment amount represented in the smallest unit of the currency passed. For example, for an amount of ₹200.35, the value of this field should be 20035.

**currency** `string`

The currency in which the payment is made. We support only `INR` for Route transactions.

**status** `string`

The status of the payment. Possible values:

* `created`
* `authorized`
* `captured`
* `refunded`
* `failed`

**method** `string`

The payment method used for making the payment. Here, it will be `transfer`.

**order\_id** `string`

Unique identifier of the order associated with the payment.

**description** `string`

Description of the payment, if any.

**refund\_status** `string`

The refund status of the payment. Possible values include:

* `null`
* `partial`
* `full`

**amount\_refunded** `integer`

The amount refunded in the smallest unit of the currency passed. For example, if the `amount_refunded` is 100, then it translates to 100 paise, that is ₹1. Only INR is supported.

**captured** `boolean`

Indicates whether the payment has been captured. Possible values:

* `true`: Payment has been captured.
* `false`: Payment has not been captured.

**email** `string`

Customer email address used for the payment.

**contact** `string`

Customer contact number used for the payment.

**fee** `integer`

Fee (including GST) charged by Razorpay Curlec.

**tax** `integer`

GST charged for the payment.

**error\_code** `string`

Code for the error that occurred during payment. For example, `BAD_GATEWAY_ERROR`.

**error\_description** `string`

Description of the error that occurred during payment.

**notes** `json object`

Set of key-value pairs that can be associated with an entity.  These pairs can be useful for storing additional information about the entity. A maximum of 15 key-value pairs, each of 256 characters (maximum), are supported.

**created\_at** `integer`

Timestamp, in Unix, on which the payment was created.

## Errors

> [accordion] The api key/secret provided is invalid
>
> **Code:** `4xx`
>
> This error occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
>
> **Solution:** Make sure the API Keys are active and entered correctly. Also, there should not be any whitespaces before or after the keys.

> [accordion] The id provided does not exist
>
> **Code:** `400`
>
> This error occurs when the Linked Account is invalid or does not belong to the requested merchant.
>
> **Solution:** Ensure the Linked Account is valid and belongs to the requested merchant.
