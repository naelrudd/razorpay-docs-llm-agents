> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Frequently Asked Questions (FAQs)

> Find answers to frequently asked questions about Razorpay Subscriptions and Subscription links.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

## General

> [accordion] How long can a Subscription remain active?
>
> We support Subscriptions for a maximum duration of 100 years. The number of billing cycles depends if the subscription is billed daily, weekly, monthly or yearly.

> [accordion] Why am I unable to use Add-ons?
>
> You are unable to use the Add-Ons feature since it is deprecated.

## Plans

> [accordion] Can I update or delete a Plan?
>
> No. You cannot update or delete a Plan. You should create a new Plan. Alternatively, you can duplicate and modify an existing Plan  as per your requirements.
>
> To duplicate a Plan:
>
> 1. Log in to the Dashboard and click **Subscriptions** under **PAYMENT PRODUCTS** in the left menu.
> 2. Go to **Plans** and click on the required **Plan Id**.
> 3. Click the **Duplicate Plan** icon in the top-right corner of the pop-up, as shown in the screenshot below.
>
>    ![Plan duplicate option on Subscription plan duplicate page](https://razorpay.com/docs/build/browser/assets/images/subscription_plan_duplicate.jpg)
> 4. Edit the plan details as required and click **Create Plan**.

## Capture Payments

> [accordion] Do I need to capture the authorisation payment used to validate a customer's card or UPI ID?
>
> No. You do not need to capture the ₹5 token authorisation payment used to validate a customer's card . This amount is auto-refunded to the customer.

> [accordion] Do I need to capture the Subscription payments made by customers?
>
> No. You do not need to capture payments made for a Subscription. Upfront amount and subsequent charges are auto-captured.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > The payment will not be captured if you cancel the Subscription before it gets authorised.

## Update Subscriptions

> [accordion] Can I update the plan amount or duration of Subscription when it is live?
>
> Yes. You can update details such as the plan amount, duration and quantity of a Subscription, even if it is live. Refer to the [Update Subscription section](https://razorpay.com/docs/sg/payments/subscriptions/update.md) for more details.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > You can only update a Subscription authorised using cards and not via UPI and Emandate.

> [accordion] When can I update a Subscription?
>
> You can only update a Subscription when it is in `authenticated` and `active` states. There is no state change when you update a Subscription. Know about [Updating a Subscription](https://razorpay.com/docs/sg/payments/subscriptions/update.md).

## Pause Subscriptions

> [accordion] Who can pause a Subscription?
>
> Only the business can pause a subscription. Customers cannot pause it.

> [accordion] Can all Subscriptions be paused?
>
> Subscriptions in the `active` state can be paused. You cannot pause a Subscription in any other state. Refer to the [life cycle](https://razorpay.com/docs/sg/payments/subscriptions/states.md) section for more details.

> [accordion] How can I pause a Subscription?
>
> You can pause a Subscription:
>
> * [From the Dashboard](https://razorpay.com/docs/sg/payments/subscriptions/pause-resume-cancel.md#pause-a-subscription-using-dashboard).
> * [Using APIs](https://razorpay.com/docs/sg/api/payments/subscriptions/pause-subscription.md).

## Resume Subscriptions

> [accordion] Who can resume a Subscription?
>
> Only the business can resume subscriptions.

> [accordion] How can I resume a Subscription?
>
> You can resume a Subscription:
>
> * [From the Dashboard](https://razorpay.com/docs/sg/payments/subscriptions/pause-resume-cancel.md#resume-a-subscription-using-dashboard).
> * [Using APIs](https://razorpay.com/docs/sg/api/payments/subscriptions/resume-subscription.md).

> [accordion] Can I resume a Subscription paused by my customer?
>
> No. You cannot resume a Subscription paused by your customer. Only your customer can resume such Subscriptions.

## Cancel Subscriptions

> [accordion] Can I cancel a Subscription?
>
> Yes. You can cancel a Subscription:
>
> * [From the Dashboard](https://razorpay.com/docs/sg/payments/subscriptions/pause-resume-cancel.md).
> * [Using APIs](https://razorpay.com/docs/sg/api/payments/subscriptions/cancel-subscription.md).

> [accordion] How can I know when my customer cancels a Subscription?
>
> You can set up the [subscription.cancelled](https://razorpay.com/docs/webhooks/subscriptions.md#subscription-cancelled) webhook event to get a notification when your customer cancels their Subscription. Know more about [subscribing to a webhook event](https://razorpay.com/docs/sg/payments/subscriptions/subscribe-to-webhooks.md).
