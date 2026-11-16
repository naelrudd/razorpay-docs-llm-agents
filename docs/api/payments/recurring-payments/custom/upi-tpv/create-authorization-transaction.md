> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# 1. Create the Authorisation Transaction

> Learn how to create an authorisation transaction for upi.

Available in
🇮🇳 India

You can create an authorisation transaction using [Razorpay APIs](#1-1-using-razorpay-apis) or [Registration Link](#1-2-using-a-registration-link).

## 1.1 Using Razorpay APIs

To create an authorisation transaction using Razorpay APIs, you need to:

1. [Create a Customer](#1-1-1-create-a-customer).
2. [Create an Order](#1-1-2-create-an-order).
3. [Create Authorisation Payment using Razorpay APIs](#1-1-3-create-an-authorisation-payment).

> [!NOTE]
>
> **Handy Tips**
>
> For the Authorisation Payment to be successful in a day (for example, 5th June), you should create an Order and the Authorisation Transaction on the same day (5th June) before 11:59 pm.

### 1.1.1 Create a Customer

Razorpay links recurring tokens to customers via a unique identifier. This unique identifier for the customer is generated using the Customer API.

You can create customers with basic details such as `email` and `contact` and use them for various Razorpay offerings. Know more about [Customers](https://razorpay.com/docs/api/customers.md).

You can create a customer using the below endpoint.

`POST /customers`

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/customers \
-H "Content-Type: application/json" \
-d '{
  "name": "Gaurav Kumar",
  "email": "gaurav.kumar@example.com",
  "contact": "9123456780",
  "fail_existing": "0",
  "notes":{
    "note_key_1": "September",
    "note_key_2": "Make it so."
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject customerRequest = new JSONObject();
customerRequest.put("name","Gaurav Kumar");
customerRequest.put("contact","9123456780");
customerRequest.put("email","gaurav.kumar@example.com");
customerRequest.put("fail_existing", "0");
customerRequest.put("gstin","29XAbbA4369J1PA");
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
customerRequest.put("notes",notes);

Customer customer = razorpay.customers.create(customerRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.customer.create({
    'name': 'Gaurav Kumar',
    'email': 'gaurav.kumar@example.com',
    'contact': '9123456780',
    'fail_existing': '0',
    'notes': {'note_key_1': 'September', 'note_key_2': 'Make it so.'}
    })
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
    "name": "Gaurav Kumar",
    "contact": 9123456780,
    "email": "gaurav.kumar@example.com",
    "fail_existing": "0",
    "notes": map[string]interface{}{
        "notes_key_1": "Tea, Earl Grey, Hot",
        "notes_key_2": "Tea, Earl Grey… decaf.",
    },
}
body, err := client.Customer.Create(data, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->customer->create(array('name' => 'Gaurav Kumar', 'email' => 'gaurav.kumar@example.com','contact'=>'9123456780','notes'=> array('notes_key_1'=> 'Tea, Earl Grey, Hot','notes_key_2'=> 'Tea, Earl Grey… decaf'));
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> options = new Dictionary<string,object>();

options.Add("name", "Gaurav Kumar"); 
options.Add("contact", "9123456780"); 
options.Add("email", "gaurav.kumar@example.com"); 
options.Add("fail_existing", "0"); 

Customer customer = Customer.Create(options);
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {
  "name": "Gaurav Kumar",
  "contact": 9123456780,
  "email": "gaurav.kumar@example.com",
  "fail_existing": "0",
  "gstin": "29XAbbA4369J1PA",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
}

Razorpay::Customer.create(para_attr)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.customers.create({
  name: "Gaurav Kumar",
  contact: 9123456780,
  email: "gaurav.kumar@example.com",
  fail_existing: "0",
  gstin: "29XAbbA4369J1PA",
  notes: {
    notes_key_1: "Tea, Earl Grey, Hot",
    notes_key_2: "Tea, Earl Grey… decaf."
  }
})
```

```json Response theme={null}
{
   "id":"cust_1Aa00000000001",
   "entity":"customer",
   "name":"Gaurav Kumar",
   "email":"gaurav.kumar@example.com",
   "contact":"9123456780",
   "gstin":null,
   "notes":{
      "note_key_1":"September",
      "note_key_2":"Make it so."
   },
   "created_at ":1234567890
}
```

Once a customer is created, you can create an order for the authorization of the payment.

### Request Parameters

`name` *mandatory*
: `string` The customer's name. For example, `Gaurav Kumar`.

`email ` *mandatory*
: `string` The customer's email address. For example, `gaurav.kumar@example.com`.

`contact ` *mandatory*
: `string` The customer's phone number. For example, `9876543210`.

`fail_existing` *optional*
: `string` The request throws an exception by default if a customer with the exact details already exists. You can pass an additional parameter `fail_existing` to get the existing customer's details in the response. Possible values:

* `1` (default): If a customer with the same details already exists, throws an error.
* `0`: If a customer with the same details already exists, fetches details of the existing customer.

`notes` *optional*
: `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

### 1.1.2. Create an Order

Use the [Orders API](https://razorpay.com/docs/api/orders.md) to create a unique Razorpay `order_id` that is associated with the authorisation transaction. The following endpoint creates an order.

`POST /orders`

> [!NOTE]
>
> **Handy Tips**
>
> The subsequent payment frequency is displayed on your customer's PSP. They can select the required frequency while registering for the mandate.

The Orders API allows you to create a unique Razorpay `order_id`, for example, `order_1Aa00000000001`, that would be tied to the authorisation transaction. Refer to our detailed [Order documentation](https://razorpay.com/docs/payments/orders) for more details.

Use the below endpoint to create an order.

`POST /orders`

You can create a payment against the `order_id` once it is generated.

```bash Request theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-X POST https://api.razorpay.com/v1/orders \
-H "Content-Type: application/json" \
-d '{
  "amount": 100,
  "currency": "INR",
  "customer_id": "cust_4xbQrmEoA5WJ01",
  "method": "upi",
  "payment_capture": true,
  "token": {
    "max_amount": 200000,
    "expire_at": 2709971120,
    "frequency": "monthly"
  },
  "bank_account":{
      "account_number":"123456789012345",
      "name":"Gaurav Kumar",
      "ifsc":"HDFC0000053"
   },
  "receipt": "Receipt No. 1",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
}'
```

```json Success Response theme={null}
{
  "id": "order_1Aa00000000002",
  "entity": "order",
  "amount": 100,
  "amount_paid": 0,
  "amount_due": 100,
  "currency": "INR",
  "receipt": "Receipt No. 1",
  "offer_id": null,
  "status": "created",
  "attempts": 0,
  "bank_account":{
      "account_number":"123456789012345",
      "name":"Gaurav Kumar",
      "ifsc":"HDFC0000053"
   },
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
    }
  "created_at": 1565172642
}
```

```json Failure Response theme={null}
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

### Request Parameters

`amount` *mandatory*
: `integer` Amount, in paise.

`currency` *mandatory*
: `string` The 3-letter ISO currency code for the payment. Currently, we only support `INR`.

`customer_id` *mandatory*
: `string` The unique identifier of the customer. For example, `cust_4xbQrmEoA5WJ01`.

`method` *mandatory*
: `string` Payment method for the authorisation transaction. Here, the value should be `upi`.

`receipt` *optional*
: `string` Unique identifier for the order entered by you. For example, `Receipt No. 1`. This parameter should be mapped to the `order_id` sent by Razorpay.

`description` *optional*
: `string` A description of the mandate that will be displayed to the customer in their UPI app. This helps the customer understand what they are subscribing to. Keep it under 50 characters and avoid special characters. For example, `Monthly Pro subscription`.

`notes`*optional*
: `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

`token`
: Details related to the authorization such as max amount, frequency and expiry information.

`max_amount` *mandatory*
: `integer` The maximum amount that can be debited in a single charge.

| MCC | Category | Min Value | Max Value |
| - | - | - | - |
| 6211 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
| 6300 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
| 7322 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
| 6529 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
| 5960 | Services | `100` (₹1) | `20000000` (₹2,00,000) |

For other categories and MCCs, the minimum value is `100` (₹1) and maximum value is 9999900 (₹99,999).

> [!NOTE]
>
> **Best Practices**
>
> Set the `max_amount` as close to the actual debit amount as possible. For example, if the expected debit amount is ₹99-₹299, setting the `max_amount` to ₹5,000 may cause the customer to drop off due to trust issues. A realistic `max_amount` builds customer trust while allowing flexibility for variable debits.

`expire_at` *mandatory*
: `integer` The Unix timestamp that indicates when the authorisation transaction must expire. The default value is 10 years and the maximum value allowed is 30 years.

`frequency` *mandatory*
: `string` The frequency at which you can charge your customer. Possible values:

* `daily`
* `weekly`
* `fortnightly`
* `bimonthly`
* `monthly`
* `quarterly`
* `half_yearly`
* `yearly`
* `as_presented`

`bank_account` *mandatory*
: Details of the bank account of the customer.

`account_number` *mandatory*
: `integer` The bank account number of the customer. For example, `123456789012345`.

`name` *mandatory*
: `string` The name of the bank account holder.

`ifsc` *mandatory*
: The IFSC of the bank. For example, `HDFC0000053`.

### 1.1.3. Create an Authorisation Payment

Integrate with Razorpay Custom Checkout using the code given below to create an authorisation payment.

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

```html Custom Checkout with handler functions theme={null}
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
      "amount": 300, // in currency subunits. Here 1000 = 1000 paise, which equals to ₹10
      "currency": "INR",// Default is INR. We support more than 90 currencies.
      "email": "gaurav.kumar@example.com",
      "contact": "9123456780",
      "notes": {
        "address": "Ground Floor, SJR Cyber, Laskar Hosur Road, Bengaluru",
      },
      "order_id": "order_00000000000001",
      "customer_id": "cust_00000000000001",
      "recurring": "1",
      "method": "upi",
      "upi":
        {
          "vpa": "gauravkumar@somebank",
          "flow": "collect"
        }// Applicable only for exempted businesses. UPI Collect is deprecated for all others effective 28 Feb 2026.
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
      "amount": 300, // in currency subunits. Here 1000 = 1000 paise, which equals to ₹10
      "currency": "INR",// Default is INR. We support more than 90 currencies.
      "email": "gaurav.kumar@example.com",
      "contact": "9123456780",
      "notes": {
        "address": "Ground Floor, SJR Cyber, Laskar Hosur Road, Bengaluru",
      },
      "order_id": "order_00000000000001",
      "customer_id": "cust_00000000000001",
      "recurring": "1",
      "method": "upi",
      "upi":
        {
          "vpa": "gauravkumar@somebank",
          "flow": "collect"
        }// Applicable only for exempted businesses. UPI Collect is deprecated for all others effective 28 Feb 2026.
    };
      btn.addEventListener("click", function(){ // has to be placed within user initiated context, such as click, in order for popup to open.
      razorpay.createPayment(data);
    })
  </script>
</body>
```

### Additional Checkout Fields

`customer_id` *mandatory*
: `string` Unique identifier of the customer created in the [first step](#1-1-1-create-a-customer).

`order_id` *mandatory*
: `string` Unique identifier of the  order created in the [second step](#1-1-2-create-an-order).

`recurring` *mandatory*
: `string` Possible values:

* `1`: Recurring payment is enabled.
* `preferred`: Use this when you want to support **recurring payments** and **one-time payment** in the same flow.

## 1.2. Using a Registration Link

Registration Link is an alternate way of creating an authorisation transaction. You can create a registration link using the [API](#1-2-1-create-a-registration-link) or [Dashboard](https://razorpay.com/docs/payments/recurring-payments/create.md#1-create-a-registration-link).

> [!NOTE]
>
> **Handy Tips**
>
> * You do not have to create a customer if you choose the registration link method for creating an authorisation transaction.
> * You can [use Webhooks to get notifications about successful payments](https://razorpay.com/docs/api/payments/recurring-payments/webhooks.md#check-registration-link-status-using-webhooks) against a registration link.

When you create a registration link, an [invoice](https://razorpay.com/docs/payments/invoices) is automatically issued to the customer. They can use this invoice to make the authorisation payment.

A registration link must always have the amount (in paise) that the customer will be charged when making the authorisation payment. For UPI, the amount must be a minimum of `₹1`.

### 1.2.1. Create a Registration Link

The following endpoint creates a registration link.

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
   "type":"link",
   "amount":"100",
   "currency":"INR",
   "description":"Registration Link for Gaurav Kumar",
   "subscription_registration":{
      "method":"upi",
      "max_amount":"500",
      "expire_at":4102444799,
      "frequency":"monthly",
      "bank_account":{
         "account_number":"123456789012345",
         "name":"Gaurav Kumar",
         "ifsc_code":"HDFC0000053"
      }
   },
   "receipt":"Receipt No. 23",
   "email_notify":true,
   "sms_notify":true,
   "expire_by":4102444799,
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
registrationLinkRequest.put("amount", 100);
registrationLinkRequest.put("currency", "INR");
registrationLinkRequest.put("description", "Registration Link for Gaurav Kumar");
JSONObject subscriptionRegistration = new JSONObject();
subscriptionRegistration.put("method","upi");
subscriptionRegistration.put("max_amount",50000);
subscriptionRegistration.put("expire_at",1609423824);
subscriptionRegistration.put("frequency","monthly");
JSONObject bank_account = new JSONObject();
bank_account.put("account_number","123456789012345"); 
bank_account.put("name","Gaurav Kumar");
bank_account.put("ifsc_code","HDFC0000053");
registrationLinkRequest.put("subscription_registration", subscriptionRegistration);
registrationLinkRequest.put("receipt", "Receipt No. #112");
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

$api->subscription->createSubscriptionRegistration(array('customer'=>array('name'=>'Gaurav Kumar','email'=>'gaurav.kumar@example.com','contact'=>'9123456780'),'type'=>'link','amount'=>100,'currency'=>'INR','description'=>'Registration Link for Gaurav Kumar','subscription_registration'=>array('method'=>'upi','max_amount'=>'500','expire_at'=>'1634215992',bank_account' => array('account_number' => 123456789012345, 'name' => Gaurav Kumar, 'ifsc_code' => 'HDFC0000053')),'receipt'=>'Receipt No. 5','email_notify'=>true,'sms_notify'=>true,'expire_by'=>1634215992,'notes' => array('note_key 1' => 'Beam me up Scotty','note_key 2' => 'Tea. Earl Gray. Hot.')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.subscriptions.createRegistrationLink({
  customer: {
    name: "Gaurav Kumar",
    email: "gaurav.kumar@example.com",
    contact: 9123456780
  },
  type: "link",
  amount: 100,
  currency: "INR",
  description: "Registration Link for Gaurav Kumar",
  subscription_registration: {
    method: "upi",
    max_amount: 500,
    expire_at: 1634215992,
    bank_account: {
        account_number: 123456789012345,
        name: "Gaurav Kumar",
        ifsc_code: "HDFC0000053"
    }
  },
  receipt: "Receipt No. 5",
  email_notify: true,
  sms_notify: true,
  expire_by: 1634215992,
  notes: {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  }
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
  "type": "link",
  "amount": 100,
  "currency": "INR",
  "description": "Registration Link for Gaurav Kumar",
  "subscription_registration": {
    "method": "upi",
    "max_amount": 500,
    "expire_at": 1634215992,
    "bank_account": {
        "account_number": 123456789012345,
        "name": "Gaurav Kumar",
        "ifsc_code": "HDFC0000053"
    }
  },
  "receipt": "Receipt No. 5",
  "email_notify": 1,
  "sms_notify": 1,
  "expire_by": 1634215992,
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  }
}
Razorpay::SubscriptionRegistration.create(para_attr)
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.registration_link.create({
   "customer":{
      "name":"Gaurav Kumar",
      "email":"gaurav.kumar@example.com",
      "contact":9123456780
   },
   "type":"link",
   "amount":100,
   "currency":"INR",
   "description":"12 p.m. Meals",
   "subscription_registration":{
      "method":"upi",
      "expire_at":1580480689,
      "max_amount":500,
      "bank_account": {
        "account_number": 123456789012345,
        "name": "Gaurav Kumar",
        "ifsc_code": "HDFC0000053"
    }
   },
   "receipt":"Receipt no. 1",
   "expire_by":1880480689,
   "sms_notify": True,
   "email_notify": True,
   "notes":{
      "note_key 1":"Beam me up Scotty",
      "note_key 2":"Tea. Earl Gray. Hot."
   }
})
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
  "type":"link",
  "amount":"100",
  "currency":"INR",
  "description":"Registration Link for Gaurav Kumar",
  "subscription_registration":map[string]interface{}{
    "method":"upi",
    "max_amount":"500",
    "expire_at":1609423824,
    "frequency": "monthly",
    "bank_account": {
        "account_number": 123456789012345,
        "name": "Gaurav Kumar",
        "ifsc_code": "HDFC0000053"
    }
  },
  "receipt":"Receipt No. 1",
  "email_notify":true,
  "sms_notify":true,
  "expire_by":1681987284,
  "notes":map[string]interface{}{
    "note_key 1":"Beam me up Scotty",
    "note_key 2":"Tea. Earl Gray. Hot.",
  },
}
body, err := client.Invoice.CreateRegistrationLink(data, nil)
```

```json Response theme={null}
{
  "id": "inv_FHr1ekX0r2VCVK",
  "entity": "invoice",
  "receipt": "Receipt No. 23",
  "invoice_number": "Receipt No. 23",
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
  "order_id": "order_FHr1ehR3nmNeXo",
  "line_items": [],
  "payment_id": null,
  "status": "issued",
  "expire_by": 4102444799,
  "issued_at": 1595489219,
  "paid_at": null,
  "cancelled_at": null,
  "expired_at": null,
  "sms_status": "pending",
  "email_status": "pending",
  "date": 1595489219,
  "terms": null,
  "partial_payment": false,
  "gross_amount": 100,
  "tax_amount": 0,
  "taxable_amount": 0,
  "amount": 100,
  "amount_paid": 0,
  "amount_due": 100,
  "currency": "INR",
  "currency_symbol": "₹",
  "description": "Registration Link for Gaurav Kumar",
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  },
  "comment": null,
  "short_url": "https://rzp.io/i/ak1WxDB",
  "view_less": true,
  "billing_start": null,
  "billing_end": null,
  "type": "link",
  "group_taxes_discounts": false,
  "created_at": 1595489219,
  "idempotency_key": null
}
```

### Request Parameters

`customer`
: `object` Details of the customer to whom the registration link is sent.

`name` *mandatory*
: `string` Customer's name.

`email` *mandatory*
: `string` Customer's email address.

`contact`*mandatory*
: `integer` Customer's contact number.

`type` *mandatory*
: `string` In this case, the value is `link`.

`amount` *mandatory*
: `integer` The payment amount in the smallest currency sub-unit.

`currency` *mandatory*
: `string` The 3-letter ISO currency code for the payment.

`description` *mandatory*
: `string` A description that appears on the hosted page.

`subscription_registration`
: Details of the authorisation transaction.

`method` *mandatory*
: `string` The payment method used to make authorisation transaction. Here, it is `card`.

`max_amount` *mandatory*
: `integer` Use to set the maximum amount (in paise) per debit request.

| MCC | Category | Min Value | Max Value |
| - | - | - | - |
| 6211 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
| 6300 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
| 7322 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
| 6529 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
| 5960 | Services | `100` (₹1) | `20000000` (₹2,00,000) |

For other categories and MCCs, the minimum value is `100` (₹1) and maximum value is 9999900 (₹99,999).

`expire_at` *optional*
: `integer` The Unix timestamp till when you can use the token to charge the customer subsequent payments. The default value is 10 years and the maximum value allowed is 30 years.

`frequency` *mandatory*
: `string` The frequency at which you can charge your customer. Possible values:

* `daily`
* `weekly`
* `fortnightly`
* `bimonthly`
* `monthly`
* `quarterly`
* `half_yearly`
* `yearly`
* `as_presented`

`bank_account` *mandatory*
: Details of the bank account of the customer.

`account_number` *mandatory*
: `integer` The bank account number of the customer. For example, `123456789012345`.

`name` *mandatory*
: `string` The name of the bank account holder.

`ifsc` *mandatory*
: `string` The IFSC of the bank. For example, `HDFC0000053`.

`sms_notify` *optional*
: `boolean` Indicates if SMS notifications are to be sent by Razorpay. Possible values:

* `true` (default): Notifications are sent by Razorpay .
* `false`: Notifications are not sent by Razorpay.

`email_notify` *optional*
: `boolean` Indicates if email notifications are to be sent by Razorpay. Possible values:

* `true` (default): Notifications are sent by Razorpay .
* `false`: Notifications are not sent by Razorpay.

`expire_by` *optional*
: `integer` The Unix timestamp indicates the expiry of the registration link.

`receipt` *optional*
: `string` A unique identifier entered by you for the order. For example, `Receipt No. 1`. You should map this parameter to the `order_id` sent by Razorpay.

`notes` *optional*
: `object` This is a key-value pair that is used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

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
