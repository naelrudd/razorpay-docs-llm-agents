> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Update a Refund

> Update a Refund using Razorpay Refunds API.

Available in
🇮🇳 India
🇺🇸 United States

Use this endpoint to update the `notes` parameter for a refund. You can modify an existing refund to update the `notes` field **only**.

* Notes can be used to record additional information about the payment.
* You can add up to 15 key-value pairs with each value of the key not exceeding 256 characters.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X PATCH https://api.razorpay.com/v1/refunds/rfnd_DfjjhJC6eDvUAi \
-H 'Content-Type: application/json' \
-d '{
    "notes": {
      "notes_key_1":"Beam me up Scotty.",
      "notes_key_2":"Engage"
    }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String refundId = "rfnd_DfjjhJC6eDvUAi";

JSONObject refundRequest = new JSONObject();
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
refundRequest.put("notes",notes);

Refund refund = razorpay.refunds.edit(refundId,refundRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->refund->fetch($refundId)->edit(array('notes'=> array('notes_key_1'=>'Beam me up Scotty.', 'notes_key_2'=>'Engage')));
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.refund.edit(refundId,{
  "notes": {
    "notes_key_1": "Beam me up Scotty.",
    "notes_key_2": "Engage"
  }
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "notes": map[string]interface{}{
    "notes_key_1":"Beam me up Scotty.",
    "notes_key_2":"Engage",
  },
}

body, err := client.Refund.Update("<refundId>", data, nil)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.refunds.edit(refundId,{
  "notes": {
    "notes_key_1": "Beam me up Scotty.",
    "notes_key_2": "Engage"
  }
}) 
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

refundId = "rfnd_DfjjhJC6eDvUAi"

para_attr = {
  "notes": {
    "notes_key_1": "Beam me up Scotty.",
    "notes_key_2": "Engage"
  }
}

Razorpay::Refund.fetch(refundId).edit(para_attr)
```

```csharp .NET theme={null}
//initialize the SDK client
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string refundId = "rfnd_Z6t7VFTb9xHeOs";

Dictionary<string, object> refundRequest = new Dictionary<string, object>();
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("notes_key_1", "Tea, Earl Grey, Hot update");
notes.Add("notes_key_2", "Tea, Earl Grey… decaf.");
refundRequest.Add("notes", notes);

Refund refund = client.Refund.Fetch(refundId).Edit(refundRequest);
```

```bash CLI theme={null}
razorpay refunds update rfnd_ABC123 --note key1="Updated note" --note key2="Another note"
```

```json Success theme={null}
{
  "id": "`rfnd_DfjjhJC6eDvUAi`",
  "entity": "refund",
  "amount": 300100,
  "currency": "INR",
  "payment_id": "pay_FIKOnlyii5QGNx",
  "notes": {
    "notes_key_1": "Beam me up Scotty.",
    "notes_key_2": "Engage"
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
      "description": "{rfnd_id} is not a valid id",
      "source": "business",
      "step": "payment_initiation",
      "reason": "input_validation_failed",
      "metadata": {}
  }
}
```

## Path Parameters

**id** `string` *required*

Unique identifier of the refund for which the `notes` field should be updated.

## Request Parameters

**notes** `json object` *required*

Additional information to be modified or added as part of `notes` field in key-pair format. Know more about [notes](https://razorpay.com/docs/api/understand.md#notes).

## Response Parameters

**id** `string`

The unique identifier of the refund. For example, `rfnd_FgRAHdNOM4ZVbO`.

**entity** `string`

Indicates the type of entity. Here, it is `refund`.

**amount** `integer`

The amount to be refunded (in the smallest unit of currency). \
&#x20;For example, if the refund value is ₹30, it will be `3000`.

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
> * A PATCH API is executed by POST method.
> * The URL is wrong or is missing something.
> * The refund id is not entered.
>
> **Solution:**
>
> * Use the correct method, that is, PATCH.
> * Ensure that the URL is correct and complete.
> * Use a valid refund id.

> [accordion] \{rfnd\_id} is not a valid id
>
> **Code:** `400`
>
> The refund id entered is invalid or incomplete.
>
> **Solution:** Use a valid and complete refund id.

> [accordion] The notes field is required
>
> **Code:** `400`
>
> The request body does not include the `notes` parameter.
>
> **Solution:** Ensure you enter the `notes` parameter in the request body.
