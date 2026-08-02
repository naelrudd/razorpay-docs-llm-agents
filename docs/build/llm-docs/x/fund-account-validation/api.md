# Account Validation APIs

To make a [payout](https://razorpay.com/docs/build/llm-docs/x/payouts.md) to a Contact, you must: 
1. Create a Contact. 
1. Add a Fund account to the Contact. 
1. Validate the Contact's Fund account. 
1. Make payouts.

You can validate your Contact's Fund account/s using the following Validation APIs.  

**WARN**

**Watch Out!**

You must [allowlist your IPs](https://razorpay.com/docs/build/llm-docs/x/dashboard/allowlist-ip.md) to use the Account Validation APIs.

## Account Validation APIs 

Account Validation APIs validate previously created Contact's Fund accounts. You can create a Contact and Fund Account from the [RazorpayX Dashboard](https://x.razorpay.com/auth) or using the APIs.

The table below lists the various endpoints and gives a brief description of each:

API Endpoint | Description
---
[Create a Contact](https://razorpay.com/docs/build/llm-docs/api/x/account-validation/create-contact.md) | Creates a Contact. 
---
[Create Fund account (Bank account)](https://razorpay.com/docs/build/llm-docs/api/x/account-validation/bank-account/create-fund-account.md) | Creates a [Fund account of the type bank account](https://razorpay.com/docs/build/llm-docs/x/fund-accounts.md#fund-account-types). 
---
[Validate a Bank Account](https://razorpay.com/docs/build/llm-docs/api/x/account-validation/bank-account.md) | Validates the Contact's bank account information. 
---
[Create Fund account (VPA)](https://razorpay.com/docs/build/llm-docs/api/x/account-validation/vpa/create-fund-account.md) | Creates a [Fund account of the type VPA](https://razorpay.com/docs/build/llm-docs/x/fund-accounts.md#fund-account-types). 
---
[Validate a VPA](https://razorpay.com/docs/build/llm-docs/api/x/account-validation/vpa.md) | Validate the Contact's Virtual Payment Address (VPA)/UPI account information.
---
[Validate VPA using Reverse Penny Drop](https://razorpay.com/docs/build/llm-docs/api/x/account-validation/reverse-penny-drop.md) | Validate a bank account using Reverse Penny Drop
---
[Fetch all Account Validation Transactions](https://razorpay.com/docs/build/llm-docs/api/x/account-validation/fetch-all-transactions.md) | Retrieves all account validation transactions.
---
[Fetch an Account Validation Transaction with ID](https://razorpay.com/docs/build/llm-docs/api/x/account-validation/fetch-transactions-with-id.md) | Retrieves a single account validation transaction with ID.
---

## Composite Account Validation APIs

With Composite Account Validation, you can use a single API to perform all the actions at once, including account validation. This is useful to create new Contacts and Fund accounts immediately. You can create a Contact and Fund Account from the [RazorpayX Dashboard](https://x.razorpay.com/auth) as well.

The table below lists the various endpoints and gives a brief description of each:

API Endpoint | Description
---
[Validate a Bank Account](https://razorpay.com/docs/build/llm-docs/api/x/composite-account-validation/bank-account.md) | Create Contact, Fund Account with bank details and Validate the Contact's bank account information in a single API call.
---
[Validate a VPA](https://razorpay.com/docs/build/llm-docs/api/x/composite-account-validation/vpa.md) | Create Contact, Fund Account with VPA and Validate the Contact's bank account information in a single API call.
---
[Fetch all Account Validation Transactions](https://razorpay.com/docs/build/llm-docs/api/x/composite-account-validation/fetch-all-transactions.md) | Retrieves all account validation transactions.
---
[Fetch an Account Validation Transaction with ID](https://razorpay.com/docs/build/llm-docs/api/x/composite-account-validation/fetch-transactions-with-id.md) | Retrieves a single account validation transaction with ID.
---

### Related Information

- [Fund Account Validation](https://razorpay.com/docs/build/llm-docs/x/fund-account-validation.md)
- [Subscribe to Webhooks](https://razorpay.com/docs/build/llm-docs/x/apis/subscribe.md)
