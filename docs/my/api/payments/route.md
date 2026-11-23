> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Route

> Use Route to create APIs for Linked Accounts, Stakeholders, Product Configuration and Stakeholders.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

You should create a linked account to integrate Route and start transferring payments to vendors.\
\


Below are the steps to integrate Route. You can also refer to our comprehensive [Route Integration guide](https://razorpay.com/docs/my/payments/route/integration-guide.md).

1. [Create a Linked Account](https://razorpay.com/docs/my/api/payments/route/create-linked-account.md)
2. [Create a Stakeholder](https://razorpay.com/docs/my/api/payments/route/create-stakeholder.md)
3. [Request a Product Configuration](https://razorpay.com/docs/my/api/payments/route/request-product-config.md)
4. [Update a Product Configuration](https://razorpay.com/docs/my/api/payments/route/update-product-config.md)
5. Transfer funds to Linked Accounts using [Orders](https://razorpay.com/docs/my/api/payments/route/create-transfers-orders.md), [Payments](https://razorpay.com/docs/my/api/payments/route/create-transfers-payments.md) or [Direct Transfer](https://razorpay.com/docs/my/api/payments/route/direct-transfers.md) methods.\
   \


Fork the Razorpay Postman Public Workspace and try the Linked Account APIs using your [Test API Keys](https://razorpay.com/docs/my/api/authentication.md#generate-api-keys).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-ee29e3a3-f06a-464c-b9f2-03a20e875591)

> [card] [Create a Linked Account](https://razorpay.com/docs/my/api/payments/route/create-linked-account.md)
>
> `POST` `/v2/accounts`
>
> Creates a Linked Account.

> [card] [Update a Linked Account](https://razorpay.com/docs/my/api/payments/route/update-linked-accounts.md)
>
> `PATCH` `/v2/accounts/:account_id`
>
> Updates a Linked Account.

> [card] [Fetch a Linked Account With ID](https://razorpay.com/docs/my/api/payments/route/fetch-with-id.md)
>
> `GET` `/v2/accounts/:account_id`
>
> Fetches a Linked Account using a unique identifier.

> [card] [Create a Stakeholder](https://razorpay.com/docs/my/api/payments/route/create-stakeholder.md)
>
> `POST` `/v2/accounts/:account_id/stakeholders`
>
> Creates a Stakeholder.

> [card] [Update a Stakeholder Account](https://razorpay.com/docs/my/api/payments/route/update-stakeholder.md)
>
> `PATCH` `/v2/accounts/:account_id/stakeholders/:stakeholder_id`
>
> Updates a Stakeholder account.

> [card] [Request a Product Configuration](https://razorpay.com/docs/my/api/payments/route/request-product-config.md)
>
> `POST` `/v2/accounts/:account_id/products`
>
> Requests a product configuration.

> [card] [Update a Product Configuration](https://razorpay.com/docs/my/api/payments/route/update-product-config.md)
>
> `PATCH` `/v2/accounts/:account_id/products/:product_id`
>
> Updates a product configuration.

> [card] [Fetch a Product Configuration](https://razorpay.com/docs/my/api/payments/route/fetch-product-config.md)
>
> `GET` `/v2/accounts/:account_id/products/:product_id`
>
> Fetches a product configuration.

> [card] [Create Transfers from Orders](https://razorpay.com/docs/my/api/payments/route/create-transfers-orders.md)
>
> `POST` `/v1/orders`
>
> Creates Transfers from orders.

> [card] [Create Transfers from Payments](https://razorpay.com/docs/my/api/payments/route/create-transfers-payments.md)
>
> `POST` `/v1/payments/:id/transfers`
>
> Creates Transfers to Linked Accounts once the payments are captured.

> [card] [Direct Transfers](https://razorpay.com/docs/my/api/payments/route/direct-transfers.md)
>
> `POST` `/v1/transfers`
>
> Transfers funds directly from your account balance to the Linked Accounts.

> [card] [Create a Direct Transfer (Idempotent Request)](https://razorpay.com/docs/my/api/payments/route/direct-transfers-idempotent-request.md)
>
> `POST` `/v1/transfers`
>
> Transfers funds directly from your account balance to the Linked Accounts.

> [card] [Fetch Transfers for a Payment](https://razorpay.com/docs/my/api/payments/route/fetch-transfers-payment.md)
>
> `GET` `/v1/payments/:id/transfers`
>
> Fetches transfers created for a specific payment.

> [card] [Fetch Transfer for an Order](https://razorpay.com/docs/my/api/payments/route/fetch-transfer-order.md)
>
> `GET` `/v1/orders/:id/?expand[]=transfers&status=processing`
>
> Fetches transfers created for a specific order.

> [card] [Fetch a Transfer With ID](https://razorpay.com/docs/my/api/payments/route/fetch-a-transfer.md)
>
> `GET` `/v1/transfers/:id`
>
> Displays specific transfer details.

> [card] [Fetch Transfers for a Settlement](https://razorpay.com/docs/my/api/payments/route/fetch-transfers-for-a-settlement.md)
>
> `GET` `/v1/transfers?recipient_settlement_id=:id`
>
> Retrieves the collection of transfers created for a particular Settlement ID.

> [card] [Fetch Settlement Details](https://razorpay.com/docs/my/api/payments/route/fetch-settlement-details.md)
>
> `GET` `/v1/transfers?expand[]=recipient_settlement`
>
> Displays the details of settlements made to Linked Accounts.

> [card] [Fetch Payments of a Linked Account](https://razorpay.com/docs/my/api/payments/route/fetch-payments-linked-account.md)
>
> `GET` `/v1/payments/`
>
> Displays all the payments received by a Linked Account.

> [card] [Refund Payments and Reverse Transfer from a Linked Account](https://razorpay.com/docs/my/api/payments/route/refund-payments-and-reverse-transfer.md)
>
> `POST` `/v1/payments/:id/refund`
>
> Initiates a payment refund to a customer.

> [card] [Reverse a Transfer](https://razorpay.com/docs/my/api/payments/route/reverse-a-transfer.md)
>
> `POST` `/v1/transfers/:id/reversals`
>
> Initiates a reversal of funds from the Linked Account to your account.

> [card] [Fetch Reversals for a Transfer](https://razorpay.com/docs/my/api/payments/route/fetch-reversals.md)
>
> `GET` `/v1/transfers/:id/reversals`
>
> Fetches reversals for a Transfer.

> [card] Modify Settlement Hold for Transfers
>
> `PATCH` `/v1/transfers/:id`
>
> Modifies the settlement configuration for a particular transfer id.

## Related Guides

* [About Linked Accounts](https://razorpay.com/docs/my/payments/route/linked-account.md)
* [About Route](https://razorpay.com/docs/my/payments/route)
* [Integrate With Route](https://razorpay.com/docs/my/payments/route/integration-guide.md)
