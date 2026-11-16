> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Steps to integrate with Razorpay Quick Integration.

Available in
🇮🇳 India

Follow these steps to integrate the standard checkout form on your website:

> [card] [1. Build Integration](https://razorpay.com/docs/payments/payment-gateway/quick-integration/integration-steps.md#1-build-integration)
>
> Integrate Standard Checkout form on website.

> [card] [2. Test Integration](https://razorpay.com/docs/payments/payment-gateway/quick-integration/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-live Checklist](https://razorpay.com/docs/payments/payment-gateway/quick-integration/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

## 1. Build Integration

Follow the steps given below:

> [accordion] 1 Create an Order in Server
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
> You can create an order using:
>
> > [tab] API Sample Code
> >
> > Use this endpoint to create an order using the Orders API.
> >
> > `POST /orders`
> >
> > ```bash Curl theme={null}
> > curl -X POST https://api.razorpay.com/v1/orders 
> > -U [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
> > -H 'content-type:application/json'
> > -d '{
> >     "amount": 50000,
> >     "currency": "INR",
> >     "receipt": "qwsaq1",
> >     "partial_payment": true,
> >     "first_payment_min_amount": 230
> > }'
> > ```
> >
> > ```java Java theme={null}
> > RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
> >
> > JSONObject orderRequest = new JSONObject();
> > orderRequest.put("amount", 50000); // amount in the smallest currency unit
> > orderRequest.put("currency", "INR");
> > orderRequest.put("receipt", "order_rcptid_11");
> >
> > Order order = razorpay.Orders.create(orderRequest);
> > } catch (RazorpayException e) {
> > // Handle Exception
> > System.out.println(e.getMessage());
> > }
> > ```
> >
> > ```python Python theme={null}
> > import razorpay
> > client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
> >
> > DATA = {
> >     "amount": 50000,
> >     "currency": "INR",
> >     "receipt": "receipt#1",
> >     "notes": {
> >         "key1": "value3",
> >         "key2": "value2"
> >     }
> > }
> > client.order.create(data=DATA)
> > ```
> >
> > ```php PHP theme={null}
> > $api = new Api($key_id, $secret);
> >
> > $api->order->create(array('receipt' => '123', 'amount' => 50000, 'currency' => 'INR', 'notes'=> array('key1'=> 'value3','key2'=> 'value2')));
> > ```
> >
> > ```csharp .NET theme={null}
> > RazorpayClient client = new RazorpayClient(your_key_id, your_secret);
> >
> > Dictionary<string, object> options = new Dictionary<string,object>();
> > options.Add("amount", 50000); // amount in the smallest currency unit
> > options.add("receipt", "order_rcptid_11");
> > options.add("currency", "INR");
> > Order order = client.Order.Create(options);
> > ```
> >
> > ```ruby Ruby theme={null}
> > require "razorpay"
> > Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
> >
> > options = amount: 50000, currency: 'INR', receipt: '<order_rcptid_11>'
> > order = Razorpay::Order.create
> > ```
> >
> > ```javascript Node.js theme={null}
> > var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
> >
> > instance.orders.create({
> > amount: 50000,
> > currency: "INR",
> > receipt: "receipt#1",
> > notes: {
> >     key1: "value3",
> >     key2: "value2"
> > }
> > })
> > ```
> >
> > ```go Go theme={null}
> > import ( razorpay "github.com/razorpay/razorpay-go" )
> > client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
> >
> > data := map[string]interface{}{
> > "amount": 50000,
> > "currency": "INR",
> > "receipt": "some_receipt_id"
> > }
> > body, err := client.Order.Create(data)
> > ```
> >
> > ```json Success Response theme={null}
> > {
> >     "id": "order_IluGWxBm9U8zJ8",
> >     "entity": "order",
> >     "amount": 50000,
> >     "amount_paid": 0,
> >     "amount_due": 50000,
> >     "currency": "INR",
> >     "receipt": "rcptid_11",
> >     "offer_id": null,
> >     "status": "created",
> >     "attempts": 0,
> >     "notes": [],
> >     "created_at": 1642662092
> > }
> > ```
> >
> > ```json Failure Response theme={null}
> > {
> > "error": {
> >     "code": "BAD_REQUEST_ERROR",
> >     "description": "Order amount less than minimum amount allowed",
> >     "source": "business",
> >     "step": "payment_initiation",
> >     "reason": "input_validation_failed",
> >     "metadata": {},
> >     "field": "amount"
> > }
> > }
> > ```
>
> > [tab] Razorpay Postman Public Workspace
> >
> > You can use the Postman workspace below to create an order:
> >
> > [![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/request/12492020-6f15a901-06ea-4224-b396-15cd94c6148d)
> >
> > > [!NOTE]
> > >
> > > **Handy Tips**
> > >
> > > Under the **Authorization** section in Postman, select **Basic Auth** and add the Key Id and secret as the Username and Password, respectively.
> >
> > You can create an order manually by integrating the API sample codes on your server.
>
> > [accordion] Request Parameters
> >
> > `amount` *mandatory*
> > : `integer` The transaction amount, expressed in the currency subunit. For example, for an actual amount of , the value of this field should be `22225`.
> >
> > `currency` *mandatory*
> > : `string` The currency in which the transaction should be made.  See the [list of supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies). Length must be of 3 characters.
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
> > : `integer` Minimum amount that must be paid by the customer as the first partial payment. For example, if an amount of ₹7,000 is to be received from the customer in two installments of #1 - ₹5,000, #2 - ₹2,000, then you can set this value as `500000`. This parameter should be passed only if `partial_payment` is `true`.
>
> > [accordion] Response Parameters
> >
> > Descriptions for the response parameters are present in the [Orders Entity](https://razorpay.com/docs/api/orders/entity.md) parameters table.
>
> > [accordion] Error Response Parameters
> >
> > The error response parameters are available in the [API Reference Guide](https://razorpay.com/docs/api/orders/create.md).

> [accordion] 2 Pass Order ID and Other Options to Checkout
>
> * This integration method provides a default **Pay with Razorpay** button that invokes the Checkout form.
>
> * Pass Checkout form options as data attributes inside a `<script>` tag. You can add any additional hidden or visible fields to the form, which will be submitted along with the form.
>
> * Send Checkout options as form-data to the following URL in a POST request.
>
> > [accordion] 2.1 Code to Add Pay Button
> >
> > `POST /https://www.example.com/success/`
> >
> > The following sample code passes the Razorpay checkout options as HTML data attributes:
> >
> > ```html Quick Integration theme={null}
> > <form action="https://www.example.com/success/" method="POST">
> > <script
> >    src="https://checkout.razorpay.com/v1/checkout.js"
> >     data-key="YOUR_KEY_ID" // Enter the Test API Key ID generated from Dashboard → Settings → API Keys
> >     data-amount="29935" // Amount is in currency subunits. Hence, 29935 refers to 29935 paise or ₹299.35.
> >     data-currency="INR"// You can accept international payments by changing the currency code. Contact our Support Team to enable International for your account
> >     data-order_id="order_CgmcjRh9ti2lP7"// Replace with the order_id generated by you in the backend.
> >     data-buttontext="Pay with Razorpay"
> >     data-name="Acme Corp"
> >     data-description="A Wild Sheep Chase is the third novel by Japanese author Haruki Murakami"
> >     data-image="https://example.com/your_logo.jpg"
> >     data-prefill.name="Gaurav Kumar"
> >     data-prefill.email="gaurav.kumar@example.com"
> >     data-theme.color="#F37254"
> > ></script>
> > <input type="hidden" custom="Hidden Element" name="hidden"/>
> > </form>
> > ```
>
> > [accordion] 2.2 Handle Payment Success and Failure
> >
> > The way the payment success and failure scenarios are handled depends on the [Checkout Sample Code](#2-1-code-to-add-pay-button) you used in the previous step.
> >
> > > [tab] Payment Success
> > >
> > > #### On Payment Success
> > >
> > > Razorpay makes a POST call to the callback URL with the **razorpay\_payment\_id**, **razorpay\_order\_id** and **razorpay\_signature** in the response object of the successful payment. Only successful authorisations are auto-submitted.
> >
> > > [tab] Payment Failure
> > >
> > > #### On Payment Failure
> > >
> > > In case of failed payments, the checkout is displayed again to facilitate payment retry.
>
> > [accordion] 2.3 Checkout Options
> >
> > `data-key` *mandatory*
> > : `string` API Key ID generated from the Razorpay Dashboard.
> >
> > `data-amount` *mandatory*
> > : `integer` The amount to be paid by the customer in cents. For example, if the amount is ₹500, enter `50000`.
> >
> > `data-currency` *mandatory*
> > : `string` The currency in which the payment should be made by the customer. See the [list of supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies)
> >
> > `data-order_id` *mandatory*
> > : `string` Unique identifier of the Order generated in [Step 1: Create an Order in your Server](#1-create-an-order-in-server).
> >
> > `data-buttontext` *mandatory*
> > : `string` The text you want to display on the button. For example, `Buy Now!`.
> >
> > `data-name` *mandatory*
> > : `string` Your Business/Enterprise name shown on the Checkout form. For example, **Acme Corp**.
> >
> > `data-description` *optional*
> > : `string` Description of the purchase item shown on the Checkout form. It should start with an alphanumeric character.
> >
> > `data-image` *mandatory*
> > : `string` Link to an image (usually your business logo) shown on the Checkout form. Can also be a **base64** string if you are not loading the image from a network.
> >
> > `data-prefill.name` *optional*
> > : `string` Cardholder's name to be pre-filled when the Checkout opens.
> >
> > `data-prefill.email` *optional*
> > : `string` Customer's email to be pre-filled when the Checkout opens.
> >
> > `data-prefill.contact` *optional*
> > : `string` Customer's phone number to be pre-filled when the Checkout opens.
> >
> > `data-theme.color` *optional*
> > : `string` Brand color to alter the appearance of Checkout form. For example, `#F37254`.
> >
> > Know more about the complete [list of available Checkout options](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/integration-steps.md#2-3-checkout-options).

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
>
> Here are the links to our [SDKs](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard.md#client-libraries) for the supported platforms.

> [accordion] 6 Verify Payment Status
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > On the Razorpay Dashboard, ensure that the payment status is `captured`. Refer to the payment capture settings page to know how to [capture payments automatically](https://razorpay.com/docs/payments/payments/capture-settings.md).
>
> > [accordion] You can track the payment status in three ways:
> >
> > > [tab] Verify Status from Dashboard
> > >
> > > To verify the payment status from the Razorpay Dashboard:
> > >
> > > 1. Log in to the Razorpay Dashboard and navigate to **Transactions** → **Payments**.
> > > 2. Check if a **Payment Id** has been generated and note the status. In case of a successful payment, the status is marked as **Captured**.
> > >
> > > ![Payment details on Dashboard](https://razorpay.com/docs/build/browser/assets/images/testpayment.jpg)
> >
> > > [tab] Subscribe to Webhook Events
> > >
> > > You can use Razorpay webhooks to configure and receive notifications when a specific event occurs. When one of these events is triggered, we send an HTTP POST payload in JSON to the webhook's configured URL. Know how to [set up webhooks.](https://razorpay.com/docs/webhooks/setup-edit-payments.md)
> > >
> > > #### Example
> > >
> > > If you have subscribed to the `order.paid` webhook event, you will receive a notification every time a customer pays you for an order.
> >
> > > [tab] Poll APIs
> > >
> > > [Poll Payment APIs](https://razorpay.com/docs/api/payments/fetch-all-payments.md) to check the payment status.

## 2. Test Integration

After the integration is complete, a **Pay** button appears on your webpage/app.

![Test integration on your webpage/app](https://razorpay.com/docs/build/browser/assets/images/test-int.gif)

Click the button and make a test transaction to ensure the integration is working as expected. You can start accepting actual payments from your customers once the test transaction is successful.

> [!WARNING]
>
> **Watch Out!**
>
> This is a mock payment page that uses your test API keys, test card and payment details.
>
> * Ensure you have entered only your [Test Mode API keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys) in the Checkout code.
> * Test mode features a mock bank page with **Success** and **Failure** buttons to replicate the live payment experience.
> * No real money is deducted due to the usage of test API keys. This is a simulated transaction.

Following are all the payment modes that the customer can use to complete the payment on the Checkout. Some of them are available by default, while others may require approval from us. Raise a request from the Dashboard to enable such payment methods.

| Payment Method | Code | Availability |
| - | - | - |
| [Debit Card](https://razorpay.com/docs/payments/payment-methods/cards.md) | `debit` | ✓ |
| [Credit Card](https://razorpay.com/docs/payments/payment-methods/cards.md) | `credit` | ✓ |
| [Netbanking](https://razorpay.com/docs/payments/payment-methods/netbanking.md) | `netbanking` | ✓ |
| [UPI](https://razorpay.com/docs/payments/payment-methods/upi.md) | `upi` | ✓ |
| EMI - [Credit Card EMI](https://razorpay.com/docs/payments/payment-methods/emi/credit-card-emi.md), [Debit Card EMI](https://razorpay.com/docs/payments/payment-methods/emi/debit-card-emi.md) and [No Cost EMI](https://razorpay.com/docs/payments/payment-methods/emi/no-cost-emi.md) | `emi` | ✓ |
| [Wallet](https://razorpay.com/docs/payments/payment-methods/wallets.md) | `wallet` | ✓ |
| [Cardless EMI](https://razorpay.com/docs/payments/payment-methods/emi/cardless-emi.md) | `cardless_emi` | Requires [Approval](https://razorpay.com/support). |
| [Bank Transfer](https://razorpay.com/docs/payments/payment-methods/bank-transfer.md) | `bank_transfer` | Requires [Approval](https://razorpay.com/support) and Integration. |
| [Emandate](https://razorpay.com/docs/payments/recurring-payments/emandate/integrate.md) | `emandate` | Requires [Approval](https://razorpay.com/support) and Integration. |
| [Pay Later](https://razorpay.com/docs/payments/payment-methods/pay-later.md) | `paylater` | Requires [Approval](https://razorpay.com/support). |

You can make test payments using one of the payment methods configured at the Checkout.

> [accordion] Netbanking
>
> You can select any of the listed banks. After choosing a bank, Razorpay will redirect to a mock page where you can make the payment `success` or a `failure`. Since this is Test Mode, we will not redirect you to the bank login portals.
>
> Check the list of [supported banks](https://razorpay.com/docs/payments/payment-methods/netbanking.md#supported-banks).

> [accordion] UPI
>
> You can enter one of the following UPI IDs:
>
> * `success@razorpay`: To make the payment successful.
> * `failure@razorpay`: To fail the payment.
>
> Check the list of [supported UPI flows](https://razorpay.com/docs/payments/payment-methods/upi.md).
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > You can use **Test Mode** to test UPI payments, and **Live Mode** for UPI Intent and QR payments.

> [accordion] Cards
>
> You can use the following test cards to test transactions for your integration in Test Mode.
>
> ### Domestic Cards
>
> Use the following test cards for Indian payments:
>
> | Network | Card Number | CVV & Expiry Date |
> | - | - | - |
> | Visa | 4100 2800 0000 1007 | Use a random CVV and any future date ^^^^^ |
> | Mastercard | 5500 6700 0000 1002 | |
> | RuPay | 6527 6589 0000 1005 | |
> | Diners | 3608 280009 1007 | |
> | Amex | 3402 560004 01007 | |
>
> #### Error Scenarios
>
> Use these test cards to simulate payment errors. See the [complete list](https://razorpay.com/docs/payments/payments/test-card-details.md#error-scenarios) of error test cards with detailed scenarios.
> Check the following lists:
>
> * [Supported Card Networks](https://razorpay.com/docs/payments/payment-methods/cards.md).
> * [Cards Error Codes](https://razorpay.com/docs/errors/payments/cards.md).
>
> ### International Cards
>
> Use the following test cards to test international payments. Use any valid expiration date in the future in the MM/YY format and any random CVV to create a successful payment.
>
> | Card Network | Card Number | CVV & Expiry Date |
> | - | - | - |
> | Mastercard | 5555 5555 5555 4444 5105 1051 0510 5100 5104 0600 0000 0008 | Use a random CVV and any future date ^^ |
> | Visa | 4012 8888 8888 1881 | |
>
> Check the list of [supported card networks](https://razorpay.com/docs/payments/payment-methods/cards.md).

> [accordion] Wallet
>
> You can select any of the listed wallets. After choosing a wallet, Razorpay will redirect to a mock page where you can make the payment `success` or a `failure`. Since this is Test Mode, we will not redirect you to the wallet login portals.
>
> Check the list of [supported wallets](https://razorpay.com/docs/payments/payment-methods/wallets.md#supported-wallets).

## 3. Go-live Checklist

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
> > * You can track the payment status using our [Fetch a Payment API](https://razorpay.com/docs/api/payments/fetch-with-id.md) or webhooks.
>
> > [tab] Auto-capture Payments (Recommended)
> >
> > Authorized payments can be automatically captured. You can auto-capture all payments [using global settings](https://razorpay.com/docs/payments/payments/capture-settings.md#auto-capture-all-payments) on the Razorpay Dashboard. Know more about [capture settings for payments](https://razorpay.com/docs/payments/payments/capture-settings.md).
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > Payment capture settings work only if you have integrated with Orders API on your server side. Know more about the [Orders API](https://razorpay.com/docs/api/orders/create.md).
>
> > [tab] Manually Capture Payments
> >
> > Each authorized payment can also be captured individually. You can manually capture payments using [Payment Capture API](https://razorpay.com/docs/api/payments/capture.md) or [Dashboard](https://razorpay.com/docs/payments/payments/dashboard.md#manually-capture-payments). Know more about [capture settings for payments](https://razorpay.com/docs/payments/payments/capture-settings.md).

> [accordion] 3 Set Up Webhooks
>
> Ensure you have [set up webhooks](https://razorpay.com/docs/webhooks/setup-edit-payments.md) in the live mode and configured the events for which you want to receive notifications.
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
> > * If a critical user-facing flow requires instant status, but the webhook notification has not arrived within the time mandated by your business needs, perform an immediate API Fetch call ([Payments](https://razorpay.com/docs/api/payments/fetch-with-id.md), [Orders](https://razorpay.com/docs/api/orders/fetch-with-id.md) and [Refunds](https://razorpay.com/docs/api/refunds/fetch-specific-refund-payment.md)) to verify the status.
