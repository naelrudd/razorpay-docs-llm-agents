> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Step-by-step guide to integrate Razorpay Payment Gateway with WooCommerce. Install Razorpay WooCommerce plugin and start accepting payments on WordPress.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Integrate Razorpay Payment Gateway with your WooCommerce website using our official WooCommerce plugin. This step-by-step guide covers installation, configuration, testing and going live with Razorpay on WordPress WooCommerce stores.

Follow the steps given below to integrate Razorpay Payment Gateway with your WooCommerce website.

> [card] [1. Build Integration](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/woocommerce/integration-steps.md#1-build-integration)
>
> Install and configure the WordPress plugin.

> [card] [2. Test Integration](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/woocommerce/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-Live Checklist](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/woocommerce/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

[How to integrate Razorpay Payment Gateway with WooCommerce Website](https://www.youtube.com/embed/p2YMdxZMyxQ)

## 1. Build Integration

Follow the steps given below:

> [accordion] 1 Install Plugin
>
> There are two methods to install our WooCommerce plugin:
>
> > [tab] Using WordPress Plugin Directory
> >
> > 1. [Download the plugin](https://wordpress.org/plugins/woo-razorpay/).
> > 2. Install it from the WordPress Plugin Directory.
>
> > [tab] Manual Installation
> >
> > 1. Download the [latest Source code zip file](https://github.com/razorpay/razorpay-woocommerce/releases/latest) from the Releases section in GitHub.
> > 2. Unzip and upload the contents of the extension to your `/wp-content/plugins/` directory.

> [accordion] 2 Configure WooCommerce
>
> Before you start:
>
> * Ensure you have created a Razorpay account and your KYC is approved.
> * You must have activated your business after the business activation email from Razorpay.
> * You have [generated the API keys](https://razorpay.com/docs/api/authentication.md#generate-api-keys) from the Dashboard (Under Account & Settings → API Keys).
>
> To configure WooCommerce:
>
> 1. Log in to your [WordPress account](https://wordpress.com/log-in) and activate the Razorpay plugin in the **WordPress Plugin Manager**.
>
> 2. Log in to your [WooCommerce account](https://woocommerce.com/), navigate to **Settings** and click the **Checkout/Payment Gateways** tab.
>
> 3. Click **Razorpay** to edit the settings.
>
> 4. Enable the Payment Method, name it Credit Card/Debit Card/Internet Banking. This is shown on the Payment page your customer sees.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > If you cannot see the Razorpay payment option during WooCommerce checkout, update the plugin to the [latest](https://github.com/razorpay/razorpay-woocommerce/releases/latest) version.
> >
> > ![Payments option error](https://razorpay.com/docs/build/browser/assets/images/Woocommerce-payment-error.jpg)
>
> 5. Add in your \[KEY\_ID] and \[KEY\_SECRET] generated from the Razorpay Dashboard.
>
> 6. Set the **Payment Action** to **Authorize and Capture** to auto-capture payments. If you want to capture payments manually from the Dashboard after manual verification, set the Payment Method to **Authorize**.
>
> > [!WARNING]
> >
> > **Watch Out: Uncaptured payments are automatically refunded after 5 days**
> >
> > If you set **Payment Action** to `Authorize`, payments are held but not settled. Any payment that is not captured within **5 days** of authorisation is automatically refunded to the customer — the merchant receives nothing.
> >
> > To prevent this, set **Payment Action** to **Authorize and Capture** for automatic capture, or manually capture payments from the Dashboard before the 5-day window closes. Review your capture settings in Dashboard → **Account & Settings** → **Payment Capture**.

> [!NOTE]
>
> **Configure Webhooks**
>
> Webhook is [auto-configured](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/woocommerce/troubleshooting-faqs.md#how-are-webhooks-auto-configured) when you enter and save the API key ID and secret on the plugin settings page. You need to verify if webhooks are enabled on your Razorpay [Dashboard](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/woocommerce/troubleshooting-faqs.md#how-can-i-verify-if-webhooks-are-auto-configured). However, for versions lower than 3.5.0, you need to [configure webhooks manually](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/woocommerce/troubleshooting-faqs.md#my-webhooks-are-not-auto-configured-since-i-am-not-using-the-upgraded-version-of-the-woocommerce-plugin-how-do-i-manually-configure-webhooks).
>
> If you regenerate your API keys, re-enter and save the new keys in the plugin settings page to re-trigger webhook auto-configuration.

The following webhook events are auto-configured when you save your API keys:

* `payment.authorized`
* `payment.captured`
* `payment.failed`
* `order.paid`

Verify these are enabled in your Razorpay Dashboard under **Account & Settings** → **Webhooks**.

## 2. Test Integration

After the integration is complete, a **Pay** button will appear on your web page/app. You need to click the button and make a test transaction to ensure that the integration is working as expected. You can start accepting actual payments from your customers once the test is successful.

You can make test payments using one of the payment methods configured at the Checkout.

* No money is deducted from the customer's account as this is a simulated transaction.
* Ensure you have entered the API keys generated in the test mode in the Checkout code.

> [accordion] Supported Payment Methods
>
> After the integration is complete, a **Pay** button appears on your webpage/app.
>
> ![Test integration on your webpage/app](https://razorpay.com/docs/build/browser/assets/images/test-int.gif)
>
> Click the button and make a test transaction to ensure the integration is working as expected. You can start accepting actual payments from your customers once the test transaction is successful.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > This is a mock payment page that uses your test API keys, test card and payment details.
> >
> > * Ensure you have entered only your [Test Mode API keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys) in the Checkout code.
> > * Test mode features a mock bank page with **Success** and **Failure** buttons to replicate the live payment experience.
> > * No real money is deducted due to the usage of test API keys. This is a simulated transaction.
>
> Following are all the payment modes that the customer can use to complete the payment on the Checkout. Some of them are available by default, while others may require approval from us. Raise a request from the Dashboard to enable such payment methods.
>
> | Payment Method | Code | Availability |
> | - | - | - |
> | [Debit Card](https://razorpay.com/docs/payments/payment-methods/cards.md) | `debit` | ✓ |
> | [Credit Card](https://razorpay.com/docs/payments/payment-methods/cards.md) | `credit` | ✓ |
> | [Netbanking](https://razorpay.com/docs/payments/payment-methods/netbanking.md) | `netbanking` | ✓ |
> | [UPI](https://razorpay.com/docs/payments/payment-methods/upi.md) | `upi` | ✓ |
> | EMI - [Credit Card EMI](https://razorpay.com/docs/payments/payment-methods/emi/credit-card-emi.md), [Debit Card EMI](https://razorpay.com/docs/payments/payment-methods/emi/debit-card-emi.md) and [No Cost EMI](https://razorpay.com/docs/payments/payment-methods/emi/no-cost-emi.md) | `emi` | ✓ |
> | [Wallet](https://razorpay.com/docs/payments/payment-methods/wallets.md) | `wallet` | ✓ |
> | [Cardless EMI](https://razorpay.com/docs/payments/payment-methods/emi/cardless-emi.md) | `cardless_emi` | Requires [Approval](https://razorpay.com/support). |
> | [Bank Transfer](https://razorpay.com/docs/payments/payment-methods/bank-transfer.md) | `bank_transfer` | Requires [Approval](https://razorpay.com/support) and Integration. |
> | [Emandate](https://razorpay.com/docs/payments/recurring-payments/emandate/integrate.md) | `emandate` | Requires [Approval](https://razorpay.com/support) and Integration. |
> | [Pay Later](https://razorpay.com/docs/payments/payment-methods/pay-later.md) | `paylater` | Requires [Approval](https://razorpay.com/support). |
>
> You can make test payments using one of the payment methods configured at the Checkout.
>
> > [accordion] Netbanking
> >
> > You can select any of the listed banks. After choosing a bank, Razorpay will redirect to a mock page where you can make the payment `success` or a `failure`. Since this is Test Mode, we will not redirect you to the bank login portals.
> >
> > Check the list of [supported banks](https://razorpay.com/docs/payments/payment-methods/netbanking.md#supported-banks).
>
> > [accordion] UPI
> >
> > You can enter one of the following UPI IDs:
> >
> > * `success@razorpay`: To make the payment successful.
> > * `failure@razorpay`: To fail the payment.
> >
> > Check the list of [supported UPI flows](https://razorpay.com/docs/payments/payment-methods/upi.md).
> >
> > > [!NOTE]
> > >
> > > **Handy Tips**
> > >
> > > You can use **Test Mode** to test UPI payments, and **Live Mode** for UPI Intent and QR payments.
>
> > [accordion] Cards
> >
> > You can use the following test cards to test transactions for your integration in Test Mode.
> >
> > ### Domestic Cards
> >
> > Use the following test cards for Indian payments:
> >
> > | Network | Card Number | CVV & Expiry Date |
> > | - | - | - |
> > | Visa | 4100 2800 0000 1007 | Use a random CVV and any future date ^^^^^ |
> > | Mastercard | 5500 6700 0000 1002 | |
> > | RuPay | 6527 6589 0000 1005 | |
> > | Diners | 3608 280009 1007 | |
> > | Amex | 3402 560004 01007 | |
> >
> > #### Error Scenarios
> >
> > Use these test cards to simulate payment errors. See the [complete list](https://razorpay.com/docs/payments/payments/test-card-details.md#error-scenarios) of error test cards with detailed scenarios.
> > Check the following lists:
> >
> > * [Supported Card Networks](https://razorpay.com/docs/payments/payment-methods/cards.md).
> > * [Cards Error Codes](https://razorpay.com/docs/errors/payments/cards.md).
> >
> > ### International Cards
> >
> > Use the following test cards to test international payments. Use any valid expiration date in the future in the MM/YY format and any random CVV to create a successful payment.
> >
> > | Card Network | Card Number | CVV & Expiry Date |
> > | - | - | - |
> > | Mastercard | 5555 5555 5555 4444 5105 1051 0510 5100 5104 0600 0000 0008 | Use a random CVV and any future date ^^ |
> > | Visa | 4012 8888 8888 1881 | |
> >
> > Check the list of [supported card networks](https://razorpay.com/docs/payments/payment-methods/cards.md).
>
> > [accordion] Wallet
> >
> > You can select any of the listed wallets. After choosing a wallet, Razorpay will redirect to a mock page where you can make the payment `success` or a `failure`. Since this is Test Mode, we will not redirect you to the wallet login portals.
> >
> > Check the list of [supported wallets](https://razorpay.com/docs/payments/payment-methods/wallets.md#supported-wallets).

> [accordion] Verify Payment Status
>
> You can track the payment status from the Dashboard or by polling APIs.
>
> > [tab] Verify Payment Status From Dashboard
> >
> > 1. Log in to the Razorpay Dashboard and navigate to **Transactions** → **Payments**.
> > 2. Check if a `payment_ID` has been generated and note the status. In case of a successful payment, the status is marked as `captured`.
> >
> >    ![Payment details on Dashboard](https://razorpay.com/docs/build/browser/assets/images/testpayment.jpg)
>
> > [tab] Poll APIs
> >
> > [Poll Payment APIs](https://razorpay.com/docs/api/payments/fetch-all-payments.md) to check the payment status.

You can also test your **WooCommerce** Integration in the Test Mode using your Test Mode API keys:

1. Go to WooCommerce → Settings → Payments → Razorpay.
2. Replace your Live API keys with Test Mode keys from the Razorpay Dashboard (Test Mode).
3. Complete a test transaction.
4. Switch back to Live keys before going live.

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
> > * You can track the payment status using our [Fetch a Payment API](https://razorpay.com/docs/api/payments/fetch-with-id.md) or webhooks.
>
> > [tab] Auto-capture Payments (Recommended)
> >
> > Authorized payments can be automatically captured. You can auto-capture all payments [using global settings](https://razorpay.com/docs/payments/payments/capture-settings.md#auto-capture-all-payments) on the Razorpay Dashboard. Know more about [capture settings for payments](https://razorpay.com/docs/payments/payments/capture-settings.md).
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > Payment capture settings work only if you have integrated with Orders API on your server side. Know more about the [Orders API](https://razorpay.com/docs/api/orders/create.md).
>
> > [tab] Manually Capture Payments
> >
> > Each authorized payment can also be captured individually. You can manually capture payments using [Payment Capture API](https://razorpay.com/docs/api/payments/capture.md) or [Dashboard](https://razorpay.com/docs/payments/payments/dashboard.md#manually-capture-payments). Know more about [capture settings for payments](https://razorpay.com/docs/payments/payments/capture-settings.md).
