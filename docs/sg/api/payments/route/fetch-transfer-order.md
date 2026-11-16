> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Transfer for an Order

> Fetch Transfer for an order using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve the collection of all transfers created on a specific order id.

```bash Curl theme={null}
curl -X GET https://api.razorpay.com/v1/orders/order_DSkl2lBNvueOly/?expand[]=transfers&status=processing \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \ 
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject request = new JSONObject();
request.put("expand[]","transfers");

Order response = razorpayclient.orders.get("orders/order_JJCYnu3hipocHz",request);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->order->fetch($orderId)->transfers(array('expand[]'=>'transfers'));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.orders.fetchTransferOrder(orderId)
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.order.fetch(orderId, {
  "expand[]": "transfers"
})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

orderId = "order_JJCYnu3hipocHz"

Razorpay::Order.fetch_transfer_order(orderId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
  "expand[]": "transfers",
}
body, err := client.Order.Fetch("<orderId>", data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]
");

string orderId = "order_JkaIDdkgGXVcwS";

Dictionary<string, object> transferRequest = new Dictionary<string, object>();
transferRequest.Add("expand[]", "transfers");

Order token = client.Order.Fetch(orderId, transferRequest);
```

```bash CLI theme={null}
razorpay route transfers fetch-by-order order_JMNiqyuoFoJcXb
```

```json Success theme={null}
{
  "id": "order_JJCYnu3hipocHz",
  "entity": "order",
  "amount": 2000,
  "amount_paid": 0,
  "amount_due": 2000,
  "currency": "SGD",
  "receipt": null,
  "offer_id": null,
  "status": "created",
  "attempts": 0,
  "notes": [],
  "created_at": 1649931742,
  "transfers": {
    "entity": "collection",
    "count": 2,
    "items": [
      {
        "id": "trf_JJCYnw77tqUT9r",
        "entity": "transfer",
        "status": "created",
        "source": "order_JJCYnu3hipocHz",
        "recipient": "acc_IRQWUleX4BqvYn",
        "amount": 1000,
        "currency": "SGD",
        "amount_reversed": 0,
        "fees": 0,
        "tax": null,
        "notes": {
          "branch": "Acme Corp Bangalore North",
          "name": "Alex Lim"
        },
        "linked_account_notes": [
          "branch"
        ],
        "on_hold": true,
        "on_hold_until": 1671222870,
        "settlement_status": null,
        "recipient_settlement_id": null,
        "created_at": 1649931742,
        "processed_at": null,
        "error": {
          "code": null,
          "description": null,
          "reason": null,
          "field": null,
          "step": null,
          "id": "trf_JJCYnw77tqUT9r",
          "source": null,
          "metadata": null
        }
      },
      {
        "id": "trf_JJCYnxe5GV19Kk",
        "entity": "transfer",
        "status": "created",
        "source": "order_JJCYnu3hipocHz",
        "recipient": "acc_IROu8Nod6PXPtZ",
        "amount": 1000,
        "currency": "SGD",
        "amount_reversed": 0,
        "fees": 0,
        "tax": null,
        "notes": {
          "branch": "Acme Corp Bangalore South",
          "name": "Saurav Kumar"
        },
        "linked_account_notes": [
          "branch"
        ],
        "on_hold": false,
        "on_hold_until": null,
        "settlement_status": null,
        "recipient_settlement_id": null,
        "created_at": 1649931742,
        "processed_at": null,
        "error": {
          "code": null,
          "description": null,
          "reason": null,
          "field": null,
          "step": null,
          "id": "trf_JJCYnxe5GV19Kk",
          "source": null,
          "metadata": null
        }
      }
    ]
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
  "id": "order_JJCYnu3hipocHz",
  "entity": "order",
  "amount": 2000,
  "amount_paid": 0,
  "amount_due": 2000,
  "currency": "MYR",
  "receipt": null,
  "offer_id": null,
  "status": "created",
  "attempts": 0,
  "notes": [],
  "created_at": 1649931742,
  "transfers": {
    "entity": "collection",
    "count": 2,
    "items": [
      {
        "id": "trf_JJCYnw77tqUT9r",
        "entity": "transfer",
        "status": "created",
        "source": "order_JJCYnu3hipocHz",
        "recipient": "acc_IRQWUleX4BqvYn",
        "amount": 1000,
        "currency": "MYR",
        "amount_reversed": 0,
        "fees": 0,
        "tax": null,
        "notes": {
          "branch": "Acme Corp Johor Bahru",
          "name": "Nur Aisyah"
        },
        "linked_account_notes": [
          "branch"
        ],
        "on_hold": true,
        "on_hold_until": 1671222870,
        "settlement_status": null,
        "recipient_settlement_id": null,
        "created_at": 1649931742,
        "processed_at": null,
        "error": {
          "code": null,
          "description": null,
          "reason": null,
          "field": null,
          "step": null,
          "id": "trf_JJCYnw77tqUT9r",
          "source": null,
          "metadata": null
        }
      },
      {
        "id": "trf_JJCYnxe5GV19Kk",
        "entity": "transfer",
        "status": "created",
        "source": "order_JJCYnu3hipocHz",
        "recipient": "acc_IROu8Nod6PXPtZ",
        "amount": 1000,
        "currency": "MYR",
        "amount_reversed": 0,
        "fees": 0,
        "tax": null,
        "notes": {
          "branch": "Acme Corp Kedah",
          "name": "Siti Aisyah"
        },
        "linked_account_notes": [
          "branch"
        ],
        "on_hold": false,
        "on_hold_until": null,
        "settlement_status": null,
        "recipient_settlement_id": null,
        "created_at": 1649931742,
        "processed_at": null,
        "error": {
          "code": null,
          "description": null,
          "reason": null,
          "field": null,
          "step": null,
          "id": "trf_JJCYnxe5GV19Kk",
          "source": null,
          "metadata": null
        }
      }
    ]
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

## Path Parameters

**id** `string` *required*

Unique identifier of the Order for which transfers must be retrieved.

## Query Parameters

**expand** `array` *required*

Used to retrieve details regarding the transfers initiated via an order. Supported value is `transfers`.

**status** `string`

Status of the transfer.

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

**checkout** `object`

Checkout configuration applied to this order, when the order was created with checkout-time options (theme, prefill, partial-payment settings).

**transfers** `object`

Collection of transfers associated with this order when Route is enabled. Contains entity type, count, and items array.

**receipt** `string`

Receipt number that corresponds to this order, set by the merchant. Up to 40 characters. For example, `audit_1778024126`.

**amount\_paid** `integer`

The amount paid for this order, in the smallest currency unit (cents for SGD). For example, `0`.

**amount\_due** `integer`

The amount due for this order, in the smallest currency unit (cents for SGD). For example, `50000`.

**attempts** `integer`

Number of payment attempts made for this order. For example, `0`.

## Errors

> [accordion] The api key/secret provided is invalid
>
> **Code:** `4xx`
>
> This error occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
>
> **Solution:** Make sure the API Keys are active and entered correctly. Also, there should not be any whitespaces before or after the keys.

> [accordion] order\_id is not a valid id
>
> **Code:** `400`
>
> This error occurs when you pass an invalid `order_id` in the API endpoint.
>
> **Solution:** Make sure to pass a vaild `order_id`.
