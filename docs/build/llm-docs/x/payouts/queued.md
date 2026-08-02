# Queued Payouts

When you do not have sufficient balance to process a payout, we queue the payout instead of failing the payout, saving you time and effort.

Payouts that are queued get processed when you add funds to your account. Know more about [adding funds to your RazorpayX account](https://razorpay.com/docs/build/llm-docs/x/account-types/current-account.md#add-funds).

**WARN**

**Watch Out!**

Any payout in `queued` state for more than 3 months will automatically be `cancelled`/`rejected` by the system.

## Queued Payouts Processing

**INFO**

**Handy Tips**

- This feature is available to you by default. You do not need to do anything to enable the feature.
- A payout is queued only when there is insufficient funds to process the payout. You cannot use this feature to schedule a payout. If you want to schedule your payouts, use [Scheduled payouts](https://razorpay.com/docs/build/llm-docs/x/payouts/scheduled.md).

### Payout Processing - Order

Queued payouts are processed in a first-in-first-out (FIFO) basis. If a payout cannot be processed due to insufficient balance, Razorpay attempts to process the next payout in the queue.

Account Balance | Action | Payout Status
---
₹5,000 | Create 3 payouts:
-  Payout A → ₹6,000

-  Payout B → ₹3,000

-  Payout C → ₹5,000
 | -  Payout A → queued( insufficient balance). Account balance → ₹5,000. 
-  Payout B → processed. Account balance → ₹2,000.
-  Payout C → queued( insufficient balance). Account balance → ₹2,000.

### Payout Life Cycle

Once a payout is queued, it can have the following statuses during its life cycle:

- `queued`
- `processing`
- `processed`
- `reversed`
- `cancelled`
- `failed`

**INFO**

**Handy Tips**

The `Pending` and `Rejected` states are available only if you have [Approval Workflow](https://razorpay.com/docs/build/llm-docs/x/manage-teams/approval-workflow.md) enabled on your account.

### Cancel a Queued Payout Using API

You can cancel a queued payout using the [Cancel a Queued Payout API](https://razorpay.com/docs/build/llm-docs/api/x/payouts/cancel.md).

### Related Information

- [Payout Life Cycle and States](https://razorpay.com/docs/build/llm-docs/x/payouts/states-life-cycle.md)
- [Intelligent Payouts](https://razorpay.com/docs/build/llm-docs/x/payouts/intelligent-payouts.md)
- [Payouts to Cards](https://razorpay.com/docs/build/llm-docs/x/payouts/cards.md)
- [Payout Status Details](https://razorpay.com/docs/build/llm-docs/errors/x/payout-status-details.md)
- [Payout Best Practices](https://razorpay.com/docs/build/llm-docs/x/payouts/best-practices.md)
