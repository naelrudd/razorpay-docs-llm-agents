> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Callback URL

> Reuse the web integration to process the payments.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

If you reuse your web integration of Razorpay Checkout inside a web view on Android or iOS, the checkout form may not open. Issues like this are handled in our [Android SDK](https://razorpay.com/docs/sg/payments/payment-gateway/android-integration/standard.md) and [iOS SDK](https://razorpay.com/docs/sg/payments/payment-gateway/ios-integration/standard.md), with the SDKs being the preferred method of integration.

> [!WARNING]
>
> **Callback URL is not the same as a Webhook URL**
>
> The callback URL is a Checkout option for WebView and redirect flows. It receives the payment result synchronously after the customer pays.
>
> A webhook URL is a server endpoint you configure on the Razorpay Dashboard to receive asynchronous event notifications (like `order.paid` or `payment.failed`). If you are looking to track payment status on your server after the customer pays, use webhooks — not `callback_url`.

If you want to reuse the web integration for any reason, you can pass the following `callback_url` along with other [checkout options](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/integration-steps.md#2-3-checkout-options) to process the desired payment:

```javascript JavaScript theme={null}
var options = {
  ... // existing options
  callback_url: 'https://your-server/callback_url',
  redirect: true
}
```

`callback_url` needs to accept incoming `POST` requests. For a successful payment, the callback URL will have `razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature` as the request parameters.

For failed payments, the request parameter are explained in the table below:

`error`
: `object` The error object.

`code`
: `string` Type of the error.

`description`
: `string` Descriptive text about the error.

`field`
: `string` Name of the parameter in the API request that caused the error.

> [!NOTE]
>
> **Handy Tips**
>
> You can set query parameters with `callback_url`, to map it with entities at your side. For example, following is a valid callback URL: [https://your-site.com/callback?cart\_id=12345](https://your-site.com/callback?cart_id=12345)

## FAQs

> [accordion] Is the handler function not supported in WebView?
>
> The handler function is not supported in WebView environments due to the inherent limitations of WebView in executing certain JavaScript functions.

> [accordion] What are all the field names posted to the callback page, and can I add custom fields?
>
> Razorpay posts only three fields to the callback page: `razorpay_payment_id`, `razorpay_order_id`, and `razorpay_signature`. Custom fields cannot be added to the callback response.
