> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Edit Customer Details

> Edit Customer Details using Razorpay Curlec Customers API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to edit the customer details such as name, email and contact details. When editing a customer's details, ensure that the combination of the values in the `email` and `contact` attributes is unique for every customer.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X PUT https://api.razorpay.com/v1/customers/cust_1Aa00000000003 \
-H "Content-Type: application/json" \
-d '{
  "name": "<name>",
  "email": "<email>",
  "contact": "<phone>"
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String customerId = "cust_1Aa00000000003";

JSONObject customerRequest = new JSONObject();
customerRequest.put("name","<name>");
customerRequest.put("contact","<phone>");
customerRequest.put("email","<email>");

Customer customer = razorpay.customers.edit(customerId,customerRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.customer.edit(customerId,{
  "name": "<name>",
  "email": "<email>",
  "contact": <phone>
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

customerId := "cust_1Aa00000000003"

data = map[string]interface{}{
  "name": "<name>",
  "email": "<email>",
  "contact": <phone>,
}
body, err := client.Customer.Edit(customerId, data, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->customer->fetch($customerId)->edit(array('name' => '<name>', 'email' => '<email>', 'contact': '<phone>', 'notes'=> array('notes_key_1'=> 'Tea, Earl Grey, Hot','notes_key_2'=> 'Tea, Earl Grey… decaf')));
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

customerId = "cust_1Aa00000000003"

Razorpay::Customer.edit(customerId,{
  "name": "<name>",
  "email": "<email>",
  "contact": <phone>,
})
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.customers.edit(customerId,{
  name: "<name>",
  email: "<email>",
  contact: <phone>
})
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string customerId = "cust_1Aa00000000003";

Dictionary<string, object> customerRequest = new Dictionary<string, object>();
customerRequest.Add("name", "<name>");
customerRequest.Add("contact", "<phone>");
customerRequest.Add("email", "<email>");

Customer card = client.Customer.Fetch(customerId).Edit(customerRequest);
```

```bash CLI theme={null}
razorpay customers update cust_ABC123 --name "Gaurav Kumar" --contact "+919123456780" --email "gaurav.kumar@example.com"
```

## Path Parameters

**id** `string` *required*

The unique identifier linked to the customer.

## Request Parameters

**name** `string`

Customer's name. Alphanumeric, with period (.), apostrophe ('), forward slash (/), at (@) and parentheses allowed. The name must be between 3-50 characters in length. For example, `Gaurav Kumar`.

**contact** `string`

The customer's phone number. A maximum length of 15 characters. For example, `+919876543210`.

**email** `string`

The customer's email address. A maximum length of 64 characters. For example, `gaurav.kumar@example.com`.

## Response Parameters

**id** `string`

Unique identifier of the customer. For example, `cust_1Aa00000000004`.

**entity** `string`

Indicates the type of entity.

**name** `string`

Customer's name. Alphanumeric, with period (.), apostrophe (') and parentheses allowed. The name must be between 3-50 characters in length.

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
> **Solution:** Enter a contact number that meets the validation criteria. It should have at least 8 digits, including the country code.

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
> The `customer_id` passed in the URL is well-formed but does not exist or does not belong to the requesting merchant.
>
> **Solution:** Use a valid `customer_id` returned from `POST /v1/customers`. Confirm by fetching the customer before retrying.

> [accordion] Customer already exists for the merchant.
>
> **Code:** `400`
>
> The `contact` or `email` passed in the edit request matches an existing customer of this merchant other than the one being edited.
>
> **Solution:** Use a different `contact` / `email`, or edit the matching customer record directly.

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
