> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch a Specific Refund for a Payment

> Fetch a Specific Refund for a Payment using Razorpay Refunds API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve details of a specific refund made for a payment.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET https://api.razorpay.com/v1/payments/pay_29QQoUBi66xm2f/refunds/rfnd_AABBdHIieexn5c
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_29QQoUBi66xm2f";

String refundId = "rfnd_AABBdHIieexn5c";

Payment payment = razorpay.payments.fetchRefund(paymentId,refundId);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetch($paymentId)->fetchRefund($refundId);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.fetch_refund_id(paymentId,refundId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Payment.FetchRefund("<paymentId>","<refundId>", nil, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymentId = "pay_29QQoUBi66xm2f"

refundId = "rfnd_AABBdHIieexn5c"

Razorpay::Payment.fetch(paymentId).fetch_refund(refundId)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.fetchRefund('pay_JTVtDcN1uRYb5n','rfnd_JTvPLzbhq92ZWD')
  "notes": {
    "notes_key_1": "Beam me up Scotty.",
    "notes_key_2": "Engage"
  }
})
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
Payment payment = client.Payment.Fetch(paymentId);

Refund refund = payment.Refunds.Fetch(refundId);

}
```

```csharp .NET theme={null}
//initialize the SDK client
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string paymentId = "pay_Z6t7VFTb9xHeOs";

string refundId = "rfnd_Z6t7VFTb9xHeOs";

Refund refund = client.Payment.Fetch(paymentId).FetchRefund(refundId);
```

```bash CLI theme={null}
razorpay refunds payment-refund pay_ABC123 rfnd_ABC123
```

```json Success theme={null}
{
  "id": "rfnd_AABBdHIieexn5c",
  "entity": "refund",
  "amount": 300100,
  "currency": "SGD",
  "payment_id": "pay_FIKOnlyii5QGNx",
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
}
```

```json Failure theme={null}
{
  "error": {
      "code": "BAD_REQUEST_ERROR",
      "description": "AABBdHIieex is not a valid id",
      "source": "business",
      "step": "payment_initiation",
      "reason": "input_validation_failed",
      "metadata": {}
  }
}
```

## Path Parameters

**payment\_id** `string` *required*

Unique identifier of the payment for which the refund has been made.

**refund\_id** `string` *required*

Unique identifier of the refund to be retrieved.

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

**acquirer\_data** `object`

An object containing a unique reference number (either RRN, ARN or UTR) that is provided by the banking partner when a refund is processed. This reference number can be used by the customer to track the status of the refund with the bank.

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
> * A GET API is executed by POST method.
>
> **Solution:**
>
> * Ensure that the URL is correct and complete.
> * Use the correct method, that is, GET.

> [accordion] \_id is not a valid id
>
> **Code:** `400`
>
> * The refund or payment id entered is invalid or incomplete.
> * There is an extra space in the URL.
>
> **Solution:** Use valid refund and payment ids without any spaces.

> [accordion] The id provided does not exist
>
> **Code:** `400`
>
> The refund id entered is incomplete or invalid.
>
> **Solution:** Use a complete and valid refund id.

> [accordion] invalid request sent
>
> **Code:** `400`
>
> The `payment_id` and `refund_id` combination does not match. Either the refund does not belong to the specified payment or one of the ids is for a non-existent record.
>
> **Solution:** Pass a matching `payment_id` / `refund_id` pair. Both must exist and the refund must belong to the payment.
