> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch All Customers

> Fetch all Customers using Razorpay Customers API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve the details of all the customers.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET https://api.razorpay.com/v1/customers?count=2&skip=1
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject params = new JSONObject();
params.put("count","1");

List<Customer> customer = razorpay.customers.fetchAll(params);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.customer.all(options)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

optional := map[string]interface{}{
	  "count":1,
	}

body, err := client.Customer.All(optional, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->customer->all($options)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

options = {"count": 2}

Razorpay::Customer.all(options)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.customers.all(options) 
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> paramRequest = new Dictionary<string, object>();
paramRequest.Add("count","1");

List<Customer> card = client.Customer.All(paramRequest);
```

```bash CLI theme={null}
razorpay customers list --count 10 --skip 0
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "cust_LQPdeJqQeKQrJM",
      "entity": "customer",
      "name": "Alex Lim",
      "email": "alex.lim@example.com",
      "contact": "+6591119111",
      "gstin": null,
      "notes": [],
      "created_at": 1678580352
    },
    {
      "id": "cust_LQPd9lomgwDE5F",
      "entity": "customer",
      "name": "Saurav Kumar",
      "email": "saurav.kumar@example.com",
      "contact": "+6591119111",
      "gstin": null,
      "notes": [],
      "created_at": 1678580324
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

**count** `integer`

The number of customer records to be retrieved from the system. The default value is 10. The maximum value is 100. This can be used for pagination in combination with `skip`.

**skip** `integer`

The number of customer records that must be skipped. The default value is 0. This can be used for pagination in combination with `count`.

## Response Parameters

**entity** `string`

Indicates the type of entity.

**id** `string`

Unique identifier of the customer. For example, `cust_1Aa00000000004`.

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

> [accordion] count must be an integer between 1 and 100.
>
> **Code:** `400`
>
> An invalid value was passed for the `count` query parameter. The API returns variants of this error depending on the input: `The count must be at least 1.` (for `count=0` or negative values), `The count may not be greater than 100.` (for values above 100), or `The parameter provided is not an integer` (for non-integer values).
>
> **Solution:** Pass `count` as a positive integer between 1 and 100.

> [accordion] The skip must be at least 0.
>
> **Code:** `400`
>
> A negative value was passed for the `skip` query parameter.
>
> **Solution:** Pass `skip` as a non-negative integer (0 or higher).

> [accordion] \{any extra field} is/are not required and should not be sent.
>
> **Code:** `400`
>
> The request contains a query parameter that is not part of the Fetch All Customers schema. Only `count`, `skip`, `from` and `to` are accepted.
>
> **Solution:** Remove any unknown query parameters from the request.
