> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Smart Collect

> Create Customer Identifiers on-demand for customers to pay via NEFT, RTGS and IMPS using Razorpay Smart Collect APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

You can create Customer Identifiers using the Smart Collect APIs to accept large payments from your customers in the form of bank transfers via NEFT, RTGS and IMPS.

> [!NOTE]
>
> **Handy Tips**
>
> * If you are a new customer, explore [Smart Collect 2.0](https://razorpay.com/docs/api/payments/smart-collect-2.md) . It uses the same APIs as **Smart Collect**, while also offering additional endpoints—such as creating a Customer Identifier with a VPA and bank account, fetching UPI payments, and adding a VPA Receiver to an existing Customer Identifier.
> * You can also **Add an Allowed Payer** or **Delete an Allowed Payer** using [Smart Collect TPV](https://razorpay.com/docs/api/payments/smart-collect-tpv.md)  APIs.

Fork the Razorpay Postman Public Workspace and try the Smart Collect APIs using your [Test API Keys](https://razorpay.com/docs/api/authentication.md#generate-api-keys).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-9fd01f11-0b59-4e97-a281-40f4b14277ec)

> [card] [Create a Customer Identifier With Bank Account Receiver](https://razorpay.com/docs/api/payments/smart-collect/create-cust-id-bank-account.md)
>
> `POST` `/v1/virtual_accounts`
>
> Creates a Customer Identifier with bank account receiver.

> [card] [Update a Customer Identifier](https://razorpay.com/docs/api/payments/smart-collect/update.md)
>
> `POST` `/v1/virtual_accounts/:id`
>
> Updates details of a Customer Identifier.

> [card] [Fetch a Customer Identifier Using ID](https://razorpay.com/docs/api/payments/smart-collect/fetch-with-id.md)
>
> `GET` `/v1/virtual_accounts/:id`
>
> Retrieves details of a Customer Identifier using id.

> [card] [Fetch All Customer Identifiers](https://razorpay.com/docs/api/payments/smart-collect/fetch-all.md)
>
> `GET` `/v1/virtual_accounts/`
>
> Retrieves details of all Customer Identifiers.

> [card] [Fetch Payments for a Customer Identifier](https://razorpay.com/docs/api/payments/smart-collect/fetch-payments-cust-id.md)
>
> `GET` `/v1/virtual_accounts/:id/payments`
>
> Retrieves details of payments made against a particular Customer Identifier.

> [card] [Fetch Payments Made By Bank Transfer](https://razorpay.com/docs/api/payments/smart-collect/fetch-payments-bank-transfer.md)
>
> `GET` `/v1/virtual_accounts/:id/payments`
>
> Retrieves details of a payment using bank transfer method.

> [card] [Fetch Payments Using UTR](https://razorpay.com/docs/api/payments/smart-collect/fetch-payments-bank-transfer-utr.md)
>
> `GET` `/v1/payments?skip=0&count=25&va_transaction_id=:id&virtual_account=1`
>
> Retrieves details of a payment using bank transfer method via UTR.

> [card] [Close a Customer Identifier](https://razorpay.com/docs/api/payments/smart-collect/close.md)
>
> `POST` `/v1/virtual_accounts/:id/close`
>
> Closes a Customer Identifier.

> [card] [Add VPA Receiver to existing Customer Identifier With Smart Collect 2.0](https://razorpay.com/docs/api/payments/smart-collect-2/add-receiver-vpa.md)
>
> `POST` `v1/virtual_accounts/:id/receivers`
>
> Adds a VPA Receiver to an existing Customer Identifier With Smart Collect 2.0.

> [card] [Create Customer Identifier with VPA and Bank Account Receivers With Smart Collect 2.0](https://razorpay.com/docs/api/payments/smart-collect-2/create-cust-id-bank-account-vpa.md)
>
> `POST` `/v1/virtual_accounts`
>
> Creates a Customer Identifier with VPA and Bank Account Receivers With Smart Collect 2.0.

> [card] [Fetch Payments Made Using UPI With Smart Collect 2.0](https://razorpay.com/docs/api/payments/smart-collect-2/fetch-payments-upi.md)
>
> `GET` `/v1/payments/:id/upi_transfer`
>
> Retrieves payments made using UPI With Smart Collect 2.0.

## Related Guides

* [About Smart Collect](https://razorpay.com/docs/payments/smart-collect)
* [Set Up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payments.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/smart-collect.md)
