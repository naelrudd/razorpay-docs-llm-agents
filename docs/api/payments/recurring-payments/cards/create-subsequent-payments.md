> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# 3. Create Subsequent Payments

> Create and charge subsequent payments using Razorpay APIs after the customer's selected payment method is successfully authorized.

Available in
🇮🇳 India

You should perform the following steps to create and charge your customer subsequent payments:

1. [Create an order to charge the customer](#3-1-create-an-order-to-charge-the-customer)
2. [Create a recurring payment](#3-2-create-a-recurring-payment)

## 3.1. Create an Order to Charge the Customer

You have to create a new order every time you want to charge your customers. This order is different from the one created during the authorisation transaction.

> [!NOTE]
>
> **Handy Tips**
>
> You can use the notification object in the request if you want to control pre-debit notifications and recurring debits.

The following endpoint creates an order.

`POST /orders`

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/orders \
-H "Content-Type: application/json" \
-d '{
  "amount":1000,
  "currency":"INR",
  "payment_capture":true,
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
orderRequest.put("receipt", "Receipt No. 1");
JSONObject notification = new JSONObject();
notification.put("token_id","token_M7K2eFBU7vToaQ");
notification.put("payment_after","1634057114");
orderRequest.put("notification", notification);
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
orderRequest.put("notes", notes);

Order order = razorpay.orders.create(orderRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->order->create(array('receipt' => '123', 'amount' => 100, 'payment_capture' => true, 'currency' => 'INR', 'notification'=> array('token_id'=> 'token_M7K2eFBU7vToaQ','payment_after'=> '1634057114'), 'notes'=> array('key1'=> 'value3','key2'=> 'value2')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.orders.create({
  "amount":1000,
  "currency":"INR",
  "payment_capture": true,
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
  "receipt": "Receipt No. 1",
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
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "amount":1000,
  "currency":"INR",
  "payment_capture": true,
  "receipt":"Receipt No. 1",
  "notification": map[string]interface{}{
    "token_id":"token_M7K2eFBU7vToaQ",
    "payment_after":1634057114
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
orderRequest.Add("receipt", "receipt#12b");
orderRequest.Add("payment_capture", true);
Dictionary<string, object> notification = new Dictionary<string, object>();
notification.Add("token_id", "token_M7K2eFBU7vToaQ");
notification.Add("payment_after", "1634057114");
orderRequest.Add("notification", notification);
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("notes_key_1", "Tea, Earl Grey, Hot");
notes.Add("notes_key_2", "Tea, Earl Grey… decaf.");
orderRequest.Add("notes", notes);

Order order = client.Order.Create(orderRequest);
```

```json Success Response theme={null}
{
  "id":"order_1Aa00000000002",
  "entity":"order",
  "amount":1000,
  "amount_paid":0,
  "amount_due":1000,
  "currency":"INR",
  "receipt":"Receipt No. 1",
  "notification":{
    "token_id":"token_M7K2eFBU7vToaQ",
    "payment_after":1634057114,
    "id":"notification_00000000000001"
  },
  "offer_id":null,
  "status":"created",
  "attempts":0,
  "notes":{
    "notes_key_1":"Tea, Earl Grey, Hot",
    "notes_key_2":"Tea, Earl Grey… decaf."
  },
  "created_at":1579782776
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

> [accordion] Request Parameters
>
> `amount` *mandatory*
> : `integer` Amount in currency subunits. For cards, the minimum value is `100`, that is, ₹1.
>
> `currency` *mandatory*
> : `string` The 3-letter ISO currency code for the payment.
>
> `receipt` *optional*
> : `string` A user-entered unique identifier for the order. For example, `Receipt No. 1`. You should map this parameter to the `order_id` sent by Razorpay.
>
> `notification`
> : `object` Details of the pre-debit notification. This object is optional. You should use it only if you want to control pre-debit notifications and debits. If you do not pass this object, we will automatically try to debit after 36 hours and 5 minutes.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > The TAT to create a debit if you send a pre-debit notification is 36 hours and 5 minutes.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > We will not attempt any retry if the debit fails for tokens with the notification object in the created order. You should manually retry the debit attempt.
>
> `token_id` *mandatory*
> : `string` The `token_id` generated when the customer successfully completes the authorisation payment. Different payment instruments for the same customer have different `token_id`.
>
> `payment_after` *optional*
> : `integer` UNIX timestamp post which the debit is supposed to happen. Defaults to 36 hours and 5 minutes after the pre-debit notification is delivered.
>
> `notes` *optional*
> : `object` Key-value pair you can use to store additional information about the entity. Maximum of 15 key-value pairs, 256 characters each. For example, `"note_key": "Beam me up Scotty”`.
>
> `payment_capture` *mandatory*
> : `boolean` Determines whether the payment status should be changed to `captured` automatically or not. Possible values:
>
> * `true`: Payments are captured automatically.
> * `false`: Payments are not captured automatically. You can manually capture payments using the [Manually Capture Payments API](https://razorpay.com/docs/api/payments/capture.md).

> [accordion] Response Parameters
>
> `id`
> : `string` A unique identifier of the order created. For example `order_1Aa00000000001`.
>
> `entity`
> : `string` The entity that has been created. Here it is `order`.
>
> `amount`
> : `integer` Amount in currency subunits.
>
> `amount_paid`
> : `integer` The amount that has been paid.
>
> `amount_due`
> : `integer` The amount that is yet to be paid.
>
> `currency`
> : `string` The 3-letter ISO currency code for the payment.
>
> `receipt`
> : `string` A user-entered unique identifier of the order. For example, `rcptid #1`.
>
> `notification`
> : `object` Details of the pre-debit notification.
>
> `token_id`
> : `string` The `token_id` generated when the customer successfully completes the authorisation payment. Different payment instruments for the same customer have different `token_id`.
>
> `payment_after`
> : `integer` UNIX timestamp post which the debit is supposed to happen.
>
> `id`
> : `string` the unique identifier of the notification. For example, `notification_00000000000001`.
>
> `status`
> : `string` The status of the order.
>
> `notes`
> : `object` Key-value pair you can use to store additional information about the entity. Maximum of 15 key-value pairs, 256 characters each. For example, `"note_key": "Beam me up Scotty”`.
>
> `created_at`
> : `integer` The Unix timestamp at which the order was created.

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

* You will get a `razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature` as a response after the payment request is successfully processed.
* In the case of some banks, such as HDFC Bank and Axis Bank, the payment entity is in the `created` state since the charging system of these banks is file-based and can take some time.

> [accordion] Request Parameters
>
> `email ` *mandatory*
> : `string` The customer's email address. For example, `gaurav.kumar@example.com`.
>
> `contact ` *mandatory*
> : `integer` The customer's phone number. For example, `9876543210`.
>
> `currency` *mandatory*
> : `string` 3-letter ISO currency code for the payment. Currently, only `INR` is allowed.
>
> `amount` *mandatory*
> : `integer` The amount you want to charge your customer. This should be the same as the order amount.
>
> `order_id`*mandatory*
> : `string` The unique identifier of the order created. For example, `order_1Aa00000000002`.
>
> `customer_id` *mandatory*
> : `string` The unique identifier of the customer you want to charge. For example, `cust_1Aa00000000002`.
>
> `token` *mandatory*
> : `string` The `token_id` generated when the customer successfully completes the authorisation payment. Different payment instruments for the same customer have different `token_id`.
>
> `recurring` *mandatory*
> : `boolean` Determines whether recurring payment is enabled or not.
>
> * `true`: Recurring payment is enabled.
> * `false`: Recurring payment is not enabled.
>
> `description`*optional*
> : `string` A user-entered description for the payment. For example, `Creating recurring payment for Gaurav Kumar`
>
> `notes`*optional*
> : `object` Key-value pair you can use to store additional information about the entity. Maximum of 15 key-value pairs, 256 characters each. For example, `"note_key": "Beam me up Scotty”`.

> [accordion] Response Parameters
>
> `razorpay_payment_id`
> : `string` The unique identifier of the payment that is created. For example, `pay_1Aa00000000001`.
>
> `razorpay_order_id`
> : `string` The unique identifier of the order that is created. For example, `order_1Aa00000000001`.
>
> `razorpay_signature`
> : `string` The signature generated by the Razorpay. For example, `9ef4dffbfd84f1318f6739a3ce19f9d85851857ae648f114332d8401e0949a3d`

> [accordion] Error Response Parameters
>
> Given below is a list of possible errors you may face while creating a Recurring Payment.
>
> | Error | Cause | Solution |
> | - | - | - |
> | pre\_debit\_notification\_not\_sent | This error occurs when a pre-debit notification is not sent and a debit attempt is made. | Make sure to send a pre-debit notification before an attempt. |
> | BAD\_REQUEST\_MANDATE\_PROMISED\_DEBIT\_DATE\_NOT\_HONOURED | This error occurs when you attempt a debit within 36 hours and 5 minutes of a notification being delivered. | You can only attempt a manual debit 36 hours and 5 minutes after the notification is delivered. |

## 3.3. Fetch an Order With ID

Use this endpoint to retrieve details of a particular order as per the id.

`GET /v1/orders/:id`

```bash Curl theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-X GET https://api.razorpay.com/v1/orders/:id
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String orderId = "order_1Aa00000000002";

Order order = razorpay.orders.fetch(orderId);
```

```python Python theme={null}
# do easy_install razorpay or
#    pip install razorpay

import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.order.fetch(orderId)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->order->fetch($orderId);
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

orderId = "order_1Aa00000000002"

Razorpay::Order.fetch(orderId)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.orders.fetch(orderId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Order.Fetch("<orderId>", nil, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string orderId = "order_1Aa00000000002";

Order order = client.Order.Fetch(orderId);
```

```json Success theme={null}
{
  "id":"order_DaaS6LOUAASb7Y",
  "entity":"order",
  "amount":2000,
  "amount_paid":0,
  "amount_due":2000,
  "currency":"INR",
  "receipt":null,
  "notification":{
    "token_id":"token_M7K2eFBU7vToaQ",
    "payment_after":1634057114,
    "id":"notification_00000000000001",
    "status":"delivered",
    "delivered_at":1634057113
  },
  "offer_id":"offer_JGQvQtvJmVDRIA",
  "offers":[
    "offer_JGQvQtvJmVDRIA"
  ],
  "status":"created",
  "attempts":0,
  "notes":[
    
  ],
  "created_at":1654776878
}
```

```json Failure theme={null}
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

> [accordion] Path Parameter
>
> `id` *mandatory*
> : `string` Unique identifier of the order to be retrieved.

> [accordion] Response Parameters
>
> `id`
> : `string` The unique identifier of the order.
>
> `amount`
> : `integer` The amount for which the order was created, in currency subunits. For example, for an amount of ₹295, enter `29500`.
>
> `entity`
> : `string` Name of the entity. Here, it is `order`.
>
> `amount_paid`
> : `integer` The amount paid against the order.
>
> `amount_due`
> : `integer` The amount pending against the order.
>
> `currency`
> : `string` ISO code for the currency in which you want to accept the payment. The default length is 3 characters. Refer to the [list of supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).
>
> `receipt`
> : `string` Receipt number that corresponds to this order. Can have a maximum length of 40 characters and has to be unique.
>
> `notification`
> : `object` Details of the pre-debit notification. The notification object is populated in the response only if you have passed this while creating an order.
>
> `token_id`
> : `string` The `token_id` generated when the customer successfully completes the authorisation payment. Different payment instruments for the same customer have different `token_id`.
>
> `payment_after`
> : `integer` Unix timestamp post which the debit is supposed to happen.
>
> `id`
> : `string` Unique identifier of the notification.
>
> `delivered_at`
> : `integer` Indicates the unix timestamp when the notification was delivered.
>
> `status`
> : `string` The status of the order. Possible values:
>
> * `created`: When you create an order it is in the `created` state. It stays in this state till a payment is attempted on it.
> * `attempted`: An order moves from `created` to `attempted` state when a payment is first attempted on it. It remains in the `attempted` state till one payment associated with that order is captured.
> * `paid`: After the successful capture of the payment, the order moves to the `paid` state. No further payment requests are permitted once the order moves to the `paid` state. The order stays in the `paid` state even if the payment associated with the order is refunded.
>
> `attempts`
> : `integer` The number of payment attempts, successful and failed, that have been made against this order.
>
> `notes`
> : `json object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.
>
> `created_at`
> : `integer` Indicates the Unix timestamp when this order was created.
