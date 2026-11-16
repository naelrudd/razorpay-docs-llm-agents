> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payment Capture Settings

> Configure auto and manual payment capture settings from Razorpay Dashboard and using APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

When a customer makes an online payment, it usually flows through different states. Know more about [payment states](https://razorpay.com/docs/us/payments/payments#payment-life-cycle).

By default, once your customer completes a payment, it is automatically moved to the `captured` state.

> [!WARNING]
>
> **Watch Out!**
>
> * For **Direct Settlement** merchants, payments will be auto-captured irrespective of the configuration.
> * You must ensure that all payments in the authorized state are moved to the captured state within 3 days of creation. This is mandatory because payments that are not captured within this period will be [refunded automatically](https://razorpay.com/docs/us/payments/refunds/auto-refunds.md) to customers.

You can configure **Payment Capture settings** on the Dashboard. You can choose to:

* [Auto-capture all payments](#auto-capture-all-payments)
* [Auto-capture with set timeouts](#auto-capture-with-custom-timeouts)
* [Manually capture timeout](#manual-capture-timeout)

> [!NOTE]
>
> **Handy Tips**
>
> * Only the Razorpay account owner can configure payment capture settings on the Dashboard.
> * Payment Capture settings are applicable only for payments created using the Orders API.

| Option | Description |
| - | - |
| Auto-capture all payments | All payments `authorized` within 3 days from the time of creation are auto-captured. |
| Auto-capture timeouts | <ul><li>Allows you to define custom auto-capture timeout.</li><li> The minimum value is 12 minutes.</li><li>The maximum value (default) is 3 days.</li></ul> |
| Manual capture timeout | <ul><li>Allows you to define custom manual capture timeout.</li><li>The minimum value is 12 minutes.</li><li> The maximum value (default) is 3 days.</li></ul> |
| Auto-refund speed | Payments in the `authorized` state are auto-refunded after the timeout. The available option is **Normal Refund** where the payment is refunded to your customer in 5-7 working days. The refund speed selected here is only applicable to payments that are auto-refunded. |

## Auto-capture All Payments

You can use this setting to capture all `authorized` payments automatically. This eliminates the time and effort spent manually capturing payments. **This is the default setting for all customers.**

## Auto-capture With Custom Timeouts

Once the payment is `created`, you can:

* Auto-capture payments that are `authorized` within a certain time period, and
* Manually capture payments that are `authorized` after that time period.

You can do this by setting up custom timeouts for automatic and manual capture.

### Auto-capture Timeout

Let us say you only want to auto-capture payments that are `authorized` within 3 days from creation.

| --- Capture Settings | <ul><li>Select **Automatic Capture** </li><li>Automatic capture timeout = 3 days.</li></ul> |
| - | - |
| Payments auto-refunded | If payments are `authorized` after 3 days. |

### Auto-capture + Manual Capture Timeouts

Let us say you want to:

* Auto-capture payments that are `authorized` within 2 days from creation.
* Manually capture payments that are `authorized` within 3 days from creation.

| --- Capture Settings | <ul><li>Select **Automatic Capture** </li><li>Automatic capture timeout = 2 days.</li><li>Manual capture timeout = 3 days.</li></ul> |
| - | - |
| Payments auto-refunded if | <ul><li>Payments not `captured` by you within 3 days.</li><li> Payments are `authorized` after 3 days.</li></ul> |

> [accordion] To configure capture settings:
>
> 1. Log in to your Dashboard.
> 2. Navigate to the **Account & Settings** option and scroll to the **Payments Capture** option.
> 3. Click the **Change** button next to **Automatic Capture**.
> 4. Under **Automatic Capture**, click the drop-down and select the time period in the **Capture all payments authorised within** field. For example, 2 days.
> 5. Click **Next**.
> 6. Select **Capture manually via dashboard or API**.
> 7. Click the drop-down and select the time period in the **Capture payments manually authorised within** field. For example, 3 days.
> 8. Click **Next**.
> 9. Select Normal Refund as the **Refund Speed**.
> 10. Click **Save**.

## Manually Capture Payments

You can use this setting to capture `authorized` payments manually.

### Manual Capture Timeout

Let us say you only want to manually capture payments that are `authorized` within 3 days from creation. To do this, you should set the manual capture timeout as 3 days.

| --- Capture Settings | <ul><li>Select **Manual Capture** </li><li>Manual capture timeout = 3 days.</li></ul> |
| - | - |
| Payments auto-refunded if | <ul><li>Payments not `captured` by you within 3 days.</li><li> Payments are `authorized` after 3 days.</li></ul> |

To set up the manual capture:

1. Log in to the Dashboard.
2. Navigate to the **Account & Settings** option and scroll to the **Payments Capture** option.
3. Click the **Change** button next to **Automatic Capture**.
4. Select the **Manual Capture** option.
5. Set the manual capture timeout to 3 days and click **Next**.
6. Select Normal Refund as the **Refund Speed**.
7. Click **Save**.

You can manually capture payments in the `authorized` state using our [Capture API](https://razorpay.com/docs/us/api/payments/capture.md) or from the [Dashboard](https://razorpay.com/docs/us/payments/payments/dashboard.md#manually-capture-payments). All payments that are not captured within the manual timeout period will be auto-refunded.

## Configure Payment Capture Settings Using Orders API

Capture values passed in the [Orders API](https://razorpay.com/docs/payments/payments/capture-settings/api) take precedence over the Payment Capture settings configured on the Dashboard. You can use this to change the capture settings for individual payments.

### Related Information

* [How Payment Gateway Works](https://razorpay.com/docs/us/payments/payment-gateway/how-it-works.md)
* [Payment States](https://razorpay.com/docs/us/payments/payments)
* [Refunds](https://razorpay.com/docs/us/payments/refunds)
* Manually capture payments in the `authorized` state using the [Capture API](https://razorpay.com/docs/us/api/payments/capture.md) or from the [Dashboard](https://razorpay.com/docs/us/payments/payments/dashboard.md#manually-capture-payments)
* [Set up and Subscribe to Webhook events](https://razorpay.com/docs/us/webhooks/setup-edit-payments.md)
