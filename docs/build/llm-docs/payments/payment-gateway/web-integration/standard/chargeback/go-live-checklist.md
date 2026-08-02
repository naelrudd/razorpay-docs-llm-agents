# 3. Go-live Checklist

Consider these steps before taking the integration live.

## Accept Live Payments

You can perform an end-to-end simulation of funds flow in the Test Mode. Once confident that the integration is working as expected, switch to the Live Mode and start accepting payments from customers. However, make sure that you **swap the Test API Key with the Live Key**.

To generate an API Key in Live Mode:

## Payment Capture

After payment is `authorized`, you need to capture it to settle the amount to your bank account as per the settlement schedule. Payments that are not captured are auto-refunded after a fixed time.

**WARN**

**Watch Out**

- You should deliver the products or services to your customers only after the payment is captured. Razorpay automatically refunds all the uncaptured payments.
- You can track the payment status using our [Fetch a Payment API](https://razorpay.com/docs/build/llm-docs/api/payments.md#fetch-a-payment) or webhooks.

  
    Authorized payments can be automatically captured. You can auto-capture all payments [using global settings](https://razorpay.com/docs/build/llm-docs/payments/payments/capture-settings.md#auto-capture-all-payments) on the Razorpay Dashboard. Know more about [capture settings for payments](https://razorpay.com/docs/build/llm-docs/payments/payments/capture-settings.md).

    
**WARN**

**Watch Out!**

Payment capture settings work only if you have integrated with Orders API on your server side. Know more about the [Orders API](https://razorpay.com/docs/build/llm-docs/api/orders/create.md).

  
  
    Each authorized payment can also be captured individually. You can manually capture payments using [Payment Capture API](https://razorpay.com/docs/build/llm-docs/api/payments.md#capture-a-payment) or [Dashboard](https://razorpay.com/docs/build/llm-docs/payments/payments/dashboard.md#manually-capture-payments). Know more about [capture settings for payments](https://razorpay.com/docs/build/llm-docs/payments/payments/capture-settings.md).
