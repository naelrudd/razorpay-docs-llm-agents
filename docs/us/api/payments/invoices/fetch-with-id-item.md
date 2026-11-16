> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Item With ID

> Fetch an Item with your Item Id.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇺🇸 United States

Use this endpoint to retrieve the details of a specific item using the `Item_id`.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
  - X GET https://api.razorpay.com/v1/items/item_7Oxp4hmm6T4SCn \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String itemId = "item_7Oxp4hmm6T4SCn";

Item item = razorpay.items.fetch(itemId)
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.item.fetch(itemId)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

itemId = "item_7Oxp4hmm6T4SCn"

Razorpay::Item.fetch(itemId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Item.Fetch("<itemId>", nil, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->Item->fetch($itemId);
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.items.fetch(itemId)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

itemId = "item_7Oxp4hmm6T4SCn"

Razorpay::Item.fetch(itemId)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string itemId = "item_7Oxp4hmm6T4SCn";

Item item = client.Item.Fetch(itemId);
```

```bash CLI theme={null}
razorpay invoices items fetch item_ABC123
```

```json Success theme={null}
{
  "id": "item_7Oxp4hmm6T4SCn",
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

The unique identifier of the item whose details are to be fetched.

## Response Parameters

**id** `string`

The unique identifier of the item.

**active** `boolean`

Indicates the status of the item. Possible values:

* true (default): Item is in active state.
* false: Item is in inactive state.

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

> [accordion] no Route matched with those values
>
> **Code:** `400`
>
> This happens when the lenght of the id is incorrect.
>
> **Solution:** Enter a valid invoice id.
