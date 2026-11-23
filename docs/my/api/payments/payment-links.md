> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payment Links

> Create, update, delete, cancel, fetch and send Payment Links using Razorpay Curlec APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

[Payment Links](https://razorpay.com/docs/my/payments/payment-links) are URLs that you can send to your customers by email to collect payments from them. Customers can click on the URL, which opens the payment request page, and complete the payment using any of the available payment methods. You can create, fetch, edit or cancel Payment Links using APIs or from the [Dashboard](https://razorpay.com/docs/my/payments/refunds#dashboard-actions).

> [card] [Create a Standard Payment Link](https://razorpay.com/docs/my/api/payments/payment-links/create-standard.md)
>
> `POST` `/v1/payment_links`
>
> Creates a Standard Payment Link.

> [card] [Fetch All Standard Payment Links](https://razorpay.com/docs/my/api/payments/payment-links/fetch-all-standard.md)
>
> `GET` `/v1/payment_links`
>
> Retrieves data of all Standard Payment Links.

> [card] [Fetch a Standard Payment Link With ID](https://razorpay.com/docs/my/api/payments/payment-links/fetch-id-standard.md)
>
> `GET` `/v1/payment_links/:id`
>
> Retrieves data of a Standard Payment Link with id.

> [card] [Send or Resend Notifications](https://razorpay.com/docs/my/api/payments/payment-links/resend.md)
>
> `POST` `/v1/payment_links/:id/notify_by/:medium`
>
> Sends notifications to your customers.

> [card] [Update a Standard Payment Link](https://razorpay.com/docs/my/api/payments/payment-links/update-standard.md)
>
> `PATCH` `/v1/payment_links/:id`
>
> Updates the details of a Standard Payment Link.

> [card] [Cancel a Standard Payment Link](https://razorpay.com/docs/my/api/payments/payment-links/cancel-standard.md)
>
> `POST` `/v1/payment_links/:id/cancel`
>
> Cancels a Standard Payment Link.

> [card] [Implement Thematic Changes on Checkout](https://razorpay.com/docs/my/api/payments/payment-links/checkout-theme.md)
>
> `POST` `/v1/payment_links`
>
> Makes thematic chages to your Payment Links.

> [card] [Changes Business Name](https://razorpay.com/docs/my/api/payments/payment-links/change-business-name.md)
>
> `POST` `/v1/payment_links`
>
> Changes your Business name.

> [card] [Customise Payment Methods (Example 1)](https://razorpay.com/docs/my/api/payments/payment-links/customise-payment-methods.md)
>
> `POST` `/v1/payment_links`
>
> Customises Payment Methods with the Options and Method Parameters.

> [card] [Customise Payment Methods (Example 2)](https://razorpay.com/docs/my/api/payments/payment-links/customise-options-config.md)
>
> `POST` `/v1/payment_links`
>
> Customises Payment Methods with the Options and Config Parameters.

> [card] [Rename Labels in the Checkout Section](https://razorpay.com/docs/my/api/payments/payment-links/rename-checkout-labels.md)
>
> `POST` `/v1/payment_links`
>
> Renames Labels in the Checkout Section.

> [card] [Rename Labels in Payment Details Section](https://razorpay.com/docs/my/api/payments/payment-links/rename-payment-details-labels.md)
>
> `POST` `/v1/payment_links`
>
> Renames Labels in the Payment details section.

## Related Guides

* [About Payment Links](https://razorpay.com/docs/my/payments/payment-links)
* [Set Up Webhooks](https://razorpay.com/docs/my/webhooks/setup-edit-payments.md)
* [Webhook Payloads](https://razorpay.com/docs/my/webhooks/payment-links.md)
