> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Balance Threshold

> Proactively queue payouts before they fail due to low balance with Balance Threshold on RazorpayX.

Available in
🇮🇳 India

When you send payouts using the `queue_if_low_balance=true` parameter in the Payout API, payouts can still fail due to minor differences between the balance reflected on RazorpayX and the actual balance at the partner bank. This typically happens when you maintain your account balance close to the minimum required for your payout volume, and payouts are processed rapidly within a short span of time (payouts per minute).

Balance Threshold solves this by proactively queuing payouts before they are sent to the bank, preventing failures caused by these balance discrepancies.

### How Balance Threshold Works

You set a threshold amount (for example, ₹5,00,000) on your RazorpayX account. When a payout is initiated, the system checks if processing it would bring your balance below the threshold. If it would, the payout is queued instead of being sent to the bank.

The system evaluates the following condition for every payout:

If (`Current Balance − Payout Amount`) \< `Balance Threshold`, the payout is queued. It is then automatically processed once the balance rises above the threshold.

### Example

| Parameter | Value |
| - | - |
| Current Balance | ₹6,00,000 |
| Balance Threshold | ₹5,00,000 |
| Payout Amount | ₹1,50,000 |

In this example, `Current Balance − Payout Amount` is `₹6,00,000 − ₹1,50,000 = ₹4,50,000`
Since ₹4,50,000 \< ₹5,00,000 (Balance Threshold), the payout is queued. The payout will be automatically released when your account balance is refreshed and rises above the ₹5,00,000 threshold.

### Advantages

Balance Threshold works seamlessly with the existing `queue_if_low_balance=true` API parameter.

* The threshold is applied at the account level. All payouts from the account are evaluated against the configured threshold.
* Queued payouts are automatically released as your balance refreshes and rises above the threshold.
* Payouts are processed in a first-in-first-out (FIFO) order, consistent with the existing Queued Payouts behaviour.
* Any payout in the queued state for more than 3 months is automatically cancelled or rejected by the system, consistent with existing queued payout behaviour.

### How to Choose the Right Threshold Amount

#### Step 1: Know Your Per-Minute Payout Volume

Estimate how much money leaves your account every minute. Multiply the number of payouts you process per minute by the average amount of each payout. For example, if you typically process 10 payouts per minute and each payout is around ₹5,000, your per-minute volume is ₹50,000.

#### Step 2: Pick Your Comfort level

Multiply your per-minute volume by a safety multiplier based on how cautious you want to be:

* Play it safe (multiply by 15) — Best if payout failures are very costly for your business.
* Balanced approach (multiply by 10) — Works well for most businesses.
* Keep it lean (multiply by 5) — Suitable if you top up your account frequently and monitor closely.

#### Step 3: Choose Your Threshold

Using the example of ₹50,000 per-minute payout volume:

| Comfort Level | Calculation | Threshold Amount |
| - | - | - |
| Keep it lean | ₹50,000 × 5 | ₹2,50,000 |
| Balanced | ₹50,000 × 10 | ₹5,00,000 |
| Safest Option | ₹50,000 × 15 | ₹7,50,000 |

The higher the threshold, the fewer payout failures you are likely to experience — but you will need to maintain a higher balance in your account.

### Enable Balance Threshold

This is an on-demand feature. To get it activated on your RazorpayX account, please raise a request with our [Support team](https://razorpay.com/support/#request).

* Your RazorpayX account number.
* The Balance Threshold amount you want to configure.

### Related Information

* [Queued Payouts](https://razorpay.com/docs/x/payouts/queued.md)
* [Intelligent Payouts](https://razorpay.com/docs/x/payouts/intelligent-payouts.md)
* [Check Payout Status Details](https://razorpay.com/docs/x/payouts/status-details.md)
* [Enable Bank Downtime Alerts](https://razorpay.com/docs/x/payouts/downtimes.md)
