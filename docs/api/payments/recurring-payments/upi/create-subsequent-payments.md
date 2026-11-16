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

You have to create a new order every time you want to charge your customers. This order is different from the one created during the authorisation transaction.

Razorpay supports two types of flows for auto-debits: the coupled flow and the decoupled flow.

* **Coupled flow:** You create the order and the payment together. Razorpay immediately sends the Pre-Debit Notification (PDN) to the customer, and schedules the debit and its retries.
* **Decoupled flow:** You create the order first and send the `notification` object. You then create the payment after ensuring that a minimum of 24 hours has passed since the PDN was sent to the customer.

> [!NOTE]
>
> **Handy Tips**
>
> We recommend choosing between the coupled and decoupled flow for your whole UPI Autopay integration on your merchant account. To maximise the collection success rate, you can use the coupled flow, as it needs the least intervention from your end.

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

### Request Parameters

`amount` *mandatory*
: `integer` Amount in currency subunits. For cards, the minimum value is `100` (₹1).

`currency` *mandatory*
: `string` The 3-letter ISO currency code for the payment. Currently, we only support `INR`.

`receipt` *optional*
: `string` A user-entered unique identifier for the order. For example, `Receipt No. 1`. You should map this parameter to the `order_id` sent by Razorpay.

`notification`
: `object` Details of the pre-debit notification. Use this object to decide between the coupled and decoupled flow. If you send this object, Razorpay does not automatically schedule the debit or its retries. If you do not pass this object, we automatically try to debit 25 hours after the pre-debit notification is delivered, and retry 3 times if the debit attempts fail.

> [!WARNING]
>
> **Watch Out!**
>
> We will not attempt any retry if the debit fails for tokens with the notification object in the created order. You should manually retry the debit attempt.

`token_id` *mandatory*
: `string` The `token_id` generated when the customer successfully completes the authorisation payment. Different payment instruments for the same customer have different `token_id`.

`payment_after` *mandatory*
: `integer` UNIX timestamp post which the debit is supposed to happen. Mandatory for the decoupled flow.

`notes` *optional*
: `object` Key-value pair you can use to store additional information about the entity. Maximum of 15 key-value pairs, 256 characters each. For example, `"note_key": "Beam me up Scotty”`.

`payment_capture` *mandatory*
: `boolean` Determines whether the payment status should be changed to `captured` automatically or not. Possible values:

* `true`: Payments are captured automatically.
* `false`: Payments are not captured automatically. You can manually capture payments using the [Manually Capture Payments API](https://razorpay.com/docs/api/payments/capture.md).

### Response Parameters

`id`
: `string` A unique identifier of the order created. For example `order_1Aa00000000001`.

`entity`
: `string` The entity that has been created. Here it is `order`.

`amount`
: `integer` Amount in currency subunits.

`amount_paid`
: `integer` The amount that has been paid.

`amount_due`
: `integer` The amount that is yet to pay.

`currency`
: `string` The 3-letter ISO currency code for the payment. Currently, we only support `INR`.

`receipt`
: `string` A user-entered unique identifier of the order. For example, `rcptid #1`.

`status`
: `string` The status of the order.

`notes`
: `object` Key-value pair you can use to store additional information about the entity. Maximum of 15 key-value pairs, 256 characters each. For example, `"note_key": "Beam me up Scotty”`.

`created_at`
: `integer` The Unix timestamp at which the order was created.

### Error Response Parameters

Given below is a list of possible errors you may face while creating an Order.

| Error | Cause | Solution |
| - | - | - |
| The api key provided is invalid | This error occurs when you enter the wrong API key or secret. | Make sure to enter the valid API key and secret. |
| The amount must be at least INR 1.00. | This error occurs when you enter an amount less than INR 1. | Make sure the entered amount is atleast INR 1. |
| The currency should be INR when method is upi | This error occurs when you enter a currency other than INR. | Make sure the currency is INR. |

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

### Response Parameters

`razorpay_payment_id`
: `string` The unique identifier of the payment that is created. For example, `pay_1Aa00000000001`.

`razorpay_order_id`
: `string` The unique identifier of the order that is created. For example, `order_1Aa00000000001`.

`razorpay_signature`
: `string` The signature generated by the Razorpay. For example, `9ef4dffbfd84f1318f6739a3ce19f9d85851857ae648f114332d8401e0949a3d`

### Error Response Parameters

Given below is a list of possible errors you may face while creating a Recurring Payment.

> [accordion] adequate\_funds\_not\_available\_blocked
>
> * **Description**: Sufficient unblocked funds not available in customer's account. Please ask customer to add fund and try again.
> * **Next Steps**: Please ask customer to add sufficient unblocked funds and try again.

> [accordion] amount\_does\_not\_match\_mandate\_amount
>
> > [accordion] Amount Mismatch - Mandate Amount
> >
> > * **Description**: The payment failed as the amount does not match the amount provided at the time of mandate creation.
> > * **Next Steps**: Pass the transaction amount less than or equal to the mandate amount.
>
> > [accordion] Amount Mismatch - Payment Amount
> >
> > * **Description**: The amount does not match with payment amount.
> > * **Next Steps**: Retry with correct amount.

> [accordion] bad\_request\_error
>
> * **Description**: Invalid Mandate Sequence Number.
> * **Next Steps**: Retry after some time during the valid cycle.

> [accordion] bank\_account\_invalid
>
> * **Description**: Payment failed because Account linked to VPA is invalid.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] bank\_not\_available
>
> * **Description**: Payment was unsuccessful as the bank linked to this UPI ID is temporarily unavailable. Any amount deducted will be refunded within 5-7 working days.
> * **Next Steps**: Retry after some time.

> [accordion] bank\_technical\_error
>
> > [accordion] Bank Decline
> >
> > * **Description**: Payment was unsuccessful as it was declined by your bank. Any amount deducted will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] Bank or Wallet Gateway Error
> >
> > * **Description**: Payment processing failed due to error at bank or wallet gateway
> > * **Next Steps**: Retry after some time.
>
> > [accordion] Temporary Bank Issue
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue at your bank. Any amount deducted will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] General Temporary Issue
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] Bank Services Halt
> >
> > * **Description**: Payment was unsuccessful due to a temporary halt of services at this bank.
> > * **Next Steps**: Retry after some time.

> [accordion] banks\_hsm\_is\_down\_remitter
>
> * **Description**: Remitter bank failed to process the transaction. Please try again after some time.
> * **Next Steps**: Please try again after some time.

> [accordion] credit\_to\_beneficiary\_failed
>
> * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> * **Next Steps**: Retry after some time.

> [accordion] debit\_declined
>
> * **Description**: Payment was unsuccessful as it was declined by remitter bank.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] debit\_instrument\_blocked
>
> * **Description**: Payment was unsuccessful as the account linked to this UPI ID is blocked. Try using another account.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] execution\_day\_rule\_mismatch
>
> > [accordion] Execution Day Rule Mismatch
> >
> > * **Description**: Day of debit does not match the debit execution rule for the payer. Please ensure execution day matches the execution rule.
> > * **Next Steps**: Please ensure execution day matches execution rule.
>
> > [accordion] Execution Day Rule Mismatch - Remitter
> >
> > * **Description**: Day of debit does not match the debit execution rule for the payer. Please ensure execution day matches the execution rule.
> > * **Next Steps**: Please ensure execution day matches execution rule and try again.

> [accordion] gateway\_technical\_error
>
> > [accordion] Bank or Wallet Gateway Error
> >
> > * **Description**: Payment processing failed due to error at bank or wallet gateway.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] Temporary Issue with Money Deduction
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue. If money got deducted, reach out to the seller.
> > * **Next Steps**: Retry after some time.

> [accordion] id\_value\_must\_be\_present
>
> * **Description**: Failed to debit customer's bank account. Mandate details are incorrect.
> * **Next Steps**: Please try after sometime.

> [accordion] insufficient\_funds
>
> * **Description**: Transaction failed due to insufficient funds.
> * **Next Steps**: Ask the customer to add balance to their account and retry.

> [accordion] invalid\_response\_from\_gateway
>
> * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> * **Next Steps**: Retry after some time.

> [accordion] invalid\_token
>
> * **Description**: Invalid Token.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] invalid\_transaction\_beneficiary
>
> * **Description**: Beneficiary address resolution failed. Please try again after some time.
> * **Next Steps**: Please try again after some time.

> [accordion] invalid\_vpa
>
> * **Description**: You have entered an incorrect UPI ID. Please retry with the correct UPI ID.
> * **Next Steps**: Ask the customer to retry with a valid VPA.

> [accordion] issuer\_dispatch\_failed
>
> * **Description**: Payment failed due to some issue at the issuer bank. Please try again after some time.
> * **Next Steps**: Please try again after some time.

> [accordion] limit\_exceeded\_remitting\_bank
>
> * **Description**: Limit exceeded for remitter bank. Please ask customer to try with another bank account.
> * **Next Steps**: Please ask customer to try with another bank account.

> [accordion] mandate\_cancelled
>
> * **Description**: UPI mandate created for payment has been cancelled by user.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] mandate\_current\_cycle\_allowed\_debit\_exceeds
>
> * **Description**: Mandate is already honoured.
> * **Next Steps**: Wait till next cycle for debiting the customer.

> [accordion] mandate\_debit\_beyond\_psp\_amount\_cap
>
> * **Description**: Debit amount is beyond payer PSP specified amount cap. Please reduce the amount and try again.
> * **Next Steps**: Please reduce the mandate amount to match customer PSP.

> [accordion] mandate\_expired
>
> * **Description**: UPI Mandate is expired.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] mandate\_not\_active
>
> * **Description**: UPI mandate is not active.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] mandate\_paused
>
> * **Description**: UPI mandate is not active, it is paused by user.
> * **Next Steps**: Ask the customer to resume the mandate & retry.

> [accordion] merchant\_error\_payee\_psp
>
> * **Description**: VPA resolution into bank account details failed. Please try again after some time.
> * **Next Steps**: Please try again after some time.

> [accordion] mobile\_number\_invalid
>
> * **Description**: Registered Mobile number linked to the account has been changed or removed.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] mpin\_not\_set\_by\_customer
>
> * **Description**: UPI MPIN not set by customer. Please ask customer to set MPIN and try again.
> * **Next Steps**: Please ask customer to set MPIN and try again.

> [accordion] nature\_of\_debit\_not\_allowed
>
> * **Description**: Nature of debit not allowed in customer's account. Please ask the customer to use a different bank account.
> * **Next Steps**: Please ask the customer to use a different bank account.

> [accordion] no\_financial\_address\_record\_found
>
> * **Description**: No financial address record found for this vpa. Please ask customer to try with another bank account.
> * **Next Steps**: Please ask customer to try with other bank account.

> [accordion] no\_original\_request\_found
>
> * **Description**: No mandate details were found in the record during debit. Please try after some time.
> * **Next Steps**: Please try after some time.

> [accordion] null\_ack\_processing\_failure
>
> * **Description**: Processing failure at gateway. Please try again after some time.
> * **Next Steps**: Please try again after some time.

> [accordion] number\_of\_pin\_tries\_exceeded
>
> * **Description**: Customer has exceeded PIN retry limit. Please ask customer to create a new mandate and enter the right PIN.
> * **Next Steps**: Please ask customer to create a new mandate and enter the right PIN.

> [accordion] payer\_account\_has\_changed
>
> * **Description**: Payer account linked to the customer's VPA has changed. Please request the customer to either change it to the bank account used during mandate registration or register a new mandate for them.
> * **Next Steps**: Please request the customer to either change it to the bank account used during mandate registration or register a new mandate for them.

> [accordion] payer\_seqnum\_validation\_failure
>
> * **Description**: Payer sequence number length validation failed.
> * **Next Steps**: Please provide a valid payer sequence number (1-3 digits).

> [accordion] payment\_failed
>
> > [accordion] Temporary Issue with Refund
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue. If amount got deducted, it will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after 1 hour.
>
> > [accordion] Try Another Bank Account
> >
> > * **Description**: Payment failed. Please try again with another bank account.
> > * **Next Steps**: Retry after some time.

> [accordion] payment\_pending
>
> * **Description**: The status of your payment is pending. You can either wait or retry to pay successfully.
> * **Next Steps**: Retry after some time.

> [accordion] payment\_risk\_check\_failed
>
> * **Description**: Payment was unsuccessful as your account does not pass the risk checks done by your bank. Try using another account.
> * **Next Steps**: Retry after some time.

> [accordion] payment\_stopped\_by\_court\_order
>
> * **Description**: Payment processing failure at remitter bank. Please ask customer to try with another bank account.
> * **Next Steps**: Please ask customer to try with another bank account.

> [accordion] payment\_timed\_out
>
> * **Description**: Payment was unsuccessful as the bank linked to this UPI ID is not reachable at this time.
> * **Next Steps**: Retry after some time.

> [accordion] per\_transaction\_limit\_exceeded
>
> * **Description**: Customer bank per transaction limit exceeded. Please try again with a lower amount.
> * **Next Steps**: Please reduce transaction amount and try again.

> [accordion] psp\_bank\_not\_available
>
> * **Description**: Payer PSP / Bank not available. Please try again after some time.
> * **Next Steps**: Please try again after some time.

> [accordion] psp\_not\_available
>
> * **Description**: Payment was unsuccessful as the UPI app is not reachable at this time. Any amount deducted will be refunded within 5-7 working days.
> * **Next Steps**: Retry after some time.

> [accordion] psp\_timeout
>
> * **Description**: Payer PSP timed out. Please try again.
> * **Next Steps**: Please try again after some time.

> [accordion] regid\_details\_must\_be\_present
>
> * **Description**: Gateway validation failure. Please try after sometime or create a new mandate.
> * **Next Steps**: Please try after sometime or create a new mandate.

> [accordion] remitter\_account\_dormant
>
> * **Description**: Bank Account is closed.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] remitter\_dispatch\_failed
>
> * **Description**: Payment failed due to some issue at the customer's. Please try again after some time.
> * **Next Steps**: Please try again after some time.

> [accordion] request\_timed\_out
>
> * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> * **Next Steps**: Retry after some time.

> [accordion] response\_not\_received\_within\_tat
>
> * **Description**: VPA resolution into bank account details failed. Please try again after some time.
> * **Next Steps**: Please try again after some time.

> [accordion] seqnum\_mismatch\_payer\_psp
>
> * **Description**: Sequence number mismatch between payer and payee PSP. Please try again after some time.
> * **Next Steps**: Please ask customer to try after sometime.

> [accordion] suspected\_fraud\_decline
>
> * **Description**: Suspected fraud, transaction declined by customer's bank. Please try again after some time.
> * **Next Steps**: Please try after sometime.

> [accordion] transaction\_frequency\_limit\_exceeded
>
> * **Description**: Payment failed. Please try again with another bank account.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] transaction\_limit\_exceeded
>
> * **Description**: Payment failed because Transaction amount limit has exceeded
> * **Next Steps**: Reach out to the customer to collect the amount.

> [accordion] transaction\_not\_allowed
>
> * **Description**: Payment was unsuccessful as it was declined by your bank. Reach out to your bank for more details. Try using another account.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] transaction\_not\_permitted\_cardholder
>
> * **Description**: Transaction not permitted for customer's account. Please ask customer to try with another bank account.
> * **Next Steps**: Please ask customer to try with another bank account.

> [accordion] transaction\_not\_permitted\_cardholder\_beneficiary
>
> * **Description**: Transaction not permitted in beneficiary account. Please try again with another bank account.
> * **Next Steps**: Please try again with another bank account.

> [accordion] transaction\_not\_permitted\_to\_vpa
>
> * **Description**: Transaction not permitted to payee VPA by the payer PSP. Please contact your bank to enable Autopay for this VPA.
> * **Next Steps**: Please contact your bank to enable autopay for this VPA.

> [accordion] umn\_does\_not\_exist\_payer
>
> * **Description**: Mandate does not exist. Please create a new mandate.
> * **Next Steps**: Please ask customer to create new mandate.

> [accordion] unable\_to\_process\_beneficiary\_bank
>
> * **Description**: Error processing request at beneficiary bank. Please try again after some time.
> * **Next Steps**: Please try again after some time.

> [accordion] vpa\_resolution\_failed
>
> * **Description**: You have entered an incorrect UPI ID. Please retry with the correct UPI ID.
> * **Next Steps**: Retry after some time.

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

### Path Parameter

`id` *mandatory*
: `string` Unique identifier of the order to be retrieved.

### Response Parameters

`id`
: `string` The unique identifier of the order.

`amount`
: `integer` The amount for which the order was created, in currency subunits. For example, for an amount of ₹295, enter `29500`.

`entity`
: `string` Name of the entity. Here, it is `order`.

`amount_paid`
: `integer` The amount paid against the order.

`amount_due`
: `integer` The amount pending against the order.

`currency`
: `string` ISO code for the currency in which you want to accept the payment. The default length is 3 characters. Refer to the [list of supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).

`receipt`
: `string` Receipt number that corresponds to this order. Can have a maximum length of 40 characters and has to be unique.

`notification`
: `object` Details of the pre-debit notification. The notification object is populated in the response only if you have passed this while creating an order.

`token_id`
: `string` The `token_id` generated when the customer successfully completes the authorisation payment. Different payment instruments for the same customer have different `token_id`.

`payment_after`
: `integer` Unix timestamp post which the debit is supposed to happen.

`id`
: `string` Unique identifier of the notification.

`delivered_at`
: `integer` Indicates the unix timestamp when the notification was delivered.

`status`
: `string` The status of the order. Possible values:

* `created`: When you create an order it is in the `created` state. It stays in this state till a payment is attempted on it.
* `attempted`: An order moves from `created` to `attempted` state when a payment is first attempted on it. It remains in the `attempted` state till one payment associated with that order is captured.
* `paid`: After the successful capture of the payment, the order moves to the `paid` state. No further payment requests are permitted once the order moves to the `paid` state. The order stays in the `paid` state even if the payment associated with the order is refunded.

`attempts`
: `integer` The number of payment attempts, successful and failed, that have been made against this order.

`notes`
: `json object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

`created_at`
: `integer` Indicates the Unix timestamp when this order was created.

## 3.4. Best Practices

> [!NOTE]
>
> **Best Practices**
>
> * For Recurring Payments, it may take between 24-36 hours for the subsequent payment to reflect on your Dashboard.
> * This is because of the failure of pre-debit notification and/or any retries that we attempt for the payment.
> * Do not create another subsequent payment until you get the status of the previous one.
> * NPCI allows only one successful debit on a token per billing cycle. For example, if the billing frequency is monthly, you can execute only one successful debit per month on that token.
> * The subsequent payment may fail if there is late authorisation of an earlier payment.
> * For mandates with fixed frequency, do not create orders on the last day of the billing cycle. Doing so will fail the debit.
> * Always check the token status before attempting the debit. If the token is not `confirmed`, do not attempt the debit.
> * Razorpay sends the pre-debit notification immediately when you submit the Create Order API. We recommend timing the notification as per the customer's billing cycle.
> * Sometimes the customer modifies the token after you send the pre-debit notification. In such cases, you immediately receive the corresponding status change webhook and the payment moves to the `failed` state.
> * For coupled flow merchants, the payment remains in the `created` state until the debit is attempted and the payment succeeds or all retries are exhausted. Since Razorpay schedules the debits and retries, wait for the final payment status before taking a call on the subscription status of the customer. Depending on your retry configuration, this can take between T+1 and T+5 days.
> * If the debit amount exceeds ₹15,000 for regular industries (or ₹1,00,000 for lending and investment categories), the customer will receive a collect request on their UPI app and must enter their PIN to approve the payment. Ensure your system handles this Additional Factor of Authentication (AFA) flow gracefully.
