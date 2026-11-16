> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Payments Made Using Bank Transfer

> Fetch Payments made using Bank Transfer payment method.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve details of payments made using the bank transfer method.

If Razorpay does not receive the bank account information of the customer from the remitting bank, the `payer_bank_account` parameter will be set to null.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET \
https://api.razorpay.com/v1/payments/pay_CmiztqmYJPtDAu/bank_transfer \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_CmiztqmYJPtDAu";

Payment payment = instance.payments.fetchBankTransfers(paymentId)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetch($virtualId)->bankTransfer();
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('key_id', 'key_secret')

paymend_id = "pay_Di5iqCqA1WEHq6"

Razorpay::Payment.fetch(paymend_id).bank_transfer
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.bank_transfer(paymentId)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.bankTransfer(paymentId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Payment.BankTransfer("<paymentID>", nil, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymend_id = "pay_Di5iqCqA1WEHq6"

Razorpay::Razorpay::Payment.fetch(paymend_id).bank_transfer
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]

string paymentId = "pay_Z6t7VFTb9xHeOs";

BankTransfer virtualaccount = client.Payment.Fetch(paymentId).BankTransfers();
```

```bash CLI theme={null}
razorpay smart-collect fetch-by-bank-transfer pay_DlGmm7jInLudH8
```

```json Success theme={null}
{
  "id": "bt_Di5iqCElVyRlCb",
  "entity": "bank_transfer",
  "payment_id": "pay_Di5iqCqA1WEHq6",
  "mode": "NEFT",
  "bank_reference": "157414364471",
  "amount": 239000,
  "payer_bank_account": {
    "id": "ba_Di5iqSxtYrTzPU",
    "entity": "bank_account",
    "ifsc": "UTIB0003198",
    "bank_name": "Axis Bank",
    "name": "Acme Corp",
    "notes": [],
    "account_number": "765432123456789"
  },
  "virtual_account_id": "va_Di5gbNptcWV8fQ",
  "virtual_account": {
    "id": "va_Di5gbNptcWV8fQ",
    "name": "Acme Corp",
    "entity": "virtual_account",
    "status": "closed",
    "description": "Customer Identifier created for M/S ABC Exports",
    "amount_expected": 2300,
    "notes": {
      "material": "teakwood"
    },
    "amount_paid": 239000,
    "customer_id": "cust_DOMUFFiGdCaCUJ",
    "receivers": [
      {
        "id": "ba_Di5gbQsGn0QSz3",
        "entity": "bank_account",
        "ifsc": "RATN0VAAPIS",
        "bank_name": "RBL Bank",
        "name": "Acme Corp",
        "notes": [],
        "account_number": "1112220061746877"
      }
    ],
    "close_by": 1574427237,
    "closed_at": 1574164078,
    "created_at": 1574143517
  }
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

The unique identifier of the payment made to the Customer Identifier.

## Response Parameters

**id** `string`

The unique identifier of the bank transfer.

**entity** `string`

The name of the entity. Here, it is `bank_transfer`.

**payment\_id** `string`

The unique identifier of the payment.

**mode** `string`

The mode of bank transfer used. Possible values are:

* `NEFT`
* `RTGS`
* `IMPS`
* `UPI`

**bank\_reference** `string`

Unique reference number provided by the bank for the transaction.

**payer\_bank\_account** `object`

The payer bank account details from which payment is received.

**id** `string`

The unique identifier of the customer's bank account.

**entity** `string`

The name of the entity. Here, it is `bank_account`.

**ifsc** `string`

The IFSC associated with the bank account.

**bank\_name** `string`

The name of the bank in which the customer has an account.

**notes** `object`

Any custom notes added to the Customer Identifier.

**account\_number** `string`

The unique account number of the customer.

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

**amount\_expected** `integer`

The amount expected by the merchant.

**amount\_paid** `integer`

The amount paid by the customer to the Customer Identifier.

**notes** `object`

Any custom notes added during the creation of the Customer Identifier.

**customer\_id** `string`

The unique identifier of the customer the Customer Identifier is linked with. Know more about [Customers API](https://razorpay.com/docs/api/customers.md).

**receivers** `object`

Configuration of desired receivers for the Customer Identifier.

**id** `string`

The unique identifier of the Customer Identifier. For example,  `ba_Di5gbQsGn0QSz3`.

**entity** `string`

The name of the entity. Here, it is `bank_account`.

**ifsc** `string`

The IFSC for the Customer Identifier created. For example, `RATN0VAAPIS`.

**bank\_name** `string`

The bank associated with the Customer Identifier. For example, `RBL`.

**account\_number** `string`

The unique account number provided by the bank. For example, `1112220061746877`.

**name** `string`

The `merchant billing label` as it appears on Dashboard.

**notes** `object`

Any custom notes added during the creation of the Customer Identifier.

**close\_by** `integer`

UNIX timestamp at which the Customer Identifier is scheduled to be automatically closed. The time must be at least 15 minutes after current time. The date range can be set till `2147483647` in UNIX timestamp format (equivalent to Tuesday, January 19, 2038 8:44:07 AM GMT+05:30). Any request beyond `2147483647` UNIX timestamp will fail.

**closed\_at** `integer`

UNIX timestamp at which the Customer Identifier is automatically closed.

**created\_at** `integer`

UNIX timestamp at which the Customer Identifier was created.

## Errors

> [accordion] The API `\<key/secret\>
> ` provided is invalid.
>
> **Code:** `4xx`
>
> Occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the dashboard.
>
> **Solution:** Make sure that the API keys are active and entered correctly. Also, make sure there are no whitespaces before or after the keys.
