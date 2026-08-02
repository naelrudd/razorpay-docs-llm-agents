# Payouts APIs

You can use the Razorpay's Payout APIs to perform various actions. You can perform most of these actions from the [RazorpayX Dashboard](https://x.razorpay.com/auth) as well.

**SUCCESS**

**What's New**

You can now initiate payouts directly to mobile numbers using the [Payout Composite API](https://razorpay.com/docs/build/llm-docs/api/x/payout-composite/create/phone-number.md)

**WARN**

**Watch Out!**

It is mandatory to [allowlist IPs](https://razorpay.com/docs/build/llm-docs/x/dashboard/allowlist-ip.md) and pass the [idempotency key](https://razorpay.com/docs/build/llm-docs/api/x/payout-idempotency/make-request.md) to make a successful payout.

## Payout APIs

The table below lists the various endpoints and gives a brief description of each:

API Endpoint | Description
---
[Creates a Payout to a Bank Account](https://razorpay.com/docs/build/llm-docs/api/x/payouts/create/bank-account.md) | Create a payout to a bank account.
---
[Create a Payout to a VPA](https://razorpay.com/docs/build/llm-docs/api/x/payouts/create/vpa.md) | Creates a payout to a VPA.
---
[Fetch a Payout with ID](https://razorpay.com/docs/build/llm-docs/api/x/payouts/fetch-with-id.md) | Retrieves details of one payout via ID.
---
[Fetch all Payouts](https://razorpay.com/docs/build/llm-docs/api/x/payouts/fetch-all.md) | Retrieves details of all the payouts.
---
[Cancel a Queued Payout](https://razorpay.com/docs/build/llm-docs/api/x/payouts/cancel.md) | Cancels a payout in `queued` state.

## Payout to Cards APIs

The table below lists the various endpoints and gives a brief description of each:

**WARN**

**Watch Out!**

Payouts via **Visa Direct** and **MasterCard Send** are temporarily unavailable. Please watch this space for further updates.

API Endpoint | Description
---
[Make Payouts to Cards without saving cards](https://razorpay.com/docs/build/llm-docs/api/x/payouts-cards/create/without-saving-card.md) | Make a payout to a card without saving card details.
---
[Create Fund Account](https://razorpay.com/docs/build/llm-docs/api/x/payouts-cards/create/save-card/external-token/fund-account.md) to make Payouts to Externally Tokenised Card | Creates a fund account for a tokenised card via external tokenisation providers.
---
[Make Payouts to Externally Tokenised Card](https://razorpay.com/docs/build/llm-docs/api/x/payouts-cards/create/save-card/external-token/payout.md) | Makes a payout to a tokenised card via external tokenisation providers.
---
[Create Fund Account](https://razorpay.com/docs/build/llm-docs/api/x/payouts-cards/create/save-card/razorpay-tokenhq/fund-account.md) to make Payouts to Tokenised Card with Razorpay TokenHQ | Creates a fund account for a tokenised card via via Razorpay Token HQ.
---
[Make Payouts to Tokenised Card with Razorpay TokenHQ](https://razorpay.com/docs/build/llm-docs/api/x/payouts-cards/create/save-card/razorpay-tokenhq/payout.md) | Makes a payout to a tokenised card via via Razorpay Token HQ.

## Payout Composite API

The table below lists the various endpoints and gives a brief description of each:

API Endpoint | Description
---
[Create a Composite Payout to Mobile Number](https://razorpay.com/docs/build/llm-docs/api/x/payout-composite/create/phone-number.md) | Creates a payout to a contact's mobile number.
---
[Create a Composite Payout to Bank Account](https://razorpay.com/docs/build/llm-docs/api/x/payout-composite/create/bank-account.md) | Creates a payout to a contact's bank account.
---
[Create a Composite Payout to VPA](https://razorpay.com/docs/build/llm-docs/api/x/payout-composite/create/vpa.md) | Creates a payout to a contact's VPA (UPI).
---
[Create a Composite Payout to Card](https://razorpay.com/docs/build/llm-docs/api/x/payout-composite/create/card.md) | Creates a payout to a contact's card.

## Payout Approval API

The table below lists the various endpoints and gives a brief description of each:

API Endpoint | Description
---
[Approve Payout](https://razorpay.com/docs/build/llm-docs/api/x/payouts-approval/approve.md) | Approves the payout.
---
[Reject Payout](https://razorpay.com/docs/build/llm-docs/api/x/payouts-approval/reject.md) | Rejects the payout.

## Payout Idempotency API

The table below lists the various endpoints and gives a brief description of each:

API Endpoint | Description
---
[Request Idempotent Payout](https://razorpay.com/docs/build/llm-docs/api/x/payout-idempotency/make-request.md) | Requests for an idempotent payout.

## Transactions APIs

The table below lists the various endpoints and gives a brief description of each:

API Endpoint | Description
---
[Fetch All Transactions](https://razorpay.com/docs/build/llm-docs/api/x/transactions/fetch-all.md) | Retrieves all the transactions made from your business account. 
---
[Fetch Transaction with ID](https://razorpay.com/docs/build/llm-docs/api/x/transactions/fetch-with-id.md) | Retrieves a particular transaction. 

## Payout Status Details

[Status details](https://razorpay.com/docs/build/llm-docs/errors/x/payout-status-details.md) are sent as part of the fetch payout API response and webhook payloads. It provides additional details about each payout status. A payout update webhook is sent every time an attribute in status details changes.

### Related Information

- [Payouts](https://razorpay.com/docs/build/llm-docs/x/payouts.md)
- [Fund Account APIs](https://razorpay.com/docs/build/llm-docs/x/fund-accounts/api.md)
- [Subscribe to Webhooks](https://razorpay.com/docs/build/llm-docs/x/apis/subscribe.md)
