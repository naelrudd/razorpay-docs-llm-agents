> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Troubleshooting & FAQs

> Troubleshoot common errors for Razorpay Direct - Credit Card Plugin Shopify integration. Find answers to frequently asked questions.

Available in
🇮🇳 India

> [accordion] Is this new plugin only for businesses who have moved to Shopify’s 1-page checkout?
>
> No, Razorpay Direct - Credit Card plugin is independent of Shopify's 1-page checkout, therefore, anyone can use this plugin.

> [accordion] How can I install Razorpay Direct - Credit Card Plugin?
>
> Follow the [installation steps](https://razorpay.com/docs/payments/ecommerce-plugins/razorpay-direct-credit-card.md) to install the plugin.

> [accordion] Can I use the same MID for Razorpay Direct - Credit Card Plugin and the Razorpay Payment Gateway app?
>
> Yes, you can use the same MID for in-platform/onsite and other Payment Gateway apps (Razorpay Payment Gateway or other Payment Gateways).

> [accordion] Can I use two in-platform/onsite apps for card transactions?
>
> No, a business can only use one in-platform/onsite app. All their card transactions will go through that in-platform/onsite app only.

> [accordion] Is Customer or Dynamic fee bearer supported on the Razorpay Direct - Credit Card Plugin?
>
> No. The Razorpay Direct - Credit Card Plugin supports only the **Platform** fee bearer. **Customer Fee Bearer (CFB)** and **Dynamic Fee Bearer (DFB)** are not supported for this flow, for both domestic and international payments.
>
> Even if CFB or DFB is enabled on your account, the applicable fee (MDR) is deducted from the merchant for payments made through this plugin. The fee is not added to the amount charged to the customer.

> [accordion] What will the UI look like when an in-platform/onsite app and multiple offsite Payment Gateway apps are installed?
>
> The in-platform/onsite cards app always takes precedence and is listed first. All other Payment Gateway apps are listed below, similar to Shopify’s checkout UI.

> [accordion] What if I am not a Razorpay Payment Gateway user? How can I start using the Razorpay Direct - Credit Card Plugin?
>
> You can create a Razorpay account and use the [Razorpay Direct - Credit Card Plugin](https://razorpay.com/docs/payments/ecommerce-plugins/razorpay-direct-credit-card.md) for credit card payments even if you are not currently a [Razorpay Payment Gateway](https://razorpay.com/docs/payments/payment-gateway) user.

> [accordion] How can I verify if webhooks are auto-configured?
>
> To verify if webhooks are enabled:
>
> 1. Log in to the Dashboard and navigate to **Account & Settings**.
> 2. In the **Website and app settings** section, click **Webhooks**.
>
>    ![Navigate to Webhooks](https://razorpay.com/docs/build/browser/assets/images/account-settings-webhooks.jpg)
> 3. Select the relevant webhook **URL**.
> 4. On the right panel, check if the status for `order.paid`, `payment.authorized`, `refund.processed` and `refund.failed` is enabled.

> [accordion] How can I accept payments?
>
> To accept **live** payments, follow the steps mentioned in the [Switch from Test Mode to Live Mode](https://razorpay.com/docs/payments/ecommerce-plugins/razorpay-direct-credit-card.md#switch-from-test-mode-to-live-mode)  section.
