> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Integrate your PHP-based website with our SDK to start accepting payments using the Razorpay Payment Gateway.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

> [card] [Payment Gateway](https://razorpay.com/docs/sg/payments/server-integration/php/integration-steps.md#integrate-with-razorpay-payment-gateway)
>
> Integrate with Razorpay Payment Gateway.

> [card] [Other Razorpay Products](https://razorpay.com/docs/sg/payments/server-integration/php/integration-steps.md#integrate-with-other-razorpay-products)
>
> Integrate with other Razorpay products using API sample codes.

## Integrate With Razorpay Payment Gateway

Start accepting domestic payments from customers on your website using the Razorpay Payment Gateway. Razorpay has developed the Standard Checkout method and manages it. You can configure **payment methods, orders, company logo** and also select **custom colour** based on your convenience. Razorpay supports these [payment methods](https://razorpay.com/docs/sg/payments/payment-methods).

> [card] Sample App
>
> We recommend you check the [PHP Sample App](https://razorpay.com/docs/build/browser/assets/images/razorpay-php-sample-project.zip).

> [card] GitHub Repository
>
> Download the latest [razorpay-php.zip](https://github.com/razorpay/razorpay-php/releases/) file from GitHub. It is pre-compiled to include all dependencies.

> [!WARNING]
>
> **Watch Out!**
>
> Ensure you are using 5.6 or a higher version of the [PHP Official SDK](https://www.php.net/downloads).

> [!NOTE]
>
> **Handy Tips**
>
> You can also download the [Razorpay PHP Test App](https://github.com/razorpay/razorpay-php-testapp) directly from GitHub.

### Project Structure

Before you begin, we recommend you check the [PHP Sample App](https://razorpay.com/docs/build/browser/assets/images/razorpay-php-sample-project.zip), and verify that your project contains the following files:

| File Name | Purpose |
| - | - |
| index.php | Contains the Orders API and Checkout code. |
| config.php | Contains the API Keys. |
| verify.php | Contains the payment signature verification code. |
| success.html | A page to redirect users once the payment is successful. |

**Before you proceed:**

<ul>
  <li>Create a [Razorpay account](https://dashboard.razorpay.com/signup). </li>
  <li>Generate the [API Keys](https://razorpay.com/docs/sg/payments/dashboard/account-settings/api-keys.md#generate-api-keys) from the Dashboard. To go live with the integration and start accepting real payments, generate Live Mode API Keys and replace them in the integration.</li>
  <li>Know about the [Payment Flow](https://razorpay.com/docs/sg/payments/payment-gateway/how-it-works.md) and follow these integration steps:</li>
</ul>

> [card] [1. Build Integration](https://razorpay.com/docs/sg/payments/server-integration/php/integration-steps.md#1-build-integration)
>
> Integrate with your PHP-based website.

> [card] [2. Test Integration](https://razorpay.com/docs/sg/payments/server-integration/php/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-live Checklist](https://razorpay.com/docs/sg/payments/server-integration/php/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

### 1. Build Integration

> [accordion] 1 Create an Order in Server
>
> Order is an important step in the payment process.
>
> * An order should be created for every payment.
>
> * You can create an order using the [Orders API](#1-1-sample-code). It is a server-side API call.  Know how to [authenticate](https://razorpay.com/docs/sg/api/authentication.md#generate-api-keys) Orders API.
>
> * The `order_id` received in the response should be passed to the checkout. This ties the Order with the payment and secures the request from being tampered.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Payments made without an `order_id` cannot be captured and will be automatically refunded. You must create an order before initiating payments to ensure proper payment processing.
>
> > [accordion] 1.1 Sample Code
> >
> > In the sample app, the **index.php** file contains the code for order creation using Orders API.
> >
> > ```php Request theme={null}
> > $api->order->create(array('receipt' => '123', 'amount' => 5000, 'currency' => 'SGD', 'notes'=> array('key1'=> 'value3','key2'=> 'value2'))); // Amount is in currency subunits. 
> > ```
> >
> > ```json Response theme={null}
> > {
> > "id": "order_EKwxwAgItmmXXX",
> > "entity": "order",
> > "amount": 5000,
> > "amount_paid": 0,
> > "amount_due": 5000,
> > "currency": "SGD",
> > "receipt": "receipt#1",
> > "offer_id": null,
> > "status": "created",
> > "attempts": 0,
> > "notes": [],
> > "created_at": 1582628071
> > }
> > ```
>
> > [accordion] 1.2 Request Parameters
> >
> > Here is the list of parameters for creating an order:
> >
> > `amount` *mandatory*
> > : `integer` The amount to be paid by the customer in cents. For example, if the amount is ₹500, enter `50000`.
> >
> > `currency` *mandatory*
> > : `string` The currency in which the payment should be made by the customer. Length must be of 3 characters.
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
> > [accordion] 1.3 Response Parameters
> >
> > Descriptions for the response parameters are present in the [Orders Entity](https://razorpay.com/docs/sg/api/orders/entity.md) table.
>
> > [accordion] 1.4 Error Response Parameters
> >
> > The error response parameters are available in the [API Reference Guide](https://razorpay.com/docs/api/orders/create.md#errors).

> [accordion] 2 Add Checkout Options
>
> Add the Razorpay Checkout options to your project. For example, if you are using HTML for your front-end, create a page called **pay.html** and add the Pay button on your web page using the checkout code and either the callback URL or handler function.
>
> > [accordion] 2.1 Callback URL or Handler Function
> >
> > | **Callback URL** | **Handler Function** |
> > | - | - |
> > | When you use this: <ul><li> On successful payment, the customer is redirected to the specified URL, for example, a payment success page. </li><li> On failure, the customer is asked to retry the payment.</li></ul> | When you use this: <ul><li> On successful payment, the customer is shown your web page. </li><li> On failure, the customer is notified of the failure and asked to retry the payment.</li></ul> |
>
> > [accordion] 2.2 Code to Add Pay Button
> >
> > Copy-paste the parameters as `options` in your code:
> >
> > ```html PHP Checkout Code theme={null}
> > $data = [
> >     "key"               => $YOUR_KEY_ID, // Enter the Key ID generated from the Dashboard
> >     "amount"            => $5000, // Amount is in currency subunits. 
> >     "currency"          => $SGD,
> >     "name"              => "Acme Corp",
> >     "description"       => "Test transaction",
> >     "image"             => "https://cdn.razorpay.com/logos/GhRQcyean79PqE_medium.png",
> >     "prefill"           => [
> >     "name"              => "<name>",
> >     "email"             => "<email>",
> >     "contact"           => "<phone>",
> >     ],
> >     "notes"             => [
> >     "address"           => "Razorpay Corporate Office",
> >     "merchant_order_id" => "12312321",
> >     ],
> >     "theme"             => [
> >     "color"             => "#3399cc"
> >     ],
> >     "order_id"          => $order_IluGWxBm9U8zJ8, // This is a sample Order ID. Pass the `id` obtained in the response of Step 1
> > ];
> >
> > $json = json_encode($data);
> > require("checkout/{$checkout}.php");
> > ```
> >
> > ```html Checkout Code (JS) theme={null}
> > // Set your callback URL
> > $callback_url = "http://localhost:8000/success.html";
> >
> > // Include Razorpay Checkout.js library
> > echo '<script src="https://checkout.razorpay.com/v1/checkout.js"></script>';
> >
> > // Create a payment button with Checkout.js
> > echo '<button onclick="startPayment()">Pay with Razorpay</button>';
> >
> > // Add a script to handle the payment
> > echo '<script>
> >     function startPayment() {
> >         var options = {
> >             key: "' . $YOUR_KEY_ID . '", // Enter the Key ID generated from the Dashboard
> >             amount: ' . $order->5000 . ', // Amount is in currency subunits. 
> >             currency: "' . $order->SGD . '",
> >             name: "Acme Corp",
> >             description: "Test transaction",
> >             image: "https://cdn.razorpay.com/logos/GhRQcyean79PqE_medium.png",
> >             order_id: "' . $order_IluGWxBm9U8zJ8 . '", // This is a sample Order ID. Pass the `id` obtained in the response of Step 1
> >             prefill: {
> >                 name: "<name>",
> >                 email: "<email>",
> >                 contact: "<phone>"
> >             },
> >             notes: {
> >                 address: "Razorpay Corporate Office"
> >             },
> >             theme: {
> >                 "color": "#3399cc"
> >             },
> >             callback_url: "' . $callback_url . '"
> >         };
> >         var rzp = new Razorpay(options);
> >         rzp.open();
> >     }
> > </script>';
> > ```
> >
> > > [!NOTE]
> > >
> > > **Handy Tips**
> > >
> > > * If you want to use this as your final code, follow the steps given below:
> > >
> > >   1. Edit the `[KEY_ID]` inside the html file. Use the test keys while testing your application.  Know how to [Generate API keys](https://razorpay.com/docs/sg/api/authentication.md#generate-api-keys).
> > >
> > >   2. Edit the `[KEY_ID]` and `[KEY_SECRET]` in **config.php**. \\
> > > * Test your integration using these [test cards](https://razorpay.com/docs/sg/payments/server-integration/php/integration-steps.md#2-test-integration).
>
> > [accordion] 2.3 Checkout Options
> >
> > `key` *mandatory*
> > : `string` API Key ID generated from the Dashboard.
> >
> > `amount` *mandatory*
> > : `integer` The amount to be paid by the customer in cents. For example, if the amount is , enter `22225`.
> >
> > `currency` *mandatory*
> > : `string` The currency in which the payment should be made by the customer. Length must be of 3 characters.
> >
> > `name` *mandatory*
> > : `string` Your Business/Enterprise name shown on the Checkout form. For example, **Acme Corp**.
> >
> > `description` *optional*
> > : `string` Description of the purchase item shown on the Checkout form. It should start with an alphanumeric character.
> >
> > `image` *optional*
> > : `string` Link to an image (usually your business logo) shown on the Checkout form. Can also be a **base64** string if you are not loading the image from a network.
> >
> > `order_id` *mandatory*
> > : `string` Order ID generated via [Orders API](https://razorpay.com/docs/api/orders.md).
> >
> > `prefill`
> > : `object` You can prefill the following details at Checkout.
> >
> > > [!NOTE]
> > >
> > > **Boost Conversions and Minimise Drop-offs**
> > >
> > > * Autofill customer contact details, especially phone number to ease form completion. Include customer’s phone number in the `contact` parameter of the JSON request's `prefill` object. Format: +(country code)(phone number). Example: "contact": "+6591119111".
> > > * This is not applicable if you do not collect customer contact details on your website before checkout, have Shopify stores or use any of the no-code apps.
> >
> > `name` *optional*
> > : `string` Cardholder's name to be prefilled if customer is to make card payments on Checkout. For example, **Alex Lim**.
> >
> > `email` *optional*
> > : `string` Email address of the customer.
> >
> > `contact` *optional*
> > : `string` Phone number of the customer. The expected format of the phone number is `+ {country code}{phone number}`. If the country code is not specified, `65` will be used as the default value. This is particularly important while prefilling `contact` of customers with phone numbers issued outside Singapore. **Examples**:
> >
> > * +14155552671 (a valid non-Singaporean number)
> > * +6591119111 (a valid Singaporean number). \
> >   If 91119111 is entered, `+65` is added to it as +6591119111.
> >
> > `method` *optional*
> > : `string` Pre-selection of the payment method for the customer. Will only work if `contact` and `email` are also prefilled. Possible values:
> >
> > * `card`
> > * `paynow`
> >
> > `notes` *optional*
> > : `object` Set of key-value pairs that can be used to store additional information about the payment. It can hold a maximum of 15 key-value pairs, each 256 characters long (maximum).
> >
> > `theme`
> > : `object` Thematic options to modify the appearance of Checkout.
> >
> > `color` *optional*
> > : `string` Enter your brand colour's HEX code to alter the text, payment method icons and CTA (call-to-action) button colour of the Checkout form.
> >
> > `backdrop_color` *optional*
> > : `string` Enter a HEX code to change the Checkout's backdrop colour.
> >
> > `modal`
> > : `object` Options to handle the Checkout modal.
> >
> > `backdropclose` *optional*
> > : `boolean` Indicates whether clicking the translucent blank space outside the Checkout form should close the form. Possible values:
> >
> > * `true`: Closes the form when your customer clicks outside the checkout form.
> > * `false` (default): Does not close the form when customer clicks outside the checkout form.
> >
> > `escape` *optional*
> > : `boolean` Indicates whether pressing the **escape** key should close the Checkout form. Possible values:
> >
> > * `true` (default): Closes the form when the customer presses the **escape** key.
> > * `false`: Does not close the form when the customer presses the **escape** key.
> >
> > `handleback` *optional*
> > : `boolean` Determines whether Checkout must behave similar to the browser when back button is pressed. Possible values:
> >
> > * `true` (default): Checkout behaves similarly to the browser. That is, when the browser's back button is pressed, the Checkout also simulates a back press. This happens as long as the Checkout modal is open.
> > * `false`: Checkout does not simulate a back press when browser's back button is pressed.
> >
> > `confirm_close` *optional*
> > : `boolean` Determines whether a confirmation dialog box should be shown if customers attempts to close Checkout. Possible values:
> >
> > * `true`: Confirmation dialog box is shown.
> > * `false` (default): Confirmation dialog box is not shown.
> >
> > `ondismiss` *optional*
> > : `function` Used to track the status of Checkout. You can pass a modal object with `ondismiss: function()\{\}` as options. This function is called when the modal is closed by the user. If `retry` is `false`, the `ondismiss` function is triggered when checkout closes, even after a failure.
> >
> > `animation` *optional*
> > : `boolean` Shows an animation before loading of Checkout. Possible values:
> >
> > * `true`(default): Animation appears.
> > * `false`: Animation does not appear.
> >
> > `callback_url` *optional*
> > : `string` Customers will be redirected to this URL on successful payment. Ensure that the domain of the Callback URL is allowlisted.
> >
> > `redirect` *optional*
> > : `boolean` Determines whether to post a response to the event handler post payment completion or redirect to Callback URL. `callback_url` must be passed while using this parameter. Possible values:
> >
> > * `true`: Customer is redirected to the specified callback URL in case of payment failure.
> > * `false` (default): Customer is shown the Checkout popup to retry the payment with the suggested next best option.
> >
> > `timeout` *optional*
> > : `integer` Sets a timeout on Checkout, in seconds. After the specified time limit, the customer will not be able to use Checkout.
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > Some browsers may pause `JavaScript` timers when the user switches tabs, especially in power saver mode. This can cause the checkout session to stay active beyond the set timeout duration.
> >
> > `readonly`
> > : `object` Marks fields as read-only.
> >
> > `contact` *optional*
> > : `boolean` Used to set the `contact` field as readonly. Possible values:
> >
> > * `true`: Customer will not be able to edit this field.
> > * `false` (default): Customer will be able to edit this field.
> >
> > `email` *optional*
> > : `boolean` Used to set the `email` field as readonly. Possible values:
> >
> > * `true`: Customer will not be able to edit this field.
> > * `false` (default): Customer will be able to edit this field.
> >
> > `name` *optional*
> > : `boolean` Used to set the `name` field as readonly. Possible values:
> >
> > * `true`: Customer will not be able to edit this field.
> > * `false` (default): Customer will be able to edit this field.
> >
> > `hidden`
> > : `object` Hides the contact details.
> >
> > `contact` *optional*
> > : `boolean` Used to set the `contact` field as optional. Possible values:
> >
> > * `true`: Customer will not be able to view this field.
> > * `false` (default): Customer will be able to view this field.
> >
> > `email` *optional*
> > : `boolean` Used to set the `email` field as optional. Possible values:
> >
> > * `true`: Customer will not be able to view this field.
> > * `false` (default): Customer will be able to view this field.
> >
> > `send_sms_hash` *optional*
> > : `boolean` Used to auto-read OTP for cards. Applicable from Android SDK version 1.5.9 and above. Possible values:
> >
> > * `true`: OTP is auto-read.
> > * `false` (default): OTP is not auto-read.
> >
> > `allow_rotation` *optional*
> > : `boolean` Used to rotate payment page as per screen orientation. Applicable from Android SDK version 1.6.4 and above. Possible values:
> >
> > * `true`: Payment page can be rotated.
> > * `false` (default): Payment page cannot be rotated.
> >
> > `retry` *optional*
> > : `object` Parameters that enable retry of payment on the checkout.
> >
> > `enabled`
> > : `boolean` Determines whether the customers can retry payments on the checkout. Possible values:
> >
> > * `true` (default): Enables customers to retry payments.
> > * `false`: Disables customers from retrying the payment.
> >
> > `max_count`
> > : `integer` The number of times the customer can retry the payment. We recommend you to set this to 4. Having a larger number here can cause loops to occur.
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > Web Integration does not support the `max_count` parameter. It is applicable only in Android and iOS SDKs.
> >
> > `config` *optional*
> > : `object` Parameters that enable checkout configuration. Know more about how to [configure payment methods on Razorpay standard checkout](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/configure-payment-methods.md).
> >
> > `display`
> > : `object` Child parameter that enables configuration of checkout display language.
> >
> > `language`
> > : `string` The language in which checkout should be displayed. Possible value is `en`: English.
> >
> > > [!NOTE]
> > >
> > > **Handy Tips**
> > >
> > > The open method of Razorpay object (`rzp1.open()`) must be invoked by your site's JavaScript, which may or may not be a user-driven action such as a click.
>
> > [accordion] 2.4 Handle Payment Success and Failure
> >
> > The way the Payment Success and Failure scenarios are handled depends on the [Checkout Sample Code](#2-2-code-to-add-pay-button) you used in the last step.
> >
> > > [accordion] Checkout with Callback URL
> > >
> > > If you used the sample code with the callback URL:
> > >
> > > > [tab] On Payment Success
> > > >
> > > > Razorpay makes a POST call to the callback URL with the **razorpay\_payment\_id**, **razorpay\_order\_id** and **razorpay\_signature** in the response object of the successful payment. Only successful authorisations are auto-submitted.
> > >
> > > > [tab] On Payment Failure
> > > >
> > > > In case of failed payments, the checkout is displayed again to facilitate payment retry.
> >
> > > [accordion] Checkout with Handler Function
> > >
> > > If you used the sample code with the handler function:
> > >
> > > > [tab] On Payment Success
> > > >
> > > > The customer sees your website page. The checkout returns the response object of the successful payment (**razorpay\_payment\_id**, **razorpay\_order\_id** and **razorpay\_signature**). Collect these and send them to your server.
> > >
> > > > [tab] On Payment Failure
> > > >
> > > > The customer is notified about payment failure and asked to retry the payment.
> > >
> > > Use the Success/Failure Handling code given below:
> > >
> > > ```javascript Success Handling Code theme={null}
> > > "handler": function (response){
> > >     alert(response.razorpay_payment_id);
> > >     alert(response.razorpay_order_id);
> > >     alert(response.razorpay_signature)}
> > > ```
> > >
> > > ```javascript Failure Handling Code theme={null}
> > > rzp1.on('payment.failed', function (response){
> > >     alert(response.error.code);
> > >     alert(response.error.description);
> > >     alert(response.error.source);
> > >     alert(response.error.step);
> > >     alert(response.error.reason);
> > >     alert(response.error.metadata.order_id);
> > >     alert(response.error.metadata.payment_id);
> > > }
> > > ```
>
> > [accordion] 2.5 Configure Payment Methods *(Optional)*
> >
> > Multiple payment methods are available on Razorpay Standard Checkout.
> >
> > * The payment methods are **fixed** and cannot be changed.
> > * You can configure the order or make certain payment methods prominent. Know more about configuring payment methods. Know more about [configuring payment methods](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/configure-payment-methods.md).

> [accordion] 3 Store Fields in Your Server
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

> [accordion] 4 Verify Payment Signature
>
> This is a mandatory step that allows you to confirm the authenticity of the details returned to the checkout for successful payments.
>
> To verify the `razorpay_signature` returned to you by the checkout:
>
> 1. Create a signature in your server using the following attributes:
>
> | Attribute | Description |
> | - | - |
> | `order_id` | Retrieve the `order_id` from your server. Do not use the `razorpay_order_id` returned by checkout. |
> | `razorpay_payment_id` | Returned during checkout. |
> | `key_secret` | Available in your server. The `key_secret` that was generated from the  [Dashboard](https://razorpay.com/docs/sg/api/authentication.md#generate-api-keys).   [Dashboard](https://razorpay.com/docs/sg/payments/dashboard/account-settings/api-keys.md#generate-api-keys). |
>
> 2. Use the SHA256 algorithm, the `razorpay_payment_id` and the `order_id` to construct an HMAC hex digest as shown below:
>
> ```
> generated_signature = hmac_sha256(order_id + "|" + razorpay_payment_id, secret);
>
>     if (generated_signature == razorpay_signature) {
>     payment is successful
>     }
> ```
>
> 3. If the signature you generate on your server matches the `razorpay_signature` returned to you by the checkout, the payment received is from an authentic source.
>
>    Use the code given below to generate signature on your server:
>
> ```php Verify Payment Signature theme={null}
> $api = new Api($key_id, $secret);
>
> $api->utility->verifyPaymentSignature(array('razorpay_order_id' => $razorpayOrderId, 'razorpay_payment_id' => $razorpayPaymentId, 'razorpay_signature' => $razorpaySignature));
> ```

> [accordion] 5 Verify Payment Status
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > On the Dashboard, ensure that the payment status is `captured`. Refer to the payment capture settings page to know how to [capture payments automatically](https://razorpay.com/docs/sg/payments/payments/capture-settings.md).
>
> You can track the payment status in three ways:
>
> > [tab] Verify Status from Dashboard
> >
> > To verify the payment status from the Dashboard:
> >
> > 1. Log in to the Dashboard and navigate to **Transactions** → **Payments**.
> > 2. Check if a **Payment Id** has been generated and note the status. In case of a successful payment, the status is marked as **Captured**.
>
> > [tab] Subscribe to Webhook Events
> >
> > You can use Razorpay webhooks to configure and receive notifications when a specific event occurs. When one of these events is triggered, we send an HTTP POST payload in JSON to the webhook's configured URL. Know how to [set up webhooks.](https://razorpay.com/docs/sg/webhooks/setup-edit-payments.md)
> >
> > #### Example
> >
> > If you have subscribed to the `order.paid` webhook event, you will receive a notification every time a customer pays you for an order.
> >
> > Given below is the webhook signature verification sample code.
> >
> > ```php PHP theme={null}
> > /* PHP SDK: https://github.com/razorpay/razorpay-php */
> > use Razorpay\Api\Api;
> > $api = new Api("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
> >
> > $api->utility->verifyWebhookSignature($webhookBody, $webhookSignature, $webhookSecret);
> > // $webhookBody should be raw webhook request body
> > ```
>
> > [tab] Poll APIs
> >
> > [Poll Payment APIs](https://razorpay.com/docs/sg/api/payments/fetch-all-payments.md) to check the payment status.

### 2. Test Integration

After the integration is complete, a **Pay** button appears on your webpage/app.

Click the button and make a test transaction to ensure the integration is working as expected. You can start accepting actual payments from your customers once the test transaction is successful.

> [!WARNING]
>
> **Watch Out!**
>
> This is a mock payment page that uses your test API keys, test card and payment details.
>
> * Ensure you have entered only your [Test Mode API keys](https://razorpay.com/docs/sg/payments/dashboard/account-settings/api-keys.md#generate-api-keys) in the Checkout code.
> * Test mode features a mock bank page with **Success** and **Failure** buttons to replicate the live payment experience.
> * No real money is deducted due to the usage of test API keys. This is a simulated transaction.

Following are all the payment modes that the customer can use to complete the payment on the Checkout. Some of them are available by default, while others may require approval from us. Raise a request from the Dashboard to enable such payment methods.

| Payment Method | Code | Availability |
| - | - | - |
| [Debit and Credit Cards](https://razorpay.com/docs/sg/payments/payment-methods/cards.md) | `card` | ✓ |
| [PayNow](https://razorpay.com/docs/sg/payments/payment-methods/paynow.md) | `paynow` | ✓ |

You can make test payments using one of the payment methods configured at the Checkout.

> [accordion] Cards
>
> You can use one of the following test cards to test transactions for your integration in Test Mode.
>
> | Card Network | Card Number | CVV & Expiry Date |
> | - | - | - |
> | Mastercard | 5272 0088 0623 5705 | Use a random CVV and any future date ^^ |
> | Visa | 4111 1111 1111 1112 | |
>
> Check the following lists:
>
> * [Supported Card Networks](https://razorpay.com/docs/sg/payments/payment-methods/cards.md).
> * [Cards Error Codes](https://razorpay.com/docs/sg/errors/payments/cards.md).

> [accordion] PayNow
>
> You can scan the QR code and make the payment using your PayNow-enabled bank app. Razorpay will redirect to a mock page where you can make the payment a success or a failure. Since this is Test Mode, we will not redirect you to the bank portals. Know more about [PayNow](https://razorpay.com/docs/sg/payments/payment-methods/paynow.md).

### 3. Go-live Checklist

Check the go-live checklist for Razorpay Web Standard Checkout integration. Consider these steps before taking the integration live.

> [accordion] 1 Accept Live Payments
>
> Perform an end-to-end simulation of funds flow in the Test Mode. Once confident that the integration is working as expected, switch to the Live Mode and start accepting payments from customers.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Ensure you are switching your test API keys with API keys generated in Live Mode.
>
> To generate API Keys in Live Mode on your Razorpay Dashboard:
>
> 1. Log in to the Razorpay Dashboard and switch to **Live Mode** on the menu.
> 2. Navigate to **Account & Settings** → **API Keys** → **Generate Key** to generate the API Key for Live Mode.
> 3. Download the keys and save them securely.
> 4. Replace the Test API Key with the Live Key in the Checkout code and start accepting actual payments.

> [accordion] 2 Payment Capture
>
> After payment is `authorized`, you need to capture it to settle the amount to your bank account as per the settlement schedule. Payments that are not captured are auto-refunded after a fixed time.
>
> > [!WARNING]
> >
> > **Watch Out**
> >
> > * You should deliver the products or services to your customers only after the payment is captured. Razorpay automatically refunds all the uncaptured payments.
> > * You can track the payment status using our [Fetch a Payment API](https://razorpay.com/docs/sg/api/payments/fetch-with-id.md) or webhooks.
>
> > [tab] Auto-capture Payments (Recommended)
> >
> > Authorized payments can be automatically captured. You can auto-capture all payments [using global settings](https://razorpay.com/docs/sg/payments/payments/capture-settings.md#auto-capture-all-payments) on the Razorpay Dashboard. Know more about [capture settings for payments](https://razorpay.com/docs/sg/payments/payments/capture-settings.md).
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > Payment capture settings work only if you have integrated with Orders API on your server side. Know more about the [Orders API](https://razorpay.com/docs/sg/api/orders/create.md).
>
> > [tab] Manually Capture Payments
> >
> > Each authorized payment can also be captured individually. You can manually capture payments using [Payment Capture API](https://razorpay.com/docs/sg/api/payments/capture.md) or [Dashboard](https://razorpay.com/docs/sg/payments/payments/dashboard.md#manually-capture-payments). Know more about [capture settings for payments](https://razorpay.com/docs/sg/payments/payments/capture-settings.md).

> [accordion] 3 Set Up Webhooks
>
> Ensure you have [set up webhooks](https://razorpay.com/docs/sg/webhooks/setup-edit-payments.md) in the live mode and configured the events for which you want to receive notifications.
>
> > [!WARNING]
> >
> > **Implementation Considerations**
> >
> > Webhooks are the primary and most efficient method for event notifications. They are delivered asynchronously in near real-time. For critical user-facing flows that need instant confirmation (like showing "Payment Successful" immediately), supplement webhooks with API verification.
> >
> > **Recommended approach** \\
> >
> > * Rely on webhooks for all automation, which can be asynchronous.
> > * If a critical user-facing flow requires instant status, but the webhook notification has not arrived within the time mandated by your business needs, perform an immediate API Fetch call ([Payments](https://razorpay.com/docs/sg/api/payments/fetch-with-id.md), [Orders](https://razorpay.com/docs/sg/api/orders/fetch-with-id.md) and [Refunds](https://razorpay.com/docs/sg/api/refunds/fetch-specific-refund-payment.md)) to verify the status.

## Integrate With Other Razorpay Products

Razorpay offers a range of [payment products](https://razorpay.com/docs/sg/payments.md) to meet your business requirements. Visit our [GitHub repository](https://github.com/razorpay/razorpay-php) for sample codes.

#### Initialisation

```php php theme={null}
use Razorpay\Api\Api;

$api = new Api($api_key, $api_secret);
```

### Related Information

[Troubleshooting and FAQs](https://razorpay.com/docs/sg/payments/server-integration/php/troubleshooting-faqs.md)
