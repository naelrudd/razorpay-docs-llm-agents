> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Steps to integrate your OpenCart Extension with Razorpay Payment Gateway.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Follow the steps given below to integrate Razorpay Payment Gateway with your OpenCart Extension.

> [card] [1. Build Integration](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/open-cart/integration-steps.md#1-build-integration)
>
> Install and configure the OpenCart plugin.

> [card] [2. Test Integration](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/open-cart/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-Live Checklist](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/open-cart/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

## 1. Build Integration

Follow the steps given below:

> [accordion] 1 Install Plugin
>
> 1. Download the latest Source code zip file of the required version of the plugin.
>
> 2. Download the latest release of the OpenCart 4 plugin from the [Releases section](https://github.com/razorpay/razorpay-opencart/releases) in GitHub. Tags for OpenCart 4 are opencart4-6.x.y.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > When installing the Razorpay plugin for Opencart 4, ensure that your zip folder only contains the following folders and file, with no hidden files:
> >
> > * `admin/`
> > * `catalog/`
> > * `system/`
> > * `install.json`
>
> 1. Download the latest release of the OpenCart 3 plugin from the [Releases section](https://github.com/razorpay/razorpay-opencart/releases) in GitHub. Tags for OpenCart 3 are opencart3-1.x.y.
> 2. For OpenCart 2, [download this release](https://github.com/razorpay/razorpay-opencart/releases/tag/opencart2-3.0.0) from GitHub. Tags for OpenCart 2 are opencart2-3.x.y.
> 3. For OpenCart 1.5, [download this release](https://github.com/razorpay/razorpay-opencart/releases/tag/opencart1.5-1.0.0) from GitHub. Tags for OpenCart 1.5 are opencart1.5-1.x.y.
> 4. Navigate to **Extensions** → **Installer** and click **Upload**. Choose the zip file.

> [accordion] 2 Configure OpenCart
>
> Configure OpenCart as given below:
>
> 1. Log in to [OpenCart](https://www.opencart.com/).
> 2. Navigate to the **Admin Panel** → **Extensions** → **Payments** to install the Razorpay Payment Gateway extension.
> 3. Click **Edit**. Complete the following steps:
>    1. Add in your Key\_ID and Key\_Secret generated from the Razorpay Dashboard.
>
>    2. Change extension status to **Enabled**.
>
>    3. Click **Save** to save the extension settings.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Webhook is auto-configured on OpenCart 3 (versions 5.0.0 and above) and OpenCart 4 when you enter and save the API key ID and secret on the plugin settings page. You need to verify if webhooks are enabled on your Razorpay [Dashboard](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/open-cart/troubleshooting-faqs.md#how-can-i-verify-if-webhooks-are-enabled). \\
> >
> > However, for versions lower than 5.0.0, you must [configure webhooks manually](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/open-cart/troubleshooting-faqs.md#my-webhooks-are-not-auto-configured-since-i-am-not-using-the-upgraded-version-of-opencart-how-do-i-manually-configure-webhooks).
>
> #### Create Cron for OpenCart 3
>
> Create a Cron for Webhook using cpanel, follow the steps given below:
>
> 1. Log on to your cPanel Interface.
> 2. Go to **Advanced** section.
> 3. Click **Cron Jobs**.
> 4. Select the specific time from the lists provided (every 5 minutes).
> 5. Enter `https://<shop_url>/index.php?route=extension/payment/razorpay/rzpWebhookCron/` in the **Command** field.
>
> For more information about Cron, refer to [OpenCart Crons](https://docs.opencart.com/developer-guide/cron-jobs).

## 2. Test Integration

After the integration, Razorpay will appear as a payment option on your webpage/app. You need to click the button and make a test transaction to ensure the integration works as expected. You can start accepting actual payments from your customers once the test is successful.

![Open Cart](https://razorpay.com/docs/build/browser/assets/images/pg-opencart-plugin-test.jpg)

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
> You can track the payment status from the Dashboard or by polling APIs.
>
> > [tab] Verify Payment Status From Dashboard
> >
> > 1. Log in to the Razorpay Dashboard and navigate to **Transactions** → **Payments**.
> > 2. Check if a `payment_ID` has been generated and note the status. In case of a successful payment, the status is marked as `captured`.
> >
> >    ![Payment details on Dashboard](https://razorpay.com/docs/build/browser/assets/images/sg-testpayment.jpg)
>
> > [tab] Poll APIs
> >
> > [Poll Payment APIs](https://razorpay.com/docs/sg/api/payments/fetch-all-payments.md) to check the payment status.

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
