> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Subscription Status

> Check the different Subscription statuses mapped between WooCommerce and Razorpay Subscriptions.

Available in
🇮🇳 India
🇲🇾 Malaysia

## WooCommerce and Razorpay Subscription Status Mapping

The subscription status names used by Razorpay and WooCommerce are different. The table below shows the mapping between the subscription statuses names used by Razorpay and WooCommerce. Know more about the [Razorpay Subscriptions states](https://razorpay.com/docs/payments/subscriptions/states.md).

| WooCommerce Subscription status | Razorpay Subscription Status | Description |
| - | - | - |
| Pending | Created | This is the initial status of the subscription before the authentication/first payment transaction is complete. |
| Active | Authenticated, Active | This is the status of the subscription once the payment transaction has been successfully completed. |
| On-hold | Pending | The subscription acquires this status when it has been suspended or halted. This is done when a charge on the customer's card is unsuccessful. |
| Cancelled | Cancelled | The `cancel` option is used to cancel the subscription altogether. Once a subscription is cancelled, it cannot be restarted. |
| Expired | Complete | The subscription acquires this status when the expiry period mentioned during the subscription creation comes to an end. |
