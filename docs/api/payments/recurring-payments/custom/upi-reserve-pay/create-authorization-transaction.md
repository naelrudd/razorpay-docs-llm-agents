> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# 1. Create the Authorisation Transaction

> Steps to create an authorisation transaction using the UPI Reserve Pay (SBMD) Custom Checkout APIs.

Available in
🇮🇳 India

UPI Reserve Pay APIs use the single-block, multiple-debit (SBMD) framework to manage scheduled or recurring transactions. With a single customer authorisation, this system allows businesses to block a specific sum from the customer's account. This reserved fund can then be debited automatically multiple times, eliminating the need for further customer approvals and ensuring a smoother, more reliable payment flow.

**Example**

A customer using the Acme Quick commerce app authorises a one-time UPI block of ₹2000 for future purchases. When they place a ₹400 order on Monday and a ₹600 order on Wednesday, both amounts are automatically debited from that reserved fund. The customer never has to enter a PIN at checkout, making their repeat orders completely frictionless.

To create a UPI Reserve Pay mandate:

1. [Create an authorisation transaction](#create-an-authorisation-transaction)
2. [Fetch and manage tokens](https://razorpay.com/docs/api/payments/recurring-payments/custom/upi-reserve-pay/tokens.md)
3. [Create a One Time payment](https://razorpay.com/docs/api/payments/recurring-payments/custom/upi-reserve-pay/one-time-payment.md)

## Create an Authorisation Transaction

To create an authorisation transaction using the Razorpay APIs, you need to:

1. [Create a Customer](#1-1-create-a-customer)
2. [Create an Order](#1-2-create-an-order)
3. [Create Authorisation Payment](#1-3-create-an-authorisation-payment)

### 1.1 Create a Customer

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

### 1.2 Create an Order

Use the [Orders API](https://razorpay.com/docs/api/orders.md) to create a unique Razorpay `order_id` that is associated with the authorisation transaction for a one time mandate. To create a one-time mandate, pass the value of the `frequency` parameter as `one_time`. The following endpoint creates an order.

`POST /orders`

```bash Curl theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-X POST https://api.razorpay.com/v1/orders \
-H "Content-Type: application/json" \
-d '{
  "amount": 100,
  "currency": "INR",
  "customer_id": "cust_4xbQrmEoA5WJ01",
  "method": "upi",
  "token": {
    "max_amount": 200000,
    "expire_at": 2709971120,
    "frequency": "as_presented",
    "type": "single_block_multiple_debit"
  },
  "receipt": "Receipt No. 1",
  "description": "Monthly Pro subscription",
  "notes":{
    "note_key_1":"September",
    "note_key_2":"Make it so."
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject orderRequest = new JSONObject();
orderRequest.put("amount", 100);
orderRequest.put("currency", "INR");
orderRequest.put("customer_id", "cust_4xbQrmEoA5WJ01");
orderRequest.put("method", "upi");
orderRequest.put("receipt", "receipt#1");
JSONObject token = new JSONObject();
token.put("max_amount","200000"); 
token.put("expire_at","2709971120");
token.put("frequency","as_presented");
token.put("type","single_block_multiple_debit");
orderRequest.put("token", token);
JSONObject notes = new JSONObject();
notes.put("notes_key_1","September");
notes.put("notes_key_2","Make it so.");
orderRequest.put("notes", notes);

Order order = razorpay.orders.create(orderRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->order->create(array('amount' => 0,'currency' => 'INR','method' => 'upi','customer_id' => 'cust_4xbQrmEoA5WJ01', 'token' => array('max_amount' => 200000, 'expire_at' => 2709971120, 'frequency' => 'as_presented', 'type'=> 'single_block_multiple_debit'),'receipt' => 'Receipt No. 1' ,'notes' => array('notes_key_1' => 'September','notes_key_2' => 'Make it so.')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.orders.create({
  amount: 0,
  currency: "INR",
  method: "upi",
  customer_id: "cust_1Aa00000000001",
  receipt: "Receipt No. 1",
  notes: {
    notes_key_1: "September",
    notes_key_2: "Make it so."
  },
  token: {
    max_amount: 9999900,
    expire_at: 4102444799,
    frequency: "as_presented",
    type: "single_block_multiple_debit"
  }
})
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.order.create({
   "amount":0,
   "currency":"INR",
   "method":"upi",
   "customer_id":"cust_1Aa00000000001",
   "receipt":"Receipt No. 1",
   "notes":{
      "notes_key_1":"September",
      "notes_key_2":"Make it so."
   },
   "token":{
      "max_amount":9999900,
      "expire_at":4102444799,
      "frequency": "as_presented",
      "type": "single_block_multiple_debit"
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
  "method": "upi",
  "customer_id": "cust_1Aa00000000001",
  "receipt": "Receipt No. 1",
  "notes": {
    "notes_key_1": "September",
    "notes_key_2": "Make it so."
  },
  "token": {
    "max_amount": 9999900,
    "expire_at": 4102444799,
    "frequency": "as_presented",
    "type": "single_block_multiple_debit"
  }
}
Razorpay.Order.create(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
   "amount":100,
   "currency":"INR",
   "customer_id":"<customerId>",
   "method":"upi",
   "token":map[string]interface{}{
      "max_amount":5000,
      "expire_at":2709971120,
      "frequency":"as_presented",
      "type": "single_block_multiple_debit"
   },
   "receipt":"Receipt No. 1",
   "notes":map[string]interface{}{
      "notes_key_1":"September",
      "notes_key_2":"Make it so.",
   },
}
body, err := client.Order.Create(data, nil)
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
  "notes": {
    "notes_key_1": "September",
    "notes_key_2": "Make it so."
    },
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

> [accordion] Request Parameters
>
> `amount` *mandatory*
> : `integer` Amount in currency subunits. The maximum amount that can be blocked is ₹10,000.
>
> `currency` *mandatory*
> : `string` The 3-letter ISO currency code for the payment. Currently, we only support `INR`.
>
> `customer_id` *mandatory*
> : `string` The unique identifier of the customer. For example, `cust_4xbQrmEoA5WJ01`.
>
> `method` *mandatory*
> : `string` The authorisation method. Here, it is `upi`.
>
> `receipt` *optional*
> : `string` A user-entered unique identifier of the order. For example, `Receipt No. 1`. You should map this parameter to the `order_id` sent by Razorpay.
>
> `description` *optional*
> : `string` A description of the mandate that will be displayed to the customer in their UPI app. This helps the customer understand what they are subscribing to. Keep it under 50 characters and avoid special characters. For example, `Monthly Pro subscription`.
>
> `notes`*optional*
> : `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters each. For example, `"note_key": "Beam me up Scotty”`.
>
> `token`
> : `object` Details related to the authorisation such as max amount, frequency and expiry information.
>
> `max_amount` *mandatory*
> : `integer` The maximum amount that can be debited is ₹10,000.
>
> `expire_at` *mandatory*
> : `integer` The Unix timestamp that indicates when the authorisation transaction must expire. The default and the maximum value allowed is 90 days.
>
> `frequency` *mandatory*
> : `string` The frequency at which you can charge your customer. The value should be `as_presented`.
>
> `type` *mandatory*
> : `string` Indicates the type of payment. Here, the possible value is `single_block_multiple_debit`.

### 1.3 Create an Authorisation Payment

Create a payment using Razorpay Custom Checkout for customers to complete the Authorisation Transaction and register their mandate. You can use the Handler Function or Callback URL.

| **Handler Function** | **Callback URL** |
| - | - |
| When you use the handler function, the response object of the successful payment (`razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature`) is submitted to the Checkout Form. You need to collect these and send them to your server. | When you use a Callback URL, the response object of the successful payment (`razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature`) is submitted to the Callback URL. |

> [!WARNING]
>
> **Watch Out!**
>
> The callback URL is not supported for recurring payments created using the registration link.

> [accordion] UPI Intent
>
> UPI Intent is supported on **mWeb (Android)** and **Mobile App (WebView)**. On **Desktop Web**, as UPI Intent is not supported, a QR code is automatically displayed instead.
>
> If UPI Intent is not enabled on your account, please reach out to the [support team](https://razorpay.com/support).
>
> | Platform | Steps |
> | - | - |
> | **mWeb** | Businesses are redirected to their preferred UPI app to complete the payment. For the complete integration guide, refer to [UPI Intent on Mobile Web](https://razorpay.com/docs/payments/payment-methods/upi/upi-intent.md#integrate-on-android-ios-and-mobile-web). |
> | **Mobile App (WebView)** | UPI Intent requires passing `webview_intent: true` in the checkout options and implementing deep link handling in your Android or iOS app. For the complete integration guide, refer to [UPI Intent in WebView — Android](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/webview/upi-intent-android.md) and [UPI Intent in WebView — iOS](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/webview/upi-intent-ios.md). |
> | **Desktop Web** | UPI Intent is not supported. A QR code is automatically displayed for businesses to scan with their preferred UPI app. No additional code changes are required. |
>
> ```html Custom Checkout with Handler Function theme={null}
> <button id="btn" style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">Pay</button>
> <script type="text/javascript" src="https://checkout.razorpay.com/v1/razorpay.js"></script>
> <script>
>   const btn = document.querySelector("#btn");
>   var razorpay = new Razorpay({
>     key: "<YOUR_KEY_ID>",
>     image: "https://i.imgur.com/n5tjHFD.jpg"
>   });
>
>   var data = {
>     "amount": 100,
>     "currency": "INR",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9123456780",
>     "order_id": "order_1Aa00000000001",
>     "customer_id": "cust_1Aa00000000001",
>     "recurring": "1",
>     "method": "upi"
>   };
>
>   btn.addEventListener("click", function() {
>     razorpay.createPayment(data);
>     razorpay.on("payment.success", function(resp) {
>       alert(resp.razorpay_payment_id);
>       alert(resp.razorpay_order_id);
>       alert(resp.razorpay_signature);
>     });
>     razorpay.on("payment.error", function(resp) {
>       alert(resp.error.description);
>     });
>   });
> </script>
> ```
>
> ```html Custom Checkout with Callback URL theme={null}
> <button id="btn" style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">Pay</button>
> <script type="text/javascript" src="https://checkout.razorpay.com/v1/razorpay.js"></script>
> <script>
>   const btn = document.querySelector("#btn");
>   var razorpay = new Razorpay({
>     key: "<YOUR_KEY_ID>",
>     image: "https://i.imgur.com/n5tjHFD.jpg"
>   });
>
>   var data = {
>     "callback_url": "https://example-callback-url.com/",
>     "amount": 100,
>     "currency": "INR",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9123456780",
>     "order_id": "order_1Aa00000000001",
>     "customer_id": "cust_1Aa00000000001",
>     "recurring": "1",
>     "method": "upi"
>   };
>
>   btn.addEventListener("click", function() {
>     razorpay.createPayment(data);
>   });
> </script>
> ```

> [accordion] UPI Collect
>
> > [!WARNING]
> >
> > **Deprecation Notice**
> >
> > **UPI Collect is deprecated effective 28 February 2026.** This section is applicable only for exempted businesses. If you are an existing Razorpay user not covered by the exemptions, refer to the [migration documentation](https://razorpay.com/docs/announcements/upi-collect-migration/recurring-payments/custom-checkout) to switch to UPI Intent.
>
> ```html Custom Checkout with Handler Function theme={null}
> <button id="btn" style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">Pay</button>
> <script type="text/javascript" src="https://checkout.razorpay.com/v1/razorpay.js"></script>
> <script>
>   const btn = document.querySelector("#btn");
>   var razorpay = new Razorpay({
>     key: "<YOUR_KEY_ID>",
>     image: "https://i.imgur.com/n5tjHFD.jpg"
>   });
>
>   var data = {
>     "amount": 100,
>     "currency": "INR",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9123456780",
>     "order_id": "order_1Aa00000000001",
>     "customer_id": "cust_1Aa00000000001",
>     "recurring": "1",
>     "method": "upi",
>     "upi": {
>       "vpa": "gaurav.kumar@somebank",
>       "flow": "collect"
>     }
>   };
>
>   btn.addEventListener("click", function() {
>     razorpay.createPayment(data);
>     razorpay.on("payment.success", function(resp) {
>       alert(resp.razorpay_payment_id);
>       alert(resp.razorpay_order_id);
>       alert(resp.razorpay_signature);
>     });
>     razorpay.on("payment.error", function(resp) {
>       alert(resp.error.description);
>     });
>   });
> </script>
> ```
>
> ```html Custom Checkout with Callback URL theme={null}
> <button id="btn" style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">Pay</button>
> <script type="text/javascript" src="https://checkout.razorpay.com/v1/razorpay.js"></script>
> <script>
>   const btn = document.querySelector("#btn");
>   var razorpay = new Razorpay({
>     key: "<YOUR_KEY_ID>",
>     image: "https://i.imgur.com/n5tjHFD.jpg"
>   });
>
>   var data = {
>     "callback_url": "https://example-callback-url.com/",
>     "amount": 100,
>     "currency": "INR",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9123456780",
>     "order_id": "order_1Aa00000000001",
>     "customer_id": "cust_1Aa00000000001",
>     "recurring": "1",
>     "method": "upi",
>     "upi": {
>       "vpa": "gaurav.kumar@somebank",
>       "flow": "collect"
>     }
>   };
>
>   btn.addEventListener("click", function() {
>     razorpay.createPayment(data);
>   });
> </script>
> ```

#### Additional Checkout Fields

`customer_id` *mandatory*
: `string` Unique identifier of the customer created in the [first step](#1-1-create-a-customer).

`order_id` *mandatory*
: `string` Unique identifier of the  order created in the [second step](#1-2-create-an-order).

`recurring` *mandatory*
: `string` Determines if the recurring payment is enabled or not. Possible values:

* `1`: Recurring payment is enabled.
* `preferred`: Use this if you want to allow **recurring payments** and **one-time payment** in the same flow.

#### Error Response Parameters

Given below is a list of possible errors you may face while making the authorisation payment.

> [accordion] bad\_request\_error
>
> * **Description**: Invalid Mandate Sequence Number.
> * **Next Steps**: Retry after some time during the valid cycle.

> [accordion] bank\_account\_invalid
>
> * **Description**: Payment failed because Account linked to VPA is invalid.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] bank\_account\_validation\_failed
>
> * **Description**: Payment was unsuccessful as the details are invalid. Please retry with the right details.
> * **Next Steps**: Ask the customer to retry again.

> [accordion] bank\_not\_available
>
> * **Description**: Payment was unsuccessful as the bank linked to this UPI ID is temporarily unavailable. Any amount deducted will be refunded within 5-7 working days.
> * **Next Steps**: Retry after some time.

> [accordion] bank\_technical\_error
>
> > [accordion] Bank Temporarily Unavailable
> >
> > * **Description**: Payment was unsuccessful as the bank linked to this UPI ID is temporarily unavailable. Any amount deducted will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] Temporary Bank Issue
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue at your bank. Any amount deducted will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] Bank Declined
> >
> > * **Description**: Payment was unsuccessful as it was declined by your bank. Any amount deducted will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] Bank or Wallet Gateway Error
> >
> > * **Description**: Payment processing failed due to error at bank or wallet gateway.
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

> [accordion] duplicate\_mandate\_request
>
> * **Description**: Duplicate mandate request. Please try again with another mandate request.
> * **Next Steps**: Please try again with another mandate request.

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

> [accordion] incorrect\_pin
>
> * **Description**: You have entered an incorrect PIN on the UPI app. Please retry with the correct PIN.
> * **Next Steps**: Ask the customer to retry with correct PIN.

> [accordion] insufficient\_funds
>
> * **Description**: Transaction failed due to insufficient funds.
> * **Next Steps**: Ask the customer to add balance to their account and retry.

> [accordion] invalid\_request
>
> * **Description**: Payment processing failed due to error at bank or wallet gateway.
> * **Next Steps**: Retry after some time.

> [accordion] invalid\_response\_from\_gateway
>
> * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> * **Next Steps**: Retry after some time.

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

> [accordion] mandate\_debit\_beyond\_psp\_amount\_cap
>
> * **Description**: Debit amount is beyond payer PSP specified amount cap. Please reduce the amount and try again.
> * **Next Steps**: Please reduce the mandate amount to match customer PSP.

> [accordion] mandate\_request\_limit\_breached
>
> * **Description**: Maximum number of mandate creation requests exceeded for customer's bank account. Please wait for some time before initiating new mandate creation requests.
> * **Next Steps**: Please wait for some time before initiating new mandate creation requests.

> [accordion] mobile\_number\_invalid
>
> * **Description**: Registered Mobile number linked to the account has been changed or removed.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] nature\_of\_debit\_not\_allowed
>
> * **Description**: Nature of debit not allowed in customer's account. Please ask the customer to use a different bank account.
> * **Next Steps**: Please ask the customer to use a different bank account.

> [accordion] no\_financial\_address\_record\_found
>
> * **Description**: No financial address record found for this VPA. Please ask customer to try with another bank account.
> * **Next Steps**: Please ask customer to try with other bank account.

> [accordion] no\_original\_request\_found
>
> * **Description**: No mandate details were found in the record during debit. Please try after some time.
> * **Next Steps**: Please try after some time.

> [accordion] payment\_collect\_request\_expired
>
> * **Description**: Payment was unsuccessful as you could not pay with the UPI app within time.
> * **Next Steps**: Retry after some time.

> [accordion] payment\_declined
>
> > [accordion] Bank Declined Payment
> >
> > * **Description**: Payment was unsuccessful as it was declined by your bank. Any amount deducted will be refunded within 5-7 working days.
> > * **Next Steps**: Ask the customer to retry with other account.
>
> > [accordion] Customer Declined Payment
> >
> > * **Description**: You have declined the payment request on the UPI app. Please retry when you are ready.
> > * **Next Steps**: Ask the customer to approve the payment.

> [accordion] payment\_failed
>
> * **Description**: Payment was unsuccessful due to a temporary issue. If amount got deducted, it will be refunded within 5-7 working days.
> * **Next Steps**: Retry after 1 hour.

> [accordion] payment\_pending
>
> * **Description**: The status of your payment is pending. You can either wait or retry to pay successfully.
> * **Next Steps**: Retry after some time.

> [accordion] payment\_risk\_check\_failed
>
> * **Description**: Payment was unsuccessful as your account does not pass the risk checks done by your bank. Try using another account.
> * **Next Steps**: Retry after some time.

> [accordion] payment\_timed\_out
>
> * **Description**: Payment was unsuccessful as you could not complete it in time.
> * **Next Steps**: Retry after some time.

> [accordion] pre\_debit\_notification\_failed
>
> * **Description**: Unable to Notify the Customer.
> * **Next Steps**: Retry after some time.

> [accordion] remitter\_dispatch\_failed
>
> * **Description**: Payment failed due to some issue at the customer's. Please try again after some time.
> * **Next Steps**: Please try again after some time.

> [accordion] request\_timed\_out
>
> > [accordion] General Timeout - Temporary Issue
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] Timeout - Bank Declined
> >
> > * **Description**: Payment was unsuccessful as it was declined by your bank. Any amount deducted will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] Timeout - Recurring Payment Creation
> >
> > * **Description**: Payment was unsuccessful as the recurring payment can not be created at this time. Any amount deducted will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after some time.

> [accordion] transaction\_frequency\_limit\_exceeded
>
> * **Description**: Payment failed. Please try again with another bank account.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] transaction\_limit\_exceeded
>
> > [accordion] Amount Limit Exceeded
> >
> > * **Description**: Payment failed because Transaction amount limit has exceeded.
> > * **Next Steps**: Reach out to the customer to collect the amount.
>
> > [accordion] Bank Account Amount Limit
> >
> > * **Description**: Payment was unsuccessful as you exceeded the amount limit on the bank account linked to this UPI ID.
> > * **Next Steps**: Ask the customer to retry after some time.

> [accordion] transaction\_not\_allowed
>
> * **Description**: Payment was unsuccessful as it was declined by your bank. Reach out to your bank for more details. Try using another account.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] upi\_dummy\_payment
>
> * **Description**: Payment was a dummy payment for one time mandate registration.
> * **Next Steps**: NA
