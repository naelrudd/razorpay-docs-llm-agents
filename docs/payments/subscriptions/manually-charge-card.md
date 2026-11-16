> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Charge a Card Manually

> Manually charge a card for Razorpay Subscriptions from the Razorpay Dashboard.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

If one or more auto-charge attempts fail, you will receive a webhook notification. Know more about [webhooks](https://razorpay.com/docs/webhooks/subscriptions.md). In such scenarios, you can manually charge the card linked to the Subscription from the Dashboard. Until a successful charge is made, the invoice will be in the `issued` state.

> [!WARNING]
>
> **Watch Out!**
>
> Manual charging of a domestic card is not supported.

## Manually Charge a Card From Dashboard

To manually charge a card:

1. Log in to the Dashboard and click **Subscriptions** under **PAYMENT PRODUCTS** in the left menu.
2. Click the **Subscription Id** in the `pending` state that is to be charged.
3. Click the invoice in the `issued` state and click **Attempt Charge**. Alternatively, you can click **Attempt Charge** against the invoice in the `issued` state on the details panel.

### Related Information

* [Create and View Plans](https://razorpay.com/docs/payments/subscriptions/create-plans.md)
* [Create Subscriptions via Links](https://razorpay.com/docs/payments/subscriptions/create-subscription-links.md)
* [Update a Subscription](https://razorpay.com/docs/payments/subscriptions/update.md)
* [Subscriptions Settings](https://razorpay.com/docs/payments/subscriptions/settings.md)
