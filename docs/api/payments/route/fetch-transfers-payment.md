> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Transfers for a Payment

> Fetch Transfers for a payment using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve the collection of all transfers created on a specific Payment id. Once the settlement against the transfer is processed, a webhook notification `settlement.processed` is sent which contains a `recipient_settlement_id`. Know more about [sample webhook payloads](https://razorpay.com/docs/webhooks/route.md#settlement-processed).

```bash Curl theme={null}
curl -X GET https://api.razorpay.com/v1/payments/pay_JGmCgTEa9OTQcX/transfers \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \ 
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_JGmCgTEa9OTQcX";

List<Payment> payments = razorpay.payments.fetchAllTransfers(paymentId)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetch('payment')->transfers();
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.fetchTransfer(paymentId)
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.transfers(paymentId)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymentId = "pay_JGmCgTEa9OTQcX"

Razorpay::Payment.fetch(paymentId).fetch_transfer
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Payment.Transfers("<paymentId>", nil, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]
");

string paymentId = "pay_E9up5WhIfMYnKW";

List<Transfer> token = client.Payment.Fetch(paymentId).Transfers();
```

```bash CLI theme={null}
razorpay route transfers fetch-by-payment pay_JMNiqyuoFoJcXb
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "trf_JJD535tJtk6Yy0",
      "entity": "transfer",
      "status": "processed",
      "source": "pay_JGmCgTEa9OTQcX",
      "recipient": "acc_IROu8Nod6PXPtZ",
      "amount": 100,
      "currency": "INR",
      "amount_reversed": 0,
      "fees": 1,
      "tax": 0,
      "notes": {
        "name": "Gaurav Kumar",
        "roll_no": "IEC2011025"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": true,
      "on_hold_until": 1671222870,
      "settlement_status": "on_hold",
      "recipient_settlement_id": null,
      "created_at": 1649933574,
      "processed_at": 1649933579,
      "error": {
        "code": null,
        "description": null,
        "reason": null,
        "field": null,
        "step": null,
        "id": "trf_JJD535tJtk6Yy0",
        "source": null,
        "metadata": null
      }
    },
    {
      "id": "trf_JJD536GI6wuz3m",
      "entity": "transfer",
      "status": "processed",
      "source": "pay_JGmCgTEa9OTQcX",
      "recipient": "acc_IRQWUleX4BqvYn",
      "amount": 300,
      "currency": "INR",
      "amount_reversed": 0,
      "fees": 1,
      "tax": 0,
      "notes": {
        "name": "Saurav Kumar",
        "roll_no": "IEC2011026"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": false,
      "on_hold_until": null,
      "settlement_status": "pending",
      "recipient_settlement_id": null,
      "created_at": 1649933574,
      "processed_at": 1649933579,
      "error": {
        "code": null,
        "description": null,
        "reason": null,
        "field": null,
        "step": null,
        "id": "trf_JJD536GI6wuz3m",
        "source": null,
        "metadata": null
      }
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
      "id": "trf_JJD535tJtk6Yy0",
      "entity": "transfer",
      "status": "processed",
      "source": "pay_JGmCgTEa9OTQcX",
      "recipient": "acc_IROu8Nod6PXPtZ",
      "amount": 100,
      "currency": "MYR",
      "amount_reversed": 0,
      "fees": 1,
      "tax": 0,
      "notes": {
        "name": "Nur Aisyah",
        "roll_no": "IEC2011025"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": true,
      "on_hold_until": 1671222870,
      "settlement_status": "on_hold",
      "recipient_settlement_id": null,
      "created_at": 1649933574,
      "processed_at": 1649933579,
      "error": {
        "code": null,
        "description": null,
        "reason": null,
        "field": null,
        "step": null,
        "id": "trf_JJD535tJtk6Yy0",
        "source": null,
        "metadata": null
      }
    },
    {
      "id": "trf_JJD536GI6wuz3m",
      "entity": "transfer",
      "status": "processed",
      "source": "pay_JGmCgTEa9OTQcX",
      "recipient": "acc_IRQWUleX4BqvYn",
      "amount": 300,
      "currency": "MYR",
      "amount_reversed": 0,
      "fees": 1,
      "tax": 0,
      "notes": {
        "name": "Siti Aisyah",
        "roll_no": "IEC2011026"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": false,
      "on_hold_until": null,
      "settlement_status": "pending",
      "recipient_settlement_id": null,
      "created_at": 1649933574,
      "processed_at": 1649933579,
      "error": {
        "code": null,
        "description": null,
        "reason": null,
        "field": null,
        "step": null,
        "id": "trf_JJD536GI6wuz3m",
        "source": null,
        "metadata": null
      }
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

## Path Parameters

**id** `string` *required*

Unique identifier of the Payment for which transfers must be retrieved.

## Response Parameters

**id** `string`

Unique identifier of the transfer.

**entity** `string`

The name of the entity. Here, it is `transfer`.

**transfer\_status** `string`

The status of the transfer. Possible values are:

* `created`
* `pending`
* `processed`
* `failed`
* `reversed`
* `partially_reversed`

**settlement\_status** `string`

The status of the settlement. Possible values are:

* `pending`
* `on_hold`
* `settled`

**source** `string`

Unique identifier of the transfer source. The source can be a `payment` or an `order`.

**recipient** `string`

Unique identifier of the transfer destination, that is, the Linked Account.

**amount** `integer`

The amount to be transferred to the Linked Account, in paise. For example, for an amount of ₹200.35, the value of this field should be 20035.

**currency** `string`

ISO currency code. We support route transfers only in `INR`.

**amount\_reversed** `integer`

Amount reversed from this transfer for refunds.

**notes** `json object`

Set of key-value pairs that can be associated with an entity. These pairs can be useful for storing additional information about the entity. A maximum of 15 key-value pairs, each of 256 characters (maximum), are supported. For example, `"region": "south", "city": "Bangalore"`.

**error** `string`

Provides error details that may occur during transfers.

**code** `string`

Type of the error.

**description** `string`

Error description.

**field** `string`

Name of the parameter in the API request that caused the error.

**source** `string`

The point of failure in the specific operation. For example, customer, business and so on.

**step** `string`

The stage where the transaction failure occurred. Stages can be different depending on the payment method used to make the transaction.

**id** `string`

Unique identifier of the transfer.

**reason** `string`

The exact error reason. It can be handled programmatically.

**linked\_account\_notes** `array`

List of keys from the `notes` object which needs to be shown to Linked Accounts on their Dashboard. For example, `"region", "city"`. Only the keys will be shown, not values.

**on\_hold** `boolean`

Indicates whether the account settlement for transfer is on hold. Possible values:

* `true`: Puts the settlement on hold.
* `false`: Releases the settlement.

**on\_hold\_until** `integer`

Timestamp, in Unix format, indicates until when the settlement of the transfer must be put on hold. If no value is passed, the settlement is put on hold indefinitely.

**recipient\_settlement\_id** `string`

Unique identifier of the settlement.

**created\_at** `integer`

Timestamp, in Unix, at which the record was created.

## Errors

> [accordion] The api key/secret provided is invalid
>
> **Code:** `4xx`
>
> This error occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
>
> **Solution:** Make sure the API Keys are active and entered correctly. Also, there should not be any whitespaces before or after the keys.

> [accordion] payment\_id is not a valid id
>
> **Code:** `400`
>
> This error occurs when you pass an invalid `payment_id` in the API endpoint.
>
> **Solution:** Make sure to pass a vaild `payment_id`.
