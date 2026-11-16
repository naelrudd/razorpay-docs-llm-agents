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

Late authorised payments are rare situations, as only less than 0.5% of the total payments get late authorised. The payments that are **late authorised** and not captured are auto-refunded once the capture time window has passed. Know more about [Payment Capture Settings](https://razorpay.com/docs/payments/payments/capture-settings.md) and [auto-refunds](https://razorpay.com/docs/payments/refunds/auto-refunds.md).

Based on your business needs, you can decide how to handle payments that may get late authorised. This largely depends on whether you can provide services for the late authorised payment.

## If You Wish to Provide Services Later

You can keep a track of these payments and fulfil the order when it is authorised.

For example, if you are an online marketplace merchant, who sells clothes and accessories, you can mark the order as 'pending' in your system and deliver the order when the payment gets authorised

## If You Cannot Provide Services for Late Authorised Payments

Ignore these orders and communicate to the customer. Payments that stay in an `Authorized` state are auto-refunded to customers within 5 working days (without considering the bank's processing time).

> [accordion] Example
>
> If you are an online food delivery service, you need to deliver food immediately on receiving payments. In this case, you cannot wait for late authorisation of payments. Ignore this order and inform the customer about order cancellation and auto-refund of any amount that may have got debited from the customer's account.

> [!NOTE]
>
> **Handy Tips**
>
> Auto refunds are issued within 5 days. However, if you want to issue a refund instantly, you can capture the payment and issue a refund as per your requirements. Know more about [Refunds](https://razorpay.com/docs/payments/refunds).

## If You Want to Provide Services Later

You can keep a track of these payments and fulfil the order when it is authorised.

> [accordion] Example
>
> If you are an online marketplace merchant, who sells clothes and accessories, you can mark the order as 'pending' in your system and deliver the order when the payment gets authorised.

> [!NOTE]
>
> **Communicate with Your Customers**
>
> When customers reach out to you about a payment that was debited from their bank accounts before the successful order completion, ensure that you clearly communicate the payment status and how you will be handling it. You can choose to send out a message such as the following:
>
> If your order has failed, any amount debited will be auto-refunded in 5 working days (not considering your bank's processing time).

## Payment Capture Settings

This is the easiest way to handle late authorisation. This feature gives you control over which payments should be auto-captured and which payments should be auto-refunded by allowing you to:

* Automatically capture all payments.
* Setup custom timeouts for automatic and [manual capture](https://razorpay.com/docs/payments/payments/capture-settings/api).
* Manually capture all payments.

Know more about [Payment Capture settings](https://razorpay.com/docs/payments/payments/capture-settings.md).

## Orders API

Orders API makes it easier to handle cases of late authorisation in the following ways:

* It clubs multiple payment attempts against the same order. If one of the payments is successful and another attempt gets **Late Authorised**, the late authorised payment is refunded immediately, and only successful payment is marked against the Order.

* Allows you to auto-capture payments based on the parameters passed in the [Orders API](https://razorpay.com/docs/payments/payments/capture-settings/api). Capture values passed in the Orders API take precedence over the Payment Capture settings configured on the Dashboard.

## Webhooks

Webhooks send you notifications when payments move to the **Authorized** state. The webhook `payment.authorized` sends you a notification when the payment you were expecting to be **Late Authorized** moves to **Authorized** state.

You can send email notifications to your customers about the payment status, asking them to take further action to deliver the service. You can set up webhooks from the Dashboard. Know more about [webhooks](https://razorpay.com/docs/webhooks).

## Frequently Asked Question (FAQs)

> [accordion] Is Late Authorisation of payment specific to ?
>
> No. While other gateways also face these interruptions, Razorpay ensures that you have a way of handling late authorised payments using:
>
> * [Orders API](https://razorpay.com/docs/api/orders.md)
> * [Webhooks](https://razorpay.com/docs/webhooks)
> * [Payment capture settings on the Dashboard](https://razorpay.com/docs/payments/payments/capture-settings.md).
>
> You can track the status of the payment on the Dashboard.

### Related Information

* [Late Authorisations](https://razorpay.com/docs/payments/payments/late-authorisation.md)
* [About Payments](https://razorpay.com/docs/payments/payments)
