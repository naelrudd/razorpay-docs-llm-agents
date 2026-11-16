> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Normal Refunds

> Check how to issue Normal Refunds to your customers, the refund process, processing time and refund fees.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can issue Normal refunds to your customers which are processed within 7-10 working days.

> [!NOTE]
>
> **Customer Looking for Refund**
>
> If you are a customer looking for a refund, know more about [customer refunds](https://razorpay.com/docs/payments/customers/customer-refunds.md).

## How Normal Refunds Work

When you make a Normal refund request to Razorpay, the information is sent to banking partners or other related stakeholders. Each of them have their own process for refund requests. After processing the refund request, the refund amount is sent to the customer's bank account or card balance.

Following is a typical flow for card refunds:

![Normal Refund Flow](https://razorpay.com/docs/build/browser/assets/images/normal-refund-flow.jpg)

### Payment Methods

We support all payment methods for Normal refunds.

Refunds are sent back to the original payment method used in making the payment. For example, if a credit card was used to make the payment, the refund amount is pushed to the same credit card.

### Processing Time

When you send a Normal refund request to Razorpay, the information is sent to our banking partners. Depending on the bank's processing time, it can take 7-10 business days for the refunds to reflect in the customer's bank account or card balance.

The time taken to process a normal refund depends on the payment mode used while making the payment.

| **Payment Method** | **Refund Time** |
| - | - |
| `credit` or `debit` cards | 5-10 days |
| `netbanking` | 2-10 days |
| `wallet` | 0-3 days |
| `upi` | 2-7 days |

### Refund Fees

For Normal refunds, Razorpay does not charge any processing fee. However, the transaction fee and GST levied by Razorpay at the time of payment capture will not be reversed to your account (merchant's account).

## Dashboard and API Actions

You can perform the following actions:

* [Issue Normal refunds](https://razorpay.com/docs/payments/refunds/issue.md)
* [View Refunds](https://razorpay.com/docs/payments/refunds/view.md)
* [Handle refund errors](https://razorpay.com/docs/payments/refunds/errors.md)

### Related Information

<ul>
  <li>[Batch Refund](https://razorpay.com/docs/payments/refunds/batch.md)</li>
  <li>[Instant Refund](https://razorpay.com/docs/payments/refunds/instant.md)</li>
  <li>[Add funds to your account to process refunds (low account balance)](https://razorpay.com/docs/payments/dashboard/account-settings/balances.md#add-funds-to-reserve-balance)</li>
  <li>[Refunds API](https://razorpay.com/docs/payments/refunds/apis.md)</li>
  <li>[Subscribe to Webhooks](https://razorpay.com/docs/payments/refunds/subscribe-to-webhooks.md)</li>
  <li>[Refunds FAQs](https://razorpay.com/docs/payments/refunds/faqs.md)</li>
</ul>
