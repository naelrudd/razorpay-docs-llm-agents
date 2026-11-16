> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# 1. Create the Authorisation Transaction

> Learn how to create an authorisation transaction for upi.

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
> **Exemptions:**
>
> UPI Collect will continue to be supported for:
>
> * MCC 6012 & 6211 (IPO and secondary market transactions).
> * iOS mobile app and mobile web transactions.
> * UPI Mandates (execute/modify/revoke operations only).
> * eRupi vouchers.
> * PACB businesses (cross-border/international payments).
>
> **Action Required:**
>
> * If you are a new Razorpay user, use UPI Intent.
> * If you are an existing Razorpay user not covered by exemptions, you must remove the UPI Collect parameters from `razorpay.js` and migrate to UPI Intent or UPI QR code to continue accepting UPI Autopay registrations. For detailed migration steps, refer to the [migration documentation](https://razorpay.com/docs/announcements/upi-collect-migration/recurring-payments/custom-checkout).

A token is the unique identifier Razorpay creates for a customer's UPI Autopay mandate. It holds the mandate terms (the maximum debit amount, the frequency and the expiry), and you use its `token_id` to execute every subsequent debit. In these docs, "mandate" refers to the authorisation the customer approves in their UPI app, and "token" is the object you work with in Razorpay APIs. One mandate maps to one token.

You can create an authorisation transaction using [Razorpay APIs](#1-1-using-razorpay-apis) or [Registration Link](#1-2-using-a-registration-link).

A token changes state as the customer and your business act on it:

* If the authorisation payment fails, the token moves to the `rejected` state.
* Once a token is `confirmed`, it never moves to `rejected`. It moves only to `paused` or `cancelled`.
* When the customer resumes a `paused` token, it moves back to `confirmed`.
* When you cancel a token, it stays in the `cancellation_initiated` state until the downstream partner confirms the cancellation. It then moves to `cancelled`.

Refer to [Token States](https://razorpay.com/docs/api/payments/recurring-payments/custom/upi/tokens.md#token-states) for all states and the webhooks generated for each.

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

> [accordion] Sample Code
>
> Razorpay links recurring tokens to customers using a unique identifier generated through the Customer API.
>
> Creating a customer is mandatory to set up a registration. You may have your own way to identify customers at your end, so passing `email` and `contact` is optional, but we recommend passing at least one of them to Razorpay. You can also use the customer for various Razorpay offerings. Know more about [Customers](https://razorpay.com/docs/api/customers.md). The following endpoint creates a customer.
>
> `POST /customers`
>
> > [accordion] Sample Code
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

The Orders API allows you to create a unique Razorpay `order_id`, for example, `order_1Aa00000000001`, that would be tied to the authorisation transaction. Refer to our detailed [Order documentation](https://razorpay.com/docs/payments/orders) for more details.

You can create a payment against the `order_id` once it is generated.

Use the below endpoint to create an order.

`POST /orders`

> [accordion] Sample Code
>
> ```bash Request theme={null}
> curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
> -X POST https://api.razorpay.com/v1/orders \
> -H "Content-Type: application/json" \
> -d '{
>   "amount": 100,
>   "currency": "INR",
>   "customer_id": "cust_4xbQrmEoA5WJ01",
>   "method": "upi",
>   "payment_capture": true,
>   "token": {
>     "max_amount": 200000,
>     "expire_at": 2709971120,
>     "frequency": "monthly"
>   },
>   "receipt": "Receipt No. 1",
>   "notes": {
>     "notes_key_1": "Tea, Earl Grey, Hot",
>     "notes_key_2": "Tea, Earl Grey… decaf."
>   }
> }'
> ```
>
> ```json Response theme={null}
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
> ```

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
> For S2S and custom checkout integrations, the customer selects the UPI app on your checkout page. We highly recommend passing the name of the app selected by the customer in this parameter. For example, `"note_key_1": "phonepe"`. This helps Razorpay debug any issue in the mandate registration journey. If you have other notes, use the next available key, such as `note_key_2`.
>
> `token`
> : Details related to the authorisation such as max amount, frequency and expiry information.
>
> `max_amount` *mandatory*
> : `integer` The maximum amount that can be debited in a single charge.
>
> The minimum value is `100` (₹1). For the maximum value for your MCC, refer to the [limits by MCC table](https://razorpay.com/docs/payments/recurring-payments/overview/integrate#limits-by-mcc).
>
> > [!NOTE]
> >
> > **Best Practices**
> >
> > Set the `max_amount` as close to the actual debit amount as possible. For example, if the expected debit amount is ₹99-₹299, setting the `max_amount` to ₹5,000 may cause the customer to drop off due to trust issues. A realistic `max_amount` builds customer trust while allowing flexibility for variable debits.
> >
> > Frequency also plays a crucial role in building customer trust. For example, if you are selling a monthly subscription but request an `as_presented` mandate, the customer may find it risky to set up the mandate. If your business has a flexible billing model, `as_presented` frequency fits your use case better, because NPCI has strict checks to ensure one successful debit per billing cycle.
> >
> > If you are a TPV (third-party validation) merchant, also prompt the customer to choose only their registered bank account at app selection. See [Create an Authorisation Payment](#1-1-3-create-an-authorisation-payment).
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

### 1.1.3. Create an Authorisation Payment

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

> [accordion] UPI Intent
>
> UPI Intent is supported on **mWeb (Android)** and **Mobile App (WebView)**. On **Desktop Web**, as UPI Intent is not supported, a QR code is displayed instead.
>
> | Platform | Procedure |
> | - | - |
> | **mWeb** | Customers are redirected to their preferred UPI app to complete the payment. For the complete integration guide, refer to [UPI Intent on Mobile Web](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/payment-methods/upi-intent-mweb.md). |
> | **Mobile App (WebView)** | UPI Intent requires deep link handling in your Android or iOS app to launch UPI apps from the WebView. For the complete integration guide, refer to [UPI Intent in WebView — Android](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/features/webview/upi-intent-android.md) and [UPI Intent in WebView — iOS](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/features/webview/upi-intent-ios.md). |
> | **Desktop Web** | UPI Intent is not supported. A QR code is automatically displayed for customers to scan with their preferred UPI app. No additional code changes are required. |
>
> > [accordion] List of Supported UPI Apps
> >
> > | Android | iOS |
> > | - | - |
> > | <ul><li>Google Pay</li><li>BHIM</li><li>PhonePe</li><li>PayTM</li><li>Amazon Pay</li></ul> | <ul><li>Google Pay</li><li>PhonePe</li><li>PayTM</li></ul> |

> [accordion] UPI Collect
>
> > [!WARNING]
> >
> > **Deprecation Notice**
> >
> > **UPI Collect is deprecated effective 28 February 2026.** This tab is applicable only for exempted businesses. If you are not covered by the exemptions, refer to the [migration documentation](https://razorpay.com/docs/announcements/upi-collect-migration/recurring-payments/custom-checkout) to switch to UPI Intent.
>
> ```html Checkout with handler functions theme={null}
> <script type="text/javascript" src="https://checkout.razorpay.com/v1/razorpay.js"></script>
> <script src= "https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"> </script>
>   <body><button id="btn" style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">Pay</button>
> <script>
>   const btn = document.querySelector("#btn");
>                 var razorpay = new Razorpay({
>                   key: "<YOUR_TEST_KEY>",
>                   image: "https://i.imgur.com/n5tjHFD.jpg"
>                 });
>           razorpay.once("ready", function(response) {
>             console.log(response.methods);
>           })
>           var data = {
>       "amount": 300, // in currency subunits. Here 1000 = 1000 paise, which equals to ₹10
>       "currency": "INR",// Default is INR. We support more than 90 currencies.
>       "email": "gaurav.kumar@example.com",
>       "contact": "9123456780",
>       "notes": {
>         "address": "Ground Floor, SJR Cyber, Laskar Hosur Road, Bengaluru",
>       },
>       "order_id": "order_00000000000001",
>       "customer_id": "cust_00000000000001",
>       "recurring": "1",
>       "method": "upi",
>       "upi":
>         {
>           "vpa": "gauravkumar@somebank",
>           "flow": "collect"
>         }// Applicable only for exempted businesses. UPI Collect is deprecated for all others effective 28 Feb 2026.
>     };
>       btn.addEventListener("click", function(){ // has to be placed within user initiated context, such as click, in order for popup to open.
>       razorpay.createPayment(data);
>       razorpay.on("payment.success", function(resp) {
>         alert(resp.razorpay_payment_id),
>         alert(resp.razorpay_order_id),
>         alert(resp.razorpay_signature)}); // will pass payment ID, order ID and Razorpay signature to success handler.
>       razorpay.on("payment.error", function(resp){alert(resp.error.description)}); // will pass error object to error handler
>     })
>   </script>
> </body>
> ```
>
> ```html Custom checkout with Callback URL theme={null}
> <script type="text/javascript" src="https://checkout.razorpay.com/v1/razorpay.js"></script>
> <script src= "https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"> </script>
>   <body><button id="btn" style="background-color: #3399cc; color: white; font-size: 16px; font-family: sans-serif">Pay</button>
> <script>
>   const btn = document.querySelector("#btn");
>                 var razorpay = new Razorpay({
>                   key: "<YOUR_TEST_KEY>",
>                   image: "https://i.imgur.com/n5tjHFD.jpg"
>                 });
>           razorpay.once("ready", function(response) {
>             console.log(response.methods);
>           })
>           var data = {
>       "callback_url": "www.example-callback-url.com",
>       "amount": 300, // in currency subunits. Here 1000 = 1000 paise, which equals to ₹10
>       "currency": "INR",// Default is INR. We support more than 90 currencies.
>       "email": "gaurav.kumar@example.com",
>       "contact": "9123456780",
>       "notes": {
>         "address": "Ground Floor, SJR Cyber, Laskar Hosur Road, Bengaluru",
>       },
>       "order_id": "order_00000000000001",
>       "customer_id": "cust_00000000000001",
>       "recurring": "1",
>       "method": "upi",
>       "upi":
>         {
>           "vpa": "gauravkumar@somebank",
>           "flow": "collect"
>         }// Applicable only for exempted businesses. UPI Collect is deprecated for all others effective 28 Feb 2026.
>     };
>       btn.addEventListener("click", function(){ // has to be placed within user initiated context, such as click, in order for popup to open.
>       razorpay.createPayment(data);
>     })
>   </script>
> </body>
> ```

Once the authorisation payment is completed, you receive the corresponding `payment.captured` or `payment.failed` webhook. If the payment is successful, the `token.confirmed` webhook is generated and you can get the `token_id` from it. If the payment fails, the `payment.failed` webhook arrives along with the `token.rejected` webhook and the `token_id`.

You can also poll for the payment status using the Fetch Payment API, but we recommend waiting for the webhook notification first and using polling as a fallback. You can also get the `token_id` using the Fetch Token APIs.

> [!WARNING]
>
> **Watch Out!**
>
> If you are a TPV (third-party validation) merchant, show a clear message to the customer just before UPI app selection asking them to choose only the bank account they have already registered with you. On S2S and custom checkout integrations, app and account selection happens on your interface, so this prompt is your responsibility. If the customer authorises the mandate from a non-registered account, the registration may succeed but all subsequent debits will fail TPV validation.

#### Additional Checkout fields

`customer_id` *mandatory*
: `string` Unique identifier of the customer created in the [first step](#1-1-1-create-a-customer).

`order_id` *mandatory*
: `string` Unique identifier of the  order created in the [second step](#1-1-2-create-an-order).

`recurring` *mandatory*
: `string` Determines if the recurring payment is enabled or not. Possible values:

* `1`: Recurring payment is enabled.
* `preferred`: Use this if you want to allow **recurring payments** and **one-time payment** in the same flow.

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

Use the below endpoint to create a registration link.

`POST /subscription_registration/auth_links`

> [accordion] Sample Code
>
> ```bash Request theme={null}
>  curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET>
>  -X POST https://api.razorpay.com/v1/subscription_registration/auth_links
>  -H "Content-Type: application/json" \
>  -d '{
>    "customer": {
>      "name": "Gaurav Kumar",
>      "email": "gaurav.kumar@example.com",
>      "contact": "9123456780"
>    },
>    "type": "link",
>    "amount": "100",
>    "currency": "INR",
>    "description": "Registration Link for Gaurav Kumar",
>    "subscription_registration": {
>        "method": "upi",
>        "max_amount": "500",
>        "expire_at": 4102444799,
>        "frequency": "monthly"
>    },
>    "receipt": "Receipt No. 1",
>    "email_notify": true,
>    "sms_notify": true,
>    "expire_by": 4102444799,
>    "notes":{
>      "note_key 1":"Beam me up Scotty",
>      "note_key 2":"Tea. Earl Gray. Hot."
>    }
>  }'
> ```
>
> ```json Response theme={null}
>  {
>    "id": "inv_FHr1ekX0r2VCVK",
>    "entity": "invoice",
>    "receipt": "Receipt No. 1",
>    "invoice_number": "Receipt No. 1",
>    "customer_id": "cust_BMB3EwbqnqZ2EI",
>    "customer_details": {
>      "id": "cust_BMB3EwbqnqZ2EI",
>      "name": "Gaurav Kumar",
>      "email": "gaurav.kumar@example.com",
>      "contact": "9123456780",
>      "gstin": null,
>      "billing_address": null,
>      "shipping_address": null,
>      "customer_name": "Gaurav Kumar",
>      "customer_email": "gaurav.kumar@example.com",
>      "customer_contact": "9123456780"
>    },
>    "order_id": "order_FHr1ehR3nmNeXo",
>    "line_items": [],
>    "payment_id": null,
>    "status": "issued",
>    "expire_by": 4102444799,
>    "issued_at": 1595489219,
>    "paid_at": null,
>    "cancelled_at": null,
>    "expired_at": null,
>    "sms_status": "pending",
>    "email_status": "pending",
>    "date": 1595489219,
>    "terms": null,
>    "partial_payment": false,
>    "gross_amount": 100,
>    "tax_amount": 0,
>    "taxable_amount": 0,
>    "amount": 100,
>    "amount_paid": 0,
>    "amount_due": 100,
>    "currency": "INR",
>    "currency_symbol": "₹",
>    "description": "Registration Link for Gaurav Kumar",
>    "notes": {
>      "note_key 1": "Beam me up Scotty",
>      "note_key 2": "Tea. Earl Gray. Hot."
>    },
>    "comment": null,
>    "short_url": "https://rzp.io/i/ak1WxDB",
>    "view_less": true,
>    "billing_start": null,
>    "billing_end": null,
>    "type": "link",
>    "group_taxes_discounts": false,
>    "created_at": 1595489219,
>    "idempotency_key": null
>  }
> ```

> [accordion] Request Parameters
>
> `customer`
> : Details of the customer to whom the registration link will be sent.
>
> `name` *mandatory*
> : `string` Customer's name.
>
> `email` *mandatory*
> : `string` Customer's email address.
>
> `contact`*mandatory*
> : `string` Customer's phone number.
>
> `type` *mandatory*
> : `string` In this case, the value is `link`.
>
> `currency` *mandatory*
> : `string` The 3-letter ISO currency code for the payment. Currently, only `INR` is supported.
>
> `amount` *mandatory*
> : `integer` The payment amount in the smallest currency sub-unit.
>
> `description` *mandatory*
> : `string` A description that appears on the hosted page. For example, `12:30 p.m. Thali meals (Gaurav Kumar)`.
>
> `subscription_registration`
> : Details of the authorisation transaction.
>
> `method` *mandatory*
> : `string` The authorization method. Here it is `card`.
>
> `max_amount` *mandatory*
> : `integer` Use to set the maximum amount (in paise) per debit request.
>
> The minimum value is `100` (₹1). For the maximum value for your MCC, refer to the [limits by MCC table](https://razorpay.com/docs/payments/recurring-payments/overview/integrate#limits-by-mcc).
>
> `expire_at` *optional*
> : `integer` The timestamp, in Unix format, till when you can use the token (authorization on the payment method) to charge the customer subsequent payments.
>
> `frequency` *mandatory*
> : `string` The frequency at which you can charge your customer. Must be set to `monthly`.
>
> `sms_notify` *optional*
> : `boolean` Indicates if SMS notifications are to be sent by Razorpay. Can have the following values:
>
> * `true` (default): Notifications are sent by Razorpay.
> * `false`: Notifications are not sent by Razorpay.
>
> `email_notify` *optional*
> : `boolean` Indicates if email notifications are to be sent by Razorpay. Can have the following values:
>
> * `true` (default): Notifications are sent by Razorpay.
> * `false`: Notifications are not sent by Razorpay.
>
> `expire_by` *optional*
> : `integer` The timestamp, in Unix, till when the registration link should be available to the customer to make the authorisation transaction.
>
> `receipt` *optional*
> : `string` A unique identifier entered by you for the order. For example, `Receipt No. 1`. This parameter should be mapped to the `order_id` sent by Razorpay.
>
> `notes` *optional*
> : `object` This is a key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

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
