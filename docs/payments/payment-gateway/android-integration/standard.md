> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Android Standard Checkout Prerequisites

> Check the prerequisites before you integrate with Razorpay Android Standard Checkout.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

> [card] [Android Standard SDK Changelog](https://razorpay.com/docs/payments/changelog.md#mobile-sdks)
>
> Discover new features, updates and deprecations related to Razorpay Android Standard SDK (since Jan 2024).

> [card] [Troubleshooting & FAQs](https://razorpay.com/docs/payments/payment-gateway/android-integration/standard/troubleshooting-faqs.md)
>
> Troubleshoot common error scenarios and find answers to frequently asked questions about Android Standard integration.

You can use Razorpay Standard SDK to integrate the Razorpay Payment Gateway with your Android Application.

> [!NOTE]
>
> **Handy Tips**
>
> * Starting from version 1.6.22, the Android Standard SDK includes codes in **Kotlin**. Please add the Kotlin library to your project.
>
> * Due to the [changes](https://support.google.com/googleplay/android-developer/answer/9047303) in Google Play Developer policy, we have removed auto-read SMS feature from Razorpay Android Standard SDK versions 1.5.1 and higher.
>
>   However, if your Android app already has permission to read SMS, then Razorpay auto-reads it.
>
> * Upgrade to the latest version available on the [Maven Repository](https://mvnrepository.com/artifact/com.razorpay/checkout).
>
> * According to the PCI regulations, payment processing is not allowed on TLS v1. Hence, if the device does not have TLS v1.1 or v1.2, the SDK will throw an error in the `onPaymentError` method. Check the [TLS versions](https://developer.android.com/reference/javax/net/ssl/SSLSocket#default-configuration-for-different-android-versions).
>
> * If you are using SDK version below 1.6.15, you need to make [changes to your Android `Manifest.xml` file](https://razorpay.com/docs/payments/payment-gateway/android-integration/standard/troubleshooting-faqs).

> [!TIP]
>
> **Update SDK**
>
> Check your [current SDK version](https://razorpay.com/docs/payments/payment-gateway/android-integration/standard/troubleshooting-faqs.md#how-can-i-check-the-razorpay-android-standard-sdk-version). If it is outdated, please [update the SDK](https://razorpay.com/docs/payments/payment-gateway/android-integration/standard/troubleshooting-faqs.md#how-can-i-update-the-razorpay-android-standard-sdk-version) manually to ensure uninterrupted settlements of your funds.
>
> From version 1.6.40 onwards, the latest version is automatically updated, eliminating the need for manual updates.

## Integration Steps

**Before you proceed:**

<ul>
  <li>Create a [Razorpay account](https://dashboard.razorpay.com/signup). </li>
  <li>Generate the [API Keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys) from the Dashboard. To go live with the integration and start accepting real payments, generate Live Mode API Keys and replace them in the integration.</li>
  <li>Know about the [Payment Flow](https://razorpay.com/docs/payments/payment-gateway/how-it-works.md).</li>
</ul>

Follow these integration steps:

> [card] [1. Build Integration](https://razorpay.com/docs/payments/payment-gateway/android-integration/standard/integration-steps.md#1-build-integration)
>
> Integrate Android Standard SDK.

> [card] [2. Test Integration](https://razorpay.com/docs/payments/payment-gateway/android-integration/standard/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-live Checklist](https://razorpay.com/docs/payments/payment-gateway/android-integration/standard/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

> [card] [Sample App](https://github.com/razorpay/razorpay-android-sample-app/)
>
> Check the sample app to integrate on GitHub.

### Related Information

[Address Verification System](https://razorpay.com/docs/payments/international-payments/address-verification-system.md)
