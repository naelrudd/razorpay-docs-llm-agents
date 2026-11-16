> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Features

> List of features that will help you build a first-class payments experience with Razorpay Checkout.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Razorpay payment gateway comes with a range of features that helps you build a first-class payments experience.

* **OTP Auto-Read and Submit**\

  Your customers gain a faster and enhanced checkout experience with Razorpay OTP auto-submit. The system automatically reads the OTP received, with your customer’s consent, and submits it. It prevents errors and the users do not need to navigate or interact with additional elements to complete verification, making the process seamless. This is available by default on Android SDK and not available on iOS SDK.

* **Configuring Payment Methods**\

  Razorpay Standard Checkout hosts a variety of payment methods for customers to make payments. You can rearrange the order of these payment methods and display them at the Checkout to provide a highly personalised experience for your customers. Know more about [configuring payment methods](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/configure-payment-methods.md).

* **Making Email Read-only**\

  You can set the email field as read-only to ensure your customers can only view the email but can not edit it. You can allow your customers to edit this field based on your preferences. Know more about [making email read-only](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/integration-steps.md#2-3-checkout-options).

* **Prefill Customer Contact Details**\

  To improve conversion rates and reduce form-fill friction, use the prefill parameter to automatically fill in customer contact information, especially their phone number. The expected format while prefilling the phone number in the [Checkout code](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/integration-steps.md#2-2-code-to-add-pay-button) is `+ (country code)(phone number)` (Example: "contact": "+6591119111").

> [!WARNING]
>
> **Watch Out!**
>
> This feature is not applicable if you:
>
> * Do not collect customer contact details on your website before checkout.
> * Have Shopify stores.
> * Use any of the no-code apps.

* **Making Phone Number Field Optional**\

  You can hide the phone number field from the checkout page based on your preferences. You can also enable customers to proceed with the payment without providing a phone number. Refer to the [Checkout Options](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/integration-steps.md#2-3-checkout-options) table to know more about making the phone number field optional.

> [!WARNING]
>
> **Watch Out!**
>
> * To enable this feature, contact our   [Support Team](https://razorpay.com/sg/).
> * If you enable customers to proceed with the payment without providing their phone number, then the field will not appear against the payment on the Dashboard and the reports.

* **Configure Email Address Field**\

  The email address field is hidden by default on checkout if it is not pre-filled. Since email is not mandatory, this will reduce drop-offs and improve conversion rates. You can choose to hide the field, make it optional or mandatory based on your business requirement. Know how to [configure the email address field](https://razorpay.com/docs/payments/dashboard/account-settings/checkout-features.md#collect-email-address-from-customers).

* **Partial Payment Capability**\

  You can allow your customer to make partial payments at the Checkout. Know more about [partial payments](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/integration-steps.md#request-parameters).

* **Checkout Timeout**\

  You set a timeout on Checkout. After the specified time limit, the customer will not be able to use Checkout and hence the payment will terminate after the set time. Know more about [checkout timeout](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/integration-steps.md#2-3-checkout-options).

* **Downtime Communication on Checkout**\

  Downtimes updates provide an overview of various downtimes grouped across different payment methods on your [Dashboard](https://razorpay.com/docs/payments/payments/downtime-updates.md). You can view the latest status of downtimes for cards at any point in time. You can also view instrument details for downtimes such as Cards Network. Know more about the [payments downtime API](https://razorpay.com/docs/sg/api/payments/downtime.md).

> [!WARNING]
>
> **Watch Out!**
>
> We temporarily prevent customers from accessing payment instruments, which are bound to fail on checkout. For example, if all payments made via cards are bound to fail, we show the option in a disabled state on checkout until it recovers. However, they can select an alternative instrument that is more likely to work to complete the payment successfully.

* **Customer Fee Bearer**\

  You can pass the Razorpay transaction fee on credit card payments to your customers. Your customers see the fee as an Admin Fee at checkout and you receive the full order amount. Apple Pay and Google Pay are not available while CFB is enabled. Know more about [Customer Fee Bearer](https://razorpay.com/docs/sg/payments/payment-gateway/customer-fee-bearer.md).

* **Checkout Retry Flow**\

  By default, Razorpay provides transparent, contextual, and actionable suggestions to customers at the point of payment failure on checkout. For example, if a customer's payment via Card fails on Razorpay checkout, the system intelligently suggests the next best payment option based on the reason for the failure and the customer's past transaction history. This reduces customer drop-offs and improves the overall payment experience.

### Related Information

* [Payment Gateway](https://razorpay.com/docs/sg/payments/payment-gateway)
* [How Payment Gateway Works](https://razorpay.com/docs/sg/payments/payment-gateway/how-it-works.md)
* [Payment Methods](https://razorpay.com/docs/sg/payments/payment-methods)
