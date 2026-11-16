> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Quickstart Guide

> Complete guide to get started with Razorpay's Banking platform.

Available in
🇮🇳 India

Welcome to Razorpay! This guide will walk you through setting up your account and how to use our solutions for your business needs.

## Step 1: Create an Account

You can [sign up for a RazorpayX account](https://x.razorpay.com/auth/signup) or if you are already a Razorpay user, use your existing credentials to sign in. After KYC completion and testing, live mode unlocks for real payments.

### Test Mode vs Live Mode

> [card] [Test Mode](https://razorpay.com/docs/payments/dashboard/test-live-modes.md#test-mode-vs-live-mode)
>
> * Start without KYC completion.
> * Use test transactions with dummy data. No real money involved.
> * API keys begin with `rzp_test_`.
> * Perfect for development and testing.

> [card] [Live Mode](https://razorpay.com/docs/payments/dashboard/test-live-modes.md#test-mode-vs-live-mode)
>
> * Requires KYC verification (24-48 hours).
> * Start creating real customer payouts.
> * API keys begin with `rzp_live_`.
> * Full access to all features.

## Step 2: Select Solutions

Choose solutions based on your business requirements.

> [accordion] Payouts
>
> With the Payouts module, you can:
>
> * Make instant Payouts individually or in bulk for chargebacks or cashbacks.
> * Use IMPS, NEFT, RTGS, UPI or Bank Transfer to pay. Know more about [creating a payout](https://razorpay.com/docs/x/payouts#create-a-payout).

> [accordion] Payout Links
>
> Send funds to anyone, even when you do not have their bank account details. You just need to enter the recipient's name, phone number or email, and the amount to be paid to create a Payout Link. [Know more about Payout Links](https://razorpay.com/docs/x/payout-links).

> [accordion] RazorpayX Vendor Payouts
>
> Manage your vendor payments effortlessly with Vendor Payouts. You can choose to settle the dues against all the invoices raised by the vendor in one go, or make selective payments. [Explore Vendor Payment capabilities on RazorpayX](https://razorpay.com/docs/x/vendor-payments).

> [accordion] RazorpayX Tax Payments
>
> Use RazorpayX to automate direct tax payments via a user-friendly interface. Know more about [RazorpayX Tax Payments](https://razorpay.com/docs/x/tax-payments).

> [accordion] RazorpayX Payroll
>
> You can manage payroll, attendance, reimbursements and compliances - all in a single Dashboard! RazorpayX Payroll fully automates payroll solutions for you., including tax and filings. Know more about [RazorpayX Payroll.](https://razorpay.com/docs/payroll.md).

## Step 3: Key Dashboard Actions

> [accordion] Generate API Keys
>
> If you are using our APIs, follow these steps to [generate API keys](https://razorpay.com/docs/api/x) for the integration:
>
> 1. Log in to Dashboard.
>
> 2. Navigate to the user icon in the top-right corner of the screen and click **My Profile** → **My Accounts & Settings**.
>
> 3. Navigate to **Developer Controls** and click **Generate Key**.
>
> 4. Download and save **Key ID** and **Key Secret** securely.
>
> > [!WARNING]
> >
> > **Important:**
> >
> > * Only Owner and Admin roles can access API keys.
> > * Generate separate keys for Test and Live modes.
> > * Key Secret is only visible at generation time.

> [accordion] Add Team Members
>
> Follow these steps:
>
> 1. Log in to the Dashboard.
> 2. Navigate to **My Account & Settings** → **Team Management** → **Manage Team**.
> 3. Click **+ Team Member**.
> 4. Enter their email address and select role from the dropdown.
> 5. Click **Send Invite**.

> [accordion] Configure Webhooks
>
> We recommend setting up webhooks to receive notifications, if you are integrating with our APIs.
>
> 1. Log in to the Dashboard.
> 2. Navigate to **My Account & Settings** → **Developer Controls**.
> 3. Click **Add Webhooks**.
> 4. Enter your endpoint URL.
> 5. Select events to monitor.
> 6. Add webhook secret for signature verification.
> 7. Click **SAVE** to enable the webhook.
>
> [Webhooks Documentation →](https://razorpay.com/docs/webhooks)

## Next Steps

Once your account is created:

1. **Complete KYC**: [Submit KYC documents](https://razorpay.com/docs/payments/set-up#kyc-details) for live mode activation.
2. **Choose Solution**: Select solutions based on your business needs and technical capabilities.
3. **Test Thoroughly**: Use test mode before going live.
4. **Go Live**: Switch to live mode when ready. Use live mode keys with our APIs.
