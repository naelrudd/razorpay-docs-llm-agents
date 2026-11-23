> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Handle Late Authorised Payments

> Use Orders API or webhooks to handle late authorisations.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Late authorised payments are rare situations, as only less than 0.5% of the total payments get late authorised. The payments that are **late authorised** and not captured are auto-refunded once the capture time window has passed. Know more about [Payment Capture Settings](https://razorpay.com/docs/my/payments/payments/capture-settings.md) and [auto-refunds](https://razorpay.com/docs/my/payments/refunds/auto-refunds.md).

Based on your business needs, you can decide how to handle payments that may get late authorised. This largely depends on whether you can provide services for the late authorised payment.

## If You Wish to Provide Services Later

You can keep a track of these payments and fulfil the order when it is authorised.

For example, if you are an online marketplace merchant, who sells clothes and accessories, you can mark the order as 'pending' in your system and deliver the order when the payment gets authorised

## Payment Capture Settings

This is the easiest way to handle late authorisation. This feature gives you control over which payments should be auto-captured and which payments should be auto-refunded by allowing you to:

* Automatically capture all payments.
* Setup custom timeouts for automatic and manual capture.
* Manually capture all payments.

Know more about [Payment Capture settings](https://razorpay.com/docs/my/payments/payments/capture-settings.md).

## Orders API

Orders API makes it easier to handle cases of late authorisation in the following ways:

* It clubs multiple payment attempts against the same order. If one of the payments is successful and another attempt gets **Late Authorised**, the late authorised payment is refunded immediately, and only successful payment is marked against the Order.

* Allows you to auto-capture payments based on the parameters passed in the Orders API. Capture values passed in the Orders API take precedence over the Payment Capture settings configured on the Dashboard.

## Webhooks

Webhooks send you notifications when payments move to the **Authorized** state. The webhook `payment.authorized` sends you a notification when the payment you were expecting to be **Late Authorized** moves to **Authorized** state.

You can send email notifications to your customers about the payment status, asking them to take further action to deliver the service. You can set up webhooks from the Dashboard. Know more about [webhooks](https://razorpay.com/docs/my/webhooks).

## Frequently Asked Question (FAQs)

> [accordion] Is Late Authorisation of payment specific to ?
>
> No. While other gateways also face these interruptions, Razorpay Curlec ensures that you have a way of handling late authorised payments using:
>
> * [Orders API](https://razorpay.com/docs/my/api/orders/create.md)
> * [Webhooks](https://razorpay.com/docs/my/webhooks)
> * [Payment capture settings on the Dashboard](https://razorpay.com/docs/my/payments/payments/capture-settings.md).
>
> You can track the status of the payment on the Dashboard.

### Related Information

* [Late Authorisations](https://razorpay.com/docs/my/payments/payments/late-authorisation.md)
* [About Payments](https://razorpay.com/docs/my/payments/payments)
