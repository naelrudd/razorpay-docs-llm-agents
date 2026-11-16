> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Subscriptions

> Know about Subscriptions and list of endpoints.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

You can use Subscriptions to charge a customer periodically. A Subscription contains details like the plan, the start date, the total number of billing cycles, the free trial period (if any) and the upfront amount to be collected.

Below are the steps to integrate Subscriptions. You can also refer to our comprehensive [Subscriptions Integration guide](https://razorpay.com/docs/sg/payments/subscriptions/integration-guide.md).

1. [Create a Plan](https://razorpay.com/docs/sg/api/payments/subscriptions/create-plan.md)
2. [Create a Subscription](https://razorpay.com/docs/sg/api/payments/subscriptions/create-subscription.md)
3. [Checkout Integration](https://razorpay.com/docs/sg/payments/subscriptions/integration-guide.md#step-1-3-integrate-with-standard-checkout)

> [card] [Create a Plan](https://razorpay.com/docs/sg/api/payments/subscriptions/create-plan.md)
>
> `POST` `/v1/plans`
>
> Creates a plan.

> [card] [Fetch All Plans](https://razorpay.com/docs/sg/api/payments/subscriptions/fetch-all-plans.md)
>
> `GET` `/v1/plans`
>
> Fetches all the plans.

> [card] [Fetch a Plan With ID](https://razorpay.com/docs/sg/api/payments/subscriptions/fetch-a-plan.md)
>
> `GET` `/v1/plans/:id`
>
> Fetches a plan by its unique identifier.

> [card] [Create a Subscription](https://razorpay.com/docs/sg/api/payments/subscriptions/create-subscription.md)
>
> `POST` `/v1/subscriptions`
>
> Creates a Subscription.

> [card] [Create a Subscription Link](https://razorpay.com/docs/sg/api/payments/subscriptions/create-subscription-link.md)
>
> `POST` `/v1/subscriptions`
>
> Creates a Subscription link.

> [card] [Fetch All Subscriptions](https://razorpay.com/docs/sg/api/payments/subscriptions/fetch-subscriptions.md)
>
> `GET` `/v1/subscriptions`
>
> Fetches all the created Subscriptions.

> [card] [Fetch Subscription With ID](https://razorpay.com/docs/sg/api/payments/subscriptions/fetch-subscription-id.md)
>
> `GET` `/v1/subscriptions/:id`
>
> Fetches a Subscription details using its unique identifier.

> [card] [Cancel a Subscription](https://razorpay.com/docs/sg/api/payments/subscriptions/cancel-subscription.md)
>
> `POST` `/v1/subscriptions/:id/cancel`
>
> Cancels a Subscription.

> [card] [Update a Subscription](https://razorpay.com/docs/sg/api/payments/subscriptions/update-subscription.md)
>
> `PATCH` `/v1/subscriptions/:id`
>
> Updates a Subscription.

> [card] [Fetch Details of a Pending Update](https://razorpay.com/docs/sg/api/payments/subscriptions/fetch-pending-update-details.md)
>
> `GET` `/v1/subscriptions/:id/retrieve_scheduled_changes`
>
> Fetches details about any update of a Subscription.

> [card] [Cancel an Update](https://razorpay.com/docs/sg/api/payments/subscriptions/cancel-update.md)
>
> `POST` `/v1/subscriptions/:id/cancel_scheduled_changes`
>
> Cancels an update.

> [card] [Pause a Subscription](https://razorpay.com/docs/sg/api/payments/subscriptions/pause-subscription.md)
>
> `POST` `/v1/subscriptions/:id/pause`
>
> Pauses an active Subscription.

> [card] [Resume a Subscription](https://razorpay.com/docs/sg/api/payments/subscriptions/resume-subscription.md)
>
> `POST` `/v1/subscriptions/:id/resume`
>
> Resumes a paused Subscription.

> [card] [Fetch All Invoices for a Subscription](https://razorpay.com/docs/sg/api/payments/subscriptions/fetch-invoices.md)
>
> `GET` `/v1/subscriptions`
>
> Fetches all the generated invoices for a Subscription.

> [card] [Link an Offer to a Subscription](https://razorpay.com/docs/sg/api/payments/subscriptions/link-offer.md)
>
> `POST` `/v1/subscriptions`
>
> Links an Offer to a Subscription.

> [card] [Delete an Offer linked to a Subscription](https://razorpay.com/docs/api/payments/subscriptions/delete-offer.md)
>
> `DELETE` `/v1/subscriptions/:sub_id/:offer_id`
>
> Deletes an Offer linked to a Subscription.

## Related Guides

* [About Subscriptions](https://razorpay.com/docs/sg/payments/subscriptions)
* [Integrate With Subscriptions](https://razorpay.com/docs/sg/payments/subscriptions/integration-guide.md)
* [Set Up Webhooks](https://razorpay.com/docs/sg/webhooks/setup-edit-payments.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/subscriptions.md)
