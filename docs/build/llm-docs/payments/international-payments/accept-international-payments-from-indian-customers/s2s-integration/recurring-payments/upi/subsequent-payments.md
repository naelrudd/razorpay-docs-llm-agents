# 3. Create Subsequent Payments

Given below are the steps to create and charge your customer subsequent payments:

## 3.1 Create an Order to Charge the Customer 

You have to create a new order every time you want to charge your customers. This order is different from the one created during the authorisation transaction.

The following endpoint creates an order.

/orders

```cURL: Request
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/orders \
-H "Content-Type: application/json" \
-d '{
    "amount": 1000,
    "currency": "INR",
    "merchant_id": "D2eavTHExqy97j",
    "customer_id": "cust_N8fv8Nftx5hato",
    "customer_details": {
        "name": "Gaurav Kumar",
        "email": "gaurav.kumar@example.com",
        "contact": "9000090000",
        "shipping_address": {
            "line1": "Mantri apartment",
            "line2": "Koramangala",
            "city": "Bengaluru",
            "country": "IND",
            "state": "Karnataka",
            "zipcode": "560032",
            "latitude": "123123",
            "longitude": "1231231"
        },
        "insights": {
            "order_count": "22",
            "chargeback_count": "4",
            "tier": "gold",
            "booking_channel": "agent",
            "has_account": true,
            "registered_at": 1234567890
        }
    },
    "receipt": "Receipt No. 1",
    "notes": {
        "notes_key_1": "Tea, Earl Grey, Hot",
        "notes_key_2": "Tea, Earl Grey... decaf."
    }
}'
```
```json: Success
{
    "amount": 1000,
    "amount_due": 1000,
    "amount_paid": 0,
    "attempts": 0,
    "created_at": 1707389202,
    "currency": "INR",
    "entity": "order",
    "id": "order_NYMDbygGb1DuDd",
    "notes": {
        "notes_key_1": "Tea, Earl Grey, Hot",
        "notes_key_2": "Tea, Earl Grey... decaf."
    },
    "offer_id": null,
    "receipt": "Receipt No. 1",
    "status": "created"
}

```json: Failure
{
   "error":{
      "code":"BAD_REQUEST_ERROR",
      "description":"The id provided does not exist",
      "source":"business",
      "step":"payment_initiation",
      "reason":"input_validation_failed",
      "metadata":{
         
      }
   }
}
```

    
### Request Parameters

`amount` _mandatory_
: `integer` Amount in currency subunits. For cards, the amount should be `100` (1).

`currency` _mandatory_
: `string` The 3-letter ISO currency code for the payment. Currently, we only support `INR`.

`merchant_id` _mandatory_
: `string` This is the Razorpay merchant ID for your Razorpay account. You can find this by logging in to the Dashboard and clicking the user icon in the top right corner.

`customer_id` _mandatory_
: `string` The unique identifier of the customer. For example, `cust_4xbQrmEoA5WJ01`.

`customer_details` _mandatory_
: `object` This contains details about the customer details of the order.

     `name` _mandatory_
     : `string` Customer's name.
      - Character length: Between 5 and 50 characters.
      - Allowed characters: Uppercase letters (A-Z), lowercase letters (a-z), and spaces (not at the beginning).
      - Not allowed characters: Numbers, special characters (e.g., @, ", ,, ., etc.), Unicode characters, emojis, and non-Latin scripts or regional languages.
      - Prohibited names: Names must be meaningful and contextually appropriate.
        - Avoid using repetitive patterns (e.g., aaa, xyz, kkk kk).
        - Names like litri litri, Hfg Gh, or husi husi are not permitted.
        - Curse words or offensive names are prohibited.
      - Example: `Gaurav Kumar`.

     `email` _optional_
     : `string` The customer's email address. A maximum length of 64 characters for the username. For example, in "gaurav.kumar@example.com", "gaurav.kumar" must not exceed 64 characters.

     `contact` _optional_
     : `string` The customer's phone number. A maximum length of 15 characters including country code. For example, `+919000090000`.

     `shipping_address` _mandatory_
     : `object` This contains the shipping address of the order.
      
         `line1` _mandatory_
         : `string` Address Line 1 of the address.
            - Character length: Must be between 3 and 100 characters.
            - Allowed characters: Uppercase letters (A-Z), lowercase letters (a-z), numbers (0-9), spaces, and special characters (*&/-()#_+{}[]:'".,.).
            - Not allowed characters: Regional languages.

         `line2` _mandatory_
         : `string` Address Line 2 of the address.
            - Character length: Must be between 3 and 100 characters.
            - Allowed characters: Uppercase letters (A-Z), lowercase letters (a-z), numbers (0-9), spaces, and special characters (*&/-()#_+{}[]:'".,.).
            - Not allowed characters: Regional languages.

         `city` _mandatory_
         : `string` Name of the city. Must be between 3 and 50 characters in length and can only include uppercase (A-Z) and lowercase (a-z) English letters, and spaces.

         `country` _mandatory_
         : `string` ISO3 country code of the billing address. Only `IND` is allowed.

         `state` _mandatory_
         : `string` Name of the state. It must be between 3 and 50 characters extended and can only include uppercase (A-Z) and lowercase (a-z) English letters and spaces. Please send the full name of the state, for example, Madhya Pradesh.

         `zipcode` _mandatory_
         : `string` The ZIP code must consist of 6-digit numeric characters. Only valid Indian ZIP codes will be accepted. Refer to the list of supported ZIP codes.

         `latitude` _optional_
         : `float` Latitude of the position expressed in decimal degrees (WSG 84), for example, 6.244203. A positive value denotes the northern hemisphere or the equator, and a negative value denotes the southern hemisphere. The number of digits to represent the precision of the coordinate.

         `longitude` _optional_
         : `float` Longitude of the position expressed in decimal degrees (WSG 84), for example, -75.581211. A positive value denotes east longitude or the prime meridian, and a negative value denotes west longitude. The number of digits to represent the precision of the coordinate.

     `insights ` _optional_
      : `json object` Additional details of the customer, including past transaction data.

          `order_count ` _optional_
          : `integer` Total orders placed by the account so far on the business platform. For example, 22.

          `chargeback_count ` _optional_
          : `integer` Total chargeback received for the customer account on the business platform. For example, 4.

          `tier` _optional_
          : `string ` Your company's passenger classification, such as with a frequent flyer program. In this case, you might use values such as:
           - `standard`
           - `gold`
           - `platinum` 

          `booking_channel` _optional_
          : `string` To share if the user is an agent, corporate, or individual. Possible values:
             - `agent`
             - `corporate`
             - `individual`

          `has_account` _optional_
          : `boolean` To denote if the buyer is on guest checkout or has logged into the account. Possible values:
             -` 1`: If the user is logged into the account.
             - `0`: If the user is on guest 

          `registered_at` _optional_
          : `integer` UNIX timestamp when the customer account was created. For example, 1234567890.

`receipt` _optional_
: `string` A user-entered unique identifier for the order. For example, `Receipt No. 1`. You should map this parameter to the `order_id` sent by Razorpay.

`notes`_optional_
: `object` Key-value pair you can use to store additional information about the entity. Maximum 15 key-value pairs, 256 characters each. For example, `"note_key": "Beam me up Scotty”`. 
        

    
### Response Parameters

`amount`
: `integer` Amount in currency subunits. For cards, the amount should be `100` (1).

`amount_due`
: `integer` The amount that the customer has yet to pay.

`amount_paid`
: `integer` The amount that has been paid.

`attempts`
: `integer` The number of payment attempts, successful and failed, that have been made against this order.

`created_at`
: `integer` The Unix timestamp at which the order was created.

`currency`
: `string` The 3-letter ISO currency code for the payment. Currently, we only support `INR`.

`entity`
: `string` Name of the entity. Here, it is `order`.

`id`
: `string` A unique identifier of the order created. For example `order_1Aa00000000002`.

`notes`
: `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

`receipt`
: `string` A user-entered unique identifier of the order. For example, `Receipt No. 1`. You should map this parameter to the `order_id` sent by Razorpay.

`status`
: `string` The status of the order.

You can create a payment against the `order_id` after you create an order.
        

## 3.2 Create a Recurring Payment 

Once you have generated an `order_id`, use it to create a payment and charge the customer. The following endpoint creates a payment to charge the customer.

/payments/create/recurring

```cURL: Request
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/payments/create/recurring \
-H "Content-Type: application/json" \
-d '{
    "amount": 1000,
    "currency": "INR",
    "order_id": "order_NYMptG6ChGaFgj",
    "email": "gaurav.kumar@example.com",
    "contact": "9000090000",
    "customer_id": "cust_N8fv8Nftx5hato",
    "token": "token_NZveVUfP5fn0fq",
    "recurring": "1",
    "notes": {
        "invoice_number": "IRS1245",
        "goods_description": "Digital Lamp"
    }
}'
```
```json: Success
{
  "razorpay_payment_id" : "pay_1Aa00000000001"
}

```json: Failure
{
   "error":{
      "code":"BAD_REQUEST_ERROR",
      "description":"Amount exceeds maximum amount allowed",
      "source":"business",
      "step":"payment_initiation",
      "reason":"input_validation_failed",
      "metadata":{
         
      }
   }
}
```

**INFO**

**UPI Payments**

- We recommend sending a pre-debit notification to the customer 24 hours before the debit date.
- For UPI, it may take between 24-36 hours for the subsequent payment to reflect on your Dashboard.
- This is because of the failure of pre-debit notification and/or any retries that we attempt for the payment.
- Do not create another subsequent payment until you get the status of the previous one.
- For UPI, **do not** create subsequent payments on the last day of the cycle. This will cause the payment to fail.
- **Pre-Debit Notification (PDN) Failure Handling:** If the pre-debit notification fails to reach the customer, either due to a PDN initiation error or a delivery failure. Razorpay automatically retries the notification request. If the notification remains undelivered after 3 attempts, the payment is marked as failed with the following details:
- Error Description: Unable to Notify the Customer.
- Error Reason: pre_debit_notification_failed.

    
### Request Parameters

`amount` _mandatory_
: `integer` The amount associated with the payment in smallest unit of the supported currency. For example, `2000` means ₹20. Must match the amount in [Create an order to charge the customer](#21-create-an-order-to-charge-the-customer).

`currency` _mandatory_
: `string` The 3-letter ISO currency code for the payment. Currently, we only support INR.

`order_id` _mandatory_
: `string` The unique identifier of the order created in [Create an order to charge the customer](#21-create-an-order-to-charge-the-customer).

`email` _mandatory_
: `string` The customer's email address. For example, `gaurav.kumar@example.com`.

`contact` _mandatory_
: `string` The customer's contact number. For example, `9000090000`.

`customer_id` _mandatory_
: `string` Unique identifier of the customer, obtained from the response of Customer API.

`token` _mandatory_
: `string` The `token_id` generated when the customer successfully completes the authorisation payment. Different payment instruments for the same customer have different `token_id`.

`recurring` _mandatory_
: `string` Possible values:
  - `1`: Recurring payment is enabled.
  - `preferred`: Use this when you want to support recurring payments and one-time payment in the same flow.

`notes` _mandatory_
: `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

    `invoice_number` _mandatory_
    : `string` Invoice number of the generated invoice. Ensure that each payment has a unique invoice number, with a length of fewer than 40 characters.

    `goods_description` _optional_
    : `string` Description of the goods. For example, `Digital Lamp`.
        

    
### Error Response Parameters

Given below is a list of possible errors you may face while creating a Recurring Payment.

    
        adequate_funds_not_available_blocked
        
         - **Description**: Sufficient unblocked funds not available in customer's account. Please ask customer to add fund and try again.
         - **Next Steps**: Please ask customer to add sufficient unblocked funds and try again.
        

    
### amount_does_not_match_mandate_amount

         
            
                Amount Mismatch - Mandate Amount
                
                 - **Description**: The payment failed as the amount does not match the amount provided at the time of mandate creation.
                 - **Next Steps**: Pass the transaction amount less than or equal to the mandate amount.
                

            
### Amount Mismatch - Payment Amount

                 - **Description**: The amount does not match with payment amount.
                 - **Next Steps**: Retry with correct amount.
                

         
        
    

    
### bad_request_error

         - **Description**: Invalid Mandate Sequence Number.
         - **Next Steps**: Retry after some time during the valid cycle.
        

    
### bank_account_invalid

         - **Description**: Payment failed because Account linked to VPA is invalid.
         - **Next Steps**: Create a new mandate with the customer.
        

    
### bank_not_available

         - **Description**: Payment was unsuccessful as the bank linked to this UPI ID is temporarily unavailable. Any amount deducted will be refunded within 5-7 working days.
         - **Next Steps**: Retry after some time.
        

    
### bank_technical_error

         
            
                Bank Decline
                
                 - **Description**: Payment was unsuccessful as it was declined by your bank. Any amount deducted will be refunded within 5-7 working days.
                 - **Next Steps**: Retry after some time.
                

            
### Bank or Wallet Gateway Error

                 - **Description**: Payment processing failed due to error at bank or wallet gateway
                 - **Next Steps**: Retry after some time.
                

            
### Temporary Bank Issue

                 - **Description**: Payment was unsuccessful due to a temporary issue at your bank. Any amount deducted will be refunded within 5-7 working days.
                 - **Next Steps**: Retry after some time.
                

            
### General Temporary Issue

                 - **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
                 - **Next Steps**: Retry after some time.
                

            
### Bank Services Halt

                 - **Description**: Payment was unsuccessful due to a temporary halt of services at this bank.
                 - **Next Steps**: Retry after some time.
                

         
        
    

    
### banks_hsm_is_down_remitter

         - **Description**: Remitter bank failed to process the transaction. Please try again after some time.
         - **Next Steps**: Please try again after some time.
        

    
### credit_to_beneficiary_failed

         - **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
         - **Next Steps**: Retry after some time.
        

    
### debit_declined

         - **Description**: Payment was unsuccessful as it was declined by remitter bank.
         - **Next Steps**: Create a new mandate with the customer.
        

    
### debit_instrument_blocked

         - **Description**: Payment was unsuccessful as the account linked to this UPI ID is blocked. Try using another account.
         - **Next Steps**: Create a new mandate with the customer.
        

    
### execution_day_rule_mismatch

         
            
                Execution Day Rule Mismatch
                
                 - **Description**: Day of debit does not match the debit execution rule for the payer. Please ensure execution day matches the execution rule.
                 - **Next Steps**: Please ensure execution day matches execution rule.
                

            
### Execution Day Rule Mismatch - Remitter

                 - **Description**: Day of debit does not match the debit execution rule for the payer. Please ensure execution day matches the execution rule.
                 - **Next Steps**: Please ensure execution day matches execution rule and try again.
                

         
        
    

    
### gateway_technical_error

         
            
                Bank or Wallet Gateway Error
                
                 - **Description**: Payment processing failed due to error at bank or wallet gateway.
                 - **Next Steps**: Retry after some time.
                

            
### Temporary Issue with Money Deduction

                 - **Description**: Payment was unsuccessful due to a temporary issue. If money got deducted, reach out to the seller.
                 - **Next Steps**: Retry after some time.
                

         
        
    

    
### id_value_must_be_present

         - **Description**: Failed to debit customer's bank account. Mandate details are incorrect.
         - **Next Steps**: Please try after sometime.
        

    
### insufficient_funds

         - **Description**: Transaction failed due to insufficient funds.
         - **Next Steps**: Ask the customer to add balance to their account and retry.
        

    
### invalid_response_from_gateway

         - **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
         - **Next Steps**: Retry after some time.
        

    
### invalid_token

         - **Description**: Invalid Token.
         - **Next Steps**: Create a new mandate with the customer.
        

    
### invalid_transaction_beneficiary

         - **Description**: Beneficiary address resolution failed. Please try again after some time.
         - **Next Steps**: Please try again after some time.
        

    
### invalid_vpa

         - **Description**: You have entered an incorrect UPI ID. Please retry with the correct UPI ID.
         - **Next Steps**: Ask the customer to retry with a valid VPA.
        

    
### issuer_dispatch_failed

         - **Description**: Payment failed due to some issue at the issuer bank. Please try again after some time.
         - **Next Steps**: Please try again after some time.
        

    
### limit_exceeded_remitting_bank

         - **Description**: Limit exceeded for remitter bank. Please ask customer to try with another bank account.
         - **Next Steps**: Please ask customer to try with another bank account.
        

    
### mandate_cancelled

         - **Description**: UPI mandate created for payment has been cancelled by user.
         - **Next Steps**: Create a new mandate with the customer.
        

    
### mandate_current_cycle_allowed_debit_exceeds

         - **Description**: Mandate is already honoured.
         - **Next Steps**: Wait till next cycle for debiting the customer.
        

    
### mandate_debit_beyond_psp_amount_cap

         - **Description**: Debit amount is beyond payer PSP specified amount cap. Please reduce the amount and try again.
         - **Next Steps**: Please reduce the mandate amount to match customer PSP.
        

    
### mandate_expired

         - **Description**: UPI Mandate is expired.
         - **Next Steps**: Create a new mandate with the customer.
        

    
### mandate_not_active

         - **Description**: UPI mandate is not active.
         - **Next Steps**: Create a new mandate with the customer.
        

    
### mandate_paused

         - **Description**: UPI mandate is not active, it is paused by user.
         - **Next Steps**: Ask the customer to resume the mandate & retry.
        

    
### merchant_error_payee_psp

         - **Description**: VPA resolution into bank account details failed. Please try again after some time.
         - **Next Steps**: Please try again after some time.
        

    
### mobile_number_invalid

         - **Description**: Registered Mobile number linked to the account has been changed or removed.
         - **Next Steps**: Create a new mandate with the customer.
        

    
### mpin_not_set_by_customer

         - **Description**: UPI MPIN not set by customer. Please ask customer to set MPIN and try again.
         - **Next Steps**: Please ask customer to set MPIN and try again.
        

    
### nature_of_debit_not_allowed

         - **Description**: Nature of debit not allowed in customer's account. Please ask the customer to use a different bank account.
         - **Next Steps**: Please ask the customer to use a different bank account.
        

    
### no_financial_address_record_found

         - **Description**: No financial address record found for this vpa. Please ask customer to try with another bank account.
         - **Next Steps**: Please ask customer to try with other bank account.
        

    
### no_original_request_found

         - **Description**: No mandate details were found in the record during debit. Please try after some time.
         - **Next Steps**: Please try after some time.
        

    
### null_ack_processing_failure

         - **Description**: Processing failure at gateway. Please try again after some time.
         - **Next Steps**: Please try again after some time.
        

    
### number_of_pin_tries_exceeded

         - **Description**: Customer has exceeded PIN retry limit. Please ask customer to create a new mandate and enter the right PIN.
         - **Next Steps**: Please ask customer to create a new mandate and enter the right PIN.
        

    
### payer_account_has_changed

         - **Description**: Payer account linked to the customer's VPA has changed. Please request the customer to either change it to the bank account used during mandate registration or register a new mandate for them.
         - **Next Steps**: Please request the customer to either change it to the bank account used during mandate registration or register a new mandate for them.
        

    
### payer_seqnum_validation_failure

         - **Description**: Payer sequence number length validation failed.
         - **Next Steps**: Please provide a valid payer sequence number (1-3 digits).
        

    
### payment_failed

         
            
                Temporary Issue with Refund
                
                 - **Description**: Payment was unsuccessful due to a temporary issue. If amount got deducted, it will be refunded within 5-7 working days.
                 - **Next Steps**: Retry after 1 hour.
                

            
### Try Another Bank Account

                 - **Description**: Payment failed. Please try again with another bank account.
                 - **Next Steps**: Retry after some time.
                

         
        
    

    
### payment_pending

         - **Description**: The status of your payment is pending. You can either wait or retry to pay successfully.
         - **Next Steps**: Retry after some time.
        

    
### payment_risk_check_failed

         - **Description**: Payment was unsuccessful as your account does not pass the risk checks done by your bank. Try using another account.
         - **Next Steps**: Retry after some time.
        

    
### payment_stopped_by_court_order

         - **Description**: Payment processing failure at remitter bank. Please ask customer to try with another bank account.
         - **Next Steps**: Please ask customer to try with another bank account.
        

    
### payment_timed_out

         - **Description**: Payment was unsuccessful as the bank linked to this UPI ID is not reachable at this time.
         - **Next Steps**: Retry after some time.
        

    
### per_transaction_limit_exceeded

         - **Description**: Customer bank per transaction limit exceeded. Please try again with a lower amount.
         - **Next Steps**: Please reduce transaction amount and try again.
        

    
### psp_bank_not_available

         - **Description**: Payer PSP / Bank not available. Please try again after some time.
         - **Next Steps**: Please try again after some time.
        

    
### psp_not_available

         - **Description**: Payment was unsuccessful as the UPI app is not reachable at this time. Any amount deducted will be refunded within 5-7 working days.
         - **Next Steps**: Retry after some time.
        

    
### psp_timeout

         - **Description**: Payer PSP timed out. Please try again.
         - **Next Steps**: Please try again after some time.
        

    
### regid_details_must_be_present

         - **Description**: Gateway validation failure. Please try after sometime or create a new mandate.
         - **Next Steps**: Please try after sometime or create a new mandate.
        

    
### remitter_account_dormant

         - **Description**: Bank Account is closed.
         - **Next Steps**: Create a new mandate with the customer.
        

    
### remitter_dispatch_failed

         - **Description**: Payment failed due to some issue at the customer's. Please try again after some time.
         - **Next Steps**: Please try again after some time.
        

    
### request_timed_out

         - **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
         - **Next Steps**: Retry after some time.
        

    
### response_not_received_within_tat

         - **Description**: VPA resolution into bank account details failed. Please try again after some time.
         - **Next Steps**: Please try again after some time.
        

    
### seqnum_mismatch_payer_psp

         - **Description**: Sequence number mismatch between payer and payee PSP. Please try again after some time.
         - **Next Steps**: Please ask customer to try after sometime.
        

    
### suspected_fraud_decline

         - **Description**: Suspected fraud, transaction declined by customer's bank. Please try again after some time.
         - **Next Steps**: Please try after sometime.
        

    
### transaction_frequency_limit_exceeded

         - **Description**: Payment failed. Please try again with another bank account.
         - **Next Steps**: Create a new mandate with the customer.
        

    
### transaction_limit_exceeded

         - **Description**: Payment failed because Transaction amount limit has exceeded
         - **Next Steps**: Reach out to the customer to collect the amount.
        

    
### transaction_not_allowed

         - **Description**: Payment was unsuccessful as it was declined by your bank. Reach out to your bank for more details. Try using another account.
         - **Next Steps**: Create a new mandate with the customer.
        

    
### transaction_not_permitted_cardholder

         - **Description**: Transaction not permitted for customer's account. Please ask customer to try with another bank account.
         - **Next Steps**: Please ask customer to try with another bank account.
        

    
### transaction_not_permitted_cardholder_beneficiary

         - **Description**: Transaction not permitted in beneficiary account. Please try again with another bank account.
         - **Next Steps**: Please try again with another bank account.
        

    
### transaction_not_permitted_to_vpa

         - **Description**: Transaction not permitted to payee VPA by the payer PSP. Please contact your bank to enable Autopay for this VPA.
         - **Next Steps**: Please contact your bank to enable autopay for this VPA.
        

    
### umn_does_not_exist_payer

         - **Description**: Mandate does not exist. Please create a new mandate.
         - **Next Steps**: Please ask customer to create new mandate.
        

    
### unable_to_process_beneficiary_bank

         - **Description**: Error processing request at beneficiary bank. Please try again after some time.
         - **Next Steps**: Please try again after some time.
        

    
### vpa_resolution_failed

         - **Description**: You have entered an incorrect UPI ID. Please retry with the correct UPI ID.
         - **Next Steps**: Retry after some time.
