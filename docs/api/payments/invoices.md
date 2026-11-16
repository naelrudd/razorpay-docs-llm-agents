> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Invoices

> Create, update, delete, cancel, fetch and send Invoices using Razorpay APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia

You can use [Razorpay Invoices](https://razorpay.com/docs/payments/invoices) to send invoices to your customers and accept payments instantly. The invoice contains information regarding the sale such as the name of the invoiced products or services, quantity, billing cycle, price breakup, receipt number and customer information.

You can create and manage Invoices using APIs or from the [Dashboard](https://razorpay.com/docs/payments/invoices/create.md#create-an-invoice-from-dashboard).

> [!NOTE]
>
> **Handy Tips**
>
> You can only create non-GST Invoices via APIs. Non-GST invoices can be created in any of the [supported international currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies). You cannot add tax rates for invoices created using international currencies.

Fork the Razorpay Postman Public Workspace and try the invoices APIs using your [Test API Keys](https://razorpay.com/docs/api/authentication.md#generate-api-keys).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-6109230d-794c-4a01-b982-4d8479afee53)

> [card] [Create an Invoice (Example 1)](https://razorpay.com/docs/api/payments/invoices/create-with-customer-id.md)
>
> `POST` `/v1/invoices`
>
> Creates an Invoice using a Customer id.

> [card] [Create an Invoice (Example 2)](https://razorpay.com/docs/api/payments/invoices/create-with-details.md)
>
> `POST` `/v1/invoices`
>
> Creates an Invoice using customer details such as name and billing details.

> [card] [Update an Invoice](https://razorpay.com/docs/api/payments/invoices/update.md)
>
> `PATCH` `/v1/invoices/:id`
>
> Updates an Invoice.

> [card] [Issue an Invoice](https://razorpay.com/docs/api/payments/invoices/issue.md)
>
> `POST` `/v1/invoices/:id/issue`
>
> Issues an Invoice.

> [card] [Delete an Invoice](https://razorpay.com/docs/api/payments/invoices/delete.md)
>
> `DELETE` `/v1/invoices/:id`
>
> Deletes an Invoice.

> [card] [Cancel an Invoice](https://razorpay.com/docs/api/payments/invoices/cancel.md)
>
> `POST` `/v1/invoices/:id/cancel`
>
> Cancels an Invoice.

> [card] [Fetch an Invoice With ID](https://razorpay.com/docs/api/payments/invoices/fetch-with-id.md)
>
> `GET` `/v1/invoices/:id`
>
> Retrieves details of a particular Invoice using id.

> [card] [Fetch All Invoices](https://razorpay.com/docs/api/payments/invoices/fetch-all.md)
>
> `GET` `/v1/invoices`
>
> Retrieves details of all Invoices.

> [card] [Send Notifications](https://razorpay.com/docs/api/payments/invoices/resend.md)
>
> `POST` `/v1/invoices/:id/notify_by/:medium`
>
> Sends notifications to customers.

> [card] [Create an Item](https://razorpay.com/docs/api/payments/invoices/create-item.md)
>
> `POST` `/v1/items`
>
> Creates an item by providing basic details such as name and amount.

> [card] [Fetch an Item With ID](https://razorpay.com/docs/api/payments/invoices/fetch-with-id-item.md)
>
> `GET` `/v1/items/:id`
>
> Retrieves details an item by id.

> [card] [Fetch All Items](https://razorpay.com/docs/api/payments/invoices/fetch-all-items.md)
>
> `GET` `/v1/items`
>
> Retrieves details of multiple items.

> [card] [Update an Item](https://razorpay.com/docs/api/payments/invoices/update-item.md)
>
> `PATCH` `/v1/items/:id`
>
> Updates the details of an item.

> [card] [Delete an Item](https://razorpay.com/docs/api/payments/invoices/delete-item.md)
>
> `DELETE` `/v1/items/:id`
>
> Deletes an item.

## Related Guides

* [About Invoices](https://razorpay.com/docs/payments/invoices)
* [Set Up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payments.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/invoices.md)
