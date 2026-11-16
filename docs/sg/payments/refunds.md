> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# About Refunds

> Initiate Normal and Instant Refund payments using Razorpay Dashboard and APIs for your customers.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

There could be situations when customers request a refund of the payments made for the products or services purchased or availed on your website or app.

> [!NOTE]
>
> **Customer Looking for Refund**
>
> If you are a customer looking for a refund, know about [customer refunds](https://razorpay.com/docs/sg/payments/customers/customer-refunds.md).

## Refund Types

Following are the various types of refunds that you can use to refund payments to your customers:

<ul>
  <li>[Normal Refund](https://razorpay.com/docs/sg/payments/refunds/normal.md)
  \
  Amount is refunded within 5-7 working days.</li>

  <li>[Batch Refund](https://razorpay.com/docs/payments/refunds/batch.md)
  \
  Issue refunds in bulk using an XLSX or CSV file. Once you upload a file, it is picked up for processing after 70 minutes. You can cancel a batch upload in the 70 minutes before it is picked up for processing.</li>
</ul>

## Dashboard Actions

You can perform the following actions on refunds from the Dashboard:

* [View Refunds](https://razorpay.com/docs/sg/payments/refunds/view.md)
* [Issue Refunds](https://razorpay.com/docs/sg/payments/refunds/issue.md)
* [View Settlement Details of a Refund](https://razorpay.com/docs/sg/payments/refunds/view.md#view-settlement-details-of-a-refund)
* [Subscribe to Webhook Events](https://razorpay.com/docs/sg/payments/refunds/subscribe-to-webhooks.md)

## Refund States

Following are the various states of a refund:

| States | Description |
| - | - |
| `processed` | This is the final state of the refund. |
| `failed` | A refund can attain the failed state in the following scenarios:<ul><li>Normal refunds are not possible for a payment which is more than 6 months old.</li><li>Instant refunds can sometimes fail because of customer's account or bank-related issues.</li></ul>A refund can attain the failed state in certain cases. For example, normal refunds are not possible for a payment which is more than 6 months old. |

> [!WARNING]
>
> **Watch Out!**
>
> Usually, Razorpay moves a refund to the `processed` state before receiving the ARN/RRN number from the Gateway. You can ensure that a refund moves to the `processed` state only after receiving confirmation from the Gateway by activating this feature on your account by [support request](https://razorpay.com/sg/support/#request).

## Handle Refund Chargeback

For the prevention of chargebacks, Razorpay only does **source refunds**. It means that money is refunded to the payment method that the customer used to make the payment. For example, if a credit card was used to make the payment, the refund is pushed to the same credit card.

## Reports

Detailed insights can be gained using reports and real-time data on the Dashboard. These reports can then be used for accounting and reconciliation purposes. Know more about [reports](https://razorpay.com/docs/sg/payments/dashboard/reports.md).

Understand [how the Refund process works](https://razorpay.com/docs/sg/payments/refunds/normal.md#how-normal-refunds-work).

### Related Information

* [Add funds to your account to process refunds (low account balance)](https://razorpay.com/docs/sg/payments/dashboard/account-settings/balances.md#add-funds-to-current-balance)
* [Handle refund errors](https://razorpay.com/docs/sg/payments/refunds/errors.md)
* [Refunds API](https://razorpay.com/docs/sg/payments/refunds/apis.md)
* [Refund Communication](https://razorpay.com/docs/sg/payments/refunds/communication.md)
* [Refunds FAQs](https://razorpay.com/docs/sg/payments/refunds/faqs.md)
