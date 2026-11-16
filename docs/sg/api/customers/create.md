> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Customer

> Create a Customer using Razorpay Customers API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create or add a customer with basic details such as name and contact details.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/customers \
-H "Content-Type: application/json" \
-d '{
    "name": "Alex Lim",
    "contact": "+6591119111",
    "email": "alex.lim@example.com",
    "fail_existing": "0",
    "notes": {
      "notes_key_1": "Tea, Earl Grey, Hot",
      "notes_key_2": "Tea, Earl Grey… decaf."
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject customerRequest = new JSONObject();
customerRequest.put("name","Alex Lim");
customerRequest.put("contact","+6591119111");
customerRequest.put("email","alex.lim@example.com");
customerRequest.put("fail_existing","0");
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
customerRequest.put("notes",notes);

Customer customer = razorpay.customers.create(customerRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.customer.create({
  "name": "Alex Lim",
  "contact": +6591119111,
  "email": "alex.lim@example.com",
  "fail_existing": "0",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
    "name": "Alex Lim",
    "contact": +6591119111,
    "email": "alex.lim@example.com",
    "fail_existing": "0",
    "notes": map[string]interface{}{
      "notes_key_1": "Tea, Earl Grey, Hot",
      "notes_key_2": "Tea, Earl Grey… decaf.",
	},
}

body, err := client.Customer.Create(data, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->customer->create(array('name' => 'Alex Lim', 'email' => 'alex.lim@example.com','contact'=>'+6591119111','notes'=> array('notes_key_1'=> 'Tea, Earl Grey, Hot','notes_key_2'=> 'Tea, Earl Grey… decaf'));
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> options = new Dictionary<string,object>();

options.Add("name", "Alex Lim"); 
options.Add("contact", "+6591119111"); 
options.Add("email", "alex.lim@example.com"); 
options.Add("fail_existing", "0"); 

Customer customer = Customer.Create(options);
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay::Customer.create({
  "name": "Alex Lim",
  "contact": +6591119111,
  "email": "alex.lim@example.com",
  "fail_existing": "0",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
})
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.customers.create({
  name: "Alex Lim",
  contact: +6591119111,
  email: "alex.lim@example.com",
  fail_existing: "0",
  notes: {
    notes_key_1: "Tea, Earl Grey, Hot",
    notes_key_2: "Tea, Earl Grey… decaf."
  }
})
```

```bash CLI theme={null}
razorpay customers create --name "Alex Lim" --contact "+91+6591119111" --email "alex.lim@example.com" --gstin "29XAbbA4369J1PA" --note key1="Test customer"
```

```json Success theme={null}
{
  "id" : "cust_1Aa00000000004",
  "entity": "customer",
  "name" : "<name>",
  "email" : "<email>",
  "contact" : "<phone>",
  "gstin": null,
  "notes": {
    "notes_key_1":"Tea, Earl Grey, Hot",
    "notes_key_2":"Tea, Earl Grey… decaf."
  },
  "created_at ": 1234567890
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "Contact number should be at least 8 digits, including country code",
    "source": "business",
    "step": "NA",
    "reason": "invalid_contact_number",
    "metadata": {},
    "field": "contact"
  }
}
```

## Request Parameters

**name** `string`

Customer's name. Alphanumeric value with period (.), apostrophe ('), forward slash (/), at (@) and parentheses are allowed. The name must be between 3-50 characters in length. For example, `Alex Lim`.

**contact** `string`

The customer's phone number. A maximum length of 15 characters including country code. For example, `+6591119111`.

**email** `string`

The customer's email address. A maximum length of 64 characters. For example, `alex.lim@example.com`.

**fail\_existing** `string`

Possible values:

* `1` (default): If a customer with the same details already exists, throws an error.
* `0`: If a customer with the same details already exists, fetches details of the existing customer.

**gstin** `string`

Customer's GST number, if available. For example, `29XAbbA4369J1PA`.

**notes** `object`

This is a key-value pair that can be used to store additional information about the entity. It can hold a maximum of 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

## Response Parameters

**id** `string`

Unique identifier of the customer. For example, `cust_1Aa00000000004`.

**entity** `string`

Indicates the type of entity.

**name** `string`

Customer's name. Alphanumeric, with period (.), apostrophe ('), forward slash (/), at (@) and parentheses allowed. The name must be between 3-50 characters in length.

**contact** `string`

The customer's phone number. A maximum length of 15 characters including country code.

**email** `string`

The customer's email address. A maximum length of 64 characters.

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

> [accordion] Contact number should be at least 8 digits, including country code.
>
> **Code:** `400`
>
> The contact number is less than 8 digits.
>
> **Solution:** Enter contact number that meets the validation criteria. It should have at least 8 digits, including the country code. For example, "+6591119111".

> [accordion] The email must be a valid email address.
>
> **Code:** `400`
>
> The value passed for `email` is not in a valid email format.
>
> **Solution:** Pass a valid email address (for example, `user@example.com`).

> [accordion] Contact number contains invalid characters, only digits and + symbol are allowed.
>
> **Code:** `400`
>
> The `contact` value contains characters other than digits and the `+` symbol (for example, letters, hyphens or spaces).
>
> **Solution:** Pass `contact` using only digits and an optional leading `+` for the country code.

> [accordion] The name may not be greater than 50 characters.
>
> **Code:** `400`
>
> The `name` value exceeds the 50-character limit.
>
> **Solution:** Keep the `name` to 50 characters or fewer.

> [accordion] Customer already exists for the merchant.
>
> **Code:** `400`
>
> A customer with the same `contact` or `email` already exists for this merchant and `fail_existing` was set to `1` (or omitted, which defaults to fail).
>
> **Solution:** Either use a different `contact` / `email`, or pass `fail_existing: "0"` in the request body to receive the existing customer in the response instead of an error.

> [accordion] Notes should not have more than 15 keys.
>
> **Code:** `400`
>
> The `notes` object contains more than 15 key-value pairs.
>
> **Solution:** Reduce the number of keys in the `notes` object to 15 or fewer.

> [accordion] The name format is invalid.
>
> **Code:** `400`
>
> The `name` value contains characters outside the allowed set. Allowed characters are letters, numbers and a limited set of punctuation (`'`, `-`, `.`, `_`, `(`, `)`, `@`, `/` and spaces). The name must start and end with a letter, number, `.` or `)`.
>
> **Solution:** Pass `name` using only the allowed characters and ensure it starts and ends with a letter, number, `.` or `)`.

> [accordion] The gstin field is invalid.
>
> **Code:** `400`
>
> The `gstin` value is not a valid Indian GSTIN. A GSTIN is a 15-character alphanumeric code in the format `<state-code><PAN><entity-code><check-digit>`.
>
> **Solution:** Pass a valid 15-character GSTIN.

> [accordion] Notes value cannot be greater than 512 characters.
>
> **Code:** `400`
>
> One of the values inside the `notes` object exceeds the 512-character limit per value.
>
> **Solution:** Keep each `notes` value under 512 characters.
