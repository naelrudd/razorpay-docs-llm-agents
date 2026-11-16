> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# 1. Create the Authorisation Transaction

> Create an authorisation transaction with Emandate as a payment method.

Available in
🇮🇳 India

You can create an authorisation transaction using [Razorpay APIs](#1-1-using-razorpay-apis) or [Registration Link](#1-2-using-a-registration-link).

## 1.1. Using Razorpay APIs

To create an authorisation transaction using Razorpay APIs, you need to:

1. [Create a Customer](#1-1-1-create-a-customer).
2. [Create an Order](#1-1-2-create-an-order).
3. [Create Authorisation Payment using Razorpay APIs](#1-1-3-create-an-authorisation-payment).

> [!NOTE]
>
> **Handy Tips**
>
> For the Authorisation Payment to be successful in a day (for example, 5th June), you should create an Order and the Authorisation Transaction on the same day (5th June) before 11:59 pm.

### 1.1.1. Create a Customer

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

> [accordion] Request Parameters
>
> `name`
> : `string` The name of the customer. For example, `Gaurav Kumar`.
>
> `email`
> : `string` The email address of the customer. For example, `gaurav.kumar@example.com`.
>
> `contact`
> : `string` The phone number of the customer. For example, `9876543210`.
>
> `fail_existing` *optional*
> : `string` The request throws an exception by default if a customer with the exact details already exists. You can pass an additional parameter `fail_existing` to get the existing customer's details in the response. Possible values:
>
> * `1` (default): If a customer with the same details already exists, throws an error.
> * `0`: If a customer with the same details already exists, fetches details of the existing customer.
>
> `notes` *optional*
> : `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

> [accordion] Response Parameters
>
> `id`
> : `string` The unique identifier of the customer. For example `cust_1Aa00000000001`.
>
> `entity`
> : `string` The name of the entity. Here, it is `customer`.
>
> `name`
> : `string` The name of the customer. For example, `Gaurav Kumar`.
>
> `email`
> : `string` The email address of the customer. For example, `gaurav.kumar@example.com`.
>
> `contact`
> : `string` The phone number of the customer. For example, `9876543210`.
>
> `notes`
> : `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.
>
> `created_at`
> : `integer` A Unix timestamp, at which the customer was created.
>
> You can create an order once you create a customer for the payment authorisation.

### 1.1.2. Create an Order

Use the [Orders API](https://razorpay.com/docs/api/orders.md) to create a unique Razorpay `order_id` that is associated with the authorisation transaction. The following endpoint creates an order.

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

> [accordion] Request Parameters
>
> `amount` *mandatory*
> : `integer` Amount in currency subunits. For emandate, the amount should be `0`.
>
> `currency` *mandatory*
> : `string` The 3-letter ISO currency code for the payment. Currently, we only support `INR`.
>
> `payment_capture` *mandatory*
> : `boolean` Determines whether the payment status should be changed to `captured` automatically or not. Possible values:
>
> * `true`: Payments are captured automatically.
> * `false`: Payments are not captured automatically. You can manually capture payments using the [Manually Capture Payments API](https://razorpay.com/docs/api/payments/capture.md).
>
> `method` *mandatory*
> : `string` The authorisation method. Here, it is `emandate`.
>
> `customer_id` *mandatory*
> : `string` The unique identifier of the customer to be charged. For example, `cust_D0cs04OIpPPU1F`.
>
> `receipt` *optional*
> : `string` A user-entered unique identifier of the order. For example, `rcptid #1`. You should map this parameter to the `order_id` sent by Razorpay.
>
> `notes`*optional*
> : `json object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.
>
> `token`
> : Details related to the authorisation such as max amount and bank account information.
>
> `auth_type` *optional*
> : `string` Emandate type used to make the authorisation payment. Possible values:
>
> * `netbanking`
> * `debitcard`
> * `aadhaar`
>
> `max_amount` *optional*
> : `integer` The maximum amount in paise a customer can be charged in a transaction. Know about the [maximum and default values](https://razorpay.com/docs/payments/recurring-payments/emandate/faqs.md#what-is-the-maximum-amount-which-can-be-debited-from-the-customers).
>
> `expire_at` *optional*
> : `integer` The Unix timestamp to indicate till when you can use the token (authorisation on the payment method) to charge the customer subsequent payments. Defaults to 40 years. The maximum value you can set is 40 years from the current date. Any value beyond this will throw an error.
>
> `notes`*optional*
> : `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.
>
> `bank_account` *optional*
> : Customer's bank account details that should be pre-filled on the checkout.
>
> `account_number` *conditional*
> : `string` Mandatory if the `bank_account` object is sent. Customer's bank account number.
>
> `account_type` *optional*
> : `string` Customer's bank account type. Possible values:
>
> * `savings` (default)
> * `current`
>
> `ifsc_code` *conditional*
> : `string` Mandatory if the `bank_account` object is sent. Customer's bank IFSC. For example `UTIB0000001`.
>
> `beneficiary_name` *conditional*
> : `string` Mandatory if the `bank_account` object is sent. Name of the beneficiary. For example, `Gaurav Kumar`.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > The `beneficiary_name` should be between 4 to 120 characters.

> [accordion] Response Parameters
>
> `id`
> : `string` A unique identifier of the order created. For example `order_1Aa00000000001`.
>
> `entity`
> : `string` The entity that has been created. Here it is `order`.
>
> `amount`
> : `integer` Amount in currency subunits. For emandate, the amount should be `0`.
>
> `amount_paid`
> : `integer` The amount that has been paid.
>
> `amount_due`
> : `integer` The amount that is yet to pay.
>
> `currency`
> : `string` The 3-letter ISO currency code for the payment. Currently, we only support `INR`.
>
> `receipt`
> : `string` A user-entered unique identifier of the order. For example, `rcptid #1`. You should map this parameter to the `order_id` sent by Razorpay.
>
> `status`
> : `string` The status of the order.
>
> `notes`
> : `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.
>
> `created_at`
> : `integer` The Unix timestamp at which the order was created.
>
> `token`
> : Details related to the authorisation such as max amount and bank account information.
>
> `auth_type`
> : `string` Emandate type used to make the authorisation payment. Possible values:
>
> * `netbanking`
> * `debitcard`
> * `aadhaar`
>
> `max_amount`
> : `integer` The maximum amount in paise a customer can be charged in a transaction. Know about the [maximum and default values](https://razorpay.com/docs/payments/recurring-payments/emandate/faqs.md#what-is-the-maximum-amount-which-can-be-debited-from-the-customers).
>
> `expire_at`
> : `integer` The Unix timestamp to indicate till when you can use the token (authorisation on the payment method) to charge the customer subsequent payments. The default value is 10 years for `emandate`. This value can range from the current date to 31-12-2099 (`4102444799`).
>
> `notes`
> : `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.
>
> `bank_account`
> : Customer's bank account details that should be pre-filled on the checkout.
>
> `account_number`
> : `string` Customer's bank account number.
>
> `account_type`
> : `string` Customer's bank account type. Possible values:
>
> * `savings` (default)
> * `current`
>
> `ifsc_code`
> : `string` Customer's bank IFSC. For example `UTIB0000001`.
>
> `beneficiary_name`
> : `string` Name of the beneficiary. For example, `Gaurav Kumar`.

### 1.1.3. Create an Authorisation Payment

Create a payment checkout form for customers to make Authorisation Transaction and register their mandate. You can use the Handler Function or Callback URL.

| Handler Function | Callback URL |
| - | - |
| When you use the handler function, the response object of the successful payment (`razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature`) is submitted to the Checkout Form. You need to collect these and send them to your server. | When you use a Callback URL, the response object of the successful payment (`razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature`) is submitted to the Callback URL. |

> [!WARNING]
>
> **Watch Out!**
>
> * The callback URL is not supported for recurring payments created using the registration link.
> * While handling the first time authorisation payment response, consume the `error_reason` field with value `upi_dummy_payment` and `error_description` field with value `Payment was a dummy payment for one time mandate registration.` to identify successful mandate registration. The parent `error_code` will be `BAD_REQUEST_ERROR`.

```html Checkout with handler functions theme={null}
<button id = "rzp-button1"> Pay </button>
  <script src = "https://checkout.razorpay.com/v1/checkout.js"> </script>
  <script>
    var options = {
      "key": "[YOUR_KEY_ID]",
      "order_id": "order_1Aa00000000001",
      "customer_id": "cust_1Aa00000000001",
      "recurring": true,
      "handler": function (response) {
        alert(response.razorpay_payment_id);
        alert(response.razorpay_order_id);
        alert(response.razorpay_signature);
      },
      "notes":{
          "note_key_1":"September",
          "note_key_2":"Make it so."
      },
      "theme": {
        "color": "#F37254"
      }
    };
    var rzp1 = new Razorpay(options);
    document.getElementById('rzp-button1').onclick = function (e) {
      rzp1.open();
      e.preventDefault();
    }
  </script>
```

```html Manual checkout with Callback URL theme={null}
<button id = "rzp-button1"> Pay </button>
  <script src = "https://checkout.razorpay.com/v1/checkout.js"> </script>
  <script>
    var options = {
      "key": "[YOUR_KEY_ID]",
      "order_id": "order_1Aa00000000001",
      "customer_id": "cust_1Aa00000000001",
      "recurring": true,
      "callback_url": "https://eneqd3r9zrjok.x.pipedream.net/",
      "notes":{
          "note_key_1":"September",
          "note_key_2":"Make it so."
      },
      "theme": {
        "color": "#F37254"
      }
    };
    var rzp1 = new Razorpay(options);
    document.getElementById('rzp-button1').onclick = function (e) {
      rzp1.open();
      e.preventDefault();
    }
  </script>
```

> [accordion] Additional Checkout Fields
>
> `customer_id` *mandatory*
> : `string` Unique identifier of the customer created in the [first step](#1-1-1-create-a-customer).
>
> `order_id` *mandatory*
> : `string` Unique identifier of the  order created in the [second step](#1-1-2-create-an-order).

## 1.2. Using a Registration Link

Registration Link is an alternate way of creating an authorisation transaction. You can create a registration link using the [API](#1-2-1-create-a-registration-link) or [Dashboard](https://razorpay.com/docs/payments/recurring-payments/create.md#1-create-a-registration-link).

* When you create a registration link, an [invoice](https://razorpay.com/docs/payments/invoices) is automatically issued to the customer. They can use this invoice to make the authorisation payment.
* A registration link should always have an order amount (in paise) the customer will be charged when making the authorisation payment. This amount should be `0` in the case of Emandate.
* You can [use Webhooks to get notifications about successful payments](https://razorpay.com/docs/api/payments/recurring-payments/webhooks.md#check-registration-link-status-using-webhooks) against a registration link.

> [!NOTE]
>
> **Handy Tips**
>
> You do not have to create a customer if you choose the registration link method for creating an authorisation transaction.

### 1.2.1. Create a Registration Link

The following endpoint creates a registration link.

`POST /subscription_registration/auth_links`

> [tab] Emandate via Aadhaar
>
> ```bash Request theme={null}
> curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET>
> -X POST https://api.razorpay.com/v1/subscription_registration/auth_links
> -H "Content-Type: application/json" \
> -d '{
>   "customer": {
>     "name": "Gaurav Kumar",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9123456780"
>   },
>   "type": "link",
>   "amount": 0,
>   "currency": "INR",
>   "description": "12 p.m. Meals",
>   "subscription_registration": {
>     "method": "emandate",
>     "auth_type": "aadhaar",
>     "expire_at": 1580480689,
>     "max_amount": 50000,
>     "bank_account": {
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": "11214311215411",
>       "account_type": "savings",
>       "ifsc_code": "HDFC0001233"
>     }
>   },
>   "receipt": "Receipt no. 1",
>   "expire_by": 1880480689,
>   "sms_notify": true,
>   "email_notify": true,
>   "notes": {
>     "note_key 1": "Beam me up Scotty",
>     "note_key 2": "Tea. Earl Gray. Hot."
>   }
> }'
> ```
>
> ```json Response theme={null}
> {
>   "id": "inv_FHrZAOeCuB9HtK",
>   "entity": "invoice",
>   "receipt": "Receipt no. 26",
>   "invoice_number": "Receipt no. 26",
>   "customer_id": "cust_BMB3EwbqnqZ2EI",
>   "customer_details": {
>     "id": "cust_BMB3EwbqnqZ2EI",
>     "name": "Gaurav Kumar",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9123456780",
>     "gstin": null,
>     "billing_address": null,
>     "shipping_address": null,
>     "customer_name": "Gaurav Kumar",
>     "customer_email": "gaurav.kumar@example.com",
>     "customer_contact": "9123456780"
>   },
>   "order_id": "order_FHrZAPOStKd4xS",
>   "line_items": [],
>   "payment_id": null,
>   "status": "issued",
>   "expire_by": 1880480689,
>   "issued_at": 1595491123,
>   "paid_at": null,
>   "cancelled_at": null,
>   "expired_at": null,
>   "sms_status": "pending",
>   "email_status": "pending",
>   "date": 1595491123,
>   "terms": null,
>   "partial_payment": false,
>   "gross_amount": 0,
>   "tax_amount": 0,
>   "taxable_amount": 0,
>   "amount": 0,
>   "amount_paid": 0,
>   "amount_due": 0,
>   "currency": "INR",
>   "currency_symbol": "₹",
>   "description": "test registration link",
>   "notes": {
>     "note_key 1": "Beam me up Scotty",
>     "note_key 2": "Tea. Earl Gray. Hot."
>   },
>   "comment": null,
>   "short_url": "https://rzp.io/i/RllVOmA",
>   "view_less": true,
>   "billing_start": null,
>   "billing_end": null,
>   "type": "link",
>   "group_taxes_discounts": false,
>   "created_at": 1595491123,
>   "idempotency_key": null
> }
> ```

> [tab] Emandate via Netbanking
>
> ```bash Curl theme={null}
> curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET>
> -X POST https://api.razorpay.com/v1/subscription_registration/auth_links
> -H "Content-Type: application/json" \
> -d '{
>   "customer": {
>     "name": "Gaurav Kumar",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9123456780"
>   },
>   "type": "link",
>   "amount": 0,
>   "currency": "INR",
>   "description": "12 p.m. Meals",
>   "subscription_registration": {
>     "method": "emandate",
>     "auth_type": "netbanking",
>     "expire_at": 1580480689,
>     "max_amount": 50000,
>     "bank_account": {
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": "11214311215411",
>       "account_type": "savings",
>       "ifsc_code": "HDFC0001233"
>     }
>   },
>   "receipt": "Receipt no. 1",
>   "expire_by": 1880480689,
>   "sms_notify": true,
>   "email_notify": true,
>   "notes": {
>     "note_key 1": "Beam me up Scotty",
>     "note_key 2": "Tea. Earl Gray. Hot."
>   }
> }'
> ```
>
> ```java Java theme={null}
> RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> JSONObject registrationLinkRequest = new JSONObject();
> JSONObject customer = new JSONObject();
> customer.put("name","Gaurav Kumar");
> customer.put("email","gaurav.kumar@example.com");
> customer.put("contact","9123456780");
> registrationLinkRequest.put("customer", customer);
> registrationLinkRequest.put("type", "link");
> registrationLinkRequest.put("amount", 0);
> registrationLinkRequest.put("currency", "INR");
> registrationLinkRequest.put("description", "12 p.m. Meals");
> JSONObject subscriptionRegistration = new JSONObject();
> subscriptionRegistration.put("method","emandate");
> subscriptionRegistration.put("auth_type","netbanking");
> subscriptionRegistration.put("max_amount",50000);
> subscriptionRegistration.put("expire_at",1609423824);
> JSONObject bankAccount = new JSONObject();
> bankAccount.put("beneficiary_name","Gaurav Kumar");
> bankAccount.put("account_number","11214311215411");
> bankAccount.put("account_type","savings");
> bankAccount.put("ifsc_code","HDFC0001233");
> subscriptionRegistration.put("bank_account",bankAccount);
> registrationLinkRequest.put("subscription_registration", subscriptionRegistration);
> registrationLinkRequest.put("receipt", "Receipt No. 25");
> registrationLinkRequest.put("email_notify", true);
> registrationLinkRequest.put("sms_notify", true);
> registrationLinkRequest.put("expire_by", 1580479824);
> JSONObject notes = new JSONObject();
> notes.put("notes_key_1","Tea, Earl Grey, Hot");
> notes.put("notes_key_2","Tea, Earl Grey… decaf.");
> registrationLinkRequest.put("notes", notes);
>
> Invoice invoice = razorpay.invoices.createRegistrationLink(registrationLinkRequest);
> ```
>
> ```php PHP theme={null}
> $api = new Api($key_id, $secret);
>
> $api->subscription->createSubscriptionRegistration(array('customer'=>array('name'=>'Gaurav Kumar','email'=>'gaurav.kumar@example.com','contact'=>'9123456780'),'type'=>'link','amount'=>100,'currency'=>'INR','description'=>'Registration Link for Gaurav Kumar','subscription_registration'=>array('method'=>'emandate','max_amount'=>'500','expire_at'=>'1634215992'),'receipt'=>'Receipt No. 5','email_notify'=>true,'sms_notify'=>true,'expire_by'=>1634215992,'notes' => array('note_key 1' => 'Beam me up Scotty','note_key 2' => 'Tea. Earl Gray. Hot.')));
> ```
>
> ```javascript Node.js theme={null}
> var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
>
> instance.subscriptions.createRegistrationLink({
>   customer: {
>     name: "Gaurav Kumar",
>     email: "gaurav.kumar@example.com",
>     contact: 9123456780
>   },
>   type: "link",
>   amount: 0,
>   currency: "INR",
>   description: "12 p.m. Meals",
>   subscription_registration: {
>     method: "emandate",
>     auth_type: "netbanking",
>     expire_at: 1580480689,
>     max_amount: 50000,
>     bank_account: {
>       beneficiary_name: "Gaurav Kumar",
>       account_number: 11214311215411,
>       account_type: "savings",
>       ifsc_code: "HDFC0001233"
>     }
>   },
>   receipt: "Receipt no. 1",
>   expire_by: 1880480689,
>   sms_notify: true,
>   email_notify: true,
>   notes: {
>     "note_key 1": "Beam me up Scotty",
>     "note_key 2": "Tea. Earl Gray. Hot."
>   }
> })
> ```
>
> ```python Python theme={null}
> client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
> client.registration_link.create({
>     'customer': {'name': 'Gaurav Kumar',
>                 'email': 'gaurav.kumar@example.com',
>                 'contact': 9123456780},
>     'type': 'link',
>     'amount': 0,
>     'currency': 'INR',
>     'description': '12 p.m. Meals',
>     'subscription_registration': {
>         'method': 'emandate',
>         'auth_type': 'netbanking',
>         'expire_at': 1580480689,
>         'max_amount': 50000,
>         'bank_account': {
>             'beneficiary_name': 'Gaurav Kumar',
>             'account_number': 11214311215411,
>             'account_type': 'savings',
>             'ifsc_code': 'HDFC0001233',
>             },
>         },
>     'receipt': 'Receipt no. 1',
>     'expire_by': 1880480689,
>     'sms_notify': True,
>     'email_notify': True,
>     'notes': {'note_key 1': 'Beam me up Scotty',
>               'note_key 2': 'Tea. Earl Gray. Hot.'}
>     })
> ```
>
> ```ruby Ruby theme={null}
> require "razorpay"
> Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
>
> para_attr = {
>   "customer": {
>     "name": "Gaurav Kumar",
>     "email": "gaurav.kumar@example.com",
>     "contact": 9123456780
>   },
>   "type": "link",
>   "amount": 0,
>   "currency": "INR",
>   "description": "12 p.m. Meals",
>   "subscription_registration": {
>     "method": "emandate",
>     "auth_type": "netbanking",
>     "expire_at": 1580480689,
>     "max_amount": 50000,
>     "bank_account": {
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": 11214311215411,
>       "account_type": "savings",
>       "ifsc_code": "HDFC0001233"
>     }
>   },
>   "receipt": "Receipt no. #12",
>   "expire_by": 1880480689,
>   "sms_notify": 1,
>   "email_notify": 1,
>   "notes": {
>     "note_key 1": "Beam me up Scotty",
>     "note_key 2": "Tea. Earl Gray. Hot."
>   }
> }
>
> Razorpay::SubscriptionRegistration.create(para_attr)
> ```
>
> ```go Go theme={null}
> import ( razorpay "github.com/razorpay/razorpay-go" )
> client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
> data:= map[string]interface{}{
>   "customer": map[string]interface{}{
>     "name": "Gaurav Kumar",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9123456780",
>   },
>   "type": "link",
>   "amount": 100,
>   "currency": "INR",
>   "description": "12 p.m. Meals",
>   "subscription_registration": map[string]interface{}{
>     "method": "emandate",
>     "auth_type": "netbanking",
>     "expire_at": 1580480689,
>     "max_amount": 50000,
>     "bank_account": map[string]interface{}{
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": "11214311215411",
>       "account_type": "savings",
>       "ifsc_code": "HDFC0001233",
>     },
>   },
>   "receipt": "Receipt no. 25",
>   "expire_by": 1880480689,
>   "sms_notify": true,
>   "email_notify": true,
>   "notes": map[string]interface{}{
>     "note_key 1": "Beam me up Scotty",
>     "note_key 2": "Tea. Earl Gray. Hot.",
>   },
> }
>
> body, err := client.Invoice.CreateRegistrationLink(data, nil)
> ```
>
> ```csharp .NET theme={null}
> RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> Dictionary<string, object> registrationLinkRequest = new Dictionary<string, object>();
> Dictionary<string, object> customer = new Dictionary<string, object>();
> customer.Add("name","Gaurav Kumar");
> customer.Add("email","gaurav.kumar@example.com");
> customer.Add("contact","9123456780");
> registrationLinkRequest.Add("customer", customer);
> registrationLinkRequest.Add("type", "link");
> registrationLinkRequest.Add("amount", 0);
> registrationLinkRequest.Add("currency", "INR");
> registrationLinkRequest.Add("description", "12 p.m. Meals");
> Dictionary<string, object> subscriptionRegistration = new Dictionary<string, object>();
> subscriptionRegistration.Add("method","emandate");
> subscriptionRegistration.Add("auth_type","netbanking");
> subscriptionRegistration.Add("max_amount",50000);
> subscriptionRegistration.Add("expire_at",1609423824);
> Dictionary<string, object> bankAccount = new Dictionary<string, object>();
> bankAccount.Add("beneficiary_name","Gaurav Kumar");
> bankAccount.Add("account_number","11214311215411");
> bankAccount.Add("account_type","savings");
> bankAccount.Add("ifsc_code","HDFC0001233");
> subscriptionRegistration.Add("bank_account",bankAccount);
> registrationLinkRequest.Add("subscription_registration", subscriptionRegistration);
> registrationLinkRequest.Add("receipt", "Receipt No. 1");
> registrationLinkRequest.Add("email_notify", true);
> registrationLinkRequest.Add("sms_notify", true);
> registrationLinkRequest.Add("expire_by", 1580479824);
> Dictionary<string, object> notes = new Dictionary<string, object>();
> notes.Add("notes_key_1","Tea, Earl Grey, Hot");
> notes.Add("notes_key_2","Tea, Earl Grey… decaf.");
> registrationLinkRequest.Add("notes", notes);
>
> Invoice invoice = client.Invoice.CreateRegistrationLink(registrationLinkRequest);
> ```
>
> ```json Response theme={null}
> {
>   "id": "inv_FHrY6tDtVP2dHg",
>   "entity": "invoice",
>   "receipt": "Receipt no. 25",
>   "invoice_number": "Receipt no. 25",
>   "customer_id": "cust_BMB3EwbqnqZ2EI",
>   "customer_details": {
>     "id": "cust_BMB3EwbqnqZ2EI",
>     "name": "Gaurav Kumar",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9123456780",
>     "gstin": null,
>     "billing_address": null,
>     "shipping_address": null,
>     "customer_name": "Gaurav Kumar",
>     "customer_email": "gaurav.kumar@example.com",
>     "customer_contact": "9123456780"
>   },
>   "order_id": "order_FHrY6tiC2y7NNN",
>   "line_items": [],
>   "payment_id": null,
>   "status": "issued",
>   "expire_by": 1880480689,
>   "issued_at": 1595491063,
>   "paid_at": null,
>   "cancelled_at": null,
>   "expired_at": null,
>   "sms_status": "pending",
>   "email_status": "pending",
>   "date": 1595491063,
>   "terms": null,
>   "partial_payment": false,
>   "gross_amount": 0,
>   "tax_amount": 0,
>   "taxable_amount": 0,
>   "amount": 0,
>   "amount_paid": 0,
>   "amount_due": 0,
>   "currency": "INR",
>   "currency_symbol": "₹",
>   "description": "test registration link",
>   "notes": {
>     "note_key 1": "Beam me up Scotty",
>     "note_key 2": "Tea. Earl Gray. Hot."
>   },
>   "comment": null,
>   "short_url": "https://rzp.io/i/DxEcNtR",
>   "view_less": true,
>   "billing_start": null,
>   "billing_end": null,
>   "type": "link",
>   "group_taxes_discounts": false,
>   "created_at": 1595491063,
>   "idempotency_key": null
> }
> ```

> [tab] Emandate via Debit Card
>
> ```bash Request theme={null}
> curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET>
> -X POST https://api.razorpay.com/v1/subscription_registration/auth_links
> -H "Content-Type: application/json" \
> -d '{
>   "customer": {
>     "name": "Gaurav Kumar",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9123456780"
>   },
>   "type": "link",
>   "amount": 0,
>   "currency": "INR",
>   "description": "12 p.m. Meals",
>   "subscription_registration": {
>     "method": "emandate",
>     "auth_type": "debitcard",
>     "expire_at": 1580480689,
>     "max_amount": 50000,
>     "bank_account": {
>       "beneficiary_name": "Gaurav Kumar",
>       "account_number": "11214311215411",
>       "account_type": "savings",
>       "ifsc_code": "HDFC0001233"
>     }
>   },
>   "receipt": "Receipt no. 1",
>   "expire_by": 1880480689,
>   "sms_notify": true,
>   "email_notify": true,
>   "notes": {
>     "note_key 1": "Beam me up Scotty",
>     "note_key 2": "Tea. Earl Gray. Hot."
>   }
> }'
> ```
>
> ```json Response theme={null}
> {
>   "id": "inv_FHrZAOeCuB9HtK",
>   "entity": "invoice",
>   "receipt": "Receipt no. 26",
>   "invoice_number": "Receipt no. 26",
>   "customer_id": "cust_BMB3EwbqnqZ2EI",
>   "customer_details": {
>     "id": "cust_BMB3EwbqnqZ2EI",
>     "name": "Gaurav Kumar",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9123456780",
>     "gstin": null,
>     "billing_address": null,
>     "shipping_address": null,
>     "customer_name": "Gaurav Kumar",
>     "customer_email": "gaurav.kumar@example.com",
>     "customer_contact": "9123456780"
>   },
>   "order_id": "order_FHrZAPOStKd4xS",
>   "line_items": [],
>   "payment_id": null,
>   "status": "issued",
>   "expire_by": 1880480689,
>   "issued_at": 1595491123,
>   "paid_at": null,
>   "cancelled_at": null,
>   "expired_at": null,
>   "sms_status": "pending",
>   "email_status": "pending",
>   "date": 1595491123,
>   "terms": null,
>   "partial_payment": false,
>   "gross_amount": 0,
>   "tax_amount": 0,
>   "taxable_amount": 0,
>   "amount": 0,
>   "amount_paid": 0,
>   "amount_due": 0,
>   "currency": "INR",
>   "currency_symbol": "₹",
>   "description": "test registration link",
>   "notes": {
>     "note_key 1": "Beam me up Scotty",
>     "note_key 2": "Tea. Earl Gray. Hot."
>   },
>   "comment": null,
>   "short_url": "https://rzp.io/i/RllVOmA",
>   "view_less": true,
>   "billing_start": null,
>   "billing_end": null,
>   "type": "link",
>   "group_taxes_discounts": false,
>   "created_at": 1595491123,
>   "idempotency_key": null
> }
> ```

> [accordion] Request Parameters
>
> `customer`
> : `object` Details of the customer to whom the registration link is sent.
>
> `name` *mandatory*
> : `string` Customer's name.
>
> `email` *mandatory*
> : `string` Customer's email address.
>
> `contact`*mandatory*
> : `integer` Customer's contact number.
>
> `type` *mandatory*
> : `string` In this case, the value is `link`.
>
> `amount` *mandatory*
> : `integer` The payment amount in the smallest currency sub-unit.
>
> `currency` *mandatory*
> : `string` The 3-letter ISO currency code for the payment.
>
> `description` *mandatory*
> : `string` A description that appears on the hosted page.
>
> `subscription_registration`
> : Details of the authorisation payment.
>
> `method` *mandatory*
> : `string` The authorization method. Here, it is `emandate`.
>
> `auth_type` *optional*
> : `string` Possible values:
>
> * `netbanking`
> * `debitcard`
> * `aadhaar`
>
> `max_amount` *optional*
> : `integer` The maximum amount, in paise, a customer can be charged in a transaction. Know about [maximum and default values](https://razorpay.com/docs/payments/recurring-payments/emandate/faqs.md#what-is-the-maximum-amount-which-can-be-debited-from-the-customers).
>
> `expire_at` *optional*
> : `integer` The Unix timestamp indicates till when you can use the token (authorization on the payment method) to charge the customer their subsequent payments. Defaults to `40 years`. The maximum value you can set is 40 years from the current date. Any value beyond this will throw an error.
>
> `bank_account` *optional*
> : The customer's bank account details.
>
> `beneficiary_name` *conditional*
> : `string` Mandatory if the `bank_account` object is sent. Name on the beneficiary. For example `Gaurav Kumar`.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > The `beneficiary_name` should be between 4 to 120 characters.
>
> `account_number` *conditional*
> : `string` Mandatory if the `bank_account` object is sent. Customer's bank account number. For example `11214311215411`.
>
> `account_type` *optional*
> : `string` Customer's bank account type. Possible values:
>
> * `savings` (default)
> * `current`
>
> `ifsc_code` *conditional*
> : `string` Mandatory if the `bank_account` object is sent. Customer's bank IFSC. For example `HDFC0000001`.
>
> `sms_notify` *optional*
> : `boolean` Indicates if SMS notifications are to be sent by Razorpay. Possible values:
>
> * `true` (default): Notifications are sent by Razorpay .
> * `false`: Notifications are not sent by Razorpay.
>
> `email_notify` *optional*
> : `boolean` Indicates if email notifications are to be sent by Razorpay. Possible values:
>
> * `true` (default): Notifications are sent by Razorpay .
> * `false`: Notifications are not sent by Razorpay.
>
> `expire_by` *optional*
> : `integer` The Unix timestamp indicates the expiry of the registration link.
>
> `receipt` *optional*
> : `string` A unique identifier entered by you for the order. For example, `Receipt No. 1`. You should map this parameter to the `order_id` sent by Razorpay.
>
> `notes` *optional*
> : `object` This is a key-value pair that is used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

> [accordion] Response Parameters
>
> `id`
> : `string` The unique identifier of the invoice.
>
> `entity`
> : `string` The entity that has been created. Here, it is `invoice`.
>
> `receipt`
> : `string` A user-entered unique identifier of the invoice.
>
> `invoice_number`
> : `string` Unique number you added for internal reference.
>
> `customer_id`
> : `string` The unique identifier of the customer. For example, `cust_BMB3EwbqnqZ2EI`.
>
> `customer_details`
> : `object` Details of the customer.
>
> `id`
> : `string` The unique identifier associated with the customer to whom the invoice has been issued.
>
> `name`
> : `string` The customer's name.
>
> `email`
> : `string` The customer's email address.
>
> `contact`
> : `integer` The customer's phone number.
>
> `billing_address`
> : `string` Details of the customer's billing address.
>
> `shipping_address`
> : `string` Details of the customer's shipping address.
>
> `order_id`
> : `string` The unique identifier of the order associated with the invoice.
>
> `line_items`
> : `string` Details of the line item that is billed in the invoice. Maximum of 50 line items are allowed.
>
> `payment_id`
> : `string` Unique identifier of a payment made against the invoice.
>
> `status`
> : `string` The status of the invoice. Possible values:
>
> * `draft`
> * `issued`
> * `partially_paid`
> * `paid`
> * `cancelled`
> * `expired`
> * `deleted`
>
> `expire_by`
> : `integer` The Unix timestamp at which the invoice will expire.
>
> `issued_at`
> : `integer` The Unix timestamp at which the invoice was issued to the customer.
>
> `paid_at`
> : `integer` The Unix timestamp at which the payment was made.
>
> `cancelled_at`
> : `integer` The Unix timestamp at which the invoice was cancelled.
>
> `expired_at`
> : `integer` The Unix timestamp at which the invoice expired.
>
> `sms_status`
> : `string` The delivery status of the SMS notification for the invoice sent to the customer. Possible values:
>
> * `pending`
> * `sent`
>
> `email_status`
> : `string` The delivery status of the email notification for the invoice sent to the customer. Possible values:
>
> * `pending`
> * `sent`
>
> `date`
> : `integer` Timestamp, in Unix format, that indicates the issue date of the invoice.
>
> `terms`
> : `string` Any terms to be included in the invoice. Maximum of 2048 characters.
>
> `partial_payment`
> : `boolean` Indicates whether the customer can make a partial payment on the invoice. Possible values:
>
> * `true`:  The customer can make partial payments.
> * `false` (default): The customer cannot make partial payments.
>
> `amount`
> : `integer` Amount to be paid using the invoice. Must be in the smallest unit of the currency. For example, if the amount to be received from the customer is ₹299.95, pass the value as `29995`.
>
> `amount_paid`
> : `integer` Amount paid by the customer against the invoice.
>
> `amount_due`
> : `integer` The remaining amount to be paid by the customer for the issued invoice.
>
> `currency`
> : `string` The currency associated with the invoice.
>
> `description`
> : `string`  A brief description of the invoice.
>
> `notes`
> : `object` Any custom notes added to the invoice. Maximum of 2048 characters.
>
> `short_url`
> : `string` The short URL that is generated. This is the link that can be shared with the customer to receive payments.
>
> `type`
> : `string` Here, it is `invoice`.
>
> `comment`
> : `string` Any comments to be added in the invoice. Maximum of 2048 characters.

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

> [accordion] Path Parameters
>
> `id`*mandatory*
> : `string` The unique identifier of the invoice linked to the registration link for which you want to send the notification. For example, `inv_1Aa00000000001`.
>
> `medium` *mandatory*
> : `string` Determines through which medium you want to resend the notification. Possible values:
>
> * `sms`
> * `email`

> [accordion] Response Parameter
>
> `success`
> : `boolean` Indicates whether the notifications were sent successfully. Possible values:
>
> * `true`: The notifications were successfully sent via SMS, email or both.
> * `false`: The notifications were not sent.

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

> [accordion] Path Parameter
>
> `id` *mandatory*
> : `string` The unique identifier for the invoice linked to the registration link that you want to cancel. For example, `inv_1Aa00000000001`.

> [accordion] Response Parameters
>
> `id`
> : `string` The unique identifier of the invoice.
>
> `entity`
> : `string` The entity that has been created. Here, it is `invoice`.
>
> `receipt`
> : `string` A user-entered unique identifier of the invoice.
>
> `invoice_number`
> : `string` Unique number you added for internal reference.
>
> `customer_id`
> : `string` The unique identifier of the customer. For example, `cust_BMB3EwbqnqZ2EI`.
>
> `customer_details`
> : `object` Details of the customer.
>
> `id`
> : `string` The unique identifier associated with the customer to whom the invoice has been issued.
>
> `name`
> : `string` The customer's name.
>
> `email`
> : `string` The customer's email address.
>
> `contact`
> : `integer` The customer's phone number.
>
> `billing_address`
> : `string` Details of the customer's billing address.
>
> `shipping_address`
> : `string` Details of the customer's shipping address.
>
> `order_id`
> : `string` The unique identifier of the order associated with the invoice.
>
> `line_items`
> : `string` Details of the line item that is billed in the invoice. Maximum of 50 line items are allowed.
>
> `payment_id`
> : `string` Unique identifier of a payment made against the invoice.
>
> `status`
> : `string` The status of the invoice. Possible values:
>
> * `draft`
> * `issued`
> * `partially_paid`
> * `paid`
> * `cancelled`
> * `expired`
> * `deleted`
>
> `expire_by`
> : `integer` The Unix timestamp at which the invoice will expire.
>
> `issued_at`
> : `integer` The Unix timestamp at which the invoice was issued to the customer.
>
> `paid_at`
> : `integer` The Unix timestamp at which the payment was made.
>
> `cancelled_at`
> : `integer` The Unix timestamp at which the invoice was cancelled.
>
> `expired_at`
> : `integer` The Unix timestamp at which the invoice expired.
>
> `sms_status`
> : `string` The delivery status of the SMS notification for the invoice sent to the customer. Possible values:
>
> * `pending`
> * `sent`
>
> `email_status`
> : `string` The delivery status of the email notification for the invoice sent to the customer. Possible values:
>
> * `pending`
> * `sent`
>
> `date`
> : `integer` Timestamp, in Unix format, that indicates the issue date of the invoice.
>
> `terms`
> : `string` Any terms to be included in the invoice. Maximum of 2048 characters.
>
> `partial_payment`
> : `boolean` Indicates whether the customer can make a partial payment on the invoice. Possible values:
>
> * `true`:  The customer can make partial payments.
> * `false` (default): The customer cannot make partial payments.
>
> `amount`
> : `integer` Amount to be paid using the invoice. Must be in the smallest unit of the currency. For example, if the amount to be received from the customer is ₹299.95, pass the value as `29995`.
>
> `amount_paid`
> : `integer` Amount paid by the customer against the invoice.
>
> `amount_due`
> : `integer` The remaining amount to be paid by the customer for the issued invoice.
>
> `currency`
> : `string` The currency associated with the invoice.
>
> `description`
> : `string`  A brief description of the invoice.
>
> `notes`
> : `object` Any custom notes added to the invoice. Maximum of 2048 characters.
>
> `short_url`
> : `string` The short URL that is generated. This is the link that can be shared with the customer to receive payments.
>
> `type`
> : `string` Here, it is `invoice`.
>
> `comment`
> : `string` Any comments to be added in the invoice. Maximum of 2048 characters.
