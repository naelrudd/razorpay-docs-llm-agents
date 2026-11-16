> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Multiple Refunds for a Payment

> Fetch Multiple Refunds for a Payment using Razorpay Refunds API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve multiple refunds for a payment. By default, only the last 10 refunds are returned. You can use `count` and `skip` parameters to change that behaviour.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET https://api.razorpay.com/v1/payments/pay_29QQoUBi66xm2f/refunds?from=1500826740&to=1500826760
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_29QQoUBi66xm2f";

JSONObject params = new JSONObject();
params.put("count","1");

List<Payment> payments = razorpay.payments.fetchAllRefunds(paymentId,params);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetch($paymentId)->fetchMultipleRefund($option);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.fetch_multiple_refund(paymentId,option)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

option := map[string]interface{}{
    "count" : 1,
}
body, err := client.Payment.FetchMultipleRefund("<paymentId>",option, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymentId = "pay_29QQoUBi66xm2f"

option = {"count":1}

Razorpay::Payment.fetch_multiple_refund(paymentId,option)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.fetchMultipleRefund(paymentId,option)
```

```csharp .NET theme={null}
//initialize the SDK client
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_Z6t7VFTb9xHeOs";

Dictionary<string, object> paramRequest = new Dictionary<string, object>();
paramRequest.add("count","1");

List<Refund> refund = client.Payment.Fetch(paymentId).AllRefunds(paramRequest)
```

```bash CLI theme={null}
razorpay refunds payment-refunds pay_ABC123 --count 10 --skip 0
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "rfnd_FP8DDKxqJif6ca",
      "entity": "refund",
      "amount": 300100,
      "currency": "SGD",
      "payment_id": "pay_29QQoUBi66xm2f",
      "notes": {
        "comment": "Comment for refund"
      },
      "receipt": null,
      "acquirer_data": {
        "arn": "10000000000000"
      },
      "created_at": 1597078124,
      "batch_id": null,
      "status": "processed",
      "speed_processed": "normal",
      "speed_requested": "optimum"
    },
    {
      "id": "rfnd_FP8DRfu3ygfOaC",
      "entity": "refund",
      "amount": 200000,
      "currency": "SGD",
      "payment_id": "pay_29QQoUBi66xm2f",
      "notes": {
        "comment": "Comment for refund"
      },
      "receipt": null,
      "acquirer_data": {
        "arn": "10000000000000"
      },
      "created_at": 1597078137,
      "batch_id": null,
      "status": "processed",
      "speed_processed": "normal",
      "speed_requested": "optimum"
    }
  ]
}
```

```json Failure theme={null}
{
    "error": {
        "code": "BAD_REQUEST_ERROR",
        "description": "The id provided does not exist",
        "source": "business",
        "step": "payment_initiation",
        "reason": "input_validation_failed",
        "metadata": {}
    }
}
```

## Path Parameters

**id** `string` *required*

Unique identifier of the payment for which refund has been requested.

## Query Parameters

**from** `integer`

Unix timestamp at which the refunds were created.

**to** `integer`

Unix timestamp till which the refunds were created.

**count** `integer`

The number of refunds to fetch for the payment.

**skip** `integer`

The number of refunds to be skipped for the payment.

## Response Parameters

**id** `string`

The unique identifier of the refund. For example, `rfnd_FgRAHdNOM4ZVbO`.

**entity** `string`

Indicates the type of entity. Here, it is `refund`.

**amount** `integer`

The amount to be refunded (in the smallest unit of currency). \
&#x20;For example, if the refund value is S\$30, it will be `3000`.

**currency** `string`

The currency of payment amount for which the refund is initiated. Check the list of [supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).

**payment\_id** `string`

The unique identifier of the payment for which a refund is initiated. For example, `pay_FgR9UMzgmKDJRi`.

**created\_at** `integer`

Unix timestamp at which the refund was created. For example, `1600856650`.

**batch\_id** `string`

This parameter is populated if the refund was created as part of a batch upload. For example, `batch_00000000000001`.

**notes** `json object`

Key-value store for storing your reference data. A maximum of 15 key-value pairs can be included. For example, `"note_key": "Beam me up Scotty”`.

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

> [accordion] \_id is not a valid id
>
> **Code:** `400`
>
> The `payment_id` entered is invalid or incomplete.
>
> **Solution:** Use a valid `payment_id`.

> [accordion] The id provided does not exist
>
> **Code:** `400`
>
> The `payment_id` is not entered.
>
> **Solution:** Use a valid `payment_id`.

> [accordion] count must be an integer between 1 and 100.
>
> **Code:** `400`
>
> An invalid value was passed for the `count` query parameter. The API returns variants of this error depending on the input: `The count must be at least 1.` (for `count=0`), `The count must be no greater than 100.` (for values above 100), `The count must be no less than 1.` (for negative values) or `The count must be an integer.` (for non-integer values like `count=abc`).
>
> **Solution:** Pass `count` as a positive integer between 1 and 100.

> [accordion] skip must be a non-negative integer.
>
> **Code:** `400`
>
> An invalid value was passed for the `skip` query parameter. The API returns `The skip must be no less than 0.` for negative values, or `The skip must be an integer.` for non-integer values.
>
> **Solution:** Pass `skip` as a non-negative integer (0 or higher).

> [accordion] from and to must be UNIX-epoch integers.
>
> **Code:** `400`
>
> A non-integer value (for example a human-readable date like `2024-01-01`) was passed for `from` or `to`. The API returns `The from must be an integer.` or `The to must be an integer.` respectively. Negative values produce `The from must be no less than 0.`
>
> **Solution:** Pass `from` and `to` as non-negative UNIX-epoch integers (seconds), not as human-readable dates.
