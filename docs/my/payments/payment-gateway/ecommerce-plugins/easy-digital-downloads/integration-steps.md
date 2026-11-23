> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Steps to integrate your Easy Digital Downloads website with Razorpay Curlec Payment Gateway.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Follow the steps given below to integrate Razorpay Curlec Payment Gateway with your Easy Digital Downloads website.\


> [card] [1. Build Integration](https://razorpay.com/docs/my/payments/payment-gateway/ecommerce-plugins/easy-digital-downloads/integration-steps.md#1-build-integration)
>
> Install and configure the Easy Digital Downloads plugin.

> [card] [2. Test Integration](https://razorpay.com/docs/my/payments/payment-gateway/ecommerce-plugins/easy-digital-downloads/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-Live Checklist](https://razorpay.com/docs/my/payments/payment-gateway/ecommerce-plugins/easy-digital-downloads/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

## 1. Build Integration

Follow the steps given below:

> [accordion] 1 Installation and Configuration
>
> 1. Download and install the latest version of the Easy Digital Downloads extension from the [WordPress plugin page](https://wordpress.org/plugins/easy-digital-downloads/).
>
> 2. Download the latest [razorpay-edd zip file](https://github.com/razorpay/razorpay-edd/releases) from the Releases section in GitHub.
>
> 3. Unzip and upload the extension contents to your `/wp-content/plugins/` directory.
>
> 4. Activate the extension via the WordPress **Plugins** menu.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > If you have downloaded the extension from GitHub or elsewhere, ensure that the directory is named `edd-razorpay`.
>
> 5. Log in to your [WordPress account](https://wordpress.com/log-in) and activate the extension in the **WordPress Plugin Manager**.
> 6. Log in to your [Easy Digital Downloads account](https://easydigitaldownloads.com).
> 7. Navigate to the **Settings** page and click the **Checkout/Payment Gateways** tab.
> 8. Click **Razorpay Curlec** to edit the settings.
> 9. Enable the Payment Method and name it Credit Card/Debit Card/Internet Banking (this will show up on the payment page your customer sees).
> 10. Enter your `[KEY_ID]` and `[KEY_SECRET]`. Generate the [API Keys](https://razorpay.com/docs/my/api/authentication.md#generate-api-keys) from the Razorpay Curlec Dashboard.
> 11. Click **Save** to save the changes.

## 2. Test Integration

After the integration, a **Pay** button will appear on your web page/app. You need to click the button and make a test transaction to ensure the integration works as expected. You can start accepting actual customer payments once the test is successful.

![](https://razorpay.com/docs/build/browser/assets/images/easy-digital-pay.jpg)

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
