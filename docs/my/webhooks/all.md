> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# All Webhook Events

> List of all Payments, Partners and Payouts webhook events.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Given below is the complete list of webhook events for [Payments](https://razorpay.com/docs/my/webhooks/payments.md).

| Concept/Product | Webhook Event | Description |
| - | - | - |
| Orders | [order.paid](https://razorpay.com/docs/my/webhooks/orders.md#order-paid) | Triggered when an order is successfully paid. |
| Payments ^^^ | [payment.authorized](https://razorpay.com/docs/my/webhooks/payments.md#payment-authorised) | Triggered when a payment is authorised. |
| | [payment.captured](https://razorpay.com/docs/my/webhooks/payments.md#payment-captured) | Triggered when a payment is successfully captured. |
| | [payment.failed](https://razorpay.com/docs/my/webhooks/payments.md#payment-failed) | Triggered when a payment fails. |
| Payment Downtime ^^^ | [payment.downtime.started](https://razorpay.com/docs/my/webhooks/payments.md#payment-downtime-started) | Triggered at the beginning of the downtime. |
| | [payment.downtime.resolved](https://razorpay.com/docs/my/webhooks/payments.md#payment-downtime-resolved) | Triggered when a downtime is resolved. |
| | [payment.downtime.updated](https://razorpay.com/docs/my/webhooks/payments.md#payment-downtime-updated) | Triggered when a downtime is updated. |
| Refunds ^^^^ | [refund.created](https://razorpay.com/docs/my/webhooks/refunds.md#refund-created) | Triggered when a refund is created. |
| | [refund.processed](https://razorpay.com/docs/my/webhooks/refunds.md#refund-processed) | Triggered when the refund is successfully processed. |
| | [refund.failed](https://razorpay.com/docs/my/webhooks/refunds.md#refund-failed) | Triggered when we are not able to process a refund. |
| | refund.speed\_changed | Triggered when the refund speed is changed. |
| Invoices ^^^ | [invoice.partially\_paid](https://razorpay.com/docs/my/webhooks/invoices.md#invoice-partially-paid) | Triggered when a partial payment is made against an invoice. |
| | [invoice.paid](https://razorpay.com/docs/my/webhooks/invoices.md#invoice-paid) | Triggered when an invoice is successfully paid. |
| | [invoice.expired](https://razorpay.com/docs/my/webhooks/invoices.md#invoice-expired) | Triggered when an invoice expires. |
| Subscriptions ^^^^^^^^^^ | [subscription.authenticated](https://razorpay.com/docs/my/webhooks/subscriptions.md#subscription-authenticated) | Sent when the first payment is made on the subscription. This can either be the authorisation amount, the upfront amount, the plan amount or a combination of the plan amount and the upfront amount. |
| | [subscription.activated](https://razorpay.com/docs/my/webhooks/subscriptions.md#subscription-activated) | Sent when the subscription moves to the active state either from the authenticated, pending or halted state. If a Subscription moves to the active state from the pending or halted state, only the subsequent invoices that are generated are charged. Existing invoices that were already generated are not charged. |
| | [subscription.charged](https://razorpay.com/docs/my/webhooks/subscriptions.md#subscription-charged) | Sent every time a successful charge is made on the subscription. |
| | [subscription.completed](https://razorpay.com/docs/my/webhooks/subscriptions.md#subscription-completed) | Sent when all the invoices are generated for a subscription and the subscription moves to the completed state. |
| | [subscription.updated](https://razorpay.com/docs/my/webhooks/subscriptions.md#subscription-updated) | Sent when a subscription is successfully updated. There is no state change when a subscription is updated. |
| | [subscription.pending](https://razorpay.com/docs/my/webhooks/subscriptions.md#subscription-pending) | Sent when the subscription moves to the pending state. This happens when a charge on the card fails. We try to charge the card on a periodic basis while it is in the pending state. If the payment fails again, the Webhook is triggered again. |
| | [subscription.halted](https://razorpay.com/docs/my/webhooks/subscriptions.md#subscription-halted) | Sent when all retries have been exhausted and the subscription moves from the pending state to the halted state. The customer has to manually retry the charge or change the card linked to the subscription, for the subscription to move back to the active state. |
| | [subscription.cancelled](https://razorpay.com/docs/my/webhooks/subscriptions.md#subscription-cancelled) | Sent when a subscription is cancelled and moved to the cancelled state. |
| | [subscription.paused](https://razorpay.com/docs/my/webhooks/subscriptions.md#subscription-paused) | Sent when a subscription is paused and moved to the paused state. |
| | [subscription.resumed](https://razorpay.com/docs/my/webhooks/subscriptions.md#subscription-resumed) | Sent when a subscription is resumed and moved to the resumed state. |
| Route (Transfers) ^^ | [transfer.processed](https://razorpay.com/docs/my/webhooks/route.md#transfer-processed) | Triggered when a transfer made to a Linked Account is processed. |
| | [transfer.failed](https://razorpay.com/docs/my/webhooks/route.md#transfer-failed) | Triggered when a transfer made to a Linked Account is failed. |
| Route (Settlements) | [settlement.processed](https://razorpay.com/docs/my/webhooks/route.md#settlement-processed) | Triggered when a transfer (made to a Parent merchant account or a Linked Account) is **settled** with the parent merchant. Available for all Razorpay Curlec users. To enable this webhook when a transfer settles on the parent account, you must contact our [Support team](https://curlec.com/support/). |
| Route (Linked Accounts) ^^^ | [product.route.under\_review](https://razorpay.com/docs/my/webhooks/route.md#product-route-under-review) | Triggered when the Linked account is in the process of being verified by Razorpay Curlec. |
| | [product.route.needs\_clarification](https://razorpay.com/docs/my/webhooks/route.md#product-route-needs-clarification) | Triggered when verification of the Linked account has failed, reasons are also included in the data object. |
| | [product.route.activated](https://razorpay.com/docs/my/webhooks/route.md#product-route-activated) | Triggered when a Linked account has been verified successfully and is activated. |
| Payment Links ^^^^ | [payment\_link.paid](https://razorpay.com/docs/my/webhooks/payment-links.md#payment-link-paid) | Triggered when a Payment Link is paid. |
| | [payment\_link.partially\_paid](https://razorpay.com/docs/my/webhooks/payment-links.md#payment-link-partially-paid) | Triggered when a partial payment is made on a Standard Payment Link. |
| | [payment\_link.cancelled](https://razorpay.com/docs/my/webhooks/payment-links.md#payment-link-cancelled) | Triggered when a Payment Link is cancelled by you. |
| | [payment\_link.expired](https://razorpay.com/docs/my/webhooks/payment-links.md#payment-link-expired) | Triggered when a Payment Link expires. |
