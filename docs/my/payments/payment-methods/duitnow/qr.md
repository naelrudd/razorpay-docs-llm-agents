> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# DuitNow QR

> Accept payments from any Malaysian banking or e-wallet app with DuitNow QR.

Available in
🇲🇾 Malaysia

Using DuitNow QR, your customers can pay by scanning a QR code with their banking app or e-wallet. DuitNow QR is Malaysia's national QR standard, run by PayNet and supported by all major banks and e-wallets. Razorpay Curlec connects to PayNet directly, so there is no separate sign-up.

## Advantages

1. **One QR, Every App**: Customers pay with Maybank MAE, CIMB, Public Bank, RHB, Touch'n Go eWallet, GrabPay, Boost and 30+ other Malaysian apps.

2. **Fast on Desktop**: No bank login or card details. The customer scans with their phone and approves.

3. **Real Time**: Payments confirm in seconds and settle on your usual settlement cycle.

4. **No Integration Change**: Works on Standard Checkout, hosted checkout, plugins and Payment Links once enabled. On the S2S API, you get the QR data and show it on your own page, kiosk or app.

## Enable DuitNow QR

DuitNow QR is enabled by Razorpay Curlec. Contact your account manager or raise a request with our [Support team](https://curlec.com/support/).

## Payment Flow

Given below is the payment flow for DuitNow QR at Razorpay Curlec checkout:

> [tab] Desktop
>
> 1. The customer selects **DuitNow QR** at checkout.
>
>    ![Checkout payment options with DuitNow QR first in the method list and its QR code open](https://mintcdn.com/razorpay-881012b3/63jl6MfxYscP_bvi/static/my/docs-home/assets/duitnow-qr-desktop-method-list.png?fit=max\&auto=format\&n=63jl6MfxYscP_bvi\&q=85\&s=a418529b59b35f6a1f4a44677fbf2df6)
> 2. A QR code with the amount filled in appears, with a 10-minute timer.
>
>    ![DuitNow QR code for MYR 1 with the countdown timer](https://mintcdn.com/razorpay-881012b3/63jl6MfxYscP_bvi/static/my/docs-home/assets/duitnow-qr-desktop-qr-timer.png?fit=max\&auto=format\&n=63jl6MfxYscP_bvi\&q=85\&s=567b7dfb3ba41841b1b675fe48da492d)
> 3. The customer scans the QR code with their banking or e-wallet app and approves the payment. Checkout waits for the payment confirmation.
>
>    ![Checkout showing Waiting for payment confirmation](https://mintcdn.com/razorpay-881012b3/63jl6MfxYscP_bvi/static/my/docs-home/assets/duitnow-qr-desktop-waiting.png?fit=max\&auto=format\&n=63jl6MfxYscP_bvi\&q=85\&s=de14bbb201f54e103098b2d28e47269a)
> 4. Checkout confirms the payment and returns the customer to your website.
>
>    ![Checkout showing Payment Successful for a DuitNow payment of MYR 1](https://mintcdn.com/razorpay-881012b3/63jl6MfxYscP_bvi/static/my/docs-home/assets/duitnow-qr-desktop-success.png?fit=max\&auto=format\&n=63jl6MfxYscP_bvi\&q=85\&s=c8159fc18d8b52d66fcd7063d1bb1419)
>
> The video below shows the complete flow.
>
> <video controls muted playsInline preload="metadata" aria-label="A RM 1.00 order on a demo store: the customer selects DuitNow QR at Razorpay Curlec Checkout, a Malaysia National QR is shown with a 10-minute timer, the customer pays from their banking app, and Checkout confirms the payment and shows Payment Successful.">
>   <source src="https://mintcdn.com/razorpay-881012b3/63jl6MfxYscP_bvi/static/my/docs-home/assets/duitnow-qr-checkout-demo.mp4?fit=max&auto=format&n=63jl6MfxYscP_bvi&q=85&s=f9da2b7c1420bbee0ccbac93a4877f8a" type="video/mp4" />
> </video>

> [tab] Mobile
>
> 1. The customer selects **DuitNow QR** at checkout and taps **Download QR**.
>
>    ![Mobile checkout showing the DuitNow QR code, the steps to pay and the Download QR button](https://mintcdn.com/razorpay-881012b3/63jl6MfxYscP_bvi/static/my/docs-home/assets/duitnow-qr-mobile-download.png?fit=max\&auto=format\&n=63jl6MfxYscP_bvi\&q=85\&s=f6dc111599eaea9013efd002a1d6b032)
> 2. They open their banking or e-wallet app and pay using the saved QR image.
> 3. They return to your website or app, where the payment status is shown.

## Supported Products

| Product | Supported |
| - | - |
| Standard Checkout (web and mobile web) | Yes |
| Hosted checkout and plugins (Shopify, WooCommerce) | Yes |
| Payment Links | Yes |
| S2S API | Yes. See [S2S integration](https://razorpay.com/docs/my/payments/payment-gateway/s2s-integration/json/v2/build-integration/duitnow-qr.md). |
| Custom Checkout | No |
| Recurring payments | No |

## Limits and Timings

| Item | Value |
| - | - |
| Minimum amount | RM 1.00 |
| Maximum amount | RM 50,000 per payment |
| Currency | MYR only |
| QR validity | 10 minutes. An expired QR fails; the customer can refresh to get a new one. |
| Refunds | Full and partial. Refunds are processed within 3 to 5 working days. |
| Test mode | Not available. Test with a live RM 1 payment and refund it. |

## Identify DuitNow QR Payments

In the API, webhooks and reports, DuitNow QR payments have the method `duitnow` and `duitnow.flow` set to `qr`.

## Frequently Asked Questions (FAQs)

> [accordion] 1. Which apps can customers use?
>
> Any Malaysian banking app or e-wallet that supports DuitNow QR, including Maybank MAE, CIMB, Public Bank, RHB, Touch'n Go eWallet, GrabPay and Boost.

> [accordion] 2. Do I need to register with PayNet?
>
> No. Razorpay Curlec handles this.

> [accordion] 3. Do I need to change my integration?
>
> Not on Standard Checkout, hosted checkout, plugins or Payment Links. On the S2S API, follow the [DuitNow QR S2S integration](https://razorpay.com/docs/my/payments/payment-gateway/s2s-integration/json/v2/build-integration/duitnow-qr.md) guide.

> [accordion] 4. How long is the QR valid?
>
> 10 minutes. After that, the payment fails and the customer can generate a new QR.

> [accordion] 5. What if the customer pays after the QR expires?
>
> The bank usually rejects the payment. If money is debited, it is refunded automatically. If it is not, contact our [Support team](https://curlec.com/support/) with the payment ID.

> [accordion] 6. How does it work on a phone?
>
> The customer downloads the QR, opens their banking or e-wallet app and pays with the saved image.

> [accordion] 7. What are the limits?
>
> RM 1.00 to RM 50,000 per payment, in MYR only.

> [accordion] 8. Can I refund a DuitNow QR payment?
>
> Yes, full or partial, from the Dashboard or API. Refunds are processed within 3 to 5 working days.

> [accordion] 9. Is there a test mode?
>
> No. Make a live RM 1 payment and refund it.

> [accordion] 10. Can I use DuitNow QR for subscriptions?
>
> No. DuitNow QR is for one-time payments only.

> [accordion] 11. Can I accept customers from outside Malaysia?
>
> No. Cross-border QR payments are not supported.

> [accordion] 12. How do I find DuitNow QR payments in reports?
>
> Filter by the method `duitnow`. The flow is `qr`.

> [accordion] 13. Can I turn DuitNow QR off?
>
> Yes. Contact your account manager or our [Support team](https://curlec.com/support/).

### Related Information

* [DuitNow](https://razorpay.com/docs/my/payments/payment-methods/duitnow)
* [DuitNow Pay](https://razorpay.com/docs/my/payments/payment-methods/duitnow/pay.md)
* [DuitNow QR S2S Integration](https://razorpay.com/docs/my/payments/payment-gateway/s2s-integration/json/v2/build-integration/duitnow-qr.md)
* [Refunds](https://razorpay.com/docs/my/payments/refunds/normal.md)
* [About Payment Methods](https://razorpay.com/docs/my/payments/payment-methods)
