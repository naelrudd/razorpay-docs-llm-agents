> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Step-by-step guide to integrate Razorpay Payment Gateway with Shopify. Install Razorpay Secure app and start accepting payments on your Shopify store.

Available in
🇮🇳 India

> [!WARNING]
>
> **Plugin Renamed**
>
> In your Shopify admin, the Razorpay plugin is listed as **01 Cards, UPI, NB, Wallets by Razorpay**. To install it, go to **Settings** → **Payments**, click **+ Method** under **More ways to pay**, click **Search by provider** and search for **01 Cards, UPI, NB, Wallets by Razorpay**. Your customers see it at checkout as **Razorpay Secure (UPI, Card, Int'l Card, Apple Pay)**. The plugin was earlier listed as **1Razorpay - UPI, Cards, Wallets, NB** and **All-in-one Razorpay Payment Gateway**.
>
> You can also install the plugin directly from the [Shopify App Store](https://apps.shopify.com/razorpay-secure-new), where it is listed as **Cards, UPI, Wallet by Razorpay**.

Follow the steps given below to integrate the Razorpay Secure App on your Shopify store.

> [card] [1. Build Integration](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/integration-steps.md#1-build-integration)
>
> Install the Razorpay Secure app.

> [card] [2. Test Integration](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-Live Checklist](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

[How to integrate Razorpay Payment Gateway with your Shopify website using the Razorpay Secure app.](https://www.youtube.com/embed/eFVzIr1lsdA)

## 1. Build Integration

Follow the steps given below:

> [accordion] 1 Installation
>
> Watch this video to see how to install and activate the Razorpay plugin on your Shopify store.
>
> <video controls playsInline preload="metadata" aria-label="Walkthrough of installing the Razorpay plugin from the Shopify admin: go to Settings, then Payments, click + Method under More ways to pay, search by provider for Razorpay, select 01 Cards, UPI, NB, Wallets by Razorpay, click Install, review the permissions, click Install again and click Activate. The plugin then appears under More ways to pay.">
>   <source src="https://mintcdn.com/razorpay-881012b3/aB4TyzN-_gCfLpz2/static/docs-home/assets/shopify-razorpay-install-walkthrough.mp4?fit=max&auto=format&n=aB4TyzN-_gCfLpz2&q=85&s=0cf346813d3278491e80cb385f34b019" type="video/mp4" />
> </video>
>
> **Step 1: Sign up for a Razorpay account**.
>
> 1. [Sign up](https://dashboard.razorpay.com/signup?) for a Razorpay account. If you already have an account, skip to Step 2.
> 2. Submit your KYC, and if we need any further clarification, we will reach out to you on WhatsApp, SMS and email.
> 3. Once our team completes KYC verification and you are enabled to accept payments, we will send a confirmation on WhatsApp, SMS and email.
>
> **Step 2: Access the Razorpay Secure App on Shopify**.
>
> Once your Razorpay account is activated, you can install the app using either of these methods:
>
> > [tab] Method A: Direct Link Installation
> >
> > Click on [this link](https://accounts.shopify.com/store-login?redirect=settings%2Fpayments%2Falternative-providers%2F1058839) to access the **01 Cards, UPI, NB, Wallets by Razorpay** app directly on your Shopify store.
>
> > [tab] Method B: Manual Installation
> >
> > 1. Login to your Shopify store.
> > 2. Navigate to **Settings** → **Payments**.
> > 3. Under **More ways to pay**, click **+ Method**.
> >
> >    ![Click + Method under More ways to pay](https://mintcdn.com/razorpay-881012b3/aB4TyzN-_gCfLpz2/static/docs-home/assets/shopify-more-ways-to-pay-add-method.png?fit=max\&auto=format\&n=aB4TyzN-_gCfLpz2\&q=85\&s=4eb496d4399e2d3239f6c4df269f79b5)
> > 4. Click **Search by provider**, search for **01 Cards, UPI, NB, Wallets by Razorpay** and select it from the results.
> >
> >    ![Search for 01 Cards, UPI, NB, Wallets by Razorpay under Search by provider](https://mintcdn.com/razorpay-881012b3/QEEEpLwWzZAyEC07/static/docs-home/assets/shopify-search-by-provider-01-cards.png?fit=max\&auto=format\&n=QEEEpLwWzZAyEC07\&q=85\&s=0236b81a706a4a036f7e1abcbadb8c7a)
>
> **Step 3: Install and Activate the App**.
>
> 1. Click **Install** in the top right corner of the app page.
>
>    ![Click Install on the 01 Cards, UPI, NB, Wallets by Razorpay app installation page](https://mintcdn.com/razorpay-881012b3/Z8GTiU-_u_NPHB4p/static/docs-home/assets/shopify-razorpay-install-app.png?fit=max\&auto=format\&n=Z8GTiU-_u_NPHB4p\&q=85\&s=ab3229503707b0ce6e89e5210ccb4fe8)
> 2. Review the data access permissions and click **Install** in the Install app dialog.
>
>    ![Review the data access permissions and click Install in the Install app dialog](https://mintcdn.com/razorpay-881012b3/Z8GTiU-_u_NPHB4p/static/docs-home/assets/shopify-razorpay-install-app-permissions.png?fit=max\&auto=format\&n=Z8GTiU-_u_NPHB4p\&q=85\&s=d32a27697fe3cc869afb3a636cdeb5e6)
> 3. You will be redirected to a landing page. Click **I am an existing user**.
>
>    ![Click I am an existing user on the Razorpay landing page](https://mintcdn.com/razorpay-881012b3/Z8GTiU-_u_NPHB4p/static/docs-home/assets/shopify-razorpay-existing-user.png?fit=max\&auto=format\&n=Z8GTiU-_u_NPHB4p\&q=85\&s=f7414d553c0f5cceaf173190a38b7305)
> 4. Scroll down and click **Login**.
>
>    > [!NOTE]
>    >
>    > **Handy Tips**
>    >
>    > Make sure you log in with **store owner** credentials to connect Razorpay with Shopify successfully.
> 5. Review the payment methods displayed, scroll to the bottom of the page and click **Activate**.
>
>    ![Click Activate on the activation screen on your Shopify Dashboard](https://mintcdn.com/razorpay-881012b3/Z8GTiU-_u_NPHB4p/static/docs-home/assets/shopify-razorpay-activate.png?fit=max\&auto=format\&n=Z8GTiU-_u_NPHB4p\&q=85\&s=b8fa4710fc466bcf34fedafb9fe23f4e)
>
> On your Shopify **Payments** page, the plugin now appears under **More ways to pay**. **Razorpay Secure (UPI, Card, Int'l Card, Apple Pay)** also appears as a Payment Gateway on your Shopify Store checkout.
>
> ![Shopify Checkout](https://razorpay.com/docs/build/browser/assets/images/shopify-v2-checkout.jpg)
>
> This completes your integration. For more information, see [Shopify FAQs](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/faqs.md).

## 2. Test Integration

After the integration of **Shopify - Razorpay Secure** on your Shopify store is complete, follow the steps given below:

> [accordion] 1 Make a Test Transaction in Test Mode
>
> After completing the integration, you must ensure it is working as expected. You can start accepting actual payments from your customers once the test mode transaction is successful.\\
>
> Follow the steps given below to test a transaction in test mode:
>
> 1. Log in to your [Shopify store](https://accounts.shopify.com/lookup?rid=f19e1541-cd24-4856-a398-156d2ed5d56f).
> 2. Navigate to **Settings** → **Payments**.
> 3. Under **More ways to pay**, click **01 Cards, UPI, NB, Wallets by Razorpay**.
>
>    ![01 Cards, UPI, NB, Wallets by Razorpay listed under More ways to pay](https://mintcdn.com/razorpay-881012b3/aB4TyzN-_gCfLpz2/static/docs-home/assets/shopify-more-ways-to-pay-razorpay.png?fit=max\&auto=format\&n=aB4TyzN-_gCfLpz2\&q=85\&s=891e8131e2b4fda7423a3ff603366bb4)
> 4. At the bottom of the page, turn on the **Test mode** toggle and click **Save**.
>
>    ![Test mode toggle turned on, with a notice that no real transactions will be processed](https://mintcdn.com/razorpay-881012b3/aB4TyzN-_gCfLpz2/static/docs-home/assets/shopify-test-mode-on.png?fit=max\&auto=format\&n=aB4TyzN-_gCfLpz2\&q=85\&s=18cb3b3539fdba00c0f4c992c3d57421)
> 5. On your Shopify store, add an item to your cart and click **Buy it now**.
>
>    ![Shopify checkout](https://razorpay.com/docs/build/browser/assets/images/buy-now-shopify.jpg)
> 6. Fill in your **contact** and **shipping** details and click **Continue to shipping**.
>
>    ![Shopify contact details](https://razorpay.com/docs/build/browser/assets/images/shipping-contact-details.jpg)
> 7. Select **Razorpay Secure (UPI, Card, Int'l Card, Apple Pay)** and click **Complete order**.
>
>    ![Shopify complete order](https://razorpay.com/docs/build/browser/assets/images/complete-order.jpg)
> 8. On the checkout screen, enter your **phone number**, click **PROCEED**, and complete the payment.
>
> You can make test payments using one of the payment methods configured at the Checkout.
>
> * No money is deducted from the customer's account as this is a simulated transaction.
>
> * Ensure you have entered the API keys generated in the test mode in the Checkout code.
>
> > [accordion] Supported Payment Methods
> >
> > After the integration is complete, a **Pay** button appears on your webpage/app.
> >
> > ![Test integration on your webpage/app](https://razorpay.com/docs/build/browser/assets/images/test-int.gif)
> >
> > Click the button and make a test transaction to ensure the integration is working as expected. You can start accepting actual payments from your customers once the test transaction is successful.
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > This is a mock payment page that uses your test API keys, test card and payment details.
> > >
> > > * Ensure you have entered only your [Test Mode API keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys) in the Checkout code.
> > > * Test mode features a mock bank page with **Success** and **Failure** buttons to replicate the live payment experience.
> > > * No real money is deducted due to the usage of test API keys. This is a simulated transaction.
> >
> > Following are all the payment modes that the customer can use to complete the payment on the Checkout. Some of them are available by default, while others may require approval from us. Raise a request from the Dashboard to enable such payment methods.
> >
> > | Payment Method | Code | Availability |
> > | - | - | - |
> > | [Debit Card](https://razorpay.com/docs/payments/payment-methods/cards.md) | `debit` | ✓ |
> > | [Credit Card](https://razorpay.com/docs/payments/payment-methods/cards.md) | `credit` | ✓ |
> > | [Netbanking](https://razorpay.com/docs/payments/payment-methods/netbanking.md) | `netbanking` | ✓ |
> > | [UPI](https://razorpay.com/docs/payments/payment-methods/upi.md) | `upi` | ✓ |
> > | EMI - [Credit Card EMI](https://razorpay.com/docs/payments/payment-methods/emi/credit-card-emi.md), [Debit Card EMI](https://razorpay.com/docs/payments/payment-methods/emi/debit-card-emi.md) and [No Cost EMI](https://razorpay.com/docs/payments/payment-methods/emi/no-cost-emi.md) | `emi` | ✓ |
> > | [Wallet](https://razorpay.com/docs/payments/payment-methods/wallets.md) | `wallet` | ✓ |
> > | [Cardless EMI](https://razorpay.com/docs/payments/payment-methods/emi/cardless-emi.md) | `cardless_emi` | Requires [Approval](https://razorpay.com/support). |
> > | [Bank Transfer](https://razorpay.com/docs/payments/payment-methods/bank-transfer.md) | `bank_transfer` | Requires [Approval](https://razorpay.com/support) and Integration. |
> > | [Emandate](https://razorpay.com/docs/payments/recurring-payments/emandate/integrate.md) | `emandate` | Requires [Approval](https://razorpay.com/support) and Integration. |
> > | [Pay Later](https://razorpay.com/docs/payments/payment-methods/pay-later.md) | `paylater` | Requires [Approval](https://razorpay.com/support). |
> >
> > You can make test payments using one of the payment methods configured at the Checkout.
> >
> > > [accordion] Netbanking
> > >
> > > You can select any of the listed banks. After choosing a bank, Razorpay will redirect to a mock page where you can make the payment `success` or a `failure`. Since this is Test Mode, we will not redirect you to the bank login portals.
> > >
> > > Check the list of [supported banks](https://razorpay.com/docs/payments/payment-methods/netbanking.md#supported-banks).
> >
> > > [accordion] UPI
> > >
> > > You can enter one of the following UPI IDs:
> > >
> > > * `success@razorpay`: To make the payment successful.
> > > * `failure@razorpay`: To fail the payment.
> > >
> > > Check the list of [supported UPI flows](https://razorpay.com/docs/payments/payment-methods/upi.md).
> > >
> > > > [!NOTE]
> > > >
> > > > **Handy Tips**
> > > >
> > > > You can use **Test Mode** to test UPI payments, and **Live Mode** for UPI Intent and QR payments.
> >
> > > [accordion] Cards
> > >
> > > You can use the following test cards to test transactions for your integration in Test Mode.
> > >
> > > ### Domestic Cards
> > >
> > > Use the following test cards for Indian payments:
> > >
> > > | Network | Card Number | CVV & Expiry Date |
> > > | - | - | - |
> > > | Visa | 4100 2800 0000 1007 | Use a random CVV and any future date ^^^^^ |
> > > | Mastercard | 5500 6700 0000 1002 | |
> > > | RuPay | 6527 6589 0000 1005 | |
> > > | Diners | 3608 280009 1007 | |
> > > | Amex | 3402 560004 01007 | |
> > >
> > > #### Error Scenarios
> > >
> > > Use these test cards to simulate payment errors. See the [complete list](https://razorpay.com/docs/payments/payments/test-card-details.md#error-scenarios) of error test cards with detailed scenarios.
> > > Check the following lists:
> > >
> > > * [Supported Card Networks](https://razorpay.com/docs/payments/payment-methods/cards.md).
> > > * [Cards Error Codes](https://razorpay.com/docs/errors/payments/cards.md).
> > >
> > > ### International Cards
> > >
> > > Use the following test cards to test international payments. Use any valid expiration date in the future in the MM/YY format and any random CVV to create a successful payment.
> > >
> > > | Card Network | Card Number | CVV & Expiry Date |
> > > | - | - | - |
> > > | Mastercard | 5555 5555 5555 4444 5105 1051 0510 5100 5104 0600 0000 0008 | Use a random CVV and any future date ^^ |
> > > | Visa | 4012 8888 8888 1881 | |
> > >
> > > Check the list of [supported card networks](https://razorpay.com/docs/payments/payment-methods/cards.md).
> >
> > > [accordion] Wallet
> > >
> > > You can select any of the listed wallets. After choosing a wallet, Razorpay will redirect to a mock page where you can make the payment `success` or a `failure`. Since this is Test Mode, we will not redirect you to the wallet login portals.
> > >
> > > Check the list of [supported wallets](https://razorpay.com/docs/payments/payment-methods/wallets.md#supported-wallets).

> [accordion] 2 Update Checkout Settings
>
> Follow the steps given below for a smooth checkout experience:
>
> 1. Log in to your [Shopify store](https://accounts.shopify.com/lookup?rid=f19e1541-cd24-4856-a398-156d2ed5d56f).
>
> 2. Navigate to **Settings** → **Checkout**.
>
> 3. On the **Customer contact method** section, click **Phone number or email** and click **Save**.
>
>    ![Shopify Checkout v2](https://razorpay.com/docs/build/browser/assets/images/shopify-checkout-v2.jpg)
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Your customer's email ID is prefilled during checkout, but the `phone number` must be entered manually.

> [accordion] 3 Verify Payment Status
>
> You can track the payment status from the Razorpay Dashboard or by polling APIs.
>
> > [tab] Verify Payment Status From Dashboard
> >
> > 1. Log in to the Razorpay Dashboard and navigate to **Transactions** → **Payments**.
> > 2. Check if a `payment_ID` has been generated and note the status. In case of a successful payment, the status is marked as `captured`.
> >
> > ![Payment status on dashboard](https://razorpay.com/docs/build/browser/assets/images/testpayment.jpg)
>
> > [tab] Poll APIs
> >
> > [Poll Payment APIs](https://razorpay.com/docs/api/payments/fetch-all-payments.md) to check the payment status.

## 3. Go-live Checklist

Follow these steps before taking the integration live:

> [accordion] 1 Switch from Test mode to Live mode
>
> You can perform an end-to-end simulation of funds flow in the Test Mode. Once confident that the installation and integration is working as expected, switch to the Live Mode and start accepting payments from customers.
>
> To switch from **Test Mode** to **Live Mode**:
>
> 1. Log in to your [Shopify store](https://accounts.shopify.com/lookup?rid=f19e1541-cd24-4856-a398-156d2ed5d56f).
> 2. Navigate to **Settings** → **Payments**.
> 3. Under **More ways to pay**, click **01 Cards, UPI, NB, Wallets by Razorpay**.
>
>    ![01 Cards, UPI, NB, Wallets by Razorpay listed under More ways to pay](https://mintcdn.com/razorpay-881012b3/aB4TyzN-_gCfLpz2/static/docs-home/assets/shopify-more-ways-to-pay-razorpay.png?fit=max\&auto=format\&n=aB4TyzN-_gCfLpz2\&q=85\&s=891e8131e2b4fda7423a3ff603366bb4)
> 4. At the bottom of the page, turn off the **Test mode** toggle and click **Save**.
>
>    ![Test mode toggle turned off, with the Save button below it](https://mintcdn.com/razorpay-881012b3/aB4TyzN-_gCfLpz2/static/docs-home/assets/shopify-test-mode-off-save.png?fit=max\&auto=format\&n=aB4TyzN-_gCfLpz2\&q=85\&s=4c60a8525481364f7e6848b172ff21b8)
>
> You can now start accepting actual payments on your Shopify store.
