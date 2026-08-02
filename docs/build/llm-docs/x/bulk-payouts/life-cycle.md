# Bulk Payouts Life Cycle

A payout created using the Bulk Upload feature can have the following statuses during its life cycle:

- `pending`
- `scheduled`
- `processing`
- `processed`
- `reversed`
- `cancelled`
- `rejected`
- `failed`

Know more about [payout life cycle and statuses](https://razorpay.com/docs/build/llm-docs/x/payouts/states-life-cycle.md).

**INFO**

**Handy Tips**

- Payouts created using the Bulk Upload feature are not queued. In case of insufficient balance, the payouts will fail.
- The `pending` and `rejected` statuses are available only if you have [Approval Workflow](https://razorpay.com/docs/build/llm-docs/x/manage-teams/approval-workflow.md) enabled on your account.

### Related Information

- [About Bulk Payouts](https://razorpay.com/docs/build/llm-docs/x/bulk-payouts.md)
- [Bulk Upload Status](https://razorpay.com/docs/build/llm-docs/x/bulk-payouts/uploads.md)
- [Bulk Upload Report](https://razorpay.com/docs/build/llm-docs/x/bulk-payouts/report.md)
