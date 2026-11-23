> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Subscribe to Webhooks

> Subscribe to various webhook events related to Payment Links to receive instant notifications.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Subscribe to webhook events relevant to Payment Links.

To subscribe to webhook events:

1. Log in to the Dashboard.
2. Navigate to **Account & Settings** → **Webhooks** to subscribe to any of the events mentioned in the following section.

## Webhook Events and Descriptions

| Webhook Events | Description |
| - | - |
| payment\_link.paid | Triggered when a Payment Link is successfully paid. |
| payment\_link.partially\_paid | Triggered when a partial payment is made against a Payment Link. |
| payment\_link.expired | Triggered when a Payment Link expires. |
| payment\_link.cancelled | Triggered when you cancel a Payment Link. |

Know more about [Webhooks](https://razorpay.com/docs/my/webhooks) and check the [sample payloads](https://razorpay.com/docs/my/webhooks/payment-links.md).

> [!NOTE]
>
> **Handy Tips**
>
> For DuitNow payments, you may receive `payment.captured` more than once for the same payment. Use the payment ID to make sure you process it only once.

#### Related Information

<ul>
  <li>[Payment Links States](https://razorpay.com/docs/my/payments/payment-links/states.md)</li>
  <li>[FAQs](https://razorpay.com/docs/my/payments/payment-links/faqs.md)</li>
  <li>[Payment Links APIs](https://razorpay.com/docs/my/payments/payment-links/apis.md)</li>
</ul>
