> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Update an Invoice

> Update the details of the Invoice using this endpoint.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇺🇸 United States

Use this endpoint to update the details of the invoice.

The following table displays ths updates allowed as per invoice states:

| Status | Parameter Update Allowed |
| - | - |
| Draft | All parameters can be updated including the line items. You can also add new line items. |
| Issued | You can update the following parameters: <ul><li>`partial_payment`</li><li>`receipt`</li><li>`comment`</li><li>`terms`</li><li>`notes`</li><li>`expire_by`</li></ul> |
| Cancelled | Only `notes` can be updated. |
| Expired | Only `notes` can be updated. |
| Partially Paid | Only `notes` can be updated. |
| Paid | Only `notes` can be updated. |

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X PATCH https://api.razorpay.com/v1/invoices/inv_DAtUWmR3Y5Dmxb \
-H 'content-type : application/json'
-d '{
  "line_items": [
    {
      "id": "li_DAweOizsysoJU6",
      "name": "Book / English August - Updated name and quantity",
      "quantity": 1
    },
    {
      "name": "Book / A Wild Sheep Chase",
      "amount": 200,
      "currency": "USD",
      "quantity": 1
    }
  ],
  "notes": {
    "updated-key": "An updated note."
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String invoiceId = "inv_DAtUWmR3Y5Dmxb";

JSONObject invoiceRequest = new JSONObject();
List<Object> lines = new ArrayList<>();
JSONObject lineItems = new JSONObject();
lineItems.put("id","li_DAweOizsysoJU6");
lineItems.put("name","Book / English August - Updated name and quantity");
lineItems.put("quantity",1);
JSONObject lineItems1 = new JSONObject();
lineItems1.put("name","Book / A Wild Sheep Chase");
lineItems1.put("amount","200");
lineItems1.put("currency","USD");
lineItems1.put("quantity",1);
lines.add(lineItems);
lines.add(lineItems1);
invoiceRequest.put("line_items",lines);
JSONObject notes = new JSONObject();
notes.put("updated-key","An updated note.");
invoiceRequest.put("notes", notes);

Invoice invoice = razorpay.invoices.edit(invoiceId,invoiceRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.invoice.edit(invoiceId,{
  "line_items": [
    {
      "id": "li_DAweOizsysoJU6",
      "name": "Book / English August - Updated name and quantity",
      "quantity": 1
    },
    {
      "name": "Book / A Wild Sheep Chase",
      "amount": 200,
      "currency": "USD",
      "quantity": 1
    }
  ],
  "notes": {
    "updated-key": "An updated note."
  }
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

line_items := make(map[string]interface{})
line_items["0"] = map[string]interface{}{
      "id": "li_DAweOizsysoJU6",
      "name": "Book / English August - Updated name and quantity",
      "quantity": 1,
    }

data:= map[string]interface{}{
  "line_items": line_items,
  "notes": map[string]interface{}{
    "updated-key": "An updated note.",
  },
}
body, err := client.Invoice.Invoice.Update("<invoiceId>", data, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

invoiceId = "inv_DAtUWmR3Y5Dmxb"

para_attr = {
  "line_items": [
    {
      "id": "li_DAweOizsysoJU6",
      "name": "Book / English August - Updated name and quantity",
      "quantity": 1
    },
    {
      "name": "Book / A Wild Sheep Chase",
      "amount": 200,
      "currency": "USD",
      "quantity": 1
    }
  ],
  "notes": {
    "updated-key": "An updated note. done"
  }
}

Razorpay::Invoice.edit(invoiceId,para_attr)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->invoice->fetch($invoiceId)->edit(array('line_items' => array(array('id' => 'li_DAweOizsysoJU6','name' => 'Book / English August - Updated name and quantity','quantity' => 1),array('name' => 'Book / A Wild Sheep Chase','amount' => 200,'currency' => 'USD','quantity' => 1)),'notes' => array('updated-key' => 'An updated note.')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.invoices.edit(invoiceId,{
  line_items: [
    {
      id: "li_DAweOizsysoJU6",
      name: "Book / English August - Updated name and quantity",
      quantity: 1
    },
    {
      name: "Book / A Wild Sheep Chase",
      amount: 200,
      currency: "USD",
      quantity: 1
    }
  ],
  notes: {
    "updated-key": "An updated note."
  }
})
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string invoiceId = "inv_Z6t7VFTb9xHeOs";

Dictionary<string, object> invoiceRequest = new Dictionary<string, object>();
List<Dictionary<string, object>> lines = new List<Dictionary<string, object>>();
Dictionary<string, object> lineItems = new Dictionary<string, object>();
lineItems.Add("id", "li_Z6t7VFTb9xHeOs");
lineItems.Add("name", "Book / English August - Updated name and quantity");
lineItems.Add("quantity", 1);
Dictionary<string, object> lineItems1 = new Dictionary<string, object>();
lineItems1.Add("name", "Book / A Wild Sheep Chase");
lineItems1.Add("amount", "200");
lineItems1.Add("currency", "USD");
lineItems1.Add("quantity", 1);
lines.Add(lineItems);
lines.Add(lineItems1);
invoiceRequest.Add("line_items", lines);
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("updated-key", "An updated note.");
invoiceRequest.Add("notes", notes);

Invoice invoice = client.Invoice.Fetch(invoiceId).Edit(invoiceRequest);
```

```bash CLI theme={null}
razorpay invoices update inv_ABC123 \
  --description "Updated description" \
  --expire-by 1776759660 \
  --note key1="Updated note"
```

```json Success theme={null}
{
  "id": "inv_DAtUWmR3Y5Dmxb",
  "entity": "invoice",
  "receipt": "#0961",
  "invoice_number": "#0961",
  "customer_id": "cust_DAtUWmvpktokrT",
  "customer_details": {
    "id": "cust_DAtUWmvpktokrT",
    "name": "<name>",
    "email": "<email>",
    "contact": "<phone>",
    "gstin": null,
    "billing_address": {
      "id": "addr_DAtUWoxgu91obl",
      "type": "billing_address",
      "primary": true,
      "line1": "Bakers Street",
      "line2": "T.P.S Road, Vazira, Borivali",
      "zipcode": "400092",
      "city": "Mumbai",
      "state": "Maharashtra",
      "country": "in"
    },
    "shipping_address": null,
    "customer_name": "<name>",
    "customer_email": "<email>",
    "customer_contact": "<phone>"
  },
  "order_id": null,
  "line_items": [
    {
      "id": "li_DAweOizsysoJU6",
      "item_id": null,
      "name": "Book / English August - Updated name and quantity",
      "description": "150 points in Quidditch",
      "amount": 400,
      "unit_amount": 400,
      "gross_amount": 400,
      "tax_amount": 0,
      "taxable_amount": 400,
      "net_amount": 400,
      "currency": "USD",
      "type": "invoice",
      "tax_inclusive": false,
      "hsn_code": null,
      "sac_code": null,
      "tax_rate": null,
      "unit": null,
      "quantity": 1,
      "taxes": []
    },
    {
      "id": "li_DAwjWQUo07lnjF",
      "item_id": null,
      "name": "Book / A Wild Sheep Chase",
      "description": null,
      "amount": 200,
      "unit_amount": 200,
      "gross_amount": 200,
      "tax_amount": 0,
      "taxable_amount": 200,
      "net_amount": 200,
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
  "status": "draft",
  "expire_by": 1567103399,
  "issued_at": null,
  "paid_at": null,
  "cancelled_at": null,
  "expired_at": null,
  "sms_status": null,
  "email_status": null,
  "date": 1566891149,
  "terms": null,
  "partial_payment": false,
  "gross_amount": 600,
  "tax_amount": 0,
  "taxable_amount": 600,
  "amount": 600,
  "amount_paid": null,
  "amount_due": null,
  "currency": "USD",
  "currency_symbol": "<currency_symbol>",
  "description": "This is a test invoice.",
  "notes": {
    "updated-key": "An updated note."
  },
  "comment": null,
  "short_url": null,
  "view_less": true,
  "billing_start": null,
  "billing_end": null,
  "type": "invoice",
  "group_taxes_discounts": false,
  "created_at": 1566906474,
  "idempotency_key": null
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

The unique identifier of the invoice.

## Request Parameters

**type** `string`

Indicates the type of entity. Here, it is `invoice`.

**description** `string`

A brief description of the invoice.

**draft** `string`

Invoice is created in `draft` state when value is set to `1`.

**customer\_id** `string`

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

Amount to be paid using the invoice. Must be in the smallest unit of the currency. For example, if the amount to be received from the customer is ₹300, pass the value as `30000`. Mandatory if `item_id` is not provided. In the case of three decimal currencies, such as KWD, BHD and OMR, to refund a payment of 295.991, pass the value as `295990`. And in the case of zero decimal currencies such as JPY, to refund a payment of 295, pass the value as `295`.

> [!WARNING]
>
> **Watch Out!**
>
> As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to refund a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.

**currency** `string`

The currency associated with the item. Defaults to `INR`. Know about the [list of supported international currencies.](https://razorpay.com/docs/payments/international-payments#supported-currencies) This should match invoice currency.

> [!NOTE]
>
> **Handy Tips**
>
> Razorpay has added support for zero decimal currencies, such as JPY, and three decimal currencies, such as KWD, BHD, and OMR, allowing businesses to accept international payments in these currencies. Know more about [Currency Conversion](https://razorpay.com/docs/payments/international-payments/currency-conversion.md) (May 2024).

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

**currency** `string`

The currency associated with the invoice. You must mandatorily pass this parameter if accepting international payments. If you have passed `currency` as a sub-parameter in the `line_item` object, you must ensure that the same currency is passed in both places. Know about the [list of supported international currencies.](https://razorpay.com/docs/payments/international-payments#supported-currencies)

> [!NOTE]
>
> **Handy Tips**
>
> Razorpay has added support for zero decimal currencies, such as JPY, and three decimal currencies, such as KWD, BHD, and OMR, allowing businesses to accept international payments in these currencies. Know more about [Currency Conversion](https://razorpay.com/docs/payments/international-payments/currency-conversion.md) (May 2024).

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

**idempotency\_key** `string`

A unique key used to ensure idempotency of the invoice creation request, preventing duplicate invoices.

**billing\_end** `integer`

Unix timestamp marking the end of the billing period for the invoice.

**gross\_amount** `integer`

The gross amount for this invoice, in the smallest currency unit (paise for INR). For example, `50000`.

**subscription\_id** `string`

Unique identifier of the subscription this invoice was generated for. `null` for one-off invoices.

## Errors

> [accordion] The api key provided is invalid
>
> **Code:** `400`
>
> The API key or secret are not entered or an invalid API key is used.
>
> **Solution:** Use and enter the correct API details while executing the API.

> [accordion] customer, line\_items, sms\_notify, email\_notify, draft, date, currency is/are not required and should not be sent
>
> **Code:** `400`
>
> The mentioned parameters are not required for updating an invoice. The API echoes the rejected field name in the response.
>
> **Solution:** Pass only the required parameters in the Update Invoice API.

> [accordion] The amount field is required when item id is not present.
>
> **Code:** `400`
>
> Only name is entered without item id or amount.
>
> **Solution:** Provide either the item id or the amount with the name.

> [accordion] The name field is required when item id is not present.
>
> **Code:** `400`
>
> Possible reasons:
>
> * Only the amount field is entered without a name or item id.
> * The amount, name or item id are not entered.
>
> **Solution:** Provide the name field of the item when passing the amount.

> [accordion] amount cannot be updated if invoice has line\_items.
>
> **Code:** `400`
>
> The invoice already has one or more `line_items`. Razorpay derives the invoice amount from the line items, so a top-level `amount` cannot be updated independently.
>
> **Solution:** Update the corresponding `line_items[].amount` instead, or remove the line items before changing the invoice amount.
