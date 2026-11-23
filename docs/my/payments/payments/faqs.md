> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Frequently Asked Questions (FAQs)

> Find answers to frequently asked questions about Razorpay Curlec Payments.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

## Payments

> [accordion] How much does  charge per transaction?
>
> Please refer to the [pricing page](https://curlec.com/pricing/).

> [accordion] How can we test our website or mobile app integration with  Payment Gateway?
>
> Razorpay Curlec offers a sandbox environment where you can test integrations before going live. To test your integration, [generate test API Keys](https://razorpay.com/docs/my/api/authentication.md#generate-api-keys) in test mode and implement them in your code. Test mode features a mock bank page with **Success** and **Failure** buttons to replicate the live payment experience. No money is deducted as these are simulated transactions.

> [accordion] What is Standard Capture?
>
> Standard capture is an authorisation followed by a `delayed` capture of the payment. In this scenario, if a customer makes a payment, the amount is deducted from the customer's bank account by Razorpay Curlec. The authorised amount is settled to your account only after you initiate a `capture` request.

> [accordion] How do I manually capture a payment?
>
> You can manually capture payments:
>
> * [From the Dashboard](https://razorpay.com/docs/my/payments/payments/capture-settings.md#manually-capture-payments)
> * [Using APIs](https://razorpay.com/docs/my/api/payments/capture.md)

> [accordion] How are payments made by my customers settled to my account? Is any action required from my end?
>
> No action is required from your end for the settlements. Razorpay Curlec automatically settles the captured payments to your account as per your settlement cycle.

> [accordion] A payment is marked as 'failed' on my Dashboard but money is debited from the customer’s account. What do I do?
>
> A payment is said to be in the 'failed' state when we do not receive a successful callback message on the transaction from the issuing bank. If the customer’s account is debited and we do not receive a successful callback, the amount will be auto-refunded by the customer’s issuing bank in 7-10 working days.\\
>
> In case of a failed payment, we verify the status with the bank at regular intervals. If there is a change in status, the payment moves to the `authorized` state, and a notification is sent to you and the customer.\\
>
> In such scenarios, you can choose to do any one of the following:
>
> * **Provide services**: Capture the payment and provide the service/good as was promised earlier to the customer.
> * **Refund the transaction**: If you are not able to provide service to the customer as per the agreed terms (Such as time of delivery, cost of purchase or inventory issues), refund the payment to the customer.

> [accordion] Is  PCI-DSS compliant?
>
> Yes, Razorpay Curlec is PCI-DSS compliant.

> [accordion] What is Late Authorisation?
>
> Late authorisation is a situation that arises when a payment is interrupted by external factors such as network issues or technical errors at customer's or bank's end. In such cases, funds may or may not get debited from the customer's bank account and Razorpay Curlec does not receive a payment status from the bank. Know more about [Late Authorisation](https://razorpay.com/docs/my/payments/payments/late-authorisation.md).
