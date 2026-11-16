> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Balances

> Details about various balances available and how you can add funds and maintain them from the Razorpay Dashboard.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can add funds to your Current balance account on the Dashboard.

## Current Balance

After the deduction of fees and tax, the payments received from your customers are added to your **Merchant Balance** or **Current Balance**.

* This accumulated amount is settled to your bank account as per your settlement cycle.
* We use you Current balance to process chargebacks, refunds to your customers and settlements to your Linked accounts.

Always maintain sufficient Current balance in your account to ensure your transactions do not fail. Know [how to add balance](#add-funds-to-current-balance).

> [!WARNING]
>
> **Watch Out!**
>
> * Refunds processed using your Current balance incur no extra charges. We only deduct the refund amount.
> * Fees and taxes from the original transaction are not reversed in you refund. As a result, you refund amount can be lesser than the original transaction.

Negative Current Balance is when your Current balance becomes less than zero.

Consider the following cases of Negative balance, where a chargeback of S\$ 300 is applicable.

* If Opening balance is S$ 0, your Negative balance is -S$ 500 (due to 0-500).
* If Opening balance is S$ 300, your Negative balance is -S$ 200 (due to 300-500).

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
> For example, according to your pricing plan for a S$ 1,000 payment, the fees and tax is S$ 5. When you add S$ 1,000 to your current balance, S$ 5 (fees and tax) is deducted and S\$ 995 is added to your current balance.

**Example 1**

Let us say you have a Current balance of S\$ 1,000.

| Scenario | Current Balance |
| - | - |
| Opening balance | S\$\$ 1,000 |
| You receive and capture a payment of S$ 1,000.<br /><br />Let us assume we charge a fee of S$ 5 to process this transaction. | S$ 1995<br /><br />(S$ 1,000 + (S$ 1,000 - S$ 5)) |
| You process a full refund of S\$\$ 1,000 for the above payment. | S$ 995<br /><br />(S$ 1995 - S\$\$ 1,000) |

**Example 2**

Let us say you have a Current balance of S\$ 0.

| Scenario | Current Balance |
| - | - |
| Opening balance | S\$\$ 0 |
| You receive and capture a payment of S$ 1,000.<br /><br />Let us say a fee of S$ 5 is charged by us to process this transaction. | S$ 995<br /><br />(S$ 0 + (S$ 1,000 - S$ 5)) |
| You try to process a full refund of S\$\$ 1,000 for the above payment. | The refund fails since you do not have a sufficient Current balance. |

### Related Information

* [About Account and Settings](https://razorpay.com/docs/sg/payments/dashboard/account-settings.md)
* [About Dashboard](https://razorpay.com/docs/sg/payments/dashboard)
