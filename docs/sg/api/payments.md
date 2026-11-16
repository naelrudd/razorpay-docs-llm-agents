> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payments

> Capture and fetch Payments using Razorpay APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Payments APIs are used to capture and fetch payments. You can also fetch payments based on orders and card details of payment.

> [!NOTE]
>
> **Handy Tips**
>
> You can use Payments API only to retrieve payment details or change the status from `authorized` to `captured` and **not** to collect payments. You can use our [products](https://razorpay.com/docs/sg/payments.md) to accept payments.

> [card] [Capture a Payment](https://razorpay.com/docs/sg/api/payments/capture.md)
>
> `POST` `/v1/payments/:id/capture`
>
> Captures a payment.

> [card] [Fetch a Payment With ID](https://razorpay.com/docs/sg/api/payments/fetch-with-id.md)
>
> `GET` `/v1/payments/:id`
>
> Retrieves details of a specific payment using id.

> [card] [Fetch a Payment With ID (Example 1)](https://razorpay.com/docs/sg/api/payments/fetch-payment-expanded-card.md)
>
> `GET` `/v1/payments/:id/?expand[]=card`
>
> Retrieves details of all the payments that is created, with the `card` parameter.

> [card] [Fetch All Payments](https://razorpay.com/docs/sg/api/payments/fetch-all-payments.md)
>
> `GET` `/v1/payments`
>
> Retrieves details of all payments.

> [card] [Fetch All Payments (Example 1)](https://razorpay.com/docs/sg/api/payments/fetch-all-payments-with-expanded-card-details.md)
>
> `GET` `/v1/payments?expand[]=card`
>
> Retrieves expanded card details of a payment.

> [card] [Fetch Payments Based on Orders](https://razorpay.com/docs/sg/api/payments/fetch-payments-orders.md)
>
> `GET` `/v1/orders/:id/payments`
>
> Retrieves payments linked to an Order.

> [card] [Fetch Card Details of a Payment](https://razorpay.com/docs/sg/api/payments/fetch-card-details-payment.md)
>
> `GET` `/v1/payments/:id/card`
>
> Retrieves card details of a payment.

> [card] [Update a Payment](https://razorpay.com/docs/sg/api/payments/update.md)
>
> `PATCH` `/v1/payments/:id/`
>
> Edits an existing payment.

## Related Guides

* [About Payments](https://razorpay.com/docs/sg/payments.md)
* [Set Up Webhooks](https://razorpay.com/docs/sg/webhooks/setup-edit-payments.md)
* [Sample Payloads](https://razorpay.com/docs/sg/webhooks/payments.md)
