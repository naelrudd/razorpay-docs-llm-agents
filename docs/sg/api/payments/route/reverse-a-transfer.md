> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Reverse a Transfer

> Reverse a Transfer using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create reversals on a particular `transfer_id`.

* The amount specified is debited from the Linked Account balance and credited to your balance.

* Partial reversals are also supported, and you can create multiple reversals on a `transfer_id`. If you do not provide the `amount` parameter in the request, then the entire amount of the transfer is reversed.

> [!NOTE]
>
> **Handy Tips**
> If a reversal ID is generated, the reversal was successful.

```bash Curl theme={null}
curl -X POST https://api.razorpay.com/v1/transfers/trf_EAznuJ9cDLnF7Y/reversals \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-H 'content-type: application/json'
-d '{
   "amount":100,
   "notes":{
      "branch":"Acme Corp Bangalore North",
      "name":"Alex Lim"
   }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String transferId = "trf_EAznuJ9cDLnF7Y";

JSONObject transferRequest = new JSONObject();
transferRequest.put("amount","100");
JSONObject notes = new JSONObject();
notes.put("branch","Acme Corp Bangalore North");
notes.put("name","Alex Lim");
transferParams.put("notes",notes);

Transfer transfer = razorpay.transfers.reversal(transferId,transferRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->transfer->fetch($transferId)->reverse(array('amount'=>'100','notes' => array('branch' => 'Acme Corp Bangalore North','name' => 'Alex Lim')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.transfers.reverse(transferId,{
    amount:100,
    notes: {
        branch: "Acme Corp Bangalore North",
        name: "Alex Lim"
      }
})
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.transfer.reverse(transferId, {
  "amount": 100,
  "notes":{
            "branch":"Acme Corp Bangalore North",
            "name":"Alex Lim"
         }
  })
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

transferId = "trf_EAznuJ9cDLnF7Y"

para_attr = {
    "amount":100,
    "notes": {
        "branch": "Acme Corp Bangalore North",
        "name": "Alex Lim"
      }
}

Razorpay::Transfer.fetch(transferId).reverse(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "amount": 100,
  "notes": map[string]interface{}{
        "branch": "Acme Corp Bangalore North",
        "name": "Alex Lim"
      }
}
body, err := client.Transfer.Reverse("<transferId>", data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]
");

string transferId = "trf_EAznuJ9cDLnF7Y";

Dictionary<string, object> transferRequest = new Dictionary<string, object>();
transferRequest.Add("amount","100");

Reversal transfer = client.Transfer.Fetch(transferId).Reversal(transferRequest);
```

```bash CLI theme={null}
razorpay route transfers reverse trf_JMNiqyuoFoJcXb \
  --amount 100
```

```bash Curl theme={null}
curl -X POST https://api.razorpay.com/v1/transfers/trf_EAznuJ9cDLnF7Y/reversals \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-H 'content-type: application/json'
-d '{
   "amount":100,
   "notes":{
      "branch":"Acme Corp Johor Bahru",
      "name":"Nur Aisyah"
   }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String transferId = "trf_EAznuJ9cDLnF7Y";

JSONObject transferRequest = new JSONObject();
transferRequest.put("amount","100");
JSONObject notes = new JSONObject();
notes.put("branch","Acme Corp Johor Bahru");
notes.put("name","Nur Aisyah");
transferParams.put("notes",notes);

Transfer transfer = razorpay.transfers.reversal(transferId,transferRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->transfer->fetch($transferId)->reverse(array('amount'=>'100','notes' => array('branch' => 'Acme Corp Johor Bahru','name' => 'Nur Aisyah')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.transfers.reverse(transferId,{
    amount:100,
    notes: {
        branch: "Acme Corp Johor Bahru",
        name: "Nur Aisyah"
      }
})
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.transfer.reverse(transferId, {
  "amount": 100,
  "notes":{
            "branch":"Acme Corp Johor Bahru",
            "name":"Nur Aisyah"
         }
  })
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

transferId = "trf_EAznuJ9cDLnF7Y"

para_attr = {
    "amount":100,
    "notes": {
        "branch": "Acme Corp Johor Bahru",
        "name": "Nur Aisyah"
      }
}

Razorpay::Transfer.fetch(transferId).reverse(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "amount": 100,
  "notes": map[string]interface{}{
        "branch": "Acme Corp Johor Bahru",
        "name": "Nur Aisyah"
      }
}
body, err := client.Transfer.Reverse("<transferId>", data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]
");

string transferId = "trf_EAznuJ9cDLnF7Y";

Dictionary<string, object> transferRequest = new Dictionary<string, object>();
transferRequest.Add("amount","100");

Reversal transfer = client.Transfer.Fetch(transferId).Reversal(transferRequest);
```

```bash CLI theme={null}
razorpay route transfers reverse trf_JMNiqyuoFoJcXb \
  --amount 100
```

```json Success theme={null}
{
  "id": "rvrsl_EB0BWgGDAu7tOz",
  "entity": "reversal",
  "transfer_id": "trf_EAznuJ9cDLnF7Y",
  "amount": 100,
  "fee": 0,
  "tax": 0,
  "currency": "SGD",
  "notes": [],
  "initiator_id": "CJoeHMNpi0nC7k",
  "customer_refund_id": null,
  "created_at": 1580456007
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
  "id": "rvrsl_EB0BWgGDAu7tOz",
  "entity": "reversal",
  "transfer_id": "trf_EAznuJ9cDLnF7Y",
  "amount": 100,
  "fee": 0,
  "tax": 0,
  "currency": "MYR",
  "notes": [],
  "initiator_id": "CJoeHMNpi0nC7k",
  "customer_refund_id": null,
  "created_at": 1580456007
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

Unique identifier of the transfer to be reversed.

## Request Parameters

**amount** `integer`

The amount to be reversed from the Linked Account to your account. If this parameter is not passed, the entire transfer amount will be reversed.

**notes** `json object`

Set of key-value pairs that can be associated with an entity. These pairs can be useful for storing additional information about the entity. A maximum of 15 key-value pairs, each of 256 characters (maximum), are supported. For example, `"region": "south", "city": "Bangalore"`.

## Response Parameters

**id** `string`

The unique identifier of the reversal.

**entity** `string`

The name of the entity. Here, it is `reversal`.

**transfer\_id** `string`

The unique identifier of the transfer that was reversed.

**amount** `integer`

The amount that was reversed, in cents.

**currency** `string`

ISO currency code. We support route reversals only in INR.

**created\_at** `integer`

Timestamp in Unix. This indicates the time at which the reversal was created.

## Errors

> [accordion] The api key/secret provided is invalid
>
> **Code:** `4xx`
>
> This error occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
>
> **Solution:** Make sure the API Keys are active and entered correctly. Also, there should not be any whitespaces before or after the keys.

> [accordion] The amount must be at least SGD 1.00
>
> **Code:** `400`
>
> This error occurs when the amount is less than the minimum amount. The transaction amount expressed in the currency subunit, such as cents (in SGD) should always be greater than or equal to S\$1.
>
> **Solution:** Make sure the amount is equal to or greater than the minimum amount of S\$1.

> [accordion] transfer\_id is not a valid id
>
> **Code:** `400`
>
> This error occurs when you pass an invalid `transfer_id` in the API endpoint.
>
> **Solution:** Make sure to pass a vaild `transfer_id`.

> [accordion] The linked account does not have sufficient balance to process reversal.
>
> **Code:** `400`
>
> Insufficient balance in the linked account to complete the reversal.
>
> **Solution:** Ensure that you have sufficient balance in your linked account to complete the reversal.
