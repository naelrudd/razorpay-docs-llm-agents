> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Turbo UPI SDK - Error Codes

> List of error codes for Turbo UPI SDK.

Available in
🇮🇳 India

Given below is the list of error codes categorised by error reasons, with relevant descriptions, source and step.

### Bad Request Errors

Given below is the list of Bad Request errors.

> [accordion] bank\_not\_live\_on\_upi
>
> * **Description**: The selected bank is not enabled on UPI. Please try using another bank.
> * **Source**: gateway
> * **Step**: customer\_onboarding

> [accordion] account\_does\_not\_exist
>
> > [accordion] Payment Debit Request
> >
> > * **Description**: No accounts found for the selected bank. Please try using another bank.
> > * **Source**: issuer\_bank
> > * **Step**: payment\_debit\_request
>
> > [accordion] Payment Credit Request
> >
> > * **Description**: Payment was unsuccessful as the receiver's bank account is not valid. Any amount deducted will be refunded within 5-7 working days.
> > * **Source**: beneficiary\_bank
> > * **Step**: payment\_credit\_request

> [accordion] transaction\_not\_allowed
>
> > [accordion] Payment Debit Request
> >
> > * **Description**: Transaction not permitted to the account as per your bank policy. Please contact your bank for more details or try with another bank account.
> > * **Source**: customer
> > * **Step**: payment\_debit\_request
>
> > [accordion] Payment Credit Request
> >
> > * **Description**: Payment not allowed as it got declined by the receiver's bank. Any amount deducted will be refunded within 5-7 working days.
> > * **Source**: beneficiary\_bank
> > * **Step**: payment\_credit\_request

> [accordion] upi\_pin\_registration\_card\_expired
>
> * **Description**: Card used while setting UPI PIN has expired. Please use another debit card or use another bank account.
> * **Source**: issuer\_bank
> * **Step**: payment\_authentication

> [accordion] upi\_pin\_registration\_card\_not\_found
>
> * **Description**: Card details used while setting UPI PIN are incorrect. Please re-check and try again.
> * **Source**: issuer\_bank
> * **Step**: payment\_authentication

> [accordion] upi\_pin\_registration\_card\_restricted
>
> * **Description**: Card used while setting UPI PIN has been blocked by your bank. Please reach out to your bank for more information or try using another bank account.
> * **Source**: issuer\_bank
> * **Step**: payment\_authentication

> [accordion] bank\_technical\_error
>
> * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> * **Source**: beneficiary\_bank
> * **Step**: payment\_status\_request

> [accordion] pin\_not\_set
>
> * **Description**: Payment was unsuccessful as you have not set the UPI PIN on the app. Try using another method.
> * **Source**: customer\_psp
> * **Step**: payment\_authentication

> [accordion] customer\_not\_registered
>
> * **Description**: No bank account is associated with this mobile number. Please try again by adding your account.
> * **Source**: gateway
> * **Step**: customer\_onboarding

> [accordion] server\_error
>
> * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> * **Source**: gateway
> * **Step**: payment\_authentication

> [accordion] payment\_cancelled\_by\_user
>
> * **Description**: Flow was aborted as you pressed back from the PIN screen. Please try again.
> * **Source**: customer
> * **Step**: payment\_authorization

### Gateway Errors

Given below is the list of gateway errors.

> [accordion] incorrect\_otp
>
> * **Description**: You have entered an incorrect OTP. Try again.
> * **Source**: customer
> * **Step**: customer\_onboarding

> [accordion] otp\_expired
>
> * **Description**: You have entered an expired OTP. Please regenerate OTP and try again.
> * **Source**: customer
> * **Step**: customer\_onboarding

> [accordion] insufficient\_funds
>
> * **Description**: Payment was unsuccessful due to insufficient funds. Kindly check your balance and try again.
> * **Source**: customer
> * **Step**: payment\_debit\_request

> [accordion] insufficient\_funds\_mandate\_block
>
> * **Description**: Payment was unsuccessful as the amount in your account is blocked for another payment. Try using another account.
> * **Source**: issuer\_bank
> * **Step**: payment\_authentication

> [accordion] otp\_attempts\_exceeded
>
> * **Description**: You have entered an incorrect OTP too many times. Try again in some time.
> * **Source**: customer\_psp
> * **Step**: customer\_onboarding

> [accordion] account\_dormant
>
> * **Description**: Payment was unsuccessful as the receiver's bank account is inactive. Any amount deducted will be refunded within 5-7 working days.
> * **Source**: beneficiary\_bank
> * **Step**: payment\_credit\_request

> [accordion] bank\_not\_live\_on\_upi
>
> * **Description**: Selected bank is not available on UPI. Please try using another bank.
> * **Source**: issuer\_bank
> * **Step**: customer\_onboarding

> [accordion] payment\_timed\_out
>
> > [accordion] Temporary Issue
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> > * **Source**: beneficiary\_bank
> > * **Step**: payment\_response
>
> > [accordion] UPI ID Not Reachable
> >
> > * **Description**: Payment was unsuccessful as the bank linked to this UPI ID is not reachable at this time.
> > * **Source**: issuer\_bank
> > * **Step**: payment\_debit\_response

> [accordion] first\_transaction\_limit\_exceeded
>
> * **Description**: Payment was unsuccessful as you exceeded the first-time transaction limit set by your bank. You can use another bank account or retry after 24 hours.
> * **Source**: issuer\_bank
> * **Step**: payment\_debit\_response

> [accordion] transaction\_limit\_exceeded
>
> > [accordion] Limit Set By Bank Exceeded
> >
> > * **Description**: Payment was unsuccessful as you exceeded the transaction limit set by your bank. Try using another account.
> > * **Source**: issuer\_bank
> > * **Step**: payment\_debit\_response
>
> > [accordion] Daily Amount Limit Exceeded
> >
> > * **Description**: Payment was unsuccessful as you exceeded the amount limit for the day with this bank account. Try using another account.
> > * **Source**: issuer\_bank
> > * **Step**: payment\_debit\_response

> [accordion] first\_time\_transaction\_freeze\_period
>
> * **Description**: Payment was unsuccessful due to the cooling period set by your bank for first-time user. Please try again after some time.
> * **Source**: issuer\_bank
> * **Step**: payment\_debit\_response

> [accordion] transaction\_frequency\_limit\_exceeded
>
> * **Description**: Payment was unsuccessful as the number of transactions exceeds the max limit set by the bank. You can use another bank account or retry after some time.
> * **Source**: issuer\_bank
> * **Step**: payment\_debit\_response

> [accordion] bank\_account\_inactive
>
> > [accordion] Issuer Bank Account Inactive
> >
> > * **Description**: Payment was unsuccessful as your account is not active. Please try using another bank account.
> > * **Source**: issuer\_bank
> > * **Step**: payment\_debit\_request
>
> > [accordion] Receiver Bank Account Inactive
> >
> > * **Description**: Payment was unsuccessful as the receiver's bank account is not active. Any amount deducted will be refunded within 5-7 working days.
> > * **Source**: beneficiary\_bank
> > * **Step**: payment\_debit\_request

> [accordion] server\_error
>
> > [accordion] Temporary Issue - Issuer Bank
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue. Please retry in some time.
> > * **Source**: beneficiary\_bank
> > * **Step**: payment\_request
>
> > [accordion] Temporary Issue - Beneficiary Bank
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue. Please retry in some time.
> > * **Source**: issuer\_bank
> > * **Step**: payment\_request

> [accordion] invalid\_ifsc
>
> * **Description**: Payment was unsuccessful due to a temporary issue. Please retry in some time.
> * **Source**: gateway
> * **Step**: payment\_authentication

> [accordion] upi\_pin\_registration\_card\_blocked
>
> * **Description**: Card used while setting UPI PIN has been blocked by your bank. Please reach out to your bank for more information or try using another bank account.
> * **Source**: issuer\_bank
> * **Step**: payment\_authentication

> [accordion] bank\_technical\_error
>
> > [accordion] UPI ID Temporarily Unavailable
> >
> > * **Description**: Payment was unsuccessful as the bank linked to this UPI ID is temporarily unavailable. Any amount deducted will be refunded within 5-7 working days.
> > * **Source**: issuer\_bank
> > * **Step**: payment\_credit\_response
>
> > [accordion] Temporary Issue
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> > * **Source**: issuer\_bank
> > * **Step**: payment\_credit\_response

> [accordion] payment\_declined
>
> > [accordion] Declined by Bank
> >
> > * **Description**: Payment was unsuccessful as it was declined by your bank. Reach out to your bank for more details. Try using another account.
> > * **Source**: issuer\_bank
> > * **Step**: payment\_debit\_request
>
> > [accordion] Temporary Issue
> >
> > * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> > * **Source**: beneficiary\_bank
> > * **Step**: payment\_debit\_request

> [accordion] pin\_attempts\_exceeded
>
> * **Description**: You have exceeded the incorrect UPI PIN attempts. You can use another bank account or retry after 24 hours.
> * **Source**: customer
> * **Step**: payment\_authentication

> [accordion] incorrect\_pin
>
> * **Description**: You have entered incorrect UPI PIN. Please try again with the correct UPI PIN.
> * **Source**: customer
> * **Step**: payment\_authentication

> [accordion] linked\_account\_removal\_failed
>
> * **Description**: Unable to remove the account. Please try again.
> * **Source**: customer\_psp
> * **Step**: account\_management

> [accordion] sms\_text\_not\_received
>
> * **Description**: Something went wrong while sending SMS. Please try again.
> * **Source**: gateway
> * **Step**: customer\_onboarding

### Server Errors

Given below is the list of server errors.

> [accordion] server\_error
>
> * **Description**: Payment was unsuccessful due to a temporary issue. Any amount deducted will be refunded within 5-7 working days.
> * **Source**: issuer\_bank
> * **Step**: customer\_onboarding

> [accordion] server\_error
>
> * **Description**: We are facing some trouble completing your request at the moment. Please try again shortly.
> * **Source**: internal
> * **Step**: payment\_authorization
