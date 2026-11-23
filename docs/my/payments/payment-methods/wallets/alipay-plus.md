> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Alipay+

> Accept payments from overseas customers paying with wallets such as GCash, DANA, TrueMoney and Alipay on Razorpay Curlec Checkout.

Available in
🇲🇾 Malaysia

Alipay+ lets your Malaysian business accept payments from customers paying with an overseas e-wallet. Your customer pays in their wallet's currency, Alipay+ handles the currency conversion, and you are settled in Malaysian ringgit, net of fees.

One integration gives you seven wallets under a single block at checkout. You choose which of them to offer — each wallet is enabled separately.

> [!NOTE]
>
> **Payment Method Enablement**
>
> Alipay+ is not enabled by default. Tell your account manager or our [Support team](https://curlec.com/support/) which wallets you want and your agreed rate, and we will enable them for you. Before we switch it on, we register your business with Alipay+, so enablement is not instant. You need no agreement of your own with Alipay+ or with any individual wallet.

## Supported Wallets

| Wallet | Country or Region |
| - | - |
| GCash | Philippines |
| DANA | Indonesia |
| TrueMoney | Thailand |
| Alipay | China |
| AlipayHK | Hong Kong |
| Kakao Pay | South Korea |
| Rabbit LINE Pay | Thailand |

Alipay+ is for overseas customers only. To accept payments from Malaysian e-wallets such as Touch 'n Go, Boost, MCash or GrabPay, see [Wallets](https://razorpay.com/docs/my/payments/payment-methods/wallets).

## How Alipay+ Works

1. The Alipay+ block appears at your checkout, surfacing wallets based on your customer's geography. The customer picks one.
2. Alipay+ hosts the approval — in the wallet's cashier on web, or in the wallet app on mobile.
3. The customer has **12 minutes** to complete the payment. After that the payment is cancelled and the customer starts a fresh one.
4. Alipay+ converts the amount and you are settled in Malaysian ringgit, net of fees.

You do not need to change your integration or write any code. Once Alipay+ is enabled, the block appears at your checkout on its own. When a new wallet joins Alipay+, it appears at your checkout without a release from you.

## Integrate on S2S

If you accept payments through our [S2S API](https://razorpay.com/docs/my/payments/payment-gateway/s2s-integration.md), Alipay+ is available on S2S on request. Contact your account manager or our [Support team](https://curlec.com/support/) to have it enabled. You then create a payment with the Alipay+ wallet code and redirect your customer to approve it. Follow the [Alipay+ S2S Integration](https://razorpay.com/docs/my/payments/payment-methods/wallets/alipay-plus/s2s-integration.md) guide.

## Frequently Asked Questions

> [accordion] Do I have to offer all seven wallets?
>
> No. Only the wallets you agreed with us are switched on and appear at your checkout.

> [accordion] What currency does my customer pay in, and what do I receive?
>
> Your customer pays in their wallet's currency. You receive Malaysian ringgit, net of fees, like any other payment on your account.

> [accordion] Can I refund an Alipay+ payment?
>
> Yes, in full or in part.

> [accordion] Will my customers be taken into their wallet app?
>
> On web, customers see the Alipay+ payment page. On mobile they may also be shown the payment page in a browser rather than being taken straight into the app. The payment works either way.

> [accordion] Can I test Alipay+ before going live?
>
> A test mode flow is not available for Alipay+ today. Contact our [Support team](https://curlec.com/support/) and we will confirm what is possible for your account.

> [accordion] Can I take recurring payments or subscriptions with Alipay+?
>
> No. Alipay+ is for one-time payments only.

### Related Information

* [Alipay+ S2S Integration](https://razorpay.com/docs/my/payments/payment-methods/wallets/alipay-plus/s2s-integration.md)
* [About Wallets](https://razorpay.com/docs/my/payments/payment-methods/wallets)
* [About Payment Methods](https://razorpay.com/docs/my/payments/payment-methods)
