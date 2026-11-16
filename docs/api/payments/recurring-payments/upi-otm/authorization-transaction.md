> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# 1. Create the Authorisation Transaction

> Steps to create an authorisation transaction for UPI one time mandate.

Available in
🇮🇳 India

Create a one time mandate on UPI to let your customers block an amount and pay later. The amount gets blocked on the customer's bank account and can be debited once within the expiry of the mandate. A one time mandate on UPI can help charge customers post-delivery of products or services, helping make the customer experience delightful for businesses like Ecommerce, Travel, Transport, Healthcare and many more.

**Example**

Gaurav Kumar wants to reserve a room at Acme Hotel. However, he is still determining the travel plan. He wants to pay after check-in.

Using UPI One Time Mandate, Gaurav Kumar can consent to block the hotel booking amount and only let Acme Hotel debit the amount after check-in.

To create a one time mandate:

1. [Create an authorisation transaction](#create-an-authorisation-transaction)
2. [Fetch and manage tokens](https://razorpay.com/docs/payments/payment-gateway/s2s-integration/recurring-payments/upi-otm/tokens.md)
3. [Create a one time mandate](https://razorpay.com/docs/payments/payment-gateway/s2s-integration/recurring-payments/upi-otm/one-time-payment.md)

## Create an Authorisation Transaction

You can create an authorisation transaction using the [Razorpay APIs](#1-1-using-razorpay-apis) or [Registration Link](#1-2-using-a-registration-link).

## 1.1 Using Razorpay APIs

To create an authorisation transaction using the Razorpay APIs, you need to:

1. [Create a Customer](#1-1-1-create-a-customer).
2. [Create an Order](#1-1-2-create-an-order).
3. [Create Authorisation Payment using Razorpay APIs](#1-1-3-create-an-authorisation-payment).

### 1.1.1 Create a Customer

Razorpay links recurring tokens to customers using a unique identifier generated through the Customer API.

You can create [customers](https://razorpay.com/docs/api/customers.md) with basic information such as `email` and `contact` and use them for various Razorpay offerings. The following endpoint creates a customer.

`POST /customers`

> [accordion] Sample Code
>
> > [!NOTE]
> >
> > ```bash Curl theme={null}
> > curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
> > -X POST https://api.razorpay.com/v1/customers \
> > -H "Content-Type: application/json" \
> > -d '{
> >   "name": "<name>",
> >   "email": "<email>",
> >   "contact": "<phone>",
> >   "fail_existing": "0",
> >   "notes":{
> >     "note_key_1": "September",
> >     "note_key_2": "Make it so."
> >   }
> > }'
> >
> > ```
> >
> > ```java Java theme={null}
> > RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
> >
> > JSONObject customerRequest = new JSONObject();
> > customerRequest.put("name","<name>");
> > customerRequest.put("contact","<phone>");
> > customerRequest.put("email","<email>");
> > customerRequest.put("fail_existing", "0");
> > JSONObject notes = new JSONObject();
> > notes.put("notes_key_1","Tea, Earl Grey, Hot");
> > notes.put("notes_key_2","Tea, Earl Grey… decaf.");
> > customerRequest.put("notes",notes);
> >
> > Customer customer = razorpay.customers.create(customerRequest);
> >
> > ```
> >
> > ```python Python theme={null}
> > import razorpay
> > client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
> >
> > client.customer.create({
> >     'name': '<name>',
> >     'email': '<email>',
> >     'contact': '<phone>',
> >     'fail_existing': "0",
> >     'notes': {'note_key_1': 'September', 'note_key_2': 'Make it so.'}
> >     })
> >
> > ```
> >
> > ```go Go theme={null}
> > import ( razorpay "github.com/razorpay/razorpay-go" )
> > client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
> >
> > data := map[string]interface{}{
> >     "name": "<name>",
> >     "contact": <phone>,
> >     "email": "<email>",
> >     "fail_existing": "0",
> >     "notes": map[string]interface{}{
> >         "notes_key_1": "Tea, Earl Grey, Hot",
> >         "notes_key_2": "Tea, Earl Grey… decaf.",
> >     },
> > }
> > body, err := client.Customer.Create(data, nil)
> >
> > ```
> >
> > ```php PHP theme={null}
> > $api = new Api($key_id, $secret);
> >
> > $api->customer->create(array('name' => '<name>', 'email' => '<email>','contact'=>'<phone>','fail_existing' => "0", 'notes'=> array('notes_key_1'=> 'Tea, Earl Grey, Hot','notes_key_2'=> 'Tea, Earl Grey… decaf'));
> > ```
> >
> > ```csharp .NET theme={null}
> > RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
> >
> > Dictionary<string, object> options = new Dictionary<string,object>();
> >
> > options.Add("name", "<name>"); 
> > options.Add("contact", "<phone>"); 
> > options.Add("email", "<email>"); 
> > options.Add("fail_existing", "0"); 
> >
> > Customer customer = Customer.Create(options);
> >
> > ```
> >
> > ```ruby Ruby theme={null}
> > require "razorpay"
> > Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
> >
> > para_attr = {
> >   "name": "<name>",
> >   "contact": "<phone>",
> >   "email": "<email>",
> >   "fail_existing": "0",
> >   "notes": {
> >     "notes_key_1": "Tea, Earl Grey, Hot",
> >     "notes_key_2": "Tea, Earl Grey… decaf."
> >   }
> > }
> >
> > Razorpay::Customer.create(para_attr)
> >
> > ```
> >
> > ```javascript Node.js theme={null}
> > var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
> >
> > instance.customers.create({
> >   name: "<name>",
> >   contact: "<phone>",
> >   email: "<email>",
> >   fail_existing: "0",
> >   notes: {
> >     notes_key_1: "Tea, Earl Grey, Hot",
> >     notes_key_2: "Tea, Earl Grey… decaf."
> >   }
> > })
> > ```
> >
> > ```json Response theme={null}
> > {
> >   "id":"cust_1Aa00000000001",
> >   "entity":"customer",
> >   "name":"<name>",
> >   "email":"<email>",
> >   "contact":"<phone>",
> >   "gstin":null,
> >   "notes":{
> >       "note_key_1":"September",
> >       "note_key_2":"Make it so."
> >   },
> >   "created_at ":1234567890
> > }
> > ```

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

### 1.1.2. Create an Order

Use the [Orders API](https://razorpay.com/docs/api/orders.md) to create a unique Razorpay `order_id` that is associated with the authorisation transaction for a one time mandate. To create a one-time mandate, pass the value of the `frequency` parameter as `one_time`. The following endpoint creates an order.

`POST /orders`

> [!NOTE]
>
> ```bash Curl theme={null}
> curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
> -X POST https://api.razorpay.com/v1/orders \
> -H "Content-Type: application/json" \
> -d '{
>   "amount": 100,
>   "currency": "INR",
>   "customer_id": "cust_4xbQrmEoA5WJ01",
>   "method": "upi",
>   "token": {
>     "max_amount": 200000,
>     "expire_at": 2709971120,
>     "frequency": "one_time"
>   },
>   "receipt": "Receipt No. 1",
>   "description": "Monthly Pro subscription",
>   "notes": {
>     "notes_key_1": "Tea, Earl Grey, Hot",
>     "notes_key_2": "Tea, Earl Grey… decaf."
>   }
> }'
>
> ```
>
> ```java Java theme={null}
> RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> JSONObject orderRequest = new JSONObject();
> orderRequest.put("amount", 100);
> orderRequest.put("currency", "INR");
> orderRequest.put("customer_id", "cust_4xbQrmEoA5WJ01");
> orderRequest.put("method", "upi");
> orderRequest.put("receipt", "receipt#1");
> JSONObject token = new JSONObject();
> token.put("max_amount","200000"); 
> token.put("expire_at","2709971120");
> token.put("frequency","one_time");
> orderRequest.put("token", token);
> JSONObject notes = new JSONObject();
> notes.put("notes_key_1","Tea, Earl Grey, Hot");
> notes.put("notes_key_2","Tea, Earl Grey… decaf.");
> orderRequest.put("notes", notes);
>
> Order order = razorpay.orders.create(orderRequest);
>
> ```
>
> ```php PHP theme={null}
> $api = new Api($key_id, $secret);
>
> $api->order->create(array('amount' => 0,'currency' => 'INR','method' => 'upi','customer_id' => 'cust_4xbQrmEoA5WJ01', 'token' => array('max_amount' => 200000, 'expire_at' => 2709971120, 'frequency' => 'one_time'),'receipt' => 'Receipt No. 1' ,'notes' => array('notes_key_1' => 'Beam me up Scotty','notes_key_2' => 'Engage')));
>
> ```
>
> ```javascript Node.js theme={null}
> var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
>
> instance.orders.create({
>   amount: 0,
>   currency: "INR",
>   method: "upi",
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
>     frequency: "one_time",
>     notes: {
>       notes_key_1: "Tea, Earl Grey, Hot",
>       notes_key_2: "Tea, Earl Grey… decaf."
>     }
>   }
> })
>
> ```
>
> ```python Python theme={null}
> client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
> client.order.create({
>    "amount":0,
>    "currency":"INR",
>    "method":"upi",
>    "customer_id":"cust_1Aa00000000001",
>    "receipt":"Receipt No. 1",
>    "notes":{
>       "notes_key_1":"Beam me up Scotty",
>       "notes_key_2":"Engage"
>    },
>    "token":{
>       "auth_type":"netbanking",
>       "max_amount":9999900,
>       "expire_at":4102444799,
>       "frequency": "one_time",
>       "notes":{
>          "notes_key_1":"Tea, Earl Grey, Hot",
>          "notes_key_2":"Tea, Earl Grey… decaf."
>       }
>    }
> })
>
> ```
>
> ```ruby Ruby theme={null}
> require "razorpay"
> Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
>
> para_attr = {
>   "amount": 0,
>   "currency": "INR",
>   "method": "upi",
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
>     "frequency": "one_time",
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf."
>     }
>   }
> }
> Razorpay.Order.create(para_attr)
>
> ```
>
> ```go Go theme={null}
> import ( razorpay "github.com/razorpay/razorpay-go" )
> client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
> data := map[string]interface{}{
>    "amount":100,
>    "currency":"INR",
>    "customer_id":"<customerId>",
>    "method":"upi",
>    "token":map[string]interface{}{
>       "max_amount":5000,
>       "expire_at":2709971120,
>       "frequency":"one_time"
>    },
>    "receipt":"Receipt No. 1",
>    "notes":map[string]interface{}{
>       "notes_key_1":"Tea, Earl Grey, Hot",
>       "notes_key_2":"Tea, Earl Grey... decaf.",
>    },
> }
> body, err := client.Order.Create(data, nil)
> ```

> [!NOTE]
>
> ```json Success Response theme={null}
> {
>   "id": "order_1Aa00000000002",
>   "entity": "order",
>   "amount": 100,
>   "amount_paid": 0,
>   "amount_due": 100,
>   "currency": "INR",
>   "receipt": "Receipt No. 1",
>   "offer_id": null,
>   "status": "created",
>   "attempts": 0,
>   "notes": {
>     "notes_key_1": "Tea, Earl Grey, Hot",
>     "notes_key_2": "Tea, Earl Grey… decaf."
>     },
>   "created_at": 1565172642
> }
>
> ```
>
> ```json Failure Response theme={null}
> {
>    "error":{
>       "code":"BAD_REQUEST_ERROR",
>       "description":"The api key provided is invalid",
>       "source":"NA",
>       "step":"NA",
>       "reason":"NA",
>       "metadata":{
>
>       }
>    }
> }
> ```

> [accordion] Request Parameters
>
> `amount` *mandatory*
> : `integer` Amount in currency subunits.
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
> : `integer` The maximum amount that can be debited in a single charge.
>
> | MCC | Category | Min Value | Max Value |
> | - | - | - | - |
> | 6211 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
> | 6300 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
> | 7322 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
> | 6529 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
> | 5960 | Services | `100` (₹1) | `20000000` (₹2,00,000) |
>
> For other categories and MCCs, the minimum value is `100` (₹1) and maximum value is 9999900 (₹99,999).
>
> > [!NOTE]
> >
> > **Best Practices**
> >
> > Set the `max_amount` as close to the actual debit amount as possible. For example, if the expected debit amount is ₹99-₹299, setting the `max_amount` to ₹5,000 may cause the customer to drop off due to trust issues. A realistic `max_amount` builds customer trust while allowing flexibility for variable debits.
>
> `expire_at` *mandatory*
> : `integer` The Unix timestamp at which the authorisation transaction expires. For insurance MCCs (6300, 5960, 6529), the maximum validity is 14 days. For all other MCCs, the maximum validity is 30 years.
>
> `frequency` *mandatory*
> : `string` The frequency at which you can charge your customer. The value should be `one_time` for one time mandate.

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

> [!NOTE]
>
> ```html Checkout with handler functions theme={null}
> <button id = "rzp-button1"> Pay </button>
>   <script src = "https://checkout.razorpay.com/v1/checkout.js"> </script>
>   <script>
>     var options = {
>       "key": "[YOUR_KEY_ID]",
>       "order_id": "order_1Aa00000000001",
>       "customer_id": "cust_1Aa00000000001",
>       "recurring": true,
>       "handler": function (response) {
>         alert(response.razorpay_payment_id);
>         alert(response.razorpay_order_id);
>         alert(response.razorpay_signature);
>       },
>       "notes":{
>           "note_key_1":"September",
>           "note_key_2":"Make it so."
>       },
>       "theme": {
>         "color": "#F37254"
>       }
>     };
>     var rzp1 = new Razorpay(options);
>     document.getElementById('rzp-button1').onclick = function (e) {
>       rzp1.open();
>       e.preventDefault();
>     }
>   </script>
> ```
>
> ```html Manual checkout with Callback URL theme={null}
> <button id = "rzp-button1"> Pay </button>
>   <script src = "https://checkout.razorpay.com/v1/checkout.js"> </script>
>   <script>
>     var options = {
>       "key": "[YOUR_KEY_ID]",
>       "order_id": "order_1Aa00000000001",
>       "customer_id": "cust_1Aa00000000001",
>       "recurring": true,
>       "callback_url": "https://eneqd3r9zrjok.x.pipedream.net/",
>       "notes":{
>           "note_key_1":"September",
>           "note_key_2":"Make it so."
>       },
>       "theme": {
>         "color": "#F37254"
>       }
>     };
>     var rzp1 = new Razorpay(options);
>     document.getElementById('rzp-button1').onclick = function (e) {
>       rzp1.open();
>       e.preventDefault();
>     }
>   </script>
> ```

#### Additional Checkout Fields

`customer_id` *mandatory*
: `string` Unique identifier of the customer created in the [first step](#1-1-1-create-a-customer).

`order_id` *mandatory*
: `string` Unique identifier of the  order created in the [second step](#1-1-2-create-an-order).

`recurring` *mandatory*
: `string` Determines if the recurring payment is enabled or not. Possible values:

* `1`: Recurring payment is enabled.
* `preferred`: Use this if you want to allow **recurring payments** and **one-time payment** in the same flow.

#### Error Response Parameters

Given below is a list of possible errors you may face while making the authorisation payment.

> [accordion] adequate\_funds\_not\_available\_blocked
>
> * **Description**: Sufficient unblocked funds not available in customer's account. Please ask customer to add fund and try again.
> * **Next Steps**: Please ask customer to add sufficient unblocked funds and try again.

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
> > * **Description**: Payment was unsuccessful as you exceeded the amount limit on the bank account linked to this UPI id.
> > * **Next Steps**: Ask the customer to retry after some time.

> [accordion] transaction\_not\_allowed
>
> * **Description**: Payment was unsuccessful as it was declined by your bank. Reach out to your bank for more details. Try using another account.
> * **Next Steps**: Create a new mandate with the customer.

> [accordion] upi\_dummy\_payment
>
> * **Description**: Payment was a dummy payment for one time mandate registration.
> * **Next Steps**: NA

## 1.2. Using a Registration Link

Registration Links are an alternate way of creating an authorisation transaction. If you create a registration link, you need not create a customer or an order.

When you create a registration link, an [invoice](https://razorpay.com/docs/payments/invoices) is automatically issued to the customer. The customer can use the invoice to make the Authorisation Payment.

> [!NOTE]
>
> **Handy Tips**
>
> You can use [Token Webhooks](https://razorpay.com/docs/api/payments/recurring-payments/webhooks.md#check-registration-link-status-using-webhooks) to get notifications about successful payments against a registration link. Do not use payment webhooks for Authorisation Payments.

### 1.2.1. Create a Registration Link

The following endpoint creates a registration link you can share with your customers to make one time mandate payments. This is a dummy transaction that fails with an error `BAD_REQUEST_ERROR` when a customer tries to approve the mandate request from a PSP application. A token is created and marked as `confirmed` for the same.

`POST /subscription_registration/auth_links`

> [!NOTE]
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
>    "type": "link",
>    "amount": "100",
>    "currency": "INR",
>    "description": "Registration Link for Gaurav Kumar",
>    "subscription_registration": {
>       "method": "upi",
>       "max_amount": "500",
>       "expire_at": 4102444799,
>       "frequency": "one_time"
>    },
>    "receipt": "Receipt No. 23",
>    "email_notify": true,
>    "sms_notify": true,
>    "expire_by": 4102444799,
>    "notes":{
>     "note_key 1":"Beam me up Scotty",
>     "note_key 2":"Tea. Earl Gray. Hot."
>   }
> }'
>
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
> registrationLinkRequest.put("amount", 100);
> registrationLinkRequest.put("currency", "INR");
> registrationLinkRequest.put("description", "Registration Link for Gaurav Kumar");
> JSONObject subscriptionRegistration = new JSONObject();
> subscriptionRegistration.put("method","upi");
> subscriptionRegistration.put("max_amount",50000);
> subscriptionRegistration.put("expire_at",1609423824);
> subscriptionRegistration.put("frequency","one_time");
> registrationLinkRequest.put("subscription_registration", subscriptionRegistration);
> registrationLinkRequest.put("receipt", "Receipt No. #112");
> registrationLinkRequest.put("email_notify", true);
> registrationLinkRequest.put("sms_notify", true);
> registrationLinkRequest.put("expire_by", 1580479824);
> JSONObject notes = new JSONObject();
> notes.put("notes_key_1","Tea, Earl Grey, Hot");
> notes.put("notes_key_2","Tea, Earl Grey… decaf.");
> registrationLinkRequest.put("notes", notes);
>
> Invoice invoice = razorpay.invoices.createRegistrationLink(registrationLinkRequest);
>
> ```
>
> ```php PHP theme={null}
> $api = new Api($key_id, $secret);
>
> $api->subscription->createSubscriptionRegistration(array('customer'=>array('name'=>'Gaurav Kumar','email'=>'gaurav.kumar@example.com','contact'=>'9123456780'),'type'=>'link','amount'=>100,'currency'=>'INR','description'=>'Registration Link for Gaurav Kumar','subscription_registration'=>array('method'=>'upi','max_amount'=>'500','expire_at'=>'1634215992','frequency'=>'one_time'),'receipt'=>'Receipt No. 5','email_notify'=>true,'sms_notify'=>true,'expire_by'=>1634215992,'notes' => array('note_key 1' => 'Beam me up Scotty','note_key 2' => 'Tea. Earl Gray. Hot.')));
>
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
>   amount: 100,
>   currency: "INR",
>   description: "Registration Link for Gaurav Kumar",
>   subscription_registration: {
>     method: "upi",
>     max_amount: 500,
>     expire_at: 1634215992,
>     frequency: "one_time"
>   },
>   receipt: "Receipt No. 5",
>   email_notify: true,
>   sms_notify: true,
>   expire_by: 1634215992,
>   notes: {
>     "note_key 1": "Beam me up Scotty",
>     "note_key 2": "Tea. Earl Gray. Hot."
>   }
> })
>
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
>   "amount": 100,
>   "currency": "INR",
>   "description": "Registration Link for Gaurav Kumar",
>   "subscription_registration": {
>     "method": "upi",
>     "max_amount": 500,
>     "expire_at": 1634215992,
>     "frequency": "one_time"
>   },
>   "receipt": "Receipt No. 5",
>   "email_notify": 1,
>   "sms_notify": 1,
>   "expire_by": 1634215992,
>   "notes": {
>     "note_key 1": "Beam me up Scotty",
>     "note_key 2": "Tea. Earl Gray. Hot."
>   }
> }
> Razorpay::SubscriptionRegistration.create(para_attr)
>
> ```
>
> ```python Python theme={null}
> client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
> client.registration_link.create({
>    "customer":{
>       "name":"Gaurav Kumar",
>       "email":"gaurav.kumar@example.com",
>       "contact":9123456780
>    },
>    "type":"link",
>    "amount":100,
>    "currency":"INR",
>    "description":"12 p.m. Meals",
>    "subscription_registration":{
>       "method":"upi",
>       "expire_at":1580480689,
>       "max_amount":500,
>       "frequency": "one_time"
>    },
>    "receipt":"Receipt no. 1",
>    "expire_by":1880480689,
>    "sms_notify": True,
>    "email_notify": True,
>    "notes":{
>       "note_key 1":"Beam me up Scotty",
>       "note_key 2":"Tea. Earl Gray. Hot."
>    }
> })
>
> ```
>
> ```go Go theme={null}
> import ( razorpay "github.com/razorpay/razorpay-go" )
> client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
> data:= map[string]interface{}{
>   "customer":map[string]interface{}{
>     "name":"Gaurav Kumar",
>     "email":"gaurav.kumar@example.com",
>     "contact":"9123456780",
>   },
>   "type":"link",
>   "amount":"100",
>   "currency":"INR",
>   "description":"Registration Link for Gaurav Kumar",
>   "subscription_registration":map[string]interface{}{
>     "method":"upi",
>     "max_amount":"500",
>     "expire_at":1609423824,
>     "frequency": "one_time"
>   },
>   "receipt":"Receipt No. 1",
>   "email_notify":true,
>   "sms_notify":true,
>   "expire_by":1681987284,
>   "notes":map[string]interface{}{
>     "note_key 1":"Beam me up Scotty",
>     "note_key 2":"Tea. Earl Gray. Hot.",
>   },
> }
> body, err := client.Invoice.CreateRegistrationLink(data, nil)
> ```
>
> ```json Response theme={null}
> {
>   "id": "inv_FHr1ekX0r2VCVK",
>   "entity": "invoice",
>   "receipt": "Receipt No. 23",
>   "invoice_number": "Receipt No. 23",
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
>   "order_id": "order_FHr1ehR3nmNeXo",
>   "line_items": [],
>   "payment_id": null,
>   "status": "issued",
>   "expire_by": 4102444799,
>   "issued_at": 1595489219,
>   "paid_at": null,
>   "cancelled_at": null,
>   "expired_at": null,
>   "sms_status": "pending",
>   "email_status": "pending",
>   "date": 1595489219,
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
>     "note_key 1": "Beam me up Scotty",
>     "note_key 2": "Tea. Earl Gray. Hot."
>   },
>   "comment": null,
>   "short_url": "https://rzp.io/i/ak1WxDB",
>   "view_less": true,
>   "billing_start": null,
>   "billing_end": null,
>   "type": "link",
>   "group_taxes_discounts": false,
>   "created_at": 1595489219,
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
> : `object` Details of the authorisation transaction.
>
> `method` *mandatory*
> : `string` The payment method used to make authorisation transaction. Here, it is `card`.
>
> `max_amount` *mandatory*
> : `integer` Use to set the maximum amount (in paise) per debit request.
>
> | MCC | Category | Min Value | Max Value |
> | - | - | - | - |
> | 6211 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
> | 6300 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
> | 7322 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
> | 6529 | Financial Services | `100` (₹1) | `20000000` (₹2,00,000) |
> | 5960 | Services | `100` (₹1) | `20000000` (₹2,00,000) |
>
> For other categories and MCCs, the minimum value is `100` (₹1) and maximum value is 9999900 (₹99,999).
>
> `expire_at` *optional*
> : `integer` The Unix timestamp till when you can use the token to charge the customer subsequent payments. The default value is 10 years and the maximum value allowed is 30 years.
>
> `frequency` *mandatory*
> : `string` The frequency at which you can charge your customer. The value should be `one_time` for one time mandate.
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

### 1.2.2. Send/Resend Notifications

The following endpoint sends/resends notifications with the short URL to the customer:

`POST /invoices/:id/notify_by/:medium`

> [accordion] Sample Code
>
> ```bash Curl theme={null}
>  curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
>  -X POST https://api.razorpay.com/v1/invoices/inv_1Aa00000000001/notify_by/sms
>
> ```
>
> ```java Java theme={null}
> RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> String invoiceId = "inv_1Aa00000000001";
>
> String medium = "sms";
>
> Invoice invoice = razorpay.invoices.notifyBy(invoiceId, medium);
>
> ```
>
> ```php PHP theme={null}
> $api = new Api($key_id, $secret);
>
> $api->invoice->fetch($invoiceId)->notify($medium);
>
> ```
>
> ```javascript Node.js theme={null}
> var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
>
> instance.invoices.notifyBy(invoiceId, medium)
>
>
> ```
>
> ```python Python theme={null}
> client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
> client.invoice.notify_by(invoiceId, medium)
>
> ```
>
> ```ruby Ruby theme={null}
> require "razorpay"
> Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
>
> invoiceId = "inv_JDdNb4xdf4gxQ7"
>
> medium = "email" 
>
> Razorpay::Invoice.notify_by(invoiceId, medium)
>
> ```
>
> ```go Go theme={null}
> import ( razorpay "github.com/razorpay/razorpay-go" )
> client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
> body, err := client.Invoice.Notify("<invoiceId>", "<medium>", nil, nil)
>
> ```
>
> ```csharp .NET theme={null}
> RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> string invoiceId = "inv_Z6t7VFTb9xHeOs";
>
> string medium = "sms";
>
> Invoice invoice = client.Invoice.Fetch(invoiceId).NotifyBy(medium);
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
>
> ```
>
> ```java Java theme={null}
> RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> String invoiceId = "inv_1Aa00000000001";
>
> Invoice invoice = razorpay.invoices.cancel(invoiceId);
>
> ```
>
> ```php PHP theme={null}
> $api = new Api($key_id, $secret);
>
> $api->invoice->fetch($invoiceId)->cancel();
> ```
>
> ```javascript Node.js theme={null}
> var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
>
> instance.invoices.cancel(invoiceId)
>
> ```
>
> ```python Python theme={null}
> client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
> client.invoice.cancel(invoiceId)
>
> ```
>
> ```ruby Ruby theme={null}
> require "razorpay"
> Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
>
> invoiceId = "inv_1Aa00000000001"
>
> Razorpay::Invoice.cancel(invoiceId)
>
> ```
>
> ```go Go theme={null}
> import ( razorpay "github.com/razorpay/razorpay-go" )
> client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
> body, err := client.Invoice.Cancel("<invoiceId>", nil, nil)
>
> ```
>
> ```csharp .NET theme={null}
> RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> string invoiceId = "inv_Z6t7VFTb9xHeOs";
>
> Invoice invoice = client.Invoice.Fetch(invoiceId).Cancel();
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
>
> ```

> [accordion] Path Parameters
>
> `id` *mandatory*
> : `string` The unique identifier for the invoice linked to the registration link that you want to cancel. For example, `inv_1Aa00000000001`.
