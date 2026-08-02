# Intelligent Payouts

Intelligent Payouts detects downtimes or degradations at Razorpay's partner or beneficiary banks' side and prevents the money from being blocked for T+3 days. Downtimes refer to the time period when payouts underperform, leading to considerable delays in processing. 

Intelligent Payout feature also reduces the chances of payouts being [deemed success](https://razorpay.com/blog/business-banking/payout-processing-imps-upi-transactions-deemed-success-npci/). With this, we aim to streamline online transactions and ensure a smoother payout experience for you.

## How it Works

If the beneficiary or the partner bank experiences downtime after a payout is made, the payout enters a `queued` state.

**WARN**

**Watch Out!**

- Intelligent payouts is available by default for Current Account users. RazorpayX Lite users must consume `payout.failed` [webhook](https://razorpay.com/docs/build/llm-docs/webhooks.md#payout-failed) to enable Intelligent payouts.
- RazorpayX Lite is currently not available for new merchants. To set up a new RazorpayX account, refer to [Current Account](https://razorpay.com/docs/build/llm-docs/x/account-types/current-account.md).

- You receive a `payout.queued` webhook event to inform you of the `status_details`.
    - The reason is either `beneficiary_bank_down` or `gateway_degraded`.
- If the issue is resolved within the defined SLA, the payout is `processed`.
- If the issue is not resolved within the defined SLA, the payout is moved to the `failed` state and you receive `payout.failed` webhook event.
- You can choose to `cancel` payouts in `queued` state from the RazorpayX Dashboard or via API.

Know more about [Payout States and Life Cycle](https://razorpay.com/docs/build/llm-docs/x/payouts/states-life-cycle.md).

Entity | Default SLA | Supported Modes | Supported Account Type
---
Beneficiary Bank/ NPCI| 15 minutes | IMPS & NEFT | Current Account & RazorpayX Lite
---
Partner Bank | 60 minutes | IMPS, NEFT, RTGS & UPI | Current Account
---

You can customise the SLA by contacting our [Support Team](https://razorpay.com/docs/build/llm-docs/x/support.md#razorpayx-users).

### Related Information

- [Queued Payouts](https://razorpay.com/docs/build/llm-docs/x/payouts/queued.md)
- [Payout Status Details](https://razorpay.com/docs/build/llm-docs/errors/x/payout-status-details.md)
- [Webhooks](https://razorpay.com/docs/build/llm-docs/webhooks/setup-edit-payouts.md)
