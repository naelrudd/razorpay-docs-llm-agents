> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Quickstart Guide

> Complete guide to get started with Razorpay's payments platform.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Welcome to Razorpay! This guide will walk you through setting up your account and choosing the right products for your business needs.

## Step 1: Create an Account

Sign up for a [Razorpay account](https://razorpay.com/us/) and complete the KYC process.

* Start using our products or SDK/API integration in Test Mode during the KYC verification process.
* After KYC completion and testing, live mode unlocks for real payments.

### Test Mode vs Live Mode

> [card] [Test Mode](https://razorpay.com/docs/us/payments/dashboard/test-live-modes.md#test-mode-vs-live-mode)
>
> * Start integration immediately without KYC completion.
> * Use test transactions with dummy data. No real money involved.
> * API keys begin with `rzp_test_`.
> * Perfect for development and testing.

> [card] [Live Mode](https://razorpay.com/docs/us/payments/dashboard/test-live-modes.md#test-mode-vs-live-mode)
>
> * Requires KYC verification (24-48 hours).
> * Accept real customer payments.
> * API keys begin with `rzp_live_`.
> * Full access to all features.

## Step 2: Select Product

[Choose Razorpay products](https://razorpay.com/docs/us/payments.md) based on your business requirements.

> [accordion] No-code Products vs. Products with Coding Requirements
>
> Pick ready-to-use payment solutions with simple setup like [Payment Links](https://razorpay.com/docs/us/payments/payment-links) or refer to our [Payment Gateway SDKs](https://razorpay.com/docs/us/payments/payment-gateway#integrate-payment-gateway-web-mobile-ecommerce-plugins) for advanced integration needs. Explore [no-code and developer-friendly options](https://razorpay.com/docs/us/payments.md#accept-payments).

> [accordion] Solutions by Industry
>
> Find tailored payment solutions designed for your industry: [Payment Gateway](https://razorpay.com/docs/us/payments/payment-gateway) for ecommerce, [Subscriptions](https://razorpay.com/docs/us/payments/subscriptions) for SaaS or comprehensive solutions for traditional retail businesses. View [industry-specific payment solutions](https://razorpay.com/docs/us/payments.md#solutions-by-industry).

> [accordion] Solutions by Platform
>
> Integrate payments seamlessly with popular ecommerce platforms like Shopify, WooCommerce, Magento using [Payment Gateway plugins](https://razorpay.com/docs/us/payments/payment-gateway#integrate-payment-gateway-web-mobile-ecommerce-plugins) or build custom solutions using our [Checkout SDKs](https://razorpay.com/docs/us/payments/payment-gateway#integrate-payment-gateway-web-mobile-ecommerce-plugins) for Go, PHP, Python, Node.js and [mobile platforms](https://razorpay.com/docs/us/payments/payment-gateway#integrate-payment-gateway-web-mobile-ecommerce-plugins) (Android, iOS, React Native, Flutter, Cordova, Capacitor). Browse [platform-specific integration guides](https://razorpay.com/docs/us/payments.md#solutions-by-platform).

## Step 3: Key Dashboard Actions

> [accordion] Generate API Keys
>
> If you are using our APIs, SDKs or plugins, follow these steps to generate API keys for the integration:
>
> 1. Log in to Dashboard.
>
> 2. Navigate to **Account & Settings** → **API Keys** under Website and app settings.
>
> 3. Click **Generate Key**.
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
>
> [API Keys Documentation →](https://razorpay.com/docs/us/payments/dashboard/account-settings/api-keys.md)

> [accordion] Add Team Members
>
> Follow these steps:
>
> 1. Log in to the Dashboard.
> 2. Navigate to **Account & Settings** → **Business settings** → **Manage Team**.
> 3. Click **Invite New Member**.
> 4. Enter their email address and select role from the dropdown.
> 5. Click **Send Invitation**.
>
> [Team Management Guide →](https://razorpay.com/docs/us/payments/dashboard/account-settings/manage-team.md)

> [accordion] Configure Webhooks
>
> We recommend setting up webhooks to receive notifications, if you are integrating with our APIs or SDKs.
>
> 1. Log in to the Dashboard.
> 2. Navigate to **Account & Settings** → **Webhooks**.
> 3. Click **Add New Webhook**.
> 4. Enter your endpoint URL.
> 5. Select events to monitor.
> 6. Add webhook secret for signature verification.
> 7. Save and activate.
>
> [Webhooks Documentation →](https://razorpay.com/docs/us/webhooks)

> [accordion] Payment Capture Settings
>
> Log in to the Dashboard. Navigate to the **Account & Settings** option and scroll to the **Payments Capture** section.
>
> | Option | Description |
> | - | - |
> | Auto-capture all payments | All payments authorized within 3 days from the time of creation are auto-captured. |
> | Auto-capture timeouts | <ul><li>Allows you to define custom auto-capture timeout.</li><li>The minimum value is 12 minutes.</li><li>The maximum value (default) is 3 days.</li></ul> |
> | Manual capture timeout | <ul><li>Allows you to define custom manual capture timeout.</li><li />The minimum value is 12 minutes.<li>The maximum value (default) is 3 days.</li></ul> |
> | Auto-refund speed | Payments in the authorized state are auto-refunded after the timeout. With the Normal Refund option, your payment is refunded to your customer in 5-7 working days. The refund speed selected here is only applicable to payments that are auto-refunded. |
>
> [Payment Capture Guide →](https://razorpay.com/docs/us/payments/payments/capture-settings.md)

## Next Steps

Once your account is created:

1. **Complete KYC**: [Submit KYC documents](https://razorpay.com/docs/us/payments/set-up#2-submit-kyc-details) for live mode activation.
2. **Choose Product/Integration Method**: Select based on your business needs and technical capabilities.
3. **Test Thoroughly**: Use test mode before going live.
4. **Go Live**: Switch to live mode when ready. Use live mode keys if integrating with our APIs/SDKs/plugins.
