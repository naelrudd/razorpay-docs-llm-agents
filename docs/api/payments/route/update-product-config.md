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

```bash Bank Account theme={null}
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

```bash VPA theme={null}
curl -X PATCH https://api.razorpay.com/v2/accounts/acc_HQVlm3bnPmccC0/products/acc_prd_HEgNpywUFctQ9e/ \
-u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-H "Content-Type: application/json" \
-d '{
   "settlement_accounts":[
      {
         "method":"upi",
         "upi":{
            "vpa":"ravi.kumar@okhdfcbank",
            "beneficiary_name":"Ravi Kumar",
            "currency":"INR",
            "is_default":true
         }
      }
   ],
   "tnc_accepted":true
}'
```

```bash Composite theme={null}
curl -X PATCH https://api.razorpay.com/v2/accounts/acc_HQVlm3bnPmccC0/products/acc_prd_HEgNpywUFctQ9e/ \
-u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-H "Content-Type: application/json" \
-d '{
   "settlement_accounts":[
      {
         "method":"bank_account",
         "bank_account":{
            "account_number":"1234567890123456",
            "beneficiary_name":"Priya Sharma",
            "code_type":"ifsc",
            "code":"HDFC0000317",
            "currency":"INR",
            "is_default":true
         }
      }
   ],
   "tnc_accepted":true
}'
```

```json Success (Bank Account) theme={null}
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

```json Success (VPA) theme={null}
{
   "requested_configuration":[

   ],
   "active_configuration":{
      "settlement_accounts":[
         {
            "id":"sa_M1a2b3c4d5e6f7g8",
            "entity":"settlement_account",
            "method":"upi",
            "upi":{
               "vpa":"ravi.kumar@okhdfcbank",
               "beneficiary_name":"Ravi Kumar",
               "currency":"INR",
               "is_default":true
            },
            "verification_status":"verified",
            "verified_at":1708445520,
            "active":true
         }
      ]
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

```json Success (Composite) theme={null}
{
   "requested_configuration":[

   ],
   "active_configuration":{
      "settlement_accounts":[
         {
            "id":"sa_M1a2b3c4d5e6f7g9",
            "entity":"settlement_account",
            "method":"bank_account",
            "bank_account":{
               "account_number":"XXXXXXXXXXXXXX56",
               "beneficiary_name":"Priya Sharma",
               "code_type":"ifsc",
               "code":"HDFC0000317",
               "currency":"INR",
               "is_default":true
            },
            "verification_status":"pending",
            "active":true
         }
      ]
   },
   "requirements":[

   ],
   "tnc":{
      "id":"tnc_K1eopBqvIzCF8E",
      "accepted":true,
      "accepted_at":1659638222
   },
   "id":"acc_prd_K1eopGG9H32uvy",
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

**settlement\_accounts** `array`

Array of settlement destinations. Use this instead of `settlements` to configure a VPA (UPI id) as the settlement destination, or to switch a Linked Account's settlement destination between VPA and bank account. We currently support only 1 method per settlement account, so this array must contain exactly one entry.

**settlement\_accounts\[].method** `string` *required*

Settlement method. Possible values: `upi`, `bank_account`.

**settlement\_accounts\[].upi** `object`

Required when `method` is `upi`.

**settlement\_accounts\[].upi.vpa** `string` *required*

Vendor's UPI Virtual Payment Address. Format: `username@psp`. The VPA must be validated and active on the vendor's UPI app before submission.

**settlement\_accounts\[].upi.beneficiary\_name** `string` *required*

Name registered with the VPA. Must match the UPI registry.

**settlement\_accounts\[].upi.currency** `string` *required*

Currency code. Currently supports `INR`.

**settlement\_accounts\[].upi.is\_default** `boolean` *required*

Must be `true`. We currently support only 1 method per settlement account.

**settlement\_accounts\[].bank\_account** `object`

Required when `method` is `bank_account`.

**settlement\_accounts\[].bank\_account.account\_number** `string` *required*

Bank account number. 5–20 characters.

**settlement\_accounts\[].bank\_account.beneficiary\_name** `string` *required*

Account holder name.

**settlement\_accounts\[].bank\_account.code\_type** `string` *required*

Routing code type. Currently supports `ifsc`.

**settlement\_accounts\[].bank\_account.code** `string` *required*

IFSC code. 11 characters, format `AAAA0XXXXXX`.

**settlement\_accounts\[].bank\_account.currency** `string` *required*

Currency code. Currently supports `INR`.

**settlement\_accounts\[].bank\_account.is\_default** `boolean` *required*

Must be `true`. We currently support only 1 method per settlement account.

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

**settlement\_accounts** `array`

Present only when `settlement_accounts` was passed in the request. List of settlement destinations on the product configuration.

**id** `string`

Unique identifier of the settlement account. For example, `sa_M1a2b3c4d5e6f7g8`.

**entity** `string`

Entity type. Value: `settlement_account`.

**method** `string`

Settlement method. Possible values: `upi`, `bank_account`. Bank account numbers are returned masked, showing only the last 2 characters. For example, `XXXXXXXXXXXXXX56`.

**verification\_status** `string`

Verification status of the settlement destination. For UPI, this is synchronous and returns `verified` in the response. For bank accounts, verification happens asynchronously via penny drop (10–15 minutes) and the status starts as `pending`.

**verified\_at** `integer`

Unix timestamp when the settlement destination was verified. Present only once `verification_status` is `verified`.

**active** `boolean`

Indicates whether the settlement destination is active.

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

> [accordion] More than one entry was provided in `settlement_accounts`.
>
> **Code:** `400`
>
> This error occurs when more than one settlement destination is provided. We currently support only 1 method per settlement account.
>
> **Solution:** Send exactly one entry in `settlement_accounts`.

> [accordion] Invalid `method`.
>
> **Code:** `400`
>
> This error occurs when `settlement_accounts[].method` is not one of the supported values.
>
> **Solution:** Use `bank_account` or `upi` as the settlement method.

> [accordion] The VPA format is invalid.
>
> **Code:** `400`
>
> This error occurs when the VPA is not in the `username@psp` format.
>
> **Solution:** Validate the VPA format on your side before submission.

> [accordion] The VPA does not exist or is inactive on the UPI registry.
>
> **Code:** `422`
>
> This error occurs when the VPA cannot be found or has not been activated on the vendor's UPI app.
>
> **Solution:** Prompt the vendor to verify and activate the VPA on their UPI app before resubmitting.

> [accordion] The beneficiary name does not match the name registered with the VPA or bank account.
>
> **Code:** `422`
>
> This error occurs when the `beneficiary_name` provided does not match the name registered with the VPA or bank account.
>
> **Solution:** Re-confirm the exact name with the vendor and update the `beneficiary_name` accordingly.
