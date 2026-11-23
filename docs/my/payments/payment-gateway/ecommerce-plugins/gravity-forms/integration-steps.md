> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Steps to integrate your WordPress website using the Gravity Forms plugin.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Follow the steps given below to integrate Razorpay Curlec Payment Gateway with your Gravity Forms website.\


> [card] [1. Build Integration](https://razorpay.com/docs/my/payments/payment-gateway/ecommerce-plugins/gravity-forms/integration-steps.md#1-build-integration)
>
> Install and configure the WordPress plugin.

> [card] [2. Test Integration](https://razorpay.com/docs/my/payments/payment-gateway/ecommerce-plugins/gravity-forms/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-Live Checklist](https://razorpay.com/docs/my/payments/payment-gateway/ecommerce-plugins/gravity-forms/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

## 1. Build Integration

Follow the steps given below:

> [accordion] 1 Download Razorpay Gravity Forms Plugin and Configure Settings
>
> Follow the steps given below:
>
> 1. Download and install the Razorpay Gravity Forms Plugin. You can do this using either of these methods:
>    * [Download the latest version of the plugin from the WordPress Plugin Directory](https://github.com/razorpay/razorpay-gravity-forms/releases/latest) and add the zip file to your WordPress website's **Plugins** folder.
>    * Add the plugin directly on your WordPress website from the **Plugin** page.
>
>      ![add wordpress plugin on website](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-gravity-forms-add-plugin-wordpress.jpg)
> 2. On your WordPress site, activate the plugin in the **WordPress Plugin Manager**. \\
>
>    ![activate plugin](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-gravity-forms-activate-plugin.jpg)
> 3. Click **Settings**. \\
>
>    ![open plugin settings](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-gravity-forms-plugin-settings.jpg)
> 4. Configure the following information and click **Update Settings**:
>    * Add in your \[KEY\_ID] and \[KEY\_SECRET] generated from the Razorpay Curlec Dashboard.
>    * **Payment Action**: Set this to **Authorize and Capture**.
> 5. Select the currency in which the payment must be accepted.
>    1. Navigate to **Forms** → **Settings**.
>    2. Under **General Settings**, go to the **Currency** field and choose the relevant currency. For this example, we will select **Indian Rupee**.
>       ![change currency](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-gravity-forms-change-currency.jpg)

> [accordion] 2 Create a Gravity Form
>
> To create a Gravity Form:
>
> 1. Navigate to **Forms** → **New Form** and click **Add New**.
> 2. Enter the form title and description in the **Create a New Form** dialog box.
> 3. Click **Create Form**.
> 4. Before entering the product details, you must select whether you are selling a subscription or a product/service. Navigate to **Settings** → **Razorpay Curlec** and configure the **Razorpay Curlec Feed**.
>    1. In the **Razorpay Curlec Feed** settings, click **Add New**.
>    2. Add a name for the feed. For example, `Ooty Green Tea`.
>    3. Select `Products and Services` as the **Transaction Type**.
>    4. Click **Update Settings**.
>
>       ![select products and services](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-gravity-forms-feed-settings.jpg)
> 5. Click **Edit** to start adding product details:
>
>    ![](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-gravity-forms-edit-form.jpg)
>
>    1. Click **Pricing Fields** and select **Product**.
>
>       ![configure gravity form](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-gravity-forms-configure-form.jpg)
>    2. Click the form to enter the product details and click **Update**.
>       1. **Field Label**: Enter the product name. For example, `Ooty Green Tea`.
>       2. **Description**: Enter a description for the product.
>       3. **Field Type**: Select the field type as required.
>       4. **Price**: Enter the product price in INR. For example, `399.99`.
>       5. **Disable Quantity Field**: Do not select this option if your customer wants to choose a quantity.
>       6. **Rules**: Enable the **Required** check box to make the quantity field mandatory.
>          ![add product details](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-gravity-forms-product-details.jpg)
>
> The form is now ready to be added to your web pages.

> [accordion] 3 Add the Form to a Webpage
>
> To add the form on a webpage:
>
> 1. Click **Pages** to navigate to the relevant page.
> 2. Add a block and click the form icon.
>
>    ![click form icon](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-gravity-forms-form-icon.jpg)
> 3. Select the form to be added to the page.
>
>    ![select form](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-gravity-forms-select-form.jpg)
> 4. Once the form is added, you can choose to hide the form title and description.
> 5. Click **Publish** or **Update**.

> [!NOTE]
>
> **Handy Tips**
>
> Webhook is auto-configured when you enter and save the API key ID and secret on the plugin settings page. You need to [verify if webhooks are enabled](https://razorpay.com/docs/my/payments/payment-gateway/ecommerce-plugins/gravity-forms/troubleshooting-faqs.md#how-can-i-verify-if-webhooks-are-enabled) on your Razorpay Curlec Dashboard. However, for versions lower than 1.3.2, you need to [configure webhooks manually](https://razorpay.com/docs/my/payments/payment-gateway/ecommerce-plugins/gravity-forms/troubleshooting-faqs.md#my-webhooks-are-not-auto-configured-since-i-am-not-using-the-upgraded-version-of-gravity-forms-how-do-i-manually-configure-webhooks).

## 2. Test Integration

After the integration, Razorpay Curlec will appear as a payment option on your web page/app. You need to click the button and make a test transaction to ensure the integration works as expected. You can start accepting actual payments from your customers once the test is successful.

![Gravity Forms](https://razorpay.com/docs/build/browser/assets/images/pg-gravity-forms-plugin.jpg)

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
> > * Ensure you have entered only your [Test Mode API keys](https://razorpay.com/docs/my/payments/dashboard/account-settings/api-keys.md#generate-api-keys) in the Checkout code.
> > * Test mode features a mock bank page with **Success** and **Failure** buttons to replicate the live payment experience.
> > * No real money is deducted due to the usage of test API keys. This is a simulated transaction.
>
> Following are all the payment modes that the customer can use to complete the payment on the Checkout. Some of them are available by default, while others may require approval from us. Raise a request from the Dashboard to enable such payment methods.
>
> | Payment Method | Code | Availability |
> | - | - | - |
> | Debit and Credit Cards | `card` | ✓ |
> | FPX | `fpx` | ✓ |
> | Wallets | `wallet` | ✓ |
>
> You can make test payments using one of the payment methods configured at the Checkout.
>
> > [accordion] FPX
> >
> > You can select any of the listed banks. After choosing a bank, Razorpay Curlec will redirect to a mock page where you can make the payment a `success` or a `failure`. Since this is Test Mode, we will not redirect you to the bank login portals.
>
> > [accordion] Wallet
> >
> > You can select any of the listed wallets. After choosing a wallet, you will be redirected to a mock page where you can make the payment `success` or a `failure`. Since this is Test Mode, we will not redirect you to the wallet login portals.
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > iOS integration for Touch'n Go wallet is currently unavailable. We will be adding support for it soon.
>
> > [accordion] Cards
> >
> > You can use one of the following test cards to test transactions for your integration in Test Mode.
> >
> > | Card Network | Card Number | CVV & Expiry Date |
> > | - | - | - |
> > | Mastercard | 5272 0088 0623 5704 | Use a random CVV and any future date ^^ |
> > | Visa | 4842 7930 0208 6571 | |
> >
> > Check the following lists:
> >
> > * [Cards Error Codes](https://razorpay.com/docs/my/errors/payments/cards.md).

> [accordion] Verify Payment Status
>
> You can track the payment status from the Dashboard or by polling APIs.
>
> > [tab] Verify Payment Status From Dashboard
> >
> > 1. Log in to the Razorpay Curlec Dashboard and navigate to **Transactions** → **Payments**.
> > 2. Check if a `payment_ID` has been generated and note the status. In case of a successful payment, the status is marked as `captured`.
> >
> >    ![Payment details on Dashboard](https://razorpay.com/docs/build/browser/assets/images/my-testpayment.jpg)
>
> > [tab] Poll APIs
> >
> > [Poll Payment APIs](https://razorpay.com/docs/my/api/payments/fetch-all-payments.md) to check the payment status.

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
> To generate API Keys in Live Mode on your Razorpay Curlec Dashboard:
>
> 1. Log in to the Razorpay Curlec Dashboard and switch to **Live Mode** on the menu.
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
> > * You should deliver the products or services to your customers only after the payment is captured. Razorpay Curlec automatically refunds all the uncaptured payments.
> > * You can track the payment status using our [Fetch a Payment API](https://razorpay.com/docs/my/api/payments/fetch-with-id.md) or webhooks.
>
> > [tab] Auto-capture Payments (Recommended)
> >
> > Authorized payments can be automatically captured. You can auto-capture all payments [using global settings](https://razorpay.com/docs/my/payments/payments/capture-settings.md#auto-capture-all-payments) on the Razorpay Curlec Dashboard. Know more about [capture settings for payments](https://razorpay.com/docs/my/payments/payments/capture-settings.md).
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > Payment capture settings work only if you have integrated with Orders API on your server side. Know more about the [Orders API](https://razorpay.com/docs/my/api/orders/create.md).
>
> > [tab] Manually Capture Payments
> >
> > Each authorized payment can also be captured individually. You can manually capture payments using [Payment Capture API](https://razorpay.com/docs/my/api/payments/capture.md) or [Dashboard](https://razorpay.com/docs/my/payments/payments/dashboard.md#manually-capture-payments). Know more about [capture settings for payments](https://razorpay.com/docs/my/payments/payments/capture-settings.md).
