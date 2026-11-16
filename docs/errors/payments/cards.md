> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Cards Error Codes

> Explore errors related to card payments, discover reasons, merchant descriptions, and actionable next steps.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Below are the top error codes associated with card payments, along with their reasons, descriptions and subsequent steps for resolution.

> [card] payment\_timed\_out
>
> * **Description**: The payment could not be completed as the customer exceeded the time limit for payment processing. This time limit is typically 10 minutes unless otherwise specified.
> * **Next Steps**: Please request your customer to pay within the specified time limits for the payment.

> [card] gateway\_technical\_error
>
> * **Description**: There was a downtime on our partner bank due to which the payment has failed.
> * **Next Steps**: Payment Aggregators depend on partner banks for payment processing, and instances of failure like these are beyond our control. \\
>
>   Nevertheless, there is a proactive solution to address these issues. Inquire with your Customer Support Executive/ Sales Executive about implementing multi-terminal routing.

> [card] payment\_cancelled
>
> **Customer Cancelled Transaction**
>
> * **Description**: The payment could not be completed because the customer cancelled the transaction or pressed the back button during the payment processing period.
> * **Next Steps**: Please suggest to your customers to make another attempt or complete the payment at a later time.
>
> **Bank Downtime**
>
> * **Description**: There was a downtime on the customer's bank due to which the payment has failed.
> * **Next Steps**: In the case of Standard Checkout, please guide your customers on interpreting downtime information during the checkout process. Encourage them to consider using a different bank to complete the transaction successfully.\\
>
>   In the case of Custom/S2S checkout, if you have not done so already, integrate the [Downtime API](https://razorpay.com/docs/api/payments/downtime.md) into your checkout system. This will allow you to showcase downtime information directly on your checkout interface.

> [card] card\_declined
>
> * **Description**: The payment was declined by the customer's bank, resulting in the transaction being unsuccessful.
> * **Next Steps**: Razorpay may not have access to specific details regarding the failure reason, as customer banks typically do not provide such information. To understand the cause and address the issue, we recommend customers reach out directly to their banks. \\
>
>   Please advise your customer to attempt the payment again using another card.

> [card] insufficient\_funds
>
> * **Description**: The payment did not go through because the customer's bank account did not have enough funds to complete the transaction.
> * **Next Steps**: We recommend informing your customers to ensure they have an adequate balance before initiating a transaction. Additionally, customers can verify their account balance through the Banking Partner app prior to proceeding with any transactions.

> [card] card\_not\_enrolled
>
> * **Description**: The payment was unsuccessful as the card was not activated or enabled by the customer for online transactions.
> * **Next Steps**:  We recommend guiding your customers to enable online transaction functionality for their card through their Card Control page. This can be easily accomplished either through their Banking App or by logging in via their net banking portal.

> [card] bank\_technical\_error
>
> * **Description**: There was a downtime on the customer's bank due to which the payment has failed.
> * **Next Steps**: In the case of Standard Checkout, please guide your customers on interpreting downtime information during the checkout process. Encourage them to consider using a different bank to complete the transaction successfully.\\
>
>   In the case of Custom/S2S checkout, if you have not done so already, integrate the [Downtime API](https://razorpay.com/docs/api/payments/downtime.md) into your checkout system. This will allow you to showcase downtime information directly on your checkout interface.

> [card] card\_disabled\_for\_online\_payments
>
> * **Description**: The payment was unsuccessful as the card was not activated or enabled by the customer for online transactions.
> * **Next Steps**: We recommend guiding your customers to enable online transaction functionality for their card through their Card Control page. This can be easily accomplished either through their Banking App or by logging in via their net banking portal.

> [card] authentication\_failed
>
> * **Description**: The payment did not go through as the customer entered incorrect OTP/verification details or accidentally closed the browser/pressed the back button during the authentication stage of the transaction.
> * **Next Steps**: Please ensure customers correctly enter the OTP during transactions and avoid closing the browser during authentication. If the card supports [Native OTP](https://razorpay.com/docs/payments/optimizer/native-otp.md), encourage its use to prevent errors.

> [card] payment\_risk\_check\_failed
>
> * **Description**: The transaction was unsuccessful as the customer's bank declined the payment, citing it as fraudulent.
> * **Next Steps**: Razorpay may not have access to specific details regarding the failure reason, as customer banks typically do not provide such information. To understand the cause and address the issue, we recommend customers reach out directly to their bank.\\
>
>   Please advise your customer to attempt the payment again using another card.

> [card] payment\_failed
>
> * **Description**: The payment was declined by the customer's bank, resulting in the transaction being unsuccessful.
> * **Next Steps**: Razorpay may not have access to specific details regarding the failure reason, as customer banks typically do not provide such information. To understand the cause and address the issue, we recommend customers reach out directly to their bank.\\
>
>   Please advise your customer to attempt the payment again using another card.

> [card] incorrect\_cvv
>
> * **Description**: The payment was unsuccessful as the customer entered an incorrect CVV during the payment process.
> * **Next Steps**: Additionally, you can promote the convenience of saving their card details at checkout, which can enable a [CVV-less flow](https://razorpay.com/docs/payments/payment-methods/cards/features/cvv-less-flow.md) and simplify the payment process for future transactions.

> [card] debit\_instrument\_inactive
>
> * **Description**: The payment was unsuccessful as the card was not activated or enabled by the customer for online transactions.
> * **Next Steps**: We recommend guiding your customers to enable online transaction functionality for their card through their card control page. This can be easily accomplished either through their banking app or by logging in via their net banking portal.

> [card] debit\_instrument\_blocked
>
> * **Description**: The payment could not be processed due to the card being blocked, either by the customer or their bank.
> * **Next Steps**: We suggest informing customers to reach out to their bank to resolve the issues and unblock their cards. However, they can attempt the transaction again using an active card.

> [card] card\_expired
>
> * **Description**: The payment could not be completed because the customer's card is expired.
> * **Next Steps**: We suggest urging customers to reach out to their bank to resolve the issues and unblock their cards. Alternatively, they can attempt the transaction again using an active card.

> [card] transaction\_limit\_exceeded
>
> * **Description**: The payment did not go through because the customer has already reached the maximum transaction limit on their card for the day.
> * **Next Steps**: We recommend suggesting to your customer to retry the payment using a different card or alternative payment methods to complete the payment.
