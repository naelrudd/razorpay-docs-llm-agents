> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Update a Customer Identifier

> Update a Customer Identifier using the Razorpay API

Available in
🇮🇳 India
🇺🇸 United States

Use this endpoint to update your Customer Identifier. You cannot update the expiry date of a Customer Identifier that has been closed.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X PATCH https://api.razorpay.com/v1/virtual_accounts/va_KFIrkRmd70ylIg
-H 'content-type: application/json'
-d '{
    "close_by": 1981615845,
    "description": "VA creation for Raftar Soft",
    "notes": {
        "project_name": "Banking Software Work"
    }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String virtualId = "va_Di5gbNptcWV8fQ";

JSONObject virtualRequest = new JSONObject();
List<Object> types = new ArrayList<>();
types.add("vpa");
virtualRequest.put("types",types);
JSONObject vpa = new JSONObject();
vpa.put("descriptor","gaurikumari");
virtualRequest.put("vpa",vpa);

VirtualAccount virtualaccount = instance.virtualAccounts.addReceiver(virtualId,virtualRequest);
```

```php PHP theme={null}
$api = new Api('YOUR_KEY_ID, 'YOUR_KEY_SECRET');
$api->virtualAccount->fetch($virtualId)->addReceiver(array('types' => array('vpa'),'vpa' => array('descriptor'=>'gauravkumar')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.virtualAccounts.addReceiver(virtualId,{
  types: [
    "vpa"
  ],
  vpa: {
    descriptor: "gaurikumari"
  }
})
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.virtual_account.add_receiver(virtualId,{
  "types": [
    "vpa"
  ],
  "vpa": {
    "descriptor": "gaurikumari"
  }
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

types := make(map[string]interface{})
types["0"] = "vpa"

data:= map[string]interface{}{
	"types": types,
	"vpa": map[string]interface{}{
	  "descriptor": "gaurikumari",
	},
  }

body, err :=  client.VirtualAccount.AddReceiver("<virtualID>", data, nil)
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String virtualId = "va_Di5gbNptcWV8fQ";

JSONObject virtualRequest = new JSONObject();
List<Object> types = new ArrayList<>();
types.add("vpa");
virtualRequest.put("types",types);
JSONObject vpa = new JSONObject();
vpa.put("descriptor","gaurikumari");
virtualRequest.put("vpa",vpa);

VirtualAccount virtualaccount = instance.virtualAccounts.addReceiver(virtualId,virtualRequest);
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string virtualId = "va_NHjFyJYeqeNsag";

Dictionary<string, object> virtualRequest = new Dictionary<string, object>();
virtualRequest.Add("description", "VA creation for Raftar Soft");
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("project_name", "Banking Software Work");
virtualRequest.Add("notes", notes);

VirtualAccount refund = client.VirtualAccount.Fetch(virtualId).Edit(virtualRequest);
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

virtualId = "va_Di5gbNptcWV8fQ"

para_attr = {
  "types": [
    "vpa"
  ],
  "vpa": {
    "descriptor": "gaurikumari"
  }
}

Razorpay::VirtualAccount.add_receiver(virtualId, para_attr)
```

```bash CLI theme={null}
razorpay smart-collect update va_DlGmm7jInLudH8 \
  --close-by 1769952000
```

```json Success theme={null}
{
  "id": "va_KFIrkRmd70ylIg",
  "name": "Word Express",
  "entity": "virtual_account",
  "status": "active",
  "description": "VA creation for Raftar Soft",
  "amount_expected": null,
  "notes": {
    "project_name": "Banking Software Work"
  },
  "amount_paid": 0,
  "customer_id": "cust_FY61BIF7OVJLRp",
  "receivers": [
    {
      "id": "ba_KFIrkdawCUDC6n",
      "entity": "bank_account",
      "ifsc": "RAZR0000001",
      "bank_name": null,
      "name": "Word Express",
      "notes": [],
      "account_number": "1112220091736494"
    }
  ],
  "close_by": 1981615845,
  "closed_at": null,
  "created_at": 1577969986
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "close by date should be atleast 15 min after current time",
    "source": "NA",
    "step": "NA",
    "reason": "NA",
    "metadata": {}
  }
}
```

## Path Parameters

**id** `string` *required*

The unique identifier of the Customer Identifier which you want to update.

## Request Parameters

**close\_by** `integer`

UNIX timestamp at which the Customer Identifier is scheduled to be automatically closed. The time must be at least 15 minutes after current time. The date range can be set till `2147483647` in UNIX timestamp format (equivalent to Tuesday, January 19, 2038 8:44:07 AM GMT+05:30).

> [!WARNING]
>
> **Watch Out!**
>
> * Any request beyond `2147483647` UNIX timestamp will fail.
> * If a Customer Identifier API is not used for 90 days, it will automatically close even if no `close_by` date has been set.

**description** `string`

A brief description of the Customer Identifier.

**notes** `json object`

Any custom notes you might want to add to the Customer Identifier can be entered here. Refer to the [Notes section](https://razorpay.com/docs/us/api/understand.md#notes) to learn more.

## Response Parameters

**id** `string`

The unique identifier of the Customer Identifier.

**name** `string`

The `merchant billing label` as it appears on the Dashboard.

**entity** `string`

Indicates the type of entity. Here, it is `virtual account`.

**status** `string`

Indicates whether the Customer Identifier is in `active` or `closed` state.

**description** `string`

A brief description about the Customer Identifier.

**amount\_expected** `integer`

The amount expected by the merchant.

**amount\_paid** `integer`

The amount paid by the customer into the Customer Identifier.

**notes** `json object`

Any custom notes you might want to add to the Customer Identifier can be entered here. Know more about [notes](https://razorpay.com/docs/us/api/understand.md#notes).

**customer\_id** `string`

Unique identifier of the customer the Customer Identifier is linked with. Know more about [Customer API](https://razorpay.com/docs/api/customers.md).

**receivers** `json object`

Configuration of desired receivers for the Customer Identifier.

**id** `string`

The unique identifier of the virtual bank account. Sample IDs for:

* Virtual bank account: `ba_Di5gbQsGn0QSz3`
* Virtual UPI ID: `vpa_CkTmLXqVYPkbxx`

**entity** `string`

Name of the entity. Possible values:

* `bank_account`
* `vpa`

**ifsc** `string`

The IFSC for the virtual bank account created. For example, `RAZR0000001`. This parameter appears in the response only when `bank_account` is passed as the receiver `type`.

**bank\_name** `string`

The bank associated with the virtual bank account. For example, `RBL Bank`. This parameter appears in the response only when `bank_account` is passed as the receiver `type`.

**account\_number** `string`

The unique account number provided by the bank. For example, `1112220061746877`. This parameter appears in the response only when `bank_account` is passed as the receiver `type`.

**name** `string`

The `merchant billing label` as it appears on the Dashboard. This parameter appears in the response only when `bank_account` is passed as the receiver `type`.

**notes** `json object`

Any custom notes you might want to add to the virtual bank account can be entered here. Know more about [notes](https://razorpay.com/docs/us/api/understand.md#notes). This parameter appears in the response only when `bank_account` is passed as the receiver `type`.

**close\_by** `integer`

UNIX timestamp at which the Customer Identifier is scheduled to be automatically closed. The time must be at least 15 minutes after current time. The date range can be set till `2147483647` in UNIX timestamp format (equivalent to Tuesday, January 19, 2038 8:44:07 AM GMT+05:30).

* Any request beyond `2147483647` UNIX timestamp will fail.
* A Customer Identifier API that has not been used for 90 days will be automatically closed even if no `close_by` date has been set.

**closed\_at** `integer`

UNIX timestamp at which the Customer Identifier is automatically closed.

**created\_at** `integer`

UNIX timestamp at which the Customer Identifier was created.

## Errors

> [accordion] Customer Identifier cannot be updated
>
> **Code:** `400`
>
> If you have created a Customer Identifier with only a VPA receiver, you cannot replace or update it.
>
> **Solution:** Create a new Customer Identifier with bank account details.

> [accordion] Bank account Receiver already exists
>
> **Code:** `400`
>
> If you have created a Customer Identifier with a receiver, for example, bank account, you cannot add another bank account receiver or replace it.
>
> **Solution:** Create a new Customer Identifier for new banking details of receiver.

> [accordion] close by date should be atleast 15 min after current time
>
> **Code:** `400`
>
> The epoch time passed is less than current time.
>
> **Solution:** Send the correct `close_by` time. And the `close_by` time should be more than 15 minutes from the current time.
