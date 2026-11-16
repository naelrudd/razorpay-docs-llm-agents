> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Auto-Refunds

> Know why Razorpay auto-refunds some payments, how to identify auto-refunds and how to prevent them.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Auto-refunds are refunds that Razorpay triggers, as opposed to refunds you initiate from the Dashboard or using APIs. Only payments in the `authorized` state can be auto-refunded. Payments in the `captured` state are never auto-refunded. They are refunded only when you initiate a refund or when you lose a dispute.

## Reasons for Auto-Refunds

The table below lists the reasons a payment can be auto-refunded and when the auto-refund is triggered.

| Reason for Auto-Refund | When the Auto-Refund is Triggered |
| - | - |
| [Late authorisation](https://razorpay.com/docs/us/payments/payments/late-authorisation.md): the payment is authorised after your capture timeout. | Once the refund time window has passed. |
| Insufficient account balance when you are on the Platform Fee Bearer model. | 3 days after the payment is authorised. |
| Duplicate payment on an order that is already in the `paid` state. | Immediately. |
| The payment is not captured within your configured capture timeout (3 days by default). Know more about [Payment Capture Settings](https://razorpay.com/docs/us/payments/payments/capture-settings.md). | Once the refund time window has passed. |
| [ACH](https://razorpay.com/docs/us/payments/payment-methods/ach.md) and POS terminal payments that are not captured manually. | Once the refund time window has passed. |

> [!NOTE]
>
> **Refund Speed**
>
> Auto-refunds are always processed at normal speed. Know more about [Normal Refunds](https://razorpay.com/docs/us/payments/refunds/normal.md) and how long they take to reach the customer.

## Identify Auto-Refunds

Auto-refunds create a refund entity, just like the refunds you initiate. Use the payment's `captured` field to tell them apart. An auto-refunded payment was never captured, so the value is always `false`. A refund on a payment where `captured` is `true` is one you initiated or one for a lost dispute.

* **Webhooks**: Auto-refunds trigger the [refunds webhook events](https://razorpay.com/docs/us/webhooks/refunds.md). Check `payload.payment.entity.captured` in the webhook payload. If it is `false`, the refund is an auto-refund.
* **APIs**: When you [fetch refunds using the API](https://razorpay.com/docs/us/api/refunds/fetch-all.md), [fetch the corresponding payment](https://razorpay.com/docs/us/api/payments/fetch-with-id.md) for each refund. If the payment's `captured` value is `false`, the refund is an auto-refund. This needs one payment request for each refund, so for large volumes, use webhooks to identify auto-refunds as they happen.
* **Emails**: Razorpay sends you an email for each auto-refund, with the reason, a description and any corrective action you need to take.

## View Auto-Refunds on the Dashboard

On the **Refunds** page of the Dashboard, check the **Refund Source** column to tell auto-refunds apart from refunds you initiate. Refunds you initiate show **Business Initiated**. Auto-refunds show the reason, for example, **Auto-refunded - Late Auth**.

You can also download the refunds report and filter the auto-refunded transactions by their refund source.

> [!NOTE]
>
> **Settlements and Fees**
>
> Auto-refunds are triggered before the payment is captured. So the auto-refunded amount is not part of your settlement amount, and no processing fee is deducted from your settlement for an auto-refund.

## Prevent Auto-Refunds

To prevent your payments from being auto-refunded:

* If you have set up manual capture on the Dashboard, capture payments within the capture timeout. Know more about [Payment Capture Settings](https://razorpay.com/docs/us/payments/payments/capture-settings.md).
* Set capture timeouts on the Dashboard in [Payment Capture Settings](https://razorpay.com/docs/us/payments/payments/capture-settings.md#auto-capture-with-custom-timeouts).
* Capture a late authorised payment yourself before it is auto-refunded. Know more about [handling late authorised payments](https://razorpay.com/docs/us/payments/payments/late-authorisation/handle.md).

### Related Information

* [Normal Refunds](https://razorpay.com/docs/us/payments/refunds/normal.md)
* [Refunds Webhook Events](https://razorpay.com/docs/us/webhooks/refunds.md)
* [Late Authorisation](https://razorpay.com/docs/us/payments/payments/late-authorisation.md)
* [Handle Late Authorised Payments](https://razorpay.com/docs/us/payments/payments/late-authorisation/handle.md)
* [Payment Capture Settings](https://razorpay.com/docs/us/payments/payments/capture-settings.md)
