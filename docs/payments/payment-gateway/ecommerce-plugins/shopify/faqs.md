> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Troubleshooting & FAQs

> Troubleshoot common errors and find answers to frequently asked questions about Shopify.

Available in
🇮🇳 India

## Integration & Setup

> [accordion] Why can't I find the Razorpay plugin on the Shopify App Store?
>
> In your Shopify admin, the Razorpay plugin is listed as **01 Cards, UPI, NB, Wallets by Razorpay**. Your customers see it at checkout as **Razorpay Secure (UPI, Card, Int'l Card, Apple Pay)**. The plugin was earlier listed as **1Razorpay - UPI, Cards, Wallets, NB** and **All-in-one Razorpay Payment Gateway**. If you are unable to find the plugin, search for **01 Cards, UPI, NB, Wallets by Razorpay** under **Search by provider** in your Shopify payment settings or use the [direct link](https://accounts.shopify.com/store-login?redirect=settings%2Fpayments%2Falternative-providers%2F1058839) to access the app on your Shopify store.

> [accordion] How do I integrate Razorpay Secure with my Shopify store?
>
> Follow the [build integration](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/integration-steps.md#1-build-integration) steps to integrate Razorpay Secure with your Shopify store.

> [accordion] Do I need API keys to integrate a payment app with Shopify?
>
> No, API keys are not required to integrate a payment app with Shopify. OAuth is used to handle the authentication process.

> [accordion] I tried connecting Razorpay Secure to my AxisRazorpay account but was unsuccessful. When I try to reconnect, the screen appears different. How should I proceed?
>
> Follow the steps given below to connect Razorpay Secure with your Razorpay account:
>
> 1. When you try to reconnect, you will get the following screen. Click **Manage**.
>
>    ![reconnect Razorpay Secure](https://razorpay.com/docs/build/browser/assets/images/razorpay-secure-reconnect.jpg)
>
> 2. You will be redirected to a landing page. Click **I am an existing user**.
>
>    ![Existing Merchant Shopify](https://razorpay.com/docs/build/browser/assets/images/shopify-existing-merchant.jpg)
>
> 3. Scroll down and click **Login**.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Make sure you log in with **owner** credentials to connect Razorpay with Shopify successfully.
>
> ![Razorpay login](https://razorpay.com/docs/build/browser/assets/images/shopify-login-v2.gif)
>
> 4. Click **Activate** on the activation screen on your Shopify Dashboard. \\
>
>    ![Shopify Authorize](https://razorpay.com/docs/build/browser/assets/images/shopify-1razorpay-activate.jpg)
>
> **Razorpay Secure (UPI, Card, Int'l Card, Apple Pay)** now appears as a Payment Gateway on your Shopify Store checkout.\\
>
> ![Shopify Checkout](https://razorpay.com/docs/build/browser/assets/images/shopify-v2-checkout.jpg)
>
> This completes your integration.

> [accordion] Why is the Activate button disabled?
>
> The Activate button may be disabled due to the plugin being integrated into another account or keyless authentication not being enabled. To enable the Activate button:\\
>
> * **Check for Integration with Another Account:** Verify if you have integrated your Shopify Store with a different Razorpay MID. If yes, revoke access under applications and retry the Razorpay Secure [integration steps](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/integration-steps.md#1-build-integration). \\
>
> * **Enable Keyless Authentication:** Ensure keyless authentication is enabled from Razorpay's end. To enable keyless authentication contact our [Support team](https://razorpay.com/support/).

> [accordion] I am getting the following error message, "Email ID Mismatch." Why?
>
> This error occurs when there is a discrepancy between the email IDs used in Shopify and Razorpay.\\
>
> You can [update the email ID](https://razorpay.com/docs/payments/dashboard/account-settings/account-details.md#update-login-email) on Razorpay to match the one used in Shopify. Verify that the email ID associated with owner access on Razorpay matches the one used in Shopify.

> [accordion] I get a blank screen when I try to log in to the  account while integrating/migrating Razorpay Secure, and I am unable to proceed further. How to proceed further?
>
> A blank screen appears when the email id used to log in to Razorpay doesn't match the email ID registered with owner access on Razorpay. Make sure that you log in using the correct email ID.

> [accordion] How do I uninstall Razorpay payment apps from Shopify?
>
> To uninstall any Razorpay payment app from your Shopify store, follow these steps:
>
> 1. Log in to your Shopify admin panel and navigate to **Settings**→**Payments**.
> 2. Click **Add payment methods**.
> 3. Click Search by provider and type **Razorpay**. This will show all the Razorpay payment apps installed on your Shopify store. Click the Razorpay app that you wish to uninstall.
>
>    ![Search Razorpay in Payment Providers](https://razorpay.com/docs/build/browser/assets/images/search-razorpay-payment-provider.jpg)
> 4. Scroll down to the bottom and click the **Uninstall** button to remove the app from your Shopify store.
>
>    ![Uninstall the app](https://razorpay.com/docs/build/browser/assets/images/uninstall-app.jpg)
>
> This will successfully uninstall the selected Razorpay payment app from your Shopify store.

> [accordion] What should I do if I am confused between legacy and current plugin versions?
>
> To avoid confusion, uninstall the legacy version of the plugin and [re-install](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/integration-steps.md#1-build-integration) the current plugin version (Razorpay Secure).

> [accordion] Our Payment Gateway stopped displaying after migrating to Shopify. How can we reactivate it?
>
> After migrating your website to Shopify, you need to integrate with the official Shopify Razorpay Secure plugin, as your previous Payment Gateway integration from the old platform will not be carried over. Follow the [integration steps](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/integration-steps.md) and once activated, your payment gateway will be displayed at checkout, allowing you to accept payments.

## Migration to Razorpay Secure

> [accordion] Why do I need to upgrade to Razorpay Secure?
>
> Shopify has launched a new payment platform, which requires existing and new payment apps to meet a new set of secure guidelines. Razorpay has built a new app, Razorpay Secure, that complies with these new rules.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Your customers' payments will fail if you do not upgrade to the Razorpay Secure app at the earliest. So, you must upgrade to Razorpay Secure to provide an uninterrupted payment experience to your customers.

> [accordion] How do I upgrade to Razorpay Secure?
>
> You can upgrade to Razorpay Secure by following a simple migration process. Know more about [how to migrate to Razorpay Secure](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/migration-steps.md).

> [accordion] Who all need to migrate to Razorpay Secure app?
>
> All Shopify and Shopify Plus merchants must migrate to the Razorpay Secure payments app to continue accepting payments without service disruptions.

> [accordion] Who can perform the migration process for Razorpay Secure app?
>
> Only a Shopify Store Owner or Administrator can complete the migration for a Shopify account. They will need Razorpay account credentials to connect the two applications.

> [accordion] What changes for me as a  merchant after I upgrade to Razorpay Secure?
>
> Nothing will change for you or your customers if you upgrade to the Razorpay Secure app. If you do not migrate, Razorpay will not appear as a payment option for your customers once the old Razorpay app is deprecated.

> [accordion] What if I do not deactivate the older Razorpay plugin?
>
> If you do not deactivate the older Razorpay plugin, two Razorpay payment gateways will be visible to your customers on your store checkout, which may lead to confusion.

## Checkout and Payment Issues

> [accordion] My customer is getting the following error when they make payments on my Shopify store, "There was an issue processing your payment. Try again or use a different payment method." What should I do?
>
> Your customers may get the following error when making payments.
>
> ![Shopify page payment error](https://razorpay.com/docs/build/browser/assets/images/econ-shopify-payment-error.jpg)
>
> Uninstall and reinstall the Razorpay Secure app from your Shopify store to resolve the error.
>
> To uninstall the app:
>
> 1. Open your Shopify store in incognito mode.
> 2. Navigate to **Settings** → **Payments**. Click **Manage** on **01 Cards, UPI, NB, Wallets by Razorpay**.
> 3. Go to **Deactivate 01 Cards, UPI, NB, Wallets by Razorpay** and click **Uninstall 01 Cards, UPI, NB, Wallets by Razorpay**. This uninstalls the app.
>
> Follow the [build integration](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/integration-steps.md#1-build-integration) steps to install the plugin again.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Ensure you uninstall and reinstall the app instead of only deactivating it.
>
> If your plugin still does not accept payments, contact [Support team](https://razorpay.com/support/).

> [accordion] Why is my Shopify checkout showing only Razorpay Direct (cards) instead of all payment methods?
>
> You might have only integrated with Razorpay Direct - Credit Card Plugin, which supports card payments only. To accept UPI, Netbanking, Wallets and Cards at checkout, you need to [integrate with Razorpay Secure](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/integration-steps.md), which is Razorpay's full payment gateway app for Shopify.

> [accordion] The Razorpay payment option has disappeared from my Shopify checkout after I added another payment provider. Even after removing it, Razorpay does not show up and I see the error "This store can't accept payments right now." What should I do?
>
> Active payment method customisations typically cause this issue in your Shopify admin. When adding multiple payment providers, these customisations may conflict and prevent Razorpay from appearing at checkout.
>
> To fix this, follow the steps below:
>
> 1. Navigate to **Shopify Admin** → **Settings** → **Payments** → **Payment Method Customizations**.
> 2. **Disable or remove all customizations** listed under this section.
> 3. Save the changes and refresh the checkout page.
>
> Once the payment customizations are removed, the Razorpay payment option should reappear at checkout.
>
> If the issue persists, contact our [Support team](https://razorpay.com/support/).

> [accordion] How can I test a payment for Razorpay Secure on the Shopify store?
>
> You can test a payment for Razorpay Secure on the Shopify store by switching to test mode. Know more about [how to test a transaction in test mode.](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/integration-steps.md#1-make-a-test-transaction-in-test-mode)
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Once you successfully make a test transaction, ensure you uncheck the **Enable test mode** option to accept live payments.

> [accordion] After migrating to Razorpay Secure, the checkout option for Razorpay Secure appears at the bottom of the list of gateways. Is it possible to move the  checkout option to the top of the list of gateways?
>
> No. It is not possible to rearrange the order payment options via the store settings of the Shopify Dashboard as it is a limitation from Shopify's end.

> [accordion] How can I enable automated payment receipts with GST split?
>
> Razorpay facilitates only payment collection. The partner is solely responsible for sending invoices or payment receipts with GST details to customers. To provide GST-compliant receipts, partners can use [Razorpay Invoice](https://razorpay.com/docs/payments/invoices) product when collecting payments.

## Account Management

> [accordion] Can I connect two merchant ids (MIDs) to the same Shopify Store?
>
> No, currently you can connect only one MID to your Shopify Store.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Make sure you log in using the correct Razorpay merchant id (MID) credentials via the Shopify Dashboard.

> [accordion] Can I integrate a second Razorpay account with my Shopify store?
>
> A Shopify store can be linked to only one Razorpay account (MID) at a time. You cannot run two Razorpay accounts on the same store simultaneously, but you can switch the store to a different account. See [how to relink your Shopify store to a different Razorpay account (MID)](#how-do-i-relink-my-shopify-store-to-a-different-razorpay-account-mid).

> [accordion] How do I relink my Shopify store to a different Razorpay account (MID)?
>
> You can relink your Shopify store to a different Razorpay account (MID) yourself; you do not need to contact Razorpay to delink the old MID. Follow the same steps you used for your first-time installation:
>
> 1. On the **old** Razorpay account, navigate to **Account & Settings** → **Applications** and revoke Shopify access.
> 2. [Uninstall](#how-do-i-uninstall-razorpay-payment-apps-from-shopify) the **01 Cards, UPI, NB, Wallets by Razorpay** app from your Shopify store.
> 3. Reinstall the app and activate it by logging in with your **new** Razorpay account, following the [integration steps](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/integration-steps.md#1-build-integration).
>
> Once you activate the app with the new account, your Shopify store is linked to the new MID.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Make sure you log in with **store owner** credentials and the correct Razorpay merchant id (MID) to connect the new account successfully.

> [accordion] I have two ecommerce websites owned by my company. If I connect both websites to my Razorpay account, will the customers be redirected to the correct webpage after payment?
>
> Yes, when customers pay through Razorpay on either of your connected websites, they will be redirected to the website they purchased from.

## Pricing and Settlements

> [accordion] Will I be charged extra for integrating/migrating to Razorpay Secure app?
>
> No, there will be no additional charges. Your pricing plan will remain the same as earlier.

> [accordion] When will my funds be settled?
>
> Funds will be settled as per the existing settlement schedule. There will be no change to it.

## Verification and Order Processing

> [accordion] Should I verify a payment on Razorpay before processing an order on Shopify?
>
> Yes. The Razorpay Shopify integration works on payment auto-capture mode, so most Razorpay authorised payments get auto-captured. However, there is a 0.5% chance that an authorised payment encounters a gateway capture failure and gets auto-refunded. Before processing an order, verify the payment status on the [Razorpay Dashboard](https://razorpay.com/docs/payments/dashboard) or reconcile it from the [reports](https://razorpay.com/docs/payments/dashboard/reports.md).

## Features and Limitations

> [accordion] Can I enable Subscriptions on my Shopify store?
>
> No, Shopify does not support Subscriptions. The Ecommerce platforms that support Subscriptions are Woocommerce, Magento, and Open Cart.

> [accordion] Does the Shopify Razorpay Secure plugin support 3 or 0 decimal unit currencies?
>
> The Shopify Razorpay Secure plugin currently supports only currencies that use 2 decimal units. For example: USD, EUR, INR. It does not support currencies with 0 decimal (for example, JPY) or 3 decimal units (for example, BHD).

> [accordion] How do I integrate Meta Pixel to accept payments through Meta Ads?
>
> Razorpay does not provide a direct plugin integration for accepting payments through Meta Ads. However, you can use Razorpay Payment Pages with [Facebook Pixel and Google Tracking ID](https://razorpay.com/docs/payments/payment-pages/plugins-add-ons.md) to track payments and conversions from your Ad campaigns.

> [accordion] Can I use Razorpay Route API with my Shopify store?
>
> No, Razorpay Route API is not supported for Shopify integration. Only the [Razorpay Secure plugin](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/integration-steps.md) is supported for Shopify stores.
