> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# iOS Standard Checkout Prerequisites

> Check the prerequisites before you integrate with Razorpay Curlec iOS Standard Checkout.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

> [card] [Troubleshooting & FAQs](https://razorpay.com/docs/my/payments/payment-gateway/ios-integration/standard/troubleshooting-faqs.md)
>
> Troubleshoot common error scenarios and find answers to frequently asked questions about iOS Standard integration.

Integrate the Razorpay Curlec Payment Gateway with your iOS app and start accepting payments from your customers.

> [!WARNING]
>
> **Watch Out!**
>
> * You cannot use an external payment gateway to accept payments by selling digital products or content. You must use Apple’s In-App Purchase to avoid app rejection. Know more about the list of restricted payment modes.
> * iOS integration for Touch'n Go wallet is currently unavailable. We will be adding support for it soon.

> [!TIP]
>
> **Update SDK**
>
> Check your [current SDK version](https://razorpay.com/docs/my/payments/payment-gateway/ios-integration/standard/troubleshooting-faqs.md#how-can-i-check-the-razorpay-curlec-ios-standard-sdk-version). If it is outdated, please [update the SDK](https://razorpay.com/docs/my/payments/payment-gateway/ios-integration/standard/troubleshooting-faqs.md#how-can-i-update-the-razorpay-curlec-ios-standard-sdk-version) to ensure uninterrupted settlements of your funds.

## Integration Steps

**Before you proceed:**

<ul>
  <li> Create a [Curlec account](https://dashboard.curlec.com/?screen=sign_in\&next=app%2Fdashboard).</li>
  <li>Generate the [API Keys](https://razorpay.com/docs/my/payments/dashboard/account-settings/api-keys.md#generate-api-keys) from the Dashboard. To go live with the integration and start accepting real payments, generate Live Mode API Keys and replace them in the integration.</li>
  <li>Know about the [Payment Flow](https://razorpay.com/docs/my/payments/payment-gateway/how-it-works.md).</li>
</ul>

Follow these integration steps:

> [card] [1. Build Integration](https://razorpay.com/docs/my/payments/payment-gateway/ios-integration/standard/integration-steps.md#1-build-integration)
>
> Integrate iOS Standard SDK.

> [card] [2. Test Integration](https://razorpay.com/docs/my/payments/payment-gateway/ios-integration/standard/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-live Checklist](https://razorpay.com/docs/my/payments/payment-gateway/ios-integration/standard/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

> [card] [Sample App](https://github.com/razorpay/razorpay-ios-sample-app)
>
> Check the sample app to integrate on GitHub.
