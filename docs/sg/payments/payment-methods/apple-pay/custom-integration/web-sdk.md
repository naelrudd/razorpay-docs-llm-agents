> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Apple Pay Web SDK

> Integrate Apple Pay on your checkout page using the Razorpay Web SDK. Choose between the web component or headless JS integration methods.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

The Razorpay Web SDK lets you integrate Apple Pay directly on your checkout page without redirecting customers to a hosted page. You can choose between two integration approaches depending on how much control you need over the payment flow.

> [!NOTE]
>
> **Availability in Singapore**
>
> Apple Pay on Custom Checkout is available on the web, on Safari (iPhone, iPad and Mac) and Chrome (Mac). It is not yet available for native mobile app integrations, such as the iOS Custom SDK or React Native, or for businesses on the Customer Fee Bearer (CFB) model.

## Integration Methods

<linecard title="Web Component" disableScaleOnHover headingVariant="H4">
  <item label="Use if you want minimal JavaScript" href="https://razorpay.com/docs/sg/payments/payment-methods/apple-pay/custom-integration/web-sdk/web-component.md" iconName="info" headingVariant="H4">
    Drop in the `<razorpay-checkout>` tag and let the component render the Apple Pay button automatically.
  </item>
</linecard>

<linecard title="Web JS Integration" disableScaleOnHover headingVariant="H4">
  <item label="Use if you want full control" href="https://razorpay.com/docs/sg/payments/payment-methods/apple-pay/custom-integration/web-sdk/web-js-integration.md" iconName="info" headingVariant="H4">
    Use the Razorpay JS object to control the button, payment flow and event handling yourself.
  </item>
</linecard>

## Prerequisites

Before you begin, ensure you have the following:

* Apple Pay enabled on your account. Contact the [Support team](https://razorpay.com/sg/support/) to enable it.
* An existing Razorpay Custom Checkout integration.
* Cards enabled on your Razorpay account in Live Mode.
* Your API Key Id available. Know how to generate [API Keys from the Dashboard](https://razorpay.com/docs/sg/payments/dashboard/account-settings/api-keys.md#generate-api-keys).
* An HTTPS-enabled domain (TLS 1.2 or higher). Apple Pay requires a secure context and will not function over HTTP.
* Server-side capability to create orders via the Razorpay Orders API.
* Apple Pay domain verification completed for every domain your customers see at checkout.

### Related Information

* [Apple Pay Standard Checkout](https://razorpay.com/docs/sg/payments/payment-methods/apple-pay.md)
* [Apple Pay Custom Integration](https://razorpay.com/docs/sg/payments/payment-methods/apple-pay/custom-integration.md)
* [Apple Pay Web Component Integration](https://razorpay.com/docs/sg/payments/payment-methods/apple-pay/custom-integration/web-sdk/web-component.md)
