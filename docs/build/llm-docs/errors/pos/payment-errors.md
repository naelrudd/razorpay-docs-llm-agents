# Razorpay POS Payment Processing Errors

Below are the payment processing-related error codes associated with POS payments, along with their details, error objects and current status.

**INFO**

For generic API errors such as invalid parameters, missing fields, authentication failures and server errors, refer to [Common Errors](https://razorpay.com/docs/build/llm-docs/errors/common.md). For standard payment error codes, refer to [Payment Error Codes](https://razorpay.com/docs/build/llm-docs/errors/payments/list.md).

    
### Validation checks

         
Error | Error Code | Description | Next Steps
---
Duplicate transaction detected or transaction already processed | PGIP000001 | The transaction was blocked because it has already been processed or is a duplicate. | Verify the transaction status before retrying.
---
Amount mismatch with order | PGIP000002 | The payment amount does not match the order amount. | Ensure the payment amount matches the order amount, then retry.
---
Negative amount | PGIP000003 | The payment request contains an invalid amount value. | Check the payment amount configuration in your system and retry.
---
Amount less than minimum allowed | PGIP000004 | The payment amount does not meet the minimum transaction requirement. | Advise the customer of the minimum amount and retry with a higher amount or another payment method.
---
Amount exceeds maximum allowed | PGIP000005 | The payment amount exceeds the maximum transaction limit configured for the terminal. | Advise the customer of maximum limits and retry with a lower amount.
---
Invalid currency (not allowed for merchant) | PGIP000006 | The currency specified is not supported for this merchant. | Ensure the transaction uses a supported currency and retry.
---
Order not found or expired or missing | PGIP000007 | The order does not exist or has expired. | Verify the order exists and create a new payment request if needed.
---
Invalid payment parameters | PGIP000008 | One or more required payment parameters are missing or invalid. | Verify all required payment parameters are provided correctly and retry.
---
Invalid amount | PGIP000003 | The payment amount is invalid. | Verify the amount and retry the transaction.
         
        

    
### Gateway errors

         
Error | Error Code | Description | Next Steps
---
Payment gateway unreachable or no response from gateway or timeout | PGIP000018 | The payment gateway is unreachable or not responding. | Retry the transaction. If the issue persists, it indicates gateway connectivity issues.
---
Invalid MSG format | PGIP000041 | The message format sent to the gateway is invalid or malformed. | Retry the transaction. If the issue persists, contact technical support.
         
        

    
### PIN failure errors

         
Error | Error Code | Description | Next Steps
---
Incorrect PIN entered | PGIP000019 | The customer entered an incorrect PIN. | Advise customer to enter correct PIN or use another card.
---
PIN tries exceeded | PGIP000020 | The customer exceeded the maximum number of PIN attempts. | Advise the customer to retry after some time or use another card.
---
PIN entry timeout or PIN required but not provided | PGIP000021 | The customer did not enter the PIN or the PIN entry timed out. | Advise the customer to enter the PIN within the time limit and retry.
---
PIN is mandatory | PGIP000038 | The transaction requires PIN authentication but the PIN was not provided. | Ask the customer to enter the PIN or use a card that does not require PIN.
---
INCORRECT PIN | PGIP000019 | The customer entered an incorrect PIN. | Ask the customer to enter the correct PIN and retry.
---
Incorrect PIN | PGIP000019 | The customer entered an incorrect PIN. | Ask the customer to enter the correct PIN and retry.
---
Invalid PIN | - | The customer entered an incorrect PIN. | Ask the customer to enter the correct PIN and retry.
---
PIN bypass not allowed | - | The payment failed because PIN bypass is not allowed. | Ask the customer to enter the PIN and retry the payment.
         
        

    
### Card or transaction decline errors from issuer

         
Error | Error Code | Description | Next Steps
---
Insufficient funds | PGIP000030 | The issuer declined the transaction due to insufficient funds in the account. | Ask the customer to use a different card or contact their issuer.
---
Expired card | PGIP000031 | The card has passed its expiration date and cannot be used. | Ask the customer to use a valid card.
---
Card blocked or stolen | - | The card is blocked or reported stolen. | Ask the customer to contact their bank or use another card.
---
Card not supported by gateway | - | The card is not supported by the gateway. | Use a supported card or a different payment method.
---
Transaction not allowed on card | - | Transactions are not allowed on this card. | Ask the customer to contact their bank or use another card.
---
Do not honor | PGIP000040 | The issuer declined the transaction with a "Do Not Honor" response. | Ask the customer to contact their card issuer or use a different card.
---
Refer to card issuer | PGIP000024 | The issuer requires the customer to contact them before processing this transaction. | Ask the customer to contact their card issuer for more information.
---
Daily transaction limit exceeded | - | The card has reached the daily transaction limit. | Ask the customer to use another card or wait before retrying.
---
Restricted card | PGIP000042 | The card has been restricted by the issuer. | Ask the customer to contact their card issuer or use a different card.
---
Invalid card number | - | The card number is invalid. | Ask the customer to verify the card details or use another card.
---
Card on negative file | - | The card is on a negative file or is blocked by the issuer. | Ask the customer to contact their bank or use another card.
---
Invalid transaction | PGIP000029 | The transaction is invalid or not permitted by the card issuer. | Ask the customer to retry or contact their card issuer.
---
Unable to locate record on file | PGIP000023 | The issuer was unable to locate the record in their system. | Ask the customer to contact their card issuer or use another card.
---
Refer to issuer's special conditions | PGIP000025 | The issuer has special conditions that require customer contact. | Ask the customer to contact their card issuer to resolve the special conditions.
---
Card not supported | PGIP000028 | The card type or brand is not supported for this merchant or terminal. | Ask the customer to use a supported card type.
---
Exceed usage limit | PGIP000033 | The card has exceeded the usage limit set by the issuer. | Ask the customer to use a different card or contact their issuer to increase limits.
---
Pick up card, special condition | PGIP000034 | The issuer requires the card to be retained due to a security concern. | Ask the customer to contact their card issuer immediately.
---
Enter lesser amount | PGIP000005 | The amount exceeds the allowed limit. | Retry with a lower amount or another payment method.
---
ECAF country flag decline | PGIP000036 | The transaction was declined due to ECAF country restrictions. | Ask the customer to use a different card or contact their issuer.
---
Fallback decline | PGIP000037 | Chip card fallback to magnetic stripe was declined by the issuer. | Ask the customer to use chip or contactless instead of magnetic stripe.
---
Transaction not supported | PGIP000039 | The transaction type is not supported by the card issuer. | Ask the customer to use a different card or payment method.
---
No or invalid accounts | PGIP000044 | No valid account is linked to the card or the account is invalid. | Ask the customer to contact their card issuer or use a different card.
---
Exceed withdrawal limit | PGIP000033 | The withdrawal or usage limit has been exceeded. | Ask the customer to use another card or retry later.
---
General decline | PGIP000040 | The issuer declined the transaction without a specific reason. | Ask the customer to contact their card issuer or use another card.
---
Card status inactive or closed | PGIP000045 | The card account is inactive or has been closed by the issuer. | Ask the customer to use a different card or contact their issuer.
---
Exceeds withdrawal frequency limit | PGIP000033 | The withdrawal frequency limit has been exceeded. | Ask the customer to retry later or use another card.
---
Card daily limit reached | - | The card has reached the daily limit. | Ask the customer to retry later or use another card.
---
Card declined | - | The card was declined by the issuer. | Ask the customer to contact their bank or use another card.
---
Customer's bank declined the payment request | - | The customer's bank declined the payment request. | Ask the customer to contact their bank or use another card.
---
Insufficient account balance | - | The account has insufficient balance. | Ask the customer to use another card or a different payment method.
         
        

    
### Chip transaction errors

         
Error | Error Code | Description | Next Steps
---
Chip card decline (auth works but confirm fails) | PGIP000047 | EMV chip authorisation succeeded but confirmation failed at the gateway. | Ask the customer to retry. No merchant action is required.
---
TC failure | PGIP000049 | Transaction Certificate (TC) validation failed during an EMV chip transaction. | Ask the customer to retry the transaction or use a different card.
         
        

    
### Gateway processing errors

         
Error | Error Code | Description | Next Steps
---
Invalid transaction code | - | The transaction code is invalid. | Verify the transaction code configuration and retry.
---
Invalid amount format | - | The amount format is invalid. | Use a valid amount format and retry the transaction.
---
Duplicate transaction at gateway | - | The gateway detected a duplicate transaction. | Verify the transaction status before retrying.
---
Original transaction not found (for reversal) | - | The original transaction was not found for reversal. | Verify the original transaction reference and retry.
---
Gateway internal error | - | The gateway encountered an internal error. | Retry the transaction. If the issue persists, contact support.
---
Batch settlement required | - | Batch settlement is required before processing new transactions. | Complete batch settlement and retry the transaction.
---
Unable to process | PGIP000027 | Payment processing failed due to an internal error. | Retry the transaction. If the issue persists, contact support.
---
Duplicate Transaction - as per Gateway | - | The gateway reported a duplicate transaction. | Verify the transaction status before retrying.
---
Payment timeout | - | The payment timed out. | Retry the transaction.
---
PRIZM_V2.30 | - | The PRIZM_V2.30 error was returned by the gateway. | Retry the transaction. If it persists, contact support.
---
Timeout (MW to Gateway or internal service) | - | The payment timed out between middleware and gateway or due to an internal service timeout. | Retry the transaction. If it persists, check connectivity.
         
        

    
### Other payment processing errors

         
Error | Error Code | Description | Next Steps
---
BIN SDK failure (Card BIN not present in RZP) | PGIP000046 | Card BIN (Bank Identification Number) is not found in Razorpay's database. | Ask the customer to use a different card. If the issue persists, contact Razorpay support to add the BIN.
