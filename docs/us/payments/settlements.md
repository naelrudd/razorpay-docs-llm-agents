> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# About Settlements

> Check how Razorpay settles money received from your customers to your bank account- Settlement Cycle, Partial Settlements and Settlement States.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Settlement is the process in which the money received from your customers is settled in your bank account. Settlements for all payments are done in USD (US Dollar), irrespective of the currency in which the customer made the payment. Once  receives the amount, it is settled in your bank account after deducting fees.

#### Prerequisites

Following are some of the prerequisites for settlements of payments from customers to your bank account:

* Your account must be fully activated for payments to be settled to your bank account.
* The payment must be captured. Know more about [capturing payments](https://razorpay.com/docs/us/payments/payments/capture-settings.md).

## Settlement Cycle

We automatically settle captured payments to the bank account submitted and following our settlement cycle. The settlement cycle is subject to bank approval and can vary based on your business vertical, risk factors and so on.

> [!NOTE]
>
> **Handy Tips**
>
> Working days do not include the bank holidays.

## Partial Settlements

Razorpay initiates partial settlements when your amount that requires settlement exceeds your current live balance (when the settlement is scheduled). Razorpay accurately calculates the amount that requires settlement based on the live balance, ensuring that settlements are not skipped. When settling transactions, we will only choose the ones that add up to your current live balance.

This ensures that your settlements are timely and regular and you can maintain stable cash flow.

> [accordion] Example 1
>
> You captured a payment of USD 1000 on July 02, 2023, and your settlement schedule is T+2 days 5:00 p.m. Hence, the live balance is USD 1000, which will be the settlement amount.
>
> However, on July 02, 2023, you had to refund your customer USD 100. Due to this, your live balance is USD 900. As the current live balance is lesser than the settlement scheduled, Razorpay will initiate partial settlements and settle your current live balance of USD 900.

> [accordion] Example 2
>
> You captured three payments of P1 - USD 500, P2 - USD 300 and P3 - USD 200 on July 02, 2023, and your settlement schedule is T+2 days 5:00 p.m. Hence, the live balance is USD 1000, which will be the settlement amount.
>
> However, on July 02, 2023, you had to refund your customer USD 100. Due to this, your live balance is USD 900. As the current live balance is lesser than the settlement scheduled, Razorpay will initiate partial settlements and settle transactions P1 and P2 on T+2 as it adds upto USD 900. P3 will be scheduled for the next day, shown as an upcoming settlement, and paid in the next slot.

## Settlement States

Following are the various states of a settlement:

![Settlement Life Cycle flow](https://razorpay.com/docs/build/browser/assets/images/dashboard-guide-settlement_life_cycle.jpg)

Some reasons for settlement failure:

* Your bank account is inactive or frozen.
* Incorrect bank account details.
* The settlement was rejected by your bank.

## Dashboard Actions

You can perform the following actions from the Razorpay Dashboard:

* [View settlement details](https://razorpay.com/docs/us/payments/settlements/dashboard.md#view-settlements-using-dashboard)
* [Check settlements break-up](https://razorpay.com/docs/us/payments/settlements/dashboard.md#settlements-break-up-description)
* [Enable settlements on hold](https://razorpay.com/docs/us/payments/settlements/dashboard.md#enable-settlements-placed-on-hold)
* [View reports related to settlements](https://razorpay.com/docs/us/payments/settlements/dashboard.md#reports)

### Related Information

* [Settlements APIs](https://razorpay.com/docs/us/payments/settlements/apis.md)
* [Settlement FAQs](https://razorpay.com/docs/us/payments/settlements/faqs.md)
