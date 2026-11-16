> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# 3. Create Subsequent Payments

> Create and charge subsequent payments using Razorpay APIs after the customer's selected payment method is authorised.

Available in
🇮🇳 India

You should perform the following steps to create and charge your customer subsequent payments:

1. [Create an order to charge the customer](#3-1-create-an-order-to-charge-the-customer)
2. [Create a recurring payment](#3-2-create-a-recurring-payment)

## 3.1. Create an Order to Charge the Customer

You have to create a new order every time you want to charge your customers. This order is different from the one created when you created the authorisation transaction.

Use the below endpoint to create an order:

`POST /orders`

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/orders \
-H "Content-Type: application/json" \
-d '{
   "amount":1000,
   "currency":"INR",
   "payment_capture":true,
   "method":"upi",
   "bank_account":{
      "account_number":"123456789012345",
      "name":"Gaurav Kumar",
      "ifsc":"HDFC0000053"
   },
   "receipt":"Receipt No. 1",
   "notification":{
      "token_id":"token_M7K2eFBU7vToaQ",
      "payment_after":1634057114
   },
   "notes":{
      "notes_key_1":"Tea, Earl Grey, Hot",
      "notes_key_2":"Tea, Earl Grey… decaf."
   }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject orderRequest = new JSONObject();
orderRequest.put("amount", 1000);
orderRequest.put("currency", "INR");
orderRequest.put("payment_capture", true);
orderRequest.put("method", "upi");
JSONObject bank_account = new JSONObject();
bank_account.put("account_number","123456789012345"); 
bank_account.put("name","Gaurav Kumar");
bank_account.put("ifsc","HDFC0000053");
orderRequest.put("bank_account", bank_account);
orderRequest.put("receipt", "Receipt No. 1");
JSONObject notification = new JSONObject();
notification.put("token_id","token_M7K2eFBU7vToaQ");
notification.put("payment_after",1634057114);
orderRequest.put("notification", notification);
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
orderRequest.put("notes", notes);

Order order = razorpay.orders.create(orderRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->order->create(array('receipt' => '123', 'amount' => 100, 'payment_capture' => true,'method' => 'upi','bank_account' => array('account_number' => 123456789012345, 'name' => Gaurav Kumar, 'ifsc' => 'HDFC0000053'),'currency' => 'INR', 'notification' => array('token_id' => 'token_M7K2eFBU7vToaQ', 'payment_after' => 1634057114), 'notes'=> array('key1'=> 'value3','key2'=> 'value2')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.orders.create({
  "amount":1000,
  "currency":"INR",
  "payment_capture": true,
  "method":"upi",
  "bank_account": {
        "account_number": 123456789012345,
        "name": "Gaurav Kumar",
        "ifsc": "HDFC0000053"
    },
  "receipt":"Receipt No. 1",
  "notification": {
    "token_id":"token_M7K2eFBU7vToaQ",
    "payment_after":1634057114
  },
  "notes": {
    "notes_key_1":"Tea, Earl Grey, Hot",
    "notes_key_2":"Tea, Earl Grey… decaf."
  }
})
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.order.create({
    'amount': 1000,
    'currency': 'INR',
    'payment_capture': True,
    'method': 'upi',
    'bank_account':{
      'account_number':123456789012345,
      'name':'Gaurav Kumar',
      'ifsc':'HDFC0000053'
   },
    'receipt': 'Receipt No. 1',
    'notification': {'token_id': 'token_M7K2eFBU7vToaQ',
    'payment_after': 1634057114},
    'notes': {'notes_key_1': 'Tea, Earl Grey, Hot',
              'notes_key_2': 'Tea, Earl Grey... decaf.'}
    })
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {
  "amount": 1000,
  "currency": "INR",
  "payment_capture": true,
  "method":"upi",
  "receipt": "Receipt No. 1",
  "bank_account":{
      "account_number":123456789012345,
      "name":"Gaurav Kumar",
      "ifsc":"HDFC0000053"
   },
  "notification": {
    "token_id":"token_M7K2eFBU7vToaQ",
    "payment_after":1634057114
  },
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
}

Razorpay::Order.create(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_S ECRET")

data:= map[string]interface{}{
  "amount":1000,
  "currency":"INR",
  "payment_capture": true,
  "method":"upi",
  "bank_account":map[string]interface{}{
      "account_number":123456789012345,
      "name":Gaurav Kumar,
      "ifsc":"HDFC0000053",
   },
  "receipt":"Receipt No. 1",
  "notification": map[string]interface{}{
    "token_id":"token_M7K2eFBU7vToaQ",
    "payment_after":1634057114,
  },
  "notes": map[string]interface{}{
    "notes_key_1":"Tea, Earl Grey, Hot",
    "notes_key_2":"Tea, Earl Grey… decaf.",
  },
}
body, err := client.Order.Create(data, nil)

```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> orderRequest = new Dictionary<string, object>();
orderRequest.Add("amount", 100);
orderRequest.Add("currency", "INR");
orderRequest.Add("payment_capture", true);
orderRequest.Add("method", "upi");
Dictionary<string, object> bank_account = new Dictionary<string, object>();
bank_account.Add("account_number","123456789012345"); 
bank_account.Add("name","Gaurav Kumar");
bank_account.Add("ifsc","HDFC0000053");
orderRequest.Add("bank_account", bank_account);
orderRequest.Add("receipt", "Receipt No. 1");
Dictionary<string, object> notification = new Dictionary<string, object>();
notification.Add("token_id", "token_M7K2eFBU7vToaQ");
notification.Add("payment_after", 1634057114);
orderRequest.Add("notification", notification);
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("notes_key_1", "Tea, Earl Grey, Hot");
notes.Add("notes_key_2", "Tea, Earl Grey… decaf.");
orderRequest.Add("notes", notes);

Order order = client.Order.Create(orderRequest);
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
: `integer` Amount in currency subunits. For cards, the minimum value is `100` (₹1).

`currency` *mandatory*
: `string` The 3-letter ISO currency code for the payment. Currently, we only support `INR`.

`receipt` *optional*
: `string` A user-entered unique identifier for the order. For example, `Receipt No. 1`. This parameter should be mapped to the `order_id` sent by Razorpay.

`notification`
: `object` Details of the pre-debit notification. This object is optional. You should use it only if you want to control pre-debit notifications and debits. If you do not pass this object, we will automatically try to debit 25 hours after the pre-debit notification is delivered.

> [!WARNING]
>
> **Watch Out!**
>
> We will not attempt any retry if the debit fails for tokens with the notification object in the created order. You should manually retry the debit attempt.

`token_id` *mandatory*
: `string` The `token_id` generated when the customer successfully completes the authorisation payment. Different payment instruments for the same customer have different `token_id`.

`payment_after` *optional*
: `integer` UNIX timestamp post which the debit is supposed to happen. Defaults to 25 hours after the pre-debit notification is delivered.

`notes` *optional*
: `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

`payment_capture` *mandatory*
: `boolean` Determines whether the payment status should be changed to `captured` automatically or not. Possible values:

* `true`: Payments are captured automatically.
* `false`: Payments are not captured automatically. You can manually capture payments using the [Manually Capture Payments API](https://razorpay.com/docs/api/payments/capture.md).

`bank_account` *mandatory*
: Details of the bank account of the customer.

`account_number` *mandatory*
: `integer` The bank account number of the customer. For example, `123456789012345`.

`name` *mandatory*
: `string` The name of the bank account holder.

`ifsc` *mandatory*
: The IFSC of the bank. For example, `HDFC0000053`.

## 3.2. Create a Recurring Payment

Once you have generated an `order_id`, use it with the `token_id` to create a payment and charge the customer. The following endpoint creates a payment to charge the customer.

`POST /payments/create/recurring`

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/payments/create/recurring \
-H "Content-Type: application/json" \
-d '{
  "email": "<email>",
  "contact": "<phone>",
  "amount": 1000,
  "currency": "INR",
  "order_id": "order_1Aa00000000002",
  "customer_id": "cust_1Aa00000000001",
  "token": "token_1Aa00000000001",
  "recurring": true,
  "description": "Creating recurring payment for <name>",
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject paymentRequest = new JSONObject();
paymentRequest.put("email", "<email>");
paymentRequest.put("contact", "<phone>");
paymentRequest.put("amount", 1000);
paymentRequest.put("currency", "INR");
paymentRequest.put("order_id", "order_1Aa00000000002");
paymentRequest.put("customer_id", "cust_1Aa00000000001");
paymentRequest.put("token", "token_1Aa00000000001");
paymentRequest.put("recurring", true);
paymentRequest.put("description", "Creating recurring payment for <name>");
JSONObject notes = new JSONObject();
paymentRequest.put("notes_key_1","Tea, Earl Grey, Hot");
paymentRequest.put("notes_key_2","Tea, Earl Grey… decaf.");

Payment payment = razorpay.payments.createRecurringPayment(paymentRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->createRecurring(array('email'=>'<email>','contact'=>'<phone>','amount'=>100,'currency'=>'INR','order_id'=>'order_1Aa00000000002','customer_id'=>'cust_1Aa00000000001','token'=>'token_1Aa00000000001','recurring'=>true,'description'=>'Creating recurring payment for <name>'));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.createRecurringPayment({
  "email": "<email>",
  "contact": "<phone>",
  "amount": 1000,
  "currency": "INR",
  "order_id": "order_1Aa00000000002",
  "customer_id": "cust_1Aa00000000001",
  "token": "token_1Aa00000000001",
  "recurring": true,
  "description": "Creating recurring payment for <name>",
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  }
})
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.createRecurring({
    'email': '<email>',
    'contact': <phone>,
    'amount': 1000,
    'currency': 'INR',
    'order_id': "order_1Aa00000000002",
    'customer_id': "cust_1Aa00000000001",
    'token': 'token_1Aa00000000001',
    'recurring': True,
    'description': 'Creating recurring payment for <name>',
    'notes': {'note_key 1': 'Beam me up Scotty',
              'note_key 2': 'Tea. Earl Gray. Hot.'}
    })
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {
  "email": "<email>",
  "contact": "<phone>",
  "amount": 1000,
  "currency": "INR",
  "order_id": "order_1Aa00000000002",
  "customer_id": "cust_1Aa00000000001",
  "token": "token_1Aa00000000001",
  "recurring": true,
  "description": "Creating recurring payment for <name>",
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  }
}
Razorpay::Payment.create_recurring_payment(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "email": "<email>",
  "contact": "<phone>",
  "amount": 1000,
  "currency": "INR",
  "order_id": "order_1Aa00000000002",
  "customer_id": "cust_1Aa00000000001",
  "token": "token_1Aa00000000001",
  "recurring": true,
  "description": "Creating recurring payment for <name>",
  "notes": map[string]interface{}{
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot.",
  },
}
body, err := Client.Payment.CreateRecurringPayment(data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> paymentRequest = new Dictionary<string, object>();
paymentRequest.Add("email", "<email>");
paymentRequest.Add("contact", "<phone>");
paymentRequest.Add("amount", 1000);
paymentRequest.Add("currency", "INR");
paymentRequest.Add("order_id", "order_MZ35KPxZaqxfXq");
paymentRequest.Add("customer_id", "cust_KUyah9o60OPhfj");
paymentRequest.Add("token", "token_MZ37MsnhLNH4tN");
paymentRequest.Add("recurring", true);
paymentRequest.Add("description", "Creating recurring payment for <name>");
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("notes_key_1", "Tea, Earl Grey, Hot");
notes.Add("notes_key_2", "Tea, Earl Grey… decaf.");
paymentRequest.Add("notes", notes);

Payment payment = client.Payment.CreateRecurringPayment(paymentRequest);
```

```json Success Response theme={null}
{
  "razorpay_payment_id" : "pay_1Aa00000000001"
}
```

```json Failure Response theme={null}
{
   "error":{
      "code":"BAD_REQUEST_ERROR",
      "description":"Amount exceeds maximum amount allowed",
      "source":"business",
      "step":"payment_initiation",
      "reason":"input_validation_failed",
      "metadata":{
         
      }
   }
}
```

> [!NOTE]
>
> **UPI Payments**
>
> * We recommend sending a pre-debit notification to the customer 24 hours before the debit date.
> * For UPI, it may take between 24-36 hours for the subsequent payment to reflect on your Dashboard.
> * This is because of the failure of pre-debit notification and/or any retries that we attempt for the payment.
> * Do not create another subsequent payment until you get the status of the previous one.

> [!WARNING]
>
> **UPI Payments**
>
> * The subsequent payment may fail if there is late authorisation of an earlier payment.
> * For UPI, **do not** create subsequent payments on the last day of the cycle. This will cause the payment to fail.

### Request Parameters

`email ` *mandatory*
: `string` The customer's email address. For example, `gaurav.kumar@example.com`.

`contact ` *mandatory*
: `integer` The customer's phone number. For example, `9876543210`.

`currency` *mandatory*
: `string` 3-letter ISO currency code for the payment. Currently, only `INR` is allowed.

`amount` *mandatory*
: `integer` The amount you want to charge your customer. This should be the same as the order amount.

`order_id`*mandatory*
: `string` The unique identifier of the order created. For example, `order_1Aa00000000002`.

`customer_id` *mandatory*
: `string` The unique identifier of the customer you want to charge. For example, `cust_1Aa00000000002`.

`token` *mandatory*
: `string` The `token_id` generated when the customer successfully completes the authorisation payment. Different payment instruments for the same customer have different `token_id`.

`recurring` *mandatory*
: `boolean` Determines whether recurring payment is enabled or not.

* `true`: Recurring payment is enabled.
* `false`: Recurring payment is not enabled.

`description`*optional*
: `string` A user-entered description for the payment. For example, `Creating recurring payment for Gaurav Kumar`

`notes`*optional*
: `object` Key-value pair you can use to store additional information about the entity. Maximum of 15 key-value pairs, 256 characters each. For example, `"note_key": "Beam me up Scotty”`.
