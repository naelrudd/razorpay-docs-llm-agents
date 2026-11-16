> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# List of Errors

> List of payment errors with descriptions and next steps.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Below are the top error codes associated with various payment methods, along with their reasons, descriptions and steps for resolution.

The `source` field in each error response tells you where the error originated and who needs to act:

| Source Value | Meaning | Who Acts |
| - | - | - |
| `customer` | The customer made an error (wrong OTP, cancelled payment, insufficient funds). | Display a meaningful message and prompt them to retry. |
| `business` | Your integration sent an invalid request (missing field, wrong amount, method not enabled). | Fix the request parameters before retrying. |
| `gateway` | The payment gateway or bank returned an error. Usually transient. | Retry or ask the customer to use a different payment method. |
| `razorpay` | An internal error at Razorpay's end. | Retry after a short delay. Contact support if it persists. |

## Bad Request Errors

| Error Reason | Detailed Error Description | Next Steps |
| - | - | - |
| amount\_less\_than\_minimum\_amount | Amount in the payment request is less than the minimum amount. Transacting through some banks have fixed fees. If the payment amount is less than the fixed fee then this error shows up. | Please make sure that the payment amount is more than the minimum fees associated with the bank. |
| authentication\_failed | The payment failed as 3D secure, or OTP authentication failed. This could happen if the user cancels the payment on the authentication (OTP submit) screen or enters incorrect authentication details such as OTP. | The customer must enter correct authentication details to complete the payment. |
| bank\_account\_invalid | The bank account is not valid. The customer or bank could have closed the account. | The customer must try using a valid bank account or another method. |
| bank\_account\_validation\_failed | The third party validation failed as the given bank account details were incorrect or could not be verified. | The customer should check the bank account details provided and try again. |
| bank\_not\_enabled | The selected bank to complete the transaction is not enabled for your business. | Please reach out to Razorpay to enable the selected bank. |
| bank\_technical\_error | The issuing bank was facing technical problems at the moment the payment was attempted. This usually occurs when the Core Banking System encounters a technical error while processing the payment. | The customer must try using another bank account or another method. |
| capture\_failed | Payment capture has failed. | Please reach out to Razorpay. |
| card\_expired | The card has expired. | The customer must retry with a valid card. |
| card\_network\_not\_enabled | The card's network (Visa, Mastercard, etc.) is not enabled for the merchant. | Please reach out to Razorpay to enable the card network. |
| card\_not\_enrolled | The card is not enrolled for this payment method. | Customer needs to enroll the card for this payment method or use another card. |
| card\_number\_invalid | The card number is invalid. | Customer needs to enter a valid card number. |
| card\_type\_invalid | The card type is invalid. | Customer needs to use a valid card type. |
| compliance\_violation | The payment violates compliance requirements. | Please ensure the payment meets all compliance requirements. |
| debit\_instrument\_blocked | The customer is using a blocked card to complete the payment. The card could have been blocked by the issuer or by customers themselves. | The customer must retry with a different card or method. |
| duplicate\_refund\_id | A refund with this ID already exists. | Please use a unique refund ID. |
| duplicate\_request | A duplicate request has been submitted. | Please avoid duplicate requests. |
| emi\_greater\_than\_max\_amount | The EMI amount is greater than the maximum allowed amount. | Please reduce the EMI amount or use another payment method. |
| emi\_plan\_unavailable | The EMI plan is not available. | Please choose another EMI plan or payment method. |
| incorrect\_atm\_pin | Incorrect ATM PIN entered. | Customer needs to enter the correct ATM PIN. |
| incorrect\_card\_details | Incorrect card details entered. | Customer needs to enter correct card details. |
| incorrect\_card\_expiry\_date | Incorrect card expiry date entered. | Customer needs to enter the correct card expiry date. |
| incorrect\_cardholder\_name | Incorrect cardholder name entered. | Customer needs to enter the correct cardholder name. |
| incorrect\_cvv | The customer has entered an incorrect CVV to complete the payment. | The customer must retry and enter the correct CVV. |
| incorrect\_otp | The customer has entered an incorrect OTP to complete the payment. | The customer must retry and enter the correct OTP. |
| incorrect\_pin | Incorrect PIN entered. | Customer needs to enter the correct PIN. |
| input\_validation\_failed | Payment failed due to wrong request or input sent in the payment request. This is also seen while creating a payment with incorrect parameter values on the Dashboard. | Rectify the validation issues and try again. Check the error description and field parameters for more information about the error. Check your integration/payment request or reach out to Razorpay. Refer to the API Reference Guide. |
| insufficient\_funds | The customer does not have sufficient funds in the account to complete the payment. | The customer must retry with a different card or method. |
| international\_transaction\_not\_allowed | International transactions are not allowed. | Customer needs to use a domestic payment method or enable international transactions. |
| invalid\_amount | The amount provided is invalid. | Please provide a valid amount. |
| invalid\_currency | The currency passed is not supported or is invalid. | Check the list of supported currencies and use the correct currency code. |
| invalid\_device | The device used is invalid for this transaction. | Customer needs to use a valid device. |
| invalid\_email | The email address provided is invalid. | Please provide a valid email address. |
| invalid\_mobile\_number | The mobile number provided is not valid. | Customer needs to provide a valid mobile number and retry. |
| invalid\_order\_id | Order ID required in the payment request is either missing or is invalid. Order ID is mandatory for every payment. | Make sure the correct order ID is always passed while initiating a new payment. |
| invalid\_request | The request is invalid. | Please check the request format and retry. |
| invalid\_user\_details | Invalid user details provided. | Customer needs to provide valid user details. |
| invalid\_vpa | The customer has entered an incorrect VPA to complete the payment. | The customer must check and enter the correct VPA. |
| live\_mode\_not\_enabled | Live mode is not enabled for your business. This error generally arises when you use test mode keys to make a live payment. | Generate the live mode keys in the Dashboard and use them in your integration. |
| merchant\_not\_activated | The merchant account is not activated. | Please contact Razorpay to activate the merchant account. |
| mismatch\_in\_transaction\_details | There is a mismatch in transaction details. | Please check and correct the transaction details. |
| mobile\_number\_invalid | The mobile number is invalid. | Customer needs to provide a valid mobile number. |
| order\_already\_paid | There can only be one successful payment for each order ID. This error arises when you are trying to use an order ID where a payment is already completed. | Check for order status before initiating a new payment attempt on the order. You can also evaluate using a different order ID for each payment. |
| order\_payment\_method\_mismatch | This error arises when the method mentioned in the order request is different from the method mentioned in the payment request. | Do not pass method in the create order request. |
| order\_amount\_mismatch | This error arises when the amount mentioned in the order request is different from the amount mentioned in the payment request. | Please make sure that the same amount is passed in both payment and order request. |
| otp\_attempts\_exceeded | OTP attempts have been exceeded. | Customer needs to wait and retry after some time. |
| otp\_expired | The OTP has expired. | Customer needs to request a new OTP. |
| payment\_cancelled | The customer has explicitly cancelled the payment due to which the authentication failed to complete. | The customer must retry to complete the payment. |
| payment\_failed | Payment processing failed due to error at bank or wallet gateway. No specific error code received from gateway in this case. | Please retry with a different payment method. |
| payment\_method\_not\_enabled | The selected payment method is not enabled for your business. This error occurs when your customer tries to complete a transaction using a method that is not enabled for you. | Reach out to Razorpay to enable payment method. |
| payment\_method\_not\_enabled | UPI is not enabled however merchant has hit the UPI Payment request on API. | Please enable the payment method. |
| payment\_pending\_approval | The payment is currently pending approval by the concerned authority as part of the maker-checker flow. | Please reach out to the approver in your organization to get the transaction approved. |
| payment\_risk\_check\_failed | Payment declined due to risk checks. Risk checks are performed by Razorpay, Gateway, and Issuer Bank. The source parameter would give additional clarity where the risk check failed. | The customer must retry with a different card or method. |
| payment\_timed\_out | The customer did not complete the transaction within the specified time. This error may also happen when no response is received from the gateway. | The customer must retry and complete the transaction within the time. |
| pin\_attempts\_exceeded | PIN attempts have been exceeded. | Customer needs to wait and retry after some time. |
| pin\_not\_set | PIN is not set for the payment method. | Customer needs to set a PIN for the payment method. |
| record\_not\_found | The requested record was not found. | Please check the details and retry. |
| recurring\_payment\_not\_enabled | Recurring payments are not enabled. | Please enable recurring payments for your account. |
| refund\_limit\_crossed | The refund limit has been crossed. | Please contact Razorpay for assistance. |
| server\_error | Technical error at Razorpay's server. This usually occurs when there is some server issue at Razorpay's end. | Please retry after some time or reach out to Razorpay. |
| transaction\_daily\_limit\_exceeded | The customer has exceeded the daily transaction limit set on the card. Some of the cards allow customers to set a limit or have a default limit set. | The customer must retry using a different instrument or wait 24 hours to complete the payment. |
| transaction\_limit\_exceeded | The customers have exceeded the credit or debit limit set on their cards. This error usually arises while doing high value transactions. | The customer must retry using a different bank's card or method. |
| transaction\_frequency\_limit\_exceeded | NPCI has a transaction limit both on the amount and the frequency per day. Customer has exhausted the frequency limit. | Please retry using another payment method. |
| transaction\_on\_vpa\_restricted | Transaction on this VPA has been temporarily / permanently blocked by the PSP. | The customer to retry with another UPI ID. |
| upi\_app\_technical\_error | Technical error occurred at the customer's PSP due to which the payment failed. | The customer must retry the payment. If the error persists then the customer should try using another UPI app. |
| upi\_autopay\_not\_supported\_on\_psp | UPI Autopay is not supported on PSP. | Please retry with another PSP app. |
| upi\_collect\_not\_enabled | UPI Collect flow is not enabled however merchant has hit the Collect payment request on API. | Please enable collect flow. |
| upi\_intent\_not\_enabled | UPI Intent flow is not enabled however merchant has hit the Intent Payment request on API. | Please enable intent flow. |
| user\_not\_eligible | The customer failed the eligibility check and is not eligible for credit. This error may arise when the customer has a poor credit score or incomplete / insufficient documents. | The customer must retry using a different payment method. |
| user\_not\_registered\_for\_netbanking | The customer's bank account is not registered for netbanking. | The customer should register their account with the issuing bank for netbanking. |
| verification\_failed | Verification of the payment using the status check API has failed. | This is a temporary error. The customer must retry. |

## Gateway Errors

| Error Reason | Detailed Error Description | Next Steps |
| - | - | - |
| authentication\_failed | The payment failed as 3D secure, or OTP authentication failed. This could happen if the user cancels the payment on the authentication (OTP submit) screen or enters incorrect authentication details such as OTP. | The customer must enter correct authentication details to complete the payment. |
| authorisation\_declined\_by\_psp | PSP app has rejected the authorisation request. This can happen when there is an issue/downtime with the PSP or there's an issue with the customer's VPA. | Recheck the customer's VPA and retry. If this is recurring, then the customer can choose another PSP app and retry. |
| bank\_cutoff\_in\_progress | Bank CBS cutoff is in progress. This is a periodic event at the bank's end. | The customer must retry. |
| bank\_not\_available | Bank is not available due to a downtime or a technical issue. | The customer must retry. |
| bank\_technical\_error | The issuing bank was facing technical problems at the moment the payment was attempted. This usually occurs when the Core Banking System encounters a technical error while processing the payment. | The customer must try using another bank account or another method. |
| beneficiary\_account\_does\_not\_exist | An issue with the beneficiary account which does not exist. | Please reach out to Razorpay. |
| beneficiary\_account\_dormant | An issue with the beneficiary account which is dormant. | Please reach out to Razorpay. |
| card\_declined | The card has been declined. | The customer must retry with a different card or method. |
| collect\_on\_mcc\_blocked | UPI Collect is blocked for this MCC (Merchant Category Code). | Please contact Razorpay for assistance. |
| collect\_request\_pending | A collect request is already pending for this transaction. | Please wait for the current request to complete or retry after some time. |
| credit\_limit\_exceeded | The customer's credit limit has been exceeded. | Customer needs to reduce the amount or use another payment method. |
| credit\_limit\_expired | The customer's credit limit has expired. | Customer needs to renew their credit limit or use another payment method. |
| credit\_limit\_inactive | The customer's credit limit is inactive. | Customer needs to activate their credit limit or use another payment method. |
| credit\_limit\_not\_approved | The customer's credit limit is not approved. | Customer needs to get their credit limit approved or use another payment method. |
| credit\_not\_permitted | Credit transactions are not permitted for this customer. | Customer needs to use another payment method. |
| credit\_failed | Credit processing has failed. | Please retry or use another payment method. |
| debit\_declined | The debit transaction has been declined. | Customer needs to retry with another payment method. |
| deemed\_transaction | The transaction is deemed and cannot be processed. | Please contact Razorpay for assistance. |
| debit\_instrument\_blocked | The customer is using a blocked card to complete the payment. The card could have been blocked by the issuer or by customers themselves. | The customer must retry with a different card or method. |
| debit\_instrument\_inactive | The debit instrument is inactive. | Customer needs to activate the instrument or use another payment method. |
| duplicate\_rrn\_found | A duplicate RRN (Retrieval Reference Number) was found. | Please retry with a new transaction. |
| funds\_blocked\_by\_mandate | Funds are blocked by an existing mandate. | Customer needs to release the mandate or use another account. |
| gateway\_technical\_error | Technical error occurred at the gateway. | Please retry after some time. |
| invalid\_response\_from\_gateway | Invalid response received from the gateway. | Please retry the transaction. |
| invalid\_vpa | The customer has entered an incorrect VPA to complete the payment. | The customer must check and enter the correct VPA. |
| issuer\_technical\_error | Technical error occurred at the card issuer. | Please retry after some time or use another card. |
| mandate\_creation\_declined | Mandate creation has been declined. | Customer needs to retry mandate creation or use another payment method. |
| mandate\_creation\_expired | Mandate creation has expired. | Customer needs to retry mandate creation. |
| mandate\_creation\_failed | Mandate creation has failed. | Customer needs to retry mandate creation or use another payment method. |
| mandate\_creation\_timeout | Mandate creation has timed out. | Customer needs to retry mandate creation. |
| mcc\_amount\_limit\_exceeded | The amount limit for this MCC (Merchant Category Code) has been exceeded. | Please reduce the amount or contact Razorpay. |
| payment\_amount\_tampered | The payment amount has been tampered. | The customer must retry with the correct amount. |
| payment\_cancelled | The customer has explicitly cancelled the payment due to which the authentication failed to complete. | The customer must retry to complete the payment. |
| payment\_collect\_request\_expired | The payment collect request has expired. | Customer needs to retry the payment. |
| payment\_declined | The payment has been declined. | Customer needs to retry with another payment method. |
| payment\_declined\_due\_to\_high\_traffic | Payment declined due to high traffic at the gateway. | Please retry after some time. |
| payment\_failed | Payment processing failed due to error at bank or wallet gateway. No specific error code received from gateway in this case. | Please retry with a different payment method. |
| payment\_pending | The payment is pending and has not been completed yet. | Please wait for the payment to complete or retry. |
| payment\_risk\_check\_failed | Payment declined due to risk checks. Risk checks are performed by Razorpay, Gateway, and Issuer Bank. The source parameter would give additional clarity where the risk check failed. | The customer must retry with a different card or method. |
| payment\_session\_expired | The payment session has expired. | Customer needs to start a new payment session. |
| payment\_timed\_out | The customer did not complete the transaction within the specified time. This error may also happen when no response is received from the gateway. | The customer must retry and complete the transaction within the time. |
| psp\_app\_not\_available | PSP app is not available. This can be because of a downtime with the PSP. | The customer must retry with another PSP app. |
| psp\_app\_not\_supported | UPI App is not supported. This is a rare error used when a particular app is blacklisted. | Please choose another PSP app and try again. |
| psp\_not\_available | PSP is not available. | Customer needs to retry with another PSP. |
| psp\_not\_registered | PSP is not registered. | Customer needs to register with a PSP or use another PSP. |
| reqauth\_mandate\_not\_acknowledged | Request authentication mandate is not acknowledged. | Customer needs to acknowledge the mandate. |
| request\_timed\_out | The request has timed out. | Please retry the request. |
| server\_error | Technical error at Razorpay's server. This usually occurs when there is some server issue at Razorpay's end. | Please retry after some time or reach out to Razorpay. |
| transaction\_daily\_count\_exceeded | The daily transaction count has been exceeded. | Customer needs to wait for the next day or use another payment method. |
| transaction\_daily\_limit\_exceeded | The customer has exceeded the daily transaction limit set on the card. Some of the cards allow customers to set a limit or have a default limit set. | The customer must retry using a different instrument or wait 24 hours to complete the payment. |
| transaction\_frequency\_limit\_exceeded | NPCI has a transaction limit both on the amount and the frequency per day. Customer has exhausted the frequency limit. | Please retry using another payment method. |
| user\_not\_eligible | The customer failed the eligibility check and is not eligible for credit. This error may arise when the customer has a poor credit score or incomplete/insufficient documents. | The customer must retry using a different payment method. |
| vpa\_resolution\_failed | The UPI network failed to validate the VPA. This is a technical error when the resolution fails. | The customer must retry using a different bank account or method. |
