> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# About Payment Methods

> Check the different payment methods that can be configured to accept payments from your customers using Razorpay Curlec products.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

The Razorpay Curlec Checkout offers multiple payment methods, allowing your customer the flexibility to complete the payment using the payment method of their choice. This improves user experience and allows you to offer alternate payment methods to your customer in the case of downtimes or low success rate with one of the payment methods.

For example, if you are facing downtime with FPX, the customer can complete the payment using cards or wallets.

## View Payment Methods

To view the payment methods enabled for you:

1. Log in to the Dashboard.
2. Click **Account & Settings** in the left menu.
3. Go to **Payment methods** to view the payment methods enabled for your Razorpay Curlec account.

Know more about [payment methods on the Dashboard](https://razorpay.com/docs/my/payments/dashboard/account-settings/payment-methods.md).

## Supported Payment Methods

Following are the payment modes that the customer can use to complete the payment on Standard Checkout, Payment Links, Payment Pages, Invoices and the ecommerce plugins.

| Payment Method | Code | Availability |
| - | - | - |
| Debit and Credit Cards | `card` | ✓ |
| [Apple Pay](https://razorpay.com/docs/my/payments/payment-methods/apple-pay) | — | ✓ |
| [FPX](https://razorpay.com/docs/my/payments/payment-methods/fpx) | `fpx` | ✓ |
| [DuitNow QR](https://razorpay.com/docs/my/payments/payment-methods/duitnow/qr.md) | — | Requires [approval](https://curlec.com/support/). Not available on Payment Pages or Invoices yet. |
| [DuitNow Pay](https://razorpay.com/docs/my/payments/payment-methods/duitnow/pay.md) | — | Early access. Contact your account manager. Not available on Payment Pages or Invoices yet. |
| [Wallets](https://razorpay.com/docs/my/payments/payment-methods/wallets) | `wallet` | ✓ |
| [UPI](https://razorpay.com/docs/my/payments/payment-methods/upi.md) | `upi` | ✓ |
| [Instalments](https://razorpay.com/docs/my/payments/payment-methods/instalments) | `instalment` | ✓ |
| [Pay Later (Atome)](https://razorpay.com/docs/my/payments/payment-methods/pay-later.md) | `paylater` | Requires [approval](https://curlec.com/support/). |

Codes are the values you pass in the `method` parameter at Checkout. Where a code is not listed, contact your account manager or raise a request with our [Support team](https://curlec.com/support/).

### Availability by Integration

Not every method is available on every integration.

| Payment Method | Standard Checkout | S2S | Mobile SDKs | Custom Checkout |
| - | :-: | :-: | :-: | :-: |
| Debit and Credit Cards | ✓ | ✓ | ✓ | ✓ |
| [Apple Pay](https://razorpay.com/docs/my/payments/payment-methods/apple-pay) | ✓ | ✓ | — | ✓ |
| [FPX](https://razorpay.com/docs/my/payments/payment-methods/fpx) | ✓ | ✓ | ✓ | ✓ |
| [FPX B2B maker-checker](https://razorpay.com/docs/my/payments/payment-methods/fpx/b2b-maker-checker.md) | ✓ | ✓ | ✕ | ✕ |
| [DuitNow QR](https://razorpay.com/docs/my/payments/payment-methods/duitnow/qr.md) | ✓ | ✓ | — | ✕ |
| [DuitNow Pay](https://razorpay.com/docs/my/payments/payment-methods/duitnow/pay.md) | ✓ | ✓ | ✓ | ✕ |
| [Wallets](https://razorpay.com/docs/my/payments/payment-methods/wallets) | ✓ | ✓ | ✓ | ✓ |
| [Alipay+](https://razorpay.com/docs/my/payments/payment-methods/wallets/alipay-plus.md) | ✓ | — | — | — |
| [UPI](https://razorpay.com/docs/my/payments/payment-methods/upi.md) | ✓ | ✓ | — | ✕ |
| [Instalments](https://razorpay.com/docs/my/payments/payment-methods/instalments) | ✓ | ✓ | ✕ | ✕ |
| [Pay Later (Atome)](https://razorpay.com/docs/my/payments/payment-methods/pay-later.md) | ✓ | ✓ | ✓ | ✓ |

✓ available  ·  ✕ not supported  ·  — not available yet

* **Standard Checkout** also covers Payment Links, Payment Pages, Invoices and the ecommerce plugins.
* **Apple Pay**: Custom Checkout is supported on the web through the [Apple Pay Web SDK](https://razorpay.com/docs/my/payments/payment-methods/apple-pay/custom-integration/web-sdk.md). S2S needs Apple Pay enabled for S2S on your account first.
* **Wallets**: Touch 'n Go supports app-to-app payments on recent SDK versions.
* **Pay Later**: on the mobile SDKs, customers are taken into the Atome app through a deep link.
* **DuitNow QR**: supported on Standard Checkout (web and mobile web), hosted checkout, the ecommerce plugins, Payment Links and the [S2S API](https://razorpay.com/docs/my/payments/payment-gateway/s2s-integration/json/v2/build-integration/duitnow-qr.md). It is not available on Payment Pages or Invoices yet, and recurring payments are not supported.
* **DuitNow Pay**: in early access. Supported on Standard Checkout, Payment Links, the mobile SDKs (through Standard Checkout) and the [S2S API](https://razorpay.com/docs/my/payments/payment-gateway/s2s-integration/json/v2/build-integration/duitnow-pay.md). On the mobile SDKs, the customer completes the payment on the bank's page. It is not available on Payment Pages or Invoices yet, and recurring payments are not supported.

For anything marked as not available yet, contact your account manager or raise a request with our [Support team](https://curlec.com/support/) to check the latest position.

> [!NOTE]
>
> **Additional Payment Methods**
>
> You can raise a request with our [Support team](https://curlec.com/support/) for additional payment methods or providers.

### Methods in Early Access

* [DuitNow Pay](https://razorpay.com/docs/my/payments/payment-methods/duitnow/pay.md) is available to a limited set of businesses only. Contact your account manager to check whether your business is eligible. Know more about [DuitNow](https://razorpay.com/docs/my/payments/payment-methods/duitnow).

### Related Information

* [Payment Methods on the Dashboard](https://razorpay.com/docs/my/payments/dashboard/account-settings/payment-methods.md)
* [Configure Payment Methods on Checkout](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods.md)
