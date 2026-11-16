> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Moon Invoice Prerequisites

> Integrate Razorpay Payment Gateway with Moon Invoice. Prerequisites and setup requirements for accepting payments on your invoices.

Available in
🇺🇸 United States

> [card] [Integration Steps](https://razorpay.com/docs/us/payments/payment-gateway/invoicing-billing/moon-invoice/integration-steps.md)
>
> Connect your Razorpay account to Moon Invoice, test the connection and go live.

> [card] [Troubleshooting & FAQs](https://razorpay.com/docs/us/payments/payment-gateway/invoicing-billing/moon-invoice/troubleshooting-faqs.md)
>
> Troubleshoot common error scenarios and find answers to frequently asked questions about the Razorpay Moon Invoice integration.

The Razorpay Moon Invoice integration lets you accept payments on the invoices you send from Moon Invoice. Your customers pay directly from the invoice using cards, ACH Direct Debit or digital wallets, and Moon Invoice updates the invoice once the payment succeeds.

You connect the two products by entering your Razorpay API keys in Moon Invoice. There is nothing to install and no code to write.

**Before you proceed:**

* Create a [Razorpay account](https://accounts.razorpay.com/auth/?auth_intent=signup\&x-country-code=US). US businesses sign up using this link.
* Ensure your KYC is approved and your business is activated. Razorpay sends a business activation email once this is complete.
* Understand the [payment flow](https://razorpay.com/docs/us/payments/payment-gateway/how-it-works.md) process.
* Generate your **Live Mode** [API Keys](https://razorpay.com/docs/us/api/authentication.md#generate-api-keys) from the Dashboard. Moon Invoice does not accept Test Mode keys.
* Have an active [Moon Invoice](https://mooninvoice.com) account with a company set up.

> [!WARNING]
>
> **Watch Out! Moon Invoice does not support Test Mode keys**
>
> Moon Invoice validates your credentials when you save them and rejects Razorpay **Test Mode** keys (`rzp_test_*`) with the error `Razorpay Key ID or Secret key are not proper.`
>
> You connect Moon Invoice using **Live Mode** keys, so you cannot run a simulated test payment through this integration. Every payment taken through it is a real payment. Verify the connection with a low-value live invoice and refund it — see [Verify the Integration](https://razorpay.com/docs/us/payments/payment-gateway/invoicing-billing/moon-invoice/integration-steps.md#2-verify-the-integration).

## Where You Configure the Integration

Razorpay is configured once per company from the Moon Invoice web portal, under **Integrations** → **Payment Methods**. Once connected, it applies to invoices you send from that company.

Moon Invoice labels the integration **Razor Pay** (two words) rather than Razorpay. It is the same integration.

## Supported Payment Methods

The payment methods available to your customers depend on the country your Razorpay account is registered in.

| Your account is registered in | Your customers can pay using | Settlement |
| - | - | - |
| United States | Credit and debit cards, ACH Direct Debit, digital wallets including Apple Pay | USD |
| India | UPI, cards, Netbanking, wallets | INR |

US accounts can also collect from customers in India, with settlement in USD. See [International Payments](https://razorpay.com/docs/us/payments/international-payments) for the full list of supported currencies and methods.

## Integration Steps

Check the integration steps to [connect Moon Invoice with Razorpay Payment Gateway](https://razorpay.com/docs/us/payments/payment-gateway/invoicing-billing/moon-invoice/integration-steps.md).

## Support

* **Payment and Razorpay account queries:** raise a ticket on the Razorpay [Support Portal](https://razorpay.com/us/support/).
* **Moon Invoice product queries:** contact the Moon Invoice [Help Center](https://help.mooninvoice.com). Questions about invoice creation, invoice status and Moon Invoice settings are handled by Moon Invoice.
