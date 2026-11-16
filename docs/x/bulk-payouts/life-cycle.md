> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Bulk Payouts Life Cycle

> Check the statuses that Payouts follow when they are made using the Bulk Upload feature.

Available in
🇮🇳 India

A payout created using the Bulk Upload feature can have the following statuses during its life cycle:

* `pending`
* `scheduled`
* `processing`
* `processed`
* `reversed`
* `cancelled`
* `rejected`
* `failed`

![bulk payout life cycle](https://razorpay.com/docs/build/browser/assets/images/RZPX-scheduled_payout_life_cycle.jpg)

Know more about [payout life cycle and statuses](https://razorpay.com/docs/x/payouts/states-life-cycle.md).

> [!NOTE]
>
> **Handy Tips**
>
> * Payouts created using the Bulk Upload feature are not queued. In case of insufficient balance, the payouts will fail.
> * The `pending` and `rejected` statuses are available only if you have [Approval Workflow](https://razorpay.com/docs/x/manage-teams/approval-workflow.md) enabled on your account.

### Related Information

* [About Bulk Payouts](https://razorpay.com/docs/x/bulk-payouts.md)
* [Bulk Upload Status](https://razorpay.com/docs/x/bulk-payouts/uploads.md)
* [Bulk Upload Report](https://razorpay.com/docs/x/bulk-payouts/report.md)
