> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Troubleshooting & FAQs

> Troubleshoot common errors and find answers to frequently asked questions about the Razorpay Moon Invoice integration and invoice payments.

Available in
🇺🇸 United States

> [accordion] Can I test the integration using Razorpay Test Mode keys?
>
> No. Moon Invoice validates your credentials when you save them and does not accept Razorpay **Test Mode** keys (`rzp_test_*`). Entering them returns the error `Razorpay Key ID or Secret key are not proper.`
>
> You connect Moon Invoice using **Live Mode** keys, which means you cannot run a simulated test payment through this integration. Verify the connection with a low-value real invoice and refund it afterwards. See [Verify the Integration](https://razorpay.com/docs/us/payments/payment-gateway/invoicing-billing/moon-invoice/integration-steps.md#2-verify-the-integration).

> [accordion] Where do I find my Key ID and Key Secret?
>
> In the Razorpay Dashboard, switch to **Live Mode**, then navigate to **Account & Settings** → **API Keys** → **Generate Key**. Download both values when prompted. The Key Secret is shown only once, so store it securely.

> [accordion] Where do I enter my Razorpay credentials in Moon Invoice?
>
> In the Moon Invoice web portal, click **Integrations** in the left sidebar, scroll to **Payment Methods** and find the **Razor Pay** card. Click **Connect**, enter your Key ID and Key Secret in the **Setup Online Payment** modal, then click **Save**.
>
> On success, the Razor Pay card shows a blue checkmark and moves to the first position in the Payment Methods grid.

> [accordion] I am getting the error "Razorpay Key ID or Secret key are not proper". Why?
>
> Moon Invoice returns this error when it cannot validate the credentials you entered. The two most common causes are:
>
> * **You used Test Mode keys.** Moon Invoice does not accept `rzp_test_*` keys. Generate Live Mode keys from the Dashboard and enter those instead.
> * **The Key ID and Key Secret do not belong to the same key pair,** or a trailing space was introduced when pasting. Re-copy both values from the Dashboard and save again.
>
> If the issue persists with Live Mode keys, contact our [Support team](https://razorpay.com/us/support/).

> [accordion] Why am I getting the error "Authentication failed"?
>
> This occurs when there is a discrepancy between the API keys. Verify that the Key ID and Key Secret entered in Moon Invoice both come from the same key pair generated in the Dashboard, and that both are Live Mode keys.

> [accordion] Razorpay does not appear as a payment option on my invoice.
>
> Check the following:
>
> * Open **Integrations** → **Payment Methods** in Moon Invoice and confirm the **Razor Pay** card shows the blue checkmark. Without it, the connection did not save.
> * Confirm you connected Razorpay for the same company the invoice was sent from. The connection applies per company.
> * In the invoice's Payment Methods picker, confirm **Razor Pay** is selected.
>
> Moon Invoice lists the integration as **Razor Pay** (two words), so it may not appear where you expect alphabetically.

> [accordion] My customer paid but the invoice still shows as unpaid. What should I do?
>
> First confirm the payment reached Razorpay. In the Dashboard, go to **Transactions** → **Payments** and search for the payment. Note the `payment_ID` and status.
>
> * **If the payment is not there,** it did not reach Razorpay. Ask your customer to retry from the invoice.
> * **If the payment is there and captured,** the payment succeeded and the invoice record has not been updated. Contact the Moon Invoice [Help Center](https://help.mooninvoice.com) with the invoice number and the Razorpay `payment_ID`, since the invoice status is maintained by Moon Invoice.

> [accordion] Why was my customer's payment refunded automatically?
>
> The payment was authorised but never captured. Authorised payments that are not captured within the capture window are refunded to the customer in full.
>
> Review your capture settings in the Dashboard under **Account & Settings** → **Payment Capture** and see [Capture Settings for Payments](https://razorpay.com/docs/us/payments/payments/capture-settings.md).

> [accordion] The merchant name on the payment page is wrong. How do I change it?
>
> The merchant name shown on the Moon Invoice payment page and on Razorpay Checkout is pulled from the business name configured on your Razorpay account, not from Moon Invoice.
>
> To change it, update your business name in the Razorpay Dashboard under **Account & Settings** → **Account Details**.

> [accordion] Why does Razorpay Checkout ask my customer for a mobile number?
>
> Razorpay Checkout collects contact details before processing the payment. The country code is detected from your account configuration, so US accounts default to +1. This is standard Checkout behaviour and is not specific to Moon Invoice.

> [accordion] Which currencies can I invoice in?
>
> Razorpay supports a wide range of currencies for international payments, including USD, GBP and EUR. See [International Payments](https://razorpay.com/docs/us/payments/international-payments) for the currencies supported on your account.
>
> Set the invoice currency in Moon Invoice as you normally would.

> [accordion] Can I use this integration if my business is registered in the United States?
>
> Yes. Razorpay offers US merchant accounts that accept cards, ACH Direct Debit and digital wallets, and settle in USD. Your account country is determined by where your business is registered, not where your customers are.
>
> US businesses sign up at [accounts.razorpay.com](https://accounts.razorpay.com/auth/?auth_intent=signup\&x-country-code=US).

> [accordion] I regenerated my API keys. Do I need to do anything in Moon Invoice?
>
> Yes. Enter and save the new Key ID and Key Secret in Moon Invoice, then confirm the **Razor Pay** card still shows the blue checkmark. Payments fail until the new keys are saved.

> [accordion] Is there a fee for connecting Razorpay to Moon Invoice?
>
> No. Razorpay does not charge a setup or maintenance fee for the connection. Razorpay's per-transaction pricing applies to payments you collect, including the low-value payment you make when verifying the integration. See [Pricing](https://razorpay.com/us/pricing/).

> [accordion] What should I do before raising a support ticket?
>
> 1. Confirm your Razorpay KYC is approved and your business is activated.
> 2. Confirm you entered **Live Mode** keys in Moon Invoice. Test Mode keys are rejected.
> 3. Confirm the **Razor Pay** card shows the blue checkmark for the correct company.
> 4. Send yourself a low-value invoice and attempt payment, noting the exact error message.
>
> If the issue is with the payment itself, raise a ticket on the Razorpay [Support Portal](https://razorpay.com/us/support/) with your Moon Invoice account email, the invoice number, the Razorpay `payment_ID` if one was generated, the payment method attempted and a screenshot or screen recording of the failure.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Never share your **Key Secret** in a support ticket, email or screenshot. Razorpay will never ask for it. Share only your **Key ID** and the `payment_ID`, and redact any credentials visible in screenshots or screen recordings. If a Key Secret has been exposed, regenerate the key pair in the Dashboard and save the new keys in Moon Invoice.
>
> If the issue is with the invoice, the invoice status or Moon Invoice settings, contact the Moon Invoice [Help Center](https://help.mooninvoice.com).
