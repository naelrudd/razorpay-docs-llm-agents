> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Update an Order

> Update an Order using Razorpay Orders API.

Available in
🇮🇳 India
🇺🇸 United States

Use this endpoint to update an Order.

* You can modify an existing order to update the `Notes` field **only**.
* Notes can be used to record additional information about the order.
* A key-value store, the `notes` field can have a maximum of 15 key-value pairs, each of 256 characters (maximum).

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]\
-X PATCH https://api.razorpay.com/v1/orders/order_DaaS6LOUAASb7Y \
-d '{
  "notes": {
    "key1": "value3",
    "key2": "value2"
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String orderId = "order_DaaS6LOUAASb7Y";

JSONObject orderRequest = new JSONObject();
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_1","Tea, Earl Grey, Hot");
orderRequest.put("notes",notes);

Order order = razorpay.orders.edit(orderId,orderRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.order.edit(orderId,{
  "notes": {
    "key1": "value3",
    "key2": "value2"
  }
})
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->order->fetch($orderId)->edit(array('notes'=> array('notes_key_1'=>'Beam me up Scotty. 1', 'notes_key_2'=>'Engage')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.orders.edit(orderId,{
  "notes": {
    "key1": "value3",
    "key2": "value2"
  }
})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

orderId = "order_DaaS6LOUAASb7Y"

para_attr = {
  "notes": {
    "key1": "value3",
    "key2": "value2"
  }
}

Razorpay::Order.edit(orderId,para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
  "notes": map[string]interface{}{
        "notes_key_1": "value1",
        "notes_key_2": "value2",
      }, 
}
body, err := client.Order.Update("<orderId>", data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string orderId = "order_Z6t7VFTb9xHeOs";

Dictionary<string, object> orderRequest = new Dictionary<string, object>();
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("notes_key_1", "Tea, Earl Grey, Hot");
notes.Add("notes_key_2", "Tea, Earl Grey, Hot Update");
orderRequest.Add("notes", notes);

Order order = client.Order.Fetch(orderId).Edit(orderRequest);
```

```bash CLI theme={null}
razorpay orders update ord_ABC123 \
  --note key1="Updated note" \
  --note key2="Another note"
```

```json Success theme={null}
{
  "id":"order_DaaS6LOUAASb7Y",
  "entity":"order",
  "amount":2200,
  "amount_paid":0,
  "amount_due":2200,
  "currency":"INR",
  "receipt":"Receipt #211",
  "offer_id":null,
  "status":"attempted",
  "attempts":1,
  "notes": {
    "key1": "value3",
    "key2": "value2"
  },
  "created_at":1572505143
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

Unique identifier of the order in which the `Notes` field must be updated.

## Request Parameters

**notes** `json object` *required*

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

## Response Parameters

**id** `string`

The unique identifier of the order.

**amount** `integer`

The amount for which the order was created, in currency subunits. For example, for an amount of , enter `29500`.

**entity** `string`

Name of the entity. Here, it is `order`.

**amount\_paid** `integer`

The amount paid against the order.

**amount\_due** `integer`

The amount pending against the order.

**currency** `string` *required*

ISO code for the currency in which you want to accept the payment. The default length is 3 characters.

**receipt** `string`

Receipt number that corresponds to this order. Can have a maximum length of 40 characters and has to be unique.

**status** `string`

The status of the order. Possible values:

* `created`: When you create an order it is in the `created` state. It stays in this state till a payment is attempted on it.
* `attempted`: An order moves from `created` to `attempted` state when a payment is first attempted on it. It remains in the `attempted` state till one payment associated with that order is captured.
* `paid`: After the successful capture of the payment, the order moves to the `paid` state. No further payment requests are permitted once the order moves to the `paid` state. The order stays in the `paid` state even if the payment associated with the order is refunded.

**attempts** `integer`

The number of payment attempts, successful and failed, that have been made against this order.

**notes** `json object`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

**created\_at** `integer`

Indicates the Unix timestamp when this order was created.

**checkout** `object`

Checkout configuration applied to this order, when the order was created with checkout-time options (theme, prefill, partial-payment settings).

**description** `string`

A brief description of the order, used for display purposes.

**offer\_id** `string`

Unique identifier of the offer associated with this order.

## Errors

> [accordion] The API `\<key/secret\>
> ` provided is invalid.
>
> **Code:** `400`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard. Possible reasons:
>
> * Different keys for test mode and live modes.
> * Expired API key.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after the keys.

> [accordion] id is not a valid id.
>
> **Code:** `400`
>
> The `order_id` passed is invalid.
>
> **Solution:** Use a valid `order_id`.

> [accordion] The id provided does not exist
>
> **Code:** `400`
>
> The `order_id` does not exist or does not belong to the requestor.
>
> **Solution:** Ensure that you use a valid `order_id` that belongs to the requestor.

> [accordion] amount is/are not required and should not be sent.
>
> **Code:** `400`
>
> `PATCH /v1/orders/:id` only allows updating the `notes` field. Sending `amount`, `currency`, `receipt` or any other immutable field is rejected.
>
> **Solution:** Include only the `notes` field in the PATCH request body. To change other order properties, create a new order.

> [accordion] Number of fields in notes should be less than or equal to 15.
>
> **Code:** `400`
>
> The `notes` object contains more than 15 key-value pairs.
>
> **Solution:** Limit `notes` to at most 15 key-value pairs.

> [accordion] Notes key cannot be greater than 255 characters.
>
> **Code:** `400`
>
> One of the keys inside the `notes` object exceeds the 255-character limit.
>
> **Solution:** Keep each `notes` key under 256 characters.

> [accordion] Notes value cannot be greater than 512 characters.
>
> **Code:** `400`
>
> One of the values inside the `notes` object exceeds the 512-character limit per value.
>
> **Solution:** Keep each `notes` value under 512 characters.

> [accordion] Notes values themselves should not be an array.
>
> **Code:** `400`
>
> A value inside `notes` was passed as a JSON array. Only scalar values (string, number, boolean) are accepted as values.
>
> **Solution:** Convert array values into strings (for example, a comma-separated list) before sending.
