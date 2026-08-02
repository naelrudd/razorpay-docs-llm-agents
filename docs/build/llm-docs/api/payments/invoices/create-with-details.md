# Create an Invoice With Customer Details

**POST** `/v1/invoices`

Use this endpoint to create an invoice using details such as `name`, `billing_address` and `shipping_address`. 

**INFO**

**Handy Tips**

You cannot create GST compliant invoices using APIs. This means you cannot add the following to the invoice when creating an invoice via APIs:

- tax rate
- cess
- HSN code
- SAC code

### Request

```cURL: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X POST https://api.razorpay.com/v1/invoices \
-H 'Content-type: application/json' \
-d '{
  "type": "invoice",
  "description": "Invoice for the month of January 2020",
  "partial_payment": true,
  "customer": {
    "name": "Gaurav Kumar",
    "contact": "+919876543210",
    "email": "gaurav.kumar@example.com",
    "billing_address": {
      "line1": "Bakers Street",
      "line2": "Country Road",
      "zipcode": "560068",
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "in"
    },
    "shipping_address": {
      "line1": "Bakers Street",
      "line2": "Country Road",
      "zipcode": "560068",
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "IN"
    }
  },
  "line_items": [
    {
      "name": "Master Cloud Computing in 30 Days",
      "description": "Book by Ravena Ravenclaw",
      "amount": 399,
      "currency": "INR",
      "quantity": 1
    }
  ],
  "sms_notify": true,
  "email_notify": false,
  "currency": "INR",
  "expire_by": 1589765167,
  "notes": {
    "key1": "Testing."
  }
}'

```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject invoiceRequest = new JSONObject();
invoiceRequest.put("type", "invoice");
invoiceRequest.put("description", "Invoice for the month of January 2020");
invoiceRequest.put("partial_payment",true);
JSONObject customer = new JSONObject();
customer.put("name","Gaurav Kumar");
customer.put("contact","+919876543210");
customer.put("email","gaurav.kumar@example.com");
JSONObject billingAddress = new JSONObject();
billingAddress.put("line1","Ground & 1st Floor, SJR Cyber Laskar");
billingAddress.put("line2","Hosur Road");
billingAddress.put("zipcode","560068");
billingAddress.put("city","Bengaluru");
billingAddress.put("state","Karnataka");
billingAddress.put("country","in");
customer.put("billing_address",billingAddress);
JSONObject shippingAddress = new JSONObject();
shippingAddress.put("line1","Ground & 1st Floor, SJR Cyber Laskar");
shippingAddress.put("line2","Hosur Road");
shippingAddress.put("zipcode","560068");
shippingAddress.put("city","Bengaluru");
shippingAddress.put("state","Karnataka");
shippingAddress.put("country","in");
customer.put("shipping_address",shippingAddress);
invoiceRequest.put("customer",customer);
List lines = new ArrayList<>();
JSONObject lineItems = new JSONObject();
lineItems.put("name","Master Cloud Computing in 30 Days");
lineItems.put("description","Book by Ravena Ravenclaw");
lineItems.put("amount",399);
lineItems.put("currency","INR");
lineItems.put("quantity",1);
lines.add(lineItems);
invoiceRequest.put("line_items",lines);
invoiceRequest.put("email_notify", true);
invoiceRequest.put("sms_notify", true);
invoiceRequest.put("currency","INR");
invoiceRequest.put("expire_by", 1580479824);

Invoice invoice = instance.invoices.create(invoiceRequest);

```python: Python
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.invoice.create({
  "type": "invoice",
  "description": "Invoice for the month of January 2020",
  "partial_payment": true,
  "customer": {
    "name": "Gaurav Kumar",
    "contact": "+919876543210",
    "email": "gaurav.kumar@example.com",
    "billing_address": {
      "line1": "Ground & 1st Floor, SJR Cyber Laskar",
      "line2": "Hosur Road",
      "zipcode": "560068",
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "in"
    },
    "shipping_address": {
      "line1": "Ground & 1st Floor, SJR Cyber Laskar",
      "line2": "Hosur Road",
      "zipcode": "560068",
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "in"
    }
  },
  "line_items": [
    {
      "name": "Master Cloud Computing in 30 Days",
      "description": "Book by Ravena Ravenclaw",
      "amount": 399,
      "currency": "INR",
      "quantity": 1
    }
  ],
  "sms_notify": True,
  "email_notify": True,
  "currency": "INR",
  "expire_by": 1589765167
})

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

line_items := make(map[string]interface{})
line_items["0"] = map[string]interface{}{
      "name": "Master Cloud Computing in 30 Days",
      "description": "Book by Ravena Ravenclaw",
      "amount": 399,
      "currency": "INR",
      "quantity": 1,
    }

data := map[string]interface{}{
  "type": "invoice",
  "description": "Invoice for the month of January 2020",
  "partial_payment": true,
  "customer": map[string]interface{}{
    "name": "Gaurav Kumar",
    "contact": "+919876543210",
    "email": "gaurav.kumar@example.com",
    "billing_address": map[string]interface{}{
      "line1": "Ground & 1st Floor, SJR Cyber Laskar",
      "line2": "Hosur Road",
      "zipcode": 560068,
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "in",
    },
    "shipping_address": map[string]interface{}{
      "line1": "Ground & 1st Floor, SJR Cyber Laskar",
      "line2": "Hosur Road",
      "zipcode": 560068,
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "in",
    },
  },
  "line_items": line_items,
  "sms_notify": true,
  "email_notify": true,
  "currency": "INR",
  "expire_by": 1589765167
}
body, err := client.Invoice.Create(data, nil)
```php: PHP
$api = new Api($key_id, $secret);

$api->invoice->create(array(
    'type' => 'invoice',
    'description' => 'Invoice for the month of January 2020',
    'partial_payment' => true,
    'customer' => array(
        'name' => 'Gaurav Kumar',
        'contact' => '+919876543210',
        'email' => 'gaurav.kumar@example.com',
        'billing_address' => array(
            'line1' => 'Ground & 1st Floor, SJR Cyber Laskar',
            'line2' => 'Hosur Road',
            'zipcode' => '560068',
            'city' => 'Bengaluru',
            'state' => 'Karnataka',
            'country' => 'in'
        ),
        'shipping_address' => array(
            'line1' => 'Ground & 1st Floor, SJR Cyber Laskar',
            'line2' => 'Hosur Road',
            'zipcode' => '560068',
            'city' => 'Bengaluru',
            'state' => 'Karnataka',
            'country' => 'in'
        )
    ),
    'line_items' => array(
        array(
            'name' => 'Master Cloud Computing in 30 Days',
            'description' => 'Book by Ravena Ravenclaw',
            'amount' => 399,
            'currency' => 'INR',
            'quantity' => 1
        )
    ),
    'sms_notify' => true,
    'email_notify' => true,
    'currency' => 'INR',
    'expire_by' => 1589765167
));

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay::Invoice.create({
  "type": "invoice",
  "description": "Invoice for the month of January 2020",
  "partial_payment": true,
  "customer": {
    "name": "Gaurav Kumar",
    "contact": "+919876543210",
    "email": "gaurav.kumar@example.com",
    "billing_address": {
      "line1": "Ground & 1st Floor, SJR Cyber Laskar",
      "line2": "Hosur Road",
      "zipcode": 560068,
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "in"
    },
    "shipping_address": {
      "line1": "Ground & 1st Floor, SJR Cyber Laskar",
      "line2": "Hosur Road",
      "zipcode": 560068,
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "in"
    }
  },
  "line_items": [
    {
      "name": "Master Cloud Computing in 30 Days",
      "description": "Book by Ravena Ravenclaw",
      "amount": 399,
      "currency": "INR",
      "quantity": 1
    }
  ],
  "sms_notify": 1,
  "email_notify": 1,
  "currency": "INR",
  "expire_by": 1589765167
})

```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.invoice.create({
  "type": "invoice",
  "description": "Invoice for the month of January 2020",
  "partial_payment": true,
  "customer": {
    "name": "Gaurav Kumar",
    "contact": "+919876543210",
    "email": "gaurav.kumar@example.com",
    "billing_address": {
      "line1": "Ground & 1st Floor, SJR Cyber Laskar",
      "line2": "Hosur Road",
      "zipcode": 560068,
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "in"
    },
    "shipping_address": {
      "line1": "Ground & 1st Floor, SJR Cyber Laskar",
      "line2": "Hosur Road",
      "zipcode": 560068,
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "in"
    }
  },
  "line_items": [
    {
      "name": "Master Cloud Computing in 30 Days",
      "description": "Book by Ravena Ravenclaw",
      "amount": 399,
      "currency": "INR",
      "quantity": 1
    }
  ],
  "sms_notify": true,
  "email_notify": true,
  "currency": "INR",
  "expire_by": 1589765167
})

```csharp: .NET
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary invoiceRequest = new Dictionary();
invoiceRequest.Add("type", "invoice");
invoiceRequest.Add("description", "Invoice for the month of January 2020");
invoiceRequest.Add("partial_payment", true);
Dictionary customer = new Dictionary();
customer.Add("name", "Gaurav Kumar");
customer.Add("contact", "+919876543210");
customer.Add("email", "gaurav.kumar@example.com");
Dictionary billingAddress = new Dictionary();
billingAddress.Add("line1", "Bakers Street");
billingAddress.Add("line2", "Country Road");
billingAddress.Add("zipcode", "560068");
billingAddress.Add("city", "Bengaluru");
billingAddress.Add("state", "Karnataka");
billingAddress.Add("country", "in");
customer.Add("billing_address", billingAddress);
Dictionary shippingAddress = new Dictionary();
shippingAddress.Add("line1", "Bakers Street");
shippingAddress.Add("line2", "Country Road");
shippingAddress.Add("zipcode", "560068");
shippingAddress.Add("city", "Bengaluru");
shippingAddress.Add("state", "Karnataka");
shippingAddress.Add("country", "in");
customer.Add("shipping_address", shippingAddress);
invoiceRequest.Add("customer", customer);
List> lines = new List>();
Dictionary lineItems = new Dictionary();
lineItems.Add("name", "Master Cloud ComAdding in 30 Days");
lineItems.Add("description", "Book by Ravena Ravenclaw");
lineItems.Add("amount", 399);
lineItems.Add("currency", "INR");
lineItems.Add("quantity", 1);
lines.Add(lineItems);
invoiceRequest.Add("line_items", lines);
invoiceRequest.Add("email_notify", true);
invoiceRequest.Add("sms_notify", true);
invoiceRequest.Add("currency", "INR");
invoiceRequest.Add("expire_by", 1580479824);

Invoice invoice = client.Invoice.Create(invoiceRequest);
```bash: CLI
razorpay invoices create \
  --type invoice \
  --customer-name "Gaurav Kumar" \
  --customer-contact "+919123456780" \
  --customer-email "gaurav.kumar@example.com" \
  --billing-line1 "Bakers Street" \
  --billing-line2 "Country Road" \
  --billing-zipcode "560068" \
  --billing-city "Bengaluru" \
  --billing-state "Karnataka" \
  --billing-country "in" \
  --description "Invoice for January 2024" \
  --currency INR \
  --line-items '[{"name":"Master Cloud Computing in 30 Days","description":"Book by Ravena Ravenclaw","amount":399,"currency":"INR","quantity":1}]' \
  --expire-by 1776759660 \
  --note key1="Testing."
```

### Response

```json: Success 
{
  "id": "inv_E7q0tqkxBRzdau",
  "entity": "invoice",
  "receipt": null,
  "invoice_number": null,
  "customer_id": "cust_E7q0trFqXgExmT",
  "customer_details": {
    "id": "cust_E7q0trFqXgExmT",
    "name": "Gaurav Kumar",
    "email": "gaurav.kumar@example.com",
    "contact": "+919876543210",
    "gstin": null,
    "billing_address": {
      "id": "addr_E7q0ttqh4SGhAC",
      "type": "billing_address",
      "primary": true,
      "line1": "Bakers Street",
      "line2": "Country Road",
      "zipcode": "560068",
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "in"
    },
    "shipping_address": {
      "id": "addr_E7q0ttKwVA1h2V",
      "type": "shipping_address",
      "primary": true,
      "line1": "Bakers Street",
      "line2": "Country Road",
      "zipcode": "560068",
      "city": "Bengaluru",
      "state": "Karnataka",
      "country": "in"
    },
    "customer_name": "Gaurav Kumar",
    "customer_email": "gaurav.kumar@example.com",
    "customer_contact": "+919876543210"
  },
  "order_id": "order_E7q0tvRpC0WJwg",
  "line_items": [
    {
      "id": "li_E7q0tuPNg84VbZ",
      "item_id": null,
      "ref_id": null,
      "ref_type": null,
      "name": "Master Cloud Computing in 30 Days",
      "description": "Book by Ravena Ravenclaw",
      "amount": 399,
      "unit_amount": 399,
      "gross_amount": 399,
      "tax_amount": 0,
      "taxable_amount": 399,
      "net_amount": 399,
      "currency": "INR",
      "type": "invoice",
      "tax_inclusive": false,
      "hsn_code": null,
      "sac_code": null,
      "tax_rate": null,
      "unit": null,
      "quantity": 1,
      "taxes": []
    }
  ],
  "payment_id": null,
  "status": "issued",
  "expire_by": 1589765167,
  "issued_at": 1579765167,
  "paid_at": null,
  "cancelled_at": null,
  "expired_at": null,
  "sms_status": "pending",
  "email_status": "pending",
  "date": 1579765167,
  "terms": null,
  "partial_payment": true,
  "gross_amount": 399,
  "tax_amount": 0,
  "taxable_amount": 399,
  "amount": 399,
  "amount_paid": 0,
  "amount_due": 399,
  "currency": "INR",
  "currency_symbol": "$",
  "description": "Invoice for the month of January 2020",
  "notes": [],
  "comment": null,
  "short_url": "https://rzp.io/i/2wxV8Xs",
  "view_less": true,
  "billing_start": null,
  "billing_end": null,
  "type": "invoice",
  "group_taxes_discounts": false,
  "created_at": 1579765167
}

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

`type` _mandatory_
: `string` Indicates the type of entity. Here, it is `invoice`.

`description` _optional_
: `string` A brief description of the invoice.

`draft` _optional_
: `string` Invoice is created in `draft` state when value is set to `1`.

`customer_id` _mandatory_
: `string` You can pass the `customer_id` in this field, if you are using the [Customers API](https://razorpay.com/docs/build/llm-docs/api/customers.md). If not, you can pass the customer object described in the below fields.

`customer`
: `object` Customer details.

    `name` _mandatory_
    : `string` Customer's name. Alphanumeric, with period (.), apostrophe (') and parentheses allowed. The name must be between 3-50 characters in length. For example, `Gaurav Kumar`.

    `email` _optional_
    : `string` The customer's email address. A maximum length of 64 characters. For example, `gaurav.kumar@example.com`.

    `contact` _optional_
    : `string` The customer's phone number. A maximum length of 15 characters including country code. For example, `+919876543210`.

    `billing_address` 
    : `object` The customer's billing address.

      `line1` _mandatory_
      : `string` The first line of the customer's address.

      `line2` _optional_
      : `string` The second line of the customer's address.

      `city` _mandatory_
      : `string` The city

      `zipcode` _mandatory_
      : `string` The zipcode

      `state` _mandatory_
      : `string` The state

      `country` _mandatory_
      : `string` The country

    `shipping_address`
    : `object` The customer's shipping address.

      `line1` _mandatory_
      : `string` The first line of the customer's address.

      `line2` _optional_
      : `string` The second line of the customer's address.

      `city` _mandatory_
      : `string` The city

      `zipcode` _mandatory_
      : `string` The zipcode

      `state` _mandatory_
      : `string` The state

      `country` _mandatory_
      : `string` The country

`line_items`
: `object` Details of the line item that is billed in the invoice. Maximum of 50 line items.

    `item_id` _conditionally mandatory_
    : `string` If you are using the [Items API](https://razorpay.com/docs/build/llm-docs/api/payments/invoices/create-item.md), you may use an existing item. You can choose to override details such as name, description by passing these along with `item_id`. While the invoice will show the updated details, the existing item will not be updated. This parameter is mandatory if you are not going to use any other parameter in the array.

    `name` _conditionally mandatory_
    : `string` The item name. Mandatory if `item_id` is not provided.

    `description` _optional_
    : `string` A brief description of the item.

    `amount` _conditionally mandatory_
    : `integer` Amount to be paid using the invoice. Must be in the smallest unit of the currency. For example, if the amount to be received from the customer is 300, pass the value as `30000`. Mandatory if `item_id` is not provided.

    `currency` _optional_
    : `string` The currency associated with the item. Defaults to `INR`. Know about the [list of supported international currencies.](https://razorpay.com/docs/build/llm-docs/payments/international-payments.md#supported-currencies) This should match invoice currency.

    `quantity` _optional_
    : `integer` The number of units of the item billed in the invoice. Defaults to `1`.

.

    `quantity` _optional_
    : `integer` The number of units of the item billed in the invoice. Defaults to `1`.

`expire_by` _optional_
: `integer` Timestamp, in Unix format, at which the invoice will expire.

`sms_notify` _optional_
: `boolean` Defines who handles the SMS notification. Possible values:
   - `true` (default): Razorpay sends the notification to the customer.
   - `false`: You send the notification to the customer.

`email_notify` _optional_
: `boolean` Defines who handles the email notification. Possible values:
   - `true` (default): Razorpay sends the notification to the customer.
   - `false`: You send the notification to the customer.

`partial_payment`
: `boolean` Indicates whether the customer can make a partial payment on the invoice. Possible values:
   - `true`: The customer can make partial payments.
   - `false` (default): The customer cannot make partial payments.

`currency` _conditionally mandatory_
: `string` The currency associated with the invoice. You must mandatorily pass this parameter if accepting international payments. If you have passed `currency` as a sub-parameter in the `line_item` object, you must ensure that the same currency is passed in both places. Know about the [list of supported international currencies.](https://razorpay.com/docs/build/llm-docs/payments/international-payments.md#supported-currencies)

.

`notes` _optional_
: `string` Any custom notes added to the invoice. Maximum of 2048 characters.

### Parameters

`id`
: `string` The unique identifier of the invoice.

`entity`
: `string` Indicates the type of entity. Here, it is `invoice`.

`type`
: `string` Here, it should be `invoice`.

`invoice_number`
: `string` Unique number you added for internal reference. The minimum character length is 1 and maximum is 40.

`customer_id`
: `string` The unique identifier of the customer. You can create `customer_id` using the [Customers API](https://razorpay.com/docs/build/llm-docs/api/customers.md). Alternatively, you can pass the customer object described in the below fields.

`customer_details`
: `object` Details of the customer.

    `id`
    : `string` Unique identifier of the customer. For example, `cust_1Aa00000000004`.

    `name`
    : `string` Customer's name. Alphanumeric, with period (.), apostrophe (') and parentheses allowed. The name must be between 3-50 characters in length. For example, `Gaurav Kumar`.

    `email`
    : `string` The customer's email address. A maximum length of 64 characters. For example, `gaurav.kumar@example.com`.

    `contact`
    : `string` The customer's phone number. A maximum length of 15 characters including country code. For example, `+919876543210`.

    `billing_address`
    : `object` Details of the customer's billing address.

        `id`
        : `string` The unique identifier generated for the customer's billing address.

        `type`
        : `string` The customer address type. Here it is `billing_address`.

        `primary`
        : `boolean` Defines if this is the primary address.
            - `true`: It is the customer's primary address.
            - `false`: It is not the customer's primary address.

        `line1`
        : `string` The first line of the customer's address.

        `line2`
        : `string` The second line of the customer's address.

        `city`
        : `string` The city.

        `zipcode`
        : `string` The zipcode.

        `state`
        : `string` The state.

        `country`
        : `string` The country.

    `shipping_address`
    : `object` Details of the customer's shipping address.

        `id`
        : `string` The unique identifier generated for the customer's shipping address.

        `type`
        : `string` The customer address type. Here it is `shipping_address`.

        `primary`
        : `boolean` Defines if this is the primary address.
            - `true`: It is the customer's primary address.
            - `false`: It is not the customer's primary address.

        `line1`
        : `string` The first line of the customer's address.

        `line2`
        : `string` The second line of the customer's address.

        `city`
        : `string` The city.

        `zipcode`
        : `string` The zipcode.

        `state`
        : `string` The state.

        `country`
        : `string` The country.

`order_id`
: `string` The unique identifier of the order associated with the invoice.

`line_items`
: `object` Details of the line item that is billed in the invoice. Maximum of 50 line items.

    `id`
    : `string` Unique identifier that is generated if a new item has been created while creating the invoice.

    `item_id`
    : `string` Unique identifier of the item generated using Items API that has been billed in the invoice.

    `name`
    : `string` The item's name.

    `description`
    : `string` A brief description of the item.

    `amount`
    : `integer` The price of the item.

    `currency`
    : `string` The currency associated with the item. Default is `INR`. Know about the [list of supported international currencies](https://razorpay.com/docs/build/llm-docs/payments/international-payments.md#supported-currencies).

    `type`
    : `string` Here, it is `invoice`.

    `quantity`
    : `integer` The quantity of the item billed in the invoice. Defaults to `1`.

.

    `type`
    : `string` Here, it is `invoice`.

    `quantity`
    : `integer` The quantity of the item billed in the invoice. Defaults to `1`.

`payment_id`
: `string` Unique identifier of a payment made against this invoice.

`status`
: `string` The status of the invoice. Know more about [Invoice States](https://razorpay.com/docs/build/llm-docs/payments/invoices/states.md). Possible values:
    - `draft`
    - `issued`
    - `partially_paid`
    - `paid`
    - `cancelled`
    - `expired`
    - `deleted`

`expire_by`
: `integer` Timestamp, in Unix format, at which the invoice will expire.

`issued_at`
: `integer` Timestamp, in Unix format, at which the invoice was issued to the customer.

`paid_at`
: `integer` Timestamp, in Unix format, at which the payment was made.

`cancelled_at`
: `integer` Timestamp, in Unix format, at which the invoice was cancelled.

`expired_at`
: `integer` Timestamp, in Unix format, at which the invoice expired.

`sms_status`
: `string` The delivery status of the SMS notification for the invoice sent to the customer. Possible values:
  - `pending`
  - `sent`

`email_status`
: `string` The delivery status of the email notification for the invoice sent to the customer. Possible values:
  - `pending`
  - `sent`

`partial_payment`
: `boolean` Indicates whether the customer can make a partial payment on the invoice. Possible values:
  - `true`:  The customer can make partial payments.
  - `false` (default): The customer cannot make partial payments.

`amount`
: `integer` Amount to be paid using the invoice. Must be in the smallest unit of the currency. For example, if the amount to be received from the customer is , pass the value as `30000`.

`amount_paid`
: `integer` Amount paid by the customer against the invoice.

`amount_due`
: `integer` The remaining amount to be paid by the customer for the issued invoice.

`currency`
: `string` The currency associated with the invoice. You must mandatorily pass this parameter if accepting international payments. If you have passed `currency` as a sub-parameter in the `line_item` object, you must ensure that the same currency is passed in both places. Know about the [list of supported international currencies.](https://razorpay.com/docs/build/llm-docs/payments/international-payments.md#supported-currencies)

.

`description`
: `string`  A brief description of the invoice. The maximum character length is 2048.

`notes`
: `object` Any custom notes added to the invoice. Maximum of 2048 characters.

`short_url`
: `string` The short URL that is generated. Share this link with customers to accept payments.

`date`
: `integer` Timestamp, in Unix format, that indicates the issue date of the invoice.

`terms`
: `string` Any terms to be included in the invoice. Maximum of 2048 characters.

`comment`
: `string` Any comments to be added in the invoice. Maximum of 2048 characters.
`ref_num`
: `string` A unique reference number for the invoice, used for internal tracking and reconciliation.

`receipt`
: `string` A unique receipt number that you can provide for the invoice, for your internal reference.

`currency_symbol`
: `string` For example, `₹`.

`billing_end`
: `integer` Unix timestamp marking the end of the billing period for the invoice.

`gross_amount`
: `integer` The gross amount for this invoice, in the smallest currency unit (paise for INR). For example, `50000`.

`billing_start`
: `integer` Unix timestamp marking the start of the billing period for the invoice.

### Errors

The API `` provided is invalid.
* code: 4xx
* description: The API key or secret are not entered or an invalid API key is used.
* solution: Use and enter the correct API details while executing the API.

customer is required.
* code: 400
* description: An invoice is issued without adding customer details.
* solution: Ensure that the customer details are entered.

the merchant doesn't have international activated.
* code: 400
* description: The line_items object has an international currency set. For example, USD, is not enabled for your account.
* solution: Ensure that your account has international payments enabled.

Currency of all items should be the same as of the invoice.
* code: 400
* description: There is a difference in currency entered between `line_items` and invoice currency.
* solution: Ensure that the `line_items` currency matches that of the invoice.

expire_by should be at least 15 minutes after current time.
* code: 400
* description: The expiry date is before or within 15 minutes of the current time
* solution: Ensure that the Expiry date is greater than the (current time + 15 minutes). For example, if the current time is 1 pm, the expiry date must be at least 1.15 pm.

line_items is required.
* code: 400
* description: A mandatory field is empty.
* solution: Ensure that you fill all the mandatory fields.

Not a valid type.
* code: 400
* description: The value passed for `type` is not one of the supported types. The API echoes the rejected value, for example `Not a valid type: invoiceee`.
* solution: Use a supported `type` value, for example `invoice`, `ecod` or `link`.

The amount must be at least INR 1.00.
* code: 400
* description: A line-item `amount` is below the per-currency minimum (`100` paise / ₹1.00 for INR). Also returned for zero or negative line-item amounts.
* solution: Pass each `line_items[].amount` greater than or equal to the per-currency minimum.

The amount must be an integer.
* code: 400
* description: A non-integer value (for example a decimal like `100.5` or a string like `"abc"`) was passed for a `line_items[].amount`.
* solution: Pass `amount` as an integer in currency subunits (paise for INR).

The quantity must be at least 1.
* code: 400
* description: A line-item `quantity` was passed as `0` or a negative value.
* solution: Pass `line_items[].quantity` as a positive integer (`1` or higher).

The email must be a valid email address.
* code: 400
* description: The value passed for `customer.email` is not in a valid email format.
* solution: Pass `customer.email` as a valid email address.

Contact number contains invalid characters, only digits and + symbol are allowed.
* code: 400
* description: The `customer.contact` value contains characters other than digits and the `+` symbol.
* solution: Pass `customer.contact` using only digits and an optional leading `+` for the country code.

The partial payment field must be true or false.
* code: 400
* description: A non-boolean value was passed for `partial_payment`.
* solution: Pass `partial_payment` as a boolean (`true` or `false`).

\{any extra field\} is/are not required and should not be sent.
* code: 400
* description: The request body contains fields that are not part of the Invoices API schema.
* solution: Only include documented fields. Remove any unknown keys from the request body.

Invoices disabled because fee bearer is customer.
* code: 400
* description: Your account has the customer fee bearer model enabled, which is not compatible with invoice creation.
* solution: Contact [Razorpay support](https://razorpay.com/support/) to switch the fee-bearer configuration before creating invoices.

Item cannot be used as it is inactive.
* code: 400
* description: A `line_items[].item_id` passed in the request refers to an item that has been marked inactive.
* solution: Activate the item via the Update Item API, or use a different active item.

The merchant doesn't have international activated.
* code: 400
* description: The `currency` passed is different from your account's default currency, but international payments are not enabled on your account.
* solution: Enable international payments from your Razorpay Dashboard, or use your account's default currency.

Currency is not supported.
* code: 400
* description: The `currency` value is not a recognised ISO-4217 currency code or is outside the list supported by Razorpay.
* solution: Use a supported ISO-4217 currency code.

Invoice amount exceeds maximum payment amount allowed.
* code: 400
* description: The total invoice amount (sum of `line_items[].amount * quantity`) exceeds the per-payment maximum configured for your account.
* solution: Split the billing into multiple invoices, or contact [Razorpay support](https://razorpay.com/support/) to raise your per-payment limit.

expire_by should be at least 15 minutes after current time.
* code: 400
* description: The `expire_by` value is in the past or less than 15 minutes from the current server time.
* solution: Pass `expire_by` as a Unix-epoch integer at least 15 minutes in the future.

Request failed. Please try after sometime.
* code: 429
* description: You have exceeded the daily rate limit for invoice creation. This per-day rate limit applies to test-mode accounts and unregistered live-mode accounts. In test mode the limit is 300 invoices/day; in live mode for unregistered businesses it is 10,000 invoices/day. Registered live-mode accounts are not subject to this limit.
* solution: Wait until the next day for the limit to reset. If you need a higher limit, register your business on the Razorpay Dashboard or contact [Razorpay support](https://razorpay.com/support/).
