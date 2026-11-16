> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Steps to integrate your Drupal Commerce website with the Razorpay Payment Gateway.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Follow the steps given below to integrate Razorpay Payment Gateway with your Drupal Commerce website.\


> [card] [1. Build Integration](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/drupal-commerce/integration-steps.md#1-build-integration)
>
> Install and configure the Drupal Commerce plugin.

> [card] [2. Test Integration](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/drupal-commerce/integration-steps.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-Live Checklist](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/drupal-commerce/integration-steps.md#3-go-live-checklist)
>
> Check the go-live checklist.

[How to integrate Razorpay Payment Gateway with Drupal Commerce Website](https://www.youtube.com/embed/37CjF-XNT70?si=e5cWAGO70V49zRHA)

## 1. Build Integration

Follow the steps given below:

> [accordion] 1 Download and Upload Plugin
>
> To upload the plugin:
>
> 1. [Download](https://github.com/razorpay/drupal_commerce_razorpay/releases) the `drupal_commerce_razorpay.zip`.
> 2. Log in to your [Drupal Commerce account](https://drupal.plugin.razorpay.in/) and navigate to **Extend**.
>
>    ![Navigate to Extend on Drupal](https://razorpay.com/docs/build/browser/assets/images/drupal-extend.jpg)
> 3. Click **+ Add new module**.
> 4. Add the module from **URL** or click **Choose file** and select the .zip file downloaded previously.
> 5. Click **Continue**.
>
> ![Add/upload drupal .zip file/URL](https://razorpay.com/docs/build/browser/assets/images/add-drupal-plugin1.gif)
>
> You have successfully uploaded the plugin.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Alternatively, you can skip this step and simply run `composer require 'drupal/drupal_commerce_razorpay:^1.0'` in your drupal directory to download the plugin. You can view the downloaded file in the `contrib` folder.

> [accordion] 2 Install Plugin
>
> To install the plugin:
>
> 1. On your Drupal Commerce Dashboard, navigate to **Extend**.
> 2. Search for **Razorpay** in the **Filter** section.
> 3. Select **Commerce Razorpay** and click **Install**.
>
> ![Install drupal plugin](https://razorpay.com/docs/build/browser/assets/images/drupal-install-plugin.jpg)

> [accordion] 3 Configure Plugin
>
> To configure the plugin:
>
> 1. On your Drupal Commerce Dashboard, navigate to **Commerce**.
>
> 2. Click **Configuration**.
>
>    ![Navigate to commerce to configure the plugin](https://razorpay.com/docs/build/browser/assets/images/drupal-commerce-config.jpg)
>
> 3. In the **Payment** section, select **Payment gateways**.
>
>    ![Configure the payment gateway](https://razorpay.com/docs/build/browser/assets/images/drupal-config-pg.jpg)
>
> 4. Click **+ Add payment gateway**.
>
>    ![Add the payment gateway](https://razorpay.com/docs/build/browser/assets/images/drupal-config-add-pg.jpg)
>
> 5. In the **Name** section, enter **Razorpay** and select **Razorpay** as the **Plugin**.
>
> 6. Select **Test** Mode to test the integration and enter the test **Key ID** and **Secret** generated from the Razorpay [Dashboard](https://razorpay.com/docs/api/authentication.md#generate-api-keys).
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > To go live with the integration and start accepting real payments:
> >
> > * Select **Live** Mode.
> > * Generate [Live Mode API Keys](https://razorpay.com/docs/api/authentication.md#live-mode-api-keys) and replace the test keys with the live keys in the integration. Click **Save**.
> >
> > ![Switch to live mode](https://razorpay.com/docs/build/browser/assets/images/drupal-live-mode.jpg)
>
> 7. Select the **Payment Action** based on your requirement. Set the Payment Action to **Authorize and Capture** to auto-capture payments. If you want to capture payments manually, set the Payment Method to **Authorize**.
>
> 8. Select **Enabled** in the **Status** section.
>
> 9. Click **Save**.
>
>    ![Configure the Razorpay payment gateway](https://razorpay.com/docs/build/browser/assets/images/drupal-config.gif)
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > If you want to edit any fields, navigate to **Commerce** → **Configuration**. Select **Payment Gateway** and click **Edit**.
>
> You have successfully integrated the Razorpay Payment Gateway with your Drupal Commerce website.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > * Webhooks are auto-configured when you enter and submit the API key ID during the installation. You can verify if webhooks are enabled on your Razorpay Dashboard.
> > * The `payment.authorized`, `payment.failed` and `refund.created` events are auto-configured. You do not have to configure it on the Razorpay Dashboard.

## 2. Test Integration

After the integration is complete, a payment button will appear on your web page/app. You need to click the button and make a test transaction to ensure the integration works as expected. You can start accepting actual payments from your customers once the test is successful.

> [!WARNING]
>
> **Watch Out!**
>
> This is a mock payment page that uses your test API keys, test card and payment details.
>
> * Ensure you have entered only your [Test Mode API keys](https://razorpay.com/docs/api/authentication.md#generate-api-keys) in the **Configuration** section of the Drupal Commerce Dashboard.
> * Test mode features a mock bank page with **Success** and **Failure** buttons to replicate the live payment experience.
> * No real money is deducted due to the usage of test API keys. This is a simulated transaction.

![Test the integration on your webpage/app](https://razorpay.com/docs/build/browser/assets/drupal-test2.gif)

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

## 3.  Go-live Checklist

Follow these steps before taking the integration live:

> [accordion] 1 Accept Live Payments
>
> You can perform an end-to-end simulation of funds flow in the Test Mode. Once confident that the integration is working as expected, switch to the Live Mode and start accepting payments from customers.
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
> 4. On your [Drupal Commerce Dashboard](https://drupal.plugin.razorpay.in/), navigate to **Commerce**.
> 5. Click **Configuration**.
>
>    ![Navigate to commerce to configure the plugin](https://razorpay.com/docs/build/browser/assets/images/drupal-commerce-config.jpg)
> 6. In the **Payment** section, select **Payment gateways**.
>
>    ![Configure the payment gateway](https://razorpay.com/docs/build/browser/assets/images/drupal-config-pg.jpg)
> 7. Click **Edit**.
>
>    ![Edit the payment gateway configurations](https://razorpay.com/docs/build/browser/assets/images/drupal-edit-config.jpg)
> 8. In the **Mode** section, select **Live**.
> 9. Replace the Test Key ID and Secret with the Live Keys and accept actual payments.
>
> ![Replace test keys with live ones](https://razorpay.com/docs/build/browser/assets/images/drupal-live-keys.jpg)

> [accordion] 2 Payment Capture
>
> After a payment is `authorized`, you must capture it to settle the amount to your bank account as per the settlement schedule.
>
> Follow the steps given below to set a payment action:
>
> 1. On the [Drupal Commerce Dashboard](https://drupal.plugin.razorpay.in/), navigate to **Commerce**.
> 2. Click **Configuration**.
>
>    ![Navigate to commerce to configure the plugin](https://razorpay.com/docs/build/browser/assets/images/drupal-commerce-config.jpg)
> 3. In the **Payment** section, select **Payment gateways**.
>
>    ![Configure the payment gateway](https://razorpay.com/docs/build/browser/assets/images/drupal-config-pg.jpg)
> 4. Click **Edit**.
>
>    ![Edit the payment gateway configurations](https://razorpay.com/docs/build/browser/assets/images/drupal-edit-config.jpg)
> 5. In the **Payment Action** section, you can choose to:
>
>    ![Edit the payment capture settings](https://razorpay.com/docs/build/browser/assets/images/drupal-payment-capture.jpg)
>
>    1. **Authorize and Capture**: This setting captures all authorized payments automatically. This eliminates the time and effort spent manually capturing payments.
>    2. **Authorize**: Each authorized payment can also be captured individually.
>       1. Once a payment is completed, navigate to **Commerce** → **Orders**.
>       2. Identify the order you want to capture the payment and click **View**.
>
>          ![Identify the order](https://razorpay.com/docs/build/browser/assets/images/drupal-order.jpg)
>       3. Navigate to **Payments**.
>       4. In the **Operations** section, click **Capture**.
>
>          ![Manually capture the payment](https://razorpay.com/docs/build/browser/assets/images/drupal-manual-capture.jpg)

#### Refunds

To initiate refunds using the Drupal Commerce Dashboard:

1. Log in to the [Drupal Commerce Dashboard](https://drupal.plugin.razorpay.in/).
2. After a payment is completed, navigate to **Commerce** → **Orders**.
3. Identify the order you want to initiate a refund and click **View**.

   ![Identify the order](https://razorpay.com/docs/build/browser/assets/images/drupal-order.jpg)
4. Navigate to **Payments**.
5. In the **Operations** section, click **Refund**.

   ![Issue a Refund](https://razorpay.com/docs/build/browser/assets/images/drupal-refund.jpg)
6. You can either issue a full refund or a partial refund.
   * For a **full refund**, enter the entire payment amount.
   * For a **partial refund**, enter a value lesser than the payment amount.
7. Click **Refund**.
