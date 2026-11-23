> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create an Item

> Create an Item with basic details such as name and amount.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create an item with basic details such as name and amount. After an item is created, it appears on the list of created items and in the drop-down menu at the time of invoice creation.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
  -H "Content-Type: application/json" \
  -X POST https://api.razorpay.com/v1/items \
  -d '{
        "name":"Book / English August",
        "description":"An indian story, Booker prize winner.",
        "amount": 20000,
        "currency": "MYR"
      }'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject itemRequest = new JSONObject();
itemRequest.put("name","Book / English August");
itemRequest.put("description","An indian story, Booker prize winner.");
itemRequest.put("amount", 20000);
itemRequest.put("currency","MYR");

Item item = razorpay.items.create(itemRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.item.create({
  "name": "Book / English August",
  "description": "An indian story, Booker prize winner.",
  "amount": 20000,
  "currency": "MYR"
})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay::Item.create({
  "name": "Book / English August",
  "description": "An indian story, Booker prize winner.",
  "amount": 20000,
  "currency": "MYR"
});
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
    "name": "Book / English August",
    "description": "An indian story, Booker prize winner.",
    "amount": 20000,
    "currency": "MYR",
}
body, err := client.Item.Create(data, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->Item->create(array("name" => "Book / English August","description" => "An indian story, Booker prize winner.","amount" => 20000,"currency" => "MYR"));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.Items.create({
  "name": "Book / English August",
  "description": "An indian story, Booker prize winner.",
  "amount": 20000,
  "currency": "MYR"
})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay::Item.create({
  "name": "Book / English August",
  "description": "An indian story, Booker prize winner.",
  "amount": 20000,
  "currency": "MYR"
});
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> itemRequest = new Dictionary<string, object>();
itemRequest.Add("name", "Book / English August");
itemRequest.Add("description", "An indian story, Booker prize winner.");
itemRequest.Add("amount", 20000);
itemRequest.Add("currency", "MYR");

Item item = client.Item.Create(itemRequest);
```

```bash CLI theme={null}
razorpay invoices items create \
  --name "Master Cloud Computing in 30 Days" \
  --amount 399 \
  --currency INR \
  --description "Book by Ravena Ravenclaw"
```

```json Success theme={null}
{
  "id": "item_JInaSLODeDUQiQ",
  "active": true,
  "name": "Book / English August",
  "description": "An indian story, Booker prize winner.",
  "amount": 20000,
  "unit_amount": 20000,
  "currency": "MYR",
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

## Request Parameters

**name** `string` *required*

Name of the item.

**description** `string`

A brief description about the item.

**amount** `integer` *required*

The price of the item. In the case of three decimal currencies, such as KWD, BHD and OMR, to refund a payment of 295.991, pass the value as `295990`. And in the case of zero decimal currencies such as JPY, to refund a payment of 295, pass the value as `295`.

> [!WARNING]
>
> **Watch Out!**
>
> As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to refund a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.

**currency** `string` *required*

The currency in which the amount should be charged. Check the list of [supported currencies](https://razorpay.com/docs/my/payments/international-payments#malaysian-businesses).

> [!NOTE]
>
> **Handy Tips**
>
> Razorpay Curlec has added support for zero decimal currencies, such as JPY, and three decimal currencies, such as KWD, BHD, and OMR, allowing businesses to accept international payments in these currencies. Know more about Currency Conversion (May 2024).

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

The currency in which the amount should be charged. Check the list of [supported currencies](https://razorpay.com/docs/my/payments/international-payments#malaysian-businesses).

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

> [accordion] The currency field is required.
>
> **Code:** `400`
>
> The currency field is blank.
>
> **Solution:** Ensure that the currency field is added with a valid currency code.

> [accordion] The merchant doesn't have international activated
>
> **Code:** `400`
>
> This happens when an international currency code is added.
>
> **Solution:** Ensure that the currency field is added with a valid currency code.

> [accordion] The amount must be at least INR 1.00
>
> **Code:** `400`
>
> This happens when the amount added in the amount field is less than INR 1.
>
> **Solution:** Ensure that the amount is INR 1 or greater.

> [accordion] The name field is required.
>
> **Code:** `400`
>
> The `name` field was not included in the request body, or the body was empty.
>
> **Solution:** Always pass `name` in the request body.

> [accordion] The amount field is required when unit amount is not present.
>
> **Code:** `400`
>
> Neither the `amount` field nor `unit_amount` field was included in the request body.
>
> **Solution:** Pass either `amount` (in currency subunits) or `unit_amount`.

> [accordion] The name may not be greater than 512 characters.
>
> **Code:** `400`
>
> The `name` value exceeds the 512-character limit.
>
> **Solution:** Keep `name` to 512 characters or fewer.
