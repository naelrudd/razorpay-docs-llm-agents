> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# QR Codes

> API Documentation for Razorpay QR Codes. Create, Close and Fetch QR Codes using APIs. Check the various use cases and code samples.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

You can use Razorpay [QR Codes](https://razorpay.com/docs/payments/qr-codes) to create QR Codes and share them with customers to accept digital payments. You can create and manage QR Codes using APIs or from the [Dashboard](https://razorpay.com/docs/payments/qr-codes/create.md).\
\


Refer to the [QR Code Flow](https://razorpay.com/docs/payments/qr-codes/how-it-works.md) and [Integration Checklist](https://razorpay.com/docs/payments/qr-codes/apis.md#integration-checklist) before you begin integrating with the APIs for QR Codes.\
\


Fork the Razorpay Postman Public Workspace and try the QR Codes APIs using your [Test API Keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/f960539b-c56c-41e5-810b-63d2a89d447e/folder/12492020-90436eef-f17f-4bc1-9d13-b622a4270125)

> [card] [Create a Customer](https://razorpay.com/docs/api/customers/create.md)
>
> `POST` `/v1/customers`
>
> Creates a customer that you can optionally link when creating a Dynamic QR Code.

> [card] [Create a QR Code](https://razorpay.com/docs/api/qr-codes/create.md)
>
> `POST` `/v1/payments/qr_codes`
>
> Creates a QR Code.

> [card] [Close a QR Code](https://razorpay.com/docs/api/qr-codes/close.md)
>
> `POST` `/v1/payments/qr_codes/:id/close`
>
> Closes a QR Code.

> [card] [Fetch All QR Codes](https://razorpay.com/docs/api/qr-codes/fetch-all.md)
>
> `GET` `/v1/payments/qr_codes?count=2`
>
> Retrieves details of all QR Codes.

> [card] [Fetch a QR Code with ID](https://razorpay.com/docs/api/qr-codes/fetch-with-id.md)
>
> `GET` `/v1/payments/qr_codes/:id`
>
> Retrieves details of a specific QR Code using id.

> [card] [Fetch QR Codes for a Customer ID](https://razorpay.com/docs/api/qr-codes/fetch-customer-id.md)
>
> `GET` `/v1/payments/qr_codes?customer_id=\{customer_id\}`
>
> Retrieves QR Codes generated for a Customer id.

> [card] [Fetch QR Codes for a Payment ID](https://razorpay.com/docs/api/qr-codes/fetch-payment-id.md)
>
> `GET` `/v1/payments/qr_codes?payment_id=\{payment_id\}`
>
> Retrieves QR Codes by Payment id.

> [card] [Fetch Payments for a QR Code](https://razorpay.com/docs/api/qr-codes/fetch-payments.md)
>
> `GET` `/v1/payments/qr_codes/:id/payments`
>
> Retrieves payments made on a QR Code.

> [card] [Update a QR Code](https://razorpay.com/docs/api/qr-codes/update.md)
>
> `PATCH` `/v1/payments/qr_codes/:id/payments`
>
> Updates payments made on a QR Code.

> [card] [Refund Payments](https://razorpay.com/docs/api/refunds/create-normal.md)
>
> `POST` `/v1/payments/:id/refund`
>
> Creates a refund for a payment.

## Related Guides

* [About QR Codes](https://razorpay.com/docs/payments/qr-codes)
