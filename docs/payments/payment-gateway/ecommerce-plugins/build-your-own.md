> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Build your own custom plugin to integrate Razorpay with your ecommerce website and start accepting payments.

Available in
🇮🇳 India

> [card] [Troubleshooting & FAQs](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/build-your-own/faqs.md)
>
> Troubleshoot common error scenarios and find answers to frequently asked questions about building a custom plugin.

You can build a plugin that integrates Razorpay Payment Gateway with websites created using ecommerce platforms such as Spree Commerce.

## Use Cases

Following are some specific cases whose integration is handled on a case-by-case basis:

> [accordion] Donations
>
> If the platform is used to collect donations, you cannot rely on the amount to be generated on the backend. While you will be ignoring this check, you should still be storing the Razorpay order ID and re-verifying it after payment completion.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > We won't be able to activate all non-profits and would be considering such merchants on a case-by-case basis.

> [accordion] WebView
>
> If your website is likely to be accessed mostly in the Facebook browser or via other mobile applications in a WebView, it might face certain issues. Refer to our [Callback URL documentation](https://razorpay.com/docs/payments/payment-gateway/callback-url.md) for more details on how to handle this.

> [accordion] Network Connectivity Issues
>
> If the customer has an issue with the network connectivity, you will not know of the payment completion from your website. In such cases, you can use our [Webhooks](https://razorpay.com/docs/webhooks) to get notified of all authorized payments and then you can mark them as successful at your end.

## Build Integration

A to-do-list for integration is given below:

> [accordion] Clone the Razorpay Sample Application in Your Language and Test the Payment Flow.
>
> You can clone any of the sample applications available in our [Integrations](https://razorpay.com/integrations/) page.

> [accordion] Integrate with Orders API on the Server Side.
>
> **Order is an important step in the payment process.**
>
> * An order should be created for every payment.
>
> * You can create an order using the [Orders API](#api-sample-code). It is a server-side API call. Know how to [authenticate](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys) Orders API.
>
> * The `order_id` received in the response should be passed to the checkout. This ties the order with the payment and secures the request from being tampered.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Payments made without an `order_id` cannot be captured and will be automatically refunded. You must create an order before initiating payments to ensure proper payment processing.
>
> You can create an order:
>
> * Using the sample code on the Razorpay Postman Public Workspace.
> * By manually integrating the API sample codes on your server.
>
> #### Razorpay Postman Public Workspace
>
> You can use the Postman workspace below to create an order:
>
> [![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/request/12492020-6f15a901-06ea-4224-b396-15cd94c6148d)
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Under the **Authorization** section in Postman, select **Basic Auth** and add the Key Id and secret as the Username and Password, respectively.
>
> #### API Sample Code
>
> Use this endpoint to create an order using the Orders API.
>
> `POST /orders`
>
> ```bash Curl theme={null}
> curl -X POST https://api.razorpay.com/v1/orders
> -U [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
> -H 'content-type:application/json'
> -d '{
>  "amount": 500,
>  "currency": "INR",
>  "receipt": "qwsaq1",
>  "partial_payment": true,
>  "first_payment_min_amount": 230,
>  "notes": {
>    "key1": "value3",
>    "key2": "value2"
>  }
> }'
> ```
>
> ```java Java theme={null}
> RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> JSONObject orderRequest = new JSONObject();
> orderRequest.put("amount",50000);
> orderRequest.put("currency","INR");
> orderRequest.put("receipt", "receipt#1");
> JSONObject notes = new JSONObject();
> notes.put("notes_key_1","Tea, Earl Grey, Hot");
> notes.put("notes_key_1","Tea, Earl Grey, Hot");
> orderRequest.put("notes",notes);
>
> Order order = instance.orders.create(orderRequest);
> ```
>
> ```python Python theme={null}
> import razorpay
> client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
> client.order.create({
>  "amount": 50000,
>  "currency": "INR",
>  "receipt": "receipt#1",
>  "partial_payment": False,
>  "notes": {
>    "key1": "value3",
>    "key2": "value2"
>  }
> })
> ```
>
> ```php PHP theme={null}
> $api = new Api($key_id, $secret);
>
> $api->order->create(array('receipt' => '123', 'amount' => 100, 'currency' => 'INR', 'notes'=> array('key1'=> 'value3','key2'=> 'value2')));
> ```
>
> ```csharp .NET theme={null}
> RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> Dictionary<string, object> orderRequest = new Dictionary<string, object>();
> orderRequest.Add("amount", 50000);
> orderRequest.Add("currency", "INR");
> orderRequest.Add("receipt", "receipt#1");
> Dictionary<string, object> notes = new Dictionary<string, object>();
> notes.Add("notes_key_1", "Tea, Earl Grey, Hot");
> notes.Add("notes_key_2", "Tea, Earl Grey, Hot");
> orderRequest.Add("notes", notes);
>
> Order order = client.Order.Create(orderRequest);
> ```
>
> ```ruby Ruby theme={null}
> require "razorpay"
> Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
>
> para_attr = {
>  "amount": 50000,
>  "currency": "INR",
>  "receipt": "receipt#1",
>  "notes": {
>    "key1": "value3",
>    "key2": "value2"
>  }
> }
>
> Razorpay::Order.create(para_attr)
> ```
>
> ```javascript Node.js theme={null}
> var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
>
> instance.orders.create({
>  "amount": 50000,
>  "currency": "INR",
>  "receipt": "receipt#1",
>  "partial_payment": false,
>  "notes": {
>    "key1": "value3",
>    "key2": "value2"
>  }
> })
> ```
>
> ```go Go theme={null}
> import ( razorpay "github.com/razorpay/razorpay-go" )
> client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
> data := map[string]interface{}{
>  "amount": 50000,
>  "currency": "INR",
>  "receipt": "some_receipt_id",
>  "partial_payment": false,
>  "notes": map[string]interface{}{
>      "key1": "value1",
>      "key2": "value2",
>    },
> }
> body, err := client.Order.Create(data, nil)
> ```
>
> ```json Success Response theme={null}
> {
>  "id": "order_IluGWxBm9U8zJ8",
>  "entity": "order",
>  "amount": 5000,
>  "amount_paid": 0,
>  "amount_due": 5000,
>  "currency": "INR",
>  "receipt": "rcptid_11",
>  "offer_id": null,
>  "status": "created",
>  "attempts": 0,
>  "notes": [],
>  "created_at": 1642662092
> }
> ```
>
> ```json Failure Response theme={null}
> {
>  "error": {
>    "code": "BAD_REQUEST_ERROR",
>    "description": "Order amount less than minimum amount allowed",
>    "source": "business",
>    "step": "payment_initiation",
>    "reason": "input_validation_failed",
>    "metadata": {},
>    "field": "amount"
>  }
> }
> ```
>
> > [accordion] Request Parameters
> >
> > `amount` *mandatory*
> > : `integer` Payment amount in the smallest currency subunit. For example, if the amount to be charged is ₹299, then pass `29900` in this field. In the case of three decimal currencies, such as KWD, BHD and OMR, to accept a payment of 295.991, pass the value as 295990. And in the case of zero decimal currencies such as JPY, to accept a payment of 295, pass the value as 295.
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to charge a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.
> >
> > `currency` *mandatory*
> > : `string` The currency in which the transaction should be made. See the [list of supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies). Length must be 3 characters.
> >
> > > [!NOTE]
> > >
> > > **Handy Tips**
> > >
> > > Razorpay has added support for zero decimal currencies, such as JPY and three decimal currencies, such as KWD, BHD and OMR, allowing businesses to accept international payments in these currencies. Know more about [Currency Conversion](https://razorpay.com/docs/payments/international-payments/currency-conversion.md) (May 2024).
> >
> > `receipt` *optional*
> > : `string` Your receipt id for this order should be passed here. Maximum length is 40 characters.
> >
> > `notes` *optional*
> > : `json object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.
> >
> > `partial_payment` *optional*
> > : `boolean` Indicates whether the customer can make a partial payment. Possible values:
> >
> > * `true`: The customer can make partial payments.
> > * `false` (default): The customer cannot make partial payments.
> >
> > `first_payment_min_amount` *optional*
> > : `integer` Minimum amount that must be paid by the customer as the first partial payment. For example, if an amount of ₹7000 is to be received from the customer in two installments of #1 - ₹5000, #2 - ₹2000 then you can set this value as `500000`. This parameter should be passed only if `partial_payment` is `true`.
> >
> > Know more about [Orders API](https://razorpay.com/docs/api/orders.md).
>
> > [accordion] Response Parameters
> >
> > Descriptions for the response parameters are present in the [Orders Entity](https://razorpay.com/docs/api/orders/entity.md) parameters table.
>
> > [accordion] Error Response Parameters
> >
> > The error response parameters are available in the [API Reference Guide](https://razorpay.com/docs/api/orders/create.md).
>
> A successful payment returns the following fields to the Checkout form.
>
> > [accordion] Success Callback
> >
> > * You need to store these fields in your server.
> > * You can confirm the authenticity of these details by verifying the signature in the next step.
> >
> > ```json Success Callback theme={null}
> > {
> >   "razorpay_payment_id": "pay_29QQoUBi66xm2f",
> >   "razorpay_order_id": "order_9A33XWu170gUtm",
> >   "razorpay_signature": "9ef4dffbfd84f1318f6739a3ce19f9d85851857ae648f114332d8401e0949a3d"
> > }
> > ```
> >
> > `razorpay_payment_id`
> > : `string` Unique identifier for the payment returned by Checkout **only** for successful payments.
> >
> > `razorpay_order_id`
> > : `string` Unique identifier for the order returned by Checkout.
> >
> > `razorpay_signature`
> > : `string` Signature returned by the Checkout. This is used to verify the payment.
>
> #### Test Heading
>
> The `razorpay_order_id`, returned on successful creation of the order, should be sent to the Checkout form. Additionally, you need to send an extra key-value pair as shown:
>
> ```
> {
>   "amount": "1000",
>    // and other options
>
>   "order_id": "order_CuEzONfnOI86Ab" // Order ID generated using Orders API
> }
> ```
>
> A successful payment for the Order returns `razorpay_order_id`, `razorpay_payment_id` and `razorpay_signature`, which is then used for payment verification.

> [accordion] Display the Checkout Form on Your Website to Your Customer.
>
> You can display the [Standard Checkout form](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard.md) on your website to collect payments from customers. Ensure that the `order_id` option is passed along with the other checkout options mentioned below.
>
> `key` *mandatory*
> : `string` API Key ID generated from the Dashboard.
>
> `amount` *mandatory*
> : `integer` Payment amount in the smallest currency subunit. For example, if the amount to be charged is , enter `222250` in this field. In the case of three decimal currencies, such as KWD, BHD and OMR, to accept a payment of 295.991, pass the value as 295990. And in the case of zero decimal currencies such as JPY, to accept a payment of 295, pass the value as 295.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to charge a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.
>
> `currency` *mandatory*
> : `string` The currency in which the payment should be made by the customer. See the list of [supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Razorpay has added support for zero decimal currencies, such as JPY, and three decimal currencies, such as KWD, BHD, and OMR, allowing businesses to accept international payments in these currencies. Know more about [Currency Conversion](https://razorpay.com/docs/payments/international-payments/currency-conversion.md) (May 2024).
>
> `name` *mandatory*
> : `string` Your Business/Enterprise name shown on the Checkout form. For example, **Acme Corp**.
>
> `description` *optional*
> : `string` Description of the purchase item shown on the Checkout form. It should start with an alphanumeric character.
>
> `image` *optional*
> : `string` Link to an image (usually your business logo) shown on the Checkout form. Can also be a **base64** string if you are not loading the image from a network.
>
> `order_id` *mandatory*
> : `string` Order ID generated via [Orders API](https://razorpay.com/docs/api/orders.md).
>
> `prefill`
> : `object` You can prefill the following details at Checkout.
>
> > [!NOTE]
> >
> > **Boost Conversions and Minimise Drop-offs**
> >
> > * Autofill customer contact details, especially phone number to ease form completion. Include customer’s phone number in the `contact` parameter of the JSON request's `prefill` object. Format: +(country code)(phone number). Example: "contact": "+919000090000".
> > * This is not applicable if you do not collect customer contact details on your website before checkout, have Shopify stores or use any of the no-code apps.
>
> `name` *optional*
> : `string` Cardholder's name to be prefilled if customer is to make card payments on Checkout. For example, **Gaurav Kumar**.
>
> `email` *optional*
> : `string` Email address of the customer.
>
> `contact` *optional*
> : `string` Phone number of the customer. The expected format of the phone number is `+ {country code}{phone number}`. If the country code is not specified, `91` will be used as the default value. This is particularly important while prefilling `contact` of customers with phone numbers issued outside India. **Examples**:
>
> * +14155552671 (a valid non-Indian number)
> * +919977665544 (a valid Indian number). \
>   If 9977665544 is entered, `+91` is added to it as +919977665544.
>
> `method` *optional*
> : `string` Pre-selection of the payment method for the customer. Will only work if `contact` and `email` are also prefilled. Possible values:
>
> <ul>
>   <li>`card`</li>
>   <li>`netbanking`</li>
>   <li>`wallet`</li>
>   <li>`upi`</li>
>   <li>`emi`</li>
> </ul>
>
> `notes` *optional*
> : `object` Set of key-value pairs that can be used to store additional information about the payment. It can hold a maximum of 15 key-value pairs, each 256 characters long (maximum).
>
> `theme`
> : `object` Thematic options to modify the appearance of Checkout.
>
> `color` *optional*
> : `string` Enter your brand colour's HEX code to alter the text, payment method icons and CTA (call-to-action) button colour of the Checkout form.
>
> `backdrop_color` *optional*
> : `string` Enter a HEX code to change the Checkout's backdrop colour.
>
> `modal`
> : `object` Options to handle the Checkout modal.
>
> `backdropclose` *optional*
> : `boolean` Indicates whether clicking the translucent blank space outside the Checkout form should close the form. Possible values:
>
> * `true`: Closes the form when your customer clicks outside the checkout form.
> * `false` (default): Does not close the form when customer clicks outside the checkout form.
>
> `escape` *optional*
> : `boolean` Indicates whether pressing the **escape** key should close the Checkout form. Possible values:
>
> * `true` (default): Closes the form when the customer presses the **escape** key.
> * `false`: Does not close the form when the customer presses the **escape** key.
>
> `handleback` *optional*
> : `boolean` Determines whether Checkout must behave similar to the browser when back button is pressed. Possible values:
>
> * `true` (default): Checkout behaves similarly to the browser. That is, when the browser's back button is pressed, the Checkout also simulates a back press. This happens as long as the Checkout modal is open.
> * `false`: Checkout does not simulate a back press when browser's back button is pressed.
>
> `confirm_close` *optional*
> : `boolean` Determines whether a confirmation dialog box should be shown if customers attempts to close Checkout. Possible values:
>
> * `true`: Confirmation dialog box is shown.
> * `false` (default): Confirmation dialog box is not shown.
>
> `ondismiss` *optional*
> : `function` Used to track the status of Checkout. You can pass a modal object with `ondismiss: function()\{\}` as options. This function is called when the modal is closed by the user. If `retry` is `false`, the `ondismiss` function is triggered when checkout closes, even after a failure.
>
> `animation` *optional*
> : `boolean` Shows an animation before loading of Checkout. Possible values:
>
> * `true`(default): Animation appears.
> * `false`: Animation does not appear.
>
> `subscription_id` *optional*
> : `string` If you are accepting recurring payments using Razorpay Checkout, you should pass the relevant `subscription_id` to the Checkout. Know more about [Subscriptions on Checkout](https://razorpay.com/docs/api/payments/subscriptions-custom#checkout-integration).
>
> `subscription_card_change` *optional*
> : `boolean` Permit or restrict customer from changing the card linked to the subscription. You can also do this from the [hosted page](https://razorpay.com/docs/payments/subscriptions/payment-retries.md#update-payment-method-on-our-hosted-page). Possible values:
>
> * `true`: Allow the customer to change the card from Checkout.
> * `false` (default): Do not allow the customer to change the card from Checkout.
>
> `recurring` *optional*
> : `boolean` Determines if you are accepting [recurring (charge-at-will) payments on Checkout](https://razorpay.com/docs/api/payments/recurring-payments) via instruments such as emandate, paper NACH and so on. Possible values:
>
> * `true`: You are accepting recurring payments.
> * `false` (default): You are not accepting recurring payments.
>
> `callback_url` *optional*
> : `string` Customers will be redirected to this URL on successful payment. Ensure that the domain of the Callback URL is allowlisted.
>
> `redirect` *optional*
> : `boolean` Determines whether to post a response to the event handler post payment completion or redirect to Callback URL. `callback_url` must be passed while using this parameter. Possible values:
>
> * `true`: Customer is redirected to the specified callback URL in case of payment failure.
> * `false` (default): Customer is shown the Checkout popup to retry the payment with the suggested next best option.
>
> `customer_id` *optional*
> : `string` Unique identifier of customer. Used for:
>
> * [Local saved cards feature](https://razorpay.com/docs/payments/payment-methods/cards/features/saved-cards.md#manage-saved-cards).
> * Static bank account details on Checkout in case of [Bank Transfer payment method](https://razorpay.com/docs/payments/payment-methods/bank-transfer.md).
>
> `remember_customer` *optional*
> : `boolean` Determines whether to allow saving of cards. Can also be configured via the [Dashboard](https://razorpay.com/docs/payments/dashboard/account-settings/checkout-features.md#flash-checkout). Possible values:
>
> * `true`: Enables card saving feature.
> * `false` (default): Disables card saving feature.
>
> `timeout` *optional*
> : `integer` Sets a timeout on Checkout, in seconds. After the specified time limit, the customer will not be able to use Checkout.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Some browsers may pause `JavaScript` timers when the user switches tabs, especially in power saver mode. This can cause the checkout session to stay active beyond the set timeout duration.
>
> `readonly`
> : `object` Marks fields as read-only.
>
> `contact` *optional*
> : `boolean` Used to set the `contact` field as readonly. Possible values:
>
> * `true`: Customer will not be able to edit this field.
> * `false` (default): Customer will be able to edit this field.
>
> `email` *optional*
> : `boolean` Used to set the `email` field as readonly. Possible values:
>
> * `true`: Customer will not be able to edit this field.
> * `false` (default): Customer will be able to edit this field.
>
> `name` *optional*
> : `boolean` Used to set the `name` field as readonly. Possible values:
>
> * `true`: Customer will not be able to edit this field.
> * `false` (default): Customer will be able to edit this field.
>
> `hidden`
> : `object` Hides the contact details.
>
> `contact` *optional*
> : `boolean` Used to set the `contact` field as optional. Possible values:
>
> * `true`: Customer will not be able to view this field.
> * `false` (default): Customer will be able to view this field.
>
> `email` *optional*
> : `boolean` Used to set the `email` field as optional. Possible values:
>
> * `true`: Customer will not be able to view this field.
> * `false` (default): Customer will be able to view this field.
>
> `send_sms_hash` *optional*
> : `boolean` Used to auto-read OTP for cards and netbanking pages. Applicable from Android SDK version 1.5.9 and above. Possible values:
>
> * `true`: OTP is auto-read.
> * `false` (default): OTP is not auto-read.
>
> `allow_rotation` *optional*
> : `boolean` Used to rotate payment page as per screen orientation. Applicable from Android SDK version 1.6.4 and above. Possible values:
>
> * `true`: Payment page can be rotated.
> * `false` (default): Payment page cannot be rotated.
>
> `retry` *optional*
> : `object` Parameters that enable retry of payment on the checkout.
>
> `enabled`
> : `boolean` Determines whether the customers can retry payments on the checkout. Possible values:
>
> * `true` (default): Enables customers to retry payments.
> * `false`: Disables customers from retrying the payment.
>
> `max_count`
> : `integer` The number of times the customer can retry the payment. We recommend you to set this to 4. Having a larger number here can cause loops to occur.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Web Integration does not support the `max_count` parameter. It is applicable only in Android and iOS SDKs.
>
> `config` *optional*
> : `object` Parameters that enable checkout configuration. Know more about how to [configure payment methods on Razorpay standard checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/configure-payment-methods.md).
>
> `display`
> : `object` Child parameter that enables configuration of checkout display language.
>
> `language`
> : `string` The language in which checkout should be displayed. Possible values:
>
> * `en`: English
> * `ben`: Bengali
> * `hi`: Hindi
> * `mar`: Marathi
> * `guj`: Gujarati
> * `tam`: Tamil
> * `tel`: Telugu

> [accordion] Verify the Signature Post Checkout Form Submission.
>
> This is a mandatory step to confirm the authenticity of the details returned to the Checkout form for successful payments.
>
> > [accordion] To verify the `razorpay_signature` returned to you by the Checkout form:
> >
> > 1. Create a signature in your server using the following attributes:
> >    * `order_id`: Retrieve the `order_id` from your server. Do not use the `razorpay_order_id` returned by Checkout.
> >    * `razorpay_payment_id`: Returned by Checkout.
> >    * `key_secret`: Available in your server. The `key_secret` that was generated from the [Dashboard](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys).
> > 2. Use the SHA256 algorithm, the `razorpay_payment_id` and the `order_id` to construct a HMAC hex digest as shown below:
> >
> > ```html HMAC Hex Digest theme={null}
> > generated_signature = hmac_sha256(order_id + "|" + razorpay_payment_id, secret);
> >
> >   if (generated_signature == razorpay_signature) {
> >     payment is successful
> >   }
> > ```
> >
> > 3. If the signature you generate on your server matches the `razorpay_signature` returned to you by the Checkout form, the payment received is from an authentic source.
>
> > [accordion] Generate Signature on Your Server
> >
> > Given below is the sample code for payment signature verification:
> >
> > ```java Java theme={null}
> > RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
> >
> > String secret = "EnLs21M47BllR3X8PSFtjtbd";
> >
> > JSONObject options = new JSONObject();
> > options.put("razorpay_order_id", "order_IEIaMR65cu6nz3");
> > options.put("razorpay_payment_id", "pay_IH4NVgf4Dreq1l");
> > options.put("razorpay_signature", "0d4e745a1838664ad6c9c9902212a32d627d68e917290b0ad5f08ff4561bc50f");
> >
> > boolean status =  Utils.verifyPaymentSignature(options, secret);
> > ```
> >
> > ```php PHP theme={null}
> > $api = new Api($key_id, $secret);
> >
> > $api->utility->verifyPaymentSignature(array('razorpay_order_id' => $razorpayOrderId, 'razorpay_payment_id' => $razorpayPaymentId, 'razorpay_signature' => $razorpaySignature));
> > ```
> >
> > ```ruby Ruby theme={null}
> > require "razorpay"
> > Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
> >
> > payment_response = {
> >        razorpay_order_id: 'order_IEIaMR65cu6nz3',
> >        razorpay_payment_id: 'pay_IH4NVgf4Dreq1l',
> >        razorpay_signature: '0d4e745a1838664ad6c9c9902212a32d627d68e917290b0ad5f08ff4561bc50f'
> >      }
> > Razorpay::Utility.verify_payment_signature(payment_response)
> > ```
> >
> > ```python Python theme={null}
> > import razorpay
> > client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
> >
> > client.utility.verify_payment_signature({
> >   'razorpay_order_id': razorpay_order_id,
> >   'razorpay_payment_id': razorpay_payment_id,
> >   'razorpay_signature': razorpay_signature
> >   })
> > ```
> >
> > ```c .NET theme={null}
> > RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
> >
> > Dictionary<string, string> options = new Dictionary<string, string>();
> > options.Add("razorpay_order_id", "order_IEIaMR65cu6nz3");
> > options.Add("razorpay_payment_id", "pay_IH4NVgf4Dreq1l");
> > options.Add("razorpay_signature", "0d4e745a1838664ad6c9c9902212a32d627d68e917290b0ad5f08ff4561bc50f");
> >
> > Utils.verifyPaymentSignature(options);
> > ```
> >
> > ```javascript Node.js theme={null}
> > var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
> >
> > var { validatePaymentVerification, validateWebhookSignature } = require('./dist/utils/razorpay-utils');
> > validatePaymentVerification({"order_id": razorpayOrderId, "payment_id": razorpayPaymentId }, signature, secret);
> > ```
> >
> > ```go Go theme={null}
> > import ( razorpay "github.com/razorpay/razorpay-go" )
> > client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
> >
> > params := map[string]interface{}{
> >  "razorpay_order_id": "order_IEIaMR65cu6nz3",
> >  "razorpay_payment_id": "pay_IH4NVgf4Dreq1l",
> > }
> >
> > signature := "0d4e745a1838664ad6c9c9902212a32d627d68e917290b0ad5f08ff4561bc50f";
> > secret := "EnLs21M47BllR3X8PSFtjtbd";
> > utils.VerifyPaymentSignature(params, signature, secret)
> > ```
>
> > [accordion] Post Signature Verification
> >
> > After you have completed the integration, you can [set up webhooks](https://razorpay.com/docs/webhooks/setup-edit-payments.md), make test payments, replace the test key with the live key and integrate with other [APIs](https://razorpay.com/docs/api).

> [accordion] Display the Confirmation Message to the Customer.
>
> You must display a `payment successful` message to the customer.

> [accordion] Mark the Platform Order as Successful.
>
> After verifying the signature, fetch the order in your system that corresponds to `razorpay_order_id` in your database. You can now mark this fetched order as successful and process the order.
>
> You can make a test payment to check whether the integration works.

## Common Issues Faced During Integration

Following are some of the common issues that you must watch out for while integrating:

1. Not storing the Razorpay order ID at your end.
2. Passing the amount from the frontend to the Razorpay order creation call.
3. Passing `USD` or any other `non-SGD` currency while creating the order.
4. Passing `razorpay_order_id` from the frontend while verifying the signature.

Alternatively, you can use this value to check the integrity of the signature while looking up the corresponding order at your end with this Razorpay order ID and marking only that as successful.

## Support

If you have queries, raise a ticket on the [Razorpay Support Portal](https://razorpay.com/support/).
