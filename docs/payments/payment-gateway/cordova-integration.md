> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Cordova Standard SDK Prerequisites

> Check the prerequisites before you integrate with Razorpay Cordova Standard SDK.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

> [card] [Cordova Standard SDK Changelog](https://razorpay.com/docs/payments/changelog.md#mobile-sdks)
>
> Discover new features, updates and deprecations related to the Razorpay Cordova Standard SDK (since Jan 2024).

> [card] [Troubleshooting & FAQs](https://razorpay.com/docs/payments/payment-gateway/cordova-integration/troubleshooting-faqs.md)
>
> Troubleshoot common error scenarios and find answers to frequently asked questions about Cordova Standard integration.

You can use Razorpay Standard SDK to integrate the Razorpay Payment Gateway with your Cordova Application to accept payments. The Razorpay Cordova plugin acts as a wrapper around the Razorpay Standard SDK to build a dynamic and responsive Checkout interface for your iOS or Android application.

> [!TIP]
>
> **Update SDK**
>
> Check your current [Cordova](https://razorpay.com/docs/payments/payment-gateway/cordova-integration/troubleshooting-faqs.md#how-can-i-check-the-razorpay-cordova-standard-sdk-version) or [Iconic](https://razorpay.com/docs/payments/payment-gateway/cordova-integration/troubleshooting-faqs.md#how-can-i-check-the-razorpay-ionic-standard-sdk-version) Standard SDK version. If it is outdated, please [update the SDK](https://razorpay.com/docs/payments/payment-gateway/cordova-integration/troubleshooting-faqs.md#how-can-i-update-the-razorpay-cordova-and-ionic-standard-sdk-version) to ensure uninterrupted settlements of your funds.

## Guidelines

* Add the integration code snippet after the `deviceready` event.

* On browser, change the [Content Security Policy](https://content-security-policy.com/) to whitelist the `razorpay.com` domain.

```javascript theme={null}
<meta http-equiv="Content-Security-Policy" content="default-src 'self' https://*.razorpay.com data: gap: https://ssl.gstatic.com 'unsafe-eval'; style-src 'self' 'unsafe-inline'; media-src *"/>
```

* We do not support [ionic server](https://github.com/ionic-team/ionic-cli/issues/354) at the moment because it does not support cordova browser plugins. Try using the `ionic cordova run browser` command instead.

## Integration Steps

**Before you proceed:**

<ul>
  <li>Create a [Razorpay account](https://dashboard.razorpay.com/signup). </li>
  <li>Generate the [API Keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys) from the Dashboard. To go live with the integration and start accepting real payments, generate Live Mode API Keys and replace them in the integration.</li>
  <li>Know about the [Payment Flow](https://razorpay.com/docs/payments/payment-gateway/how-it-works.md).</li>
</ul>

Follow these integration steps:

> [card] [1. Build Integration](https://razorpay.com/docs/payments/payment-gateway/cordova-integration/integration-steps.md#1-build-integration)
>
> Integrate Cordova Standard SDK.

> [card] [2. Test Integration](https://razorpay.com/docs/payments/payment-gateway/cordova-integration/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-live Checklist](https://razorpay.com/docs/payments/payment-gateway/cordova-integration/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

> [card] [Sample Code](https://github.com/razorpay/razorpay-cordova-sample-app/tree/master/)
>
> Check the sample code on GitHub to integrate.

### Related Information

[Address Verification System](https://razorpay.com/docs/payments/international-payments/address-verification-system.md)
