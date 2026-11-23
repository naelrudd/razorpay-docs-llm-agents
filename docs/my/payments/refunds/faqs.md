> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Frequently Asked Questions (FAQs)

> Find answers to frequently asked questions about Refunds via Razorpay Curlec and IRCTC refunds.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Find answers to commonly asked questions about refunds.

## General FAQs

> [accordion] How do I initiate a refund?
>
> You can issue partial or full refunds:
>
> * [From the Dashboard](https://razorpay.com/docs/my/payments/refunds/issue.md#issue-refunds)
> * [Using APIs](https://razorpay.com/docs/my/api/refunds.md)
>
> By default, the entire amount is refunded. If you issue a partial refund, ensure the partial refund option is selected and enter the desired value in MYR.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Razorpay Curlec issues immediate refunds. Once a refund is issued, it cannot be canceled or reversed.

> [accordion] Do you charge for refund?
>
> We charge a flat fee of RM 0.50 per refund.

> [accordion] I am unable to refund a payment. What do I do?
>
> If your current balance is less than the amount you are trying to refund, you can either initiate the refund once you receive further payments or you can [add funds](https://razorpay.com/docs/my/payments/dashboard/account-settings/balances.md#add-funds-to-current-balance) to your account from the Dashboard.

> [accordion] Why was a payment refunded that I did not refund?
>
> Razorpay Curlec auto-refunds some payments that are not captured, for example, payments that are not captured within your capture timeout, late authorised payments or duplicate payments on an already paid order. These auto-refunds are processed at normal speed. Know more about [auto-refunds](https://razorpay.com/docs/my/payments/refunds/auto-refunds.md).

> [accordion] When a refund is initiated, can its status remain 'pending' until settlement? How should I track the final status (processed/failed)?
>
> Yes, a refund status can remain in a 'pending' state, particularly when the refund cannot be processed instantly. This state indicates that the refund has been accepted by Razorpay Curlec but is still being processed by the bank or payment network.
>
> The **`refund.processed` webhook** is the **most reliable and recommended** way to receive the final status update (Processed, Failed or Reversed).
>
> We strongly suggest implementing **both** the Refund API response handler (for immediate status) and the **`refund.processed` webhook** (for the definitive final status update) to ensure reliable status tracking and update your inventory/ledger accurately.

> [accordion] Do all refunds (including Instant Refunds) always return a 'processed' status instantly via the Refund API?
>
> No, not all refunds return 'processed' instantly.
>
> * **Instant Refunds (Optimum Speed):** If the refund is successfully processed instantly, the API response will typically show a `processed` status immediately or shortly after.
> * **Normal Refunds (Standard Speed) or Failed Instant Refunds:** If the refund defaults to the normal processing speed (5-7 business days) or if the API call is synchronous but the bank processing takes time, the initial API response might return a **`pending`** status.
>
> In all scenarios, rely on the **`refund.processed` webhook** for the final, verified status update to ensure your application records are correct.

> [accordion] How do I integrate the Razorpay Curlec Refund API into my Shopify (or other e-commerce) store?
>
> For major e-commerce platforms like Shopify, WooCommerce or Magento, you typically **do not** integrate the Refund API directly into your website's code.
>
> The process works automatically through the platform's administration panel:
>
> 1. **Initiate Refund:** Log in to your Shopify (or platform) **Admin Panel**.
> 2. **Select Order:** Locate the order you wish to refund.
> 3. **Process Refund:** Use the platform's native **Refund** button or feature.
>
> The platform's installed Razorpay plugin or application then automatically calls the necessary Refund API on your behalf to process the refund via Razorpay Curlec.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > You only need to integrate the Refund API directly if you are using a **custom-built website** or application, not a standard e-commerce platform.
