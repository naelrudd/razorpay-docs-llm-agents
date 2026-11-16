> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Customer With ID

> Fetch Customer With id using Razorpay Customers API.

Available in
🇮🇳 India
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve details of a customer with id.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET https://api.razorpay.com/v1/customers/cust_1Aa00000000001 \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String customerId = "cust_1Aa00000000001";

Customer customer = razorpay.customers.fetch(customerId);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.customer.fetch(customerId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

customerId := "cust_1Aa00000000001"

body, err := client.Customer.Fetch(customerId, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->customer->fetch($customerId)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.customers.fetch(customerId)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

customerId = "cust_1Aa00000000001"

Razorpay::Customer.fetch(customerId)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string customerId = "cust_1Aa00000000001";

Customer customer = client.Customer.Fetch("cust_M462yViJrhNrQc");
```

```bash CLI theme={null}
razorpay customers fetch cust_ABC123
```

```json Success theme={null}
{
  "id": "cust_1Aa00000000001",
  "entity": "customer",
  "name": "Alex Lim",
  "email": "alex.lim@example.com",
  "contact": "+6591119111",
  "gstin": null,
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  },
  "created_at": 1655298731
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "LQPd9lomgwDE5Fs is not a valid id",
    "source": "business",
    "step": "payment_initiation",
    "reason": "input_validation_failed",
    "metadata": {}
  }
}
```

## Path Parameters

**id** `string` *required*

The unique identifier linked to the customer.

## Response Parameters

**id** `string`

Unique identifier of the customer. For example, `cust_1Aa00000000004`.

**entity** `string`

Indicates the type of entity.

**name** `string`

Customer's name. Alphanumeric, with period (.), apostrophe ('), forward slash (/), at (@) and parentheses allowed. The name must be between 3-50 characters in length. For example, `Alex Lim`.

**contact** `string`

The customer's phone number. A maximum length of 15 characters including country code. For example, `+6591119111`.

**email** `string`

The customer's email address. A maximum length of 64 characters. For example, `alex.lim@example.com`.

**gstin** `string`

GST number linked to the customer. For example, `29XAbbA4369J1PA`.

**notes** `object`

This is a key-value pair that can be used to store additional information about the entity. It can hold a maximum of 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

**created\_at** `integer`

UNIX timestamp, when the customer was created. For example, `1234567890`.

**shipping\_address** `object`

The customer's shipping address. An address object with `line1`, `line2`, `city`, `state`, `country`, and `zipcode` fields. Empty when none is set.

## Errors

> [accordion] The API `\<key/secret\>
> ` provided is invalid.
>
> **Code:** `4xx`
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
> The `customer_id` passed is invalid.
>
> **Solution:** Use a valid `customer_id`.

> [accordion] The id provided does not exist.
>
> **Code:** `400`
>
> The `customer_id` does not exist or does not belong to the requestor.
>
> **Solution:** Ensure that you use a valid `customer_id` that belongs to the requestor.
