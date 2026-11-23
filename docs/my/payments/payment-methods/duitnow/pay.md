> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# DuitNow Pay

> Accept payments straight from your customers' Malaysian bank accounts with DuitNow Pay.

Available in
🇲🇾 Malaysia

DuitNow Pay lets your customers pay straight from their Malaysian bank account. The customer picks their bank at checkout, approves the payment on their bank's page or app, and comes back to your website. DuitNow is Malaysia's national real-time payment network, run by PayNet, so payments confirm in seconds.

To let customers pay by scanning a QR code, see [DuitNow QR](https://razorpay.com/docs/my/payments/payment-methods/duitnow/qr.md).

> [!WARNING]
>
> **Watch Out!**
>
> DuitNow Pay is in early access. Your business must be registered with PayNet before you can accept it. Razorpay Curlec does the registration for you. Contact your account manager to ask for DuitNow Pay.

## Advantages

1. **Pay From the Bank**: No card details. Customers approve on their own bank's page or app.

2. **Real Time**: Payments confirm in seconds and settle on your usual settlement cycle.

3. **Familiar Bank List**: Customers see the major Malaysian banks they already use for online banking.

## Payment Flow

Given below is the payment flow for DuitNow Pay at Razorpay Curlec checkout:

1. The customer selects **DuitNow Pay** at checkout.

   ![Checkout payment options with DuitNow Pay selected and the list of banks](https://mintcdn.com/razorpay-881012b3/0HVPm4LHtcRuLYJ0/static/my/docs-home/assets/duitnow-pay-desktop-bank-list.png?fit=max\&auto=format\&n=0HVPm4LHtcRuLYJ0\&q=85\&s=e87873af9074f7bee3e2088d9239927d)
2. They search for and pick their bank, and are taken to the bank's page.

   ![DuitNow Pay bank search with HSBC in the search results](https://mintcdn.com/razorpay-881012b3/0HVPm4LHtcRuLYJ0/static/my/docs-home/assets/duitnow-pay-desktop-bank-search.png?fit=max\&auto=format\&n=0HVPm4LHtcRuLYJ0\&q=85\&s=3da259df5566d01df83e449fd1841238)

   ![Checkout showing Processing your payment before the customer goes to their bank](https://mintcdn.com/razorpay-881012b3/63jl6MfxYscP_bvi/static/my/docs-home/assets/duitnow-pay-desktop-processing.png?fit=max\&auto=format\&n=63jl6MfxYscP_bvi\&q=85\&s=4177b8ee11458ff9d29340cba6f1f3b2)
3. They log in and approve the payment.
4. They return to your website or app, and Razorpay Curlec confirms the payment.

The video below shows the complete flow.

<video controls muted playsInline preload="metadata" aria-label="A RM 1.00 order on a demo store: the customer selects DuitNow Pay at Razorpay Curlec Checkout, picks HSBC, logs in and approves the payment on the bank's page, and is returned to the store's callback URL.">
  <source src="https://mintcdn.com/razorpay-881012b3/0HVPm4LHtcRuLYJ0/static/my/docs-home/assets/duitnow-pay-checkout-demo.mp4?fit=max&auto=format&n=0HVPm4LHtcRuLYJ0&q=85&s=10269d41706a04ac77e4820ad6cb659a" type="video/mp4" />
</video>

## Standard Checkout

You do not need to change your Standard Checkout integration. Once DuitNow Pay is enabled on your account, it appears at checkout.

* **Pass a callback URL**: DuitNow Pay always sends the customer to their bank's page. Set `redirect` to `true` and pass `callback_url` in your checkout options, as you do for FPX, so the customer comes back to your website after paying. Without it, the customer can end up on a Razorpay Curlec page that does not return them to you, and your `handler` function is not called.
* **Success**: Razorpay Curlec submits `razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature` to your callback URL. [Verify the signature](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/integration-steps.md#1-build-integration) as for any other payment.
* **Failure**: The callback carries [error fields](https://razorpay.com/docs/my/errors) and no signature. Treat any callback without a valid signature as a failed payment.
* **Webhooks**: Subscribe to `payment.captured` and `payment.failed` so you do not depend on the customer coming back.

The checkout options that matter for DuitNow Pay:

```javascript Checkout Options theme={null}
var options = {
  "key": "[YOUR_KEY_ID]",
  "amount": 10000,
  "currency": "MYR",
  "order_id": "order_TrGnI0fFdayPhx",
  "redirect": true,
  "callback_url": "https://merchant.example.my/payment/return",
  "prefill": {
    "email": "nur.aisyah@example.com",
    "contact": "+60123456789"
  }
};
```

## Supported Products

| Product | Supported |
| - | - |
| Standard Checkout (web and mobile web) | Yes |
| S2S API | Yes. See [S2S integration](https://razorpay.com/docs/my/payments/payment-gateway/s2s-integration/json/v2/build-integration/duitnow-pay.md). |
| Payment Links | Yes |
| Mobile SDKs | Yes, through Standard Checkout. The customer completes the payment on the bank's page. Opening the bank's app directly (app-to-app) is coming soon. |
| Payment Pages, Invoices | Coming soon |
| Custom Checkout | No |
| Recurring payments | No |

## Limits and Timings

| Item | Value |
| - | - |
| Minimum amount | RM 1.00 |
| Maximum amount | RM 50,000 per payment |
| Currency | MYR only |
| Payment window | 10 minutes. The customer must approve the payment at their bank within the time the bank allows. If they do not, the payment fails. |
| Refunds | Supported. During early access, the customer receives the money as a bank transfer within 5 to 7 working days. See [Refunds](#refunds). |
| Test mode | Not available. Test with a live RM 1.00 payment. |

## Refunds

Create full or partial refunds for DuitNow Pay payments from the Dashboard or the [Refunds API](https://razorpay.com/docs/my/api/refunds/create-normal.md), as for any other method.

During early access, the refund stays pending while Razorpay Curlec sends the money to your customer's bank account as a bank transfer within 5 to 7 working days. The refund then shows as processed. Your customer sees a transfer from Razorpay Curlec, not a reversal of the original payment. Do not also refund the customer yourself.

## Identify DuitNow Pay Payments

In the API, webhooks and reports, DuitNow Pay payments have the method `duitnow` and `duitnow.flow` set to `online_banking`. The `bank` field holds the code of the customer's bank.

## Frequently Asked Questions (FAQs)

> [accordion] 1. Who can use DuitNow Pay?
>
> Businesses that Razorpay Curlec has registered with PayNet. DuitNow Pay is in early access. Contact your account manager.

> [accordion] 2. Do I need to register with PayNet myself?
>
> No. Razorpay Curlec registers your business.

> [accordion] 3. Do I need to change my integration?
>
> Not on Standard Checkout or Payment Links, apart from passing a callback URL. On the S2S API, follow the [DuitNow Pay S2S integration](https://razorpay.com/docs/my/payments/payment-gateway/s2s-integration/json/v2/build-integration/duitnow-pay.md) guide.

> [accordion] 4. Which banks can customers use?
>
> Major Malaysian banks. The list is shown at checkout. For S2S, use the bank codes in the [integration guide](https://razorpay.com/docs/my/payments/payment-gateway/s2s-integration/json/v2/build-integration/duitnow-pay.md#1-1-get-the-list-of-banks).

> [accordion] 5. How is it different from FPX?
>
> The customer experience is similar: pick a bank and approve on its page. DuitNow Pay runs on PayNet's real-time network.

> [accordion] 6. Can I refund a DuitNow Pay payment?
>
> Yes, full or partial, from the Dashboard or API. During early access, your customer receives the money as a bank transfer from Razorpay Curlec within 5 to 7 working days.

> [accordion] 7. Can my customers pay in their bank's app?
>
> They approve on the bank's page today, which may open the bank's app on a phone. Opening the bank's app directly is coming soon.

> [accordion] 8. Is there a test mode?
>
> No. Make a live RM 1.00 payment.

> [accordion] 9. Can I use DuitNow Pay for subscriptions?
>
> No. DuitNow Pay is for one-time payments only.

> [accordion] 10. How do I find DuitNow Pay payments in reports?
>
> Filter by the method `duitnow`. The flow is `online_banking`.

### Related Information

* [DuitNow](https://razorpay.com/docs/my/payments/payment-methods/duitnow)
* [DuitNow QR](https://razorpay.com/docs/my/payments/payment-methods/duitnow/qr.md)
* [DuitNow Pay S2S Integration](https://razorpay.com/docs/my/payments/payment-gateway/s2s-integration/json/v2/build-integration/duitnow-pay.md)
* [About Payment Methods](https://razorpay.com/docs/my/payments/payment-methods)
