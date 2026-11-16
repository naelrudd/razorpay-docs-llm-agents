> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Step-by-step guide to connect Razorpay Payment Gateway with Moon Invoice. Configure your API keys, verify the connection and start accepting payments on invoices.

Available in
🇺🇸 United States

Connect Razorpay Payment Gateway to Moon Invoice to accept payments on your invoices. This guide covers configuration, verification and going live.

> [!WARNING]
>
> **Watch Out! Moon Invoice does not support Test Mode keys**
>
> Moon Invoice validates your credentials when you save them and does not accept Razorpay **Test Mode** keys (`rzp_test_*`). Entering them returns the error `Razorpay Key ID or Secret key are not proper.`
>
> You must connect Moon Invoice using **Live Mode** keys. This means you cannot run a simulated test payment through this integration, and every payment taken through it is a real payment that creates a real order on your Razorpay Dashboard. Verify the connection with a low-value live invoice instead, as described in [Verify the Integration](https://razorpay.com/docs/us/payments/payment-gateway/invoicing-billing/moon-invoice/integration-steps.md#2-verify-the-integration).

> [card] [1. Build Integration](https://razorpay.com/docs/us/payments/payment-gateway/invoicing-billing/moon-invoice/integration-steps.md#1-build-integration)
>
> Generate your Live Mode API keys and connect Razorpay in Moon Invoice.

> [card] [2. Verify the Integration](https://razorpay.com/docs/us/payments/payment-gateway/invoicing-billing/moon-invoice/integration-steps.md#2-verify-the-integration)
>
> Confirm the connection with a low-value live invoice.

> [card] [3. Go-Live Checklist](https://razorpay.com/docs/us/payments/payment-gateway/invoicing-billing/moon-invoice/integration-steps.md#3-go-live-checklist)
>
> Check capture settings and settlement before you invoice customers.

## 1. Build Integration

### 1.1 Generate API Keys

Generate **Live Mode** keys. Moon Invoice rejects Test Mode keys, so there is no Test Mode step in this integration.

1. Log in to the Razorpay [Dashboard](https://dashboard.razorpay.com/) and switch to **Live Mode**.
2. Navigate to **Account & Settings** → **API Keys** → **Generate Key**.
3. Download the **Key ID** and **Key Secret**.

> [!WARNING]
>
> **Watch Out!**
>
> The Key Secret is displayed only once. Download and store it securely. If you lose it, you must regenerate the key pair and re-enter both values in Moon Invoice.

### 1.2 Connect Razorpay in Moon Invoice

Before you start:

* Your Razorpay KYC is approved and your business is activated.
* You have your Live Mode Key ID and Key Secret.

To connect Razorpay:

1. Log in to your [Moon Invoice](https://mooninvoice.com) account.
2. Click **Integrations** in the left sidebar.
3. Scroll to the **Payment Methods** section and find the **Razor Pay** card.
4. Click **Connect**. The **Setup Online Payment** modal opens with two fields, **Key ID** and **Secret Key**.
5. Enter your Key ID and Key Secret, then click **Save**.

On success, the **Razor Pay** card shows a blue checkmark and moves to the first position in the Payment Methods grid. A three-dot menu on the card lets you manage the connection.

> [!NOTE]
>
> **Handy Tips**
>
> * Moon Invoice labels the integration **Razor Pay** (two words) rather than Razorpay. It is the same integration.
> * Razorpay is connected per company. If you run more than one company in Moon Invoice, connect it for each company you invoice from.

For a walkthrough, watch [How to Enable Razorpay Payments for Online Transactions in Moon Invoice](https://www.youtube.com/watch?v=Pet38wK7pTU).

## 2. Verify the Integration

Because Moon Invoice does not accept Test Mode keys, you cannot make a simulated test payment. Verify the connection with a **low-value real invoice** instead, then refund it.

> [!WARNING]
>
> **Watch Out! This is a real payment**
>
> The invoice you send here is paid with a real payment method and real money moves. It creates a live order and payment on your Razorpay Dashboard, and Razorpay's standard per-transaction pricing applies. Keep the amount low and refund the payment once you have verified it.

To verify the integration:

1. In Moon Invoice, create a low-value invoice made out to yourself or a colleague.
2. Confirm **Razor Pay** appears in the invoice's payment methods, then send the invoice.
3. Open the invoice as the recipient and click **Pay Now**. The Moon Invoice payment page opens with your merchant name, the invoice reference and the amount.
4. Click the **Razorpay** button. Razorpay Checkout opens with the invoice amount and the available payment methods.
5. Complete the payment.

Check the following lists for the methods and errors you may encounter:

* [Supported Card Networks](https://razorpay.com/docs/us/payments/payment-methods/cards.md).
* [Cards Error Codes](https://razorpay.com/docs/us/errors/payments/cards.md).

### Verify Payment Status

> [tab] In the Razorpay Dashboard
>
> 1. Log in to the Razorpay Dashboard and navigate to **Transactions** → **Payments**.
> 2. Check whether a `payment_ID` has been generated and note the status. A successful payment shows as `captured`.

> [tab] In Moon Invoice
>
> Open the invoice you paid. The invoice status changes from unpaid to paid once the payment succeeds.
>
> If the payment appears in your Razorpay Dashboard but the invoice has not updated, see [Troubleshooting & FAQs](https://razorpay.com/docs/us/payments/payment-gateway/invoicing-billing/moon-invoice/troubleshooting-faqs.md).

### Refund the Verification Payment

Once you have confirmed the payment and the invoice status, refund it from the Razorpay Dashboard under **Transactions** → **Payments**. See [Refunds](https://razorpay.com/docs/us/payments/refunds) for how refunds are processed and how long they take to reach the customer.

## 3. Go-Live Checklist

You are already using Live Mode keys, so work through the checks below before you send invoices to real customers.

### 3.1 Confirm the Connection

1. In Moon Invoice, open **Integrations** → **Payment Methods** and confirm the **Razor Pay** card shows the blue checkmark.
2. Confirm Razorpay is connected for every company you invoice from.
3. Confirm your verification payment appears in **Transactions** → **Payments** in the Razorpay Dashboard.

### 3.2 Payment Capture and Settlement

Payments must be captured before they settle to your bank account. Review your capture settings in the Dashboard under **Account & Settings** → **Payment Capture**, and see [Capture Settings for Payments](https://razorpay.com/docs/us/payments/payments/capture-settings.md) for how automatic capture works.

> [!WARNING]
>
> **Watch Out!**
>
> Deliver goods or services only after the payment is captured. Authorised payments that are never captured are refunded to the customer automatically.

Settlement timelines are set by your account's settlement schedule. See [Settlements](https://razorpay.com/docs/us/payments/settlements).
