> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Steps to integrate your WordPress website with Razorpay Payment Gateway.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Follow the steps given below to integrate Razorpay Payment Gateway with your WordPress website.

> [card] [1. Build Integration](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/wordpress/integration-steps.md#1-build-integration)
>
> Install and configure the WordPress plugin.

> [card] [2. Test Integration](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/wordpress/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-Live Checklist](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/wordpress/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

## 1. Build Integration

Follow the steps given below:

> [accordion] 1 Installation and Configuration
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > This plugin does not support dynamic amount calculation from your webpage. You can accept only fixed amounts using this plugin. Explore our [WooCommerce plugin](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/woocommerce.md) for your use case.
>
> 1. [Download the plugin](https://wordpress.org/plugins/razorpay-quick-payments/) from the WordPress Plugin Directory.
> 2. Open your WordPress site and navigate to **Plugins** → **Add New**.
> 3. Upload the plugin.
>
>    ![Upload plugin screen](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-wordpress-upload-plugin.jpg)
> 4. Click **Activate Plugin**.
>
>    ![Activate plugin](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-wordpress-activate-plugin.jpg)
> 5. Click **Settings**.
>
>    ![Plugin settings](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-wordpress-click-settings.jpg)
> 6. Make the following changes in the **Edit Settings** screen:
>    1. Select **Enable Razorpay Payment Module**.
>    2. Edit **Title** and **Description** as required.
>    3. Add your \[KEY\_ID] and \[KEY\_SECRET]. These can be generated from your Razorpay Dashboard.
>    4. Set the **Payment Action** to **Authorize and Capture** to auto-capture payments.
>    5. Click **Save Changes**.
>
> ![Razorpay PG save settings](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-wordpress-edit-settings.jpg)

> [accordion] 2 Add Custom Fields
>
> 1. In your WordPress site, open the page or blog post where you want the button to appear.
>
> 2. Click the more icon and select **Preferences**.
>
>    ![Select Preferences](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-wordpress-options.jpg)
>
> 3. Click **Panels** and enable the **Custom Fields** checkbox in the **Additional** section. Now you will have the option to add custom fields on your page/blog post.
>
>    ![Preferences custom fields](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-wordpress-custom-fields.jpg)
>
> 4. Scroll down the current page till you see the **Custom fields** section.
>
>    ![Custom field section](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-wordpress-custom-fields-scroll.jpg)
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > If you are using WordPress 4.8 or later, the custom fields can be added via **Screen Option**. If you are still not able to view the custom field, refer to the [FAQs](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/wordpress/faqs.md#i-am-unable-to-view-the-custom-fields-under-the-screen-options-menu-what-should-i-do).
>
> 1. Add the following three custom fields as metadata:
>    1. amount (in SGD).
>    2. name (name of the product).
>    3. description (description of the product that is being sold).
>
> ![Custom fields amount name description](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-wordpress-custom-fields-added.jpg)
>
> 1. Add the `[RZP]`(shortcode indicated by square brackets) in the content section to display the **Pay with Razorpay** button anywhere.
>
>    ![RZP shortcode](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-wordpress-shortcode.jpg)
>
> 2. Publish or update the page. The page appears with the **Pay with Razorpay** button.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > If the payment button does not appear, ensure the Button script is placed inside the `<form>` tag. This issue might be caused by certain cache plugins (for example, SpeedyCache) or Optimizer plugins (for example, SiteGround Optimizer). To resolve it, please deactivate these plugins. Once they are deactivated, the payment button should work properly.

## 2. Test Integration

After the integration, a **Pay** button will appear on your web page/app. You need to click the button and make a test transaction to ensure the integration works as expected. You can start accepting actual payments from your customers once the test is successful.

You can make test payments using one of the payment methods configured at the Checkout.

* No money is deducted from the customer's account as this is a simulated transaction.
* Ensure you have entered the API keys generated in the test mode in the Checkout code.

> [accordion] Supported Payment Methods
>
> After the integration is complete, a **Pay** button appears on your webpage/app.
>
> Click the button and make a test transaction to ensure the integration is working as expected. You can start accepting actual payments from your customers once the test transaction is successful.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > This is a mock payment page that uses your test API keys, test card and payment details.
> >
> > * Ensure you have entered only your [Test Mode API keys](https://razorpay.com/docs/sg/payments/dashboard/account-settings/api-keys.md#generate-api-keys) in the Checkout code.
> > * Test mode features a mock bank page with **Success** and **Failure** buttons to replicate the live payment experience.
> > * No real money is deducted due to the usage of test API keys. This is a simulated transaction.
>
> Following are all the payment modes that the customer can use to complete the payment on the Checkout. Some of them are available by default, while others may require approval from us. Raise a request from the Dashboard to enable such payment methods.
>
> | Payment Method | Code | Availability |
> | - | - | - |
> | [Debit and Credit Cards](https://razorpay.com/docs/sg/payments/payment-methods/cards.md) | `card` | ✓ |
> | [PayNow](https://razorpay.com/docs/sg/payments/payment-methods/paynow.md) | `paynow` | ✓ |
>
> You can make test payments using one of the payment methods configured at the Checkout.
>
> > [accordion] Cards
> >
> > You can use one of the following test cards to test transactions for your integration in Test Mode.
> >
> > | Card Network | Card Number | CVV & Expiry Date |
> > | - | - | - |
> > | Mastercard | 5272 0088 0623 5705 | Use a random CVV and any future date ^^ |
> > | Visa | 4111 1111 1111 1112 | |
> >
> > Check the following lists:
> >
> > * [Supported Card Networks](https://razorpay.com/docs/sg/payments/payment-methods/cards.md).
> > * [Cards Error Codes](https://razorpay.com/docs/sg/errors/payments/cards.md).
>
> > [accordion] PayNow
> >
> > You can scan the QR code and make the payment using your PayNow-enabled bank app. Razorpay will redirect to a mock page where you can make the payment a success or a failure. Since this is Test Mode, we will not redirect you to the bank portals. Know more about [PayNow](https://razorpay.com/docs/sg/payments/payment-methods/paynow.md).

> [accordion] Verify Payment Status
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > On the Razorpay Dashboard, ensure that the payment status is `captured`. Refer to the payment capture settings page to know how to [capture payments automatically](https://razorpay.com/docs/sg/payments/payments/capture-settings.md).
>
> > [accordion] You can track the payment status in three ways:
> >
> > > [tab] Verify Status from Dashboard
> > >
> > > To verify the payment status from the Razorpay Dashboard:
> > >
> > > 1. Log in to the Razorpay Dashboard and navigate to **Transactions** → **Payments**.
> > > 2. Check if a **Payment Id** has been generated and note the status. In case of a successful payment, the status is marked as **Captured**.
> > >
> > > ![Payment details on Dashboard](https://razorpay.com/docs/build/browser/assets/images/sg-testpayment.jpg)
> >
> > > [tab] Subscribe to Webhook Events
> > >
> > > You can use Razorpay webhooks to configure and receive notifications when a specific event occurs. When one of these events is triggered, we send an HTTP POST payload in JSON to the webhook's configured URL. Know how to [set up webhooks.](https://razorpay.com/docs/sg/webhooks/setup-edit-payments.md)
> > >
> > > #### Example
> > >
> > > If you have subscribed to the `order.paid` webhook event, you will receive a notification every time a customer pays you for an order.
> >
> > > [tab] Poll APIs
> > >
> > > [Poll Payment APIs](https://razorpay.com/docs/sg/api/payments/fetch-all-payments.md) to check the payment status.

## 3. Go-live Checklist

Follow these steps before taking the integration live:

> [accordion] 1 Accept Live Payments
>
> Perform an end-to-end simulation of funds flow in the Test Mode. Once confident that the integration is working as expected, switch to the Live Mode and start accepting payments from customers.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Ensure you are switching your test API keys with API keys generated in Live Mode.
>
> To generate API Keys in Live Mode on your Razorpay Dashboard:
>
> 1. Log in to the Razorpay Dashboard and switch to **Live Mode** on the menu.
> 2. Navigate to **Account & Settings** → **API Keys** → **Generate Key** to generate the API Key for Live Mode.
> 3. Download the keys and save them securely.
> 4. Replace the Test API Key with the Live Key in the Checkout code and start accepting actual payments.

> [accordion] 2 Payment Capture
>
> After payment is `authorized`, you need to capture it to settle the amount to your bank account as per the settlement schedule. Payments that are not captured are auto-refunded after a fixed time.
>
> > [!WARNING]
> >
> > **Watch Out**
> >
> > * You should deliver the products or services to your customers only after the payment is captured. Razorpay automatically refunds all the uncaptured payments.
> > * You can track the payment status using our [Fetch a Payment API](https://razorpay.com/docs/sg/api/payments/fetch-with-id.md) or webhooks.
>
> > [tab] Auto-capture Payments (Recommended)
> >
> > Authorized payments can be automatically captured. You can auto-capture all payments [using global settings](https://razorpay.com/docs/sg/payments/payments/capture-settings.md#auto-capture-all-payments) on the Razorpay Dashboard. Know more about [capture settings for payments](https://razorpay.com/docs/sg/payments/payments/capture-settings.md).
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > Payment capture settings work only if you have integrated with Orders API on your server side. Know more about the [Orders API](https://razorpay.com/docs/sg/api/orders/create.md).
>
> > [tab] Manually Capture Payments
> >
> > Each authorized payment can also be captured individually. You can manually capture payments using [Payment Capture API](https://razorpay.com/docs/sg/api/payments/capture.md) or [Dashboard](https://razorpay.com/docs/sg/payments/payments/dashboard.md#manually-capture-payments). Know more about [capture settings for payments](https://razorpay.com/docs/sg/payments/payments/capture-settings.md).
