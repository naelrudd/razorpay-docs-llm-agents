# Create an Instant Refund

**POST** `/v1/payments/:id/refund`

Use this endpoint to process refunds instantaneously to your customers. The instant refund is enabled by default for your account. You should set the refund speed to `optimum` when creating a refund request to ensure refunds are processed instantly. We will consider the default speed if you do not specify the same during the refund request. Know more about [setting the default speed](https://razorpay.com/docs/build/llm-docs/payments/refunds/refund-speed.md) from the Dashboard.

- Refunds will be processed at an optimal speed based on Razorpay's internal fund transfer logic.
-  If the refund can be processed instantly, Razorpay will do so irrespective of the payment method used to make the payment.

**`speed` attribute in Request** | **`speed_processed` attribute in Response** | **Description**
---
`normal` | `normal` | Refund processed via `normal` speed.
---
`optimum` | `normal` | A faster speed was not available, so processed via `normal` speed.

Once the refund moves to the `processed` state, the refund response displays the `speed_processed` parameter, the final state of the refund.

### Request

```curl: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/payments/pay_29QQoUBi66xm2f/refund \
-H 'Content-Type: application/json' \
-d '{
  "amount":500100,
  "speed":"optimum",
  "receipt":"Receipt No. 31",
  "notes":{
    "notes_key_1":"Tea, Earl Grey, Hot",
    "notes_key_2":"Tea, Earl Grey… decaf."
  }
}'

```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_29QQoUBi66xm2f";

JSONObject refundRequest = new JSONObject();
refundRequest.put("amount",100);
refundRequest.put("speed","optimum");
refundRequest.put("receipt","Receipt No. #31");
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
refundRequest.put("notes",notes);
              
Payment payment = razorpay.payments.refund(paymentId,refundRequest);

```php: PHP
$api = new Api($key_id, $secret);

$api->payment->fetch($paymentId)->refund(array("amount"=> "100","speed"=>"optimum","notes"=>array("notes_key_1"=>"Beam me up Scotty.", "notes_key_2"=>"Engage"),"receipt"=>"Receipt No. 31"));

```python: Python
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.refund(paymentId,{
  "amount": "100",
  "speed": "optimum",
  "notes": {
    "notes_key_1": "Beam me up Scotty.",
    "notes_key_2": "Engage"
  },
  "receipt": "Receipt No. 31"
})

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
	"speed": "optimum",
  "notes": map[string]interface{}{
    "key_1": "value1",
    "key_2": "value2"
  },
	"receipt": "Receipt No. #12",
}
body, err := client.Payment.Refund("",100, data, nil)

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymentId = "pay_29QQoUBi66xm2f"

para_attr = {
  "amount": "100",
  "speed": "optimum",
  "notes": {
    "notes_key_1": "Beam me up Scotty.",
    "notes_key_2": "Engage"
  },
  "receipt": "Receipt No. 31"
}
Razorpay::Payment.fetch(paymentId).refund(para_attr)

```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.refund(paymentId,{
  "amount": "100",
  "speed": "optimum",
  "notes": {
    "notes_key_1": "Beam me up Scotty.",
    "notes_key_2": "Engage"
  },
  "receipt": "Receipt No. 31"
})

```csharp: .NET
//initialize the SDK client
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_Z6t7VFTb9xHeOs";

Dictionary refundRequest = new Dictionary();
refundRequest.Add("amount",100);
refundRequest.Add("speed","optimum");
Dictionary notes = new Dictionary();
notes.Add("notes_key_1", "Tea, Earl Grey, Hot");
notes.Add("notes_key_2", "Tea, Earl Grey… decaf.");
refundRequest.Add("notes", notes);
refundRequest.Add("receipt","Receipt No. 31");

Refund refund = client.Payment.Fetch(paymentId).Refund(refundRequest);

```bash: CLI
razorpay refunds create pay_ABC123 --amount 50000 --speed optimum
```

### Response

```json: Success
{
  "id": "rfnd_FP8R8EGjGbPkVb",
  "entity": "refund",
  "amount": 500100,
  "currency": "INR",
  "payment_id": "pay_29QQoUBi66xm2f",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  },
  "receipt": "Receipt No. 31",
  "acquirer_data": {
    "arn": null
  },
  "created_at": 1597078914,
  "batch_id": null,
  "status": "processed",
  "speed_processed": "normal",
  "speed_requested": "optimum"
}
```json: Failure
{
    "error": {
        "code": "BAD_REQUEST_ERROR",
        "description": "_29QQoUBi66xm2f is not a valid id",
        "source": "business",
        "step": "payment_initiation",
        "reason": "input_validation_failed",
        "metadata": {}
    }
}
```

### Parameters

`id` _mandatory_
: `string` The unique identifier of the payment which needs to be refunded.

### Parameters

`amount` _optional_
: `integer` The amount to be refunded. Amount should be in the smallest unit of the currency in which the payment was made. **Required in case of partial refund**.
  - For a **partial refund**, enter a value lesser than the payment amount. For example, if the payment amount is ₹1200, and you want to refund only ₹200, you must pass `20000`.
  - In case of a **full refund**, enter the full payment amount. If `amount` parameter is not passed, the entire payment amount will be refunded.

  
  
**SUCCESS**

**What's New**

Refund amounts of ₹1 or lower are now supported.

  

`speed` _mandatory_
: `string` Here, it must be `optimum`. Indicates that the refund will be processed at an optimal speed based on Razorpay's internal fund transfer logic.
    - If the refund can be processed instantly, Razorpay will do so, irrespective of the payment method used to make the payment.
    - If an instant refund is not possible, Razorpay will initiate a refund that is processed at the normal speed.

`notes` _optional_
: `json object` This is a key-value pair that can be used to store additional information about the entity. It can hold a maximum of 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

`receipt` _optional_
: `string` A unique identifier provided by you for your internal reference.

### Parameters

`id`
: `string` The unique identifier of the refund. For example, `rfnd_FgRAHdNOM4ZVbO`.

`entity`
: `string` Indicates the type of entity. Here, it is `refund`.

`amount`
: `integer` The amount to be refunded (in the smallest unit of currency). 
 For example, if the refund value is 30 it will be `3000`.

`currency`
: `string` The currency of payment amount for which the refund is initiated. Check the list of [supported currencies](https://razorpay.com/docs/build/llm-docs/payments/international-payments.md#supported-currencies).

`payment_id`
: `string` The unique identifier of the payment for which a refund is initiated. For example, `pay_FgR9UMzgmKDJRi`.

`created_at`
: `integer` Unix timestamp at which the refund was created. For example, `1600856650`.

`batch_id`
: `string` This parameter is populated if the refund was created as part of a batch upload. For example, `batch_00000000000001`.

`notes`
: `json object` Key-value store for storing your reference data. A maximum of 15 key-value pairs can be included. For example, `"note_key": "Beam me up Scotty”`.

`receipt`
: `string` A unique identifier provided by you for your internal reference.

`acquirer_data`
: `array` A dynamic array consisting of a unique reference number (either RRN, ARN or UTR) that is provided by the banking partner when a refund is processed. This reference number can be used by the customer to track the status of the refund with the bank.

`status`
: `string` Indicates the state of the refund. Possible values:
  - `pending`: This state indicates that Razorpay is attempting to process the refund.
  - `processed`: This is the final state of the refund.
  - `failed`: A refund can attain the failed state in the following scenarios:

     - Normal refund is not possible for a payment which is more than 6 months old.

     - Instant Refund can sometimes fail because of customer's account or bank-related issues.

`speed_requested`
: `string` The processing mode of the refund seen in the refund response. 
 This attribute is seen in the refund response only if the `speed` parameter is set in the refund request.
Possible values:
  - `normal`: Indicates that the refund will be processed via the normal speed. The refund will take 5-7 working days.
  - `optimum`: Indicates that the refund will be processed at an optimal speed based on Razorpay's internal fund transfer logic.
     - If the refund can be processed instantly, Razorpay will do so, irrespective of the payment method used to make the payment.
     - If an instant refund is not possible, Razorpay will initiate a refund that is processed at the normal speed.

`speed_processed`
: `string` This is a parameter in the response which describes the mode used to process a refund. 
 This attribute is seen in the refund response only if the `speed` parameter is set in the refund request. Possible values:
  - `instant`: Indicates that the refund has been processed instantly via fund transfer.
  - `normal`: Indicates that the refund has been processed by the payment processing partner. The refund will take 5-7 working days.

### Errors

The API \{key/secret\} provided is invalid.
* code: 4xx
* description: The API credentials passed in the API call differ from the ones generated on the Dashboard.
* solution: The API keys must be active and entered correctly with no whitespace before or after.

\{Payment_id\} is not a valid id.
* code: 400
* description: The `payment_id` provided is invalid.
* solution: Use a valid `payment_id`.

The requested URL was not found on the server.
* code: 400
* description: Possible reasons: - The URL is wrong or is missing something.
- A POST API is executed by GET method.

* solution: - Ensure that the URL is correct and complete.
- Use the correct method, that is, POST.

\{any Extra field\} is/are not required and should not be sent.
* code: 400
* description: An additional or unrequired parameter is passed.
* solution: Ensure that you only pass the required parameters in the request body.

The refund amount provided is greater than amount captured.
* code: 400
* description: The refund amount entered is more than the amount captured.
* solution: Enter an amount equal to or less than the amount captured.

The payment has been fully refunded already.
* code: 400
* description: The `payment_id` has already been refunded fully.
* solution: Use a `payment_id` that has not been fully refunded.

Your account does not have enough balance to carry out the refund operation.
* code: 400
* description: The merchant's Razorpay balance is lower than the refund amount being requested. Refunds are paid out from the merchant balance, not directly from the original payment.
* solution: Add funds to your Razorpay account from the Dashboard or capture additional payments to increase your balance, then retry the refund.

The payment status should be captured for action to be taken.
* code: 400
* description: The payment is not in the `captured` state. This typically happens because it failed, is still `authorized`, was `cancelled` or has already been fully refunded. Refunds can only be initiated against payments that are currently in the `captured` state.
* solution: Confirm the payment status using `GET /v1/payments/:id` before refunding. Only attempt refunds on payments where `status` is `captured`.

Amount cannot be blank.
* code: 400
* description: The `amount` field was passed as `0`. Razorpay treats `0` as a missing value rather than a zero-amount refund. Omitting `amount` is valid and triggers a full refund.
* solution: Pass `amount` as a positive integer in currency subunits (paise for INR).

Instant refund not supported for the payment.
* code: 400
* description: The payment cannot be refunded at instant speed — typically because the underlying payment method, gateway or acquirer does not support instant refunds.
* solution: Retry the refund without `speed: optimum`, or omit the `speed` parameter to fall back to a normal refund.

Refund is currently not supported for this payment method.
* code: 400
* description: The payment method used for this transaction (for example, Cash on Delivery, offline, BharatQR) does not support refunds via API.
* solution: Reconcile the refund offline with the customer. Do not retry the API call.

Partial refund is currently not supported for this payment method.
* code: 400
* description: The gateway or payment method used for this payment supports only full refunds, not partial ones.
* solution: Issue a full refund by omitting the `amount` parameter, or pass the full captured amount.

Refunds cannot be created on your account.
* code: 400
* description: Refunds are disabled at the account level for the merchant making the request.
* solution: Contact Razorpay support to enable refunds on your account.

Refunds cannot be created on your account for \{payment method\} payments.
* code: 400
* description: Refunds are disabled on your account for the specific payment method used (for example, `card`, `upi`, `netbanking`, `wallet`, `emi`, `pay later`). The placeholder is replaced with the actual method name in the response.
* solution: Contact Razorpay support to enable refunds for that payment method, or use a different payment method.

Refund has already been processed.
* code: 400
* description: A refund for this payment has already moved to a final state and cannot be re-initiated using the same request.
* solution: Use the Fetch Refunds API to check the existing refund status before retrying.

The refund on this payment is blocked due to ongoing dispute investigation.
* code: 400
* description: The payment is under an active dispute (chargeback) and cannot be refunded until the dispute is resolved.
* solution: Wait for the dispute to be resolved before initiating a refund. Track the dispute status from the Razorpay Dashboard.

Duplicate receipt found for this refund request.
* code: 400
* description: The value passed in the `receipt` parameter has already been used for an earlier refund on the same payment. `receipt` is treated as an idempotency key.
* solution: Pass a unique value in `receipt`, or check the existing refund created with the same receipt before retrying.

Notes validation failed.
* code: 400
* description: The `notes` object failed validation. Possible reasons: more than 15 keys, a key longer than 255 characters, or a value longer than 512 characters.
* solution: Limit `notes` to a maximum of 15 key-value pairs, keep each key under 256 characters, and each value under 512 characters.

Request failed because another payment operation is in progress.
* code: 400
* description: A concurrent operation (such as another refund attempt or a capture) is already running for the same payment.
* solution: Wait a few seconds and retry. If the issue persists, fetch the payment and its existing refunds to confirm the current state before retrying.

Void is not supported for partial refunds.
* code: 400
* description: A partial-amount refund was requested on a payment that is still in the `authorized` state. A void can only be performed for the full authorised amount.
* solution: Either capture the payment first and then issue a partial refund, or void the full authorised amount by omitting the `amount` parameter.
