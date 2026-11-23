> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Balances

> Details about various balances available and how you can add funds and maintain them from the Razorpay Curlec Dashboard.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can add funds to your Current Balance account on the Dashboard.

## Current Balance

After the deduction of fees and tax, the payments received from your customers are added to your **Merchant Balance** or **Current Balance**.

* This accumulated amount is settled to your bank account as per your settlement cycle.
* We use you Current balance to process chargebacks, refunds to your customers and settlements to your linked accounts.

Always maintain sufficient current balance in your account to ensure your transactions do not fail. Know [how to add balance](#add-funds-to-current-balance).

> [!WARNING]
>
> **Watch Out!**
>
> * Refunds processed using your Current balance incur no extra charges. We only deduct the refund amount.
> * Fees and taxes from the original transaction are not reversed in you refund. As a result, you refund amount can be lesser than the original transaction.

### Negative Current Balance

Negative Current balance is when your Current balance becomes less than zero.

Consider the following example of Negative balance, where a chargeback of RM 300 is applicable.

* If opening balance is RM 0, your Negative balance is -RM 500 (due to 0-500).
* If opening balance is RM 300, your Negative balance is -RM 200 (due to 300-500).

Because Negative balance impacts your customer satisfaction, ensure you maintain sufficient Current balance.

## Add Funds to Current Balance

To add funds to your Current balance:

1. Log in to the Dashboard.
2. Navigate to **Account & Settings** and click **Balances** under **Payments and refunds** section.
3. Click **Add Funds** in the Current Balance section and follow the on-screen instructions.

> [!NOTE]
>
> **Handy Tips**
>
> When you add funds to your Current balance, fees and tax are deducted and the remaining amount is added to your Current balance. The fees and tax charged are the same as what is charged on payments received from customers.
>
> For example, according to your pricing plan for an RM 1,000 payment, the fees and tax is RM 5. When you add RM 1,000 to your current balance, RM 5 (fees and tax) is deducted and RM 995 is added to your current balance.

**Example 1**

Let us say you have a Current balance of RM 1,000.

| Scenario | Current Balance |
| - | - |
| Opening balance | RM 1,000 |
| You receive and capture a payment of RM 1,000. Let us assume we charge a fee of RM 5 to process this transaction. | RM 1995 (RM 1,000 + (RM 1,000 - RM 5)) |
| You process a full refund of RM 1,000 for the above payment. | RM 995 (RM 1995 - RM 1,000) |

**Example 2**

Let us say you have a Current balance of RM 0.

| Scenario | Current Balance |
| - | - |
| Opening balance | RM 0 |
| You receive and capture a payment of RM 1,000. Let us say a fee of RM 5 is charged by us to process this transaction. | RM 995 (RM 0 + (RM 1,000 - RM 5)) |
| You try to process a full refund of RM 1,000 for the above payment. | The refund fails since you do not have a sufficient Current balance. |

### Related Information

* [About Account and Settings](https://razorpay.com/docs/my/payments/dashboard/account-settings.md)
* [About Dashboard](https://razorpay.com/docs/my/payments/dashboard)
