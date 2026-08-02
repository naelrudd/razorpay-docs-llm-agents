# API Integration Checklist

The following table lists the recommended practices for a successful API Integration with RazorpayX.

**WARN**

**Watch Out!**

RazorpayX Lite is currently not available for new merchants. To set up a new RazorpayX account, refer to [Current Account](https://razorpay.com/docs/build/llm-docs/x/account-types/current-account.md).

Checklist | Description
---
Ensure you have a Live Account | You can access both, Live and Test mode. [Generate Key ID and Secret](https://razorpay.com/docs/build/llm-docs/api/x.md#generate-api-key) in Live mode for real-time transactions.
---
Select the Type of Account | -  [Current Account](https://razorpay.com/docs/build/llm-docs/x/account-types/current-account.md) :  A direct Integration with the bank is more economical. The beneficiary gets the registered company name in the narration field.
-  [RazorpayX Lite](https://razorpay.com/docs/build/llm-docs/x/account-types/razorpayx-lite.md) : A backup channel in case of primary channel failure.

---
Select the Type of API integration | While using standalone API's, the fund account can be re-used, which reduces the response time, which in turn, reduces the load on the data base.
---
Choose a Payout Method | Bank accounts and UPI are available by default. [Cards](https://razorpay.com/docs/build/llm-docs/api/x/payouts-cards.md) require PCI-DSS compliance.
---
Make a [Penny Drop](https://razorpay.com/docs/build/llm-docs/x/fund-account-validation.md) | Improved efficiency as fund accounts are validated before actual payout.
---
Check for Additional Integration | You have the provision to include multiple solutions other than payouts to enhance end-user experience.
---
Use [Source Account Validation](https://razorpay.com/docs/build/llm-docs/x/account-types/source-account-validation.md) | Fund inflow from only trusted sources.
---
Use [Payouts Pro](https://razorpay.com/docs/build/llm-docs/x/payouts/intelligent-payouts.md) | Increase success rate of payouts when the beneficiary bank is down.
---
Check [Idempotency](https://razorpay.com/docs/build/llm-docs/api/x/payout-idempotency/make-request.md) Header ([Handling 5XX error](https://razorpay.com/docs/build/llm-docs/errors/x.md#handling-5xx-errors)) | Eliminate duplicate payouts due to human or network error.
---
Check if Feature Enablement is required | [Contact support](https://razorpay.com/docs/build/llm-docs/x/support.md) and enable the feature in case the required is not available on your dashboard.
---
[Set up Webhooks](https://razorpay.com/docs/build/llm-docs/webhooks/setup-edit-payouts.md) | Receive realtime status update. There is less load on the Dashboard due to reduced fetch calls.
---
[Fetch Transactions API](https://razorpay.com/docs/build/llm-docs/api/x/transactions/fetch-all.md) | Combined with webhook reconciliation, the fetch API's provide an optimal/reliable reconciliation process.
---
[Allowlist IPs](https://razorpay.com/docs/build/llm-docs/x/dashboard/allowlist-ip.md) | Non-allowlisted IP API calls are rejected, hence, improves security.
---
Get [Custom Reports](https://razorpay.com/docs/build/llm-docs/x/reports.md) | Efficiently collate data that is required to ease reconciliation.
---
Enable [Downtime webhook events](https://razorpay.com/docs/build/llm-docs/webhooks.md#payout-downtime-started) | Provides proactive alerts in case of scheduled downtimes.
---
[Contact support team](https://razorpay.com/docs/build/llm-docs/x/support.md) or your RazorpayX POC for Custom Integration | Custom builds are available for specific use cases.

### Related Information

- [Payouts Best Practices](https://razorpay.com/docs/build/llm-docs/x/payouts/best-practices.md)
