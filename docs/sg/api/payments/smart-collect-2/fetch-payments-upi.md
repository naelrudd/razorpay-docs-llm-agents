> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Payments Made Using UPI Payment Method

> Fetch Payments made using UPI payment method, using the Razorpay API

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve details of payments made using the UPI payment method.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET \
https://api.razorpay.com/v1/payments/pay_E5YETrWuVgP3fI/upi_transfer \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_CmiztqmYJPtDAu";

Payment payment = instance.payments.fetchupiTransfers(paymentId)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetch($virtualId)->upiTransfer();
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.upi_transfer(paymentId)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.upiTransfer(paymentId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Payment.upiTransfer("<paymentID>", nil, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymend_id = "pay_Di5iqCqA1WEHq6"

Razorpay::Razorpay::Payment.fetch(paymend_id).upiTransfer
```

```bash CLI theme={null}
razorpay smart-collect fetch-upi-payment pay_DlGmm7jInLudH8
```

```json Success theme={null}
{
  "id": "ut_E5YEUKb9yA0YvX",
  "entity": "upi_transfer",
  "amount": 100,
  "payer_vpa": "gauravkumar@exampleupi",
  "payer_bank": "HDFC BANK LTD",
  "payer_account": "50100000000001",
  "payer_ifsc": "HDFC0000004",
  "payment_id": "pay_E5YETrWuVgP3fI",
  "npci_reference_id": "001718859181",
  "virtual_account_id": "va_E5V3Rb3sQaMS5v",
  "virtual_account": {
    "id": "va_E5V3Rb3sQaMS5v",
    "name": "Acme Corp",
    "entity": "virtual_account",
    "status": "active",
    "description": "First Customer Identifier",
    "amount_expected": null,
    "notes": [],
    "amount_paid": 200,
    "customer_id": "cust_9xnHzNGIEY4TAV",
    "receivers": [
      {
        "id": "vpa_E5V3RsO1g4QK7t",
        "entity": "vpa",
        "username": "rpy.payto00000gaurikumari",
        "handle": "icici",
        "address": "rpy.payto00000gaurikumari@icici"
      }
    ],
    "close_by": null,
    "closed_at": null,
    "created_at": 1579254678
  }
}
```

## Path Parameters

**id** `string` *required*

The unique identifier of the payment made to the Customer Identifier.

## Response Parameters

**id** `string`

The unique identifier of the UPI transfer.

**entity** `string`

The name of the entity. Here, it is `upi_transfer`.

**amount** `integer`

The amount paid by the customer.

**payer\_vpa** `string`

The UPI ID of the customer that is used to make the payment.

**payer\_bank** `string`

The name of the customer's bank.

**payer\_account** `string`

The bank account number of the customer that is linked to the UPI ID.

**payer\_ifsc** `string`

The IFSC associated with the bank account.

**payment\_id** `string`

The unique identifier of the payment made by the customer.

**npci\_reference\_id** `string`

The unique reference number provided by NPCI for the payment.

**virtual\_account\_id** `string`

The unique identifier of the Customer Identifier.

**virtual\_account** `object`

Details of the Customer Identifier.

**id** `string`

The unique identifier of the Customer Identifier.

**name** `string`

The `merchant billing label` as it appears on Dashboard.

**entity** `string`

The name of the entity. Here, it is `virtual account`.

**status** `string`

Indicates the status of the Customer Identifier. Possible values are:

* `active`
* `closed`

**description** `string`

A brief description about the Customer Identifier.

**amount\_paid** `integer`

The amount paid by the customer into the Customer Identifier.

**notes** `object`

Any custom notes added during the creation of the Customer Identifier.

**customer\_id** `string`

The unique identifier of the customer the Customer Identifier is linked with. For more details, refer to the [Customers API](https://razorpay.com/docs/sg/api/customers.md).

**receivers** `object`

Configuration of desired receivers for the Customer Identifier.

**id** `string`

The unique identifier of the virtual UPI ID. For example, `vpa_CkTmLXqVYPkbxx`.

**entity** `string`

The name of the entity. Here, it is `vpa`.

**username** `string`

The unique identifier which forms the first half of the virtual UPI ID. For example, `rpy.payto00000gaurikumari`.

**handle** `string`

The bank name that forms the second half of the virtual UPI ID. For example, `icici`.

**address** `string`

The UPI ID that combines the `username` and the `handle` with the `@` symbol. For example, `rpy.payto00000gaurikumari@icici`. This parameter appears in the response only when `vpa` is passed as the receiver `type`.

**close\_by** `integer`

UNIX timestamp at which the Customer Identifier is scheduled to be automatically closed. The time must be at least 15 minutes after current time. The date range can be set till `2147483647` in UNIX timestamp format (equivalent to Tuesday, January 19, 2038 8:44:07 AM GMT+05:30).\\

> [!NOTE]
>
> **Handy Tips**\
> Any request beyond `2147483647` UNIX timestamp will fail.

**closed\_at** `integer`

UNIX timestamp at which the Customer Identifier is automatically closed.

**created\_at** `integer`

UNIX timestamp at which the Customer Identifier was created.
