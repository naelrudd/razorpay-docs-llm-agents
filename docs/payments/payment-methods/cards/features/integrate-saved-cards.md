> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integrate Saved Cards at Standard Checkout

> Know how to integrate saved cards at Standard Checkout.

Available in
🇮🇳 India
🇸🇬 Singapore

Check the prerequisites and the integration steps for [Saved Cards](https://razorpay.com/docs/payments/payment-methods/cards/features/saved-cards.md) on your standard checkout page. Know [how to integrate Saved Cards on Custom Checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/features/saved-cards.md).

## Prerequisites

* Create a [Razorpay account](https://dashboard.razorpay.com/signup).
* [Generate API Keys on Dashboard.](https://razorpay.com/docs/api/authentication.md#generate-api-keys)

> [tab] Test Mode API Keys
>
> Watch this video to know how to generate Test Mode API keys.
>
> [Generate Test Mode API keys.](https://www.youtube.com/embed/6mJnOWZDhDo)

* [Integrate with our Standard Checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard.md).

## Step 1: Enable Flash Checkout on Dashboard

Flash Checkout, enabled by default on your Standard Checkout, lets your customers save their card details for future purchases. Customers can choose whether to save their card information during the payment process. All card details are stored securely using PCI-DSS-compliant technology. Know more about [Flash Checkout](https://razorpay.com/docs/payments/dashboard/account-settings/checkout-features.md#flash-checkout).

## Step 2: Create a Customer

Create a customer whose card details should be saved from the Dashboard or using the Customers API. You can create customers with basic details such as `email` and `contact` using the following endpoint:

> [accordion] API Sample Code
>
> The following endpoint creates or add a customer with basic details such as name and contact details. You can use this API for various Razorpay Solution offerings.
>
> `POST /customers`
>
> ```bash Curl theme={null}
> curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
> -X POST https://api.razorpay.com/v1/customers \
> -H "Content-Type: application/json" \
> -d '{
>     "name": "<name>",
>     "contact": "<phone>",
>     "email": "<email>",
>     "fail_existing": "0",
>     "notes": {
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf."
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
>   "name": "<name>",
>   "contact": "<phone>",
>   "email": "<email>",
>   "fail_existing": "0",
>   "notes": {
>     "notes_key_1": "Tea, Earl Grey, Hot",
>     "notes_key_2": "Tea, Earl Grey… decaf."
>   }
> })
> ```
>
> ```go Go theme={null}
> import ( razorpay "github.com/razorpay/razorpay-go" )
> client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
> data := map[string]interface{}{
>     "name": "<name>",
>     "contact": "<phone>",
>     "email": "<email>",
>     "fail_existing": "0",
>     "notes": map[string]interface{}{
>       "notes_key_1": "Tea, Earl Grey, Hot",
>       "notes_key_2": "Tea, Earl Grey… decaf.",
> 	},
> }
>
> body, err := client.Customer.Create(data, nil)
> ```
>
> ```php PHP theme={null}
> $api = new Api($key_id, $secret);
>
> $api->customer->create(array('name' => '<name>', 'email' => '<email>','contact'=>'<phone>','notes'=> array('notes_key_1'=> 'Tea, Earl Grey, Hot','notes_key_2'=> 'Tea, Earl Grey… decaf'));
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
> Razorpay::Customer.create({
>   "name": "<name>",
>   "contact": "<phone>",
>   "email": "<email>",
>   "fail_existing": "0",
>   "notes": {
>     "notes_key_1": "Tea, Earl Grey, Hot",
>     "notes_key_2": "Tea, Earl Grey… decaf."
>   }
> })
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
> ```json Success Response theme={null}
> {
>   "id" : "cust_1Aa00000000004",
>   "entity": "customer",
>   "name" : "<name>",
>   "email" : "<email>",
>   "contact" : "<phone>",
>   "gstin": null,
>   "notes": {
>     "notes_key_1":"Tea, Earl Grey, Hot",
>     "notes_key_2":"Tea, Earl Grey… decaf."
>   },
>   "created_at ": 1234567890
> }
> ```
>
> ```json Failure Response theme={null}
> {
>   "error": {
>     "code": "BAD_REQUEST_ERROR",
>     "description": "Contact number should be at least 8 digits, including country code",
>     "source": "business",
>     "step": "NA",
>     "reason": "invalid_contact_number",
>     "metadata": {},
>     "field": "contact"
>   }
> }
> ```
>
> Know more about [Customers API](https://razorpay.com/docs/api/customers.md).
>
> #### Request Parameters
>
> `name` *optional*
> : `string` Customer's name. Alphanumeric value with period (.), apostrophe ('), forward slash (/), at (@) and parentheses are allowed. The name must be between 3-50 characters in length. For example, `Gaurav Kumar`.
>
> `contact ` *optional*
> : `string` The customer's phone number. A maximum length of 15 characters including country code. For example, `+919876543210`.
>
> `email ` *optional*
> : `string` The customer's email address. A maximum length of 64 characters. For example, `gaurav.kumar@example.com`.
>
> `fail_existing` *optional*
> : `string` Possible values:
>
> * `1` (default): If a customer with the same details already exists, throws an error.
> * `0`: If a customer with the same details already exists, fetches details of the existing customer.
>
> `gstin` *optional*
> : `string` Customer's GST number, if available. For example, `29XAbbA4369J1PA`.
>
> `notes` *optional*
> : `object` This is a key-value pair that can be used to store additional information about the entity. It can hold a maximum of 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

## Step 3: Create an Order

Order is an important step in the payment process.

* An order should be created for every payment.
* You can create an order using the [Orders API](#api-sample-code). It is a server-side API call.  Know how to [authenticate](https://razorpay.com/docs/api/authentication.md#generate-api-keys) Orders API.
* The order\_id received in the response should be passed to the checkout. This ties the Order with the payment and secures the request from being tampered.

> [!WARNING]
>
> **Watch Out!**
>
> Payments made without an `order_id` cannot be captured and will be automatically refunded. You must create an order before initiating payments to ensure proper payment processing.

#### API Sample Code

The following is a sample API request and response for creating an order:

```bash Curl theme={null}
curl -X POST https://api.razorpay.com/v1/orders
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-H 'content-type:application/json'
-d '{
    "amount": 50000,
    "currency": "INR",
    "receipt": "rcptid_11",
    "partial_payment": true,
    "first_payment_min_amount": 23000
}'
```

```java Java theme={null}
try {
  JSONObject orderRequest = new JSONObject();
  orderRequest.put("amount", 50000); // amount in the smallest currency unit
  orderRequest.put("currency", "INR");
  orderRequest.put("receipt", "order_rcptid_11");

  Order order = razorpay.Orders.create(orderRequest);
} catch (RazorpayException e) {
  // Handle Exception
  System.out.println(e.getMessage());
}
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("api_key", "api_secret"))

DATA = {
    "amount": 50000,
    "currency": "INR",
    "receipt": "receipt#1",
    "notes": {
        "key1": "value3",
        "key2": "value2"
    }
}
client.order.create(data=DATA)
```

```php PHP theme={null}
$order  = $client->order->create([
  'receipt'         => 'order_rcptid_11',
  'amount'          => 50000, // amount in the smallest currency unit
  'currency'        => 'INR'// <a href="/payments/international-payments/#supported-currencies" target="_blank">See the list of supported currencies</a>.)
]);
```

```csharp .NET theme={null}
Dictionary<string, object> options = new Dictionary<string,object>();
options.Add("amount", 50000); // amount in the smallest currency unit
options.add("receipt", "order_rcptid_11");
options.add("currency", "INR");
Order order = client.Order.Create(options);
```

```ruby Ruby theme={null}
options = amount: 50000, currency: 'INR', receipt: '<order_rcptid_11>'
order = Razorpay::Order.create
```

```javascript Node.js theme={null}
var options = {
  amount: 50000,  // amount in the smallest currency unit
  currency: "INR",
  receipt: "order_rcptid_11"
};
instance.orders.create(options, function(err, order) {
  console.log(order);
});
```

```json Response theme={null}
{
    "id": "order_DBJOWzybf0sJbb",
    "entity": "order",
    "amount": 50000,
    "amount_paid": 0,
    "amount_due": 50000,
    "currency": "INR",
    "receipt": "rcptid_11",
    "status": "created",
    "attempts": 0,
    "notes": [],
    "created_at": 1566986570
}
```

#### Request Parameters

Here is the list of parameters and their description for creating an order:

`amount` *mandatory*
: `integer` Payment amount in the smallest currency sub-unit. For example, if the amount to be charged is ₹299, then pass `29900` in this field. In the case of three decimal currencies, such as KWD, BHD and OMR, to accept a payment of 295.991, pass the value as 295990. And in the case of zero decimal currencies such as JPY, to accept a payment of 295, pass the value as 295.

> [!WARNING]
>
> **Watch Out!**
>
> As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to charge a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.

`currency` *mandatory*
: `string` The currency in which the transaction should be made. See the [list of supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies). Length must be 3 characters.

> [!NOTE]
>
> **Handy Tips**
>
> Razorpay has added support for zero decimal currencies, such as JPY and three decimal currencies, such as KWD, BHD and OMR, allowing businesses to accept international payments in these currencies. Know more about [Currency Conversion](https://razorpay.com/docs/payments/international-payments/currency-conversion.md) (May 2024).

`receipt` *optional*
: `string` Your receipt id for this order should be passed here. Maximum length is 40 characters.

`notes` *optional*
: `json object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

`partial_payment` *optional*
: `boolean` Indicates whether the customer can make a partial payment. Possible values:

* `true`: The customer can make partial payments.
* `false` (default): The customer cannot make partial payments.

`id` *mandatory*
: `string` Unique identifier of the customer. For example, `cust_1Aa00000000004`.

Know more about [Orders API](https://razorpay.com/docs/api/orders.md).

#### Response Parameters

Descriptions for the response parameters are present in the [Orders Entity](https://razorpay.com/docs/api/orders/entity.md) table.

#### Error Response Parameters

The error response parameters are available in the [API Reference Guide](https://razorpay.com/docs/api/orders/create.md).

## Step 4: Enable Customer Card Saving on Checkout

While making the payment, the customer enters card details and can choose to save them for future use. Pass `customer_id` along with the other parameters into the Checkout form.

> [tab] Web
>
> ```html Web Standard Checkout theme={null}
> <button id="rzp-button1">Pay</button>
> <script src="https://checkout.razorpay.com/v1/checkout.js"></script>
> <script>
> var options = {
>     "key": "<YOUR_KEY_ID>",
>     "amount": "5076",
>     "currency": "INR",
>     "name": "Acme Corp",
>     "description": "Test Transaction",
>     "image": "https://example.com/your_logo",
>     "customer_id": "cust_EYqfYOviw62csf",
>     "order_id": "order_DBJOWzybf0sJbb",
>     "prefill":{
>         "contact":"<phone>",
>         "email":"<email>",
>         "name":"<name>"
>         },
>     "handler": function (response){
>         alert(response.razorpay_payment_id);
>         alert(response.razorpay_order_id);
>         alert(response.razorpay_signature)
>     }
> };
> var rzp1 = new Razorpay(options);
> document.getElementById('rzp-button1').onclick = function(e){
>     rzp1.open();
>     e.preventDefault();
> }
> </script>
> ```
>
> #### Request Parameter
>
> `customer_id` *mandatory*
> : `string` Unique identifier of the customer. This can be obtained from the response of the previous step.
>
> Know more about [Checkout parameters](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/integration-steps.md#2-3-checkout-options) for web integration.

> [tab] Android
>
> To enable customers to save their cards, pass `customer_id` along with other parameters:
>
> ```java Save Card theme={null}
> JSONObject payload = new JSONObject();
> payload.put("currency", "INR");
> payload.put("customer_id", "cust_4lsdkfldlteskf");
> payload.put("order_id", "order_DBJOWzybf0sJbb");
> // And the remaining fields
> ```
>
> #### Request Parameter
>
> `customer_id` *mandatory*
> : `string` Unique identifier of the customer. This can be obtained from the response of the previous step.
>
> Know more about [Checkout parameters](https://razorpay.com/docs/payments/payment-gateway/android-integration/standard/integration-steps.md#checkout-options) for Android integration.

> [tab] iOS
>
> To enable customers to save their cards, pass `customer_id` along with other parameters. The `options` dictionary in Swift and Objective C are shown below:
>
> ```swift Swift theme={null}
> internal func showPaymentForm(){
> let options: [String:Any] = [
>         "customer_id":"cust_4lsdkfldlteskf",
>         "order_id":"order_DBJOWzybf0sJbb"
>         // And the remaining fields
>     ]
> razorpay.open(options)
> }
> ```
>
> ```objectivec Objective C theme={null}
>     @"customer_id" : @"cust_4lsdkfldlteskf",
>     @"order_id": "order_DBJOWzybf0sJbb"
>     // And the remaining fields
> ```
>
> #### Request Parameter
>
> `customer_id` *mandatory*
> : `string` Unique identifier of the customer. This can be obtained from the response of the previous step.
>
> Know more about [other Checkout parameters for iOS integration](https://razorpay.com/docs/payments/payment-gateway/ios-integration/standard/integration-steps.md).

## Step 5: Create Payments Using Saved Card

Once the card is saved, customers can complete payments on repeat purchases by only entering the CVV. To fetch saved cards, pass the `customer_id` to the Checkout form.

> [tab] Web
>
> Initiate payment by passing `customer_id` to Checkout along with the other options.
>
> ```html Standard Checkout theme={null}
> <button id="rzp-button1">Pay</button>
> <script src="https://checkout.razorpay.com/v1/checkout.js"></script>
> <script>
> var options = {
>     "key": "YOUR_KEY_ID", // Enter the Key ID generated from the Dashboard
>     "amount": "50000", // Amount is in currency subunits.
>     "currency": "INR",
>     "name": "Acme Corp",
>     "description": "Test Transaction",
>     "order_id":"order_CgmcjRh9ti2lP7",
>     "image": "https://example.com/your_logo",
>     "customer_id": "cust_EYqfYOviw62csf",
>     "handler": function (response){
>         alert(response.razorpay_payment_id);
>         alert(response.razorpay_order_id);
>         alert(response.razorpay_signature)
>     }
> };
> var rzp1 = new Razorpay(options);
> document.getElementById('rzp-button1').onclick = function(e){
>     rzp1.open();
>     e.preventDefault();
> }
> </script>
> ```
>
> #### Request Parameter
>
> `customer_id` *mandatory*
> : `string` Unique identifier of the customer. [Created in Step 2](#step-2-create-a-customer).

> [tab] Android
>
> Initiate payment by passing `customer_id` to Checkout along with the other options.
>
> ```java Initiate Payment theme={null}
>    JSONObject payload = new JSONObject();
>    payload.put("customer_id", "cust_4lsdkfldlteskf");
>    // And the remaining fields
> ```
>
> #### Request Parameter
>
> `customer_id` *mandatory*
> : `string` Unique identifier of the customer. [Created in Step 2](#step-2-create-a-customer).

> [tab] iOS
>
> Initiate payment by passing `customer_id` to Checkout along with the other options.
>
> ```swift Swift theme={null}
> internal func showPaymentForm(){
> let options: [String:Any] = [
>        "amount": "100",
>        "currency": "INR",//Amount is in currency subunits.
>        "description": "purchase description",
>        "order_id": "order_4xbQrmEoA5WJ0G",
>        "image": "https://cdn.razorpay.com/logos/F9Yhfb7ZXjXmIQ_medium.jpg",
>        "name": "business or product name",
>        "customer_id":"cust_4lsdkfldlteskf",
>        "prefill": [
>            "contact": "<phone>",
>            "email": "<email>"
>        ],
>        "theme": [
>            "color": "#F37254"
>        ]
>        // And the remaining fields
>    ]
> razorpay.open(options)
> }
> ```
>
> ```objectivec Objective C theme={null}
>    @"amount" : @(2000),
>    @"email" : @"<email>",
>    @"contact" : @"<phone>",
>    @"customer_id" : @"cust_4lsdkfldlteskf"
>    // And the remaining fields
> ```
>
> #### Request Parameter
>
> `customer_id` *mandatory*
> : `string` Unique identifier of the customer. [Created in Step 2](#step-2-create-a-customer).

## Test Integration

Use test cards to test your payment integration before going live. The test cards simulate different payment scenarios and error conditions for all supported card networks. Know more about [Test Cards](https://razorpay.com/docs/payments/payments/test-card-details.md).
