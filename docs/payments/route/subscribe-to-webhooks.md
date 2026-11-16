> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Subscribe to Webhooks

> Subscribe to various Webhook events related to Razorpay Route to receive instant notifications.

Available in
🇮🇳 India
🇲🇾 Malaysia

To subscribe to webhook events:

1. Log in to the Dashboard.
2. Navigate to **Accounts & Settings** → **Webhooks** to subscribe to any of the events mentioned in the following section.

## Webhook Events and Descriptions

### Transfer and Settlement Events

| Webhook Event | Description |
| - | - |
| `transfer.processed` | Triggered when a transfer made to a Linked Account is processed. |
| `settlement.processed` | Triggered when a transfer made to a Linked Account is settled with the parent merchant. (Available only for [Razorpay Route](https://razorpay.com/docs/payments/route)). |
| `transfer.failed` | Triggered when a transfer made to a Linked Account has failed. |

### VPA Events

Available in 🇮🇳 India only. Linked Accounts that settle to a VPA (UPI id) emit the standard account events. There are no VPA-specific events. See [VPA Settlements](https://razorpay.com/docs/payments/route/linked-account/vpa-settlements.md).

| Webhook Event | Description |
| - | - |
| `account.activated` | Triggered when a VPA Linked Account is activated. |
| `account.under_review` | Triggered when a VPA Linked Account is under review. |
| `account.needs_clarification` | Triggered when a VPA Linked Account needs clarification. |
| `account.updated` | Triggered when a VPA Linked Account is updated. |

Know more about [Webhooks](https://razorpay.com/docs/webhooks) and check the [sample payloads](https://razorpay.com/docs/webhooks/route.md).

### Related Information

* [VPA Settlements](https://razorpay.com/docs/payments/route/linked-account/vpa-settlements.md)
* [Route APIs](https://razorpay.com/docs/payments/route/apis.md)
