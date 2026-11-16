> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Refunds

> Initiate normal and instant refunds to your customers using Razorpay Refund APIs. View and update refund using APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Make full or partial refunds to customers. You can initiate refunds only on those payments that are in `captured` state. A payment in `authorized` state is auto-refunded if not `captured` within 3 days of creation. You can create and manage refunds using APIs or from the [Dashboard](https://razorpay.com/docs/payments/refunds#dashboard-actions).\
\


Fork the Razorpay Postman Public Workspace and try the Refunds APIs using your [Test API Keys](https://razorpay.com/docs/api/authentication.md#generate-api-keys).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-49fdb1f6-7e7d-426c-b7b4-3dd468d8565e)

> [card] [Create a Normal Refund](https://razorpay.com/docs/api/refunds/create-normal.md)
>
> `POST` `/v1/payments/:id/refund`
>
> Creates a normal refund for a payment.

> [card] [Create a Normal Refund (Idempotent Request)](https://razorpay.com/docs/api/refunds/normal-refunds-idempotent.md)
>
> `POST` `/v1/payments/:id/refund`
>
> Retry or send the same normal refund request multiple times safely by creating a normal refund idempotency request.

> [card] [Create an Instant Refund](https://razorpay.com/docs/api/refunds/create-instant.md)
>
> `POST` `/v1/payments/:id/refund`
>
> Creates an instant refund for a payment.

> [card] [Create an Instant Refund (Idempotent Request)](https://razorpay.com/docs/api/refunds/instant-refunds-idempotent.md)
>
> `POST` `/v1/payments/:id/refund`
>
> Retry or send the same instant refund request multiple times safely by creating an instant refund idempotency request.

> [card] [Fetch Multiple Refunds for a Payment](https://razorpay.com/docs/api/refunds/fetch-multiple-refund-payment.md)
>
> `GET` `/v1/payments/:id/refunds`
>
> Retrieves multiple refunds for a payment.

> [card] [Fetch a Specific Refund for a Payment](https://razorpay.com/docs/api/refunds/fetch-specific-refund-payment.md)
>
> `GET` `/v1/payments/:payment_id/refunds/:refund_id`
>
> Retrieves details of a specific refund made for a payment.

> [card] [Fetch All Refunds](https://razorpay.com/docs/api/refunds/fetch-all.md)
>
> `GET` `/v1/refunds/`
>
> Retrieves details of all refunds.

> [card] [Fetch Refund With ID](https://razorpay.com/docs/api/refunds/fetch-with-id.md)
>
> `GET` `/v1/refunds/:id`
>
> Retrieves the refund using the id.

> [card] [Update a Refund](https://razorpay.com/docs/api/refunds/update.md)
>
> `PATCH` `/v1/refunds/:id/`
>
> Updates the `notes` parameter for a refund.

## Related Guides

* [About Refunds](https://razorpay.com/docs/payments/refunds)
* [Set Up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payments.md)
* [Sample Payloads](https://razorpay.com/docs/webhooks/refunds.md)
