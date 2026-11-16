> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Steps to integrate your WHMCS website with Razorpay Payment Gateway.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Follow the steps given below to integrate Razorpay Payment Gateway with your WHMCS website.

> [card] [1. Build Integration](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/whmcs/integration-steps.md#1-build-integration)
>
> Install and configure the WordPress plugin.

> [card] [2. Test Integration](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/whmcs/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-Live Checklist](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/whmcs/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

## 1. Build Integration

Follow the steps given below:

> [accordion] 1 Installation and Configuration
>
> 1. Ensure you have installed the latest version of WHMCS.
> 2. Download the Source code zip file of the required version of the plugin from the Releases section in GitHub.
>    * If you are using WHMCS 5, download the release tagged [version 1.0.3](https://github.com/razorpay/razorpay-whmcs/releases/tag/v1.0.3).
>    * If you are using WHMCS 6, 7 or 8, download the release tagged [version 2.0.1](https://github.com/razorpay/razorpay-whmcs/releases/tag/2.0.1).
> 3. Unzip and upload the repository contents to your WHMCS Installation directory. That is, the contents of the module folder from the repository go into the module folder of your WHMCS Installation directory.
> 4. Log in to your site as the WHMCS administrator. This is done by adding `/admin` to the URL where you have installed WHMCS, for example, `www.example.com/whmcs/admin`.
> 5. Navigate to **Setup** → **Payments** → **Payment Gateways**.
> 6. Select Razorpay from the drop-down list and **Activate** it.
> 7. Enter the \[KEY\_ID] and \[KEY\_SECRET]. You can generate these from your Razorpay Dashboard.
> 8. Set **Convert for Processing** to SGD if your store has a different default currency. In this case, update the Exchange Rate in your currency management settings.
> 9. Click **Save Changes**.

> [accordion] 2 Configure Webhooks
>
> To receive webhook notifications, you should configure webhooks on your WHMCS site and the Razorpay Dashboard.
>
> > [tab] WHMCS Site
> >
> > To set up webhooks in the WHMCS site:
> >
> > 1. Log in to your site as the WHMCS administrator.
> > 2. Navigate to **System Settings** → **Payment Gateways**.
> > 3. Click **Manage Existing Gateways**.
> > 4. Select the **Enable Webhook** option.
> > 5. Copy the URL that appears on the screen. In the Razorpay Dashboard, configure this URL in **Accounts & Settings** → **Webhooks**. Know more about how to [setup webhooks](https://razorpay.com/docs/sg/webhooks).
> > 6. Enter the secret.
> >
> > ![Setting up Webhooks on WHMCS site](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-whmcs-whmcs-webhooks.jpg)
>
> > [tab] Dashboard
> >
> > To set up webhooks in the Razorpay Dashboard:
> >
> > 1. Log in to the Razorpay Dashboard.
> > 2. Navigate to **Accounts & Settings** → **Webhooks**.
> > 3. Click + Add New Webhook.
> > 4. In the Webhook Setup modal:
> >    * Paste the URL copied from the WHMCS site.
> >
> > > [!NOTE]
> > >
> > > **Handy Tips**
> > >
> > > Webhooks can only be delivered to public URLs. You will notice an error if you attempt to save a localhost endpoint as part of a webhook setup. Know about [validating and testing webhooks for alternatives to localhost](https://razorpay.com/docs/sg/webhooks/validate-test.md#test-webhooks).
> >
> > * Enter the Secret you provided on the WHMCS site. The secret is used to validate where the webhook is from Razorpay. Do not expose the secret publicly. Know about how to [validate webhooks](https://razorpay.com/docs/sg/webhooks/validate-test.md#validate-webhooks).
> >
> > * In the **Alert Email field**, enter the email address to which notifications must be sent in case of webhook failure.
> >
> > * Select the `order.paid` event from the list of **Active Events**.
> >
> > 5. Click **Create Webhook**.

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
