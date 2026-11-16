> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Normal Refund

> Create a Normal Refund using Razorpay Refunds API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create a normal refund for a payment.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/payments/pay_29QQoUBi66xm2f/refund \
-H 'Content-Type: application/json' \
-d '{
  "amount": 500100
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_29QQoUBi66xm2f";

JSONObject refundRequest = new JSONObject();
refundRequest.put("amount",100);
refundRequest.put("speed","normal");
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
refundRequest.put("notes",notes);
refundRequest.put("receipt","Receipt No. #31");

Payment payment = razorpay.payments.refund(paymentId,refundRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetch($paymentId)->refund(array("amount"=> "100", "speed"=>"normal", "notes"=>array("notes_key_1"=>"Beam me up Scotty.", "notes_key_2"=>"Engage"), "receipt"=>"Receipt No. 31"));
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.refund(paymentId,{
  "amount": "100",
  "speed": "normal",
  "notes": {
    "notes_key_1": "Beam me up Scotty.",
    "notes_key_2": "Engage"
  },
  "receipt": "Receipt No. 31"
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
  "speed": "normal",
  "notes": map[string]interface{}{
    "key_1": "value1",
    "key_2": "value2"
  },
}
body, err := client.Payment.Refund("<paymentId>",1200, data, nil)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.refund(paymentId,{
  "amount": "100",
  "speed": "normal",
  "notes": {
    "notes_key_1": "Beam me up Scotty.",
    "notes_key_2": "Engage"
  },
  "receipt": "Receipt No. 31"
})
```

```csharp .NET theme={null}
//initialize the SDK client
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string paymentId = "pay_Z6t7VFTb9xHeOs";

Dictionary<string, object> refundRequest = new Dictionary<string, object>();
refundRequest.Add("amount", 200);
refundRequest.Add("speed", "normal");
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("notes_key_1", "Tea, Earl Grey, Hot");
notes.Add("notes_key_2", "Tea, Earl Grey… decaf.");
refundRequest.Add("notes", notes);
refundRequest.Add("receipt", "Receipt No. #32");

Refund refund = client.Payment.Fetch(paymentId).Refund(refundRequest);
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymentId = "pay_29QQoUBi66xm2f"

para_attr = {
  "amount": "100",
  "speed": "normal",
  "notes": {
    "notes_key_1": "Beam me up Scotty.",
    "notes_key_2": "Engage"
  },
  "receipt": "Receipt No. 31"
}

Razorpay::Payment.fetch(paymentId).refund(para_attr)
```

```bash CLI theme={null}
razorpay refunds create pay_ABC123 --amount 50000 --note key1="Test refund"
```

```json Success theme={null}
{
  "id": "rfnd_FP8QHiV938haTz",
  "entity": "refund",
  "amount": 500100,
  "receipt": "Receipt No. 31",
  "currency": "SGD",
  "payment_id": "pay_29QQoUBi66xm2f",
  "notes": [],
  "receipt": null,
  "acquirer_data": {
    "arn": null
  },
  "created_at": 1597078866,
  "batch_id": null,
  "status": "processed",
  "speed_processed": "normal",
  "speed_requested": "normal"
}
```

```json Failure theme={null}
{
    "error": {
        "code": "BAD_REQUEST_ERROR",
        "description": "The amount must be at least SGD 1.00",
        "source": "business",
        "step": "payment_initiation",
        "reason": "input_validation_failed",
        "metadata": {},
        "field": "amount"
    }
}
```

## Path Parameters

**id** `string` *required*

The unique identifier of the payment which needs to be refunded.

## Request Parameters

**amount** `integer`

The amount to be refunded. Amount should be in the smallest unit of the currency in which the payment was made. In the case of three decimal currencies, such as KWD, BHD and OMR, to refund a payment of 295.991, pass the value as `295990`. And in the case of zero decimal currencies such as JPY, to refund a payment of 295, pass the value as `295`.

* For a **partial refund**, enter a value lesser than the payment amount. For example, if the payment amount is S$1500 and you want to refund only S$500, you must pass `50000`.
* For **full refund**, enter the entire payment amount. If the `amount` parameter is not passed, the entire payment amount will be refunded.

> [!WARNING]
>
> **Watch Out!**
>
> As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to refund a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.

**speed** `string`

The speed at which the refund is to be processed. The default value is `normal`. Refund will be processed via the normal speed, and the customer will receive the refund within 5-7 working days.

**notes** `json object`

Key-value pairs used to store additional information. A maximum of 15 key-value pairs can be included.

**receipt** `string`

A unique identifier provided by you for your internal reference.

## Response Parameters

**id** `string`

The unique identifier of the refund. For example, `rfnd_FgRAHdNOM4ZVbO`.

**entity** `string`

Indicates the type of entity. Here, it is `refund`.

**amount** `integer`

The amount to be refunded (in the smallest unit of currency). \
&#x20;For example, if the refund value is S\$30 it will be `3000`.

**currency** `string`

The currency of payment amount for which the refund is initiated. Check the list of [supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).

**payment\_id** `string`

The unique identifier of the payment for which a refund is initiated. For example, `pay_FgR9UMzgmKDJRi`.

**created\_at** `integer`

Unix timestamp at which the refund was created. For example, `1600856650`.

**batch\_id** `string`

This parameter is populated if the refund was created as part of a batch upload. For example, `batch_00000000000001`.

**notes** `json object`

Key-value store for storing your reference data. A maximum of 15 key-value pairs can be included. For example, `"note_key": "Beam me up Scotty"`.

**receipt** `string`

A unique identifier provided by you for your internal reference.

**acquirer\_data** `array`

A dynamic array consisting of a unique reference number (either RRN, ARN or UTR) that is provided by the banking partner when a refund is processed. This reference number can be used by the customer to track the status of the refund with the bank.

**status** `string`

Indicates the state of the refund. Possible values:

* `pending`: This state indicates that Razorpay is attempting to process the refund.
* `processed`: This is the final state of the refund.
* `failed`: A refund can attain the failed state in the following scenarios:\\

  * Normal refund is not possible for a payment which is more than 6 months old.\\

  * Instant Refund can sometimes fail because of customer's account or bank-related issues.

**speed\_requested** `string`

The processing mode of the refund seen in the refund response. \
&#x20;This attribute is seen in the refund response only if the `speed` parameter is set in the refund request.\
Possible values:

* `normal`: Indicates that the refund will be processed via the normal speed. The refund will take 5-7 working days.
* `optimum`: Indicates that the refund will be processed at an optimal speed based on Razorpay's internal fund transfer logic.
  * If the refund can be processed instantly, Razorpay will do so, irrespective of the payment method used to make the payment.
  * If an instant refund is not possible, Razorpay will initiate a refund that is processed at the normal speed.

**speed\_processed** `string`

This is a parameter in the response which describes the mode used to process a refund. \
&#x20;This attribute is seen in the refund response only if the `speed` parameter is set in the refund request. Possible values:

* `instant`: Indicates that the refund has been processed instantly via fund transfer.
* `normal`: Indicates that the refund has been processed by the payment processing partner. The refund will take 5-7 working days.

## Errors

> [accordion] The API \{key/secret} provided is invalid.
>
> **Code:** `4xx`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after.

> [accordion] \{Payment\_id} is not a valid id.
>
> **Code:** `400`
>
> The `payment_id` provided is invalid.
>
> **Solution:** Use a valid `payment_id`.

> [accordion] The requested URL was not found on the server.
>
> **Code:** `400`
>
> Possible reasons:
>
> * The URL is wrong or is missing something.
> * A POST API is executed by GET method.
>
> **Solution:**
>
> * Ensure that the URL is correct and complete.
> * Use the correct method, that is, POST.

> [accordion] \{any Extra field} is/are not required and should not be sent.
>
> **Code:** `400`
>
> An additional or unrequired parameter is passed.
>
> **Solution:** Ensure that you only pass the required parameters in the request body.

> [accordion] The refund amount provided is greater than amount captured.
>
> **Code:** `400`
>
> The refund amount entered is more than the amount captured.
>
> **Solution:** Enter an amount equal to or less than the amount captured.

> [accordion] The amount must be at least
> SGD 1.00.
>
> **Code:** `400`
>
> The refund amount entered is less than .
>
> **Solution:** Enter an amount of at least .

> [accordion] The payment has been fully refunded already.
>
> **Code:** `400`
>
> The `payment_id` has already been refunded fully.
>
> **Solution:** Use a `payment_id` that has not been fully refunded.

> [accordion] The amount must be an integer.
>
> **Code:** `400`
>
> A non-integer value (for example a string or a decimal) was passed for the `amount` field.
>
> **Solution:** Pass `amount` as an integer in currency subunits (for example, `100` for S\$1.00).

> [accordion] The selected speed is invalid.
>
> **Code:** `400`
>
> An unsupported value was passed for the `speed` field.
>
> **Solution:** Use one of the supported values: `normal` or `optimum`.

> [accordion] Your account does not have enough balance to carry out the refund operation.
>
> **Code:** `400`
>
> The merchant's Razorpay balance is lower than the refund amount being requested. Refunds are paid out from the merchant balance, not directly from the original payment.
>
> **Solution:** Add funds to your Razorpay account from the Dashboard or capture additional payments to increase your balance, then retry the refund.

> [accordion] The payment status should be captured for action to be taken.
>
> **Code:** `400`
>
> The payment is not in the `captured` state. This typically happens because it failed, is still `authorized`, was `cancelled` or has already been fully refunded. Refunds can only be initiated against payments that are currently in the `captured` state.
>
> **Solution:** Confirm the payment status using `GET /v1/payments/:id` before refunding. Only attempt refunds on payments where `status` is `captured`.

> [accordion] Amount cannot be blank.
>
> **Code:** `400`
>
> The `amount` field was passed as `0`. Razorpay treats `0` as a missing value rather than a zero-amount refund. Omitting `amount` is valid and triggers a full refund.
>
> **Solution:** Pass `amount` as a positive integer in currency subunits (cents for SGD).

> [accordion] Refund is currently not supported for this payment method.
>
> **Code:** `400`
>
> The payment method used for this transaction (for example, Cash on Delivery, offline, BharatQR) does not support refunds via API.
>
> **Solution:** Reconcile the refund offline with the customer. Do not retry the API call.

> [accordion] Partial refund is currently not supported for this payment method.
>
> **Code:** `400`
>
> The gateway or payment method used for this payment supports only full refunds, not partial ones.
>
> **Solution:** Issue a full refund by omitting the `amount` parameter, or pass the full captured amount.

> [accordion] Refunds cannot be created on your account.
>
> **Code:** `400`
>
> Refunds are disabled at the account level for the merchant making the request.
>
> **Solution:** Contact Razorpay support to enable refunds on your account.

> [accordion] Refunds cannot be created on your account for \{payment method} payments.
>
> **Code:** `400`
>
> Refunds are disabled on your account for the specific payment method used (for example, `card`, `upi`, `netbanking`, `wallet`, `emi`, `pay later`). The placeholder is replaced with the actual method name in the response.
>
> **Solution:** Contact Razorpay support to enable refunds for that payment method, or use a different payment method.

> [accordion] Refund has already been processed.
>
> **Code:** `400`
>
> A refund for this payment has already moved to a final state and cannot be re-initiated using the same request.
>
> **Solution:** Use the Fetch Refunds API to check the existing refund status before retrying.

> [accordion] The refund on this payment is blocked due to ongoing dispute investigation.
>
> **Code:** `400`
>
> The payment is under an active dispute (chargeback) and cannot be refunded until the dispute is resolved.
>
> **Solution:** Wait for the dispute to be resolved before initiating a refund. Track the dispute status from the Razorpay Dashboard.

> [accordion] Duplicate receipt found for this refund request.
>
> **Code:** `400`
>
> The value passed in the `receipt` parameter has already been used for an earlier refund on the same payment. `receipt` is treated as an idempotency key.
>
> **Solution:** Pass a unique value in `receipt`, or check the existing refund created with the same receipt before retrying.

> [accordion] Notes validation failed.
>
> **Code:** `400`
>
> The `notes` object failed validation. Possible reasons: more than 15 keys, a key longer than 255 characters, or a value longer than 512 characters.
>
> **Solution:** Limit `notes` to a maximum of 15 key-value pairs, keep each key under 256 characters, and each value under 512 characters.

> [accordion] Request failed because another payment operation is in progress.
>
> **Code:** `400`
>
> A concurrent operation (such as another refund attempt or a capture) is already running for the same payment.
>
> **Solution:** Wait a few seconds and retry. If the issue persists, fetch the payment and its existing refunds to confirm the current state before retrying.
