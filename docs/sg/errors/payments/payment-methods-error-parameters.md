> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payment Method Error Parameters

> List of values for Source and Step parameters for each payment method supported by Razorpay.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

There are certain error codes specific for each payment method supported by Razorpay. To understand the errors and their `reasons`, it is recommended to know the `source` (stakeholders) and the `steps` involved in the payment flows:

* [Cards](#cards)
* [PayNow](#paynow)

## Cards

> [tab] Source Parameter
>
> The possible values for the `source` parameter for cards are listed below:
>
> * `customer`
> * `business`
> * `internal`
> * `gateway`
> * `issuer_bank`

> [tab] Step Parameter
>
> The possible values for the `step` parameter, along with the description, are listed below:
>
> 1. `payment_initiation`\\
>
>    Your system initiates and sends the payment request to our server. Our server validates your request, creates the payment flow and forwards the request to the Gateway.
>
> 2. `card_enrollment_check`\\
>
>    Upon receiving a request from Razorpay, Gateway sends the enrollment check request to the bank for the enrollment of the card check.
>
> 3. `payment_authentication`\\
>
>    The bank verifies the enrollment of the card, and then requests the authentication of the customer by sending 3DS URL and OTP to the customer.
>
>    * 3DS URL\\
>
>      Bank sends the Authentication (3DS URL), which is routed through Gateway > Razorpay > Customer.
>
>    * OTP\\
>
>      The bank sends the OTP to the customer’s mobile directly. The customer enters the valid OTP within the time on the bank's OTP page.
>
> 4. `payment_authorization`\\
>
>    Once the customer has completed the authentication, the bank authorises the release of the funds. The authorisation status is communicated to the Gateway which in turn communicates the same to Razorpay.
>
> 5. `payment_capture`\\
>
>    Once the payment is successfully authorised, Razorpay sends the capture request to the Gateway which in turn sends the same to the bank to capture the authorised payment.

## PayNow

> [tab] Source Parameter
>
> The possible values for the `source` parameter for PayNow are listed below:
>
> * `customer`
> * `business`

> [tab] Step Parameter
>
> The possible values for the `step` parameter, along with the description, are listed below:
>
> 1. `payment_initiation`\\
>
>    Your system initiates and sends the payment request to our server. Our server validates your request, creates the payment flow and forwards the request to the Gateway.
>
> 2. `payment_authentication`\\
>
>    The customer logs into his bank account and completes the transaction.
>
> 3. `payment_authorization`\\
>
>    Upon successful authentication, bank authorises the release of funds and notifies Razorpay. Razorpay in turn, notifies the business.
