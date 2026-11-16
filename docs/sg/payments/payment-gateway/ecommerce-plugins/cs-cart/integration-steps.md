> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Steps to integrate your CS-Cart website with Razorpay Payment Gateway.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Follow the steps given below to integrate Razorpay Payment Gateway with your CS-Cart website.\


> [card] [1. Build Integration](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/cs-cart/integration-steps.md#1-build-integration)
>
> Install and configure the CS-Cart plugin.

> [card] [2. Test Integration](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/cs-cart/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-Live Checklist](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/cs-cart/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

## 1. Build Integration

Follow the steps given below:

> [accordion] 1 Installation
>
> 1. Ensure you have the latest version of CS-Cart installed.
> 2. Download the latest [Source code zip file](https://github.com/razorpay/razorpay-cscart/releases) from the releases section. Unzip the repository.
> 3. Run the `install.razorpay.sql` file, which can be found inside the unzipped package, against your CS-Cart database. To do this, you can either:
>    * Use phpMyAdmin to import the file into your CS-Cart database.
>    * Copy and paste the content and run it directly in your MySQL shell.
> 4. Upload the rest of the plugin's contents to your CS-Cart Installation directory.
>    1. The app folder's content goes into your CS-Cart Installation directory.
>    2. The content of the design folder goes into the design folder in your CS-Cart Installation directory.

> [accordion] 2 Configuration
>
> 1. Log in to CS-Cart as administrator.
> 2. Navigate to **Administration** → **Payment Methods**.
> 3. Add a new payment method.
> 4. Select **Razorpay** from the list and then click **Save**. Select `cc_outside.tpl` for the template.
> 5. Navigate to the **Configure** tab.
> 6. Add your \[KEY\_ID] and \[KEY\_SECRET] generated from the Razorpay Dashboard.

> [!NOTE]
>
> **Handy Tips**
>
> Webhook is auto-configured when you enter and save the API key ID and secret on the plugin settings page. You need to verify that webhooks are enabled on your Razorpay [Dashboard](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/cs-cart/troubleshooting-faqs.md#how-can-i-verify-if-webhooks-are-enabled). However, for versions lower than 1.4.0, you need to [manually configure webhooks](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/cs-cart/troubleshooting-faqs.md#my-webhooks-are-not-auto-configured-since-i-am-not-using-the-upgraded-version-of-cs-cart-how-do-i-manually-configure-webhooks).

## 2. Test Integration

After the integration, Razorpay is added as a payment option on your web page/app. You need to click the button and make a test transaction to ensure the integration works as expected. You can start accepting actual customer payments once the test is successful.

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
