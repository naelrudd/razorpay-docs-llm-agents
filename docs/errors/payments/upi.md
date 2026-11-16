> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# UPI Error Codes

> Explore errors related to UPI payments, discover reasons, merchant descriptions, and actionable next steps.

Available in
🇮🇳 India

Below are the top error codes associated with UPI payments, along with their reasons, descriptions, and subsequent steps for resolution.

> [card] bank\_technical\_error
>
> * **Description**: The payment failed due to a downtime on the UPI provider.
> * **Next Steps**: In the case of Standard Checkout, please guide your customers in interpreting downtime information during the checkout process and encourage them to consider using a UPI App to successfully complete the transaction.\\
>
>   In the case of Custom/S2S Checkout, we recommend integrating the [Downtime API](https://razorpay.com/docs/api/payments/downtime.md) into your checkout system. This will allow you to showcase downtime information directly on your checkout interface.

> [card] credit\_failed
>
> **Customer Bank Account Mismatch**
>
> * **Description**: The payment was unsuccessful because the customer selected a different bank account that was not used during the time of registration with your business.
> * **Next Steps**: Please ask your customers to use the bank account they initially registered with your business to make the payment.
>
> **Partner Bank Downtime**
>
> * **Description**: The payment failed due to a downtime on our partner bank.
> * **Next Steps**: Payment Aggregators depend on partner banks for payment processing, and instances of failure like these are beyond our control.\\
>
>   However, reach out to your Customer Support Executive/Sales Executive about implementing multi-terminal routing.

> [card] gateway\_technical\_error
>
> **Partner Bank Technical Issues**
>
> * **Description**: The payment could not be completed due to technical issues from the partner bank.
> * **Next Steps**: Payment Aggregators depend on partner banks for payment processing, and instances of failure like these are beyond our control.\\
>
>   We recommend advising your customers to attempt the transaction again after some time.
>
> **Partner Bank Downtime**
>
> * **Description**: The payment failed due to a downtime on our partner bank.
> * **Next Steps**: Payment Aggregators depend on the partner banks for payment processing, and instances of failure like these are beyond our control.\\
>
>   However, reach out to your Customer Support Executive/Sales Executive about implementing multi-terminal routing.

> [card] insufficient\_funds
>
> * **Description**: The payment did not go through because the customer's bank account did not have enough funds to complete the transaction.
> * **Next Steps**: Notify your customers to confirm they have sufficient funds before initiating a transaction or choosing a different bank account with adequate balance. Additionally, customers can check their account balance on the UPI App using the Check balance feature.

> [card] invalid\_vpa
>
> * **Description**: The payment was unsuccessful due to the customer not being a valid user on the UPI App.
> * **Next Steps**: Guide your customers in finalising the registration process by linking their bank account with the VPA on the UPI App. Please request customers to re-attempt the payment after completing the registration steps.

> [card] payment\_cancelled
>
> * **Description**: The payment could not be completed because the customer cancelled the transaction or pressed the back button during the payment processing period.
> * **Next Steps**: Please suggest to your customers to make another attempt.

> [card] payment\_collect\_request\_expired
>
> * **Description**: The payment could not be completed as the customer exceeded the time limit for payment processing. This time limit is typically 10 minutes unless otherwise specified.
> * **Next Steps**: Please request the customer to complete the payment within the specified time limit.

> [card] payment\_declined
>
> * **Description**: The payment did not go through because the funds could not be debited from the customer's bank account.
> * **Next Steps**: Please suggest to your customers to make another attempt.

> [card] payment\_timed\_out
>
> **Customer Exceeded Payment Time Limit**
>
> * **Description**: The payment could not be completed as the customer exceeded the time limit for payment processing. This time limit is typically 10 minutes unless otherwise specified.
> * **Next Steps**: Please request the customer to complete the payment within the specified time limit.
>
> **Partner Bank Downtime**
>
> * **Description**: The payment failed due to a downtime at our partner bank.
> * **Next Steps**: Payment Aggregators depend on partner banks for payment processing, and instances of failure like these are beyond our control.\\
>
>   However, reach out to your Customer Support Executive/Sales Executive about implementing multi-terminal routing.

> [card] vpa\_resolution\_failed
>
> * **Description**: The payment was unsuccessful due to a failure to process the transaction using the customer's UPI ID.
> * **Next Steps**: Please raise a ticket with the Technical support team to address and resolve these issues.
