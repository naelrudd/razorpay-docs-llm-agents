# About Payments

You can accept live payments using the Razorpay Payment Gateway once your Razorpay account is activated.

## Payment Life Cycle

Following are the various states of a payment:

States | Description
---
`created` | This is the first state.  The customer has provided the payment details, which are sent to Razorpay. The payment has not been processed yet.
---
`authorized` | The payment state changes to `authorized` when the bank successfully authenticates the customer's payment details. The money is deducted from the customer’s account by Razorpay. The amount is settled to your account after the payment is manually or automatically captured.  Payment in this state is auto-refunded to the customer if not captured within 3 days of creation.
---
`captured` |  When the payment status is changed to `captured`, the payment is verified as complete by Razorpay. The amount is settled to your account as per the settlement schedule.
---
`refunded` | You can refund the payments that have been successfully captured at your end. The amount is reversed to the customer's account.
---
`failed` | An unsuccessful payment attempt is marked as `failed`, and the customer will have to retry the payment. Any amount debited will be refunded into customers account in 5-7 working days.

The following state diagram depicts the flow of money through the various payment states:

## Late Authorisation

Late authorisation is a situation that arises when a payment is interrupted by external factors such as network issues or technical errors at the customer's or bank's end. In such cases, funds may or may not get debited from the customer's bank account, and Razorpay does not receive a payment status from the bank. Know more about [Late Authorization](https://razorpay.com/docs/build/llm-docs/payments/payments/late-authorisation.md).

## Dashboard Actions

You can perform the following actions on payments from the Dashboard:

- Configure settings to [auto-capture payments](https://razorpay.com/docs/build/llm-docs/payments/payments/capture-settings.md).
- [Manually capture payments](https://razorpay.com/docs/build/llm-docs/payments/payments/capture-settings.md#manually-capture-payments)
- [Issue a refund for a payment](https://razorpay.com/docs/build/llm-docs/payments/refunds/issue.md)
- [View details of a payment](https://razorpay.com/docs/build/llm-docs/payments/payments/dashboard.md#view-payment-details)
- [View settlement details of a payment](https://razorpay.com/docs/build/llm-docs/payments/settlements/dashboard.md#view-settlements-using-dashboard)

### Related Information

- [Payment Methods](https://razorpay.com/docs/build/llm-docs/payments/payment-methods.md)
- [Test Card Details](https://razorpay.com/docs/build/llm-docs/payments/payments/test-card-details.md)
- [Payment Capture Settings](https://razorpay.com/docs/build/llm-docs/payments/payments/capture-settings.md)
- [International Payment Support](https://razorpay.com/docs/build/llm-docs/payments/international-payments.md)
