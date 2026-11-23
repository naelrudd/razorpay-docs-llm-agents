> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Settlements - Dashboard Actions

> View settlement details, check the settlements break-up, enable settlements on hold and view reports from the Razorpay Curlec Dashboard.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

## View Settlements Using Dashboard

You can view details of settlements made to you from the Dashboard.

* View a detailed break-down of the amount settled to you from the Dashboard.
* View details, such as the total settlement amount (credit + debit amount), applicable service fees, service tax, adjustments, and so on.

To view settlement details:

1. Log in to the Dashboard.
2. Navigate to **Settlements**.
3. Click on a **Settlement id** that you wish to refer to.

### View Settlements Using API

You can view settlement details using the [Settlements API](https://razorpay.com/docs/my/api/settlements.md).

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
: Fees deducted by Razorpay Curlec for the transactions.

## View Settlement Timeline on Dashboard

You can view the settlement timeline to check when the settlement for a particular payment will be credited.

To view the settlement timeline:

1. Log in to the Dashboard.

2. Navigate to **Transactions** and select **Payments** or **Refunds** depending on what you wish to view the settlement timeline for.

3. Select the payment id or the refund id you wish to check.

4. Click **View settlement timeline**.

5. Upon expanding the settlement timeline, you will be able to see the settlement schedule for that particular payment.

## Enable Settlements Placed On Hold

Your settlement can be placed on hold if we detect some risk with your payments or with your Razorpay Curlec account. You are notified about this on your Dashboard.

To enable settlements when they are put on hold:

1. Log in to the Dashboard.
2. Navigate to **Home**.
3. Click [**Contact Support**](https://curlec.com/support).

## Reports

Detailed insights can be gained using reports and real-time data on the Dashboard. These reports can then be used for accounting and reconciliation purposes. Know more about [reports.](https://razorpay.com/docs/my/payments/dashboard/reports.md)

### Related Information

* [About Settlements](https://razorpay.com/docs/my/payments/settlements)
* [Settlements API](https://razorpay.com/docs/my/payments/settlements/apis.md)
* [Settlement FAQs](https://razorpay.com/docs/my/payments/settlements/faqs.md)
