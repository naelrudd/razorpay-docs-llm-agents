> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fund Accounts

> List of Fund Accounts APIs to create, retrieve and activate Fund Accounts.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Every Contact has an associated Fund Account. When you [make payouts](https://razorpay.com/docs/x/payouts) to a Contact, they receive the amount in their Fund Account. Fund Accounts can be of [four types](https://razorpay.com/docs/x/fund-accounts#fund-account-types), and a Contact can have multiple Fund Accounts.  \
&#x20;\


You must [create a Contact](https://razorpay.com/docs/api/x/contacts/create.md) to create a Fund Account. We recommend you to create Contacts and Fund Accounts beforehand to improve the [payout processing time](https://razorpay.com/docs/x/payouts/status-details.md). When making payouts, ensure to [allowlist IPs](https://razorpay.com/docs/x/dashboard/allowlist-ip.md), else the request will fail. \
&#x20;\


Fork the Razorpay Postman Public Workspace and try the Fund Accounts APIs using your [Test API Keys](https://razorpay.com/docs/x/dashboard/api-keys.md).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-47aa8c0b-d897-48d2-aa5a-5d5c10c5c2b1)

> [card] [Create Bank Account type Fund Account](https://razorpay.com/docs/api/x/fund-accounts/create/bank-account.md)
>
> `POST` `/v1/fund_accounts`
>
> Creates a new Fund Account using bank account details.

> [card] [Create VPA type Fund Account](https://razorpay.com/docs/api/x/fund-accounts/create/vpa.md)
>
> `POST` `/v1/fund_accounts`
>
> Creates a new Fund Account using VPA details.

> [card] [Fetch All Fund Account](https://razorpay.com/docs/api/x/fund-accounts/fetch-all.md)
>
> `GET` `/v1/fund_accounts`
>
> Retrieves all the Fund Accounts.

> [card] [Fetch a Fund Account with ID](https://razorpay.com/docs/api/x/fund-accounts/fetch-with-id.md)
>
> `GET` `/v1/fund_accounts/:id`
>
> Retrieves a single Fund Account with ID.

> [card] [Activate/Deactivate a Fund Account](https://razorpay.com/docs/api/x/fund-accounts/activate-or-deactivate.md)
>
> `PATCH` `/v1/fund_accounts/:id`
>
> Activates or deactivates an existing Fund Account.

## Related Guides

* [About Fund Accounts](https://razorpay.com/docs/x/fund-accounts)
* [Set Up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payouts.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/account-validation.md)
