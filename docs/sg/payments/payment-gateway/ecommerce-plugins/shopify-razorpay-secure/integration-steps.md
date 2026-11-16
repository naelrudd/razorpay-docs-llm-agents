> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Step-by-step guide to integrate Razorpay Payment Gateway with Shopify. Install Razorpay Secure app and start accepting payments on your Shopify store.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Follow the steps given below to integrate Razorpay Secure on your Shopify store.

> [card] [1. Build Integration](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/shopify-razorpay-secure/integration-steps.md#1-build-integration)
>
> Install the Razorpay Secure App.

> [card] [2. Test Integration](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/shopify-razorpay-secure/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-Live Checklist](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/shopify-razorpay-secure/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

## Prerequisites

Before you start:

* Create a [Razorpay account](https://razorpay.com/docs/sg/payments/set-up).
* Complete KYC. Refer to the list of [documents](https://razorpay.com/docs/payments/business-types-kyc-documents.md) required.
* You will receive a confirmation email and WhatsApp message when your account is activated. You can use test mode to test the integration till your KYC is completed.

## 1. Build Integration

Follow the steps given below:

> [accordion] 1 Installation
>
> 1. Sign up for a [Razorpay account](https://dashboard.razorpay.com/signup).
>
> 2. Once your Razorpay account is activated, click on [this link](https://apps.shopify.com/razorpay-secure) to access the Razorpay Secure App on your Shopify store. Click **Install**.
>
>    ![Shopify Install](https://razorpay.com/docs/build/browser/assets/images/shopify-razorpay-secure-install-new.jpg)
>
> 3. Click **Install**.
>
>    ![Click Install](https://razorpay.com/docs/build/browser/assets/images/razorpay-secure-install.jpg)
>
> 4. You will be redirected to a landing page. **Select Country** of your registered company and click **I am an existing user**.
>
>    ![Shopify Select Country](https://razorpay.com/docs/build/browser/assets/images/shopify-select-country.jpg)
>
> 5. Scroll down and click **Login**.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Make sure you log in with **owner** credentials to connect Razorpay with Shopify successfully.
>
> 6. Click **Activate** on the activation screen on your Shopify Dashboard. \\
>
>    ![Shopify Activate](https://razorpay.com/docs/build/browser/assets/images/shopify-1razorpay-activate.jpg)
>
> Razorpay Secure now appears as a Payment Gateway on your Shopify Store checkout. This completes your integration. For more information, see [Shopify FAQs](https://razorpay.com/docs/sg/payments/payment-gateway/ecommerce-plugins/shopify-razorpay-secure/faqs.md).
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > **Shopify Plus** merchants can use the [**Shopify Script**](https://help.shopify.com/en/manual/checkout-settings/script-editor/examples/payment-gateway-scripts#reorder-gateways) to modify their plugins. \\
> >
> > For example, you can: \\
> >
> > * Change the order of the payment methods on your checkout.
> > * Select the relevant payment methods on your checkout.
> > * Modify the payment option title on your checkout.
> >
> >   ![Shopify Secure Plus changes](https://razorpay.com/docs/build/browser/assets/images/sg-shopify-secure-plus.jpg)

## 2. Test Integration

After the integration of **Shopify - Razorpay Secure** on your Shopify store is complete, follow the steps given below:

> [accordion] 1 Make a Test Transaction in Test Mode
>
> After completing the integration, you must ensure it is working as expected. You can start accepting actual payments from your customers once the test mode transaction is successful.\\
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Test mode in Shopify is a separate toggle from your Razorpay Dashboard. Enabling test mode on the Razorpay Dashboard alone is not enough. You must enable it on Shopify as well (Settings → Payments → Manage → Enable test mode).
>
> Follow the steps given below to test a transaction in test mode:
>
> 1. Log in to your [Shopify store](https://accounts.shopify.com/lookup?rid=f19e1541-cd24-4856-a398-156d2ed5d56f).
> 2. Navigate to **Settings** → **Payments**.
> 3. Under **Additional payment methods** section, click **Razorpay Secure** app.
>
>    ![Shopify go live v2](https://razorpay.com/docs/build/browser/assets/images/shopify-go-live-v3.jpg)
> 4. At the bottom of the page, toggle the **Test mode** option and click **Save**.
>
>    ![Shopify go live v2 save test](https://razorpay.com/docs/build/browser/assets/images/shopify-go-live-test.jpg)
> 5. On your Shopify store, add an item to your cart and click **Buy it now**.
>
>    ![Shopify checkout](https://razorpay.com/docs/build/browser/assets/images/sg-buy-now-shopify.jpg)
> 6. Fill in your **Delivery** details and click **Pay now**.
>
>    ![Shopify contact details](https://razorpay.com/docs/build/browser/assets/images/sg-shopify-delivery-address.jpg)
> 7. On the checkout screen, select the payment method, and complete the payment.
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
> > Click the button and make a test transaction to ensure the integration is working as expected. You can start accepting actual payments from your customers once the test transaction is successful.
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > This is a mock payment page that uses your test API keys, test card and payment details.
> > >
> > > * Ensure you have entered only your [Test Mode API keys](https://razorpay.com/docs/sg/payments/dashboard/account-settings/api-keys.md#generate-api-keys) in the Checkout code.
> > > * Test mode features a mock bank page with **Success** and **Failure** buttons to replicate the live payment experience.
> > > * No real money is deducted due to the usage of test API keys. This is a simulated transaction.
> >
> > Following are all the payment modes that the customer can use to complete the payment on the Checkout. Some of them are available by default, while others may require approval from us. Raise a request from the Dashboard to enable such payment methods.
> >
> > | Payment Method | Code | Availability |
> > | - | - | - |
> > | [Debit and Credit Cards](https://razorpay.com/docs/sg/payments/payment-methods/cards.md) | `card` | ✓ |
> > | [PayNow](https://razorpay.com/docs/sg/payments/payment-methods/paynow.md) | `paynow` | ✓ |
> >
> > You can make test payments using one of the payment methods configured at the Checkout.
> >
> > > [accordion] Cards
> > >
> > > You can use one of the following test cards to test transactions for your integration in Test Mode.
> > >
> > > | Card Network | Card Number | CVV & Expiry Date |
> > > | - | - | - |
> > > | Mastercard | 5272 0088 0623 5705 | Use a random CVV and any future date ^^ |
> > > | Visa | 4111 1111 1111 1112 | |
> > >
> > > Check the following lists:
> > >
> > > * [Supported Card Networks](https://razorpay.com/docs/sg/payments/payment-methods/cards.md).
> > > * [Cards Error Codes](https://razorpay.com/docs/sg/errors/payments/cards.md).
> >
> > > [accordion] PayNow
> > >
> > > You can scan the QR code and make the payment using your PayNow-enabled bank app. Razorpay will redirect to a mock page where you can make the payment a success or a failure. Since this is Test Mode, we will not redirect you to the bank portals. Know more about [PayNow](https://razorpay.com/docs/sg/payments/payment-methods/paynow.md).

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
> >    ![Payment details on Dashboard](https://razorpay.com/docs/build/browser/assets/images/sg-testpayment.jpg)
>
> > [tab] Poll APIs
> >
> > [Poll Payment APIs](https://razorpay.com/docs/sg/api/payments/fetch-all-payments.md) to check the payment status.

## 3. Go-live Checklist

Follow these steps before taking the integration live:

> [accordion] 1 Switch from Test mode to Live mode
>
> You can perform an end-to-end simulation of funds flow in the Test Mode. Once confident that the installation and integration is working as expected, switch to the Live Mode and start accepting payments from customers.
>
> Watch this short animation to know how to switch from **Test Mode** to **Live Mode** on your Shopify store.
>
> ![Shopify Go Live](https://razorpay.com/docs/build/browser/assets/images/shopify-go-live-v2.gif)
>
> To switch from **Test Mode** to **Live Mode**:
>
> 1. Log in to your [Shopify store](https://accounts.shopify.com/lookup?rid=f19e1541-cd24-4856-a398-156d2ed5d56f).
> 2. Navigate to **Settings** → **Payments**.
> 3. On the **Supported payment methods** section, click **Manage** on the **Razorpay Secure** app.
>
>    ![Shopify go live v2](https://razorpay.com/docs/build/browser/assets/images/shopify-go-live-v2.jpg)
> 4. At the bottom of the page, untick the **Enable test mode** option and click **Save**.
>
>    ![Shopify go live v2 save](https://razorpay.com/docs/build/browser/assets/images/shopify-go-live-save.jpg)
>
> You can now start accepting actual payments on your Shopify store.

> [!WARNING]
>
> **Watch Out!**
>
> Before you go live:
>
> * Ensure you have turned off the **Enable test mode** option on Shopify (Settings → Payments → Manage)
> * Ensure your Razorpay account is in Live Mode with Live API keys configured.
>
> Missing either step will result in payment failures in real-time.
