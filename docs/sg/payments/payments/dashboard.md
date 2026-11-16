> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payments - Dashboard Actions

> View payment details, manually capture payments, issue a refund or view settlement details of a payment from the Razorpay Dashboard.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can use the Dashboard to perform the following actions:

<ul>
  <li>[View Payment Details](#view-payment-details) </li>
  <li>[View Settlement Details of a Payment](#view-settlement-details-of-a-payment) </li>
  <li>[Manually Capture Payments](#manually-capture-payments) </li>
  <li>[Issue a Refund](#issue-a-refund) </li>
  <li>[Subscribe to Webhook Events](#subscribe-to-webhook-events) </li>
</ul>

## View Payment Details

To view the details of a payment made to your account:

1. Log in to your Dashboard.
2. Click **Transactions** → **Payments**.
3. Click a **Payment Id** to view details of the payment.

## View Settlement Details of a Payment

To view a detailed break-down of a settlement made to your account:

1. Log in to your Dashboard.
2. Navigate to **Transactions** → **Payments**.
3. Click on the specific **Payment Id** for which you want to view the settlement details.
4. In the **Payment Details** view, you can view the settlement details.
5. Click on the **settlement\_id** to view the detailed breakdown.

## Manually Capture Payments

To manually capture payments:

1. Log in to the Dashboard.
2. Navigate to **Transactions** → **Payments**.
3. Under the **Payments** tab, identify the authorized payment you want to capture.
4. Click the relevant **Payment Id**.
5. In the **Payment Details** pane, click **Capture Payment**.
6. A dialog box is displayed. Click **Yes, Capture**.

## Issue a Refund

You can issue refunds to your customers from the Dashboard. Know more about [issuing refunds](https://razorpay.com/docs/sg/payments/refunds/issue.md).

## Subscribe to Webhook Events

You can subscribe to webhook events from the Dashboard. Know more about [Webhooks](https://razorpay.com/docs/sg/webhooks).

To subscribe to webhook events:

1. Log in to the Dashboard.
2. Navigate to **Accounts & Settings** → **Webhooks** to subscribe to events available for payments.

The table below lists the webhook events available for payments.

| Webhook Event | Description |
| - | - |
| `payment.authorized` | Triggered when a payment is authorised. |
| `payment.captured` | Triggered when a payment is successfully captured. |
| `payment.failed` | Triggered when a payment fails. |

> [!NOTE]
>
> **Handy Tips**
>
> <ul>
>   <li>The payload for a Webhook is a snapshot of the entity when the event occurred.
>   For example, when a customer makes a payment, its status changes to `authorized`. It can then immediately move to the `captured` state.</li>
>   <li>The payment can be in the `captured` state when the `payment.authorized` Webhook is fired. However, the payload for the `payment.authorized` event contains details of the events when the payment was authorised, not when it was captured.</li>
> </ul>

Know more about [webhooks](https://razorpay.com/docs/sg/webhooks) and check the [sample payloads](https://razorpay.com/docs/sg/webhooks/payments.md).

### Related Information

* [About Payments](https://razorpay.com/docs/sg/payments/payments)
* [Payment APIs](https://razorpay.com/docs/sg/payments/payments/apis.md)
