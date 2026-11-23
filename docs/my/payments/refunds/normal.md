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
> If you are a customer looking for a refund, know more about [customer refunds](https://razorpay.com/docs/my/payments/customers/customer-refunds.md).

## How Normal Refunds Work

When you make a Normal refund request to Razorpay Curlec, the information is sent to banking partners or other related stakeholders. Each of them have their own process for refund requests. After processing the refund request, the refund amount is sent to the customer's bank account or card balance.

Following is a typical flow for card refunds:

![Normal Refund Flow](https://razorpay.com/docs/build/browser/assets/images/normal-refund-flow.jpg)

### Payment Methods

We support all payment methods for Normal refunds.

Refunds are sent back to the original payment method used in making the payment. For example, if a credit card was used to make the payment, the refund amount is pushed to the same credit card.

DuitNow QR refunds go back to the customer's bank or e-wallet account. Refunds are processed within 3 to 5 working days.

DuitNow Pay refunds are supported. During early access, Razorpay Curlec pays the customer by bank transfer within 5 to 7 working days. The customer sees a transfer from Razorpay Curlec, not a reversal of the original payment.

### Processing Time

When you send a Normal refund request to Razorpay Curlec, the information is sent to our banking partners. Depending on the bank's processing time, it can take 7-10 business days for the refunds to reflect in the customer's bank account or card balance.

The time taken to process a normal refund depends on the payment mode used while making the payment.

| **Payment Method** | **Refund Time** |
| - | - |
| `credit` or `debit` cards | 5-10 days |
| `wallet` | 0-3 days |
| `fpx` | 0-3 days |
| `duitnow` ([DuitNow QR](https://razorpay.com/docs/my/payments/payment-methods/duitnow/qr.md)) | 3-5 working days |
| `duitnow` ([DuitNow Pay](https://razorpay.com/docs/my/payments/payment-methods/duitnow/pay.md)) | 5-7 working days during early access, paid as a bank transfer |

### Refund Fees

For Normal refunds, Razorpay Curlec charges a flat fee of RM 0.50 per refund. In addition, the transaction fee levied by Razorpay Curlec at the time of payment capture will not be reversed to your account (merchant's account).

## Dashboard and API Actions

You can perform the following actions:

* [Issue Normal refunds](https://razorpay.com/docs/my/payments/refunds/issue.md)
* [View Refunds](https://razorpay.com/docs/my/payments/refunds/view.md)
* [Handle refund errors](https://razorpay.com/docs/my/payments/refunds/errors.md)

### Related Information

<ul>
  <li>Batch Refund</li>

  <li>[Add funds to your account to process refunds (low account balance)](https://razorpay.com/docs/my/payments/dashboard/account-settings/balances.md#add-funds-to-current-balance)</li>
  <li>[Refunds API](https://razorpay.com/docs/my/payments/refunds/apis.md)</li>
  <li>[Subscribe to Webhooks](https://razorpay.com/docs/my/payments/refunds/subscribe-to-webhooks.md)</li>
  <li>[Refunds FAQs](https://razorpay.com/docs/my/payments/refunds/faqs.md)</li>
</ul>
