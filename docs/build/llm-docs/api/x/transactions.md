# Transactions

Transactions are the records of inflow of funds to your business account, and payouts to a Contact's Fund Account and reversals. You can retrieve the details of a particular transaction or the details of all transactions using the Transactions APIs.

Fork the Razorpay Postman Public Workspace and try the Transactions APIs using your [Test API Keys](https://razorpay.com/docs/build/llm-docs/x/dashboard/api-keys.md). 

[](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-a9f166e4-bfee-48ae-bfc3-3a5baaa67f1c)

### Related Guides
 
[About Account Statement](https://razorpay.com/docs/build/llm-docs/x/account-statement.md)
[Set Up Webhooks](https://razorpay.com/docs/build/llm-docs/webhooks/setup-edit-payouts.md)
[Webhook Payloads](https://razorpay.com/docs/build/llm-docs/webhooks/transactions.md)

### Endpoints

- **get** `/v1/transactions?account_number=\{account number\}` - Fetch All Transactions: 
Retrieves all the transactions made from your business account.

- **get** `/v1/transactions/:id` - Fetch a Transaction with ID: 
Retrieves a transaction using its ID.
