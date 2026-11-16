> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Update a Product Configuration

> Update a product configuration using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to update a product configuration.

```bash Curl theme={null}
curl -X PATCH https://api.razorpay.com/v2/accounts/acc_HQVlm3bnPmccC0/products/acc_prd_HEgNpywUFctQ9e/ \
-u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-H "Content-Type: application/json" \
-d '{
   "settlements":{
      "account_number":"1234567890123456",
      "ifsc_code":"HDFC0000317",
      "beneficiary_name":"Gaurav Kumar"
   },
   "tnc_accepted":true
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String accountId = "acc_HQVlm3bnPmccC0";

String productId = "acc_prd_HEgNpywUFctQ9e";

JSONObject productRequest = new JSONObject();

JSONObject settlements = new JSONObject();
settlements.put("account_number","1234567890123456");
settlements.put("ifsc_code","HDFC0000317");
settlements.put("beneficiary_name","Gaurav Kumar");

productRequest.put("settlements",settlements);

productRequest.put("tnc_accepted",true);

Account product = instance.product.edit(accountId, productId, productRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

accountId = "acc_HQVlm3bnPmccC0"
productId = "acc_prd_HEgNpywUFctQ9e"

client.product.edit(accountId, productId, {
  "settlements": {
    "account_number": "1234567890123456",
    "ifsc_code": "HDFC0000317",
    "beneficiary_name": "Gaurav Kumar"
  },
  "tnc_accepted": True
})
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$accountId = "acc_HQVlm3bnPmccC0";
$productId = "acc_prd_HEgNpywUFctQ9e";

$api->account->fetch($accountId)->products()->edit($productId, array(
    "settlements" => array(
        "account_number" => "1234567890123456",
        "ifsc_code" => "HDFC0000317",
        "beneficiary_name" => "Gaurav Kumar"
    ),
    "tnc_accepted" => true
));
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient(your_key_id, your_secret);

string accountId = "acc_HQVlm3bnPmccC0";

string productId = "acc_prd_HEgNpywUFctQ9e";

Dictionary<string, object> productRequest = new Dictionary<string, object>();

Dictionary<string, object> settlements = new Dictionary<string, object>();
settlements.Add("account_number", "1234567891");
settlements.Add("ifsc_code", "HDFC0000317");
settlements.Add("beneficiary_name", "Gaurav Kumar");

productRequest.Add("settlements", settlements);
productRequest.Add("tnc_accepted", true);

Product product = client.Product.Fetch(accountId, productId).Edit(productRequest);
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

accountId = "acc_HQVlm3bnPmccC0"
productId = "acc_prd_HEgNpywUFctQ9e"

Razorpay::Product.edit(accountId, productId, {
  "settlements": {
    "account_number": "1234567890123456",
    "ifsc_code": "HDFC0000317",
    "beneficiary_name": "Gaurav Kumar"
  },
  "tnc_accepted": true
})
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

var accountId = "acc_HQVlm3bnPmccC0";
var productId = "acc_prd_HEgNpywUFctQ9e";

instance.products.edit(accountId, productId, {
  "settlements": {
    "account_number": "1234567890123456",
    "ifsc_code": "HDFC0000317",
    "beneficiary_name": "Gaurav Kumar"
  },
  "tnc_accepted": true
});
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

accountId := "acc_HQVlm3bnPmccC0"
productId := "acc_prd_HEgNpywUFctQ9e"

data := map[string]interface{}{
    "settlements": map[string]interface{}{
        "account_number":"1234567890123456",
        "ifsc_code": "HDFC0000317",
        "beneficiary_name": "Gaurav Kumar",
    },
    "tnc_accepted": true
}

body, err := client.Product.Edit(accountId, productId, data, nil)
```

```bash CLI theme={null}
razorpay route accounts product-update acc_IEIkSOM5VJb2Lm pro_IEIkSOM5VJb2Lm \
  --account-number 9876543210123456 \
  --ifsc HDFC0001234 \
  --beneficiary-name "Acme Pvt Ltd" \
  --tnc-accepted
```

```json Success theme={null}
{
   "requested_configuration":[

   ],
   "active_configuration":{
      "settlements":{
         "account_number":"1234567890123456",
         "ifsc_code":"HDFC0000317",
         "beneficiary_name":"Gaurav Kumar"
      }
   },
   "requirements":[

   ],
   "tnc":{
      "id":"tnc_K1eopApuHyBE7D",
      "accepted":true,
      "accepted_at":1659638222
   },
   "id":"acc_prd_K1eopFF8G21tux",
   "product_name":"route",
   "activation_status":"activated",
   "account_id":"acc_K1em7bWYEiwmnc",
   "requested_at":1659638222
}
```

```json Failure theme={null}
{
   "error":{
      "code":"BAD_REQUEST_ERROR",
      "description":"Linked account does not exist",
      "source":"",
      "step":"",
      "reason":"linked_account_id_does_not_exist",
      "metadata":{

      }
   }
}
```

## Path Parameters

**account\_id** `string` *required*

The unique identifier of an account generated by Razorpay. For example, `acc_HQVlm3bnPmccC0`.

**product\_id** `string` *required*

The unique identifier of a product generated by Razorpay. For example, `acc_prd_HEgNpywUFctQ9e`.

## Request Parameters

**settlements** `object`

The Settlement settings object.

**account\_number** `string`

The bank account number to which settlements are made. For example, `1234567890123456`.

**ifsc\_code** `string`

The IFSC associated with the bank account. For example, `HDFC0000317`.

**beneficiary\_name** `string` *required*

The name of the beneficiary associated with the bank account.

**tnc\_accepted** `boolean` *required*

Determines whether the terms and conditions are accepted or not. Possible values: `true`/`false`.

## Response Parameters

**requested\_configuration** `object`

The configuration of the product requested by the user that is yet to be set as active.

**active\_configuration** `object`

The configuration of the product that has been set as active.

**settlements** `object`

The Settlement settings object.

**account\_number** `string`

The bank account number to which settlements are made. Account details can be found on the Dashboard. For example, `7878780080310012`.

**ifsc\_code** `string`

The IFSC associated with the bank account. For example, `RATN0VAAPIS`.

**beneficiary\_name** `string`

The name of the beneficiary associated with the bank account.

> [!NOTE]
>
> **Handy Tip**
>
> This API parameter is needed to complete the KYC process. However, it is optional for this API.

**requirements** `object`

The list of requirements to be enabled for this product or some of the configurations under this product.

## Errors

> [accordion] Linked account does not exist.
>
> **Code:** `400`
>
> This error occurs when the requester is not the parent of the child account, or the child account does not exist.
>
> **Solution:** Ensure the Linked Account id exists before proceeding with the update API.

> [accordion] Merchant activation form has been locked for editing by admin.
>
> **Code:** `400`
>
> This error occurs when the submitted extra fields are under the review stage.
>
> **Solution:** You can wait for the review to be successful.

> [accordion] Invalid IFSC Code.
>
> **Code:** `400`
>
> This error occurs when the IFSC is invalid.
>
> **Solution:** Ensure to pass the valid IFSC.

> [accordion] The account number must be between 5 and 20 characters.
>
> **Code:** `400`
>
> This error occurs when the account number is less than 5 or more than 20 characters.
>
> **Solution:** Ensure the account number is between 5 to 20 characters.
