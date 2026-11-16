> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Transactions

> List of Transactions APIs to retrieve transactions.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Transactions are the records of inflow of funds to your business account, and payouts to a Contact's Fund Account and reversals. You can retrieve the details of a particular transaction or the details of all transactions using the Transactions APIs.

Fork the Razorpay Postman Public Workspace and try the Transactions APIs using your [Test API Keys](https://razorpay.com/docs/x/dashboard/api-keys.md).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-a9f166e4-bfee-48ae-bfc3-3a5baaa67f1c)

> [card] [Fetch All Transactions](https://razorpay.com/docs/api/x/transactions/fetch-all.md)
>
> `GET` `/v1/transactions?account_number=\{account number\}`
>
> Retrieves all the transactions made from your business account.

> [card] [Fetch a Transaction with ID](https://razorpay.com/docs/api/x/transactions/fetch-with-id.md)
>
> `GET` `/v1/transactions/:id`
>
> Retrieves a transaction using its ID.

## Related Guides

* [About Account Statement](https://razorpay.com/docs/x/account-statement)
* [Set Up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payouts.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/transactions.md)
