> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Check Payout Status

> Check the status of payouts on the RazorpayX Dashboard.

Available in
🇮🇳 India

Payout Status details are returned when a payout is created and moves to another state. Know more about [Payout States](https://razorpay.com/docs/x/payouts/states-life-cycle.md).

> [!WARNING]
>
> **Watch Out!**
>
> The `failure_reason`, `queueing_details` and `cancellation_details` fields, along with the error object, would be deprecated from the API response. Please move to Payout status details to understand the status of your payout and share this information with your developers.

## About Status Details

Status details shows intermediate statuses (`pending`, `processing`, `queued`) and terminal states (`reversed` and `failed`) along with the payout clearance SLA. You can view the status of a payout in the following places:

* [RazorpayX Dashboard](#check-status-on-dashboard)
* [Fetch Payout API response](https://razorpay.com/docs/errors/x/payout-status-details.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks)

Status details also tells you why a payout is in the `processing` state. Some reasons include:

* [Deemed Success](https://razorpay.com/blog/business-banking/payout-processing-imps-upi-transactions-deemed-success-npci/)
* NEFT/RTGS off hours
* Partner bank or beneficiary bank issues
* Other bank or server issues

Whenever an attribute in the status details changes, we send a payout update webhook, which you can use to inform your beneficiaries.

## Check Status on Dashboard

You can check the status details of a payout in three ways on the RazorpayX Dashboard.

1. Log in to the [RazorpayX Dashboard](https://x.razorpay.com/auth).
2. Navigate to either of the following.

> [accordion] Need Help Widget
>
> You can check the payout status using the **Need Help?** button at the bottom-right corner of the Dashboard. Watch the video below or read along.
>
> [Check Payout Status via Support Widget | RazorpayX](https://www.youtube.com/embed/epkmUCUI83c)
>
> 1. Click the **Need Help?** widget.
> 2. In the right pane, use commas to enter multiple Payout IDs in the text box.
>
>    ![Search Payout Status on RazorpayX Dashboard](https://razorpay.com/docs/build/browser/assets/images/x-payout-status-support-search.jpg)
> 3. Click **Search**.
>
> It opens a list view of the payouts along with their statuses. You can hover over the payout status or open the summary view for more information on the payout's status.

> [accordion] Payout Summary View
>
> 1. Navigate to **Payouts** from the left menu.
> 2. Select the particular payout to open the summary view in the right pane.
>
>    ![Payout status details on RazorpayX Dashboard](https://razorpay.com/docs/build/browser/assets/images/x-payouts-status-summary.jpg)

> [accordion] Subscribe to Daily Reports
>
> You can also subscribe to daily reports to receive a detailed document on the status, status and SLA for the payouts in the `processing` status.
>
> To subscribe, [raise a support ticket](https://razorpay.com/docs/x/support.md) from the RazorpayX Dashboard with a list of recipient email IDs. We will enable the function for you in 3 working days.

![Check Payout Status on RazorpayX Dashboard](https://razorpay.com/docs/build/browser/assets/images/x-check-payout-status-dashboard.jpg)

## Payout Status Details

Find below an exhaustive list of payout statuses, their details and also possible steps you can take to proceed further.

> [accordion] Status: reversed/failed
>
> > [accordion] bank\_account\_closed
> >
> > * **Description**: Payout failed as the beneficiary account is closed. Please contact the beneficiary bank.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: NA
>
> > [accordion] bank\_account\_frozen
> >
> > * **Description**: Payout failed as beneficiary account is frozen. Please contact the beneficiary bank.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: NA
>
> > [accordion] bank\_account\_invalid
> >
> > * **Description**: Payout failed due to invalid beneficiary account details.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: NA
>
> > [accordion] beneficiary\_account\_dormant
> >
> > * **Description**: Payout failed as beneficiary account is dormat. Please contact the beneficiary bank.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: NA
>
> > [accordion] beneficiary\_bank\_failure
> >
> > * **Description**: Payout failed at the beneficiary bank due to a technical issue. Please retry after 30 min.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: Retry
>
> > [accordion] beneficiary\_bank\_offline
> >
> > * **Description**: Beneficiary bank systems are offline. Please retry after 30 min.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: Retry
>
> > [accordion] beneficiary\_bank\_rejected
> >
> > * **Description**: Payout rejected by the beneficiary bank. Please contact the beneficiary bank.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: NA
>
> > [accordion] beneficiary\_bank\_technical\_error
> >
> > * **Description**: Payout failed due to a technical issue at the beneficiary bank. Please retry after 30 min.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: Retry
>
> > [accordion] beneficiary\_psp\_offline
> >
> > * **Description**: Beneficiary PSP systems are offline. Please retry after 30 min.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: Retry
>
> > [accordion] imps\_not\_allowed
> >
> > * **Description**: IMPS is not enabled on beneficiary account. Please retry with different mode.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: Retry with a different payment mode.
>
> > [accordion] invalid\_ifsc\_code
> >
> > * **Description**: Payout failed as the IFSC code is invalid. Please correct the IFSC code and retry.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: Retry with correct IFSC code.
>
> > [accordion] npci\_beneficiary\_timeout
> >
> > * **Description**: Temporary technical issue between NPCI and the beneficiary bank. Please retry after 30 min.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: Retry
>
> > [accordion] transaction\_limit\_exceeded
> >
> > * **Description**: Payout amount greater than the limit supported by the beneficiary account.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: NA
>
> > [accordion] amount\_limit\_exhausted\_neft
> >
> > * **Description**: The NEFT 24\*7 limits for your account has been exhausted. Please retry after sometime.
> > * **Source**: business
> > * **Next Steps**: Retry
>
> > [accordion] beneficiary\_account\_invalid
> >
> > * **Description**: Payout failed due to invalid beneficiary account number.
> > * **Source**: business
> > * **Next Steps**: NA
>
> > [accordion] beneficiary\_vpa\_invalid
> >
> > * **Description**: UPI validation failed. If the UPI ID is valid, please retry after sometime.
> > * **Source**: business
> > * **Next Steps**: Ensure UPI ID is valid and retry.
>
> > [accordion] insufficient\_funds
> >
> > * **Description**: Payout failed due to insufficient funds in your account.
> > * **Source**: business
> > * **Next Steps**: Add funds to your account and retry.
>
> > [accordion] invalid\_beneficiary
> >
> > * **Description**: Customer account does not exist with the wallet provider for the given phone number.
> > * **Source**: business
> > * **Next Steps**: NA
>
> > [accordion] gateway\_down
> >
> > * **Description**: Payout failed as the partner bank is facing technical issues. Please retry.
> > * **Source**: gateway
> > * **Next Steps**: Retry
>
> > [accordion] gateway\_technical\_error
> >
> > * **Description**: Payout failed due to a temporary technical issue at the partner bank. Please retry after 30 min.
> > * **Source**: gateway
> > * **Next Steps**: Retry
>
> > [accordion] gateway\_timeout
> >
> > * **Description**: Payout timed out at the partner bank. Please retry after 30 min.
> > * **Source**: gateway
> > * **Next Steps**: Retry
>
> > [accordion] server\_error
> >
> > * **Description**: Payout failed. Contact support for help.
> > * **Source**: internal
> > * **Next Steps**: Contact support to find out the exact issue.
>
> > [accordion] server\_error\_temporary
> >
> > * **Description**: Payout failed due to temporary technical issue. Please retry.
> > * **Source**: internal
> > * **Next Steps**: Retry

> [accordion] Status: processing
>
> > [accordion] beneficiary\_bank\_confirmation\_pending
> >
> > * **Description**: Confirmation of credit to the beneficiary is pending from `beneficiary_bank`. Please check the status after (date,time).
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: Inform the customer of the delay, reason for the same and by when it will be cleared.
>
> > [accordion] bank\_window\_closed
> >
> > * **Description**: The `mode` window for the day is closed. Please check the status after (date,time).
> > * **Source**: gateway
> > * **Next Steps**: Inform the customer of the delay, reason for the same and by when it will be cleared.
>
> > [accordion] payout\_bank\_processing
> >
> > * **Description**: Payout is being processed by the partner bank. Please check the final status after (date,time).
> > * **Source**: gateway
> > * **Next Steps**: Inform the customer of the delay, reason for the same and by when it will be cleared.
>
> > [accordion] amount\_limit\_exhausted
> >
> > * **Description**: The (mode) 24\*7 limits for your account has been exhausted. Please check the status after (date,time).
> > * **Source**: business
> > * **Next Steps**: Inform the customer of the delay, reason for the same and by when it will be cleared.
>
> > [accordion] partner\_bank\_pending
> >
> > * **Description**: Payout is being processed by our partner bank. Please check the final status after (date,time).
> > * **Source**: internal
> > * **Next Steps**: Inform the customer of the delay, reason for the same and by when it will be cleared.

> [accordion] Status: processed
>
> > [accordion] payout\_processed
> >
> > * **Description**: Payout is processed and the money has been credited into the beneficiary's account.
> > * **Source**: beneficiary\_bank
> > * **Next Steps**: NA

> [accordion] Status: pending
>
> > [accordion] pending\_approval
> >
> > * **Description**: Workflow for the payout is pending approval from the approver(s).
> > * **Source**: business
> > * **Next Steps**: NA

> [accordion] Status: queued
>
> > [accordion] gateway\_degraded
> >
> > * **Description**: Payout is queued as Partner bank systems are down.
> > * **Source**: gateway
> > * **Next Steps**: NA
>
> > [accordion] beneficiary\_bank\_down
> >
> > * **Description**: Beneficiary bank's systems are not working. Payout will be processed after the system starts working else it will be failed after the pre-defined time limit.
> > * **Source**: gateway
> > * **Next Steps**: NA
>
> > [accordion] low\_balance
> >
> > * **Description**: Payout is queued as there is insufficient balance in your account to process the payout.
> > * **Source**: business
> > * **Next Steps**: NA
>
> > [accordion] syncing\_balance
> >
> > * **Description**: Payout is queued as your balance is being synced with the bank. Please check the status after some time.
> > * **Source**: gateway
> > * **Next Steps**: Check status after some time.
>
> > [accordion] fee\_recovery\_pending
> >
> > * **Description**: Payout is queued as you have a pending fee recovery payout. It will get processed after the fee recovery payout is cleared.
> > * **Source**: business
> > * **Next Steps**: NA

### Related Information

* [About Payouts](https://razorpay.com/docs/x/payouts)
* [Payout Best Practices](https://razorpay.com/docs/x/payouts/best-practices.md)
* [Status Details via API](https://razorpay.com/docs/errors/x/payout-status-details.md)
