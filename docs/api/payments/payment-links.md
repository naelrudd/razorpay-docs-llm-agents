> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payment Links

> Create, update, delete, cancel, fetch and send Payment Links using Razorpay APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

[Payment Links](https://razorpay.com/docs/payments/payment-links) are URLs that you can send to your customers through SMS and email to collect payments from them. Customers can click on the URL, which opens the payment request page, and complete the payment using any of the available payment methods. You can create, fetch, edit or cancel Payment Links using APIs or from the [Dashboard](https://razorpay.com/docs/payments/refunds#dashboard-actions).

Fork the Razorpay Postman Public Workspace and try the Payment Links APIs using your [Test API Keys](https://razorpay.com/docs/api/authentication.md#generate-api-keys).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-a731e460-9f2d-4fa8-b149-3fc7df7983f5?ctx=documentation)

> [card] [Create a Standard Payment Link](https://razorpay.com/docs/api/payments/payment-links/create-standard.md)
>
> `POST` `/v1/payment_links`
>
> Creates a Standard Payment Link.

> [card] [Create a UPI Payment Link](https://razorpay.com/docs/api/payments/payment-links/create-upi.md)
>
> `POST` `/v1/payment_links`
>
> Creates a UPI Payment Link.

> [card] [Fetch All Standard Payment Links](https://razorpay.com/docs/api/payments/payment-links/fetch-all-standard.md)
>
> `GET` `/v1/payment_links`
>
> Retrieves data of all Standard Payment Links.

> [card] [Fetch All UPI Payment Links](https://razorpay.com/docs/api/payments/payment-links/fetch-all-upi.md)
>
> `GET` `/v1/payment_links`
>
> Retrieves data of all UPI Payment Links.

> [card] [Fetch a Standard Payment Link With ID](https://razorpay.com/docs/api/payments/payment-links/fetch-id-standard.md)
>
> `GET` `/v1/payment_links/:id`
>
> Retrieves data of a Standard Payment Link with id.

> [card] [Fetch a UPI Payment Link With ID](https://razorpay.com/docs/api/payments/payment-links/fetch-id-upi.md)
>
> `GET` `/v1/payment_links/:id`
>
> Retrieves data of a UPI Payment Link with id.

> [card] [Send or Resend Notifications](https://razorpay.com/docs/api/payments/payment-links/resend.md)
>
> `POST` `/v1/payment_links/:id/notify_by/:medium`
>
> Sends notifications to your customers.

> [card] [Update a Standard Payment Link](https://razorpay.com/docs/api/payments/payment-links/update-standard.md)
>
> `PATCH` `/v1/payment_links/:id`
>
> Updates the details of a Standard Payment Link.

> [card] [Update a UPI Payment Link](https://razorpay.com/docs/api/payments/payment-links/update-upi.md)
>
> `PATCH` `/v1/payment_links/:id`
>
> Updates the details of a UPI Payment Link.

> [card] [Cancel a Standard Payment Link](https://razorpay.com/docs/api/payments/payment-links/cancel-standard.md)
>
> `POST` `/v1/payment_links/:id/cancel`
>
> Cancels a Standard Payment Link.

> [card] [Cancel a UPI Payment Link](https://razorpay.com/docs/api/payments/payment-links/cancel-upi.md)
>
> `POST` `/v1/payment_links/:id/cancel`
>
> Cancels a UPI Payment Link.

> [card] [Implement Thematic Changes on Checkout](https://razorpay.com/docs/api/payments/payment-links/checkout-theme.md)
>
> `POST` `/v1/payment_links`
>
> Makes thematic chages to your Payment Links.

> [card] [Changes Business Name](https://razorpay.com/docs/api/payments/payment-links/change-business-name.md)
>
> `POST` `/v1/payment_links`
>
> Changes your Business name.

> [card] [Customise Payment Methods (Example 1)](https://razorpay.com/docs/api/payments/payment-links/customise-payment-methods.md)
>
> `POST` `/v1/payment_links`
>
> Customises Payment Methods with the Options and Method Parameters.

> [card] [Customise Payment Methods (Example 2)](https://razorpay.com/docs/api/payments/payment-links/customise-options-config.md)
>
> `POST` `/v1/payment_links`
>
> Customises Payment Methods with the Options and Config Parameters.

> [card] [Rename Labels in the Checkout Section](https://razorpay.com/docs/api/payments/payment-links/rename-checkout-labels.md)
>
> `POST` `/v1/payment_links`
>
> Renames Labels in the Checkout Section.

> [card] [Rename Labels in Payment Details Section](https://razorpay.com/docs/api/payments/payment-links/rename-payment-details-labels.md)
>
> `POST` `/v1/payment_links`
>
> Renames Labels in the Payment details section.

> [card] [Offers on Payment Links](https://razorpay.com/docs/api/payments/payment-links/offers.md)
>
> `POST` `/v1/payment_links`
>
> Helps you provide discount and cashback offers on Payment Links

> [card] [Manage Reminders for Payment Links](https://razorpay.com/docs/api/payments/payment-links/reminders)
>
> `POST` `/v1/payment_links`
>
> Helps you manage reminders on Payment Links.

> [card] [Transfer Payments Received Using Payment Links](https://razorpay.com/docs/api/payments/payment-links/transfer-payments.md)
>
> `POST` `/v1/payment_links`
>
> Helps you transfer payments received using Payment Links.

> [card] [Perform Third-Party Validation Using Payment Links](https://razorpay.com/docs/api/payments/payment-links/third-party-validation.md)
>
> `POST` `/v1/payment_links`
>
> Helps you perform Third-Party Validation using Payment Links.

## Related Guides

* [About Payment Links](https://razorpay.com/docs/payments/payment-links)
* [Set Up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payments.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/payment-links.md)
