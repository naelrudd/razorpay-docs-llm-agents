> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch All Invoices of a Subscription

> Fetch all invoices of a Subscription using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve all invoices of a Subscription. The `count` in the response indicates the number of invoices generated for a Subscription.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET https://api.razorpay.com/v1/invoices?subscription_id=sub_00000000000001 \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject params = new JSONObject();
params.put("subscription_id",subscriptionId);

List<Invoice> invoices = razorpay.invoices.fetchAll(params);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->invoice->all(['subscription_id'=>$subscriptionId]);
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.invoices.all({
  'subscription_id':subscriptionId
})
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.invoice.all({'subscription_id': subscriptionId})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {"subscription_id": "sub_00000000000001"}

Razorpay::Invoice.all(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{ "subscription_id": "sub_00000000000001" }
body, err := client.Invoice.All(data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> param = new Dictionary<string, object>();
param.Add("subscription_id", "sub_Z6t7VFTb9xHeOs");

List<Invoice> subscription = client.Invoice.All(param);
```

```bash CLI theme={null}
razorpay subscriptions invoices sub_ABC123 --count 10 --skip 0
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "inv_00000000000003",
      "entity": "invoice",
      "receipt": null,
      "invoice_number": null,
      "customer_id": "cust_00000000000001",
      "customer_details": {
        "id": "cust_00000000000001",
        "name": null,
        "email": "<email>",
        "contact": "<phone>",
        "gstin": null,
        "billing_address": null,
        "shipping_address": null,
        "customer_name": null,
        "customer_email": "<email>",
        "customer_contact": "<phone>"
      },
      "order_id": "order_00000000000002",
      "subscription_id": "sub_00000000000001",
      "line_items": [
        {
          "id": "li_00000000000003",
          "item_id": null,
          "ref_id": null,
          "ref_type": null,
          "name": "Monthly Plan",
          "description": null,
          "amount": 99900,
          "unit_amount": 99900,
          "gross_amount": 99900,
          "tax_amount": 0,
          "taxable_amount": 99900,
          "net_amount": 99900,
          "currency": "SGD",
          "type": "plan",
          "tax_inclusive": false,
          "hsn_code": null,
          "sac_code": null,
          "tax_rate": null,
          "unit": null,
          "quantity": 1,
          "taxes": []
        }
      ],
      "payment_id": "pay_00000000000002",
      "status": "paid",
      "expire_by": null,
      "issued_at": 1593344888,
      "paid_at": 1593344889,
      "cancelled_at": null,
      "expired_at": null,
      "sms_status": null,
      "email_status": null,
      "date": 1593344888,
      "terms": null,
      "partial_payment": false,
      "gross_amount": 99900,
      "tax_amount": 0,
      "taxable_amount": 99900,
      "amount": 99900,
      "amount_paid": 99900,
      "amount_due": 0,
      "currency": "SGD",
      "currency_symbol": "S$",
      "description": null,
      "notes": [],
      "comment": null,
      "short_url": "https://rzp.io/i/Ys4feGqEp",
      "view_less": true,
      "billing_start": 1594405800,
      "billing_end": 1597084200,
      "type": "invoice",
      "group_taxes_discounts": false,
      "created_at": 1593344888,
      "idempotency_key": null
    },
    {
      "id": "inv_00000000000001",
      "entity": "invoice",
      "receipt": null,
      "invoice_number": null,
      "customer_id": "cust_00000000000001",
      "customer_details": {
        "id": "cust_00000000000001",
        "name": null,
        "email": "<email>",
        "contact": "<phone>",
        "gstin": null,
        "billing_address": null,
        "shipping_address": null,
        "customer_name": null,
        "customer_email": "<email>",
        "customer_contact": "<phone>"
      },
      "order_id": "order_00000000000001",
      "subscription_id": "sub_00000000000001",
      "line_items": [
        {
          "id": "li_00000000000001",
          "item_id": null,
          "ref_id": null,
          "ref_type": null,
          "name": "Monthly Plan",
          "description": null,
          "amount": 99900,
          "unit_amount": 99900,
          "gross_amount": 99900,
          "tax_amount": 0,
          "taxable_amount": 99900,
          "net_amount": 99900,
          "currency": "SGD",
          "type": "plan",
          "tax_inclusive": false,
          "hsn_code": null,
          "sac_code": null,
          "tax_rate": null,
          "unit": null,
          "quantity": 1,
          "taxes": []
        },
        {
          "id": "li_00000000000002",
          "item_id": null,
          "ref_id": null,
          "ref_type": null,
          "name": "Delivery charges",
          "description": null,
          "amount": 30000,
          "unit_amount": 30000,
          "gross_amount": 30000,
          "tax_amount": 0,
          "taxable_amount": 30000,
          "net_amount": 30000,
          "currency": "SGD",
          "type": "addon",
          "tax_inclusive": false,
          "hsn_code": null,
          "sac_code": null,
          "tax_rate": null,
          "unit": null,
          "quantity": 1,
          "taxes": []
        }
      ],
      "payment_id": "pay_00000000000001",
      "status": "paid",
      "expire_by": null,
      "issued_at": 1591878130,
      "paid_at": 1591878210,
      "cancelled_at": null,
      "expired_at": null,
      "sms_status": null,
      "email_status": null,
      "date": 1591878130,
      "terms": null,
      "partial_payment": false,
      "gross_amount": 129900,
      "tax_amount": 0,
      "taxable_amount": 129900,
      "amount": 129900,
      "amount_paid": 129900,
      "amount_due": 0,
      "currency": "SGD",
      "currency_symbol": "S$",
      "description": null,
      "notes": [],
      "comment": null,
      "short_url": "https://rzp.io/i/nt5k3df",
      "view_less": true,
      "billing_start": 1591878205,
      "billing_end": 1594405800,
      "type": "invoice",
      "group_taxes_discounts": false,
      "created_at": 1591878130,
      "idempotency_key": null
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

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "inv_00000000000003",
      "entity": "invoice",
      "receipt": null,
      "invoice_number": null,
      "customer_id": "cust_00000000000001",
      "customer_details": {
        "id": "cust_00000000000001",
        "name": null,
        "email": "<email>",
        "contact": "<phone>",
        "gstin": null,
        "billing_address": null,
        "shipping_address": null,
        "customer_name": null,
        "customer_email": "<email>",
        "customer_contact": "<phone>"
      },
      "order_id": "order_00000000000002",
      "subscription_id": "sub_00000000000001",
      "line_items": [
        {
          "id": "li_00000000000003",
          "item_id": null,
          "ref_id": null,
          "ref_type": null,
          "name": "Monthly Plan",
          "description": null,
          "amount": 99900,
          "unit_amount": 99900,
          "gross_amount": 99900,
          "tax_amount": 0,
          "taxable_amount": 99900,
          "net_amount": 99900,
          "currency": "SGD",
          "type": "plan",
          "tax_inclusive": false,
          "hsn_code": null,
          "sac_code": null,
          "tax_rate": null,
          "unit": null,
          "quantity": 1,
          "taxes": []
        }
      ],
      "payment_id": "pay_00000000000002",
      "status": "paid",
      "expire_by": null,
      "issued_at": 1593344888,
      "paid_at": 1593344889,
      "cancelled_at": null,
      "expired_at": null,
      "sms_status": null,
      "email_status": null,
      "date": 1593344888,
      "terms": null,
      "partial_payment": false,
      "gross_amount": 99900,
      "tax_amount": 0,
      "taxable_amount": 99900,
      "amount": 99900,
      "amount_paid": 99900,
      "amount_due": 0,
      "currency": "SGD",
      "currency_symbol": "RM",
      "description": null,
      "notes": [],
      "comment": null,
      "short_url": "https://rzp.io/i/Ys4feGqEp",
      "view_less": true,
      "billing_start": 1594405800,
      "billing_end": 1597084200,
      "type": "invoice",
      "group_taxes_discounts": false,
      "created_at": 1593344888,
      "idempotency_key": null
    },
    {
      "id": "inv_00000000000001",
      "entity": "invoice",
      "receipt": null,
      "invoice_number": null,
      "customer_id": "cust_00000000000001",
      "customer_details": {
        "id": "cust_00000000000001",
        "name": null,
        "email": "<email>",
        "contact": "<phone>",
        "gstin": null,
        "billing_address": null,
        "shipping_address": null,
        "customer_name": null,
        "customer_email": "<email>",
        "customer_contact": "<phone>"
      },
      "order_id": "order_00000000000001",
      "subscription_id": "sub_00000000000001",
      "line_items": [
        {
          "id": "li_00000000000001",
          "item_id": null,
          "ref_id": null,
          "ref_type": null,
          "name": "Monthly Plan",
          "description": null,
          "amount": 99900,
          "unit_amount": 99900,
          "gross_amount": 99900,
          "tax_amount": 0,
          "taxable_amount": 99900,
          "net_amount": 99900,
          "currency": "SGD",
          "type": "plan",
          "tax_inclusive": false,
          "hsn_code": null,
          "sac_code": null,
          "tax_rate": null,
          "unit": null,
          "quantity": 1,
          "taxes": []
        },
        {
          "id": "li_00000000000002",
          "item_id": null,
          "ref_id": null,
          "ref_type": null,
          "name": "Delivery charges",
          "description": null,
          "amount": 30000,
          "unit_amount": 30000,
          "gross_amount": 30000,
          "tax_amount": 0,
          "taxable_amount": 30000,
          "net_amount": 30000,
          "currency": "SGD",
          "type": "addon",
          "tax_inclusive": false,
          "hsn_code": null,
          "sac_code": null,
          "tax_rate": null,
          "unit": null,
          "quantity": 1,
          "taxes": []
        }
      ],
      "payment_id": "pay_00000000000001",
      "status": "paid",
      "expire_by": null,
      "issued_at": 1591878130,
      "paid_at": 1591878210,
      "cancelled_at": null,
      "expired_at": null,
      "sms_status": null,
      "email_status": null,
      "date": 1591878130,
      "terms": null,
      "partial_payment": false,
      "gross_amount": 129900,
      "tax_amount": 0,
      "taxable_amount": 129900,
      "amount": 129900,
      "amount_paid": 129900,
      "amount_due": 0,
      "currency": "SGD",
      "currency_symbol": "RM",
      "description": null,
      "notes": [],
      "comment": null,
      "short_url": "https://rzp.io/i/nt5k3df",
      "view_less": true,
      "billing_start": 1591878205,
      "billing_end": 1594405800,
      "type": "invoice",
      "group_taxes_discounts": false,
      "created_at": 1591878130,
      "idempotency_key": null
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

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "inv_00000000000003",
      "entity": "invoice",
      "receipt": null,
      "invoice_number": null,
      "customer_id": "cust_00000000000001",
      "customer_details": {
        "id": "cust_00000000000001",
        "name": null,
        "email": "<email>",
        "contact": "<phone>",
        "gstin": null,
        "billing_address": null,
        "shipping_address": null,
        "customer_name": null,
        "customer_email": "<email>",
        "customer_contact": "<phone>"
      },
      "order_id": "order_00000000000002",
      "subscription_id": "sub_00000000000001",
      "line_items": [
        {
          "id": "li_00000000000003",
          "item_id": null,
          "ref_id": null,
          "ref_type": null,
          "name": "Monthly Plan",
          "description": null,
          "amount": 99900,
          "unit_amount": 99900,
          "gross_amount": 99900,
          "tax_amount": 0,
          "taxable_amount": 99900,
          "net_amount": 99900,
          "currency": "SGD",
          "type": "plan",
          "tax_inclusive": false,
          "hsn_code": null,
          "sac_code": null,
          "tax_rate": null,
          "unit": null,
          "quantity": 1,
          "taxes": []
        }
      ],
      "payment_id": "pay_00000000000002",
      "status": "paid",
      "expire_by": null,
      "issued_at": 1593344888,
      "paid_at": 1593344889,
      "cancelled_at": null,
      "expired_at": null,
      "sms_status": null,
      "email_status": null,
      "date": 1593344888,
      "terms": null,
      "partial_payment": false,
      "gross_amount": 99900,
      "tax_amount": 0,
      "taxable_amount": 99900,
      "amount": 99900,
      "amount_paid": 99900,
      "amount_due": 0,
      "currency": "SGD",
      "currency_symbol": "$",
      "description": null,
      "notes": [],
      "comment": null,
      "short_url": "https://rzp.io/i/Ys4feGqEp",
      "view_less": true,
      "billing_start": 1594405800,
      "billing_end": 1597084200,
      "type": "invoice",
      "group_taxes_discounts": false,
      "created_at": 1593344888,
      "idempotency_key": null
    },
    {
      "id": "inv_00000000000001",
      "entity": "invoice",
      "receipt": null,
      "invoice_number": null,
      "customer_id": "cust_00000000000001",
      "customer_details": {
        "id": "cust_00000000000001",
        "name": null,
        "email": "<email>",
        "contact": "<phone>",
        "gstin": null,
        "billing_address": null,
        "shipping_address": null,
        "customer_name": null,
        "customer_email": "<email>",
        "customer_contact": "<phone>"
      },
      "order_id": "order_00000000000001",
      "subscription_id": "sub_00000000000001",
      "line_items": [
        {
          "id": "li_00000000000001",
          "item_id": null,
          "ref_id": null,
          "ref_type": null,
          "name": "Monthly Plan",
          "description": null,
          "amount": 99900,
          "unit_amount": 99900,
          "gross_amount": 99900,
          "tax_amount": 0,
          "taxable_amount": 99900,
          "net_amount": 99900,
          "currency": "SGD",
          "type": "plan",
          "tax_inclusive": false,
          "hsn_code": null,
          "sac_code": null,
          "tax_rate": null,
          "unit": null,
          "quantity": 1,
          "taxes": []
        },
        {
          "id": "li_00000000000002",
          "item_id": null,
          "ref_id": null,
          "ref_type": null,
          "name": "Delivery charges",
          "description": null,
          "amount": 30000,
          "unit_amount": 30000,
          "gross_amount": 30000,
          "tax_amount": 0,
          "taxable_amount": 30000,
          "net_amount": 30000,
          "currency": "SGD",
          "type": "addon",
          "tax_inclusive": false,
          "hsn_code": null,
          "sac_code": null,
          "tax_rate": null,
          "unit": null,
          "quantity": 1,
          "taxes": []
        }
      ],
      "payment_id": "pay_00000000000001",
      "status": "paid",
      "expire_by": null,
      "issued_at": 1591878130,
      "paid_at": 1591878210,
      "cancelled_at": null,
      "expired_at": null,
      "sms_status": null,
      "email_status": null,
      "date": 1591878130,
      "terms": null,
      "partial_payment": false,
      "gross_amount": 129900,
      "tax_amount": 0,
      "taxable_amount": 129900,
      "amount": 129900,
      "amount_paid": 129900,
      "amount_due": 0,
      "currency": "USD",
      "currency_symbol": "$",
      "description": null,
      "notes": [],
      "comment": null,
      "short_url": "https://rzp.io/i/nt5k3df",
      "view_less": true,
      "billing_start": 1591878205,
      "billing_end": 1594405800,
      "type": "invoice",
      "group_taxes_discounts": false,
      "created_at": 1591878130,
      "idempotency_key": null
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

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "inv_00000000000003",
      "entity": "invoice",
      "receipt": null,
      "invoice_number": null,
      "customer_id": "cust_00000000000001",
      "customer_details": {
        "id": "cust_00000000000001",
        "name": null,
        "email": "<email>",
        "contact": "<phone>",
        "gstin": null,
        "billing_address": null,
        "shipping_address": null,
        "customer_name": null,
        "customer_email": "<email>",
        "customer_contact": "<phone>"
      },
      "order_id": "order_00000000000002",
      "subscription_id": "sub_00000000000001",
      "line_items": [
        {
          "id": "li_00000000000003",
          "item_id": null,
          "ref_id": null,
          "ref_type": null,
          "name": "Monthly Plan",
          "description": null,
          "amount": 99900,
          "unit_amount": 99900,
          "gross_amount": 99900,
          "tax_amount": 0,
          "taxable_amount": 99900,
          "net_amount": 99900,
          "currency": "SGD",
          "type": "plan",
          "tax_inclusive": false,
          "hsn_code": null,
          "sac_code": null,
          "tax_rate": null,
          "unit": null,
          "quantity": 1,
          "taxes": []
        }
      ],
      "payment_id": "pay_00000000000002",
      "status": "paid",
      "expire_by": null,
      "issued_at": 1593344888,
      "paid_at": 1593344889,
      "cancelled_at": null,
      "expired_at": null,
      "sms_status": null,
      "email_status": null,
      "date": 1593344888,
      "terms": null,
      "partial_payment": false,
      "gross_amount": 99900,
      "tax_amount": 0,
      "taxable_amount": 99900,
      "amount": 99900,
      "amount_paid": 99900,
      "amount_due": 0,
      "currency": "SGD",
      "currency_symbol": "S$",
      "description": null,
      "notes": [],
      "comment": null,
      "short_url": "https://rzp.io/i/Ys4feGqEp",
      "view_less": true,
      "billing_start": 1594405800,
      "billing_end": 1597084200,
      "type": "invoice",
      "group_taxes_discounts": false,
      "created_at": 1593344888,
      "idempotency_key": null
    },
    {
      "id": "inv_00000000000001",
      "entity": "invoice",
      "receipt": null,
      "invoice_number": null,
      "customer_id": "cust_00000000000001",
      "customer_details": {
        "id": "cust_00000000000001",
        "name": null,
        "email": "<email>",
        "contact": "<phone>",
        "gstin": null,
        "billing_address": null,
        "shipping_address": null,
        "customer_name": null,
        "customer_email": "<email>",
        "customer_contact": "<phone>"
      },
      "order_id": "order_00000000000001",
      "subscription_id": "sub_00000000000001",
      "line_items": [
        {
          "id": "li_00000000000001",
          "item_id": null,
          "ref_id": null,
          "ref_type": null,
          "name": "Monthly Plan",
          "description": null,
          "amount": 99900,
          "unit_amount": 99900,
          "gross_amount": 99900,
          "tax_amount": 0,
          "taxable_amount": 99900,
          "net_amount": 99900,
          "currency": "SGD",
          "type": "plan",
          "tax_inclusive": false,
          "hsn_code": null,
          "sac_code": null,
          "tax_rate": null,
          "unit": null,
          "quantity": 1,
          "taxes": []
        },
        {
          "id": "li_00000000000002",
          "item_id": null,
          "ref_id": null,
          "ref_type": null,
          "name": "Delivery charges",
          "description": null,
          "amount": 30000,
          "unit_amount": 30000,
          "gross_amount": 30000,
          "tax_amount": 0,
          "taxable_amount": 30000,
          "net_amount": 30000,
          "currency": "SGD",
          "type": "addon",
          "tax_inclusive": false,
          "hsn_code": null,
          "sac_code": null,
          "tax_rate": null,
          "unit": null,
          "quantity": 1,
          "taxes": []
        }
      ],
      "payment_id": "pay_00000000000001",
      "status": "paid",
      "expire_by": null,
      "issued_at": 1591878130,
      "paid_at": 1591878210,
      "cancelled_at": null,
      "expired_at": null,
      "sms_status": null,
      "email_status": null,
      "date": 1591878130,
      "terms": null,
      "partial_payment": false,
      "gross_amount": 129900,
      "tax_amount": 0,
      "taxable_amount": 129900,
      "amount": 129900,
      "amount_paid": 129900,
      "amount_due": 0,
      "currency": "SGD",
      "currency_symbol": "S$",
      "description": null,
      "notes": [],
      "comment": null,
      "short_url": "https://rzp.io/i/nt5k3df",
      "view_less": true,
      "billing_start": 1591878205,
      "billing_end": 1594405800,
      "type": "invoice",
      "group_taxes_discounts": false,
      "created_at": 1591878130,
      "idempotency_key": null
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

**subscription\_id** `string` *required*

The unique identifier linked to the Subscription. For example, `sub_00000000000001`.

## Response Parameters

**count** `integer`

The number of invoices generated for the Subscription.

**item** `array`

List of invoices generated for the Subscription.

**id** `string`

The unique identifier of the invoice issued for the Subscription.

**entity** `string`

The entity being created. Here, it is `invoice`.

**receipt** `string`

Here, it is `null`.

**invoice\_number** `string`

The invoice number. Here, it is `null`.

**customer\_id** `string`

The unique identifier of the customer linked to the Subscription.

**customer\_details** `object`

Details of the customer.

**id** `string`

The unique identifier of the customer linked to the Subscription.

**name** `string`

The customer's name. Know more [Customers API](https://razorpay.com/docs/sg/api/customers.md).

**email** `string`

The customer's email address.

**contact** `string`

The customer's contact number.

**billing\_address** `string`

The customer's billing address.

**shipping\_address** `string`

The customer's shipping address.

**customer\_name** `string`

The customer's name.

**customer\_email** `string`

The customer's email address.

**customer\_contact** `string`

The customer's contact number.

**order\_id** `string`

The unique identifier of the order associated with the invoice.

**subscription\_id** `string`

The unique identifier of the Subscription. For example, `sub_00000000000001`.

**line\_items** `array`

Details of the line item that is billed in the invoice. Number of arrays = number of line items billed in the invoice. For example, if the Subscription starts immediately and has an upfront fee attached to it, the number of line items = 2. One for the Subscription charge and one for the upfront fee.

**id** `string`

The unique identifier linked to the item billed in the invoice. For example, `li_00000000000001`.

**item\_id** `string`

Here, it is `null`.

**name** `string`

The item's name. For example, `Monthly Plan`.

**description** `string`

A brief description of the item. Here, it is `null`.

**amount** `integer`

The item's price, in currency subunits. For example, `99900`.

**currency** `string`

The currency for the amount charged for the item.

**type** `string`

The type of charge. Possible values:

* `plan`
* `addon`

**quantity** `integer`

The number of units of the item billed in the invoice. For example, `1`.

**payment\_id** `string`

Unique identifier of the payment made by the customer using this invoice. For example, `pay_00000000000001`.

**status** `string`

The status of the invoice. Possible values:

* `draft`
* `issued`
* `partially_paid`
* `paid`
* `expired`
* `cancelled`
* `deleted`

**expire\_by** `integer`

The Unix timestamp, indicates at which the invoice will expire. For example, `1593411509`

**issued\_at** `integer`

The Unix timestamp, indicates at which the invoice was issued to the customer. For example, `1593411209`

**paid\_at** `integer`

The Unix timestamp, indicates at which the payment was made. For example, `1593411325`

**cancelled\_at** `integer`

The Unix timestamp, indicates at which the invoice was canceled by you. For example, `1593411209`

**expired\_at** `integer`

The Unix timestamp, indicates at which the invoice has expired. For example, `1593411209`

**sms\_status** `string`

Indicates whether the SMS notification for the invoice was sent to the customer. Possible values:

* `pending`
* `sent`

**email\_status** `string`

Indicates whether the email notification for the invoice was sent to the customer. Possible values:

* `pending`
* `sent`

**date** `integer`

The Unix timestamp, that indicates the date of the invoice.

**terms** `string`

Any terms to be included in the invoice. Here, it is `null`.

**partial\_payment** `boolean`

Indicates whether the customer can make a partial payment on the invoice.

* `true`: Customer can make partial payments.
* `false`: Customer cannot make partial payments.

**amount** `integer`

Amount to be paid using the invoice. This should be in the smallest unit of the currency. For example, `29995`.

**amount\_paid** `integer`

Amount paid by the customer using the invoice. For example, `29995`.

**amount\_due** `integer`

The remaining amount to be paid by the customer for the issued invoice.

**currency** `string`

The currency associated with the item.

**description** `string`

A brief description of the invoice. Here, it is `null`.

**notes** `object`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

**comment** `string`

Any comments to be added in the invoice. Here, it is `null`.

**short\_url** `string`

The short URL that is generated. This is the link that can be shared with customers to accept payments. Once canceled, no payments can be accepted using the link. For example, `https://rzp.io/i/gb5827Hh`.

**view\_less** `boolean`

Used when the link description is lengthy and you want to make the text collapsible. The text can be expanded by the customer using the **Show More** link.

* `true` (default): Link description appears collapsed, with a **Show More** link.
* `false`: Link description appears expanded.

**type** `string`

Here, it is `invoice`.

**created\_at** `integer`

The Unix timestamp, that indicates when this invoice entity was created. For example, `1593411943`.

## Errors

> [accordion] The API key/secret provided is invalid.
>
> **Code:** `4xx`
>
> This error occurs due to a mismatch between the API credentials passed in the API call and those generated on the Dashboard.
>
> **Solution:** Ensure that the API keys are active and correctly entered, with no whitespaces before or after the keys.

> [accordion] The subscription id must be at least 14 characters.
>
> **Code:** `400`
>
> The `subscription_id` query parameter is malformed (shorter than the expected `sub_<14 alphanumeric chars>` format).
>
> **Solution:** Pass `subscription_id` as a well-formed subscription id (`sub_<14 alphanumeric chars>`).
