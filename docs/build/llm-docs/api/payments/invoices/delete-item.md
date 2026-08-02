# Delete an Item

**DELETE** `/v1/items/:id`

Use this endpoint to delete an item.

### Request

```curl: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
  -X DELETE https://api.razorpay.com/v1/items/item_7Oy8OMV6BdEAac \

```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String itemId = "item_7Oy8OMV6BdEAac";

List item  = razorpay.items.delete(itemId)

```python: Python
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.item.delete(itemId)

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

itemId = "item_7Oy8OMV6BdEAac"

Razorpay::Item.delete(itemId)

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Item.Delete("", nil, nil)

```php: PHP
$api = new Api($key_id, $secret);

$api->Item->fetch($itemId)->delete();
```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.Items.delete(itemId)

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

itemId = "item_7Oy8OMV6BdEAac"

Razorpay::Item.delete(itemId)

```csharp: .NET
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string itemId = "item_7Oy8OMV6BdEAac";

List payment = client.Item.Fetch(itemId).Delete();

```bash: CLI
razorpay invoices items delete item_ABC123
```

### Response

```json: Success
[]

```json: Failure 
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

### Parameters

`id` _mandatory_
: `string` The unique identifier of the item that must be deleted.

### Errors

The API `` provided is invalid.
* code: 4xx
* description: The API key or secret are not entered or an invalid API key is used.
* solution: Use and enter the correct API details while executing the API.

The id provided does not exist.
* code: 400
* description: The invoice id entered is either invalid or does not belong to the requester account.
* solution: Enter a valid invoice id.

Delete operation not allowed for item of type: \{type\}.
* code: 400
* description: The item id passed belongs to a non-invoice item type (for example, `payment_page`). Only items of type `invoice` can be deleted through this endpoint.
* solution: Confirm the item's type using the Fetch Item API. Only invoice-type items support deletion via `DELETE /v1/items/:id`.

Cannot delete an item with which invoices have been created already.
* code: 400
* description: The item has already been associated with one or more invoices. Razorpay does not allow deleting items that have a history of use, to preserve invoice integrity.
* solution: Mark the item as inactive instead by calling `PATCH /v1/items/:id` with `active: false`. Inactive items remain available on past invoices but cannot be used on new ones.
