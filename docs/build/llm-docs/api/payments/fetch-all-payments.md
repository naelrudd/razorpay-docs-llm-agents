# Fetch All Payments

**GET** `/v1/payments`

Use this endpoint to retrieve details of all the payments. By default, only the last 10 records are displayed. You can use the `count` and `skip` parameters to retrieve the specific number of records that you need.

### Parameters

`from` _optional_
: `integer` UNIX timestamp, in seconds, from when payments are to be fetched.

`to` _optional_
: `integer` UNIX timestamp, in seconds, till when payments are to be fetched.

`count` _optional_
: `integer` Number of payments to be fetched. 
 Default value is 10. Maximum value is 100. This can be used for pagination, in combination with the `skip` parameter.

`skip` _optional_
: `integer` Number of records to be skipped while fetching the payments.

### Parameters

`id`
: `string` Unique identifier of the payment.

`entity`
: `string` Indicates the type of entity.

`amount`
: `integer` The payment amount in currency subunits. For example, for an amount of 1 enter 100.

`currency`
: `string` The currency in which the payment is made. Refer to the list of [international currencies](https://razorpay.com/docs/build/llm-docs/payments/international-payments.md#supported-currencies) that we support.

`status`
: `string` The status of the payment. Possible values:
  - `created`
  - `authorized`
  - `captured`
  - `refunded`
  - `failed`

`method`
: `string` The payment method used for making the payment. Possible values:
  - `card`
  - `netbanking`
  - `wallet`
  - `emi`
  - `upi`

`order_id`
: `string` Order id, if provided. Know more about [Orders](https://razorpay.com/docs/build/llm-docs/payments/orders.md).

`description`
: `string` Description of the payment, if any.

`international`
: `boolean` Indicates whether the payment is done via an international card or a domestic one. Possible values:
    - `true`: Payment made using international card.
    - `false`: Payment not made using international card.

`refund_status`
: `string` The refund status of the payment. Possible values:
  - `null`
  - `partial` 
  - `full`

`amount_refunded`
: `integer` The amount refunded in currency subunits. For example, if `amount_refunded = 100`, it is equal to 1.

`captured`
: `boolean` Indicates if the payment is captured. Possible values:
    - `true`: Payment has been captured.
    - `false`: Payment has not been captured.

`email`
: `string` Customer email address used for the payment.

`contact`
: `string` Customer contact number used for the payment.

`fee`
: `integer` Fee (including GST) charged by Razorpay.

`tax`
: `integer` GST charged for the payment.

`error_code`
: `string` Error that occurred during payment. For example, `BAD_REQUEST_ERROR`.

`error_description`
: `string` Description of the error that occurred during payment. For example, `Payment processing failed because of incorrect OTP`.

`error_source`
: `string` The point of failure. For example, `customer`.

`error_step`
: `string` The stage where the transaction failure occurred. The stages can vary depending on the payment method used to complete the transaction. For example, `payment_authentication`.

`error_reason`
: `string` The exact error reason. For example, `incorrect_otp`.

`notes`
: `json object` Contains user-defined fields, stored for reference purposes.

`created_at`
: `integer` Timestamp, in UNIX format, on which the payment was created.

`card_id`
: `string` The unique identifier of the card used by the customer to make the payment.

`card`
: `object` Details of the card used to make the payment.

  `id`
  : `string` The unique identifier of the card used by the customer to make the payment.

  `entity`
  : `string` The name of the entity. Here, it is `card`.

  `name`
  : `string` Name of the cardholder.

  `last4`
  : `integer` The last 4 digits of the card number.

  `network`
  : `string` The card network. Possible values:
    - `American Express`
    - `Diners Club` (Only available for private limited and registered businesses)
    - `Maestro`
    - `MasterCard`
    - `RuPay`
    - `Unknown`
    - `Visa`

  `type`
  : `string` The card type. Possible values:
    - `credit`
    - `debit`
    - `prepaid`
    - `unknown`

  

  

  `issuer`
  : `string` The card issuer. The 4-character code denotes the issuing bank. This attribute will not be set for the card issued by a foreign bank.

  `emi`
  : `boolean` Indicates whether the card can be used for EMI payment method. Possible values:
    - `true`: Card can be used for EMI payments.
    - `false`: Card cannot be used for EMI payments.

  `sub_type`
  : `string` The sub-type of the customer's card. Possible values:
    - `customer` 
    - `business`

    
    Know how to accept payments made by customers using [corporate cards](https://razorpay.com/docs/build/llm-docs/payments/payment-methods/cards/corporate-cards.md).

`upi`
: `object` Details of the UPI payment received. Only applicable if `method` is `upi`.

  `payer_account_type`
  : `string` The payment method used for making the payment. Possible values:
    - `bank_account`
    - `credit_card`
    - `wallet`

  
  `vpa`
  : `string` The customer's VPA (Virtual Payment Address) or UPI id used to make the payment. For example, `gauravkumar@exampleupi`.

  `flow` 
  : `string` The type of UPI flow. Possible values:
    - `intent`: When a UPI app is selected and user is redirected to it.
    - `collect`: The user enters their UPI ID and receives a notification from the UPI app. They open the app and complete the payment.
    - `in_app`: In case of Turbo UPI Payments.

`bank`
: `string` The 4-character bank code which the customer's account is associated with. For example, `UTIB` for Axis Bank.

`vpa`
: `string` The customer's VPA (Virtual Payment Address) or UPI id used to make the payment. For example, `gauravkumar@exampleupi`.

`wallet`
: `string` The name of the wallet used by the customer to make the payment. For example, `payzapp`.

`acquirer_data`
: `object` An object containing unique reference numbers. 

    `rrn`
    : `string` A unique bank reference number provided by the banking partner when a refund is processed. This reference number can be used by the customer to track the status of the refund with the bank.

    `authentication_reference_number`
    : `string` A unique reference number generated for RuPay card payments.
    
    `bank_transaction_id`
    : `string` A unique reference number provided by the banking partner in case of netbanking payments.

  

  `issuer`
  : `string` The card issuer. The 4-character code denotes the issuing bank. This attribute will not be set for the card issued by a foreign bank.

  `emi`
  : `boolean` Indicates whether the card can be used for EMI payment method. Possible values:
     - `true`: Card can be used for EMI payments.
     - `false`: Card cannot be used for EMI payments.

  `sub_type`
  : `string` The sub-type of the customer's card. Possible values:
    - `customer` 
    - `business`
       Know how to accept payments made by customers using [corporate cards](https://razorpay.com/docs/build/llm-docs/payments/payment-methods/cards/corporate-cards.md).

`bank`
: `string` The 4-character bank code which the customer's account is associated with. For example, `UTIB` for Axis Bank.

`vpa`
: `string` The customer's VPA (Virtual Payment Address) or UPI id used to make the payment. For example, `gauravkumar@exampleupi`.

`wallet`
: `string` The name of the wallet used by the customer to make the payment. For example, `payzapp`.

`acquirer_data`
: `array` A dynamic array consisting of a unique reference numbers. 

    `rrn`
    : `string` A unique bank reference number provided by the banking partner when a refund is processed. This reference number can be used by the customer to track the status of the refund with the bank.

    `authentication_reference_number`
    : `string` A unique reference number generated for RuPay card payments.
    
    `bank_transaction_id`
    : `string` A unique reference number provided by the banking partner in case of netbanking payments.

`token_id`
: `string` Unique identifier of the token associated with this payment.

`invoice_id`
: `string` Unique identifier of the invoice associated with this payment.

### Errors

The API \{key/secret\} provided is invalid.
* code: 4xx
* description: The API credentials passed in the API call differ from the ones generated on the Dashboard.
* solution: The API keys must be active and entered correctly with no whitespace before or after.

from must be between 946684800 and 4765046400
* code: 400
* description: The time range entered is invalid.
* solution: Enter a valid time range between `946684800` and `4765046400`.

The count must be at least 1.
* code: 400
* description: `count=0` (or otherwise less than 1) passed in the query string.
* solution: Pass `count` as a positive integer between 1 and 100.

The count may not be greater than 100.
* code: 400
* description: `count` value above 100 in the query string. The Payments list endpoint caps per-page results at 100.
* solution: Use a `count` of 100 or fewer. For larger datasets, paginate using the `skip` parameter.

The count must be an integer.
* code: 400
* description: `count` query parameter is non-numeric (for example, `count=abc`).
* solution: Pass `count` as a positive integer.

from must be an integer.
* code: 400
* description: `from` query parameter is not a UNIX-epoch integer (for example, an ISO date string was passed).
* solution: Pass `from` as a UNIX-epoch integer (for example, `1700000000`), not a human-readable date.

to must be an integer.
* code: 400
* description: `to` query parameter is not a UNIX-epoch integer.
* solution: Pass `to` as a UNIX-epoch integer.

The skip must be at least 0.
* code: 400
* description: `skip` query parameter was passed as a negative integer.
* solution: Pass `skip` as a non-negative integer (0 or higher).

The skip must be an integer.
* code: 400
* description: `skip` query parameter is non-numeric.
* solution: Pass `skip` as a non-negative integer.
