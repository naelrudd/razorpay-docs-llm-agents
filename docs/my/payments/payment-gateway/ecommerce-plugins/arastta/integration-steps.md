> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Steps to integrate your Arastta website with Razorpay Curlec Payment Gateway.

Available in
🇮🇳 India
🇲🇾 Malaysia

Follow the steps given below to integrate Razorpay Curlec Payment Gateway with your Arastta website.\


> [card] [1. Build Integration](https://razorpay.com/docs/my/payments/payment-gateway/ecommerce-plugins/arastta/integration-steps.md#1-build-integration)
>
> Install and configure the Arastta Commerce plugin.

> [card] [2. Test Integration](https://razorpay.com/docs/my/payments/payment-gateway/ecommerce-plugins/arastta/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-Live Checklist](https://razorpay.com/docs/my/payments/payment-gateway/ecommerce-plugins/arastta/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

## 1. Build Integration

Follow the steps given below:

> [accordion] 1 Installation
>
> 1. Download a ZIP of the [repository](https://github.com/razorpay/razorpay-arastta/archive/master.zip). The master branch holds the plugin for the latest Arastta version.
>
>    ![](https://razorpay.com/docs/build/browser/assets/images/ecommerce-plugins-arastta-1.jpg)
> 2. Copy all files and folders recursively to Arastta installation directory.
> 3. Log in to [Arastta](https://arastta.org/).
> 4. Navigate to the **Admin Panel** → **Marketplace** → **Payments** and enable the Razorpay Curlec extension.
> 5. Click **Edit** next to Razorpay Curlec and complete the following actions:
>    1. Add your Razorpay Curlec `[KEY_ID]` and `[KEY_SECRET]`. These can be generated from your Razorpay Curlec [Dashboard](https://razorpay.com/docs/my/api/authentication.md#generate-api-keys).
>    2. Change plugin status to **Enabled**.
>    3. Click **Save** to save the plugin settings.

## 2. Test Integration

After the integration is complete, a **Pay** button will appear on your web page/app. You need to click the button and make a test transaction to ensure the integration works as expected. You can start accepting actual payments from your customers once the test is successful.

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
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > On the Razorpay Curlec Dashboard, ensure that the payment status is `captured`. Refer to the payment capture settings page to know how to [capture payments automatically](https://razorpay.com/docs/my/payments/payments/capture-settings.md).
>
> > [accordion] You can track the payment status in three ways:
> >
> > > [tab] Verify Status from Dashboard
> > >
> > > To verify the payment status from the Razorpay Curlec Dashboard:
> > >
> > > 1. Log in to the Razorpay Curlec Dashboard and navigate to **Transactions** → **Payments**.
> > > 2. Check if a **Payment Id** has been generated and note the status. In case of a successful payment, the status is marked as **Captured**.
> > >
> > > ![Payment details on Dashboard](https://razorpay.com/docs/build/browser/assets/images/my-testpayment.jpg)
> >
> > > [tab] Subscribe to Webhook Events
> > >
> > > You can use Razorpay Curlec webhooks to configure and receive notifications when a specific event occurs. When one of these events is triggered, we send an HTTP POST payload in JSON to the webhook's configured URL. Know how to [set up webhooks.](https://razorpay.com/docs/my/webhooks/setup-edit-payments.md)
> > >
> > > #### Example
> > >
> > > If you have subscribed to the `order.paid` webhook event, you will receive a notification every time a customer pays you for an order.
> >
> > > [tab] Poll APIs
> > >
> > > [Poll Payment APIs](https://razorpay.com/docs/my/api/payments/fetch-all-payments.md) to check the payment status.

## 3. Go-live Checklist

Follow these steps before taking the integration live:

> [accordion] Accept Live Payments
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
