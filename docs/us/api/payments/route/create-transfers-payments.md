> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create Transfers From Payments

> Initiate Transfers from captured payments using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create Transfers from captured payments. You can create and capture payments in the regular payments flow using the [Razorpay Checkout](https://razorpay.com/docs/us/payments/payment-gateway/web-integration/standard.md) and [Payment APIs](https://razorpay.com/docs/us/api/payments/capture.md).

You should perform additional steps to disburse payments using Razorpay Route.

1. The customer pays the amount using the standard payment flow.
2. Once the payment is `captured`, you can initiate a transfer to Linked Accounts with a transfer API call. You have to pass the details such as `account_id` and `amount`.

```bash Curl theme={null}
curl -X POST https://api.razorpay.com/v1/payments/pay_E8JR8E0XyjUSZd/transfers \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-H 'content-type: application/json'
-d '{
  "transfers": [
    {
      "account": "acc_IROu8Nod6PXPtZ",
      "amount": 100,
      "currency": "INR",
      "notes": {
        "name": "Gaurav Kumar",
        "roll_no": "IEC2011025"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": true,
      "on_hold_until": 1671222870
    },
    {
      "account": "acc_IRQWUleX4BqvYn",
      "amount": 300,
      "currency": "INR",
      "notes": {
        "name": "Saurav Kumar",
        "roll_no": "IEC2011026"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": false
    }
  ]
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_E8JR8E0XyjUSZd";

JSONObject transferRequest = new JSONObject();
List<Object> transfers = new ArrayList<>();
JSONObject transferParams = new JSONObject();
transferParams.put("account","acc_I0QRP7PpvaHhpB");
transferParams.put("amount",100);
transferParams.put("currency","INR");
JSONObject notes = new JSONObject();
notes.put("name","Gaurav Kumar");
notes.put("roll_no","IEC2011026");
transferParams.put("notes",notes);
List<Object> linkedAccountNotes = new ArrayList<>();
linkedAccountNotes.add("roll_no");
transferParams.put("linked_account_notes",linkedAccountNotes);
transferParams.put("on_hold",true);
transfers.add(transferParams);
transferRequest.put("transfers", transfers);

List<Transfer> transfer = razorpay.payments.transfer(paymentId,transferRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetch($paymentId)->transfer(array('transfers' => array('account'=> $accountId, 'amount'=> '1000', 'currency'=>'INR', 'notes'=> array('name'=>'Gaurav Kumar', 'roll_no'=>'IEC2011025'), 'linked_account_notes'=>array('branch'), 'on_hold'=> true, 'on_hold_until'=>'1671222870')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.transfer(paymentId,{
   "transfers": [
    {
      "account": 'acc_HgzcrXeSLfNP9U',
      "amount": 100,
      "currency": "INR",
      "notes": {
        "name": "Gaurav Kumar",
        "roll_no": "IEC2011025"
      },
      "linked_account_notes": [
        "branch"
      ],
      "on_hold": true,
      "on_hold_until": 1671222870
    }
  ]
 })
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.transfer(paymentId,{
   "transfers": [
    {
      "account": 'acc_HgzcrXeSLfNP9U',
      "amount": 100,
      "currency": "INR",
      "notes": {
        "name": "Gaurav Kumar",
        "roll_no": "IEC2011025"
      },
      "linked_account_notes": [
        "branch"
      ],
      "on_hold": True,
      "on_hold_until": 1671222870
    }
  ]
 })
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymentId = "pay_E8JR8E0XyjUSZd"

para_attr = {
   "transfers": [
    {
      "account": 'acc_HgzcrXeSLfNP9U',
      "amount": 100,
      "currency": "INR",
      "notes": {
        "name": "Gaurav Kumar",
        "roll_no": "IEC2011025"
      },
      "linked_account_notes": [
        "branch"
      ],
      "on_hold": 1,
      "on_hold_until": 1671222870
    }
  ]
 }

Razorpay::Payment.fetch(paymentId).transfer(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "transfers": []interface{}{
    map[string]interface{}{
      "account": "acc_HjVXbtpSCIxENR",
      "amount": 100,
      "currency": "INR",
      "notes": map[string]interface{}{
        "name": "Gaurav Kumar",
        "roll_no": "IEC2011025",
      },
      "linked_account_notes": []string{
        "roll_no",
      },
      "on_hold": true,
      "on_hold_until": 1671222870,
    },
  },
}

body, err := client.Payment.Transfer("<paymentId>", data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]
");

string paymentId = "pay_E8JR8E0XyjUSZd";

Dictionary<string, object> transferRequest = new Dictionary<string, object>();
List<Dictionary<string, object>> transfers = new List<Dictionary<string, object>>();
Dictionary<string, object> transferParams = new Dictionary<string, object>();
transferParams.Add("account", "acc_I0QRP7PpvaHhpB");
transferParams.Add("amount", 100);
transferParams.Add("currency", "INR");
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("name", "Gaurav Kumar");
notes.Add("roll_no", "IEC2011025");
transferParams.Add("notes", notes);
List<string> linkedAccountNotes = new List<string>();
linkedAccountNotes.Add("roll_no");
transferParams.Add("linked_account_notes", linkedAccountNotes);
transferParams.Add("on_hold", true);
transfers.Add(transferParams);
transferRequest.Add("transfers", transfers);

List<Transfer> transfer = client.Payment.Fetch(paymentId).Transfer(transferRequest);
```

```bash CLI theme={null}
razorpay route transfers create-from-payment pay_ABC123 \
  --transfers '[
    {"account":"acc_ABC","amount":10000,"currency":"INR","notes":{"branch":"south"},"linked_account_notes":["branch"]},
    {"account":"acc_XYZ","amount":20000,"currency":"INR","on_hold":true,"on_hold_until":1779376925}
  ]'
```

```bash Curl theme={null}
curl -X POST https://api.razorpay.com/v1/payments/pay_E8JR8E0XyjUSZd/transfers \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-H 'content-type: application/json'
-d '{
  "transfers": [
    {
      "account": "acc_IROu8Nod6PXPtZ",
      "amount": 100,
      "currency": "MYR",
      "notes": {
        "name": "Nur Aisyah",
        "roll_no": "IEC2011025"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": true,
      "on_hold_until": 1671222870
    },
    {
      "account": "acc_IRQWUleX4BqvYn",
      "amount": 300,
      "currency": "MYR",
      "notes": {
        "name": "Siti Aisyah",
        "roll_no": "IEC2011026"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": false
    }
  ]
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_E8JR8E0XyjUSZd";

JSONObject transferRequest = new JSONObject();
List<Object> transfers = new ArrayList<>();
JSONObject transferParams = new JSONObject();
transferParams.put("account","acc_I0QRP7PpvaHhpB");
transferParams.put("amount",100);
transferParams.put("currency","MYR");
JSONObject notes = new JSONObject();
notes.put("name","Nur Aisyah");
notes.put("roll_no","IEC2011026");
transferParams.put("notes",notes);
List<Object> linkedAccountNotes = new ArrayList<>();
linkedAccountNotes.add("roll_no");
transferParams.put("linked_account_notes",linkedAccountNotes);
transferParams.put("on_hold",true);
transfers.add(transferParams);
transferRequest.put("transfers", transfers);

List<Transfer> transfer = razorpay.payments.transfer(paymentId,transferRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetch($paymentId)->transfer(array('transfers' => array('account'=> $accountId, 'amount'=> '100', 'currency'=>'MYR', 'notes'=> array('name'=>'Nur Aisyah', 'roll_no'=>'IEC2011025'), 'linked_account_notes'=>array('branch'), 'on_hold'=> true, 'on_hold_until'=>'1671222870')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.transfer(paymentId,{
   "transfers": [
    {
      "account": 'acc_HgzcrXeSLfNP9U',
      "amount": 100,
      "currency": "MYR",
      "notes": {
        "name": "Nur Aisyah",
        "roll_no": "IEC2011025"
      },
      "linked_account_notes": [
        "branch"
      ],
      "on_hold": true,
      "on_hold_until": 1671222870
    }
  ]
 })
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.fetch({
   "transfers":{
      "amount":100,
      "currency":"MYR",
      "notes":{
         "name":"Nur Aisyah",
         "roll_no":"IEC2011025"
      },
      "linked_account_notes":[
         "branch"
      ],
      "on_hold": True,
      "on_hold_until":1671222870
   }
})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymentId = "pay_E8JR8E0XyjUSZd"

para_attr = {
   "transfers": [
    {
      "account": 'acc_HgzcrXeSLfNP9U',
      "amount": 100,
      "currency": "MYR",
      "notes": {
        "name": "Nur Aisyah",
        "roll_no": "IEC2011025"
      },
      "linked_account_notes": [
        "branch"
      ],
      "on_hold": 1,
      "on_hold_until": 1671222870
    }
  ]
 }

Razorpay::Payment.fetch(paymentId).transfer(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "transfers": []interface{}{
    map[string]interface{}{
      "account": "acc_HjVXbtpSCIxENR",
      "amount": 100,
      "currency": "MYR",
      "notes": map[string]interface{}{
        "name": "Nur Aisyah",
        "roll_no": "IEC2011025",
      },
      "linked_account_notes": []string{
        "roll_no",
      },
      "on_hold": true,
      "on_hold_until": 1671222870,
    },
  },
}

body, err := client.Payment.Transfer("<paymentId>", data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]
");

string paymentId = "pay_E8JR8E0XyjUSZd";

Dictionary<string, object> transferRequest = new Dictionary<string, object>();
List<Dictionary<string, object>> transfers = new List<Dictionary<string, object>>();
Dictionary<string, object> transferParams = new Dictionary<string, object>();
transferParams.Add("account", "acc_I0QRP7PpvaHhpB");
transferParams.Add("amount", 100);
transferParams.Add("currency", "MYR");
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("name", "Nur Aisyah");
notes.Add("roll_no", "IEC2011025");
transferParams.Add("notes", notes);
List<string> linkedAccountNotes = new List<string>();
linkedAccountNotes.Add("roll_no");
transferParams.Add("linked_account_notes", linkedAccountNotes);
transferParams.Add("on_hold", true);
transfers.Add(transferParams);
transferRequest.Add("transfers", transfers);

List<Transfer> transfer = client.Payment.Fetch(paymentId).Transfer(transferRequest);
```

```bash CLI theme={null}
razorpay route transfers create-from-payment pay_ABC123 \
  --transfers '[
    {"account":"acc_ABC","amount":10000,"currency":"INR","notes":{"branch":"south"},"linked_account_notes":["branch"]},
    {"account":"acc_XYZ","amount":20000,"currency":"INR","on_hold":true,"on_hold_until":1779376925}
  ]'
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "trf_JJD535tJtk6Yy0",
      "entity": "transfer",
      "status": "pending",
      "source": "pay_JGmCgTEa9OTQcX",
      "recipient": "acc_IROu8Nod6PXPtZ",
      "amount": 100,
      "currency": "INR",
      "amount_reversed": 0,
      "notes": {
        "name": "Gaurav Kumar",
        "roll_no": "IEC2011025"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": true,
      "on_hold_until": 1671222870,
      "recipient_settlement_id": null,
      "created_at": 1649933574,
      "processed_at": null,
      "error": {
        "code": null,
        "description": null,
        "reason": null,
        "field": null,
        "step": null,
        "id": "trf_JJD535tJtk6Yy0",
        "source": null,
        "metadata": null
      }
    },
    {
      "id": "trf_JJD536GI6wuz3m",
      "entity": "transfer",
      "status": "pending",
      "source": "pay_JGmCgTEa9OTQcX",
      "recipient": "acc_IRQWUleX4BqvYn",
      "amount": 300,
      "currency": "INR",
      "amount_reversed": 0,
      "notes": {
        "name": "Saurav Kumar",
        "roll_no": "IEC2011026"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": false,
      "on_hold_until": null,
      "recipient_settlement_id": null,
      "created_at": 1649933574,
      "processed_at": null,
      "error": {
        "code": null,
        "description": null,
        "reason": null,
        "field": null,
        "step": null,
        "id": "trf_JJD536GI6wuz3m",
        "source": null,
        "metadata": null
      }
    }
  ]
}
```

```json Failure theme={null}
{
   "error":{
      "code":"BAD_REQUEST_ERROR",
      "description":"The api key provided is invalid",
      "source":"NA",
      "step":"NA",
      "reason":"NA",
      "metadata":{

      }
   }
}
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "trf_JJD535tJtk6Yy0",
      "entity": "transfer",
      "status": "pending",
      "source": "pay_JGmCgTEa9OTQcX",
      "recipient": "acc_IROu8Nod6PXPtZ",
      "amount": 100,
      "currency": "MYR",
      "amount_reversed": 0,
      "notes": {
        "name": "Nur Aisyah",
        "roll_no": "IEC2011025"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": true,
      "on_hold_until": 1671222870,
      "recipient_settlement_id": null,
      "created_at": 1649933574,
      "processed_at": null,
      "error": {
        "code": null,
        "description": null,
        "reason": null,
        "field": null,
        "step": null,
        "id": "trf_JJD535tJtk6Yy0",
        "source": null,
        "metadata": null
      }
    },
    {
      "id": "trf_JJD536GI6wuz3m",
      "entity": "transfer",
      "status": "pending",
      "source": "pay_JGmCgTEa9OTQcX",
      "recipient": "acc_IRQWUleX4BqvYn",
      "amount": 300,
      "currency": "MYR",
      "amount_reversed": 0,
      "notes": {
        "name": "Siti Aisyah",
        "roll_no": "IEC2011026"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": false,
      "on_hold_until": null,
      "recipient_settlement_id": null,
      "created_at": 1649933574,
      "processed_at": null,
      "error": {
        "code": null,
        "description": null,
        "reason": null,
        "field": null,
        "step": null,
        "id": "trf_JJD536GI6wuz3m",
        "source": null,
        "metadata": null
      }
    }
  ]
}
```

```json Failure theme={null}
{
   "error":{
      "code":"BAD_REQUEST_ERROR",
      "description":"The api key provided is invalid",
      "source":"NA",
      "step":"NA",
      "reason":"NA",
      "metadata":{

      }
   }
}
```

## Path Parameters

**id** `string` *required*

Unique identifier of the payment on which the transfer must be created.

## Request Parameters

**transfers** `array`

Details regarding the transfer.

**account** `string` *required*

Unique identifier of the Linked Account to which the transfer is to be made.

**amount** `integer` *required*

The amount to be transferred to the Linked Account. For example, for an amount of ₹200.35, the value of this field should be 20035.

**currency** `string` *required*

The currency in which the transfer should be made. We support only `INR` for Route transactions.

**notes** `json object`

Set of key-value pairs that can be associated with an entity.  These pairs can be useful for storing additional information about the entity. A maximum of 15 key-value pairs, each of 256 characters (maximum), are supported. For example, `"region": "south", "city": "Bangalore"`.

**linked\_account\_notes** `array`

List of keys from the `notes` object which needs to be shown to Linked Accounts on their Dashboard. For example, `"region", "city"`. Only the keys will be shown, not values.

**on\_hold** `boolean`

Indicates whether the account settlement for transfer is on hold. Know more about [on hold settlements](https://razorpay.com/docs/payments/route/schedule-settlement.md#settlement-settings-for-linked-accounts). Possible values:

* `true`: Puts the settlement on hold.
* `false`: Releases the settlement.

**on\_hold\_until** `integer`

Timestamp, in Unix, that indicates until when the settlement of the transfer must be put on hold. If no value is passed, the settlement is put on hold indefinitely. We recommend you set the on\_hold\_until value greater than 30 mins from the transfer creation time.

> [!NOTE]
>
> **Handy Tips**
>
> * The settlement schedule defined for the Linked Account takes precedence over the `on_hold` and `on_hold_until` functionality. This means that a defined settlement schedule is the minimum time required for the transfer to be settled.
>
> * Let us take the example of a T+10 settlement schedule:
>
>   * If you create a transfer with `on_hold: true` and then release it on T+7 day, the settlement will only go out on T+10 day.
>   * If you create a transfer with `on_hold: true` and `on_hold_until: 1491567400` (assume the timestamp 1491567400 corresponds to 7 days after transfer), the `on_hold` will change to false on T+7 day. The settlement will only go out on T+10 day.

## Response Parameters

**id** `string`

Unique identifier of the transfer.

**entity** `string`

The name of the entity. Here, it is `transfer`.

**transfer\_status** `string`

The status of the transfer. Possible values are:

* `created`
* `pending`
* `processed`
* `failed`
* `reversed`
* `partially_reversed`

**settlement\_status** `string`

The status of the settlement. Possible values are:

* `pending`
* `on_hold`
* `settled`

**source** `string`

Unique identifier of the transfer source. The source can be a `payment` or an `order`.

**recipient** `string`

Unique identifier of the transfer destination, that is, the Linked Account.

**amount** `integer`

The amount to be transferred to the Linked Account, in paise. For example, for an amount of ₹200.35, the value of this field should be 20035.

**currency** `string`

ISO currency code. We support route transfers only in `INR`.

**amount\_reversed** `integer`

Amount reversed from this transfer for refunds.

**notes** `json object`

Set of key-value pairs that can be associated with an entity. These pairs can be useful for storing additional information about the entity. A maximum of 15 key-value pairs, each of 256 characters (maximum), are supported. For example, `"region": "south", "city": "Bangalore"`.

**error** `string`

Provides error details that may occur during transfers.

**code** `string`

Type of the error.

**description** `string`

Error description.

**field** `string`

Name of the parameter in the API request that caused the error.

**source** `string`

The point of failure in the specific operation. For example, customer, business and so on.

**step** `string`

The stage where the transaction failure occurred. Stages can be different depending on the payment method used to make the transaction.

**id** `string`

Unique identifier of the transfer.

**reason** `string`

The exact error reason. It can be handled programmatically.

**linked\_account\_notes** `array`

List of keys from the `notes` object which needs to be shown to Linked Accounts on their Dashboard. For example, `"region", "city"`. Only the keys will be shown, not values.

**on\_hold** `boolean`

Indicates whether the account settlement for transfer is on hold. Possible values:

* `true`: Puts the settlement on hold.
* `false`: Releases the settlement.

**on\_hold\_until** `integer`

Timestamp, in Unix format, indicates until when the settlement of the transfer must be put on hold. If no value is passed, the settlement is put on hold indefinitely.

**recipient\_settlement\_id** `string`

Unique identifier of the settlement.

**created\_at** `integer`

Timestamp, in Unix, at which the record was created.

## Errors

> [accordion] The api key/secret provided is invalid
>
> **Code:** `4xx`
>
> This error occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
>
> **Solution:** Make sure the API Keys are active and entered correctly. Also, there should not be any whitespaces before or after the keys.

> [accordion] The transfers.0.amount must be at least 100.
>
> **Code:** `400`
>
> This error occurs when the amount is less than the minimum amount. The transaction amount expressed in the currency subunit, such as paise (in INR) should always be greater than or equal to 100.
>
> **Solution:** Make sure the amount is equal to or greater than the minimum amount of ₹100.

> [accordion] The input field is required
>
> **Code:** `400`
>
> This error occurs when a mandatory field is empty.
>
> **Solution:** Make sure to fill in all the mandatory fields.

> [accordion] payment\_id is not a valid id
>
> **Code:** `400`
>
> This error occurs when you pass an invalid `payment_id` in the API endpoint.
>
> **Solution:** Make sure to pass a vaild `payment_id`.

> [accordion] The id provided does not exist
>
> **Code:** `400`
>
> This error occurs when there is a miss-match between the API keys via which the transaction was initiated for that particular `payment_id` and the API keys passed in the API call.
>
> **Solution:** Ensure the API keys via which you have accepted the payment for the `payment_id` passed in the API endpoint matches the API keys passed in the API call.

> [accordion] input is an invalid account\_code.
>
> **Code:** `400`
>
> This error occurs when the `account_code` passed is invalid or does not belong to the requested merchant.
>
> **Solution:** Make sure to pass the valid `account_code`.

> [accordion] Transfer cannot be made due to insufficient balance
>
> **Code:** `400`
>
> This error occurs when the total balance is less than or equal to the transfer amount.
>
> **Solution:** Make sure you have enough balance. You can also [add funds](https://razorpay.com/docs/us/payments/dashboard/account-settings/balances.md#add-funds-to-current-balance) to the account and then try doing the transfer.

> [accordion] The sum of amount requested for transfer is greater than the captured amount
>
> **Code:** `400`
>
> This error occurs when the total transferred amount exceeds the captured payment amount.
>
> **Solution:** Make sure the transfer amount is less than the captured payment.
