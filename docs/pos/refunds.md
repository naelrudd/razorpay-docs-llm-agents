> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# About Refunds

> Initiate refunds using Razorpay POS Dashboard and APIs for your customers.

Available in
🇮🇳 India

There could be situations when customers request a refund of the payments made for the products or services purchased or availed on your website or app.

> [!NOTE]
>
> **Customer Looking for Refund**
>
> If you are a customer looking for a refund, know about [customer refunds](https://razorpay.com/docs/payments/customers/customer-refunds.md).

## Refund Types

You can use [Normal Refunds](https://razorpay.com/docs/payments/refunds/normal.md) to refund payments to your customers. The amount is refunded within 5-7 working days.

## Dashboard Actions

You can perform the following actions on refunds from the Dashboard:

* [View Refunds](https://razorpay.com/docs/pos/refunds/view.md)
* [Issue Refunds](https://razorpay.com/docs/pos/refunds/issue.md)
* [View Settlement Details of a Refund](https://razorpay.com/docs/pos/refunds/view.md#view-settlement-details-of-a-refund)

## Refund States

Following are the various states of a refund:

| States | Description |
| - | - |
| `created` | This state indicates that the refund is initiated from Razorpay. This state will be displayed only on the Refunds API. |
| `processed` | This is the final state of the refund. |
| `failed` | A refund can attain the failed state in the following scenarios:<ul><li>Normal refunds are not possible for a payment that is more than 6 months old.</li><li>Instant refunds can sometimes fail because of the customer's account or bank-related issues.</li></ul> |

> [!WARNING]
>
> **Watch Out!**
>
> Usually, Razorpay moves a refund to the `processed` state before receiving the ARN/RRN number from the Gateway. You can ensure that a refund moves to the `processed` state only after receiving confirmation from the Gateway by activating this feature on your account by raising a [support request](https://razorpay.com/support/#request).

## Void

A void is a request to return the transaction amount to your customer **before** the payment is settled to your account. Use a void instead of a refund when you need to cancel a transaction on the same day, before settlement.

> [!NOTE]
>
> **Handy Tips**
>
> A void can only be issued for the full transaction amount. For partial amounts, or after a payment is settled, [issue a refund](https://razorpay.com/docs/pos/refunds/issue.md) instead.

For void transactions, the refund status and process remain the same as a regular refund. See [Handle Refund Errors](https://razorpay.com/docs/pos/refunds/errors.md#void-errors) for void-specific errors.

## Handle Refund Chargeback

For the prevention of chargebacks, Razorpay only does **source refunds**. It means that money is refunded to the payment method that the customer used to make the payment. For example, if a credit card was used to make the payment, the refund is pushed to the same credit card. Similarly, in the case of UPI payments, the refund is pushed to the VPA used while making the payment.

If a chargeback is received for an instantly refunded payment, the processed refund will have a **UTR (Unique Transfer Reference)** in the callback. This UTR appears against the **ARN (Application Reference Number)** parameter in the Refund entity. The UTR serves as proof of refund completed between you and Razorpay.

Additionally, Razorpay passes the **RRN (Razorpay Reference Number)** of the payment in the Fund Transfer Request sent for the refund. This ties the instant refund back to the parent payment, thereby, serving as proof of the refund. This data can also be used as a defense against a future chargeback or arbitration case.

## Reports

Detailed insights can be gained using reports and real-time data on the Dashboard. These reports can then be used for accounting and recon purposes. Know more about [reports](https://razorpay.com/docs/payments/dashboard/reports.md).

Understand [how the Refund process works](https://razorpay.com/docs/payments/refunds/normal.md#how-normal-refunds-work).

### Related Information

* [Handle refund errors](https://razorpay.com/docs/pos/refunds/errors.md)
* [Refunds API](https://razorpay.com/docs/pos/refunds/apis.md)
* [Refunds FAQs](https://razorpay.com/docs/pos/refunds/faqs.md)
