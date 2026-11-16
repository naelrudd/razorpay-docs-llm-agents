> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Delete an Item

> Delete an Item using this endpoint.

Available in
🇮🇳 India
🇺🇸 United States

Use this endpoint to delete an item.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
  -X DELETE https://api.razorpay.com/v1/items/item_7Oy8OMV6BdEAac \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String itemId = "item_7Oy8OMV6BdEAac";

List<Item> item  = razorpay.items.delete(itemId)
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.item.delete(itemId)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

itemId = "item_7Oy8OMV6BdEAac"

Razorpay::Item.delete(itemId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Item.Delete("", nil, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->Item->fetch($itemId)->delete();
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.Items.delete(itemId)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

itemId = "item_7Oy8OMV6BdEAac"

Razorpay::Item.delete(itemId)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string itemId = "item_7Oy8OMV6BdEAac";

List<Item> payment = client.Item.Fetch(itemId).Delete();
```

```bash CLI theme={null}
razorpay invoices items delete item_ABC123
```

```json Success theme={null}
[]
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

The unique identifier of the item that must be deleted.

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

> [accordion] Delete operation not allowed for item of type: \{type}.
>
> **Code:** `400`
>
> The item id passed belongs to a non-invoice item type (for example, `payment_page`). Only items of type `invoice` can be deleted through this endpoint.
>
> **Solution:** Confirm the item's type using the Fetch Item API. Only invoice-type items support deletion via `DELETE /v1/items/:id`.

> [accordion] Cannot delete an item with which invoices have been created already.
>
> **Code:** `400`
>
> The item has already been associated with one or more invoices. Razorpay does not allow deleting items that have a history of use, to preserve invoice integrity.
>
> **Solution:** Mark the item as inactive instead by calling `PATCH /v1/items/:id` with `active: false`. Inactive items remain available on past invoices but cannot be used on new ones.
