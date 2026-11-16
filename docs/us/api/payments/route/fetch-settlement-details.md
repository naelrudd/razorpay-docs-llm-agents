> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Settlement Details

> Fetch settlement details using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to fetch details of settlements made to Linked Accounts. You should append `?expand[]=recipient_settlement` as the query parameter to the fetch transfer request. This would return a `settlement` entity and the `transfer` entity.

```bash Curl theme={null}
curl -X GET https://api.razorpay.com/v1/transfers?expand[]=recipient_settlement \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \ 
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject params = new JSONObject();
params.put("expand[]","recipient_settlement");

List<Transfer> transfer = razorpay.transfers.fetchAll(params);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->transfer->all(array('expand[]'=> 'recipient_settlement'));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.transfers.all({
  expand[] = 'recipient_settlement'  
})
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.transfer.all({
   "expand[]":"recipient_settlement"
})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay::Transfer.fetch_settlements
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "expand[]": "recipient_settlement",
}
body, err := client.Transfer.All(data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]
");

Dictionary<string, object> transferRequest = new Dictionary<string, object>();
transferRequest.Add("expand[]", "recipient_settlement");

List<Transfer> transfer = client.Transfer.All(transferRequest);
```

```bash CLI theme={null}
razorpay route transfers list --expand recipient_settlement
```

```json Success theme={null}
{
   "entity":"collection",
   "count":2,
   "items":[
      {
         "id":"trf_LQzChWyKaanhLt",
         "entity":"transfer",
         "status":"processed",
         "source":"pay_LObWTFZaMBE09S",
         "recipient":"acc_LQDB1eV0EnS808",
         "account_code":"sartest",
         "amount":200,
         "currency":"INR",
         "amount_reversed":0,
         "fees":0,
         "tax":0,
         "notes":[

         ],
         "linked_account_notes":[

         ],
         "on_hold":false,
         "on_hold_until":null,
         "settlement_status":"settled",
         "recipient_settlement_id":"setl_LRfWxcxaJyXwde",
         "recipient_settlement":{
            "id":"setl_LRfWxcxaJyXwde",
            "entity":"settlement",
            "amount":200,
            "status":"processed",
            "fees":0,
            "tax":0,
            "utr":"cg8kkuoffu3jpb4k8hgg",
            "created_at":1678854659
         },
         "created_at":1678705600,
         "processed_at":1678705601,
         "error":{
            "code":null,
            "description":null,
            "reason":null,
            "field":null,
            "step":null,
            "id":"trf_LQzChWyKaanhLt",
            "source":null,
            "metadata":null
         },
         "source_channel":"online"
      },
      {
         "id":"trf_Ks9IagO4T2wZ5l",
         "entity":"transfer",
         "status":"processed",
         "source":"pay_Ks9IUPU43z3FRz",
         "recipient":"acc_H9sehmPXd5nd2n",
         "account_code":"Palguna_test",
         "amount":100000,
         "currency":"INR",
         "amount_reversed":0,
         "fees":0,
         "tax":0,
         "notes":[

         ],
         "linked_account_notes":[

         ],
         "on_hold":false,
         "on_hold_until":null,
         "settlement_status":"settled",
         "recipient_settlement_id":"setl_KstcJycgGX6lRa",
         "recipient_settlement":{
            "id":"setl_KstcJycgGX6lRa",
            "entity":"settlement",
            "amount":200000,
            "status":"processed",
            "fees":0,
            "tax":0,
            "utr":"ceen24sa13gn9rr3uij0",
            "created_at":1671262362
         },
         "created_at":1671099247,
         "processed_at":1671099247,
         "error":{
            "code":null,
            "description":null,
            "reason":null,
            "field":null,
            "step":null,
            "id":"trf_Ks9IagO4T2wZ5l",
            "source":null,
            "metadata":null
         },
         "source_channel":"online"
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
      "id": "trf_JCu3ZstilY6Whi",
      "entity": "transfer",
      "status": "failed",
      "source": "pay_HWjY9DZSMsbm5E",
      "recipient": "acc_CNo3jSI8OkFJJJ",
      "amount": 100,
      "currency": "MYR",
      "amount_reversed": 0,
      "fees": 0,
      "tax": null,
      "notes": {
        "name": "Nur Aisyah",
        "roll_no": "IEC2011026"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": false,
      "on_hold_until": null,
      "settlement_status": null,
      "recipient_settlement_id": null,
      "recipient_settlement": null,
      "created_at": 1648556539,
      "processed_at": 1648556543,
      "error": {
        "code": "BAD_REQUEST_TRANSFER_INSUFFICIENT_BALANCE",
        "description": "Account does not have sufficient balance to carry out transfer operation",
        "reason": "insufficient_account_balance",
        "field": "amount",
        "step": "transfer_processing",
        "id": "trf_JCu3ZstilY6Whi",
        "source": null,
        "metadata": null
      }
    },
    {
      "id": "trf_JCu3ZsTVSuy7oN",
      "entity": "transfer",
      "status": "failed",
      "source": "pay_HWjY9DZSMsbm5E",
      "recipient": "acc_CPRsN1LkFccllA",
      "amount": 100,
      "currency": "MYR",
      "amount_reversed": 0,
      "fees": 0,
      "tax": null,
      "notes": {
        "name": "Siti Aisyah",
        "roll_no": "IEC2011025"
      },
      "linked_account_notes": [
        "roll_no"
      ],
      "on_hold": true,
      "on_hold_until": 1671222870,
      "settlement_status": null,
      "recipient_settlement_id": null,
      "recipient_settlement": null,
      "created_at": 1648556539,
      "processed_at": 1648556543,
      "error": {
        "code": "BAD_REQUEST_TRANSFER_INSUFFICIENT_BALANCE",
        "description": "Account does not have sufficient balance to carry out transfer operation",
        "reason": "insufficient_account_balance",
        "field": "amount",
        "step": "transfer_processing",
        "id": "trf_JCu3ZsTVSuy7oN",
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

## Query Parameters

**expand** `string` *required*

Used to retrieve settlement entity along with transfer entity. Supported value is `recipient_settlement`.

**transfer\_type** `string`

Applicable only if you are a Razorpay Partner. Controls which transfers are returned based on the destination account and partner configuration. Possible values are:

* `platform`: Returns transfers excluding those sent to the partner's own Linked Accounts.
* `regular` (or when the parameter is omitted): The behaviour depends on the partner's `route_partnerships` feature setting:
  * If `route_partnerships` is enabled: Returns transfers sent to the partner's own Linked Accounts.
  * If `route_partnerships` is disabled: Returns all regular transfers associated with the Partner account.

Descriptions for the optional query parameters are present in the [Pagination & Rate Limiting](https://razorpay.com/docs/us/api/understand.md#pagination) documentation.

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

Set of key-value pairs that can be associated with an entity.  This can be useful for storing additional information about the entity. A maximum of 15 key-value pairs, each of 256 characters (maximum), are supported.

**on\_hold** `boolean`

Indicates whether the account settlement for transfer is on hold. Possible values:

* `true`: Puts the settlement on hold.
* `false`: Releases the settlement.

**on\_hold\_until** `integer`

Timestamp, in Unix, that indicates until when the settlement of the transfer must be put on hold. If no value is passed, the settlement is put on hold indefinitely.

**recipient\_settlement\_id** `string`

Unique identifier of the settlement.

**recipient\_settlement** `array`

**id** `string`

Unique identifier of the settlement received by the Linked Account.

**entity** `string`

Indicates the type of entity. Here, it is `settlement`.

**amount** `string`

The settlement amount represented in the smallest unit of the currency passed.

**status** `string`

The status of the settlement. Possible values:
-`processed` - The settlement process was successful.
-`failed` - The settlement process failed.

**fee** `integer`

Fee (including GST) charged by Razorpay.

**tax** `integer`

GST charged for the payment.

**utr** `string`

Unique identifier received for the settlement from the bank.

**created\_at** `integer`

Timestamp, in Unix, at which the settlement was created.

**linked\_account\_notes** `array`

List of keys from the `notes` object which needs to be shown to Linked Accounts on their Dashboard. For example, `"region", "city"`. Only the keys will be shown, not values.

**created\_at** `integer`

Timestamp, in Unix, at which the transfer was created.

**processed\_at** `integer`

Timestamp, in Unix, at which the transfer was processed.

**error** `array`

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

**reason** `string`

The exact error reason. It can be handled programmatically.

**source\_channel** `string`

Medium through which transfers were created. For example, `online`.

## Errors

> [accordion] The api key/secret provided is invalid
>
> **Code:** `4xx`
>
> This error occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
>
> **Solution:** Make sure the API Keys are active and entered correctly. Also, there should not be any whitespaces before or after the keys. If you get null as an API response, an invalid `recipient_settlement_id` was passed. Ensure to pass a valid `recipient_settlement_id`, and it belongs to the Linked Account.
