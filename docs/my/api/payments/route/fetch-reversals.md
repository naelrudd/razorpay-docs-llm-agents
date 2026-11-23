> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Reversals for a Transfer

> Fetch Reversals for a Transfer using the Razorpay Curlec API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve a list of reversals made for a transfer.

```bash Curl theme={null}
curl -X GET https://api.razorpay.com/v1/transfers/trf_Lt048W7cgLdo1u/reversals \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \ 
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->transfer->fetch("trf_Lt048W7cgLdo1u")->reversals();
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.transfer.reversals(transferId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Transfer.Reversals("<transferId>", nil, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

transferId = "trf_JhemwjNekar9Za"
Razorpay::Transfer.reversals(transferId)
```

```bash CLI theme={null}
razorpay route transfers reversals trf_JMNiqyuoFoJcXb
```

```json Success theme={null}
{
   "entity":"collection",
   "count":1,
   "items":[
      {
         "id":"rvrsl_Lt09xvyzskI7KZ",
         "entity":"reversal",
         "transfer_id":"trf_Lt048W7cgLdo1u",
         "amount":50000,
         "fee":0,
         "tax":0,
         "currency":"INR",
         "notes":[

         ],
         "initiator_id":"Ghri4beeOuMTAb",
         "customer_refund_id":null,
         "utr":null,
         "created_at":1684822489
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

```json Success theme={null}
{
   "entity":"collection",
   "count":1,
   "items":[
      {
         "id":"rvrsl_Lt09xvyzskI7KZ",
         "entity":"reversal",
         "transfer_id":"trf_Lt048W7cgLdo1u",
         "amount":50000,
         "fee":0,
         "tax":0,
         "currency":"MYR",
         "notes":[

         ],
         "initiator_id":"Ghri4beeOuMTAb",
         "customer_refund_id":null,
         "utr":null,
         "created_at":1684822489
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

Unique identifier of the transfer.

## Response Parameters

**id** `string`

The unique identifier of the reversal.

**entity** `string`

The name of the entity. Here, it is `reversal`.

**transfer\_id** `string`

The unique identifier of the transfer that was reversed.

**amount** `integer`

The amount that was reversed, in paise.

**currency** `string`

ISO currency code. We support route reversals only in INR.

**initiator\_id** `string`

The unique identifier of the merchant (MID).

**created\_at** `integer`

Timestamp in Unix. This indicates the time at which the reversal was created.

## Errors

> [accordion] The API key/secret provided is invalid.
>
> **Code:** `4xx`
>
> This error occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
>
> **Solution:** Make sure the API Keys are active and entered correctly. Also, there should not be any whitespaces before or after the keys.
