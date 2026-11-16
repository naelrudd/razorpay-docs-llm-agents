> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create an Invoice With Customer Details

> Create an Invoice with basic details such as name and billing address.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇺🇸 United States

Use this endpoint to create an invoice using details such as `name`, `billing_address` and `shipping_address`.

> [!NOTE]
>
> **Handy Tips**
>
> You cannot create GST compliant invoices using APIs. This means you cannot add the following to the invoice when creating an invoice via APIs:\\
>
> * tax rate
> * cess
> * HSN code
> * SAC code

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X POST https://api.razorpay.com/v1/invoices \
-H 'Content-type: application/json' \
-d '{
  "type": "invoice",
  "description": "Invoice for the month of January 2020",
  "partial_payment": true,
  "customer": {
    "name": "<name>",
    "contact": "<phone>",
    "email": "<email>",
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
      "currency": "USD",
      "quantity": 1
    }
  ],
  "sms_notify": true,
  "email_notify": false,
  "currency": "USD",
  "expire_by": 1589765167,
  "notes": {
    "key1": "Testing."
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject invoiceRequest = new JSONObject();
invoiceRequest.put("type", "invoice");
invoiceRequest.put("description", "Invoice for the month of January 2020");
invoiceRequest.put("partial_payment",true);
JSONObject customer = new JSONObject();
customer.put("name","<name>");
customer.put("contact","<phone>");
customer.put("email","<email>");
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
List<Object> lines = new ArrayList<>();
JSONObject lineItems = new JSONObject();
lineItems.put("name","Master Cloud Computing in 30 Days");
lineItems.put("description","Book by Ravena Ravenclaw");
lineItems.put("amount",399);
lineItems.put("currency","USD");
lineItems.put("quantity",1);
lines.add(lineItems);
invoiceRequest.put("line_items",lines);
invoiceRequest.put("email_notify", true);
invoiceRequest.put("sms_notify", true);
invoiceRequest.put("currency","USD");
invoiceRequest.put("expire_by", 1580479824);

Invoice invoice = instance.invoices.create(invoiceRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.invoice.create({
  "type": "invoice",
  "description": "Invoice for the month of January 2020",
  "partial_payment": true,
  "customer": {
    "name": "<name>",
    "contact": "<phone>",
    "email": "<email>",
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
      "currency": "USD",
      "quantity": 1
    }
  ],
  "sms_notify": True,
  "email_notify": True,
  "currency": "USD",
  "expire_by": 1589765167
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

line_items := make(map[string]interface{})
line_items["0"] = map[string]interface{}{
      "name": "Master Cloud Computing in 30 Days",
      "description": "Book by Ravena Ravenclaw",
      "amount": 399,
      "currency": "USD",
      "quantity": 1,
    }

data := map[string]interface{}{
  "type": "invoice",
  "description": "Invoice for the month of January 2020",
  "partial_payment": true,
  "customer": map[string]interface{}{
    "name": "<name>",
    "contact": "<phone>",
    "email": "<email>",
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
  "currency": "USD",
  "expire_by": 1589765167
}
body, err := client.Invoice.Create(data, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->invoice->create(array(
    'type' => 'invoice',
    'description' => 'Invoice for the month of January 2020',
    'partial_payment' => true,
    'customer' => array(
        'name' => '<name>',
        'contact' => '<phone>',
        'email' => '<email>',
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
            'currency' => 'USD',
            'quantity' => 1
        )
    ),
    'sms_notify' => true,
    'email_notify' => true,
    'currency' => 'USD',
    'expire_by' => 1589765167
));
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay::Invoice.create({
  "type": "invoice",
  "description": "Invoice for the month of January 2020",
  "partial_payment": true,
  "customer": {
    "name": "<name>",
    "contact": "<phone>",
    "email": "<email>",
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
      "currency": "USD",
      "quantity": 1
    }
  ],
  "sms_notify": 1,
  "email_notify": 1,
  "currency": "USD",
  "expire_by": 1589765167
})
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.invoice.create({
  "type": "invoice",
  "description": "Invoice for the month of January 2020",
  "partial_payment": true,
  "customer": {
    "name": "<name>",
    "contact": "<phone>",
    "email": "<email>",
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
      "currency": "USD",
      "quantity": 1
    }
  ],
  "sms_notify": true,
  "email_notify": true,
  "currency": "USD",
  "expire_by": 1589765167
})
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> invoiceRequest = new Dictionary<string, object>();
invoiceRequest.Add("type", "invoice");
invoiceRequest.Add("description", "Invoice for the month of January 2020");
invoiceRequest.Add("partial_payment", true);
Dictionary<string, object> customer = new Dictionary<string, object>();
customer.Add("name", "<name>");
customer.Add("contact", "<phone>");
customer.Add("email", "<email>");
Dictionary<string, object> billingAddress = new Dictionary<string, object>();
billingAddress.Add("line1", "Bakers Street");
billingAddress.Add("line2", "Country Road");
billingAddress.Add("zipcode", "560068");
billingAddress.Add("city", "Bengaluru");
billingAddress.Add("state", "Karnataka");
billingAddress.Add("country", "in");
customer.Add("billing_address", billingAddress);
Dictionary<string, object> shippingAddress = new Dictionary<string, object>();
shippingAddress.Add("line1", "Bakers Street");
shippingAddress.Add("line2", "Country Road");
shippingAddress.Add("zipcode", "560068");
shippingAddress.Add("city", "Bengaluru");
shippingAddress.Add("state", "Karnataka");
shippingAddress.Add("country", "in");
customer.Add("shipping_address", shippingAddress);
invoiceRequest.Add("customer", customer);
List<Dictionary<string, object>> lines = new List<Dictionary<string, object>>();
Dictionary<string, object> lineItems = new Dictionary<string, object>();
lineItems.Add("name", "Master Cloud ComAdding in 30 Days");
lineItems.Add("description", "Book by Ravena Ravenclaw");
lineItems.Add("amount", 399);
lineItems.Add("currency", "USD");
lineItems.Add("quantity", 1);
lines.Add(lineItems);
invoiceRequest.Add("line_items", lines);
invoiceRequest.Add("email_notify", true);
invoiceRequest.Add("sms_notify", true);
invoiceRequest.Add("currency", "USD");
invoiceRequest.Add("expire_by", 1580479824);

Invoice invoice = client.Invoice.Create(invoiceRequest);
```

```bash CLI theme={null}
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

```json Success theme={null}
{
  "id": "inv_E7q0tqkxBRzdau",
  "entity": "invoice",
  "receipt": null,
  "invoice_number": null,
  "customer_id": "cust_E7q0trFqXgExmT",
  "customer_details": {
    "id": "cust_E7q0trFqXgExmT",
    "name": "<name>",
    "email": "<email>",
    "contact": "<phone>",
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
    "customer_name": "<name>",
    "customer_email": "<email>",
    "customer_contact": "<phone>"
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
      "currency": "USD",
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
  "currency": "USD",
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

**type** `string` *required*

Indicates the type of entity. Here, it is `invoice`.

**description** `string`

A brief description of the invoice.

**draft** `string`

Invoice is created in `draft` state when value is set to `1`.

**customer\_id** `string` *required*

You can pass the `customer_id` in this field, if you are using the [Customers API](https://razorpay.com/docs/api/customers.md). If not, you can pass the customer object described in the below fields.

**customer** `object`

Customer details.

**name** `string` *required*

Customer's name. Alphanumeric, with period (.), apostrophe (') and parentheses allowed. The name must be between 3-50 characters in length. For example, `Gaurav Kumar`.

**email** `string`

The customer's email address. A maximum length of 64 characters. For example, `gaurav.kumar@example.com`.

**contact** `string`

The customer's phone number. A maximum length of 15 characters including country code. For example, `+919876543210`.

**billing\_address** `object`

The customer's billing address.

**line1** `string` *required*

The first line of the customer's address.

**line2** `string`

The second line of the customer's address.

**city** `string` *required*

The city

**zipcode** `string` *required*

The zipcode

**state** `string` *required*

The state

**country** `string` *required*

The country

**shipping\_address** `object`

The customer's shipping address.

**line1** `string` *required*

The first line of the customer's address.

**line2** `string`

The second line of the customer's address.

**city** `string` *required*

The city

**zipcode** `string` *required*

The zipcode

**state** `string` *required*

The state

**country** `string` *required*

The country

**line\_items** `object`

Details of the line item that is billed in the invoice. Maximum of 50 line items.

**item\_id** `string` *required*

If you are using the [Items API](https://razorpay.com/docs/us/api/payments/invoices/create-item.md), you may use an existing item. You can choose to override details such as name, description by passing these along with `item_id`. While the invoice will show the updated details, the existing item will not be updated. This parameter is mandatory if you are not going to use any other parameter in the array.

**name** `string` *required*

The item name. Mandatory if `item_id` is not provided.

**description** `string`

A brief description of the item.

**amount** `integer` *required*

Amount to be paid using the invoice. Must be in the smallest unit of the currency. For example, if the amount to be received from the customer is ₹300, pass the value as `30000`. Mandatory if `item_id` is not provided.

**currency** `string`

The currency associated with the item. Defaults to `INR`. Know about the [list of supported international currencies.](https://razorpay.com/docs/payments/international-payments#supported-currencies) This should match invoice currency.

**quantity** `integer`

The number of units of the item billed in the invoice. Defaults to `1`.

**expire\_by** `integer`

Timestamp, in Unix format, at which the invoice will expire.

**sms\_notify** `boolean`

Defines who handles the SMS notification. Possible values:

* `true` (default): Razorpay sends the notification to the customer.
* `false`: You send the notification to the customer.

**email\_notify** `boolean`

Defines who handles the email notification. Possible values:

* `true` (default): Razorpay sends the notification to the customer.
* `false`: You send the notification to the customer.

**partial\_payment** `boolean`

Indicates whether the customer can make a partial payment on the invoice. Possible values:

* `true`: The customer can make partial payments.
* `false` (default): The customer cannot make partial payments.

**currency** `string` *required*

The currency associated with the invoice. You must mandatorily pass this parameter if accepting international payments. If you have passed `currency` as a sub-parameter in the `line_item` object, you must ensure that the same currency is passed in both places. Know about the [list of supported international currencies.](https://razorpay.com/docs/payments/international-payments#supported-currencies)

**notes** `string`

Any custom notes added to the invoice. Maximum of 2048 characters.

## Response Parameters

**id** `string`

The unique identifier of the invoice.

**entity** `string`

Indicates the type of entity. Here, it is `invoice`.

**type** `string`

Here, it should be `invoice`.

**invoice\_number** `string`

Unique number you added for internal reference. The minimum character length is 1 and maximum is 40.

**customer\_id** `string`

The unique identifier of the customer. You can create `customer_id` using the [Customers API](https://razorpay.com/docs/api/customers.md). Alternatively, you can pass the customer object described in the below fields.

**customer\_details** `object`

Details of the customer.

**id** `string`

Unique identifier of the customer. For example, `cust_1Aa00000000004`.

**name** `string`

Customer's name. Alphanumeric, with period (.), apostrophe (') and parentheses allowed. The name must be between 3-50 characters in length. For example, `Gaurav Kumar`.

**email** `string`

The customer's email address. A maximum length of 64 characters. For example, `gaurav.kumar@example.com`.

**contact** `string`

The customer's phone number. A maximum length of 15 characters including country code. For example, `+919876543210`.

**billing\_address** `object`

Details of the customer's billing address.

**id** `string`

The unique identifier generated for the customer's billing address.

**type** `string`

The customer address type. Here it is `billing_address`.

**primary** `boolean`

Defines if this is the primary address.

* `true`: It is the customer's primary address.
* `false`: It is not the customer's primary address.

**line1** `string`

The first line of the customer's address.

**line2** `string`

The second line of the customer's address.

**city** `string`

The city.

**zipcode** `string`

The zipcode.

**state** `string`

The state.

**country** `string`

The country.

**shipping\_address** `object`

Details of the customer's shipping address.

**id** `string`

The unique identifier generated for the customer's shipping address.

**type** `string`

The customer address type. Here it is `shipping_address`.

**primary** `boolean`

Defines if this is the primary address.

* `true`: It is the customer's primary address.
* `false`: It is not the customer's primary address.

**line1** `string`

The first line of the customer's address.

**line2** `string`

The second line of the customer's address.

**city** `string`

The city.

**zipcode** `string`

The zipcode.

**state** `string`

The state.

**country** `string`

The country.

**order\_id** `string`

The unique identifier of the order associated with the invoice.

**line\_items** `object`

Details of the line item that is billed in the invoice. Maximum of 50 line items.

**id** `string`

Unique identifier that is generated if a new item has been created while creating the invoice.

**item\_id** `string`

Unique identifier of the item generated using Items API that has been billed in the invoice.

**name** `string`

The item's name.

**description** `string`

A brief description of the item.

**amount** `integer`

The price of the item.

**currency** `string`

The currency associated with the item. Default is `INR`. Know about the [list of supported international currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).

**type** `string`

Here, it is `invoice`.

**quantity** `integer`

The quantity of the item billed in the invoice. Defaults to `1`.

**payment\_id** `string`

Unique identifier of a payment made against this invoice.

**status** `string`

The status of the invoice. Know more about [Invoice States](https://razorpay.com/docs/payments/invoices/states.md). Possible values:

* `draft`
* `issued`
* `partially_paid`
* `paid`
* `cancelled`
* `expired`
* `deleted`

**expire\_by** `integer`

Timestamp, in Unix format, at which the invoice will expire.

**issued\_at** `integer`

Timestamp, in Unix format, at which the invoice was issued to the customer.

**paid\_at** `integer`

Timestamp, in Unix format, at which the payment was made.

**cancelled\_at** `integer`

Timestamp, in Unix format, at which the invoice was cancelled.

**expired\_at** `integer`

Timestamp, in Unix format, at which the invoice expired.

**sms\_status** `string`

The delivery status of the SMS notification for the invoice sent to the customer. Possible values:

* `pending`
* `sent`

**email\_status** `string`

The delivery status of the email notification for the invoice sent to the customer. Possible values:

* `pending`
* `sent`

**partial\_payment** `boolean`

Indicates whether the customer can make a partial payment on the invoice. Possible values:

* `true`:  The customer can make partial payments.
* `false` (default): The customer cannot make partial payments.

**amount** `integer`

Amount to be paid using the invoice. Must be in the smallest unit of the currency. For example, if the amount to be received from the customer is , pass the value as `30000`.

**amount\_paid** `integer`

Amount paid by the customer against the invoice.

**amount\_due** `integer`

The remaining amount to be paid by the customer for the issued invoice.

**currency** `string`

The currency associated with the invoice. You must mandatorily pass this parameter if accepting international payments. If you have passed `currency` as a sub-parameter in the `line_item` object, you must ensure that the same currency is passed in both places. Know about the [list of supported international currencies.](https://razorpay.com/docs/payments/international-payments#supported-currencies)

**description** `string`

A brief description of the invoice. The maximum character length is 2048.

**notes** `object`

Any custom notes added to the invoice. Maximum of 2048 characters.

**short\_url** `string`

The short URL that is generated. Share this link with customers to accept payments.

**date** `integer`

Timestamp, in Unix format, that indicates the issue date of the invoice.

**terms** `string`

Any terms to be included in the invoice. Maximum of 2048 characters.

**comment** `string`

Any comments to be added in the invoice. Maximum of 2048 characters.

**ref\_num** `string`

A unique reference number for the invoice, used for internal tracking and reconciliation.

**receipt** `string`

A unique receipt number that you can provide for the invoice, for your internal reference.

**currency\_symbol** `string`

For example, `₹`.

**billing\_end** `integer`

Unix timestamp marking the end of the billing period for the invoice.

**gross\_amount** `integer`

The gross amount for this invoice, in the smallest currency unit (paise for INR). For example, `50000`.

**billing\_start** `integer`

Unix timestamp marking the start of the billing period for the invoice.

## Errors

> [accordion] The API `\<key/secret\>
> ` provided is invalid.
>
> **Code:** `4xx`
>
> The API key or secret are not entered or an invalid API key is used.
>
> **Solution:** Use and enter the correct API details while executing the API.

> [accordion] customer is required.
>
> **Code:** `400`
>
> An invoice is issued without adding customer details.
>
> **Solution:** Ensure that the customer details are entered.

> [accordion] the merchant doesn't have international activated.
>
> **Code:** `400`
>
> The line\_items object has an international currency set. For example, USD, is not enabled for your account.
>
> **Solution:** Ensure that your account has international payments enabled.

> [accordion] Currency of all items should be the same as of the invoice.
>
> **Code:** `400`
>
> There is a difference in currency entered between `line_items` and invoice currency.
>
> **Solution:** Ensure that the `line_items` currency matches that of the invoice.

> [accordion] expire\_by should be at least 15 minutes after current time.
>
> **Code:** `400`
>
> The expiry date is before or within 15 minutes of the current time
>
> **Solution:** Ensure that the Expiry date is greater than the (current time + 15 minutes). For example, if the current time is 1 pm, the expiry date must be at least 1.15 pm.

> [accordion] line\_items is required.
>
> **Code:** `400`
>
> A mandatory field is empty.
>
> **Solution:** Ensure that you fill all the mandatory fields.

> [accordion] Not a valid type.
>
> **Code:** `400`
>
> The value passed for `type` is not one of the supported types. The API echoes the rejected value, for example `Not a valid type: invoiceee`.
>
> **Solution:** Use a supported `type` value, for example `invoice`, `ecod` or `link`.

> [accordion] The amount must be at least INR 1.00.
>
> **Code:** `400`
>
> A line-item `amount` is below the per-currency minimum (`100` paise / ₹1.00 for INR). Also returned for zero or negative line-item amounts.
>
> **Solution:** Pass each `line_items[].amount` greater than or equal to the per-currency minimum.

> [accordion] The amount must be an integer.
>
> **Code:** `400`
>
> A non-integer value (for example a decimal like `100.5` or a string like `"abc"`) was passed for a `line_items[].amount`.
>
> **Solution:** Pass `amount` as an integer in currency subunits (paise for INR).

> [accordion] The quantity must be at least 1.
>
> **Code:** `400`
>
> A line-item `quantity` was passed as `0` or a negative value.
>
> **Solution:** Pass `line_items[].quantity` as a positive integer (`1` or higher).

> [accordion] The email must be a valid email address.
>
> **Code:** `400`
>
> The value passed for `customer.email` is not in a valid email format.
>
> **Solution:** Pass `customer.email` as a valid email address.

> [accordion] Contact number contains invalid characters, only digits and + symbol are allowed.
>
> **Code:** `400`
>
> The `customer.contact` value contains characters other than digits and the `+` symbol.
>
> **Solution:** Pass `customer.contact` using only digits and an optional leading `+` for the country code.

> [accordion] The partial payment field must be true or false.
>
> **Code:** `400`
>
> A non-boolean value was passed for `partial_payment`.
>
> **Solution:** Pass `partial_payment` as a boolean (`true` or `false`).

> [accordion] \{any extra field} is/are not required and should not be sent.
>
> **Code:** `400`
>
> The request body contains fields that are not part of the Invoices API schema.
>
> **Solution:** Only include documented fields. Remove any unknown keys from the request body.

> [accordion] Invoices disabled because fee bearer is customer.
>
> **Code:** `400`
>
> Your account has the customer fee bearer model enabled, which is not compatible with invoice creation.
>
> **Solution:** Contact [Razorpay support](https://razorpay.com/support/) to switch the fee-bearer configuration before creating invoices.

> [accordion] Item cannot be used as it is inactive.
>
> **Code:** `400`
>
> A `line_items[].item_id` passed in the request refers to an item that has been marked inactive.
>
> **Solution:** Activate the item via the Update Item API, or use a different active item.

> [accordion] The merchant doesn't have international activated.
>
> **Code:** `400`
>
> The `currency` passed is different from your account's default currency, but international payments are not enabled on your account.
>
> **Solution:** Enable international payments from your Razorpay Dashboard, or use your account's default currency.

> [accordion] Currency is not supported.
>
> **Code:** `400`
>
> The `currency` value is not a recognised ISO-4217 currency code or is outside the list supported by Razorpay.
>
> **Solution:** Use a supported ISO-4217 currency code.

> [accordion] Invoice amount exceeds maximum payment amount allowed.
>
> **Code:** `400`
>
> The total invoice amount (sum of `line_items[].amount * quantity`) exceeds the per-payment maximum configured for your account.
>
> **Solution:** Split the billing into multiple invoices, or contact [Razorpay support](https://razorpay.com/support/) to raise your per-payment limit.

> [accordion] expire\_by should be at least 15 minutes after current time.
>
> **Code:** `400`
>
> The `expire_by` value is in the past or less than 15 minutes from the current server time.
>
> **Solution:** Pass `expire_by` as a Unix-epoch integer at least 15 minutes in the future.

> [accordion] Request failed. Please try after sometime.
>
> **Code:** `429`
>
> You have exceeded the daily rate limit for invoice creation. This per-day rate limit applies to test-mode accounts and unregistered live-mode accounts. In test mode the limit is 300 invoices/day; in live mode for unregistered businesses it is 10,000 invoices/day. Registered live-mode accounts are not subject to this limit.
>
> **Solution:** Wait until the next day for the limit to reset. If you need a higher limit, register your business on the Razorpay Dashboard or contact [Razorpay support](https://razorpay.com/support/).
