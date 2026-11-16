> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Update an Item

> Update an Item details using this endpoint.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇺🇸 United States

Use this endpoint to update the details of an item. You can also edit the details of a created item from the Dashboard by clicking on that specific item from the list of items.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
  -H "Content-Type: application/json" \
  -X PATCH https://api.razorpay.com/v1/items/item_7Oy8OMV6BdEAac \
  -d '{
        "name":"Book / Ignited Minds - Updated name!",
        "description":"New descirption too."
      }'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String itemId = "item_7Oy8OMV6BdEAac";

JSONObject itemRequest = new JSONObject();
itemRequest.put("name","Book / Ignited Minds - Updated name!");
itemRequest.put("description","An indian story, Booker prize winner.");
itemRequest.put("amount", 20000);
itemRequest.put("currency","USD");
itemRequest.put("active",true);

Item item = razorpay.items.edit(itemId, itemRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.item.edit({
  "name": "Book / Ignited Minds - Updated name!",
  "description": "New descirption too.",
  "amount": 20000,
  "currency": "USD",
  "active": true
})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

itemId = "item_7Oy8OMV6BdEAac"

para_attr = {
  "name": "Book / Ignited Minds - Updated name!",
  "description": "New descirption too.",
  "amount": 20000,
  "currency": "USD",
  "active": true
}

Razorpay::Item.edit(itemId,para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
    "name": "Book / Ignited Minds - Updated name!",
    "description": "New descirption too.",
    "amount": 20000,
    "currency": "USD",
    "active": true,
}
body, err := client.Item.Update("<itemId>", data, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->Item->fetch($itemId)->edit(array("name" => "Book / Ignited Minds - Updated name!","description" => "New descirption too.","amount" => 20000,"currency" => "USD","active" => true
));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.Items.edit({
  "name": "Book / Ignited Minds - Updated name!",
  "description": "New descirption too.",
  "amount": 20000,
  "currency": "USD",
  "active": true
})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

itemId = "item_JDcbIdX9xojCje"

para_attr = {
  "name": "Book / Ignited Minds - Updated name!",
  "description": "New descirption too.",
  "amount": 20000,
  "currency": "USD",
  "active": true
}

Razorpay::Item.edit(itemId,para_attr)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string itemId = "item_7Oy8OMV6BdEAac";

Dictionary<string, object> itemRequest = new Dictionary<string, object>();
itemRequest.Add("name", "Book / Ignited Minds - Updated name!");
itemRequest.Add("description", "An indian story, Booker prize winner.");
itemRequest.Add("amount", 20000);
itemRequest.Add("currency", "USD");
itemRequest.Add("active", true);

Item payment = client.Item.Fetch(itemId).Edit(itemRequest);
```

```bash CLI theme={null}
razorpay invoices items update item_ABC123 \
  --name "Updated Item Name" \
  --amount 499 \
  --description "Updated description" \
  --active=false
```

```json Success theme={null}
{
  "id": "item_7Oy8OMV6BdEAac",
  "active": true,
  "name": "Book / Ignited Minds - Updated name!",
  "description": "New descirption too.",
  "amount": 20000,
  "unit_amount": 20000,
  "currency": "USD",
  "type": "invoice",
  "unit": null,
  "tax_inclusive": false,
  "hsn_code": null,
  "sac_code": null,
  "tax_rate": null,
  "tax_id": null,
  "tax_group_id": null,
  "created_at": 1649843796
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

The unique identifer of the item whose details are to be updated.

## Request Parameters

**name** `string`

The name of the item.

**description** `string`

A brief description about the item.

**amount** `integer`

The price of the item in the lowest unit of currency.

**currency** `string`

The currency in which the amount should be charged. Check the list of [supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).

**active** `boolean`

Indicates the status of the item. Possible values:

* `true` (default): Item is in the active state.
* `false`: Item is in the inactive state.

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
> The API key or secret are not entered or an invalid API key is used.
>
> **Solution:** Use and enter the correct API details while executing the API.

> [accordion] The id provided does not exist.
>
> **Code:** `400`
>
> The invoice id entered is either invalid or does not belong to the requester account.
>
> **Solution:** Enter a valid invoice id.

> [accordion] The amount field is required when item id is not present.
>
> **Code:** `400`
>
> Only name is entered without item id or amount.
>
> **Solution:** Provide either the item id or the amount with the name.

> [accordion] The name field is required when item id is not present.
>
> **Code:** `400`
>
> Possible reasons:
>
> * Only the amount field is entered without a name or item id.
> * The amount, name or item id are not entered.
>
> **Solution:** Provide the name field of the item when passing the amount.

> [accordion] The name may not be greater than 512 characters.
>
> **Code:** `400`
>
> The `name` value exceeds the 512-character limit.
>
> **Solution:** Keep `name` to 512 characters or fewer.

> [accordion] The amount must be an integer.
>
> **Code:** `400`
>
> A non-integer value (for example a decimal like `100.5` or a string like `"abc"`) was passed for `amount`.
>
> **Solution:** Pass `amount` as an integer in currency subunits.

> [accordion] Update operation not allowed for item of type: \{type}.
>
> **Code:** `400`
>
> The item id passed belongs to a non-invoice item type (for example, `payment_page`). Only items of type `invoice` can be updated through this endpoint.
>
> **Solution:** Confirm the item's type using the Fetch Item API. Only invoice-type items support updates via `PATCH /v1/items/:id`.
