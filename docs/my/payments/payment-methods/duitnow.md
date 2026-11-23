> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# DuitNow

> Accept real-time payments from Malaysian bank accounts and e-wallets with DuitNow.

Available in
🇲🇾 Malaysia

DuitNow is Malaysia's national real-time payment network, run by PayNet. Customers pay straight from their bank account or e-wallet, and the payment confirms in seconds. Razorpay Curlec connects to PayNet directly, so you do not need a separate agreement.

## Ways to Accept DuitNow

| Option | How the customer pays | Works best on | Status |
| - | - | - | - |
| [DuitNow QR](https://razorpay.com/docs/my/payments/payment-methods/duitnow/qr.md) | Scans a QR code shown at checkout with any Malaysian banking or e-wallet app. | Desktop | Live |
| [DuitNow Pay](https://razorpay.com/docs/my/payments/payment-methods/duitnow/pay.md) | Selects their bank and approves the payment on the bank's page or app. | Desktop and Mobile | Early access |

## What Both Have in Common

* Both accept Malaysian ringgit (MYR) only, for one-time payments. Recurring payments are not supported.
* In the API, webhooks and reports, both use the method `duitnow`. The `duitnow.flow` value tells them apart: `qr` for DuitNow QR and `online_banking` for DuitNow Pay.
* DuitNow QR is available on Standard Checkout, Payment Links and the [S2S API](https://razorpay.com/docs/my/payments/payment-gateway/s2s-integration/json/v2/build-integration/duitnow-qr.md).
* DuitNow Pay is available on Standard Checkout, Payment Links and the [S2S API](https://razorpay.com/docs/my/payments/payment-gateway/s2s-integration/json/v2/build-integration/duitnow-pay.md).
* Razorpay Curlec enables DuitNow on your account. Contact your account manager or raise a request with our [Support team](https://curlec.com/support/). For DuitNow Pay, Razorpay Curlec also registers your business with PayNet.

### Related Information

* [DuitNow QR](https://razorpay.com/docs/my/payments/payment-methods/duitnow/qr.md)
* [DuitNow Pay](https://razorpay.com/docs/my/payments/payment-methods/duitnow/pay.md)
* [About Payment Methods](https://razorpay.com/docs/my/payments/payment-methods)
