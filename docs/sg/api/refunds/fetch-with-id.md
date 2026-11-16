> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Refund With ID

> Fetch Refund With id using Razorpay Refunds API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve the refund using the id.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \

-X GET https://api.razorpay.com/v1/refunds/rfnd_DfjjhJC6eDvUAi
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String refundId = "rfnd_DfjjhJC6eDvUAi";

List<Refund> refund = razorpay.refunds.fetch(refundId);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->refund->fetch($refundId);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.refund.fetch(refundId)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

refundId = "rfnd_DfjjhJC6eDvUAi"

Razorpay::Refund.fetch(refundId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Refund.Fetch("<refundId>", nil, nil)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.refunds.fetch(refundId)
```

```csharp .NET theme={null}
//initialize the SDK client
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string refundId = "rfnd_Z6t7VFTb9xHeOs";

Refund refund = client.Refund.Fetch(refundId);
```

```bash CLI theme={null}
razorpay refunds fetch rfnd_ABC123
```

```json Success theme={null}
{
  "id": "rfnd_DfjjhJC6eDvUAi",
  "entity": "refund",
  "amount": 6000,
  "currency": "SGD",
  "payment_id": "pay_EpkFDYRirena0f",
  "notes": {
    "comment": "Issuing an instant refund"
  },
  "receipt": null,
  "acquirer_data": {
    "arn": "10000000000000"
  },
  "created_at": 1589521675,
  "batch_id": null,
  "status": "processed",
  "speed_processed": "optimum",
  "speed_requested": "optimum"
}
```

```json Failure theme={null}
{
    "error": {
        "code": "BAD_REQUEST_ERROR",
        "description": "The requested URL was not found on the server.",
        "source": "NA",
        "step": "NA",
        "reason": "NA",
        "metadata": {}
    }
}
```

## Path Parameters

**id** `string` *required*

Unique identifier of the refund which is to be retrieved.

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
> The refund id entered is invalid.
>
> **Solution:** Use a valid refund id.

> [accordion] The id provided does not exist
>
> **Code:** `400`
>
> The refund id entered is incomplete or invalid.
>
> **Solution:** Use a complete and valid refund id.
