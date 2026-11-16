> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# 1. Create the Authorisation Transaction

> Know how to create an authorisation transaction with method emandate so customers can complete the authorization using Aadhaar, netbanking or a debit card.

Available in
🇮🇳 India

You can create an authorisation transaction using [Razorpay APIs](#1-1-using-razorpay-apis) or [Registration Link](#1-2-using-a-registration-link).

## 1.1. Using Razorpay APIs

To create an authorisation transaction using the Razorpay APIs, you need to:

1. [Fetch Payment Methods](#1-1-1-fetch-payment-methods).
2. [Create a Customer](#1-1-2-create-a-customer).
3. [Create an Order](#1-1-3-create-an-order).
4. [Create Authorisation Payment using Razorpay APIs](#1-1-4-create-an-authorisation-payment).

### 1.1.1. Fetch Payment Methods

Use the below endpoint to fetch a list of banks Razorpay supports for different payment methods.

`GET /methods`

> [!WARNING]
>
> **Watch Out!**
>
> To fire this API, provide your \[KEY\_ID] for authorization. Your \[KEY\_SECRET] is NOT required and should NOT be passed.

```bash Request theme={null}
curl -u [YOUR_KEY_ID]\
- X GET https://api.razorpay.com/v1/methods \
```

```json Response theme={null}
{
    "methods": {
        "entity": "methods",
        ...
        recurring: {
            emandate: {
                        "AUBL": {
                            "auth_types": [
                            "netbanking",
                            "aadhaar",
                            "debitcard"
                            ],
                            "is_merged_bank": false,
                            "name": "AU SMALL FINANCE BANK"
                        },
                    },
            }
        }
    }
```

### 1.1.2. Create a Customer

Razorpay links recurring tokens to customers using a unique identifier generated through the Customer API.

You can create [customers](https://razorpay.com/docs/api/customers.md) with basic information such as `email` and `contact` and use them for various Razorpay offerings. The following endpoint creates a customer.

`POST /customers`

> [accordion] Sample Code
>
> ```bash Curl theme={null}
> curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
> -X POST https://api.razorpay.com/v1/customers \
> -H "Content-Type: application/json" \
> -d '{
>   "name": "<name>",
>   "email": "<email>",
>   "contact": "<phone>",
>   "fail_existing": "0",
>   "notes":{
>     "note_key_1": "September",
>     "note_key_2": "Make it so."
>   }
> }'
> ```
>
> ```java Java theme={null}
> RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> JSONObject customerRequest = new JSONObject();
> customerRequest.put("name","<name>");
> customerRequest.put("contact","<phone>");
> customerRequest.put("email","<email>");
> customerRequest.put("fail_existing", "0");
> JSONObject notes = new JSONObject();
> notes.put("notes_key_1","Tea, Earl Grey, Hot");
> notes.put("notes_key_2","Tea, Earl Grey… decaf.");
> customerRequest.put("notes",notes);
>
> Customer customer = razorpay.customers.create(customerRequest);
> ```
>
> ```python Python theme={null}
> import razorpay
> client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
> client.customer.create({
>     'name': '<name>',
>     'email': '<email>',
>     'contact': '<phone>',
>     'fail_existing': "0",
>     'notes': {'note_key_1': 'September', 'note_key_2': 'Make it so.'}
>     })
> ```
>
> ```go Go theme={null}
> import ( razorpay "github.com/razorpay/razorpay-go" )
> client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
> data := map[string]interface{}{
>     "name": "<name>",
>     "contact": <phone>,
>     "email": "<email>",
>     "fail_existing": "0",
>     "notes": map[string]interface{}{
>         "notes_key_1": "Tea, Earl Grey, Hot",
>         "notes_key_2": "Tea, Earl Grey… decaf.",
>     },
> }
> body, err := client.Customer.Create(data, nil)
> ```
>
> ```php PHP theme={null}
> $api = new Api($key_id, $secret);
>
> $api->customer->create(array('name' => '<name>', 'email' => '<email>','contact'=>'<phone>','fail_existing' => "0", 'notes'=> array('notes_key_1'=> 'Tea, Earl Grey, Hot','notes_key_2'=> 'Tea, Earl Grey… decaf'));
> ```
>
> ```csharp .NET theme={null}
> RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> Dictionary<string, object> options = new Dictionary<string,object>();
>
> options.Add("name", "<name>"); 
> options.Add("contact", "<phone>"); 
> options.Add("email", "<email>"); 
> options.Add("fail_existing", "0"); 
>
> Customer customer = Customer.Create(options);
> ```
>
> ```ruby Ruby theme={null}
> require "razorpay"
> Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
>
> para_attr = {
>   "name": "<name>",
>   "contact": "<phone>",
>   "email": "<email>",
>   "fail_existing": "0",
>   "notes": {
>     "notes_key_1": "Tea, Earl Grey, Hot",
>     "notes_key_2": "Tea, Earl Grey… decaf."
>   }
> }
>
> Razorpay::Customer.create(para_attr)
> ```
>
> ```javascript Node.js theme={null}
> var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
>
> instance.customers.create({
>   name: "<name>",
>   contact: "<phone>",
>   email: "<email>",
>   fail_existing: "0",
>   notes: {
>     notes_key_1: "Tea, Earl Grey, Hot",
>     notes_key_2: "Tea, Earl Grey… decaf."
>   }
> })
> ```
>
> ```json Response theme={null}
> {
>   "id":"cust_1Aa00000000001",
>   "entity":"customer",
>   "name":"<name>",
>   "email":"<email>",
>   "contact":"<phone>",
>   "gstin":null,
>   "notes":{
>       "note_key_1":"September",
>       "note_key_2":"Make it so."
>   },
>   "created_at ":1234567890
> }
> ```

### Request Parameters

`name`
: `string` The name of the customer. For example, `Gaurav Kumar`.

`email`
: `string` The email address of the customer. For example, `gaurav.kumar@example.com`.

`contact`
: `string` The phone number of the customer. For example, `9876543210`.

`fail_existing` *optional*
: `string` The request throws an exception by default if a customer with the exact details already exists. You can pass an additional parameter `fail_existing` to get the existing customer's details in the response. Possible values:

* `1` (default): If a customer with the same details already exists, throws an error.
* `0`: If a customer with the same details already exists, fetches details of the existing customer.

`notes` *optional*
: `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

### 1.1.3. Create an Order

You can use the Orders API to create a unique Razorpay order\_id that is associated with the authorisation transaction. The following endpoint creates an order.

`POST /orders`

> [tab] Emandate via Aadhaar
>
> Given below is the sample code to authenticate emandate with Aadhaar. Aadhaar authentication type is enabled by default for your Razorpay account.
>
> ```bash Curl theme={null}
> curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
> -X POST https://api.razorpay.com/v1/orders \
> -H "Content-Type: application/json" \
> -d '{
>   "amount": 0,
>   "currency": "INR",
>   "payment_capture": true,
>   "method": "emandate",
>   "customer_id": "cust_1Aa00000000001",
>   "receipt": "Receipt No. 1",
>   "notes": {
>     "notes_key_1": "Beam me up Scotty",
>     "notes_key_2": "Engage"
>   },
>   "token": {
>     "auth_type": "aadhaar",
>     "max_amount": 9999900,
>     "expire_at": 4102444799,
>     "bank_account": {
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": "1121431121541121",
>       "account_type": "savings",
>       "ifsc_code": "HDFC0000001"
>     },
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf."
>     }
>   }
> }'
> ```
>
> ```java Java theme={null}
> RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> JSONObject orderRequest = new JSONObject();
> orderRequest.put("amount", 0);
> orderRequest.put("currency", "INR");
> orderRequest.put("payment_capture", true);
> orderRequest.put("customer_id", "cust_JDdNazagOgg9Ig");
> orderRequest.put("method", "emandate");
> orderRequest.put("receipt", "receipt#1");
> JSONObject notes = new JSONObject();
> notes.put("notes_key_1","Tea, Earl Grey, Hot");
> notes.put("notes_key_2","Tea, Earl Grey… decaf.");
> orderRequest.put("notes", notes);
> JSONObject token = new JSONObject();
> token.put("auth_type","aadhaar");
> token.put("max_amount","9999900");
> token.put("expire_at","2709971120");
> JSONObject tokenNotes = new JSONObject();
> tokenNotes.put("notes_key_1","Tea, Earl Grey, Hot");
> tokenNotes.put("notes_key_2","Tea, Earl Grey… decaf.");
> token.put("notes",tokenNotes);
> orderRequest.put("token", token);
> JSONObject bankAccount = new JSONObject();
> bankAccount.put("beneficiary_name","Gaurav Kumar");
> bankAccount.put("account_number","11214311215411");
> bankAccount.put("account_type","savings");
> bankAccount.put("ifsc_code","HDFC0000001");
> token.put("bank_account",bankAccount);
>
> Order order = razorpay.orders.create(orderRequest);
> ```
>
> ```php PHP theme={null}
> $api = new Api($key_id, $secret);
>
> $api->order->create(array('amount' => 0,'currency' => 'INR','payment_capture' => true,'method' => 'emandate','customer_id' => 'cust_1Aa00000000001','receipt' => 'Receipt No. 1','notes' => array('notes_key_1' => 'Beam me up Scotty','notes_key_2' => 'Engage'),'token' => array('auth_type' => 'aadhaar','max_amount' => 9999900,'expire_at' => 4102444799,'notes' => array('notes_key_1' => 'Tea, Earl Grey, Hot','notes_key_2' => 'Tea, Earl Grey… decaf.'),'bank_account' => array('beneficiary_name' => 'Gaurav Kumar','account_number' => '1121431121541121','account_type' => 'savings','ifsc_code' => 'HDFC0000001'))));
> ```
>
> ```javascript Node.js theme={null}
> var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
>
> instance.orders.create({
>   amount: 0,
>   currency: "INR",
>   payment_capture: true,
>   method: "emandate",
>   customer_id: "cust_1Aa00000000001",
>   receipt: "Receipt No. 1",
>   notes: {
>     notes_key_1: "Beam me up Scotty",
>     notes_key_2: "Engage"
>   },
>   token: {
>     auth_type: "aadhaar",
>     max_amount: 9999900,
>     expire_at: 4102444799,
>     notes: {
>       notes_key_1: "Tea, Earl Grey, Hot",
>       notes_key_2: "Tea, Earl Grey… decaf."
>     },
>     bank_account: {
>       beneficiary_name: "Gaurav Kumar",
>       account_number: 1121431121541121,
>       account_type: "savings",
>       ifsc_code: "HDFC0000001"
>     }
>   }
> })
> ```
>
> ```python Python theme={null}
> client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
> client.order.create({
>     'amount': 0,
>     'currency': 'INR',
>     'method': 'emandate',
>     'payment_capture': True,
>     'customer_id': 'cust_1Aa00000000001',
>     'receipt': 'Receipt No. 1',
>     'notes': {'notes_key_1': 'Beam me up Scotty',
>               'notes_key_2': 'Engage'},
>     'token': {
>         'auth_type': 'aadhaar',
>         'max_amount': 9999900,
>         'expire_at': 4102444799,
>         'notes': {'notes_key_1': 'Tea, Earl Grey, Hot',
>                   'notes_key_2': 'Tea, Earl Grey... decaf.'},
>         'bank_account': {
>             'beneficiary_name': 'Gaurav Kumar',
>             'account_number': 1121431121541121,
>             'account_type': 'savings',
>             'ifsc_code': 'HDFC0000001'
>             }
>         }
>     })
> ```
>
> ```ruby Ruby theme={null}
> require "razorpay"
> Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
>
> Razorpay::Customer.create({
>   "amount": 0,
>   "currency": "INR",
>   "method": "emandate",
>   "customer_id": "cust_1Aa00000000001",
>   "receipt": "Receipt No. 1",
>   "notes": {
>     "notes_key_1": "Beam me up Scotty",
>     "notes_key_2": "Engage"
>   },
>   "token": {
>     "auth_type": "aadhaar",
>     "max_amount": 9999900,
>     "expire_at": 4102444799,
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf."
>     },
>     "bank_account": {
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": 1121431121541121,
>       "account_type": "savings",
>       "ifsc_code": "HDFC0000001"
>     }
>   }
> })
> ```
>
> ```go Go theme={null}
> import ( razorpay "github.com/razorpay/razorpay-go" )
> client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
> data := map[string]interface{}{
>   "amount": 0,
>   "currency": "INR",
>   "payment_capture": true,
>   "method": "emandate",
>   "customer_id": "cust_1Aa00000000001",
>   "receipt": "Receipt No. 1",
>   "notes": map[string]interface{}{
>     "notes_key_1": "Beam me up Scotty",
>     "notes_key_2": "Engage",
>   },
>   "token": map[string]interface{}{
>     "auth_type": "aadhaar",
>     "max_amount": 9999900,
>     "expire_at": 4102444799,
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf.",
>     },
>     "bank_account": map[string]interface{}{
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": "1121431121541121",
>       "account_type": "savings",
>       "ifsc_code": "HDFC0000001",
>     },
>   },
> }
> body, err := client.Order.Create(data, nil)
> ```
>
> ```json Response theme={null}
> {
>   "id": "order_1Aa00000000001",
>   "entity": "order",
>   "amount": 0,
>   "amount_paid": 0,
>   "amount_due": 0,
>   "currency": "INR",
>   "receipt": "Receipt No. 1",
>   "offer_id": null,
>   "status": "created",
>   "attempts": 0,
>   "notes": {
>     "notes_key_1": "Beam me up Scotty",
>     "notes_key_2": "Engage"
>   },
>   "created_at": 1579700597,
>   "token": {
>     "method": "emandate",
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf."
>     },
>     "recurring_status": null,
>     "failure_reason": null,
>     "currency": "INR",
>     "max_amount": 9999900,
>     "auth_type": "aadhaar",
>     "expire_at": 4102444799,
>     "bank_account": {
>       "ifsc": "HDFC0000001",
>       "bank_name": "HDFC Bank",
>       "name": "Gaurav Kumar",
>       "account_number": "1121431121541121",
>       "account_type": "savings",
>       "beneficiary_email": "gaurav.kumar@example.com",
>       "beneficiary_mobile": "9000090000"
>     },
>     "first_payment_amount": 0
>   }
> }
> ```

> [tab] Emandate via Netbanking
>
> Given below is the sample code to authenticate emandate with Netbanking.
>
> ```bash Curl theme={null}
> curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
> -X POST https://api.razorpay.com/v1/orders \
> -H "Content-Type: application/json" \
> -d '{
>   "amount": 0,
>   "currency": "INR",
>   "payment_capture": true,
>   "method": "emandate",
>   "customer_id": "cust_1Aa00000000001",
>   "receipt": "Receipt No. 1",
>   "notes": {
>     "notes_key_1": "Beam me up Scotty",
>     "notes_key_2": "Engage"
>   },
>   "token": {
>     "auth_type": "netbanking",
>     "max_amount": 9999900,
>     "expire_at": 4102444799,
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf."
>     },
>     "bank_account": {
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": "1121431121541121",
>       "account_type": "savings",
>       "ifsc_code": "HDFC0000001"
>     }
>   }
> }'
> ```
>
> ```java Java theme={null}
> RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> JSONObject orderRequest = new JSONObject();
> orderRequest.put("amount", 0);
> orderRequest.put("currency", "INR");
> orderRequest.put("payment_capture", true);
> orderRequest.put("customer_id", "cust_JDdNazagOgg9Ig");
> orderRequest.put("method", "emandate");
> orderRequest.put("receipt", "receipt#1");
> JSONObject notes = new JSONObject();
> notes.put("notes_key_1","Tea, Earl Grey, Hot");
> notes.put("notes_key_2","Tea, Earl Grey… decaf.");
> orderRequest.put("notes", notes);
> JSONObject token = new JSONObject();
> token.put("auth_type","netbanking");
> token.put("max_amount","9999900");
> token.put("expire_at","2709971120");
> JSONObject tokenNotes = new JSONObject();
> tokenNotes.put("notes_key_1","Tea, Earl Grey, Hot");
> tokenNotes.put("notes_key_2","Tea, Earl Grey… decaf.");
> token.put("notes",tokenNotes);
> orderRequest.put("token", token);
> JSONObject bankAccount = new JSONObject();
> bankAccount.put("beneficiary_name","Gaurav Kumar");
> bankAccount.put("account_number","11214311215411");
> bankAccount.put("account_type","savings");
> bankAccount.put("ifsc_code","HDFC0000001");
> token.put("bank_account",bankAccount);
>
> Order order = razorpay.orders.create(orderRequest);
> ```
>
> ```php PHP theme={null}
> $api = new Api($key_id, $secret);
>
> $api->order->create(array('amount' => 0,'currency' => 'INR','payment_capture' => true,'method' => 'emandate','customer_id' => 'cust_1Aa00000000001','receipt' => 'Receipt No. 1','notes' => array('notes_key_1' => 'Beam me up Scotty','notes_key_2' => 'Engage'),'token' => array('auth_type' => 'netbanking','max_amount' => 9999900,'expire_at' => 4102444799,'notes' => array('notes_key_1' => 'Tea, Earl Grey, Hot','notes_key_2' => 'Tea, Earl Grey… decaf.'),'bank_account' => array('beneficiary_name' => 'Gaurav Kumar','account_number' => '1121431121541121','account_type' => 'savings','ifsc_code' => 'HDFC0000001'))));
> ```
>
> ```javascript Node.js theme={null}
> var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
>
> instance.orders.create({
>   amount: 0,
>   currency: "INR",
>   payment_capture: true,
>   method: "emandate",
>   customer_id: "cust_1Aa00000000001",
>   receipt: "Receipt No. 1",
>   notes: {
>     notes_key_1: "Beam me up Scotty",
>     notes_key_2: "Engage"
>   },
>   token: {
>     auth_type: "netbanking",
>     max_amount: 9999900,
>     expire_at: 4102444799,
>     notes: {
>       notes_key_1: "Tea, Earl Grey, Hot",
>       notes_key_2: "Tea, Earl Grey… decaf."
>     },
>     bank_account: {
>       beneficiary_name: "Gaurav Kumar",
>       account_number: 1121431121541121,
>       account_type: "savings",
>       ifsc_code: "HDFC0000001"
>     }
>   }
> })
> ```
>
> ```python Python theme={null}
> client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
> client.order.create({
>     'amount': 0,
>     'currency': 'INR',
>     'method': 'emandate',
>     'customer_id': 'cust_1Aa00000000001',
>     'payment_capture': True,
>     'receipt': 'Receipt No. 1',
>     'notes': {'notes_key_1': 'Beam me up Scotty',
>               'notes_key_2': 'Engage'},
>     'token': {
>         'auth_type': 'netbanking',
>         'max_amount': 9999900,
>         'expire_at': 4102444799,
>         'notes': {'notes_key_1': 'Tea, Earl Grey, Hot',
>                   'notes_key_2': 'Tea, Earl Grey... decaf.'},
>         'bank_account': {
>             'beneficiary_name': 'Gaurav Kumar',
>             'account_number': 1121431121541121,
>             'account_type': 'savings',
>             'ifsc_code': 'HDFC0000001'
>             }
>         }
>     })
> ```
>
> ```ruby Ruby theme={null}
> require "razorpay"
> Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
>
> Razorpay::Customer.create({
>   "amount": 0,
>   "currency": "INR",
>   "method": "emandate",
>   "customer_id": "cust_1Aa00000000001",
>   "receipt": "Receipt No. 1",
>   "notes": {
>     "notes_key_1": "Beam me up Scotty",
>     "notes_key_2": "Engage"
>   },
>   "token": {
>     "auth_type": "netbanking",
>     "max_amount": 9999900,
>     "expire_at": 4102444799,
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf."
>     },
>     "bank_account": {
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": 1121431121541121,
>       "account_type": "savings",
>       "ifsc_code": "HDFC0000001"
>     }
>   }
> })
> ```
>
> ```go Go theme={null}
> import ( razorpay "github.com/razorpay/razorpay-go" )
> client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
> data := map[string]interface{}{
>   "amount": 0,
>   "currency": "INR",
>   "payment_capture": true,
>   "method": "emandate",
>   "customer_id": "cust_1Aa00000000001",
>   "receipt": "Receipt No. 1",
>   "notes": map[string]interface{}{
>     "notes_key_1": "Beam me up Scotty",
>     "notes_key_2": "Engage",
>   },
>   "token": map[string]interface{}{
>     "auth_type": "netbanking",
>     "max_amount": 9999900,
>     "expire_at": 4102444799,
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf.",
>     },
>     "bank_account": map[string]interface{}{
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": "1121431121541121",
>       "account_type": "savings",
>       "ifsc_code": "HDFC0000001",
>     },
>   },
> }
> body, err := client.Order.Create(data, nil)
> ```
>
> ```csharp .NET theme={null}
> RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> Dictionary<string, object> orderRequest = new Dictionary<string, object>();
> orderRequest.Add("amount", 0);
> orderRequest.Add("currency", "INR");
> orderRequest.Add("payment_capture", true);
> orderRequest.Add("customer_id", "cust_JDdNazagOgg9Ig");
> orderRequest.Add("method", "emandate");
> orderRequest.Add("receipt", "receipt#1");
> Dictionary<string, object> notes = new Dictionary<string, object>();
> notes.Add("notes_key_1","Tea, Earl Grey, Hot");
> notes.Add("notes_key_2","Tea, Earl Grey… decaf.");
> orderRequest.Add("notes", notes);
> Dictionary<string, object> token = new Dictionary<string, object>();
> token.Add("auth_type","netbanking");
> token.Add("max_amount","9999900");
> token.Add("expire_at","2709971120");
> Dictionary<string, object> tokenNotes = new Dictionary<string, object>();
> tokenNotes.Add("notes_key_1","Tea, Earl Grey, Hot");
> tokenNotes.Add("notes_key_2","Tea, Earl Grey… decaf.");
> token.Add("notes",tokenNotes);
> orderRequest.Add("token", token);
> Dictionary<string, object> bankAccount = new Dictionary<string, object>();
> bankAccount.Add("beneficiary_name","Gaurav Kumar");
> bankAccount.Add("account_number","11214311215411");
> bankAccount.Add("account_type","savings");
> bankAccount.Add("ifsc_code","HDFC0001233");
> token.Add("bank_account",bankAccount);
>
> Order order = client.Order.Create(orderRequest);
> ```
>
> ```json Response theme={null}
> {
>   "id": "order_1Aa00000000001",
>   "entity": "order",
>   "amount": 0,
>   "amount_paid": 0,
>   "amount_due": 0,
>   "currency": "INR",
>   "receipt": "Receipt No. 1",
>   "offer_id": null,
>   "status": "created",
>   "attempts": 0,
>   "notes": {
>     "notes_key_1": "Beam me up Scotty",
>     "notes_key_2": "Engage"
>   },
>   "created_at": 1579700597,
>   "token": {
>     "method": "emandate",
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf."
>     },
>     "recurring_status": null,
>     "failure_reason": null,
>     "currency": "INR",
>     "max_amount": 9999900,
>     "auth_type": "netbanking",
>     "expire_at": 4102444799,
>     "bank_account": {
>       "ifsc": "HDFC0000001",
>       "bank_name": "HDFC Bank",
>       "name": "Gaurav Kumar",
>       "account_number": "1121431121541121",
>       "account_type": "savings",
>       "beneficiary_email": "gaurav.kumar@example.com",
>       "beneficiary_mobile": "9000090000"
>     },
>     "first_payment_amount": 0
>   }
> }
> ```

> [tab] Emandate via Debit Card
>
> Given below is the sample code to authenticate emandate with debit card.
>
> ```bash Curl theme={null}
> curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
> -X POST https://api.razorpay.com/v1/orders \
> -H "Content-Type: application/json" \
> -d '{
>   "amount": 0,
>   "currency": "INR",
>   "payment_capture": true,
>   "method": "emandate",
>   "customer_id": "cust_1Aa00000000001",
>   "receipt": "Receipt No. 1",
>   "notes": {
>     "notes_key_1": "Beam me up Scotty",
>     "notes_key_2": "Engage"
>   },
>   "token": {
>     "auth_type": "debitcard",
>     "max_amount": 9999900,
>     "expire_at": 4102444799,
>     "bank_account": {
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": "1121431121541121",
>       "account_type": "savings",
>       "ifsc_code": "HDFC0000001"
>     },
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf."
>     }
>   }
> }'
> ```
>
> ```java Java theme={null}
> RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> JSONObject orderRequest = new JSONObject();
> orderRequest.put("amount", 0);
> orderRequest.put("currency", "INR");
> orderRequest.put("payment_capture", true);
> orderRequest.put("customer_id", "cust_JDdNazagOgg9Ig");
> orderRequest.put("method", "emandate");
> orderRequest.put("receipt", "receipt#1");
> JSONObject notes = new JSONObject();
> notes.put("notes_key_1","Tea, Earl Grey, Hot");
> notes.put("notes_key_2","Tea, Earl Grey… decaf.");
> orderRequest.put("notes", notes);
> JSONObject token = new JSONObject();
> token.put("auth_type","debitcard");
> token.put("max_amount","9999900");
> token.put("expire_at","2709971120");
> JSONObject tokenNotes = new JSONObject();
> tokenNotes.put("notes_key_1","Tea, Earl Grey, Hot");
> tokenNotes.put("notes_key_2","Tea, Earl Grey… decaf.");
> token.put("notes",tokenNotes);
> orderRequest.put("token", token);
> JSONObject bankAccount = new JSONObject();
> bankAccount.put("beneficiary_name","Gaurav Kumar");
> bankAccount.put("account_number","11214311215411");
> bankAccount.put("account_type","savings");
> bankAccount.put("ifsc_code","HDFC0000001");
> token.put("bank_account",bankAccount);
>
> Order order = razorpay.orders.create(orderRequest);
> ```
>
> ```php PHP theme={null}
> $api = new Api($key_id, $secret);
>
> $api->order->create(array('amount' => 0,'currency' => 'INR','payment_capture' => true,'method' => 'emandate','customer_id' => 'cust_1Aa00000000001','receipt' => 'Receipt No. 1','notes' => array('notes_key_1' => 'Beam me up Scotty','notes_key_2' => 'Engage'),'token' => array('auth_type' => 'debitcard','max_amount' => 9999900,'expire_at' => 4102444799,'notes' => array('notes_key_1' => 'Tea, Earl Grey, Hot','notes_key_2' => 'Tea, Earl Grey… decaf.'),'bank_account' => array('beneficiary_name' => 'Gaurav Kumar','account_number' => '1121431121541121','account_type' => 'savings','ifsc_code' => 'HDFC0000001'))));
> ```
>
> ```javascript Node.js theme={null}
> var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
>
> instance.orders.create({
>   amount: 0,
>   currency: "INR",
>   payment_capture: true,
>   method: "emandate",
>   customer_id: "cust_1Aa00000000001",
>   receipt: "Receipt No. 1",
>   notes: {
>     notes_key_1: "Beam me up Scotty",
>     notes_key_2: "Engage"
>   },
>   token: {
>     auth_type: "debitcard",
>     max_amount: 9999900,
>     expire_at: 4102444799,
>     notes: {
>       notes_key_1: "Tea, Earl Grey, Hot",
>       notes_key_2: "Tea, Earl Grey… decaf."
>     },
>     bank_account: {
>       beneficiary_name: "Gaurav Kumar",
>       account_number: 1121431121541121,
>       account_type: "savings",
>       ifsc_code: "HDFC0000001"
>     }
>   }
> })
> ```
>
> ```python Python theme={null}
> client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
> client.order.create({
>     'amount': 0,
>     'currency': 'INR',
>     'method': 'emandate',
>     'customer_id': 'cust_1Aa00000000001',
>     'payment_capture': True,
>     'receipt': 'Receipt No. 1',
>     'notes': {'notes_key_1': 'Beam me up Scotty',
>               'notes_key_2': 'Engage'},
>     'token': {
>         'auth_type': 'debitcard',
>         'max_amount': 9999900,
>         'expire_at': 4102444799,
>         'notes': {'notes_key_1': 'Tea, Earl Grey, Hot',
>                   'notes_key_2': 'Tea, Earl Grey... decaf.'},
>         'bank_account': {
>             'beneficiary_name': 'Gaurav Kumar',
>             'account_number': 1121431121541121,
>             'account_type': 'savings',
>             'ifsc_code': 'HDFC0000001'
>             }
>         }
>     })
> ```
>
> ```ruby Ruby theme={null}
> require "razorpay"
> Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
>
> Razorpay::Customer.create({
>   "amount": 0,
>   "currency": "INR",
>   "method": "emandate",
>   "customer_id": "cust_1Aa00000000001",
>   "receipt": "Receipt No. 1",
>   "notes": {
>     "notes_key_1": "Beam me up Scotty",
>     "notes_key_2": "Engage"
>   },
>   "token": {
>     "auth_type": "debitcard",
>     "max_amount": 9999900,
>     "expire_at": 4102444799,
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf."
>     },
>     "bank_account": {
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": 1121431121541121,
>       "account_type": "savings",
>       "ifsc_code": "HDFC0000001"
>     }
>   }
> })
> ```
>
> ```go Go theme={null}
> import ( razorpay "github.com/razorpay/razorpay-go" )
> client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
> data := map[string]interface{}{
>   "amount": 0,
>   "currency": "INR",
>   "payment_capture": true,
>   "method": "emandate",
>   "customer_id": "cust_1Aa00000000001",
>   "receipt": "Receipt No. 1",
>   "notes": map[string]interface{}{
>     "notes_key_1": "Beam me up Scotty",
>     "notes_key_2": "Engage",
>   },
>   "token": map[string]interface{}{
>     "auth_type": "debitcard",
>     "max_amount": 9999900,
>     "expire_at": 4102444799,
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf.",
>     },
>     "bank_account": map[string]interface{}{
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": "1121431121541121",
>       "account_type": "savings",
>       "ifsc_code": "HDFC0000001",
>     },
>   },
> }
> body, err := client.Order.Create(data, nil)
> ```
>
> ```json Response theme={null}
> {
>   "id": "order_1Aa00000000001",
>   "entity": "order",
>   "amount": 0,
>   "amount_paid": 0,
>   "amount_due": 0,
>   "currency": "INR",
>   "receipt": "Receipt No. 1",
>   "offer_id": null,
>   "status": "created",
>   "attempts": 0,
>   "notes": {
>     "notes_key_1": "Beam me up Scotty",
>     "notes_key_2": "Engage"
>   },
>   "created_at": 1579700597,
>   "token": {
>     "method": "emandate",
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf."
>     },
>     "recurring_status": null,
>     "failure_reason": null,
>     "currency": "INR",
>     "max_amount": 9999900,
>     "auth_type": "debitcard",
>     "expire_at": 4102444799,
>     "bank_account": {
>       "ifsc": "HDFC0000001",
>       "bank_name": "HDFC Bank",
>       "name": "Gaurav Kumar",
>       "account_number": "1121431121541121",
>       "account_type": "savings",
>       "beneficiary_email": "gaurav.kumar@example.com",
>       "beneficiary_mobile": "9000090000"
>     },
>     "first_payment_amount": 0
>   }
> }
> ```

> [!NOTE]
>
> **Authorisation transaction + auto-charge first payment**
>
> You can register a customer's mandate **and** charge them the first recurring payment as part of the same transaction. Know more about [charge first payment automatically after Emandate registration](https://razorpay.com/docs/api/payments/recurring-payments/emandate/auto-debit.md).

### Request Parameters

`amount` *mandatory*
: `integer` Amount in currency subunits. For emandate, the amount has to be `0`.

`currency` *mandatory*
: `string` The 3-letter ISO currency code for the payment. Currently, we only support `INR`.

`method` *mandatory*
: `string` The authorisation method. In this case the value will be `emandate`.

`payment_capture` *mandatory*
: `boolean` Determines if payment should be automatically captured. Possible values:

* `true` (recommended): Automatically capture the payment.
* `false` (default/not recommended): You have to manually capture payments.

`customer_id` *mandatory*
: `string` The unique identifier of the customer, who is to be charged. For example, `cust_D0cs04OIpPPU1F`.

`receipt` *optional*
: `string` A user-entered unique identifier for the order. For example, `rcptid #1`. This parameter should be mapped to the `order_id` sent by Razorpay.

`notes`*optional*
: `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

`token`
: Details related to the authorisation such as max amount and bank account information.

`auth_type` *optional*
: `string` Possible values:

* `netbanking`
* `debitcard`
* `aadhaar`

`max_amount` *optional*
: `integer` The maximum amount, in paise, that a customer can be charged in one transaction. Know about [maximum and default values](https://razorpay.com/docs/payments/recurring-payments/emandate/faqs.md#what-is-the-maximum-amount-which-can-be-debited-from-the-customers).

`expire_at` *optional*
: `integer` The Unix timestamp to indicate till when you can use the token (authorisation on the payment method) to charge the customer subsequent payments. Defaults to 40 years. The maximum value you can set is 40 years from the current date. Any value beyond this will throw an error.

`notes`*optional*
: `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

`bank_account` *optional*
: Customer's bank account details that should be pre-filled on the checkout.

`account_number` *conditional*
: `string` Mandatory if the `bank_account` object is sent. Customer's bank account number.

`account_type` *optional*
: `string` Customer's bank account type. Possible values:

* `savings` (default)
* `current`

`ifsc_code` *conditional*
: `string` Mandatory if the `bank_account` object is sent. Customer's bank IFSC. For example `UTIB0000001`.

`beneficiary_name` *conditional*
: `string` Mandatory if the `bank_account` object is sent. Customer's name. For example, `Gaurav Kumar`.

`notes`*optional*
: `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

> [!NOTE]
>
> **Authorisation transaction + auto-charge first payment**
>
> You can register a customer's mandate **AND** charge them the first recurring payment as part of the same transaction. Refer to the [Emandate section under Registration and Charge First Payment Together](https://razorpay.com/docs/api/payments/recurring-payments/emandate/auto-debit.md) for more information.

### 1.1.4. Create an Authorisation Payment

> [!NOTE]
>
> **Handler Function vs Callback URL**
>
> * **Handler Function**:
>   \
>   When you use the handler function, the response object of the successful payment (`razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature`) is submitted to the Checkout Form. You need to collect these and send them to your server.
> * **Callback URL**:
>   \
>   When you use a Callback URL, the response object of the successful payment (`razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature`) is submitted to the Callback URL.

> [accordion] Netbanking
>
> ```html Handler Function theme={null}
>  <script
>    type="text/javascript"
>    src="https://checkout.razorpay.com/v1/razorpay.js">
>  </script>
>  <script
>    src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js">
>  </script>
>
>  <body>
>    <button
>      id="btn"
>      style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">
>      Pay
>    </button>
>
>    <script>
>      const btn = document.querySelector("#btn");
>
>      var razorpay = new Razorpay({
>        key: "<YOUR_TEST_KEY>",
>        image: "https://i.imgur.com/n5tjHFD.jpg"
>      });
>
>      razorpay.once("ready", function (response) {
>        console.log(response.methods);
>      })
>
>      var data = {
>        "amount": 100, // in currency subunits. Here 1000 = 1000 paise, which equals to ₹10
>        "currency": "INR", // Default is INR. We support more than 90 currencies.
>        "email": "gaurav.kumar@example.com",
>        "contact": "9123456780",
>        "notes": {
>          "address": "Ground Floor, SJR Cyber, Laskar Hosur Road, Bengaluru",
>        },
>        "order_id": "order_00000000000001",
>        "customer_id": "cust_00000000000001",
>        "recurring": true,
>        "method": "emandate",
>        "bank": "HDFC",
>        "auth_type": "netbanking",
>        "bank_account[name]": "Gaurav Kumar",
>        "bank_account[account_number]": "1121431121541121",
>        "bank_account[account_type]": "savings",
>        "bank_account[ifsc]": "HDFC0000001"
>      };
>
>      btn.addEventListener("click", function () { // has to be placed within user initiated context, such as click, in order for popup to open.
>        razorpay.createPayment(data);
>
>        razorpay.on("payment.success", function (resp) {
>          alert(resp.razorpay_payment_id),
>          alert(resp.razorpay_order_id),
>          alert(resp.razorpay_signature)
>        }); // will pass payment ID, order ID and Razorpay signature to success handler.
>
>        razorpay.on("payment.error", function (resp) {
>          alert(resp.error.description)
>        }); // will pass error object to error handler
>      })
>    </script>
>  </body>
> ```
>
> ```html Callback URL theme={null}
>  <script
>    type="text/javascript"
>    src="https://checkout.razorpay.com/v1/razorpay.js">
>  </script>
>  <script
>    src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js">
>  </script>
>
>  <body>
>    <button
>      id="btn"
>      style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">
>      Pay
>    </button>
>
>    <script>
>      const btn = document.querySelector("#btn");
>
>      var razorpay = new Razorpay({
>        key: "<YOUR_TEST_KEY>",
>        image: "https://i.imgur.com/n5tjHFD.jpg"
>      });
>
>      razorpay.once("ready", function (response) {
>        console.log(response.methods);
>      })
>
>      var data = {
>        "callback_url": "www.example-callback-url.com",
>        "amount": 100, // in currency subunits. Here 1000 = 1000 paise, which equals to ₹10
>        "currency": "INR", // Default is INR. We support more than 90 currencies.
>        "email": "gaurav.kumar@example.com",
>        "contact": "9123456780",
>        "notes": {
>          "address": "Ground Floor, SJR Cyber, Laskar Hosur Road, Bengaluru",
>        },
>        "order_id": "order_00000000000001",
>        "customer_id": "cust_00000000000001",
>        "recurring": true,
>        "method": "emandate",
>        "bank": "HDFC",
>        "auth_type": "netbanking",
>        "bank_account[name]": "Gaurav Kumar",
>        "bank_account[account_number]": "1121431121541121",
>        "bank_account[account_type]": "savings",
>        "bank_account[ifsc]": "HDFC0000001"
>      };
>
>      btn.addEventListener("click", function () { // has to be placed within user initiated context, such as click, in order for popup to open.
>        razorpay.createPayment(data);
>      })
>    </script>
>  </body>
> ```

> [accordion] Debit Card
>
> ```html Handler Function theme={null}
>  <script
>    type="text/javascript"
>    src="https://checkout.razorpay.com/v1/razorpay.js">
>  </script>
>  <script
>    src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js">
>  </script>
>  <body>
>    <button
>      id="btn"
>      style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">
>      Pay
>    </button>
>    <script>
>      const btn = document.querySelector("#btn");
>
>      var razorpay = new Razorpay({
>        key: "<YOUR_TEST_KEY>",
>        image: "https://i.imgur.com/n5tjHFD.jpg"
>      });
>
>      razorpay.once("ready", function (response) {
>        console.log(response.methods);
>      })
>
>      var data = {
>        "amount": 100, // in currency subunits. Here 1000 = 1000 paise, which equals to ₹10
>        "currency": "INR", // Default is INR. We support more than 90 currencies.
>        "email": "gaurav.kumar@example.com",
>        "contact": "9123456780",
>        "notes": {
>          "address": "Ground Floor, SJR Cyber, Laskar Hosur Road, Bengaluru",
>        },
>        "order_id": "order_00000000000001",
>        "customer_id": "cust_00000000000001",
>        "recurring": true,
>        "method": "emandate",
>        "bank": "HDFC",
>        "auth_type": "debitcard",
>        "bank_account[name]": "Gaurav Kumar",
>        "bank_account[account_number]": "1121431121541121",
>        "bank_account[account_type]": "savings",
>        "bank_account[ifsc]": "HDFC0000001"
>      };
>
>      btn.addEventListener("click", function () { // has to be placed within user initiated context, such as click, in order for popup to open.
>        razorpay.createPayment(data);
>
>        razorpay.on("payment.success", function (resp) {
>          alert(resp.razorpay_payment_id),
>          alert(resp.razorpay_order_id),
>          alert(resp.razorpay_signature)
>        }); // will pass payment ID, order ID and Razorpay signature to success handler.
>
>        razorpay.on("payment.error", function (resp) {
>          alert(resp.error.description)
>        }); // will pass error object to error handler
>      })
>    </script>
>  </body>
> ```
>
> ```html Callback URL theme={null}
>  <script
>    type="text/javascript"
>    src="https://checkout.razorpay.com/v1/razorpay.js">
>  </script>
>  <script
>    src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js">
>  </script>
>
>  <body>
>    <button
>      id="btn"
>      style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">
>      Pay
>    </button>
>
>    <script>
>      const btn = document.querySelector("#btn");
>
>      var razorpay = new Razorpay({
>        key: "<YOUR_TEST_KEY>",
>        image: "https://i.imgur.com/n5tjHFD.jpg"
>      });
>
>      razorpay.once("ready", function (response) {
>        console.log(response.methods);
>      })
>
>      var data = {
>        "callback_url": "www.example-callback-url.com",
>        "amount": 100, // in currency subunits. Here 1000 = 1000 paise, which equals to ₹10
>        "currency": "INR", // Default is INR. We support more than 90 currencies.
>        "email": "gaurav.kumar@example.com",
>        "contact": "9123456780",
>        "notes": {
>          "address": "Ground Floor, SJR Cyber, Laskar Hosur Road, Bengaluru",
>        },
>        "order_id": "order_00000000000001",
>        "customer_id": "cust_00000000000001",
>        "recurring": true,
>        "method": "emandate",
>        "bank": "HDFC",
>        "auth_type": "debitcard",
>        "bank_account[name]": "Gaurav Kumar",
>        "bank_account[account_number]": "1121431121541121",
>        "bank_account[account_type]": "savings",
>        "bank_account[ifsc]": "HDFC0000001"
>      };
>
>      btn.addEventListener("click", function () { // has to be placed within user initiated context, such as click, in order for popup to open.
>        razorpay.createPayment(data);
>      })
>    </script>
>  </body>
> ```

> [accordion] Aadhaar
>
> ```html Handler Function theme={null}
>  <script
>    type="text/javascript"
>    src="https://checkout.razorpay.com/v1/razorpay.js">
>  </script>
>  <script
>    src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js">
>  </script>
>
>  <body>
>    <button
>      id="btn"
>      style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">
>      Pay
>    </button>
>
>    <script>
>      const btn = document.querySelector("#btn");
>
>      var razorpay = new Razorpay({
>        key: "<YOUR_TEST_KEY>",
>        image: "https://i.imgur.com/n5tjHFD.jpg"
>      });
>
>      razorpay.once("ready", function (response) {
>        console.log(response.methods);
>      })
>
>      var data = {
>        "amount": 100, // in currency subunits. Here 1000 = 1000 paise, which equals to ₹10
>        "currency": "INR", // Default is INR. We support more than 90 currencies.
>        "email": "gaurav.kumar@example.com",
>        "contact": "9123456780",
>        "notes": {
>          "address": "Ground Floor, SJR Cyber, Laskar Hosur Road, Bengaluru",
>        },
>        "order_id": "order_00000000000001",
>        "customer_id": "cust_00000000000001",
>        "recurring": true,
>        "method": "emandate",
>        "bank": "HDFC",
>        "auth_type": "aadhaar",
>        "bank_account[name]": "Gaurav Kumar",
>        "bank_account[account_number]": "1121431121541121",
>        "bank_account[account_type]": "savings",
>        "bank_account[ifsc]": "HDFC0000001"
>      };
>
>      btn.addEventListener("click", function () { // has to be placed within user initiated context, such as click, in order for popup to open.
>        razorpay.createPayment(data);
>
>        razorpay.on("payment.success", function (resp) {
>          alert(resp.razorpay_payment_id),
>          alert(resp.razorpay_order_id),
>          alert(resp.razorpay_signature)
>        }); // will pass payment ID, order ID and Razorpay signature to success handler.
>
>        razorpay.on("payment.error", function (resp) {
>          alert(resp.error.description)
>        }); // will pass error object to error handler
>      })
>    </script>
>  </body>
> ```
>
> ```html Callback URL theme={null}
>  <script
>    type="text/javascript"
>    src="https://checkout.razorpay.com/v1/razorpay.js">
>  </script>
>  <script
>    src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js">
>  </script>
>
>  <body>
>    <button
>      id="btn"
>      style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">
>      Pay
>    </button>
>
>    <script>
>      const btn = document.querySelector("#btn");
>
>      var razorpay = new Razorpay({
>        key: "<YOUR_TEST_KEY>",
>        image: "https://i.imgur.com/n5tjHFD.jpg"
>      });
>
>      razorpay.once("ready", function (response) {
>        console.log(response.methods);
>      })
>
>      var data = {
>        "callback_url": "www.example-callback-url.com",
>        "amount": 100, // in currency subunits. Here 1000 = 1000 paise, which equals to ₹10
>        "currency": "INR", // Default is INR. We support more than 90 currencies.
>        "email": "gaurav.kumar@example.com",
>        "contact": "9123456780",
>        "notes": {
>          "address": "Ground Floor, SJR Cyber, Laskar Hosur Road, Bengaluru",
>        },
>        "order_id": "order_00000000000001",
>        "customer_id": "cust_00000000000001",
>        "recurring": true,
>        "method": "emandate",
>        "bank": "HDFC",
>        "auth_type": "aadhaar",
>        "bank_account[name]": "Gaurav Kumar",
>        "bank_account[account_number]": "1121431121541121",
>        "bank_account[account_type]": "savings",
>        "bank_account[ifsc]": "HDFC0000001"
>      };
>
>      btn.addEventListener("click", function () { // has to be placed within user initiated context, such as click, in order for popup to open.
>        razorpay.createPayment(data);
>      })
>    </script>
>  </body>
> ```

### Additional Checkout Fields

`customer_id` *mandatory*
: `string` Unique identifier of the customer created in the [first step](#1-1-2-create-a-customer).

`order_id` *mandatory*
: `string` Unique identifier of the  order created in the [second step](#1-1-3-create-an-order).

`recurring` *mandatory*
: `boolean` Determines whether the recurring is enabled or not. Possible values:

* `true`: Recurring payment is enabled.
* `false`: Recurring payment is not enabled.

## 1.2. Using a Registration Link

Registration Link is an alternate way of creating an authorisation transaction. You can create a registration link using the [API](#1-2-1-create-a-registration-link) or [Dashboard](https://razorpay.com/docs/payments/recurring-payments/create.md#1-create-a-registration-link).

> [!NOTE]
>
> **Handy Tips**
>
> * You do not have to create a customer if you choose the registration link method for creating an authorisation transaction.
> * You can [use Webhooks to get notifications about successful payments](https://razorpay.com/docs/api/payments/recurring-payments/webhooks.md#check-registration-link-status-using-webhooks) against a registration link.

When you create a registration link, an [invoice](https://razorpay.com/docs/payments/invoices) is automatically issued to the customer. They can use this invoice to make the authorisation payment.

A registration link must always have an amount (in Paise) that the customer will be charged when making the authorisation payment. In the case of emandate, the order amount must be `0`.

### 1.2.1. Create a Registration Link

Use the below endpoint to create a registration link for recurring payments.

`POST /subscription_registration/auth_links`

```bash Emandate via Netbanking theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET>
-X POST https://api.razorpay.com/v1/subscription_registration/auth_links
-H "Content-Type: application/json" \
-d '{
  "customer": {
    "name": "Gaurav Kumar",
    "email": "gaurav.kumar@example.com",
    "contact": "9123456780"
  },
  "type": "link",
  "amount": 0,
  "currency": "INR",
  "description": "12 p.m. Meals",
  "subscription_registration": {
    "method": "emandate",
    "auth_type": "netbanking",
    "expire_at": 1580480689,
    "max_amount": 50000,
    "bank_account": {
      "beneficiary_name": "Gaurav Kumar",
      "account_number": "11214311215411",
      "account_type": "savings",
      "ifsc_code": "HDFC0001233"
    }
  },
  "receipt": "Receipt no. 1",
  "expire_by": 1880480689,
  "sms_notify": true,
  "email_notify": true,
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  }
}'
```

```json Response theme={null}
{
  "id": "inv_FHrY6tDtVP2dHg",
  "entity": "invoice",
  "receipt": "Receipt no. 1",
  "invoice_number": "Receipt no. 1",
  "customer_id": "cust_BMB3EwbqnqZ2EI",
  "customer_details": {
    "id": "cust_BMB3EwbqnqZ2EI",
    "name": "Gaurav Kumar",
    "email": "gaurav.kumar@example.com",
    "contact": "9123456780",
    "gstin": null,
    "billing_address": null,
    "shipping_address": null,
    "customer_name": "Gaurav Kumar",
    "customer_email": "gaurav.kumar@example.com",
    "customer_contact": "9123456780"
  },
  "order_id": "order_FHrY6tiC2y7NNN",
  "line_items": [],
  "payment_id": null,
  "status": "issued",
  "expire_by": 1880480689,
  "issued_at": 1595491063,
  "paid_at": null,
  "cancelled_at": null,
  "expired_at": null,
  "sms_status": "pending",
  "email_status": "pending",
  "date": 1595491063,
  "terms": null,
  "partial_payment": false,
  "gross_amount": 0,
  "tax_amount": 0,
  "taxable_amount": 0,
  "amount": 0,
  "amount_paid": 0,
  "amount_due": 0,
  "currency": "INR",
  "currency_symbol": "₹",
  "description": "test registration link",
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  },
  "comment": null,
  "short_url": "https://rzp.io/i/DxEcNtR",
  "view_less": true,
  "billing_start": null,
  "billing_end": null,
  "type": "link",
  "group_taxes_discounts": false,
  "created_at": 1595491063,
  "idempotency_key": null
}
```

```bash Emandate via Debit Card theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET>
-X POST https://api.razorpay.com/v1/subscription_registration/auth_links
-H "Content-Type: application/json" \
-d '{
  "customer": {
    "name": "Gaurav Kumar",
    "email": "gaurav.kumar@example.com",
    "contact": "9123456780"
  },
  "type": "link",
  "amount": 0,
  "currency": "INR",
  "description": "12 p.m. Meals",
  "subscription_registration": {
    "method": "emandate",
    "auth_type": "debitcard",
    "expire_at": 1580480689,
    "max_amount": 50000,
    "bank_account": {
      "beneficiary_name": "Gaurav Kumar",
      "account_number": "11214311215411",
      "account_type": "savings",
      "ifsc_code": "HDFC0001233"
    }
  },
  "receipt": "Receipt no. 1",
  "expire_by": 1880480689,
  "sms_notify": true,
  "email_notify": true,
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  }
}'
```

```json Response theme={null}
{
  "id": "inv_FHrZAOeCuB9HtK",
  "entity": "invoice",
  "receipt": "Receipt no. 1",
  "invoice_number": "Receipt no. 1",
  "customer_id": "cust_BMB3EwbqnqZ2EI",
  "customer_details": {
    "id": "cust_BMB3EwbqnqZ2EI",
    "name": "Gaurav Kumar",
    "email": "gaurav.kumar@example.com",
    "contact": "9123456780",
    "gstin": null,
    "billing_address": null,
    "shipping_address": null,
    "customer_name": "Gaurav Kumar",
    "customer_email": "gaurav.kumar@example.com",
    "customer_contact": "9123456780"
  },
  "order_id": "order_FHrZAPOStKd4xS",
  "line_items": [],
  "payment_id": null,
  "status": "issued",
  "expire_by": 1880480689,
  "issued_at": 1595491123,
  "paid_at": null,
  "cancelled_at": null,
  "expired_at": null,
  "sms_status": "pending",
  "email_status": "pending",
  "date": 1595491123,
  "terms": null,
  "partial_payment": false,
  "gross_amount": 0,
  "tax_amount": 0,
  "taxable_amount": 0,
  "amount": 0,
  "amount_paid": 0,
  "amount_due": 0,
  "currency": "INR",
  "currency_symbol": "₹",
  "description": "test registration link",
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  },
  "comment": null,
  "short_url": "https://rzp.io/i/RllVOmA",
  "view_less": true,
  "billing_start": null,
  "billing_end": null,
  "type": "link",
  "group_taxes_discounts": false,
  "created_at": 1595491123,
  "idempotency_key": null
}
```

```bash Emandate via Aadhaar theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET>
-X POST https://api.razorpay.com/v1/subscription_registration/auth_links
-H "Content-Type: application/json" \
-d '{
  "customer": {
    "name": "Gaurav Kumar",
    "email": "gaurav.kumar@example.com",
    "contact": "9123456780"
  },
  "type": "link",
  "amount": 0,
  "currency": "INR",
  "description": "12 p.m. Meals",
  "subscription_registration": {
    "method": "emandate",
    "auth_type": "aadhaar",
    "expire_at": 1580480689,
    "max_amount": 50000,
    "bank_account": {
      "beneficiary_name": "Gaurav Kumar",
      "account_number": "11214311215411",
      "account_type": "savings",
      "ifsc_code": "HDFC0001233"
    }
  },
  "receipt": "Receipt no. 1",
  "expire_by": 1880480689,
  "sms_notify": true,
  "email_notify": true,
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  }
}'
```

```json Response theme={null}
{
  "id": "inv_FHrZAOeCuB9HtK",
  "entity": "invoice",
  "receipt": "Receipt no. 1",
  "invoice_number": "Receipt no. 1",
  "customer_id": "cust_BMB3EwbqnqZ2EI",
  "customer_details": {
    "id": "cust_BMB3EwbqnqZ2EI",
    "name": "Gaurav Kumar",
    "email": "gaurav.kumar@example.com",
    "contact": "9123456780",
    "gstin": null,
    "billing_address": null,
    "shipping_address": null,
    "customer_name": "Gaurav Kumar",
    "customer_email": "gaurav.kumar@example.com",
    "customer_contact": "9123456780"
  },
  "order_id": "order_FHrZAPOStKd4xS",
  "line_items": [],
  "payment_id": null,
  "status": "issued",
  "expire_by": 1880480689,
  "issued_at": 1595491123,
  "paid_at": null,
  "cancelled_at": null,
  "expired_at": null,
  "sms_status": "pending",
  "email_status": "pending",
  "date": 1595491123,
  "terms": null,
  "partial_payment": false,
  "gross_amount": 0,
  "tax_amount": 0,
  "taxable_amount": 0,
  "amount": 0,
  "amount_paid": 0,
  "amount_due": 0,
  "currency": "INR",
  "currency_symbol": "₹",
  "description": "test registration link",
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  },
  "comment": null,
  "short_url": "https://rzp.io/i/RllVOmA",
  "view_less": true,
  "billing_start": null,
  "billing_end": null,
  "type": "link",
  "group_taxes_discounts": false,
  "created_at": 1595491123,
  "idempotency_key": null
}
```

### Request Parameters

`customer`
: Details of the customer to whom the registration link will be sent.

`name` *mandatory*
: `string` Customer's name.

`email` *mandatory*
: `string` Customer's email address.

`contact`*mandatory*
: `string` Customer's phone number.

`type` *mandatory*
: `string` In this case, the value is `link`.

`currency` *mandatory*
: `string` The 3-letter ISO currency code for the payment. Currently, only `INR` is supported.

`amount` *mandatory*
: `integer` The payment amount in the smallest currency sub-unit.

`description` *mandatory*
: `string` A description that appears on the hosted page. For example, `12:30 p.m. Thali meals (Gaurav Kumar)`.

`subscription_registration`
: Details of the authorisation payment.

`method` *mandatory*
: `string` The authorization method. In this case, it will be `emandate`.

`auth_type` *optional*
: `string` Possible values:

* `netbanking`
* `debitcard`
* `aadhaar`

`max_amount` *optional*
: `integer` The maximum amount, in paise, that a customer can be charged in one transaction. Know about [maximum and default values](https://razorpay.com/docs/payments/recurring-payments/emandate/faqs.md#what-is-the-maximum-amount-which-can-be-debited-from-the-customers).

`expire_at` *optional*
: `integer` The timestamp, in Unix format, till when you can use the token (authorization on the payment method) to charge the customer subsequent payments. Defaults to 10 years for `emandate`. The value can range from the current date to 31-12-2099 (`4101580799`).

`bank_account` *optional*
: The customer's bank account details.

`beneficiary_name` *conditional*
: `string` Mandatory if the `bank_account` object is sent. Name on the bank account. For example `Gaurav Kumar`.

`account_number` *conditional*
: `integer` Mandatory if the `bank_account` object is sent. Customer's bank account number. For example `11214311215411`.

`account_type` *optional*
: `string` Customer's bank account type. Possible values:

* `savings` (default)
* `current`

`ifsc_code` *conditional*
: `string` Mandatory if the `bank_account` object is sent. Customer's bank IFSC. For example `HDFC0000001`.

`sms_notify` *optional*
: `boolean` Indicates if SMS notifications are to be sent by Razorpay. Can have the following values:

* `true` (default): Notifications are sent by Razorpay.
* `false`: Notifications are not sent by Razorpay.

`email_notify` *optional*
: `boolean` Indicates if email notifications are to be sent by Razorpay. Can have the following values:

* `true` (default): Notifications are sent by Razorpay.
* `false`: Notifications are not sent by Razorpay.

`expire_by` *optional*
: `integer` The timestamp, in Unix, till when the registration link should be available to the customer to make the authorisation transaction.

`receipt` *optional*
: `string` A unique identifier entered by you for the order. For example, `Receipt No. 1`. This parameter should be mapped to the `order_id` sent by Razorpay.

`notes` *optional*
: `object` This is a key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

### 1.2.2. Send/Resend Notifications

The following endpoint sends/resends notifications with the short URL to the customer:

`POST /invoices/:id/notify_by/:medium`

> [accordion] Sample Code
>
> ```bash Curl theme={null}
>  curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
>  -X POST https://api.razorpay.com/v1/invoices/inv_1Aa00000000001/notify_by/sms
> ```
>
> ```java Java theme={null}
>  RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
>  String invoiceId = "inv_1Aa00000000001";
>
>  String medium = "sms";
>
>  Invoice invoice = razorpay.invoices.notifyBy(invoiceId, medium);
> ```
>
> ```php PHP theme={null}
>  $api = new Api($key_id, $secret);
>
>  $api->invoice->fetch($invoiceId)->notify($medium);
> ```
>
> ```javascript Node.js theme={null}
>  var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
>
>  instance.invoices.notifyBy(invoiceId, medium)
> ```
>
> ```python Python theme={null}
>  client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
>  client.invoice.notify_by(invoiceId, medium)
> ```
>
> ```ruby Ruby theme={null}
>  require "razorpay"
>  Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
>
>  invoiceId = "inv_JDdNb4xdf4gxQ7"
>
>  medium = "email" 
>
>  Razorpay::Invoice.notify_by(invoiceId, medium)
> ```
>
> ```go Go theme={null}
>  import ( razorpay "github.com/razorpay/razorpay-go" )
>  client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
>  body, err := client.Invoice.Notify("<invoiceId>", "<medium>", nil, nil)
> ```
>
> ```csharp .NET theme={null}
>  RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
>  string invoiceId = "inv_Z6t7VFTb9xHeOs";
>
>  string medium = "sms";
>
>  Invoice invoice = client.Invoice.Fetch(invoiceId).NotifyBy(medium);
> ```
>
> ```json Response theme={null}
> {
>   "success": true
> }
> ```

### Path Parameters

`id`*mandatory*
: `string` The unique identifier of the invoice linked to the registration link for which you want to send the notification. For example, `inv_1Aa00000000001`.

`medium` *mandatory*
: `string` Determines through which medium you want to resend the notification. Possible values:

* `sms`
* `email`

### 1.2.3. Cancel a Registration Link

The following endpoint cancels a registration link.

`POST /invoices/:id/cancel`

> [!NOTE]
>
> **Handy Tips**
>
> You can only cancel registration link in the `issued` state.

> [accordion] Sample Code
>
> ```bash Curl theme={null}
>  curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
>  -X POST https://api.razorpay.com/v1/invoices/inv_1Aa00000000001/cancel
> ```
>
> ```java Java theme={null}
>  RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
>  String invoiceId = "inv_1Aa00000000001";
>
>  Invoice invoice = razorpay.invoices.cancel(invoiceId);
> ```
>
> ```php PHP theme={null}
>  $api = new Api($key_id, $secret);
>
>  $api->invoice->fetch($invoiceId)->cancel();
> ```
>
> ```javascript Node.js theme={null}
>  var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
>
>  instance.invoices.cancel(invoiceId)
> ```
>
> ```python Python theme={null}
>  client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
>  client.invoice.cancel(invoiceId)
> ```
>
> ```ruby Ruby theme={null}
>  require "razorpay"
>  Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
>
>  invoiceId = "inv_1Aa00000000001"
>
>  Razorpay::Invoice.cancel(invoiceId)
> ```
>
> ```go Go theme={null}
>  import ( razorpay "github.com/razorpay/razorpay-go" )
>  client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
>  body, err := client.Invoice.Cancel("<invoiceId>", nil, nil)
> ```
>
> ```csharp .NET theme={null}
>  RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
>  string invoiceId = "inv_Z6t7VFTb9xHeOs";
>
>  Invoice invoice = client.Invoice.Fetch(invoiceId).Cancel();
> ```
>
> ```json Response theme={null}
> {
>   "id": "inv_FHrfRupD2ouKIt",
>   "entity": "invoice",
>   "receipt": "Receipt No. 1",
>   "invoice_number": "Receipt No. 1",
>   "customer_id": "cust_BMB3EwbqnqZ2EI",
>   "customer_details": {
>       "id": "cust_BMB3EwbqnqZ2EI",
>       "name": "<name>",
>       "email": "<email>",
>       "contact": "<phone>",
>       "gstin": null,
>       "billing_address": null,
>       "shipping_address": null,
>       "customer_name": "<name>",
>       "customer_email": "<email>",
>       "customer_contact": "<phone>"
>   },
>   "order_id": "order_FHrfRw4TZU5Q2L",
>   "line_items": [],
>   "payment_id": null,
>   "status": "cancelled",
>   "expire_by": 4102444799,
>   "issued_at": 1595491479,
>   "paid_at": null,
>   "cancelled_at": 1595491488,
>   "expired_at": null,
>   "sms_status": "sent",
>   "email_status": "sent",
>   "date": 1595491479,
>   "terms": null,
>   "partial_payment": false,
>   "gross_amount": 100,
>   "tax_amount": 0,
>   "taxable_amount": 0,
>   "amount": 100,
>   "amount_paid": 0,
>   "amount_due": 100,
>   "currency": "INR",
>   "currency_symbol": "₹",
>   "description": "Registration Link for Gaurav Kumar",
>   "notes": {
>       "note_key 1": "Beam me up Scotty",
>       "note_key 2": "Tea. Earl Gray. Hot."
>   },
>   "comment": null,
>   "short_url": "https://rzp.io/i/QlfexTj",
>   "view_less": true,
>   "billing_start": null,
>   "billing_end": null,
>   "type": "link",
>   "group_taxes_discounts": false,
>   "created_at": 1595491480,
>   "idempotency_key": null
> }
> ```

### Path Parameter

`id` *mandatory*
: `string` The unique identifier for the invoice linked to the registration link that you want to cancel. For example, `inv_1Aa00000000001`.
