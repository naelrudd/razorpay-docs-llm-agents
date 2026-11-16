> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Smart Collect 2.0 APIs

> Integrate Smart Collect 2.0 using Razorpay APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Smart Collect is not available in Malaysia, Singapore.

Smart Collect 2.0, which is an upgraded version of [Smart Collect](https://razorpay.com/docs/sg/api/payments/smart-collect.md) , offers additional APIs which enables you to create Customer Identifiers with Bank Account and VPA Receiver, add VPA Receiver to existing Customer Identifier, and fetch payments made using UPI.

Open a Current account or an Escrow account to start using [Smart Collect 2.0](https://razorpay.com/docs/payments/smart-collect).

> [!NOTE]
>
> **Handy Tips**
>
> * **Smart Collect 2.0** offers all the existing functionalities of **Smart Collect** and uses the same **Smart Collect** API endpoints, in addition to the new APIs listed on this page.
>
> * Use [Smart Collect TPV](https://razorpay.com/docs/sg/api/payments/smart-collect-tpv.md)  APIs to **Add an Allowed Payer** or **Delete an Allowed Payer**

> [!WARNING]
>
> **Watch Out!**
>
> Bank account is mandatory to create a Customer Identifier. You cannot create a Customer Identifier using VPA (UPI) alone.

> [card] [Create Customer Identifier with VPA and Bank Account Receivers With Smart Collect 2.0](https://razorpay.com/docs/sg/api/payments/smart-collect-2/create-cust-id-bank-account-vpa.md)
>
> `POST` `/v1/virtual_accounts`
>
> Creates a Customer Identifier with VPA and Bank Account Receivers With Smart Collect 2.0.

> [card] [Add VPA Receiver to existing Customer Identifier With Smart Collect 2.0](https://razorpay.com/docs/sg/api/payments/smart-collect-2/add-receiver-vpa.md)
>
> `POST` `v1/virtual_accounts/:id/receivers`
>
> Adds a VPA Receiver to an existing Customer Identifier With Smart Collect 2.0.

> [card] [Fetch Payments Made Using UPI With Smart Collect 2.0](https://razorpay.com/docs/sg/api/payments/smart-collect-2/fetch-payments-upi.md)
>
> `GET` `/v1/payments/:id/upi_transfer`
>
> Retrieves payments made using UPI With Smart Collect 2.0.

> [card] [Create a Customer Identifier With Bank Account Receiver](https://razorpay.com/docs/sg/api/payments/smart-collect/create-cust-id-bank-account.md)
>
> `POST` `/v1/virtual_accounts`
>
> Creates a Customer Identifier with bank account receiver.

> [card] [Update a Customer Identifier](https://razorpay.com/docs/api/payments/smart-collect/update.md)
>
> `POST` `/v1/virtual_accounts/:id`
>
> Updates details of a Customer Identifier.

> [card] [Fetch a Customer Identifier Using ID](https://razorpay.com/docs/sg/api/payments/smart-collect/fetch-with-id.md)
>
> `GET` `/v1/virtual_accounts/:id`
>
> Retrieves details of a Customer Identifier using id.

> [card] [Fetch All Customer Identifiers](https://razorpay.com/docs/sg/api/payments/smart-collect/fetch-all.md)
>
> `GET` `/v1/virtual_accounts/`
>
> Retrieves details of all Customer Identifiers.

> [card] [Fetch Payments for a Customer Identifier](https://razorpay.com/docs/sg/api/payments/smart-collect/fetch-payments-cust-id.md)
>
> `GET` `/v1/virtual_accounts/:id/payments`
>
> Retrieves details of payments made against a particular Customer Identifier.

> [card] [Fetch Payments Made By Bank Transfer](https://razorpay.com/docs/sg/api/payments/smart-collect/fetch-payments-bank-transfer.md)
>
> `GET` `/v1/virtual_accounts/:id/payments`
>
> Retrieves details of a payment using bank transfer method.

> [card] [Fetch Payments Using UTR](https://razorpay.com/docs/sg/api/payments/smart-collect/fetch-payments-bank-transfer-utr.md)
>
> `GET` `/v1/payments?skip=0&count=25&va_transaction_id=:id&virtual_account=1`
>
> Retrieves details of a payment using bank transfer method via UTR.

> [card] [Close a Customer Identifier](https://razorpay.com/docs/sg/api/payments/smart-collect/close.md)
>
> `POST` `/v1/virtual_accounts/:id/close`
>
> Closes a Customer Identifier.

> [card] [Add VPA Receiver to existing Customer Identifier With Smart Collect 2.0](https://razorpay.com/docs/sg/api/payments/smart-collect-2/add-receiver-vpa.md)
>
> `POST` `v1/virtual_accounts/:id/receivers`
>
> Adds a VPA Receiver to an existing Customer Identifier With Smart Collect 2.0.

> [card] [Create Customer Identifier with VPA and Bank Account Receivers With Smart Collect 2.0](https://razorpay.com/docs/sg/api/payments/smart-collect-2/create-cust-id-bank-account-vpa.md)
>
> `POST` `/v1/virtual_accounts`
>
> Creates a Customer Identifier with VPA and Bank Account Receivers With Smart Collect 2.0.

> [card] [Fetch Payments Made Using UPI With Smart Collect 2.0](https://razorpay.com/docs/sg/api/payments/smart-collect-2/fetch-payments-upi.md)
>
> `GET` `/v1/payments/:id/upi_transfer`
>
> Retrieves payments made using UPI With Smart Collect 2.0.

## Related Guides

* [About Smart Collect 2.0](https://razorpay.com/docs/payments/smart-collect)
* [Set Up Webhooks](https://razorpay.com/docs/sg/webhooks/setup-edit-payments.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/smart-collect.md)
