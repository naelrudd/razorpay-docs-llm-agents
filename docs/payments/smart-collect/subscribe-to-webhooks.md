> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Subscribe to Webhooks

> Subscribe to various webhook events related to Smart Collect to receive instant notifications.

Available in
🇮🇳 India

Subscribe to webhook events relevant to Smart Collect.

To subscribe to webhook events:

1. Log in to the Dashboard.
2. Navigate to **Dashboard** → **Account & Settings** → **Webhooks** to subscribe to any of the events mentioned in the following section.

> [!NOTE]
>
> **Handy Tips**
>
> * Ensure that you mitigate possible webhook failures.
> * Ensure that you have subscribed to [Smart Collect Events](https://razorpay.com/docs/webhooks/smart-collect.md).
> * If the Customer Identifier is customer-specific, please pass `customer_id` while creating the Customer Identifier. Customer\_id will be reflected in webhooks as well for easy reconciliation.
> * To uniquely identify the payment, store the `bank_reference` (unique reference number on the customer's bank statement) received in [webhooks](https://razorpay.com/docs/webhooks/smart-collect.md) or the [Fetch API response](https://razorpay.com/docs/api/payments/smart-collect/fetch-with-id.md).

## Webhook Events and Descriptions

| Webhook Events | Description |
| - | - |
| virtual\_account.created | Triggered when a Customer Identifier is created. |
| virtual\_account.credited | Triggered when a payment is made to a Customer Identifier. |
| virtual\_account.closed | Triggered when a Customer Identifier expires on a date set by you or is manually closed by you. |

Know more about [Webhooks](https://razorpay.com/docs/webhooks) and check the [sample payloads](https://razorpay.com/docs/webhooks/smart-collect.md).

### Related Information

* [Razorpay Smart Collect](https://razorpay.com/docs/payments/smart-collect)
* [How Smart Collect Works](https://razorpay.com/docs/payments/smart-collect/how-it-works.md)
* [Customer Identifier States](https://razorpay.com/docs/payments/smart-collect/states.md)
* [Smart Collect Dashboard](https://razorpay.com/docs/payments/smart-collect)
* [Create Customer Identifiers](https://razorpay.com/docs/payments/smart-collect/create.md)
* [Close Customer Identifiers](https://razorpay.com/docs/payments/smart-collect/close.md)
* [Refund Payments](https://razorpay.com/docs/payments/smart-collect/refund.md)
* [Refund Failures](https://razorpay.com/docs/payments/smart-collect/refund-failures.md)
* [Search for a Customer Identifier](https://razorpay.com/docs/payments/smart-collect/search.md)
* [Make Test Payments](https://razorpay.com/docs/payments/smart-collect/test-payments.md)
* [Smart Collect APIs](https://razorpay.com/docs/api/payments/smart-collect.md)
