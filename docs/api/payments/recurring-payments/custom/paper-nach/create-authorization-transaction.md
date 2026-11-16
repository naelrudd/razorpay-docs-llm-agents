> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# 1. Create the Authorisation Transaction

> Learn how to create an authorisation transaction with method NACH so customers can set up authorization by signing a physical NACH form.

Available in
🇮🇳 India

The flow to complete an authorisation transaction using paper NACH is a little different from the regular recurring payment flow. The flow when using paper NACH is:

1. Create a customer.

2. Create an order by passing the `customer_id` and method `nach`. When you do this, Razorpay generates a NACH form with the customer information pre-filled and ready to sign.

3. The customer signs the form. The customer can obtain the form in one of the following ways:
   * You can download the form from the Dashboard and send it to the customer.
   * Download from the Hosted page (in the case of registration links).

4. The signed form is uploaded to Razorpay. This can be done in one of the following ways:
   * Using custom Checkout page created from Razorpay APIs.
   * Hosted page (in the case of registration links).
   * The customer can send you the form and you can upload the form for the customer. The acceptable image formats and size are:
     * jpeg
     * jpg
     * png
     * Maximum accepted size is 6 MB.

Once the details are validated, the authorisation transaction is completed and a token is generated. You can charge your customer as per your business model once the token status changes to `confirmed`.

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

### 1.1.2. Create an Order

```bash Curl theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-X POST https://api.razorpay.com/v1/orders \
-H "Content-Type: application/json" \
-d '{
  "amount":0,
  "currency":"INR",
  "method":"nach",
  "customer_id": "cust_1Aa00000000001",
  "receipt":"Receipt No. 1",
  "notes": {
    "notes_key_1": "Beam me up Scotty",
    "notes_key_2": "Engage"
  },
  "token":{
    "auth_type":"physical",
    "max_amount":10000000,
    "expire_at":2709971120,
    "notes": {
      "notes_key_1": "Tea, Earl Grey, Hot",
      "notes_key_2": "Tea, Earl Grey… decaf."
    },
    "bank_account":{
      "account_number":"11214311215411",
      "ifsc_code":"HDFC0000001",
      "beneficiary_name":"Gaurav Kumar",
      "account_type":"savings"
    },
    "nach":{
      "form_reference1":"Recurring Payment for Gaurav Kumar",
      "form_reference2":"Method Paper NACH",
      "description":"Paper NACH Gaurav Kumar"
    }
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject orderRequest = new JSONObject();
orderRequest.put("amount", 0);
orderRequest.put("currency", "INR");
orderRequest.put("customer_id", "cust_JDdNazagOgg9Ig");
orderRequest.put("method", "nach");
orderRequest.put("receipt", "receipt#1");
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
orderRequest.put("notes", notes);
JSONObject token = new JSONObject();
token.put("auth_type","physical");
token.put("max_amount","10000000");
token.put("expire_at","2709971120");
JSONObject tokenNotes = new JSONObject();
tokenNotes.put("notes_key_1","Tea, Earl Grey, Hot");
tokenNotes.put("notes_key_2","Tea, Earl Grey… decaf.");
token.put("notes",tokenNotes);
orderRequest.put("token", token);
JSONObject bankAccount = new JSONObject();
bankAccount.put("beneficiary_name","Gaurav Kumar");
bankAccount.put("account_number","11214311215411");
bankAccount.put("account_type","savings");
bankAccount.put("ifsc_code","HDFC0001233");
token.put("bank_account",bankAccount);
JSONObject nach = new JSONObject();
nach.put("form_reference1","Recurring Payment for Gaurav Kumar");
nach.put("form_reference2","Method Paper NACH");
nach.put("description","Paper NACH Gaurav Kumar");
token.put("nach",nach);

Order order = razorpay.orders.create(orderRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->order->create(array('amount' => 0,'currency' => 'INR','method' => 'nach','customer_id' => 'cust_1Aa00000000001','receipt' => 'Receipt No. 1',  'notes' => array('notes_key_1' => 'Beam me up Scotty','notes_key_2' => 'Engage'),'token' => array('auth_type' => 'physical','max_amount' => 10000000,'expire_at' => 2709971120,'notes' => array('notes_key_1' => 'Tea, Earl Grey, Hot','notes_key_2' => 'Tea, Earl Grey… decaf.'),'bank_account' => array('account_number' => '11214311215411','ifsc_code' => 'HDFC0000001','beneficiary_name' => 'Gaurav Kumar','account_type' => 'savings'),'nach' => array('form_reference1' => 'Recurring Payment for Gaurav Kumar','form_reference2' => 'Method Paper NACH','description' => 'Paper NACH Gaurav Kumar'))));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.orders.create({
  amount: 0,
  currency: "INR",
  method: "nach",
  customer_id: "cust_1Aa00000000001",
  receipt: "Receipt No. 1",
  notes: {
    notes_key_1: "Beam me up Scotty",
    notes_key_2: "Engage"
  },
  token: {
    auth_type: "netbanking",
    max_amount: 9999900,
    expire_at: 4102444799,
    notes: {
      notes_key_1: "Tea, Earl Grey, Hot",
      notes_key_2: "Tea, Earl Grey… decaf."
    },
    bank_account: {
      beneficiary_name: "Gaurav Kumar",
      account_number: "1121431121541121",
      account_type: "savings",
      ifsc_code: "HDFC0000001"
    }
  }
})
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.order.create({
    'amount': 0,
    'currency': 'INR',
    'method': 'nach',
    'customer_id': 'cust_1Aa00000000001',
    'receipt': 'Receipt No. 1',
    'notes': {'notes_key_1': 'Beam me up Scotty',
              'notes_key_2': 'Engage'},
    'token': {
        'auth_type': 'netbanking',
        'max_amount': 9999900,
        'expire_at': 4102444799,
        'notes': {'notes_key_1': 'Tea, Earl Grey, Hot',
                  'notes_key_2': 'Tea, Earl Grey... decaf.'},
        'bank_account': {
            'beneficiary_name': 'Gaurav Kumar',
            'account_number': 1121431121541121,
            'account_type': 'savings',
            'ifsc_code': 'HDFC0000001'
            }
        }
    })
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {
  "amount": 0,
  "currency": "INR",
  "method": "nach",
  "customer_id": "cust_1Aa00000000001",
  "receipt": "Receipt No. 1",
  "notes": {
    "notes_key_1": "Beam me up Scotty",
    "notes_key_2": "Engage"
  },
  "token": {
    "auth_type": "netbanking",
    "max_amount": 9999900,
    "expire_at": 4102444799,
    "notes": {
      "notes_key_1": "Tea, Earl Grey, Hot",
      "notes_key_2": "Tea, Earl Grey… decaf."
    },
    "bank_account": {
      "beneficiary_name": "Gaurav Kumar",
      "account_number": 1121431121541121,
      "account_type": "savings",
      "ifsc_code": "HDFC0000001"
    }
  }
}

Razorpay::Order.create(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
  "amount":0,
  "currency":"INR",
  "method":"nach",
  "customer_id": "cust_1Aa00000000001",
  "receipt":"Receipt No. 1",
  "notes": map[string]interface{}{
    "notes_key_1": "Beam me up Scotty",
    "notes_key_2": "Engage",
  },
  "token":map[string]interface{}{
    "auth_type":"physical",
    "max_amount":10000000,
    "expire_at":2709971120,
    "notes": map[string]interface{}{
      "notes_key_1": "Tea, Earl Grey, Hot",
      "notes_key_2": "Tea, Earl Grey… decaf.",
    },
    "bank_account":map[string]interface{}{
      "account_number":"11214311215411",
      "ifsc_code":"HDFC0000001",
      "beneficiary_name":"Gaurav Kumar",
      "account_type":"savings",
    },
    "nach":map[string]interface{}{
      "form_reference1":"Recurring Payment for Gaurav Kumar",
      "form_reference2":"Method Paper NACH",
      "description":"Paper NACH Gaurav Kumar",
    },
  },
}
body, err := client.Order.Create(data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> orderRequest = new Dictionary<string, object>();
orderRequest.Add("amount", 0);
orderRequest.Add("currency", "INR");
orderRequest.Add("customer_id", "cust_JDdNazagOgg9Ig");
orderRequest.Add("method", "nach");
orderRequest.Add("receipt", "receipt#1");
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("notes_key_1","Tea, Earl Grey, Hot");
notes.Add("notes_key_2","Tea, Earl Grey… decaf.");
orderRequest.Add("notes", notes);
Dictionary<string, object> token = new Dictionary<string, object>();
token.Add("auth_type","physical");
token.Add("max_amount","10000000");
token.Add("expire_at","2709971120");
Dictionary<string, object> tokenNotes = new Dictionary<string, object>();
tokenNotes.Add("notes_key_1","Tea, Earl Grey, Hot");
tokenNotes.Add("notes_key_2","Tea, Earl Grey… decaf.");
token.Add("notes",tokenNotes);
orderRequest.Add("token", token);
Dictionary<string, object> bankAccount = new Dictionary<string, object>();
bankAccount.Add("beneficiary_name","Gaurav Kumar");
bankAccount.Add("account_number","11214311215411");
bankAccount.Add("account_type","savings");
bankAccount.Add("ifsc_code","HDFC0001233");
token.Add("bank_account",bankAccount);
Dictionary<string, object> nach = new Dictionary<string, object>();
nach.Add("form_reference1","Recurring Payment for Gaurav Kumar");
nach.Add("form_reference2","Method Paper NACH");
nach.Add("description","Paper NACH Gaurav Kumar");
token.Add("nach",nach);

Order order = client.Order.Create(orderRequest);
```

```json Success Response theme={null}
{
   "id":"order_1Aa00000000001",
   "entity":"order",
   "amount":0,
   "amount_paid":0,
   "amount_due":0,
   "currency":"INR",
   "receipt":"rcptid #10",
   "offer_id":null,
   "offers":{
      "entity":"collection",
      "count":0,
      "items":[
         
      ]
   },
   "status":"created",
   "attempts":0,
   "notes":{
      "notes_key_1":"Beam me up Scotty",
      "notes_key_2":"Engage"
   },
   "created_at":1579775420,
   "token":{
      "method":"nach",
      "notes":{
         "notes_key_1":"Tea, Earl Grey, Hot",
         "notes_key_2":"Tea, Earl Grey… decaf."
      },
      "recurring_status":null,
      "failure_reason":null,
      "currency":"INR",
      "max_amount":10000000,
      "auth_type":"physical",
      "expire_at":1580480689,
      "nach":{
         "create_form":true,
         "form_reference1":"Recurring Payment for Gaurav Kumar",
         "form_reference2":"Method Paper NACH",
         "prefilled_form":"https://rzp.io/i/bitw",
         "upload_form_url":"https://rzp.io/i/gts",
         "description":"Paper NACH Gaurav Kumar"
      },
      "bank_account":{
         "ifsc":"HDFC0000001",
         "bank_name":"HDFC Bank",
         "name":"Gaurav Kumar",
         "account_number":"11214311215411",
         "account_type":"savings",
         "beneficiary_email":"gaurav.kumar@example.com",
         "beneficiary_mobile":"9876543210"
      },
      "first_payment_amount":0
   }
}
```

```json Failure Response theme={null}
{
   "error":{
      "code":"BAD_REQUEST_ERROR",
      "description":"The id provided does not exist",
      "source":"business",
      "step":"payment_initiation",
      "reason":"input_validation_failed",
      "metadata":{
         
      }
   }
}
```

### Request Parameters

`amount` *mandatory*
: `integer` Amount in currency subunits. For Paper NACH, the amount has to be `0`.

`currency` *mandatory*
: `string` The 3-letter ISO currency code for the payment. Currently, we only support `INR`.

`method` *mandatory*
: `string` The authorization method. In this case, the value will be `nach`.

`customer_id` *mandatory*
: `string` The unique identifier of the customer, who is to be charged. For example, `cust_D0cs04OIpPPU1F`.

`receipt` *optional*
: `string` A user-entered unique identifier for the order. For example, `Receipt No. 1`. This parameter should be mapped to the `order_id` sent by Razorpay.

`notes`*optional*
: `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

`token`
: Details related to the authorization such as max amount, bank account information and NACH information.

`auth_type` *mandatory*
: `string` In this case, it will be `physical`.

`bank_account`
: Customer's bank account details that will be printed on the NACH form.

`account_number`*mandatory*
: `string` Customer's bank account number. For example, `11214311215411`.

`ifsc_code`*mandatory*
: `string` Customer's bank IFSC. For example, `UTIB0000001`.

`beneficiary_name`*mandatory*
: `string` Customer's name. For example, `Gaurav Kumar`.

`account_type` *optional*
: `string` Customer's bank account type. Possible values:

* `savings` (default)
* `current`

`max_amount` *optional*
: `integer` Use to set the maximum amount per debit request. Know about [maximum and default values](https://razorpay.com/docs/payments/recurring-payments/paper-nach/faqs.md#is-there-a-limit-on-the-debit-amount-in-physical-nach).

`expire_at` *optional*
: `integer` Timestamp, in Unix, that specifies when the registration link should expire. The default value is 30 years.

`nach`
: Additional information to be printed on the NACH form that your customer will sign.

`form_reference1` *optional*
: `string` A user-entered reference that appears on the NACH form.

`form_reference2` *optional*
: `string` A user-entered reference that appears on the NACH form.

`description` *optional*
: `string` A user-entered description that appears on the hosted page. For example, `Form for Gaurav Kumar.`

`notes`*optional*
: `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

### 1.1.3. Create an Authorisation Payment

Follow these steps to create authorisation transaction:

1. Download the Paper NACH form and send it to the customers.
2. Ask the customers to fill the form and
   * Upload it via the Checkout.
   * Send it to you and you can upload it from the Dashboard.
3. Upload the received form via create NACH File API.

#### 1.1.3.1 Upload the NACH File via Checkout

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

```html Custom checkout with handler functions theme={null}
<script type="text/javascript" src="https://checkout.razorpay.com/v1/razorpay.js"></script>
<script src= "https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"> </script>
  <body><button id="btn" style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">Pay</button>
<script>
  const btn = document.querySelector("#btn");
                var razorpay = new Razorpay({
                  key: "<YOUR_TEST_KEY>",
                  image: "https://i.imgur.com/n5tjHFD.jpg"
                });
          razorpay.once("ready", function(response) {
            console.log(response.methods);
          })
          var data = {
      "amount": 100, // in currency subunits. Here 1000 = 1000 paise, which equals to ₹10
      "currency": "INR",// Default is INR. We support more than 90 currencies.
      "email": "gaurav.kumar@example.com",
      "contact": "9123456780",
      "notes": {
        "address": "Ground Floor, SJR Cyber, Laskar Hosur Road, Bengaluru",
      },
      "order_id": "order_00000000000001",
      "customer_id": "cust_00000000000001",
      "recurring": true,
      "method": "nach",
  	  "bank": "HDFC",
  	  "auth_type": "physical",
  	  "bank_account[name]": "Gaurav Kumar",
  	  "bank_account[account_number]": "1121431121541121",
  	  "bank_account[account_type]": "savings",
  	  "bank_account[ifsc]": "HDFC0000001"
    };
      btn.addEventListener("click", function(){ // has to be placed within user initiated context, such as click, in order for popup to open.
      razorpay.createPayment(data);
      razorpay.on("payment.success", function(resp) {
        alert(resp.razorpay_payment_id),
        alert(resp.razorpay_order_id),
        alert(resp.razorpay_signature)}); // will pass payment ID, order ID and Razorpay signature to success handler.
      razorpay.on("payment.error", function(resp){alert(resp.error.description)}); // will pass error object to error handler
    })
  </script>
</body>
```

```html Custom checkout with Callback URL theme={null}
<script type="text/javascript" src="https://checkout.razorpay.com/v1/razorpay.js"></script>
<script src= "https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"> </script>
  <body><button id="btn" style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">Pay</button>
<script>
  const btn = document.querySelector("#btn");
                var razorpay = new Razorpay({
                  key: "<YOUR_TEST_KEY>",
                  image: "https://i.imgur.com/n5tjHFD.jpg"
                });
          razorpay.once("ready", function(response) {
            console.log(response.methods);
          })
          var data = {
       "callback_url": "www.example-callback-url.com",
       "amount": 100, // in currency subunits. Here 1000 = 1000 paise, which equals to ₹10
      "currency": "INR",// Default is INR. We support more than 90 currencies.
      "email": "gaurav.kumar@example.com",
      "contact": "9123456780",
      "notes": {
        "address": "Ground Floor, SJR Cyber, Laskar Hosur Road, Bengaluru",
      },
      "order_id": "order_00000000000001",
      "customer_id": "cust_00000000000001",
      "recurring": true,
      "method": "nach",
  	  "bank": "HDFC",
  	  "auth_type": "physical",
  	  "bank_account[name]": "Gaurav Kumar",
  	  "bank_account[account_number]": "1121431121541121",
  	  "bank_account[account_type]": "savings",
  	  "bank_account[ifsc]": "HDFC0000001"
    };
      btn.addEventListener("click", function(){ // has to be placed within user initiated context, such as click, in order for popup to open.
      razorpay.createPayment(data);
    })
  </script>
</body>
```

#### Additional Checkout Fields

`customer_id` *mandatory*
: `string` Unique identifier of the customer created in the [first step](#1-1-1-create-a-customer).

`order_id` *mandatory*
: `string` Unique identifier of the  order created in the [second step](#1-1-2-create-an-order).

`recurring` *mandatory*
: `boolean` Determines whether the recurring is enabled or not. Possible values:

* `true`: Recurring payment is enabled.
* `false`: Recurring payment is not enabled.

#### 1.1.3.2 Upload the NACH File via API

> [!NOTE]
>
> **Feature Request**
>
> This feature is available only on request. It is not available by default. Raise a request on our [Support Portal](https://razorpay.com/support/#request) to get this feature enabled.

You can use the Create NACH File API to upload the signed NACH forms you collect from your customers. On successful verification, we submit the form to NPCI and return a success/failure response to you.

Use the below endpoint to upload the completed NACH file.

`POST /payments/create/nach/file`

```bash Request theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-X POST 'https://api.razorpay.com/v1/payments/create/nach/file' \
-H "Content-Type: multipart/form-data" \
-F 'order_id=order_FoLdZrq6QGKUWg' \
-F 'file=@/Users/your_name/sample_uploaded.jpeg' // file path
```

```json Successful Response theme={null}
{
  "razorpay_payment_id": "pay_FjDn43bvssCqEM",
  "razorpay_order_id": "order_FoLdZrq6QGKUWg",
  "razorpay_signature": "f13775ea8a91e9bf229b9fdba3ad783f7ff2bdbce1c35e87a69ae7418808da04"
}
```

```json Error Response theme={null}
{
"error": {
  "code": "BAD_REQUEST_ERROR",
  "description": "file size exceeds limit",
  "field": null,
  "source": "customer",
  "step": "form_upload",
  "reason": "file size exceeds limit",
  "metadata": {
    "payment_id": null,
    "order_id": "order_FoLdZrq6QGKUWg"
    }
  }
}
```

#### Error Reasons

To learn about errors, refer to the FAQ [Upload the NACH File](https://razorpay.com/docs/payments/recurring-payments/paper-nach/faqs.md) section.

## 1.2. Using a Registration Link

Registration Link is an alternate way of creating an authorisation transaction. You can create a registration link using the [API](#1-2-1-create-a-registration-link) or [Dashboard](https://razorpay.com/docs/payments/recurring-payments/create.md#1-create-a-registration-link).

> [!NOTE]
>
> **Handy Tips**
>
> * You do not have to create a customer if you choose the registration link method for creating an authorisation transaction.
> * You can [use Webhooks to get notifications about successful payments](https://razorpay.com/docs/api/payments/recurring-payments/webhooks.md#check-registration-link-status-using-webhooks) against a registration link.

When you create a registration link, an [invoice](https://razorpay.com/docs/payments/invoices) is automatically issued to the customer. They can use this invoice to make the authorisation payment.

In the case of Paper NACH, the order amount must be `0`.

### 1.2.1. Create a Registration Link

The following endpoint creates a registration link for recurring payments.

`POST /subscription_registration/auth_links`

```bash Curl theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET>
-X POST https://api.razorpay.com/v1/subscription_registration/auth_links
-H "Content-Type: application/json" \
-d '{
  "customer":{
    "name":"Gaurav Kumar",
    "email":"gaurav.kumar@example.com",
    "contact":"9123456780"
  },
  "amount":0,
  "currency":"INR",
  "type":"link",
  "description":"12 p.m. Meals",
  "subscription_registration":{
    "method":"nach",
    "auth_type":"physical",
    "bank_account":{
      "beneficiary_name":"Gaurav Kumar",
      "account_number":"11214311215411",
      "account_type":"savings",
      "ifsc_code":"HDFC0001233"
    },
    "nach":{
      "form_reference1":"Recurring Payment for Gaurav Kumar",
      "form_reference2":"Method Paper NACH"
    },
    "expire_at":1947483647,
    "max_amount":50000
  },
  "receipt":"Receipt No. 1",
  "sms_notify":true,
  "email_notify":true,
  "expire_by":1647483647,
  "notes":{
    "note_key 1":"Beam me up Scotty",
    "note_key 2":"Tea. Earl Gray. Hot."
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject registrationLinkRequest = new JSONObject();
JSONObject customer = new JSONObject();
customer.put("name","Gaurav Kumar");
customer.put("email","gaurav.kumar@example.com");
customer.put("contact","9123456780");
registrationLinkRequest.put("customer", customer);
registrationLinkRequest.put("type", "link");
registrationLinkRequest.put("amount", 0);
registrationLinkRequest.put("currency", "INR");
registrationLinkRequest.put("description", "12 p.m. Meals");
JSONObject subscriptionRegistration = new JSONObject();
subscriptionRegistration.put("method","nach");
subscriptionRegistration.put("auth_type","physical");
subscriptionRegistration.put("max_amount",50000);
subscriptionRegistration.put("expire_at",1609423824);
JSONObject bankAccount = new JSONObject();
bankAccount.put("beneficiary_name","Gaurav Kumar");
bankAccount.put("account_number","11214311215411");
bankAccount.put("account_type","savings");
bankAccount.put("ifsc_code","HDFC0001233");
JSONObject nach = new JSONObject();
nach.put("form_reference1","Recurring Payment for Gaurav Kumar");
nach.put("form_reference2","Method Paper NACH");
subscriptionRegistration.put("bank_account",bankAccount);
subscriptionRegistration.put("nach",nach);
registrationLinkRequest.put("subscription_registration", subscriptionRegistration);
registrationLinkRequest.put("receipt", "Receipt No. #1");
registrationLinkRequest.put("email_notify", true);
registrationLinkRequest.put("sms_notify", true);
registrationLinkRequest.put("expire_by", 1580479824);
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
registrationLinkRequest.put("notes", notes);

Invoice invoice = razorpay.invoices.createRegistrationLink(registrationLinkRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->subscription->createSubscriptionRegistration(array('customer' => array('name' => 'Gaurav Kumar','email' => 'gaurav.kumar@example.com','contact' => '9123456780'),'amount' => 0,'currency' => 'INR','type' => 'link','description' => '12 p.m. Meals','subscription_registration' => array('method' => 'nach','auth_type' => 'physical','bank_account' => array('beneficiary_name' => 'Gaurav Kumar','account_number' => '11214311215411','account_type' => 'savings','ifsc_code' => 'HDFC0001233'),'nach' => array('form_reference1' => 'Recurring Payment for Gaurav Kumar','form_reference2' => 'Method Paper NACH'),'expire_at' => 1947483647,'max_amount' => 50000),'receipt' => 'Receipt No. 1','sms_notify' => true,'email_notify' => true,'expire_by' => 1647483647,'notes' => array('note_key 1' => 'Beam me up Scotty','note_key 2' => 'Tea. Earl Gray. Hot.')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.createRecurringPayment({
  customer: {
    name: "Gaurav Kumar",
    email: "gaurav.kumar@example.com",
    contact: 9123456780
  },
  amount: 0,
  currency: "INR",
  type: "link",
  description: "12 p.m. Meals",
  subscription_registration: {
    method: "nach",
    auth_type: "physical",
    bank_account: {
      beneficiary_name: "Gaurav Kumar",
      account_number: 11214311215411,
      account_type: "savings",
      ifsc_code: "HDFC0001233"
    },
    nach: {
      form_reference1: "Recurring Payment for Gaurav Kumar",
      form_reference2: "Method Paper NACH"
    },
    expire_at: 1947483647,
    max_amount: 50000
  },
  receipt: "Receipt No. 1",
  sms_notify: true,
  email_notify: true,
  expire_by: 1647483647,
  notes: {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  }
})
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.registration_link.create({
    'customer': {'name': 'Gaurav Kumar',
                 'email': 'gaurav.kumar@example.com',
                 'contact': 9123456780},
    'amount': 0,
    'currency': 'INR',
    'type': 'link',
    'description': '12 p.m. Meals',
    'subscription_registration': {
        'method': 'nach',
        'auth_type': 'physical',
        'bank_account': {
            'beneficiary_name': 'Gaurav Kumar',
            'account_number': 11214311215411,
            'account_type': 'savings',
            'ifsc_code': 'HDFC0001233',
            },
        'nach': {'form_reference1': 'Recurring Payment for Gaurav Kumar'
                 , 'form_reference2': 'Method Paper NACH'},
        'expire_at': 1947483647,
        'max_amount': 50000,
        },
    'receipt': 'Receipt No. 1',
    'sms_notify': True,
    'email_notify': True,
    'expire_by': 1647483647,
    'notes': {'note_key 1': 'Beam me up Scotty',
              'note_key 2': 'Tea. Earl Gray. Hot.'}
    })
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {
  "customer": {
    "name": "Gaurav Kumar",
    "email": "gaurav.kumar@example.com",
    "contact": 9123456780
  },
  "amount": 0,
  "currency": "INR",
  "type": "link",
  "description": "12 p.m. Meals",
  "subscription_registration": {
    "method": "nach",
    "auth_type": "physical",
    "bank_account": {
      "beneficiary_name": "Gaurav Kumar",
      "account_number": 11214311215411,
      "account_type": "savings",
      "ifsc_code": "HDFC0001233"
    },
    "nach": {
      "form_reference1": "Recurring Payment for Gaurav Kumar",
      "form_reference2": "Method Paper NACH"
    },
    "expire_at": 1947483647,
    "max_amount": 50000
  },
  "receipt": "Receipt No. 1",
  "sms_notify": 1,
  "email_notify": 1,
  "expire_by": 1647483647,
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  }
}

Razorpay::SubscriptionRegistration.create(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "customer":map[string]interface{}{
    "name":"Gaurav Kumar",
    "email":"gaurav.kumar@example.com",
    "contact":"9123456780",
  },
  "amount":0,
  "currency":"INR",
  "type":"link",
  "description":"12 p.m. Meals",
  "subscription_registration":map[string]interface{}{
    "method":"nach",
    "auth_type":"physical",
    "bank_account":map[string]interface{}{
      "beneficiary_name":"Gaurav Kumar",
      "account_number":"11214311215411",
      "account_type":"savings",
      "ifsc_code":"HDFC0001233",
    },
    "nach":map[string]interface{}{
      "form_reference1":"Recurring Payment for Gaurav Kumar",
      "form_reference2":"Method Paper NACH",
    },
    "expire_at":1947483647,
    "max_amount":50000,
  },
  "receipt":"Receipt No. 1",
  "sms_notify":true,
  "email_notify":true,
  "expire_by":1647483647,
  "notes":map[string]interface{}{
    "note_key 1":"Beam me up Scotty",
    "note_key 2":"Tea. Earl Gray. Hot.",
  },
}

body, err := client.Invoice.CreateRegistrationLink(data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> registrationLinkRequest = new Dictionary<string, object>();
Dictionary<string, object> customer = new Dictionary<string, object>();
customer.Add("name","Gaurav Kumar");
customer.Add("email","gaurav.kumar@example.com");
customer.Add("contact","9123456780");
registrationLinkRequest.Add("customer", customer);
registrationLinkRequest.Add("type", "link");
registrationLinkRequest.Add("amount", 0);
registrationLinkRequest.Add("currency", "INR");
registrationLinkRequest.Add("description", "12 p.m. Meals");
Dictionary<string, object> subscriptionRegistration = new Dictionary<string, object>();
subscriptionRegistration.Add("method","nach");
subscriptionRegistration.Add("auth_type","physical");
subscriptionRegistration.Add("max_amount",50000);
subscriptionRegistration.Add("expire_at",1609423824);
Dictionary<string, object> bankAccount = new Dictionary<string, object>();
bankAccount.Add("beneficiary_name","Gaurav Kumar");
bankAccount.Add("account_number","11214311215411");
bankAccount.Add("account_type","savings");
bankAccount.Add("ifsc_code","HDFC0001233");
Dictionary<string, object> nach = new Dictionary<string, object>();
nach.Add("form_reference1","Recurring Payment for Gaurav Kumar");
nach.Add("form_reference2","Method Paper NACH");
subscriptionRegistration.Add("bank_account",bankAccount);
subscriptionRegistration.Add("nach",nach);
registrationLinkRequest.Add("subscription_registration", subscriptionRegistration);
registrationLinkRequest.Add("receipt", "Receipt No. #111");
registrationLinkRequest.Add("email_notify", true);
registrationLinkRequest.Add("sms_notify", true);
registrationLinkRequest.Add("expire_by", 1580479824);
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("notes_key_1","Tea, Earl Grey, Hot");
notes.Add("notes_key_2","Tea, Earl Grey… decaf.");
registrationLinkRequest.Add("notes", notes);

Invoice invoice = client.Invoice.CreateRegistrationLink(registrationLinkRequest);
```

```json Response theme={null}
{
    "id": "inv_FHrZiAubEzDdaq",
    "entity": "invoice",
    "receipt": "Receipt No. 1",
    "invoice_number": "Receipt No. 1",
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
    "order_id": "order_FHrZiBOkWHZPOp",
    "line_items": [],
    "payment_id": null,
    "status": "issued",
    "expire_by": 1647483647,
    "issued_at": 1595491154,
    "paid_at": null,
    "cancelled_at": null,
    "expired_at": null,
    "sms_status": "sent",
    "email_status": "sent",
    "date": 1595491154,
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
    "description": "12 p.m. Meals",
    "notes": {
        "note_key 1": "Beam me up Scotty",
        "note_key 2": "Tea. Earl Gray. Hot."
    },
    "comment": null,
    "short_url": "https://rzp.io/i/bzDYbNg",
    "view_less": true,
    "billing_start": null,
    "billing_end": null,
    "type": "link",
    "group_taxes_discounts": false,
    "created_at": 1595491154,
    "idempotency_key": null,
    "token": {
        "method": "nach",
        "notes": {
            "note_key 1": "Beam me up Scotty",
            "note_key 2": "Tea. Earl Gray. Hot."
        },
        "recurring_status": null,
        "failure_reason": null,
        "currency": "INR",
        "max_amount": 50000,
        "auth_type": "physical",
        "expire_at": 1947483647,
        "nach": {
            "create_form": true,
            "form_reference1": "Recurring Payment for Gaurav Kumar",
            "form_reference2": "Method Paper NACH",
            "prefilled_form": "https://rzp.io/i/exdIzYN",
            "upload_form_url": "https://rzp.io/i/bzDYbNg",
            "description": "12 p.m. Meals"
        },
        "bank_account": {
            "ifsc": "HDFC0001233",
            "bank_name": "HDFC Bank",
            "name": "Gaurav Kumar",
            "account_number": "11214311215411",
            "account_type": "savings",
            "beneficiary_email": "gaurav.kumar@example.com",
            "beneficiary_mobile": "9123456780"
        },
        "first_payment_amount": 0
    },
    "nach_form_url": "https://rzp.io/i/exdIzYN"
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
: `string` In this case, it will be `nach`.

`auth_type` *mandatory*
: `string` In this case, it will be `physical`.

`bank_account`
: The customer's bank account details.

`beneficiary_name` *mandatory*
: `string` Name on the bank account. For example, `Gaurav Kumar`.

`account_number` *mandatory*
: `integer` Customer's bank account number. For example, `11214311215411`.

`account_type` *mandatory*
: `string` Customer's bank account type. Possible values:

* `savings` (default)
* `current`

`ifsc_code` *mandatory*
: `string` Customer's bank IFSC. For example, `HDFC0000001`.

`nach`
: Additional information to be printed on the NACH form that your customer will sign.

`form_reference1` *optional*
: `string` A user-entered reference that appears on the NACH form.

`form_reference2` *optional*
: `string` A user-entered reference that appears on the NACH form.

`max_amount` *optional*
: `integer` Use to set the maximum amount per debit request. Know about [maximum and default values](https://razorpay.com/docs/payments/recurring-payments/paper-nach/faqs.md#is-there-a-limit-on-the-debit-amount-in-physical-nach).

`expire_at` *optional*
: `integer` The timestamp, in Unix format, till when you can use the token (authorization on the payment method) to charge the customer subsequent payments.

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

Use the below endpoint to cancel a registration link.

`POST /invoices/:id/cancel`

> [!NOTE]
>
> **Note**
>
> You can only cancel registration link that is in the `issued` state.

```bash Request theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET>
-X POST https://api.razorpay.com/v1/invoices/inv_1Aa00000000001/cancel
```

```json Response theme={null}
{
  "id": "inv_FHrZiAubEzDdaq",
  "entity": "invoice",
  "receipt": "Receipt No. 1",
  "invoice_number": "Receipt No. 1",
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
  "order_id": "order_FHrZiBOkWHZPOp",
  "line_items": [],
  "payment_id": null,
  "status": "cancelled",
  "expire_by": 1647483647,
  "issued_at": 1595491154,
  "paid_at": null,
  "cancelled_at": 1595491339,
  "expired_at": null,
  "sms_status": "sent",
  "email_status": "sent",
  "date": 1595491154,
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
  "description": "12 p.m. Meals",
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  },
  "comment": null,
  "short_url": "https://rzp.io/i/bzDYbNg",
  "view_less": true,
  "billing_start": null,
  "billing_end": null,
  "type": "link",
  "group_taxes_discounts": false,
  "created_at": 1595491154,
  "idempotency_key": null,
  "token": {
    "method": "nach",
    "notes": {
      "note_key 1": "Beam me up Scotty",
      "note_key 2": "Tea. Earl Gray. Hot."
    },
    "recurring_status": null,
    "failure_reason": null,
    "currency": "INR",
    "max_amount": 50000,
    "auth_type": "physical",
    "expire_at": 1947483647,
    "nach": {
      "create_form": true,
      "form_reference1": "Recurring Payment for Gaurav Kumar",
      "form_reference2": "Method Paper NACH",
      "prefilled_form": "https://rzp.io/i/tSYd5aV",
      "upload_form_url": "https://rzp.io/i/bzDYbNg",
      "description": "12 p.m. Meals"
    },
    "bank_account": {
      "ifsc": "HDFC0001233",
      "bank_name": "HDFC Bank",
      "name": "Gaurav Kumar",
      "account_number": "11214311215411",
      "account_type": "savings",
      "beneficiary_email": "gaurav.kumar@example.com",
      "beneficiary_mobile": "9123456780"
    },
    "first_payment_amount": 0
  },
  "nach_form_url": "https://rzp.io/i/tSYd5aV"
}
```

### Path Parameter

`id` *mandatory*
: `string` The unique identifier for the invoice linked to the registration link that you want to cancel. For example, `inv_1Aa00000000001`.
