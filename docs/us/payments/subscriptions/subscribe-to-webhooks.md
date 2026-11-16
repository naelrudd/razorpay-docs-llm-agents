> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Subscribe to Webhooks

> Subscribe to various webhook events related to Subscriptions to receive instant notifications.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can use Razorpay [Webhooks](https://razorpay.com/docs/us/webhooks) to receive notifications of all events related to Subscriptions.

To subscribe to webhook events:

1. Log in to the Dashboard.
2. Navigate to **Accounts & Settings** → **Webhooks** to subscribe to any of the events mentioned in the following section.

## Webhook Events and Descriptions

| Webhook Event | Description |
| - | - |
| `subscription.authenticated` | Sent when the first payment is made on the subscription. This can either be the authorization amount, the upfront amount, the plan amount or a combination of the plan amount and the upfront amount. |
| `subscription.activated` | Sent when the subscription moves to the `active` state either from the `authenticated`, `pending` or `halted` state. If a Subscription moves to the `active` state from the `pending` or `halted` state, only the subsequent invoices that are generated are charged. Existing invoices that were already generated are not charged. |
| `subscription.charged` | Sent every time a successful charge is made on the subscription. |
| `subscription.completed` | Sent when all the invoices are generated for a subscription and the subscription moves to the `completed` state. |
| `subscription.updated` | Sent when a subscription is successfully updated. There is no state change when a subscription is updated. |
| `subscription.pending` | Sent when the subscription moves to the `pending` state. This happens when a charge on the card fails. We try to charge the card on a periodic basis while it is in the `pending` state. If the payment fails again, the Webhook is triggered again. |
| `subscription.halted` | Sent when all retries have been exhausted and the subscription moves from the `pending` state to the `halted` state. The customer has to manually retry the charge or change the card linked to the subscription, for the subscription to move back to the `active` state. |
| `subscription.cancelled` | Sent when a subscription is cancelled and moved to the `cancelled` state. |
| `subscription.paused` | Sent when a subscription is paused and moved to the `paused` state. |
| `subscription.resumed` | Sent when a subscription is resumed and moved to the `resumed` state. |

Know more about [Webhooks](https://razorpay.com/docs/us/webhooks) and check the [sample payloads](https://razorpay.com/docs/webhooks/subscriptions.md).

### Related Information

[Subscriptions APIs](https://razorpay.com/docs/us/payments/subscriptions/apis.md)
