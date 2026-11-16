> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# 1. Create an Authorisation Transaction

> Create an authorisation transaction for UPI using Razorpay APIs and Registration Link.

Available in
🇮🇳 India

> [!WARNING]
>
> **UPI Collect Flow Deprecated**
>
> According to NPCI guidelines, the UPI Collect flow is being deprecated for new UPI Autopay registrations effective 28 February 2026.
>
> * Customers can no longer register UPI mandates by manually entering VPA/UPI id/mobile numbers.
> * Subsequent debits for existing mandates created via UPI Collect will continue to be executed without change.
>
> **Exemptions**
>
> UPI Collect will continue to be supported for:
>
> * MCC 6012 & 6211 (IPO and secondary market transactions).
> * iOS mobile app and mobile web transactions.
> * UPI Mandates (execute/modify/revoke operations only).
> * eRupi vouchers.
> * PACB businesses (cross-border/international payments).
>
> **Action Required**
>
> * If you are a new Razorpay user, use UPI Intent.
> * If you are an existing Razorpay user not covered by exemptions, you must migrate to UPI Intent or UPI QR code to continue accepting UPI Autopay registrations. For detailed migration steps, refer to the [migration documentation](https://razorpay.com/docs/announcements/upi-collect-migration/recurring-payments/standard-checkout).

A token is the unique identifier Razorpay creates for a customer's UPI Autopay mandate. It holds the mandate terms (the maximum debit amount, the frequency and the expiry), and you use its `token_id` to execute every subsequent debit. In these docs, "mandate" refers to the authorisation the customer approves in their UPI app, and "token" is the object you work with in Razorpay APIs. One mandate maps to one token.

You can create an authorisation transaction using [Razorpay APIs](#1-1-using-razorpay-apis) or [Registration Link](#1-2-using-a-registration-link).

A token changes state as the customer and your business act on it:

* If the authorisation payment fails, the token moves to the `rejected` state.
* Once a token is `confirmed`, it never moves to `rejected`. It moves only to `paused` or `cancelled`.
* When the customer resumes a `paused` token, it moves back to `confirmed`.
* When you cancel a token, it stays in the `cancellation_initiated` state until the downstream partner confirms the cancellation. It then moves to `cancelled`.

Refer to [Token States](https://razorpay.com/docs/api/payments/recurring-payments/upi/tokens.md#token-states) for all states and the webhooks generated for each.

## 1.1 Using Razorpay APIs

Mandate registration is the journey where the customer sets up the subscription for the first time. At Razorpay, it involves three steps: creating a customer, creating an order (to give context to the token) and creating an authorisation payment, where the first debit authorisation is performed on the customer. If the first debit fails, the registration fails. Here are the steps:

1. [Create a Customer](#1-1-1-create-a-customer) - This allows Razorpay to uniquely identify the customer and store UPI Autopay tokens against the customer ID.
2. [Create an Order](#1-1-2-create-an-order) - Send the token details required to set up UPI Autopay on the customer ID.
3. [Create an Authorisation Payment](#1-1-3-create-an-authorisation-payment) - Initialise the authorisation journey where the actual mandate registration happens.

> [!NOTE]
>
> **Handy Tips**
>
> For the Authorisation Payment to be successful in a day (for example, 5th June), you should create an Order and the Authorisation Transaction on the same day (5th June) before 11:59 pm.

### 1.1.1 Create a Customer

Razorpay links recurring tokens to customers using a unique identifier generated through the Customer API.

Creating a customer is mandatory to set up a registration. You may have your own way to identify customers at your end, so passing `email` and `contact` is optional, but we recommend passing at least one of them to Razorpay. You can also use the customer for various Razorpay offerings. Know more about [Customers](https://razorpay.com/docs/api/customers.md). The following endpoint creates a customer.

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

### 1.1.2 Create an Order

Use the [Orders API](https://razorpay.com/docs/api/orders.md) to create a unique Razorpay `order_id` that is associated with the authorisation transaction. The following endpoint creates an order.

`POST /orders`

> [accordion] Sample Code
>
> > [!NOTE]
> >
> > ```bash Curl theme={null}
> > curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
> > -X POST https://api.razorpay.com/v1/orders \
> > -H "Content-Type: application/json" \
> > -d '{
> >   "amount": 100,
> >   "currency": "INR",
> >   "customer_id": "cust_4xbQrmEoA5WJ01",
> >   "method": "upi",
> >   "token": {
> >     "max_amount": 200000,
> >     "expire_at": 2709971120,
> >     "frequency": "monthly"
> >   },
> >   "receipt": "Receipt No. 1",
> >   "description": "Monthly Pro subscription",
> >   "notes": {
> >     "notes_key_1": "Tea, Earl Grey, Hot",
> >     "notes_key_2": "Tea, Earl Grey… decaf."
> >   }
> > }'
> >
> > ```
> >
> > ```java Java theme={null}
> > RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
> >
> > JSONObject orderRequest = new JSONObject();
> > orderRequest.put("amount", 100);
> > orderRequest.put("currency", "INR");
> > orderRequest.put("customer_id", "cust_4xbQrmEoA5WJ01");
> > orderRequest.put("method", "upi");
> > orderRequest.put("receipt", "receipt#1");
> > JSONObject token = new JSONObject();
> > token.put("max_amount","200000"); 
> > token.put("expire_at","2709971120");
> > token.put("frequency","monthly");
> > orderRequest.put("token", token);
> > JSONObject notes = new JSONObject();
> > notes.put("notes_key_1","Tea, Earl Grey, Hot");
> > notes.put("notes_key_2","Tea, Earl Grey… decaf.");
> > orderRequest.put("notes", notes);
> >
> > Order order = razorpay.orders.create(orderRequest);
> >
> > ```
> >
> > ```php PHP theme={null}
> > $api = new Api($key_id, $secret);
> >
> > $api->order->create(array('amount' => 0,'currency' => 'INR','method' => 'upi','customer_id' => 'cust_4xbQrmEoA5WJ01', 'token' => array('max_amount' => 200000, 'expire_at' => 2709971120, 'frequency' => 'monthly'),'receipt' => 'Receipt No. 1' ,'notes' => array('notes_key_1' => 'Beam me up Scotty','notes_key_2' => 'Engage')));
> >
> > ```
> >
> > ```javascript Node.js theme={null}
> > var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
> >
> > instance.orders.create({
> >   amount: 0,
> >   currency: "INR",
> >   method: "upi",
> >   customer_id: "cust_1Aa00000000001",
> >   receipt: "Receipt No. 1",
> >   notes: {
> >     notes_key_1: "Beam me up Scotty",
> >     notes_key_2: "Engage"
> >   },
> >   token: {
> >     auth_type: "netbanking",
> >     max_amount: 9999900,
> >     expire_at: 4102444799,
> >     notes: {
> >       notes_key_1: "Tea, Earl Grey, Hot",
> >       notes_key_2: "Tea, Earl Grey… decaf."
> >     }
> >   }
> > })
> >
> > ```
> >
> > ```python Python theme={null}
> > client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
> >
> > client.order.create({
> >    "amount":0,
> >    "currency":"INR",
> >    "method":"upi",
> >    "customer_id":"cust_1Aa00000000001",
> >    "receipt":"Receipt No. 1",
> >    "notes":{
> >       "notes_key_1":"Beam me up Scotty",
> >       "notes_key_2":"Engage"
> >    },
> >    "token":{
> >       "auth_type":"netbanking",
> >       "max_amount":9999900,
> >       "expire_at":4102444799,
> >       "notes":{
> >          "notes_key_1":"Tea, Earl Grey, Hot",
> >          "notes_key_2":"Tea, Earl Grey… decaf."
> >       }
> >    }
> > })
> >
> > ```
> >
> > ```ruby Ruby theme={null}
> > require "razorpay"
> > Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
> >
> > para_attr = {
> >   "amount": 0,
> >   "currency": "INR",
> >   "method": "upi",
> >   "customer_id": "cust_1Aa00000000001",
> >   "receipt": "Receipt No. 1",
> >   "notes": {
> >     "notes_key_1": "Beam me up Scotty",
> >     "notes_key_2": "Engage"
> >   },
> >   "token": {
> >     "auth_type": "netbanking",
> >     "max_amount": 9999900,
> >     "expire_at": 4102444799,
> >     "notes": {
> >       "notes_key_1": "Tea, Earl Grey, Hot",
> >       "notes_key_2": "Tea, Earl Grey… decaf."
> >     }
> >   }
> > }
> > Razorpay.Order.create(para_attr)
> >
> > ```
> >
> > ```go Go theme={null}
> > import ( razorpay "github.com/razorpay/razorpay-go" )
> > client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
> >
> > data := map[string]interface{}{
> >    "amount":100,
> >    "currency":"INR",
> >    "customer_id":"<customerId>",
> >    "method":"upi",
> >    "token":map[string]interface{}{
> >       "max_amount":5000,
> >       "expire_at":2709971120,
> >       "frequency":"monthly",
> >    },
> >    "receipt":"Receipt No. 1",
> >    "notes":map[string]interface{}{
> >       "notes_key_1":"Tea, Earl Grey, Hot",
> >       "notes_key_2":"Tea, Earl Grey... decaf.",
> >    },
> > }
> > body, err := client.Order.Create(data, nil)
> > ```
>
> > [!NOTE]
> >
> > ```json Success Response theme={null}
> > {
> >   "id": "order_1Aa00000000002",
> >   "entity": "order",
> >   "amount": 100,
> >   "amount_paid": 0,
> >   "amount_due": 100,
> >   "currency": "INR",
> >   "receipt": "Receipt No. 1",
> >   "offer_id": null,
> >   "status": "created",
> >   "attempts": 0,
> >   "notes": {
> >     "notes_key_1": "Tea, Earl Grey, Hot",
> >     "notes_key_2": "Tea, Earl Grey… decaf."
> >     }
> >   "created_at": 1565172642
> > }
> >
> > ```
> >
> > ```json Failure Response theme={null}
> > {
> >    "error":{
> >       "code":"BAD_REQUEST_ERROR",
> >       "description":"The api key provided is invalid",
> >       "source":"NA",
> >       "step":"NA",
> >       "reason":"NA",
> >       "metadata":{
> >
> >       }
> >    }
> > }
> > ```

> [!NOTE]
>
> **Handy Tips**
>
> The subsequent payment frequency is displayed on your customer's PSP. They can select the required frequency while registering for the mandate.

> [!NOTE]
>
> **Handy Tips**
>
> The `token.max_amount` value must respect the limits defined by NPCI for your merchant category. Refer to the [limits by MCC table](https://razorpay.com/docs/payments/recurring-payments/overview/integrate#limits-by-mcc) for the maximum mandate amount and the AFA-free limit for your MCC.

> [!NOTE]
>
> **Handy Tips**
>
> UPI Autopay supports only `INR`. Recurring payments on cards support other currencies.

> [accordion] Request Parameters
>
> `amount` *mandatory*
> : `integer` Amount, **in paise**.
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
> : Details related to the authorisation such as max amount, frequency and expiry information.
>
> `max_amount` *mandatory*
> : `integer` The maximum amount that can be debited in a single charge.
> The minimum value is `100` (₹1). For the maximum value for your MCC, refer to the [limits by MCC table](https://razorpay.com/docs/payments/recurring-payments/overview/integrate#limits-by-mcc).
>
> > [!NOTE]
> >
> > **Best Practices**
> >
> > Set the `max_amount` as close to the actual debit amount as possible. For example, if the expected debit amount is ₹99-₹299, setting the `max_amount` to ₹5,000 may cause the customer to drop off due to trust issues. A realistic `max_amount` builds customer trust while allowing flexibility for variable debits.
> >
> > Frequency also plays a crucial role in building customer trust. For example, if you are selling a monthly subscription but request an `as_presented` mandate, the customer may find it risky to set up the mandate. If your business has a flexible billing model, `as_presented` frequency fits your use case better, because NPCI has strict checks to ensure one successful debit per billing cycle.
>
> `expire_at` *mandatory*
> : `integer` The Unix timestamp that indicates when the authorisation transaction must expire. The default value is 10 years and the maximum value allowed is 30 years.
>
> `frequency` *mandatory*
> : `string` The frequency at which you can charge your customer. Possible values:
>
> * `daily`
> * `weekly`
> * `fortnightly`
> * `bimonthly`
> * `monthly`
> * `quarterly`
> * `half_yearly`
> * `yearly`
> * `as_presented`

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
> : `integer` The amount that is yet to be paid.
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

> [accordion] Error Response Parameters
>
> Given below is a list of possible errors you may face while creating an Order.
>
> | Error | Cause | Solution |
> | - | - | - |
> | The id provided does not exist | This error occurs when you enter an incorrect `customer_id.` | Make sure to enter a valid `customer_id`. |
> | The api key provided is invalid | This error occurs when you enter the wrong API key or secret. | Make sure to enter a valid API key and secret. |
> | The amount must be at least INR 1.00. | This error occurs when you enter an amount less than INR 1. | Make sure the entered amount is atleast INR 1.00. |
> | The currency should be INR when method is upi | This error occurs when you enter a currency other than INR | Make sure the currency is INR. |
> | The amount field is required. | This error occurs when you have not entered the amount or the `max_amount` value. | Make sure to enter the `max_amount` value. |
> | The minimum transaction amount allowed is Re. 5. | This error occurs when you enter the maximum amount less than the minimum amount. | Make sure the `max_amount` value is more than the `min_amount` value. |
> | The order amount cannot be greater than the token max amount for upi recurring. | This error occurs when the order amount exceeds the `token_max` amount passed in the API request payload. | Ensure the order amount is lesser than the `token_max` account. |

### 1.1.3. Create an Authorisation Payment

Create a payment checkout form for customers to make Authorisation Transaction and register their mandate. You can use the Handler Function or Callback URL.

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
> UPI Intent is supported on **mWeb (Android and iOS)** and **Mobile App (WebView)**. On **Desktop Web**, as UPI Intent is not supported, a QR code is automatically displayed instead.
>
> If UPI Intent is not enabled on your account, please reach out to the [support team](https://razorpay.com/support).
>
> | Platform | Steps |
> | - | - |
> | **mWeb** | Customers are redirected to their preferred UPI app to complete the payment. For the complete integration guide, refer to [UPI Intent on Mobile Web](https://razorpay.com/docs/payments/payment-methods/upi/upi-intent.md#integrate-on-android-ios-and-mobile-web). |
> | **Mobile App (WebView)** | UPI Intent requires passing `webview_intent: true` in the checkout options and implementing deep link handling in your Android or iOS app. For the complete integration guide, refer to [UPI Intent in WebView — Android](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/webview/upi-intent-android.md) and [UPI Intent in WebView — iOS](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/webview/upi-intent-ios.md). |
> | **Desktop Web** | UPI Intent is not supported. A QR code is automatically displayed for customers to scan with their preferred UPI app. No additional code changes are required. |

> [accordion] UPI Collect
>
> > [!WARNING]
> >
> > **Deprecation Notice**
> >
> > **UPI Collect is deprecated effective 28 February 2026.** This section is applicable only for exempted businesses. If you are an existing Razorpay user not covered by the exemptions, refer to the [migration documentation](https://razorpay.com/docs/announcements/upi-collect-migration/recurring-payments/standard-checkout) to switch to UPI Intent.
>
> > [!NOTE]
> >
> > ```html UPI Collect with handler functions theme={null}
> > <button id = "rzp-button1"> Pay </button>
> >   <script src = "https://checkout.razorpay.com/v1/checkout.js"> </script>
> >   <script>
> >     var options = {
> >       "key": "[YOUR_KEY_ID]",
> >       "order_id": "order_1Aa00000000001",
> >       "customer_id": "cust_1Aa00000000001",
> >       "recurring": "1",
> >       "handler": function (response) {
> >         alert(response.razorpay_payment_id);
> >         alert(response.razorpay_order_id);
> >         alert(response.razorpay_signature);
> >       },
> >       "notes": {
> >         "note_key 1": "Beam me up Scotty",
> >         "note_key 2": "Tea. Earl Gray. Hot."
> >       },
> >       "theme": {
> >         "color": "#F37254"
> >       }
> >     };
> >     var rzp1 = new Razorpay(options);
> >     document.getElementById('rzp-button1').onclick = function (e) {
> >       rzp1.open();
> >       e.preventDefault();
> >     }
> >   </script>
> > ```
> >
> > ```html UPI Collect with Callback URL theme={null}
> > <button id = "rzp-button1"> Pay </button>
> >   <script src = "https://checkout.razorpay.com/v1/checkout.js"> </script>
> >   <script>
> >     var options = {
> >       "key": "[YOUR_KEY_ID]",
> >       "order_id": "order_1Aa00000000001",
> >       "customer_id": "cust_1Aa00000000001",
> >       "recurring": "1",
> >       "callback_url": "https://eneqd3r9zrjok.x.pipedream.net/",
> >       "notes": {
> >         "note_key 1": "Beam me up Scotty",
> >         "note_key 2": "Tea. Earl Gray. Hot."
> >       },
> >       "theme": {
> >         "color": "#F37254"
> >       }
> >     };
> >     var rzp1 = new Razorpay(options);
> >     document.getElementById('rzp-button1').onclick = function (e) {
> >       rzp1.open();
> >       e.preventDefault();
> >     }
> >   </script>
> > ```

Once the authorisation payment is completed, you receive the corresponding `payment.captured` or `payment.failed` webhook. If the payment is successful, the `token.confirmed` webhook is generated and you can get the `token_id` from it. If the payment fails, the `payment.failed` webhook arrives along with the `token.rejected` webhook and the `token_id`.

You can also poll for the payment status using the Fetch Payment API, but we recommend waiting for the webhook notification first and using polling as a fallback. You can also get the `token_id` using the Fetch Token APIs.

#### Additional Checkout Fields

`customer_id` *mandatory*
: `string` Unique identifier of the customer created in the [first step](#1-1-1-create-a-customer).

`order_id` *mandatory*
: `string` Unique identifier of the  order created in the [second step](#1-1-2-create-an-order).

`recurring` *mandatory*
: `string` Determines if the recurring payment is enabled or not. Possible values:

* `1`: Recurring payment is enabled.
* `preferred`: Use this if you want to allow **recurring payments** and **one-time payment** in the same flow.

> [accordion] Error Response Parameters
>
> Given below is a list of possible errors you may face while making the authorisation payment.
>
> > [accordion] adequate\_funds\_not\_available\_blocked
> >
> > * **Description**: Sufficient unblocked funds not available in customer's account. Please ask customer to add fund and try again.
> > * **Next Steps**: Please ask customer to add sufficient unblocked funds and try again.
>
> > [accordion] bad\_request\_error
> >
> > * **Description**: Invalid Mandate Sequence Number.
> > * **Next Steps**: Retry after some time during the valid cycle.
>
> > [accordion] bank\_account\_invalid
> >
> > * **Description**: Payment failed because Account linked to VPA is invalid.
> > * **Next Steps**: Create a new mandate with the customer.
>
> > [accordion] bank\_account\_validation\_failed
> >
> > * **Description**: Payment was unsuccessful as the details are invalid. Please retry with the right details.
> > * **Next Steps**: Ask the customer to retry again.
>
> > [accordion] bank\_not\_available
> >
> > * **Description**: Payment was unsuccessful as the bank linked to this UPI ID is temporarily unavailable. Any amount deducted will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] bank\_technical\_error
> >
> > > [accordion] Bank Temporarily Unavailable
> > >
> > > * **Description**: Payment was unsuccessful as the bank linked to this UPI ID is temporarily unavailable. Any amount deducted will be refunded within 5-7 working days.
> > > * **Next Steps**: Retry after some time.
> >
> > > [accordion] Temporary Bank Issue
> > >
> > > * **Description**: Payment was unsuccessful due to a temporary issue at your bank. Any amount deducted will be refunded within 5-7 working days.
> > > * **Next Steps**: Retry after some time.
> >
> > > [accordion] Bank Declined
> > >
> > > * **Description**: Payment was unsuccessful as it was declined by your bank. Any amount deducted will be refunded within 5-7 working days.
> > > * **Next Steps**: Retry after some time.
> >
> > > [accordion] Bank or Wallet Gateway Error
> > >
> > > * **Description**: Payment processing failed due to error at bank or wallet gateway.
> > > * **Next Steps**: Retry after some time.
> >
> > > [accordion] General Temporary Issue
> > >
> > > * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> > > * **Next Steps**: Retry after some time.
> >
> > > [accordion] Bank Services Halt
> > >
> > > * **Description**: Payment was unsuccessful due to a temporary halt of services at this bank.
> > > * **Next Steps**: Retry after some time.
>
> > [accordion] credit\_to\_beneficiary\_failed
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] debit\_declined
> >
> > * **Description**: Payment was unsuccessful as it was declined by remitter bank.
> > * **Next Steps**: Create a new mandate with the customer.
>
> > [accordion] debit\_instrument\_blocked
> >
> > * **Description**: Payment was unsuccessful as the account linked to this UPI ID is blocked. Try using another account.
> > * **Next Steps**: Create a new mandate with the customer.
>
> > [accordion] duplicate\_mandate\_request
> >
> > * **Description**: Duplicate mandate request. Please try again with another mandate request.
> > * **Next Steps**: Please try again with another mandate request.
>
> > [accordion] gateway\_technical\_error
> >
> > > [accordion] Bank or Wallet Gateway Error
> > >
> > > * **Description**: Payment processing failed due to error at bank or wallet gateway.
> > > * **Next Steps**: Retry after some time.
> >
> > > [accordion] Temporary Issue with Money Deduction
> > >
> > > * **Description**: Payment was unsuccessful due to a temporary issue. If money got deducted, reach out to the seller.
> > > * **Next Steps**: Retry after some time.
>
> > [accordion] incorrect\_pin
> >
> > * **Description**: You have entered an incorrect PIN on the UPI app. Please retry with the correct PIN.
> > * **Next Steps**: Ask the customer to retry with correct PIN.
>
> > [accordion] insufficient\_funds
> >
> > * **Description**: Transaction failed due to insufficient funds.
> > * **Next Steps**: Ask the customer to add balance to their account and retry.
>
> > [accordion] invalid\_request
> >
> > * **Description**: Payment processing failed due to error at bank or wallet gateway.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] invalid\_response\_from\_gateway
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] invalid\_transaction\_beneficiary
> >
> > * **Description**: Beneficiary address resolution failed. Please try again after some time.
> > * **Next Steps**: Please try again after some time.
>
> > [accordion] invalid\_vpa
> >
> > * **Description**: You have entered an incorrect UPI ID. Please retry with the correct UPI ID.
> > * **Next Steps**: Ask the customer to retry with a valid VPA.
>
> > [accordion] issuer\_dispatch\_failed
> >
> > * **Description**: Payment failed due to some issue at the issuer bank. Please try again after some time.
> > * **Next Steps**: Please try again after some time.
>
> > [accordion] limit\_exceeded\_remitting\_bank
> >
> > * **Description**: Limit exceeded for remitter bank. Please ask customer to try with another bank account.
> > * **Next Steps**: Please ask customer to try with another bank account.
>
> > [accordion] mandate\_debit\_beyond\_psp\_amount\_cap
> >
> > * **Description**: Debit amount is beyond payer PSP specified amount cap. Please reduce the amount and try again.
> > * **Next Steps**: Please reduce the mandate amount to match customer PSP.
>
> > [accordion] mandate\_request\_limit\_breached
> >
> > * **Description**: Maximum number of mandate creation requests exceeded for customer's bank account. Please wait for some time before initiating new mandate creation requests.
> > * **Next Steps**: Please wait for some time before initiating new mandate creation requests.
>
> > [accordion] mobile\_number\_invalid
> >
> > * **Description**: Registered Mobile number linked to the account has been changed or removed.
> > * **Next Steps**: Create a new mandate with the customer.
>
> > [accordion] nature\_of\_debit\_not\_allowed
> >
> > * **Description**: Nature of debit not allowed in customer's account. Please ask the customer to use a different bank account.
> > * **Next Steps**: Please ask the customer to use a different bank account.
>
> > [accordion] no\_financial\_address\_record\_found
> >
> > * **Description**: No financial address record found for this VPA. Please ask customer to try with another bank account.
> > * **Next Steps**: Please ask customer to try with other bank account.
>
> > [accordion] no\_original\_request\_found
> >
> > * **Description**: No mandate details were found in the record during debit. Please try after some time.
> > * **Next Steps**: Please try after some time.
>
> > [accordion] payment\_collect\_request\_expired
> >
> > * **Description**: Payment was unsuccessful as you could not pay with the UPI app within time.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] payment\_declined
> >
> > > [accordion] Bank Declined Payment
> > >
> > > * **Description**: Payment was unsuccessful as it was declined by your bank. Any amount deducted will be refunded within 5-7 working days.
> > > * **Next Steps**: Ask the customer to retry with other account.
> >
> > > [accordion] Customer Declined Payment
> > >
> > > * **Description**: You have declined the payment request on the UPI app. Please retry when you are ready.
> > > * **Next Steps**: Ask the customer to approve the payment.
>
> > [accordion] payment\_failed
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue. If amount got deducted, it will be refunded within 5-7 working days.
> > * **Next Steps**: Retry after 1 hour.
>
> > [accordion] payment\_pending
> >
> > * **Description**: The status of your payment is pending. You can either wait or retry to pay successfully.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] payment\_risk\_check\_failed
> >
> > * **Description**: Payment was unsuccessful as your account does not pass the risk checks done by your bank. Try using another account.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] payment\_timed\_out
> >
> > * **Description**: Payment was unsuccessful as you could not complete it in time.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] pre\_debit\_notification\_failed
> >
> > * **Description**: Unable to Notify the Customer.
> > * **Next Steps**: Retry after some time.
>
> > [accordion] remitter\_dispatch\_failed
> >
> > * **Description**: Payment failed due to some issue at the customer's. Please try again after some time.
> > * **Next Steps**: Please try again after some time.
>
> > [accordion] request\_timed\_out
> >
> > > [accordion] General Timeout - Temporary Issue
> > >
> > > * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> > > * **Next Steps**: Retry after some time.
> >
> > > [accordion] Timeout - Bank Declined
> > >
> > > * **Description**: Payment was unsuccessful as it was declined by your bank. Any amount deducted will be refunded within 5-7 working days.
> > > * **Next Steps**: Retry after some time.
> >
> > > [accordion] Timeout - Recurring Payment Creation
> > >
> > > * **Description**: Payment was unsuccessful as the recurring payment can not be created at this time. Any amount deducted will be refunded within 5-7 working days.
> > > * **Next Steps**: Retry after some time.
>
> > [accordion] transaction\_frequency\_limit\_exceeded
> >
> > * **Description**: Payment failed. Please try again with another bank account.
> > * **Next Steps**: Create a new mandate with the customer.
>
> > [accordion] transaction\_limit\_exceeded
> >
> > > [accordion] Amount Limit Exceeded
> > >
> > > * **Description**: Payment failed because Transaction amount limit has exceeded.
> > > * **Next Steps**: Reach out to the customer to collect the amount.
> >
> > > [accordion] Bank Account Amount Limit
> > >
> > > * **Description**: Payment was unsuccessful as you exceeded the amount limit on the bank account linked to this UPI id.
> > > * **Next Steps**: Ask the customer to retry after some time.
>
> > [accordion] transaction\_not\_allowed
> >
> > * **Description**: Payment was unsuccessful as it was declined by your bank. Reach out to your bank for more details. Try using another account.
> > * **Next Steps**: Create a new mandate with the customer.
>
> > [accordion] upi\_dummy\_payment
> >
> > * **Description**: Payment was a dummy payment for one time mandate registration.
> > * **Next Steps**: NA

## 1.2 Using a Registration Link

Registration Link is an alternate way of creating an authorisation transaction. You can create a registration link using the [API](#1-2-1-create-a-registration-link) or [Dashboard](https://razorpay.com/docs/payments/recurring-payments/create.md#1-create-a-registration-link).

> [!NOTE]
>
> **Handy Tips**
>
> You do not have to create a customer if you choose the registration link method for creating an authorisation transaction.

* When you create a registration link, an [invoice](https://razorpay.com/docs/payments/invoices) is automatically issued to the customer. They can use this invoice to make the authorisation payment.
* A registration link should always have an order amount (in paise) the customer is charged when making the authorisation payment. For UPI, the amount must be a minimum of `₹1`.

> [!NOTE]
>
> **Handy Tips**
>
> You can [use Webhooks to get notifications about successful payments](https://razorpay.com/docs/api/payments/recurring-payments/webhooks.md#check-registration-link-status-using-webhooks) against a registration link.

### 1.2.1 Create a Registration Link

The following endpoint creates a registration link.

`POST /subscription_registration/auth_links`

> [accordion] Sample Code
>
> > [!NOTE]
> >
> > ```bash Curl theme={null}
> > curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET>
> > -X POST https://api.razorpay.com/v1/subscription_registration/auth_links
> > -H "Content-Type: application/json" \
> > -d '{
> >   "customer": {
> >     "name": "Gaurav Kumar",
> >     "email": "gaurav.kumar@example.com",
> >     "contact": "9123456780"
> >   },
> >   "type": "link",
> >   "amount": "100",
> >   "currency": "INR",
> >   "description": "Registration Link for Gaurav Kumar",
> >   "subscription_registration": {
> >       "method": "upi",
> >       "max_amount": "500",
> >       "expire_at": 4102444799,
> >       "frequency": "monthly"
> >   },
> >   "receipt": "Receipt No. 23",
> >   "email_notify": true,
> >   "sms_notify": true,
> >   "expire_by": 4102444799,
> >   "notes":{
> >     "note_key 1":"Beam me up Scotty",
> >     "note_key 2":"Tea. Earl Gray. Hot."
> >   }
> > }'
> >
> > ```
> >
> > ```java Java theme={null}
> > RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
> >
> > JSONObject registrationLinkRequest = new JSONObject();
> > JSONObject customer = new JSONObject();
> > customer.put("name","Gaurav Kumar");
> > customer.put("email","gaurav.kumar@example.com");
> > customer.put("contact","9123456780");
> > registrationLinkRequest.put("customer", customer);
> > registrationLinkRequest.put("type", "link");
> > registrationLinkRequest.put("amount", 100);
> > registrationLinkRequest.put("currency", "INR");
> > registrationLinkRequest.put("description", "Registration Link for Gaurav Kumar");
> > JSONObject subscriptionRegistration = new JSONObject();
> > subscriptionRegistration.put("method","upi");
> > subscriptionRegistration.put("max_amount",50000);
> > subscriptionRegistration.put("expire_at",1609423824);
> > subscriptionRegistration.put("frequency","monthly");
> > registrationLinkRequest.put("subscription_registration", subscriptionRegistration);
> > registrationLinkRequest.put("receipt", "Receipt No. #112");
> > registrationLinkRequest.put("email_notify", true);
> > registrationLinkRequest.put("sms_notify", true);
> > registrationLinkRequest.put("expire_by", 1580479824);
> > JSONObject notes = new JSONObject();
> > notes.put("notes_key_1","Tea, Earl Grey, Hot");
> > notes.put("notes_key_2","Tea, Earl Grey… decaf.");
> > registrationLinkRequest.put("notes", notes);
> >
> > Invoice invoice = razorpay.invoices.createRegistrationLink(registrationLinkRequest);
> >
> > ```
> >
> > ```php PHP theme={null}
> > $api = new Api($key_id, $secret);
> >
> > $api->subscription->createSubscriptionRegistration(array('customer'=>array('name'=>'Gaurav Kumar','email'=>'gaurav.kumar@example.com','contact'=>'9123456780'),'type'=>'link','amount'=>100,'currency'=>'INR','description'=>'Registration Link for Gaurav Kumar','subscription_registration'=>array('method'=>'upi','max_amount'=>'500','expire_at'=>'1634215992','frequency'=>'monthly'),'receipt'=>'Receipt No. 5','email_notify'=>true,'sms_notify'=>true,'expire_by'=>1634215992,'notes' => array('note_key 1' => 'Beam me up Scotty','note_key 2' => 'Tea. Earl Gray. Hot.')));
> >
> > ```
> >
> > ```javascript Node.js theme={null}
> > var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
> >
> > instance.subscriptions.createRegistrationLink({
> >   customer: {
> >     name: "Gaurav Kumar",
> >     email: "gaurav.kumar@example.com",
> >     contact: 9123456780
> >   },
> >   type: "link",
> >   amount: 100,
> >   currency: "INR",
> >   description: "Registration Link for Gaurav Kumar",
> >   subscription_registration: {
> >     method: "upi",
> >     max_amount: 500,
> >     expire_at: 1634215992,
> >     frequency: "monthly"
> >   },
> >   receipt: "Receipt No. 5",
> >   email_notify: true,
> >   sms_notify: true,
> >   expire_by: 1634215992,
> >   notes: {
> >     "note_key 1": "Beam me up Scotty",
> >     "note_key 2": "Tea. Earl Gray. Hot."
> >   }
> > })
> >
> > ```
> >
> > ```ruby Ruby theme={null}
> > require "razorpay"
> > Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
> >
> > para_attr = {
> >   "customer": {
> >     "name": "Gaurav Kumar",
> >     "email": "gaurav.kumar@example.com",
> >     "contact": 9123456780
> >   },
> >   "type": "link",
> >   "amount": 100,
> >   "currency": "INR",
> >   "description": "Registration Link for Gaurav Kumar",
> >   "subscription_registration": {
> >     "method": "upi",
> >     "max_amount": 500,
> >     "expire_at": 1634215992
> >   },
> >   "receipt": "Receipt No. 5",
> >   "email_notify": 1,
> >   "sms_notify": 1,
> >   "expire_by": 1634215992,
> >   "notes": {
> >     "note_key 1": "Beam me up Scotty",
> >     "note_key 2": "Tea. Earl Gray. Hot."
> >   }
> > }
> > Razorpay::SubscriptionRegistration.create(para_attr)
> >
> > ```
> >
> > ```python Python theme={null}
> > client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
> >
> > client.registration_link.create({
> >   "customer":{
> >       "name":"Gaurav Kumar",
> >       "email":"gaurav.kumar@example.com",
> >       "contact":9123456780
> >   },
> >   "type":"link",
> >   "amount":100,
> >   "currency":"INR",
> >   "description":"12 p.m. Meals",
> >   "subscription_registration":{
> >       "method":"upi",
> >       "expire_at":1580480689,
> >       "max_amount":500
> >   },
> >   "receipt":"Receipt no. 1",
> >   "expire_by":1880480689,
> >   "sms_notify": True,
> >   "email_notify": True,
> >   "notes":{
> >       "note_key 1":"Beam me up Scotty",
> >       "note_key 2":"Tea. Earl Gray. Hot."
> >   }
> > })
> >
> > ```
> >
> > ```go Go theme={null}
> > import ( razorpay "github.com/razorpay/razorpay-go" )
> > client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
> >
> > data:= map[string]interface{}{
> >   "customer":map[string]interface{}{
> >     "name":"Gaurav Kumar",
> >     "email":"gaurav.kumar@example.com",
> >     "contact":"9123456780",
> >   },
> >   "type":"link",
> >   "amount":"100",
> >   "currency":"INR",
> >   "description":"Registration Link for Gaurav Kumar",
> >   "subscription_registration":map[string]interface{}{
> >     "method":"upi",
> >     "max_amount":"500",
> >     "expire_at":1609423824,
> >     "frequency": "monthly",
> >   },
> >   "receipt":"Receipt No. 1",
> >   "email_notify":true,
> >   "sms_notify":true,
> >   "expire_by":1681987284,
> >   "notes":map[string]interface{}{
> >     "note_key 1":"Beam me up Scotty",
> >     "note_key 2":"Tea. Earl Gray. Hot.",
> >   },
> > }
> > body, err := client.Invoice.CreateRegistrationLink(data, nil)
> >
> > ```
> >
> > ```json Response theme={null}
> > {
> >   "id": "inv_FHr1ekX0r2VCVK",
> >   "entity": "invoice",
> >   "receipt": "Receipt No. 23",
> >   "invoice_number": "Receipt No. 23",
> >   "customer_id": "cust_BMB3EwbqnqZ2EI",
> >   "customer_details": {
> >     "id": "cust_BMB3EwbqnqZ2EI",
> >     "name": "Gaurav Kumar",
> >     "email": "gaurav.kumar@example.com",
> >     "contact": "9123456780",
> >     "gstin": null,
> >     "billing_address": null,
> >     "shipping_address": null,
> >     "customer_name": "Gaurav Kumar",
> >     "customer_email": "gaurav.kumar@example.com",
> >     "customer_contact": "9123456780"
> >   },
> >   "order_id": "order_FHr1ehR3nmNeXo",
> >   "line_items": [],
> >   "payment_id": null,
> >   "status": "issued",
> >   "expire_by": 4102444799,
> >   "issued_at": 1595489219,
> >   "paid_at": null,
> >   "cancelled_at": null,
> >   "expired_at": null,
> >   "sms_status": "pending",
> >   "email_status": "pending",
> >   "date": 1595489219,
> >   "terms": null,
> >   "partial_payment": false,
> >   "gross_amount": 100,
> >   "tax_amount": 0,
> >   "taxable_amount": 0,
> >   "amount": 100,
> >   "amount_paid": 0,
> >   "amount_due": 100,
> >   "currency": "INR",
> >   "currency_symbol": "₹",
> >   "description": "Registration Link for Gaurav Kumar",
> >   "notes": {
> >     "note_key 1": "Beam me up Scotty",
> >     "note_key 2": "Tea. Earl Gray. Hot."
> >   },
> >   "comment": null,
> >   "short_url": "https://rzp.io/i/ak1WxDB",
> >   "view_less": true,
> >   "billing_start": null,
> >   "billing_end": null,
> >   "type": "link",
> >   "group_taxes_discounts": false,
> >   "created_at": 1595489219,
> >   "idempotency_key": null
> > }
> > ```

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
> : Details of the authorisation transaction.
>
> `method` *mandatory*
> : `string` The payment method used to make authorisation transaction. Here, it is `card`.
>
> `max_amount` *mandatory*
> : `integer` Use to set the maximum amount (in paise) per debit request.
> The minimum value is `100` (₹1). For the maximum value for your MCC, refer to the [limits by MCC table](https://razorpay.com/docs/payments/recurring-payments/overview/integrate#limits-by-mcc).
>
> `expire_at` *optional*
> : `integer` The Unix timestamp till when you can use the token to charge the customer subsequent payments. The default value is 10 years and the maximum value allowed is 30 years.
>
> `frequency` *mandatory*
> : `string` The frequency at which you can charge your customer. Possible values:
>
> * `daily`
> * `weekly`
> * `fortnightly`
> * `bimonthly`
> * `monthly`
> * `quarterly`
> * `half_yearly`
> * `yearly`
> * `as_presented`
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
> : `integer` Amount to be paid using the invoice. Must be in the smallest unit of the currency. For example, if the amount to be received from the customer is <currency MY="299.95" IN="299.95" SG="299.95" US="299.95" />, pass the value as `29995`.
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

### 1.2.2 Send/Resend Notifications

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

> [accordion] Response Parameters
>
> `success`
> : `boolean` Indicates whether the notifications were sent successfully. Possible values:
>
> * `true`: The notifications were successfully sent via SMS, email or both.
> * `false`: The notifications were not sent.

### 1.2.3 Cancel a Registration Link

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
> : `integer` Amount to be paid using the invoice. Must be in the smallest unit of the currency. For example, if the amount to be received from the customer is <currency MY="299.95" IN="299.95" SG="299.95" US="299.95" />, pass the value as `29995`.
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
