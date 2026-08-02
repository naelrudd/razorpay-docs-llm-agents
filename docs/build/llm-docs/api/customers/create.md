# Create a Customer

**POST** `/v1/customers`

Use this endpoint to create or add a customer with basic details such as name and contact details.

### Request

```cURL: Curl

curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/customers \
-H "Content-Type: application/json" \
-d '{
    "name": "Gaurav Kumar",
    "contact": "9123456780",
    "email": "gaurav.kumar@example.com",
    "fail_existing": "0",
    "notes": {
      "notes_key_1": "Tea, Earl Grey, Hot",
      "notes_key_2": "Tea, Earl Grey… decaf."
  }
}'

```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject customerRequest = new JSONObject();
customerRequest.put("name","Gaurav Kumar");
customerRequest.put("contact","9123456780");
customerRequest.put("email","gaurav.kumar@example.com");
customerRequest.put("fail_existing","0");
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
customerRequest.put("notes",notes);

Customer customer = razorpay.customers.create(customerRequest);

```python: Python
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.customer.create({
  "name": "Gaurav Kumar",
  "contact": 9123456780,
  "email": "gaurav.kumar@example.com",
  "fail_existing": "0",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
})

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
    "name": "Gaurav Kumar",
    "contact": 9123456780,
    "email": "gaurav.kumar@example.com",
    "fail_existing": "0",
    "notes": map[string]interface{}{
      "notes_key_1": "Tea, Earl Grey, Hot",
      "notes_key_2": "Tea, Earl Grey… decaf.",
	},
}

body, err := client.Customer.Create(data, nil)

```php: PHP
$api = new Api($key_id, $secret);

$api->customer->create(array('name' => 'Gaurav Kumar', 'email' => 'gaurav.kumar@example.com','contact'=>'9123456780','notes'=> array('notes_key_1'=> 'Tea, Earl Grey, Hot','notes_key_2'=> 'Tea, Earl Grey… decaf'));

```csharp: .NET
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary options = new Dictionary();

options.Add("name", "Gaurav Kumar"); 
options.Add("contact", "9123456780"); 
options.Add("email", "gaurav.kumar@example.com"); 
options.Add("fail_existing", "0"); 

Customer customer = Customer.Create(options);

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay::Customer.create({
  "name": "Gaurav Kumar",
  "contact": 9123456780,
  "email": "gaurav.kumar@example.com",
  "fail_existing": "0",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
})

```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.customers.create({
  name: "Gaurav Kumar",
  contact: 9123456780,
  email: "gaurav.kumar@example.com",
  fail_existing: "0",
  notes: {
    notes_key_1: "Tea, Earl Grey, Hot",
    notes_key_2: "Tea, Earl Grey… decaf."
  }
})

```bash: CLI
razorpay customers create --name "Gaurav Kumar" --contact "+919123456780" --email "gaurav.kumar@example.com" --gstin "29XAbbA4369J1PA" --note key1="Test customer"
```

### Response

```json: Success
{
  "id" : "cust_1Aa00000000004",
  "entity": "customer",
  "name" : "Gaurav Kumar",
  "email" : "gaurav.kumar@example.com",
  "contact" : "+919876543210",
  "gstin": null,
  "notes": {
    "notes_key_1":"Tea, Earl Grey, Hot",
    "notes_key_2":"Tea, Earl Grey… decaf."
  },
  "created_at ": 1234567890
}
```json: Failure
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

### Parameters

`name` _optional_
: `string` Customer's name. Alphanumeric value with period (.), apostrophe ('), forward slash (/), at (@) and parentheses are allowed. The name must be between 3-50 characters in length. For example, `Gaurav Kumar`.

`contact ` _optional_
: `string` The customer's phone number. A maximum length of 15 characters including country code. For example, `+919876543210`.

`email ` _optional_
: `string` The customer's email address. A maximum length of 64 characters. For example, `gaurav.kumar@example.com`.

`fail_existing` _optional_
: `string` Possible values:
     - `1` (default): If a customer with the same details already exists, throws an error.
     - `0`: If a customer with the same details already exists, fetches details of the existing customer.
   

`gstin` _optional_
: `string` Customer's GST number, if available. For example, `29XAbbA4369J1PA`.

`notes` _optional_
: `object` This is a key-value pair that can be used to store additional information about the entity. It can hold a maximum of 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

### Parameters

`id`
: `string` Unique identifier of the customer. For example, `cust_1Aa00000000004`.

`entity` _optional_
: `string` Indicates the type of entity.

`name` 
: `string` Customer's name. Alphanumeric, with period (.), apostrophe ('), forward slash (/), at (@) and parentheses allowed. The name must be between 3-50 characters in length.

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
* solution: Enter contact number that meets the validation criteria. It should have at least 8 digits, including the country code. For example, "+919876543210".

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

Customer already exists for the merchant.
* code: 400
* description: A customer with the same `contact` or `email` already exists for this merchant and `fail_existing` was set to `1` (or omitted, which defaults to fail).
* solution: Either use a different `contact` / `email`, or pass `fail_existing: "0"` in the request body to receive the existing customer in the response instead of an error.

Notes should not have more than 15 keys.
* code: 400
* description: The `notes` object contains more than 15 key-value pairs.
* solution: Reduce the number of keys in the `notes` object to 15 or fewer.

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
