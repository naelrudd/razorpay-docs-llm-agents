# 2. Execute Subsequent Payments

Once the customer's mandate is registered and the token is in the `confirmed` state, you can execute subsequent payments (debits) against the mandate. Perform the following steps to charge your customer:

1. [Create an Order to Charge the Customer](#21-create-an-order-to-charge-the-customer)
1. [Create a Recurring Payment](#22-create-a-recurring-payment)

**INFO**

**UPI Payments**

- We recommend sending a pre-debit notification to the customer 24-48 hours before the debit date.
- For Recurring Payments, it may take between 24-36 hours for the subsequent payment to reflect on your Dashboard.
- This is because of the failure of pre-debit notification and/or any retries that we attempt for the payment.
- Do not create another subsequent payment until you get the status of the previous one.
- NPCI allows only one successful debit on a token per billing cycle. For example, if the billing frequency is monthly, you can execute only one successful debit per month on that token.
- The subsequent payment may fail if there is late authorisation of an earlier payment.
- Avoid creating subsequent debits on the last day of the billing cycle. Pre-debit notifications are delivered 24 hours before the debit and the actual debit is attempted in the 25th hour. If you initiate on the last day, the debit attempt falls into the next billing cycle and will fail.
- If the debit amount exceeds ₹15,000 for regular industries (or ₹1,00,000 for lending and investment categories), the customer will receive a collect request on their UPI app and must enter their PIN to approve the payment. Ensure your system handles this AFA flow gracefully.

## 2.1. Create an Order to Charge the Customer

You have to create a new order every time you want to charge your customers. This order is different from the one created when you initiated the mandate registration.

Use the below endpoint to create an order:

/orders

```cURL: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/orders \
-H "Content-Type: application/json" \
-d '{
   "amount":10000,
   "currency":"INR",
   "payment_capture": true
}'
```php: PHP
$api = new Api($key_id, $secret);

$api->order->create(array('amount' => 100, 'payment_capture' => true, 'currency' => 'INR'));
```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.order.create({
  "amount":1000,
  "currency":"INR",
  "payment_capture": true
})
```python: Python
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.order.create({
    'amount': 1000,
    'payment_capture': True,
    'currency': 'INR',
    })

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "amount":1000,
  "currency":"INR",
  "payment_capture": true,
}
body, err := client.Order.Create(data, nil)

```json: Response
{
   "id":"order_1Aa00000000002",
   "entity":"order",
   "amount":10000,
   "currency":"INR",
   "status":"created",
   "attempts":0,
   "created_at":1455696638,
   "notes":[
      
   ]
}
```

### Request Parameters

`amount` _mandatory_
: `integer` Amount in currency subunits. For cards, the minimum value is `100` (₹1).

`currency` _mandatory_
: `string` The 3-letter ISO currency code for the payment. Currently, we only support `INR`.

`payment_capture` _mandatory_
: `boolean` Determines whether the payment status should be changed to `captured` automatically or not. Possible values:
    - `true`: Payments are captured automatically.
    - `false`: Payments are not captured automatically. You can manually capture payments using the [Manually Capture Payments API](https://razorpay.com/docs/build/llm-docs/api/payments.md#capture-a-payment).

## 2.2. Create a Recurring Payment

Once you have generated an `order_id`, use it along with the `token_id` to create a payment and charge the customer.

Use the below endpoint to create a payment and charge the customer.

/payments/create/recurring

```cURL: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/payments/create/recurring \
-H "Content-Type: application/json" \
-d '{
  "email": "gaurav.kumar@example.com",
  "contact": "9000090000",
  "amount": 1000,
  "currency": "INR",
  "order_id": "order_1Aa00000000002",
  "customer_id": "cust_1Aa00000000001",
  "token": "token_1Aa00000000001",
  "recurring": true,
  "description": "Creating recurring payment for Gaurav Kumar",
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  }
}'

```php: PHP
$api = new Api($key_id, $secret);

$api->payment->createRecurring(array('email'=>'gaurav.kumar@example.com','contact'=>'9000090000','amount'=>100,'currency'=>'INR','order_id'=>'order_1Aa00000000002','customer_id'=>'cust_1Aa00000000001','token'=>'token_1Aa00000000001','recurring'=> true,'description'=>'Creating recurring payment for Gaurav Kumar'));

```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.createRecurringPayment({
  "email": "gaurav.kumar@example.com",
  "contact": 9000090000,
  "amount": 100,
  "currency": "INR",
  "order_id": "order_1Aa00000000002",
  "customer_id": "cust_1Aa00000000001",
  "token": "token_1Aa00000000001",
  "recurring": true,
  "description": "Creating recurring payment for Gaurav Kumar",
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  }
})

```python: Python
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.createRecurring({
    'email': 'gaurav.kumar@example.com',
    'contact': 9000090000,
    'amount': 1000,
    'currency': 'INR',
    'order_id': "order_1Aa00000000002",
    'customer_id': "cust_1Aa00000000001",
    'token': 'token_1Aa00000000001',
    'recurring': True,
    'description': 'Creating recurring payment for Gaurav Kumar',
    'notes': {'note_key 1': 'Beam me up Scotty',
              'note_key 2': 'Tea. Earl Gray. Hot.'}
    })

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "email": "gaurav.kumar@example.com",
  "contact": "9000090000",
  "amount": 1000,
  "currency": "INR",
  "order_id": "order_1Aa00000000002",
  "customer_id": "cust_1Aa00000000001",
  "token": "token_1Aa00000000001",
  "recurring": true,
  "description": "Creating recurring payment for Gaurav Kumar",
  "notes": map[string]interface{}{
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot.",
  },
}
body, err := Client.Payment.CreateRecurringPayment(data, nil)

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {
  "email": "gaurav.kumar@example.com",
  "contact": "9000090000",
  "amount": 1000,
  "currency": "INR",
  "order_id": "order_1Aa00000000002",
  "customer_id": "cust_1Aa00000000001",
  "token": "token_1Aa00000000001",
  "recurring": true,
  "description": "Creating recurring payment for Gaurav Kumar",
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  }
}
Razorpay::Payment.create_recurring_payment(para_attr)

```json: Response
{
  "razorpay_payment_id" : "pay_1Aa00000000001",
  "razorpay_order_id" : "order_1Aa00000000001",
  "razorpay_signature" : "9ef4dffbfd84f1318f6739a3ce19f9d85851857ae648f114332d8401e0949a3d"
}
```

Once our system validates and successfully processes the payment request, a `razorpay_payment_id` is returned. In the case of some banks such as HDFC Bank and Axis Bank, the payment entity returned will be in the `created` state since the charge system of these banks are file-based and can take a few hours.

### Request Parameters

`email ` _mandatory_
: `string` The customer's email address. For example, `gaurav.kumar@example.com`.

`contact ` _mandatory_
: `string` The customer's phone number. For example, `9876543210`.

`amount` _mandatory_
: `integer` The amount you want to charge your customer. This should be the same as the amount in the order.

`currency` _mandatory_
: `string` 3-letter ISO currency code for the payment. Currently, only `INR` is allowed.

`order_id`_mandatory_
: `string` The unique identifier of the order created. For example, `order_1Aa00000000002`.

`customer_id` _mandatory_
: `string` The `customer_id` for the customer you want to charge. For example, `cust_1Aa00000000002`.

`token` _mandatory_
: `string` The `token_id` generated when the customer successfully completes the mandate registration. Different payment instruments for the same customer have different `token_id`.

`recurring` _mandatory_
: `boolean` Determines if recurring payment is enabled or not.
    - `true`: Recurring Payment is enabled.
    - `false`: Recurring Payment is not enabled.

`description`_optional_
: `string` A user-entered description for the payment. For example, `Creating recurring payment for Gaurav Kumar`.

`notes`_optional_
: `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty"`.
