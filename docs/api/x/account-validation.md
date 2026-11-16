> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Account Validation

> Overview of Account Validation for RazorpayX, APIs and webhook payload. Validate customer's bank account before you make payouts.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

[Account Validation](https://razorpay.com/docs/x/fund-account-validation.md) validates your Contact's Fund Account details (such as bank account or virtual payment address (VPA) details) to verify the account number where the user wants to receive the amount. Account Validation is not available in test mode and is possible only for RazorpayX Lite.

To make an account validation transaction, you must [allowlist your IPs](https://razorpay.com/docs/x/dashboard/allowlist-ip.md), [Create a Contact](https://razorpay.com/docs/api/x/account-validation/create-contact.md) and Create a Fund Account for the Contact using either [bank account](https://razorpay.com/docs/api/x/account-validation/bank-account/create-fund-account.md) or [VPA details](https://razorpay.com/docs/api/x/account-validation/vpa/create-fund-account.md).

Fork the Razorpay Postman Public Workspace and try the Account Validation APIs using your [Test API Keys](https://razorpay.com/docs/x/dashboard/api-keys.md).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-62befdac-a937-4ee9-8bc4-943801ce2368)

> [card] [Create Contact](https://razorpay.com/docs/api/x/account-validation/create-contact.md)
>
> `POST` `/v1/contacts`
>
> Creates a Contact using customer's contact details such a phone number or email id.

> [card] [Create a Fund Account of Type Bank Account](https://razorpay.com/docs/api/x/account-validation/bank-account/create-fund-account.md)
>
> `POST` `/v1/fund_accounts`
>
> Creates a Fund Account for an existing Contact using customer's bank account details.

> [card] [Validate a Bank Account](https://razorpay.com/docs/api/x/account-validation/bank-account.md)
>
> `POST` `/v1/fund_accounts/validations`
>
> Validates the contact's bank account.

> [card] [Create a Fund Account of Type VPA](https://razorpay.com/docs/api/x/account-validation/vpa/create-fund-account.md)
>
> `POST` `/v1/fund_accounts`
>
> Creates a Fund Account for an existing Contact using customer's virtual payment address or UPI.

> [card] [Validate a VPA](https://razorpay.com/docs/api/x/account-validation/vpa.md)
>
> `POST` `/v1/fund_accounts/validations`
>
> Validates the contact's virtual payment address or UPI fund account.

> [card] [Validate VPA using Reverse Penny Drop](https://razorpay.com/docs/api/x/account-validation/reverse-penny-drop.md)
>
> `POST` `/v1/fund_accounts/validations`
>
> Validates the contact's virtual payment address or UPI fund account via Reverse Penny Drop.

> [card] [Fetch All Account Validation Transactions](https://razorpay.com/docs/api/x/account-validation/fetch-all-transactions.md)
>
> `GET` `/v1/fund_accounts/validations?account_number=\{account number\}`
>
> Retrieves the details of all Fund Account Validation transactions you have made.

> [card] [Fetch Account Validation Transactions With ID](https://razorpay.com/docs/api/x/account-validation/fetch-transactions-with-id.md)
>
> `GET` `/v1/fund_accounts/validations/:id`
>
> Retrieves particular Fund Account Validation transaction with its id.

## Related Guides

* [About Fund Account Validation](https://razorpay.com/docs/x/fund-account-validation.md)
* [Set up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payouts.md)
* [Webhooks Payloads](https://razorpay.com/docs/webhooks/account-validation.md)
