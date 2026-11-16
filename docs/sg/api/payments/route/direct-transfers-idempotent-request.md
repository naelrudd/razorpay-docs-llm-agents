> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Direct Transfer (Idempotent Request)

> Retry or send the same transfer request multiple times safely using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Idempotency allows you to safely retry or send the same request multiple times without fear of repeating the transfer request more than once.

* When you try to create a transfer, in some cases due to network downtimes, you may not get a response from our servers. As a consequence, you will not be aware of the transfer id or its state. In such cases, you can safely retry the transaction using the same idempotency key without risk of double-payout or duplication.

* To make a transfer request idempotent, add the header `X-Transfer-Idempotency` to the request and pass an idempotency key against it. The idempotency key (4-36 characters) can contain alphabets, numbers, hyphens, underscores and space only. For example, `fbdabb70-9548-4cfe-8da1-c9bbf39e96b0`.

> [!WARNING]
>
> **Watch Out!**
>
> Currently, idempotency is supported only on the Direct Transfers API.

> [!NOTE]
>
> **Handy Tips**
>
> * When retrying a request, the request body must be the same as the first request for idempotency to work. A different payload will be rejected as a `BAD_REQUEST`.
> * The idempotency key in retries must be the same as the original request.
> * Use unique idempotency keys for each unique request.
> * If we receive another request while the first one is in process, we will send a 409 error code. You can retry if you get this error code.

```bash Curl theme={null}
curl -X POST https://api.razorpay.com/v1/transfers \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-H 'content-type: application/json' \
-H 'X-Transfer-Idempotency: fbdabb70-9548-4cfe-8da1-c9bbf39e96b0' \
-d '{
  "account": "acc_CPRsN1LkFccllA",
  "amount": 100,
  "currency": "SGD"
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject transferRequest = new JSONObject();
headers.put("X-Transfer-Idempotency","fbdabb70-9548-4cfe-8da1-c9bbf39e96b0");
razorpay.addHeaders(headers);
transferRequest.put("amount",50000);
transferRequest.put("currency","SGD");
transferRequest.put("account","acc_CPRsN1LkFccllA");

Transfer transfer = razorpay.transfers.create(transferRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->setHeader("X-Transfer-Idempotency","fbdabb70-9548-4cfe-8da1-c9bbf39e96b0");

$api->transfer->create(array('account' => $accountId, 'amount' => 500, 'currency' => 'SGD'));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.transfers.create({
  "amount": 500,
  "currency": "SGD",
  "account": "acc_CPRsN1LkFccllA"
})
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.transfer.create({
   "amount":500,
   "currency":"SGD",
   "account": "acc_CPRsN1LkFccllA"
})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay.headers = {"X-Transfer-Idempotency" => "fbdabb70-9548-4cfe-8da1-c9bbf39e96b0"}

para_attr = {
  "account": accountId,
  "amount": 500,
  "currency": "SGD"
}

Razorpay::Transfer.create(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

extraHeaders:= map[string]string{
    "X-Transfer-Idempotency": "fbdabb70-9548-4cfe-8da1-c9bbf39e96b0",
    }

data:= map[string]interface{}{
  "account": "<accountId>",
  "amount": 100,
  "currency": "SGD",
}
body, err := client.Transfer.Create(data, nil)
```

```bash CLI theme={null}
razorpay route transfers create \
  --account acc_IEIkSOM5VJb2Lm \
  --amount 10000 \
  --currency SGD \
  --idempotency-key order-abc-001
```

```bash Curl theme={null}
curl -X POST https://api.razorpay.com/v1/transfers \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-H 'content-type: application/json' \
-H 'X-Transfer-Idempotency: fbdabb70-9548-4cfe-8da1-c9bbf39e96b0' \
-d '{
  "account": "acc_CPRsN1LkFccllA",
  "amount": 100,
  "currency": "MYR"
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject transferRequest = new JSONObject();
headers.put("X-Transfer-Idempotency","fbdabb70-9548-4cfe-8da1-c9bbf39e96b0");
razorpay.addHeaders(headers);
transferRequest.put("amount",500);
transferRequest.put("currency","MYR");
transferRequest.put("account","acc_CPRsN1LkFccllA");

Transfer transfer = razorpay.transfers.create(transferRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->setHeader("X-Transfer-Idempotency","fbdabb70-9548-4cfe-8da1-c9bbf39e96b0");

$api->transfer->create(array('account' => $accountId, 'amount' => 500, 'currency' => 'MYR'));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.transfers.create({
  "amount": 500,
  "currency": "MYR",
  "account": "acc_CPRsN1LkFccllA"
})
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.transfer.create({
   "amount":500,
   "currency":"MYR",
   "account": "acc_CPRsN1LkFccllA"
})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay.headers = {"X-Transfer-Idempotency" => "fbdabb70-9548-4cfe-8da1-c9bbf39e96b0"}

para_attr = {
  "account": accountId,
  "amount": 500,
  "currency": "MYR"
}

Razorpay::Transfer.create(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

extraHeaders:= map[string]string{
    "X-Transfer-Idempotency": "fbdabb70-9548-4cfe-8da1-c9bbf39e96b0",
    }

data:= map[string]interface{}{
  "account": "<accountId>",
  "amount": 100,
  "currency": "MYR",
}
body, err := client.Transfer.Create(data, nil)
```

```bash CLI theme={null}
razorpay route transfers create \
  --account acc_IEIkSOM5VJb2Lm \
  --amount 10000 \
  --currency MYR \
  --idempotency-key order-abc-001
```

```json Success theme={null}
{
  "id": "trf_JqpKevElHShZkw",
  "entity": "transfer",
  "status": "processed",
  "source": "acc_CJoeHMNpi0nC7k",
  "recipient": "acc_CPRsN1LkFccllA",
  "amount": 100,
  "currency": "SGD",
  "amount_reversed": 0,
  "fees": 1,
  "tax": 0,
  "notes": [],
  "linked_account_notes": [],
  "on_hold": false,
  "on_hold_until": null,
  "recipient_settlement_id": null,
  "created_at": 1657273505,
  "processed_at": 1657273505,
  "error": {
    "code": null,
    "description": null,
    "reason": null,
    "field": null,
    "step": null,
    "id": "trf_JqpKevElHShZkw",
    "source": null,
    "metadata": null
  }
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
  "id": "trf_JqpKevElHShZkw",
  "entity": "transfer",
  "status": "processed",
  "source": "acc_CJoeHMNpi0nC7k",
  "recipient": "acc_CPRsN1LkFccllA",
  "amount": 100,
  "currency": "MYR",
  "amount_reversed": 0,
  "fees": 1,
  "tax": 0,
  "notes": [],
  "linked_account_notes": [],
  "on_hold": false,
  "on_hold_until": null,
  "recipient_settlement_id": null,
  "created_at": 1657273505,
  "processed_at": 1657273505,
  "error": {
    "code": null,
    "description": null,
    "reason": null,
    "field": null,
    "step": null,
    "id": "trf_JqpKevElHShZkw",
    "source": null,
    "metadata": null
  }
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

## Request Parameters

**account** `string` *required*

Unique identifier of the Linked Account to which the transfer must be made.

**amount** `integer` *required*

The amount (in cents) to be transferred to the Linked Account. For example, for an amount of S\$200.35, the value of this field should be 20035.

**currency** `string` *required*

The currency used in the transaction. We support only `INR` for Route transactions.

**notes** `json object`

Set of key-value pairs that can be associated with an entity.  These pairs can be useful for storing additional information about the entity. A maximum of 15 key-value pairs, each of 256 characters (maximum), are supported.

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

The amount to be transferred to the Linked Account, in cents. For example, for an amount of S\$200.35, the value of this field should be 20035.

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

> [accordion] The API key/secret provided is invalid.
>
> **Code:** `4xx`
>
> This error occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
>
> **Solution:** Make sure the API Keys are active and entered correctly. Also, there should not be any whitespaces before or after the keys.
