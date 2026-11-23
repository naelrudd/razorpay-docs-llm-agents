> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Best Practices for Standard Checkout Integration

> Best practices for a smoother Standard Checkout web integration and payment experience.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Follow the best practices for a smooth Standard Checkout web integration.

1. **Capture Payment Using Payment Capture Settings**

   You **must capture** the authorised payments for the **settlement of the payments** in your bank account. Use the [Payment Capture Setting](https://razorpay.com/docs/my/payments/payments/capture-settings.md) to configure the capture settings at an account level via the Dashboard.

2. **Integrate Orders API**

   Orders bind multiple payment attempts for a single order. This helps to **prevent multiple payments**. [Integrate with Orders API](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/integration-steps.md#1-create-an-order-in-server) on your server-side and pass the `order_id` to Checkout.

3. **Verify Signature to Avoid Data Tampering**

   This is a mandatory step to confirm the authenticity of the details returned to the Checkout form for successful payments. Know how to [verify payment signature](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/integration-steps.md#5-verify-payment-signature).

4. **Check Payment/Order Status before Providing Services**

   Check the payment/order status, that is if the payment's status is `captured` and the order's status is `paid` before proving the services to the customers.

   * [Fetch All Payments for an Order API](https://razorpay.com/docs/my/api/orders/fetch-payments.md)
   * [Fetch Status of a Payment using Payment id API](https://razorpay.com/docs/my/api/payments/fetch-with-id.md)
   * [Fetch Status of an Order using Order id API](https://razorpay.com/docs/my/api/orders/fetch-with-id.md)

5. **Implement Webhooks**

   Implement webhooks or the query API to avoid callback failure (drop-offs could be due to connectivity or network failure) and to verify the payment details via an S2S call. Know more about [Webhooks](https://razorpay.com/docs/my/webhooks/setup-edit-payments.md). You should enable the following webhooks:

   * `payment.captured`
   * `payment.failed`
   * `order.paid`

6. **Implement Callback URL**

   Sites like Instagram, Facebook Messenger, Opera and UC browser do not support i-frame. You should implement [callback URL](https://razorpay.com/docs/my/payments/payment-gateway/callback-url.md) if your customers use any of these for making payments.
