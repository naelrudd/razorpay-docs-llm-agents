> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Customer Identifier With TPV

> Create a Customer Identifier using the Razorpay Smart Collect API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create a Customer Identifier. While sharing the details of CIs (created using RBL bank) with the customers, ensure that the fifth character in the IFSC is number `0` and not the letter O. For example, valid IFSC is `RATN0VAAPIS` and not `RATNOVAAPIS`.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/virtual_accounts \
-H "Content-Type: application/json" \
-d '{
    "receivers": {
        "types": [
            "bank_account"
        ],
        "bank_account":
        {
            "descriptor": "1234567890"
        }

    },
    "allowed_payers": [
      {
        "type": "bank_account",
        "bank_account": {
          "ifsc": "UTIB0000013",
          "account_number": "914010012345679"
        }
      },
      {
        "type": "bank_account",
        "bank_account": {
          "ifsc": "UTIB0000014",
          "account_number": "914010012345680"
        }
      }
    ],
    "description": "Customer Identifier created for Raftar Soft",
    "customer_id": "cust_CaVDm8eDRSXYME",
    "close_by": 1681615838,
    "notes": {
        "project_name": "Banking Software"
    }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject virtualRequest = new JSONObject();
List<Object> types = new ArrayList<>();
JSONObject typesParam = new JSONObject();
types.add("bank_account");
typesParam.put("types",types);
virtualRequest.put("receivers",typesParam);
List<Object> allowedPayer = new ArrayList<>();
JSONObject allowedPayerParams = new JSONObject();
allowedPayerParams.put("type","bank_account");
JSONObject bankAccount = new JSONObject();
bankAccount.put("ifsc","UTIB0000013");
bankAccount.put("account_number","914010012345679");
allowedPayer.add(allowedPayerParams);
allowedPayerParams.put("bank_account",bankAccount);
virtualRequest.put("allowed_payers",allowedPayer);
virtualRequest.put("description","Customer Identifier created for Raftar Soft");
virtualRequest.put("customer_id","cust_JDdNazagOgg9Ig");
virtualRequest.put("close_by",1681615838);
JSONObject notes = new JSONObject();
notes.put("project_name","Banking Software");
virtualRequest.put("notes", notes);

VirtualAccount virtualaccount = instance.virtualAccounts.create(virtualRequest);
```

```php PHP theme={null}
$api = new Api($api_key, $api_secret);

$api->virtualAccount->create(array('receivers' => array('types'=> array('bank_account')),'allowed_payers' => array(array('type'=>'bank_account','bank_account'=>array('ifsc'=>'RATN0VAAPIS','account_number'=>'2223330027558515'))),'description' => 'Customer Identifier created for Raftar Soft','customer_id' => 'cust_HssUOFiOd2b1TJ', 'notes' => array('project_name' => 'Banking Software')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.virtualAccounts.create({
  receivers: {
    types: [
      "bank_account"
    ]
  },
  allowed_payers: [
    {
      type: "bank_account",
      bank_account: {
        ifsc: "RATN0VAAPIS",
        account_number: "2223330027558515"
      }
    }
  ],
  description: "Customer Identifier created for Raftar Soft",
  customer_id: "cust_HssUOFiOd2b1TJ",
  notes: {
    project_name: "Banking Software"
  }
})
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.virtual_account.create({
  "receivers": {
    "types": [
      "bank_account"
    ]
  },
  "allowed_payers": [
    {
      "type": "bank_account",
      "bank_account": {
        "ifsc": "RATN0VAAPIS",
        "account_number": 2223330027558515
      }
    }
  ],
  "description": "Customer Identifier created for Raftar Soft",
  "customer_id": "cust_HssUOFiOd2b1TJ",
  "notes": {
    "project_name": "Banking Software"
  }
})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay::VirtualAccount.create({
  "receivers": {
    "types": [
      "bank_account"
    ]
  },
  "allowed_payers": [
    {
      "type": "bank_account",
      "bank_account": {
        "ifsc": "RATN0VAAPIS",
        "account_number": 2223330027558515
      }
    }
  ],
  "description": "Customer Identifier created for Raftar Soft",
  "customer_id": "cust_HssUOFiOd2b1TJ",
  "notes": {
    "project_name": "Banking Software"
  }
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

types := make(map[string]interface{})
types["0"] = "bank_account"

allowed_payers := make(map[string]interface{})
allowed_payers["0"] = map[string]interface{}{
      "type": "bank_account",
      "bank_account": map[string]interface{}{
        "ifsc": "RATN0VAAPIS",
        "account_number": 2223330099089860,
      },
    }

data:= map[string]interface{}{
  "receivers": map[string]interface{}{
    "types": types,
  },
  "allowed_payers" : allowed_payers,
  "description": "Customer Identifier created for Raftar Soft",
  "customer_id": "cust_CaVDm8eDRSXYME",
  "close_by": 1681615838,
  "notes": map[string]interface{}{
    "project_name": "Banking Software",
  },
}

body, err := client.VirtualAccount.Create(data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]

Dictionary<string, object> virtualRequest = new Dictionary<string, object>();
List<string> types = new List<string>();
Dictionary<string, object> typesParam = new Dictionary<string, object>();
types.Add("bank_account");
typesParam.Add("types", types);
virtualRequest.Add("receivers", typesParam);
List<Dictionary<string, object>> allowedPayer = new List<Dictionary<string, object>>();
Dictionary<string, object> allowedPayerParams = new Dictionary<string, object>();
allowedPayerParams.Add("type", "bank_account");
Dictionary<string, object> bankAccount = new Dictionary<string, object>();
bankAccount.Add("ifsc", "UTIB0000013");
bankAccount.Add("account_number", "914010012345679");
allowedPayer.Add(allowedPayerParams);
allowedPayerParams.Add("bank_account", bankAccount);
virtualRequest.Add("allowed_payers", allowedPayer);
virtualRequest.Add("description", "Virtual Account created for Raftar Soft");
virtualRequest.Add("customer_id", "cust_JDdNazagOgg9Ig");
virtualRequest.Add("close_by", 1681615838);
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("project_name", "Banking Software");
virtualRequest.Add("notes", notes);

VirtualAccount virtualaccount = client.VirtualAccount.Create(virtualRequest);
```

```bash CLI theme={null}
razorpay smart-collect tpv-create \
  --receiver-type bank_account \
  --bank-account-descriptor "ACME Corp" \
  --allowed-payers '[
    {"type":"bank_account","bank_account":{"ifsc":"UTIB0000001","account_number":"9876543210123456"}},
    {"type":"bank_account","bank_account":{"ifsc":"HDFC0000002","account_number":"1234567890123456"}}
  ]'
  --description "TPV collection" \
  --customer-id cust_ABC123
```

```json Success theme={null}
{
  "id":"va_DlGmm7jInLudH9",
  "name":"Acme Corp",
  "entity":"virtual_account",
  "status":"active",
  "description":"Customer Identifier created for Raftar Soft",
  "amount_expected":null,
  "notes":{
    "project_name":"Banking Software"
  },
  "amount_paid":0,
  "customer_id":"cust_CaVDm8eDRSXYME",
  "receivers":[
    {
      "id":"ba_DlGmm9mSj8fjRM",
      "entity":"bank_account",
      "ifsc":"RATN0VAAPIS",
      "bank_name": "RBL Bank",
      "name":"Acme Corp",
      "notes":[],
      "account_number":"2223330099089860"
    }
  ],
  "allowed_payers": [
    {
      "type": "bank_account",
      "id":"ba_DlGmm9mSj8fjRM",
      "bank_account": {
        "ifsc": "UTIB0000013",
        "account_number": "914010012345679"
      }
    },
    {
      "type": "bank_account",
      "id":"ba_Cmtnm5tSj6agUW",
      "bank_account": {
        "ifsc": "UTIB0000014",
        "account_number": "914010012345680"
      }
    }
  ],
  "close_by":1681615838,
  "closed_at":null,
  "created_at":1574837626
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "Account validation is only applicable on bank account as a receiver type",
    "field": "receivers",
    "source": "business",
    "step": "virtual_account_edit",
    "reason": "account_validation_not_supported_on_vpa",
    "metadata": []
  }
}
```

## Request Parameters

**receivers** `json object` *required*

Configuration of desired receivers for the Customer Identifier.

**types** `array`

List of desired receiver types. Possible value is `bank_account`

**bank\_account** `json object` *required*

Descriptor details for the Bank Account. This is to be passed only when `bank_account` is passed as the receiver `types`.

**descriptor** `string`

A unique, numeric / alphanumeric custom descriptor defined by you for the bank account. The maximum length allowed is 10 digits.\\

> [!NOTE]
>
> **Handy Tips**\
> Please reach out to the [support team](https://razorpay.com/support/#request) if you are unable to pass the parameter with `bank_account`.

**allowed\_payers** `array` *required*

Details of customer bank accounts which will be allowed to make payments to your Customer Identifier. The parent parameter under which the customer bank account details must be passed as child parameters. You can add account details of 10 allowed payers for a Customer Identifier. For more details, refer to the [Third Party Validation](https://razorpay.com/docs/payments/smart-collect/third-party-validation.md) section.

**type** `string` *required*

The type of account through which the customer will make the payment. Possible value is `bank_account`.

**bank\_account** `object` *required*

Indicates the bank account details such as `ifsc` and `account_number`.

**ifsc** `string` *required*

The IFSC associated with the bank account through which the customer is expected to make the payment.

**account\_number** `string` *required*

The bank account number through which the customer is expected to make the payment. SBI account numbers can contain zeros preceding actual numbers. You should enter the complete account number, including these zeros, or else the transaction will fail, and the amount will be refunded automatically. For example, if the account number is 00000022234631312, add the complete account number and not just 22234631312.

**description** `string`

A brief description of the Customer Identifier.

**customer\_id** `string`

Unique identifier of the customer to whom the Customer Identifier must be tagged. Refer to the [Customer API](https://razorpay.com/docs/api/customers.md) documentation to learn how to create a customer.

**notes** `json object`

Any custom notes you might want to add to the Customer Identifier can be entered here. Refer to the [Notes section](https://razorpay.com/docs/api/understand.md#notes) to learn more.

**close\_by** `integer`

UNIX timestamp at which the Customer Identifier is scheduled to be automatically closed. For example, `1681615838`. This needs to be passed only if you want the Customer Identifier to be temporary and auto-deleted after a specific usage time.

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

Any custom notes you might want to add to the Customer Identifier can be entered here. Check the [Notes section](https://razorpay.com/docs/api/understand.md#notes) to know more.

**customer\_id** `string`

Unique identifier of the customer the Customer Identifier is linked with. Check the [Customer API](https://razorpay.com/docs/api/customers.md) section to know more.

**receivers** `json object`

Configuration of desired receivers for the Customer Identifier.

**id** `string`

The unique identifier of the Customer Identifier. Sample id for Customer Identifier is `ba_Di5gbQsGn0QSz3`

**entity** `string`

Name of the entity. Possible value is `bank_account`.

**ifsc** `string`

The IFSC for the Customer Identifier created. For example, `RAZR0000001`. This parameter appears in the response only when `bank_account` is passed as the receiver `type`.

**bank\_name** `string`

The bank associated with the Customer Identifier. For example, `RAZR0000001`. This parameter appears in the response only when `bank_account` is passed as the receiver `type`.

**account\_number** `string`

The unique account number provided by the bank. For example, `1112220061746877`. This parameter appears in the response only when `bank_account` is passed as the receiver `type`.

**name** `string`

The `merchant billing label` as it appears on the Dashboard. This parameter appears in the response only when `bank_account` is passed as the receiver `type`.

**notes** `json object`

Any custom notes you might want to add to the Customer Identifier can be entered here. Check the [Notes section](https://razorpay.com/docs/api/understand.md#notes) to know more. This parameter appears in the response only when `bank_account` is passed as the receiver `type`.

**allowed\_payers** `array`

Details of customer bank accounts which will be allowed to make payments to your Customer Identifier. The parent parameter under which the customer bank account details must be passed as child parameters. You can add account details of 10 allowed payers for a Customer Identifier. For more details, refer to the [Third Party Validation](https://razorpay.com/docs/payments/smart-collect/third-party-validation.md) section.

**type** `string`

The type of account through which the customer will make the payment. Possible value is `bank_account`.

**id** `string`

The unique identifier of the `allowed_payers` account.

**bank\_account** `object`

Indicates the bank account details such as `ifsc` and `account_number`.

**ifsc** `string`

The IFSC associated with the bank account through which the customer is expected to make the payment.

**account\_number** `string`

The bank account number through which the customer is expected to make the payment.

**close\_by** `integer`

UNIX timestamp at which the Customer Identifier is scheduled to be automatically closed. This is returned only if the UNIX timestamp was specified during the Customer Identifier creation. There is no expiry time for a Customer Identifier unless specified during creation.

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
> * Occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
> * `customer_id` is not correct.
>
> **Solution:**
>
> * Make sure that the API keys are active and entered correctly. Also, make sure there are no whitespaces before or after the API keys.
> * Make sure that the `customer_id` and the API keys used belong to the same account and same mode, whether test or live respectively.

> [accordion] The `field name` is required
>
> **Code:** `400`
>
> Occurs when a mandatory field is empty.
>
> **Solution:** Make sure that all the mandatory fields are filled.

> [accordion] The id provided does not exist
>
> **Code:** `400`
>
> Occurs when the `customer_id` passed is wrong or does not belong to the identifier associated to the API keys used.
>
> **Solution:** Make sure that the `customer_id` and the API keys used belong to the same identifier and same mode, whether test or live respectively.

> [accordion] only 10 allowed payers can be added
>
> **Code:** `400`
>
> Occurs when more than 10 allowed payers are added in the Dashboard.
>
> **Solution:** When creating the Customer Identifier, allowed payers cannot be more than 10.

> [accordion] Account validation is only applicable on bank account as receiver type.
>
> **Code:** `400`
>
> This error occurs when you try to add an allowed payer account on a Customer Identifier with VPA added as a receiver (with or without a Bank account).
>
> **Solution:** Allowed payers must have bank account details and not VPA.

> [accordion] The bank account IFSC field is required when the bank is present ( in allowed payers)
>
> **Code:** `400`
>
> This error occurs when you do not pass the IFSC code in the request.
>
> **Solution:** Provide IFSC code for the allowed payers bank account.

> [accordion] Invalid IFSC OR IFSC must be 11 Characters
>
> **Code:** `400`
>
> This error occurs when you pass an incorrect IFSC code in the request. An IFSC must be 11 characters.
>
> **Solution:** Pass the correct IFSC code of the allowed payers bank account.
