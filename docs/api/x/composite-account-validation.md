> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Account Validation Composite

> Composite Account Validation for RazorpayX, APIs and webhook payload. Validate your customers’ bank account or VPA with a single API before you make payouts.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Composite Account Validation API allows you to create a Contact [Linked Text](https://razorpay.com/docs/api/x/contacts/create.md), the contact's Fund Account (bank account or UPI) and validate it in a single API call.

> [!WARNING]
>
> **Watch Out!**
>
> Account Validation is not available in test mode and is possible only for RazorpayX Lite.

To make an account validation transaction, you must [allowlist your IPs](https://razorpay.com/docs/x/dashboard/allowlist-ip.md), [Create a Contact](https://razorpay.com/docs/api/x/account-validation/create-contact.md) and Create a Fund Account for the Contact using either [bank account](https://razorpay.com/docs/api/x/account-validation/bank-account/create-fund-account.md) or [VPA details](https://razorpay.com/docs/api/x/account-validation/vpa/create-fund-account.md).

> [card] [Validate a Bank Account](https://razorpay.com/docs/api/x/composite-account-validation/bank-account.md)
>
> `POST` `/v1/fund_accounts/validations`
>
> Creates and validates the contact's bank account.

> [card] [Validate a VPA](https://razorpay.com/docs/api/x/composite-account-validation/vpa.md)
>
> `POST` `/v1/fund_accounts/validations`
>
> Creates and validates the contact's virtual payment address or UPI fund account.

> [card] [Fetch All Account Validation Transactions](https://razorpay.com/docs/api/x/composite-account-validation/fetch-all-transactions.md)
>
> `GET` `/v1/fund_accounts/validations?account_number=\{account number\}`
>
> Retrieves the details of all Fund Account Validation transactions you have made.

> [card] [Fetch Account Validation Transactions With ID](https://razorpay.com/docs/api/x/composite-account-validation/fetch-transactions-with-id.md)
>
> `GET` `/v1/fund_accounts/validations/:id`
>
> Retrieves particular Fund Account Validation transaction with its id.

## Related Guides

* [About Fund Account Validation](https://razorpay.com/docs/x/fund-account-validation.md)
* [Set up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payouts.md)
* [Webhooks Payloads](https://razorpay.com/docs/webhooks/account-validation.md)
