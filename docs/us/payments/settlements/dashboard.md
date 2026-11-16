> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Settlements - Dashboard Actions

> View settlement details, check the settlements break-up, enable settlements on hold and view reports from the Razorpay Dashboard.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

## View Settlements Using Dashboard

You can view details of settlements made to you from the Dashboard.

* View a detailed break-down of the amount settled to you from the Dashboard.
* View details, such as the total settlement amount (credit + debit amount), applicable service fees, service tax, adjustments, and so on.

### View Settlements Using API

You can view settlement details using the [Settlements API](https://razorpay.com/docs/api/settlements.md).

### Settlements Break-Up Description

| Transaction Details | Amount (SGD)(USD)(INR)(RM) |
| - | - |
| Payment | 18012.00 |
| Adjustment | 6.00 |
| Tax | 65.56 |
| Fee | 364.24 |
| Total amount settled in your account | 17576.20 |

A settlement has the following components:

`Payment`
: The total payment amount that is being settled before deductions.

`Adjustment`
: Adjustments to transactions, if any.

`Tax`
: Tax deducted on the payment.

`Fee`
: Fees deducted by Razorpay for the transactions.

## View Settlement Timeline on Dashboard

You can view the settlement timeline to check when the settlement for a particular payment will be credited.

To view the settlement timeline:

1. Log in to the Dashboard.
2. Navigate to **Settlements**.
3. Click on the **details** of the settlement id for which you want to view the timeline.
4. You will be able to see the settlement timeline for that particular settlement id.

## Enable Settlements Placed On Hold

Your settlement can be placed on hold if we detect some risk with your payments or with your Razorpay account. You are notified about this on your Dashboard.

Contact the [support team](https://razorpay.com/us/support/) to enable settlements that are placed on hold.

## Reports

Detailed insights can be gained using reports and real-time data on the Dashboard. These reports can then be used for accounting and reconciliation purposes. Know more about [reports.](https://razorpay.com/docs/us/payments/dashboard/reports.md)

### Related Information

* [About Settlements](https://razorpay.com/docs/us/payments/settlements)
* [Settlements API](https://razorpay.com/docs/us/payments/settlements/apis.md)
* [Settlement FAQs](https://razorpay.com/docs/us/payments/settlements/faqs.md)
