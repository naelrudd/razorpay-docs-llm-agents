# Edit Customer Details

**PUT** `/v1/customers/:id`

Use this endpoint to edit the customer details such as name, email and contact details. When editing a customer's details, ensure that the combination of the values in the `email` and `contact` attributes is unique for every customer.

### Request

```cURL: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X PUT https://api.razorpay.com/v1/customers/cust_1Aa00000000003 \
-H "Content-Type: application/json" \
-d '{
  "name": "Gaurav Kumar",
  "email": "gaurav.kumar@example.com",
  "contact": "+919876543210"
}'

```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String customerId = "cust_1Aa00000000003";

JSONObject customerRequest = new JSONObject();
customerRequest.put("name","Gaurav Kumar");
customerRequest.put("contact","+919876543210");
customerRequest.put("email","gaurav.kumar@example.com");

Customer customer = razorpay.customers.edit(customerId,customerRequest);

```Python: Python
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.customer.edit(customerId,{
  "name": "Gaurav Kumar",
  "email": "gaurav.kumar@example.com",
  "contact": +919876543210
})

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

customerId := "cust_1Aa00000000003"

data = map[string]interface{}{
  "name": "Gaurav Kumar",
  "email": "gaurav.kumar@example.com",
  "contact": +919876543210,
}
body, err := client.Customer.Edit(customerId, data, nil)

```php: PHP
$api = new Api($key_id, $secret);

$api->customer->fetch($customerId)->edit(array('name' => 'Gaurav Kumar', 'email' => 'gaurav.kumar@example.com', 'contact': '+919876543210', 'notes'=> array('notes_key_1'=> 'Tea, Earl Grey, Hot','notes_key_2'=> 'Tea, Earl Grey… decaf')));

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

customerId = "cust_1Aa00000000003"

Razorpay::Customer.edit(customerId,{
  "name": "Gaurav Kumar",
  "email": "gaurav.kumar@example.com",
  "contact": +919876543210,
})

```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.customers.edit(customerId,{
  name: "Gaurav Kumar",
  email: "gaurav.kumar@example.com",
  contact: +919876543210
})

```csharp: .NET
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string customerId = "cust_1Aa00000000003";

Dictionary customerRequest = new Dictionary();
customerRequest.Add("name", "Gaurav Kumar");
customerRequest.Add("contact", "+919876543210");
customerRequest.Add("email", "gaurav.kumar@example.com");

Customer card = client.Customer.Fetch(customerId).Edit(customerRequest);

```bash: CLI
razorpay customers update cust_ABC123 --name "Gaurav Kumar" --contact "+919123456780" --email "gaurav.kumar@example.com"
```

### Parameters

`id` _mandatory_
: `string` The unique identifier linked to the customer.

### Parameters

`name` _optional_
: `string` Customer's name. Alphanumeric, with period (.), apostrophe ('), forward slash (/), at (@) and parentheses allowed. The name must be between 3-50 characters in length. For example, `Gaurav Kumar`.

`contact` _optional_
: `string` The customer's phone number. A maximum length of 15 characters. For example, `+919876543210`.

`email` _optional_
: `string` The customer's email address. A maximum length of 64 characters. For example, `gaurav.kumar@example.com`.

### Parameters

`id`
: `string` Unique identifier of the customer. For example, `cust_1Aa00000000004`.

`entity` _optional_
: `string` Indicates the type of entity.

`name` 
: `string` Customer's name. Alphanumeric, with period (.), apostrophe (') and parentheses allowed. The name must be between 3-50 characters in length.

`contact`
: `string` The customer's phone number. A maximum length of 15 characters including country code.

`email`
: `string` The customer's email address. A maximum length of 64 characters.

`gstin`
: `string` GST number linked to the customer. For example, `29XAbbA4369J1PA`.

`notes`
: `object` This is a key-value pair that can be used to store additional information about the entity. It can hold a maximum of 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

`created_at`
: `integer` UNIX timestamp, when the customer was created. For example, `1234567890`.

`shipping_address`
: `object` The customer's shipping address. An address object with `line1`, `line2`, `city`, `state`, `country`, and `zipcode` fields. Empty when none is set.

### Errors

The API `` provided is invalid.
* code: 4xx
* description: The API credentials passed in the API call differ from the ones generated on the Dashboard. Possible reasons: - Different keys for test mode and live modes.
- Expired API key.

* solution: The API keys must be active and entered correctly with no whitespace before or after the keys.
 
Contact number should be at least 8 digits, including country code.
* code: 400
* description: The contact number is less than 8 digits.
* solution: Enter a contact number that meets the validation criteria. It should have at least 8 digits, including the country code.

id is not a valid id.
* code: 400
* description: The `customer_id` passed is invalid.
* solution: Use a valid `customer_id`.

The id provided does not exist.
* code: 400
* description: The `customer_id` passed in the URL is well-formed but does not exist or does not belong to the requesting merchant.
* solution: Use a valid `customer_id` returned from `POST /v1/customers`. Confirm by fetching the customer before retrying.

Customer already exists for the merchant.
* code: 400
* description: The `contact` or `email` passed in the edit request matches an existing customer of this merchant other than the one being edited.
* solution: Use a different `contact` / `email`, or edit the matching customer record directly.

The email must be a valid email address.
* code: 400
* description: The value passed for `email` is not in a valid email format.
* solution: Pass a valid email address (for example, `user@example.com`).

Contact number contains invalid characters, only digits and + symbol are allowed.
* code: 400
* description: The `contact` value contains characters other than digits and the `+` symbol (for example, letters, hyphens or spaces).
* solution: Pass `contact` using only digits and an optional leading `+` for the country code.

The name may not be greater than 50 characters.
* code: 400
* description: The `name` value exceeds the 50-character limit.
* solution: Keep the `name` to 50 characters or fewer.

The name format is invalid.
* code: 400
* description: The `name` value contains characters outside the allowed set. Allowed characters are letters, numbers and a limited set of punctuation (`'`, `-`, `.`, `_`, `(`, `)`, `@`, `/` and spaces). The name must start and end with a letter, number, `.` or `)`.
* solution: Pass `name` using only the allowed characters and ensure it starts and ends with a letter, number, `.` or `)`.

The gstin field is invalid.
* code: 400
* description: The `gstin` value is not a valid Indian GSTIN. A GSTIN is a 15-character alphanumeric code in the format ``.
* solution: Pass a valid 15-character GSTIN.

Notes value cannot be greater than 512 characters.
* code: 400
* description: One of the values inside the `notes` object exceeds the 512-character limit per value.
* solution: Keep each `notes` value under 512 characters.
