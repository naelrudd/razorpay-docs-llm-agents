> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Refund Payments and Reverse Transfer from a Linked Account

> Refund Payments and reverse Transfer from a Linked Account using the Razorpay Curlec API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create refunds on a particular `payment_id`.

* The amount is deducted from your main account balance when refunding a payment. You can set the `reverse_all` parameter to `true` in the refund POST request to recover the amount from the Linked Account. This will recover the amount for every transfer made on the payment before processing the refund to the customer.

* You can automate reversals with the `reverse_all` parameter in the following refund scenarios:
  * Full refund
  * Partial refund for a payment transferred to a single account.

> [!WARNING]
>
> **Watch Out!**
>
> For partial refunds on a payment transferred to multiple accounts, the `reverse_all` parameter cannot be applied since Razorpay Curlec cannot determine which transfer to reverse partially. You will have to use the transfer reversal API to reverse this payment.

A new `reversal` entity is created internally and linked for every `reversal` defined by the `transfer_id`.

```bash Curl theme={null}
curl -X POST  https://api.razorpay.com/v1/payments/pay_JJCqynf4fQS0N1/refund \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-H 'content-type: application/json'
-d '{
  "amount": 100,
  "reverse_all": true
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_JJCqynf4fQS0N1";

JSONObject params = new JSONObject();
params.put("amount",100);
params.put("reverse_all",true);

Refund payment = razorpay.payments.refund(paymentId,params);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetch($paymentId)->refund(array('amount'=> '100','reverse_all'=> true));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.refund(paymentId,{
    amount : 100,
    reverse_all : true
})
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.refund(paymentId, {"amount": 100, "reverse_all": True})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymentId = "pay_JJCqynf4fQS0N1"

para_attr = {
    "amount" : 100,
    "reverse_all" : 1
}

Razorpay::Payment.fetch(paymentId).refund(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "reverse_all": true,
}
body, err := client.Payment.Refund("<paymentId>", <amount>, data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]
");

String paymentId = "pay_EAdwQDe4JrhOFX";

Dictionary<string, object> param = new Dictionary<string, object>();
param.Add("amount",100);
param.Add("reverse_all",true);

Refund transfer = client.Payment.Fetch("pay_MZS53duPD7FNd1").Refund(param);
```

```bash CLI theme={null}
razorpay route refund-with-reversal pay_ABC123 --amount 5000 --reverse-all=true 
```

```json Success theme={null}
{
  "id": "rfnd_JJFNlNXPHY640A",
  "entity": "refund",
  "amount": 100,
  "currency": "INR",
  "payment_id": "pay_JJCqynf4fQS0N1",
  "notes": [],
  "receipt": null,
  "acquirer_data": {
    "arn": null
  },
  "created_at": 1649941680,
  "batch_id": null,
  "status": "processed",
  "speed_processed": "normal",
  "speed_requested": "normal"
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
  "id": "rfnd_JJFNlNXPHY640A",
  "entity": "refund",
  "amount": 100,
  "currency": "MYR",
  "payment_id": "pay_JJCqynf4fQS0N1",
  "notes": [],
  "receipt": null,
  "acquirer_data": {
    "arn": null
  },
  "created_at": 1649941680,
  "batch_id": null,
  "status": "processed",
  "speed_processed": "normal",
  "speed_requested": "normal"
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

## Path Parameters

**id** `string` *required*

A unique identifier of the payment that should be refunded.

## Request Parameters

**amount** `string` *required*

The amount of refund in the smallest unit of currency. For example, for an amount of ₹200.35, the value of this field should be 20035.

**reverse\_all** `boolean`

Reverses transfer made to a linked account. Possible values:

* `true`: Reverses transfer made to a linked account.
* `false`: Does not reverse transfer made to a linked account.

## Response Parameters

**id** `string`

Unique identifier of the refund.

**entity** `string`

Indicates the type of entity. Here, it is `refund`.

**amount** `integer`

The amount of refund in the smallest unit of currency. For example, for an amount of ₹200.35, the value of this field should be 20035.

**currency** `string`

The currency of refund. Currently, only INR is supported.

**payment\_id** `string`

Unique identifier of the payment for which this refund has been requested.

**created\_at** `integer`

Timestamp, in Unix, of refund creation.

**notes** `json object`

Set of key-value pairs that can be associated with an entity. These pairs can be useful for storing additional information about the entity. A maximum of 15 key-value pairs, each of 256 characters (maximum), are supported.

**receipt** `string`

Unique identifier that you can use for internal reference.

**acquirer\_data** `array`

A dynamic array consisting of a unique reference number (either RRN, ARN or UTR) that is provided by the banking partner when a refund is processed. This reference number can be used by the customer to track the status of the refund with the bank.

## Errors

> [accordion] The api key/secret provided is invalid
>
> **Code:** `4xx`
>
> This error occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
>
> **Solution:** Make sure the API Keys are active and entered correctly. Also, there should not be any whitespaces before or after the keys.

> [accordion] The sum of amount requested for refund is greater than the available  amount
>
> **Code:** `400`
>
> This error occurs when the total transferred amount exceeds the payment amount.
>
> **Solution:** Make sure to check the amount passed with the payment made.

> [accordion] The amount must be at least INR 1.00
>
> **Code:** `400`
>
> This error occurs when the amount is less than the minimum amount. The transaction amount expressed in the currency subunit, such as paise (in INR) should always be greater than or equal to ₹1.
>
> **Solution:** Make sure the amount is equal to or greater than the minimum amount of ₹1.

> [accordion] payment\_id is not a valid id
>
> **Code:** `400`
>
> This error occurs when you pass an invalid `payment_id` in the API endpoint.
>
> **Solution:** Make sure to pass a vaild `payment_id`.
