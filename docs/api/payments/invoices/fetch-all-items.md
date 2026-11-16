> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch All Items

> Retrieve all the Items created till date.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇺🇸 United States

Use this endpoint to retrieve the details of all the items created till date.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
  - X GET https://api.razorpay.com/v1/items/ \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject params = new JSONObject();
params.put("count","1");

List<Item> item = razorpay.items.fetchAll(params);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.item.all(options)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

options = {"count":1}

Razorpay::Item.all(options)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

options:= map[string]interface{}{
    "count": 2,
    "skip": 1,
}
body, err := client.Item.All(options, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->Item->all($options);
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.items.all(options)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

options = {"count":2}

Razorpay::Item.all(options)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> itemRequest = new Dictionary<string, object>();
itemRequest.Add("count","1");

List<Item> item = client.Item.All();
```

```bash CLI theme={null}
razorpay invoices items list --count 10 --skip 0 --active 1
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "item_JInaSLODeDUQiQ",
      "active": true,
      "name": "Book / English August",
      "description": "An indian story, Booker prize winner.",
      "amount": 20000,
      "unit_amount": 20000,
      "currency": "INR",
      "type": "invoice",
      "unit": null,
      "tax_inclusive": false,
      "hsn_code": null,
      "sac_code": null,
      "tax_rate": null,
      "tax_id": null,
      "tax_group_id": null,
      "created_at": 1649843796
    },
    {
      "id": "item_JIPSg5L06yhHie",
      "active": false,
      "name": "Book / Ignited Minds - Updated name!",
      "description": "New descirption too. :).",
      "amount": 20000,
      "unit_amount": 20000,
      "currency": "INR",
      "type": "invoice",
      "unit": null,
      "tax_inclusive": false,
      "hsn_code": null,
      "sac_code": null,
      "tax_rate": null,
      "tax_id": null,
      "tax_group_id": null,
      "created_at": 1649758835
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

## Query Parameters

**from** `integer`

Unix timestamp, in seconds, from when the items are to be fetched.

**to** `integer`

Unix timestamp, in seconds, till when the items are to be fetched.

**count** `integer`

Number of items to be fetched.

* Default value: `10`
* Maximum value: `100`
* This can be used for pagination, in combination with the `skip` parameter.

**skip** `integer`

Number of records to be skipped while fetching the items.

**active** `integer`

Fetches number of active or inactive items.

* The value is `1` for active items.
* The value is `0` for inactive items.

## Response Parameters

**id** `string`

The unique identifier of the item.

**active** `boolean`

Indicates the status of the item. Possible values:

* `true` (default): Item is in the active state.
* `false`: Item is in the inactive state.

**name** `string`

The name of the item.

**description** `string`

A text description about the item.

**amount** `integer`

The price of the item.

**unit\_amount** `integer`

The per unit billing amount for each individual unit.

**currency** `string`

The currency in which the amount should be charged. Check the list of [supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).

**type** `string`

Here, it must be `invoice`.

**unit** `integer`

The number of units of the item billed in the invoice.

**tax\_inclusive** `boolean`

Indicates whether the base amount includes tax.

* `true`: The base amount includes tax.
* `false`: The base amount does not include tax. By default, the value is set to `false`.

**hsn\_code** `integer`

The 8-digit code used to classify the product as per the Harmonised System of Nomenclature.

**sac\_code** `integer`

The 6-digit code used to classify the service as per the Services Accounting Code.

**tax\_rate** `string`

The percentage at which an individual or a corporation is taxed.

**tax\_id** `string`

The identification number that gets displayed on invoices issued to the customer.

**tax\_group\_id** `string`

The identification number for the tax group. A tax group is a collection of taxes that can be applied as a single set of rules.

**created\_at** `integer`

Unix timestamp, at which the item was created. For example, `1649843796`.

## Errors

> [accordion] The API `\<key/secret\>
> ` provided is invalid.
>
> **Code:** `4xx`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard.
>
> * Different keys for test mode and live modes.
> * Expired API key.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after the keys.

> [accordion] count must be an integer between 1 and 100.
>
> **Code:** `400`
>
> An invalid value was passed for the `count` query parameter. The API returns `The count must be at least 1.` (for `count=0` or negative), `The count may not be greater than 100.` (for values above 100), or `The count must be an integer.` (for non-integer values).
>
> **Solution:** Pass `count` as a positive integer between 1 and 100.

> [accordion] skip must be a non-negative integer.
>
> **Code:** `400`
>
> A negative or non-integer value was passed for the `skip` query parameter.
>
> **Solution:** Pass `skip` as a non-negative integer (0 or higher).

> [accordion] from and to must be UNIX-epoch integers.
>
> **Code:** `400`
>
> A non-integer value (for example a human-readable date like `2024-01-01`) was passed for `from` or `to`.
>
> **Solution:** Pass `from` and `to` as UNIX-epoch integers in seconds.

> [accordion] The active field must be true or false.
>
> **Code:** `400`
>
> A non-boolean value was passed for the `active` query parameter. The accepted values are `1` (active items) or `0` (inactive items).
>
> **Solution:** Pass `active` as `1` or `0`.

> [accordion] \{any extra field} is/are not required and should not be sent.
>
> **Code:** `400`
>
> A query parameter that is not part of the Items list schema was passed (for example `name`, which is not a documented filter). The API echoes the rejected field name.
>
> **Solution:** Only pass documented query parameters: `from`, `to`, `count`, `skip`, `active`.
