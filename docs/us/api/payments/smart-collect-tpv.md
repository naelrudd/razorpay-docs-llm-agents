> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Smart Collect With TPV

> Create and manage Customer Identifiers and fetch payment details using Razorpay **Smart Collect TPV** APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can create Customer Identifiers using the **Smart Collect** APIs to accept large payments from your customers in the form of bank transfers via NEFT, RTGS and IMPS. In addition, you can also  add an Allowed Payer or delete an Allowed payer using **Smart Collect TPV** APIs.

> [!NOTE]
>
> **Handy Tips**
>
> If you are a new customer, explore [Smart Collect 2.0](https://razorpay.com/docs/us/api/payments/smart-collect-2.md) . It uses the same APIs as **Smart Collect**, while also offering additional endpoints—such as creating a Customer Identifier with a VPA and bank account, fetching UPI payments, and adding a VPA Receiver to an existing Customer Identifier.

Fork the Razorpay Postman Public Workspace and try the Smart Collect with TPV APIs using your [Test API Keys](https://razorpay.com/docs/us/api/authentication.md#generate-api-keys).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-3ea069ae-e9fc-4778-b70b-193e0693e476)

> [card] [Create a Customer Identifier with TPV](https://razorpay.com/docs/us/api/payments/smart-collect-tpv/create.md)
>
> `POST` `/v1/virtual_accounts`
>
> Creates a Customer Identifier with bank account.

> [card] [Add an Allowed Payer With TPV](https://razorpay.com/docs/us/api/payments/smart-collect-tpv/add-allowed-payer.md)
>
> `POST` `/v1/virtual_accounts/:va_id/allowed_payers`
>
> Adds an allowed payer's account.

> [card] [Fetch a Customer Identifier Using id With TPV](https://razorpay.com/docs/us/api/payments/smart-collect-tpv/fetch-with-id.md)
>
> `GET` `/v1/virtual_accounts/:id`
>
> Retrieves details of a Customer Identifier with id.

> [card] [Fetch All Customer Identifiers With TPV](https://razorpay.com/docs/us/api/payments/smart-collect-tpv/fetch-all.md)
>
> `GET` `/v1/virtual_accounts`
>
> Retrieves details of all Customer Identifiers.

> [card] [Fetch Payments for a Customer Identifier With TPV](https://razorpay.com/docs/us/api/payments/smart-collect-tpv/fetch-payments.md)
>
> `GET` `/v1/virtual_accounts/:id/payments`
>
> Retrieves details of payments made against a particular Customer Identifier.

> [card] [Fetch Payment Details Using id and Transfer Method With TPV](https://razorpay.com/docs/us/api/payments/smart-collect-tpv/fetch-payment-id-transfer.md)
>
> `GET` `/v1/payments/:id/bank_transfer`
>
> Retrieves details of a payment using payment id and bank transfer method.

> [card] [Delete an Allowed Payer Account With TPV](https://razorpay.com/docs/us/api/payments/smart-collect-tpv/delete-allowed-payer.md)
>
> `DELETE` `/v1/virtual_accounts/:va_id/allowed_payers/:id`
>
> Deletes an allowed payer account.

## Related Guides

* [About Smart Collect](https://razorpay.com/docs/payments/smart-collect)
* [Set Up Webhooks](https://razorpay.com/docs/us/webhooks/setup-edit-payments.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/smart-collect.md)
