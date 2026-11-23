> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# FAQs (Frequently Asked Questions)

> Find answers to frequently asked questions about Razorpay Curlec Route.

Available in
🇮🇳 India
🇲🇾 Malaysia

> [accordion] How can I transfer money to customers?
>
> You can use Razorpay Curlec Route from the Dashboard or using APIs to transfer money to customers.
>
> **To use Route from the Dashboard**:
>
> 1. Log in to the Dashboard.
> 2. Find a payment on the Transactions panel (left column). Click on the Payment id to view its details on the right panel. Create a transfer from the payment.
> 3. Alternatively, find a payment under the Payments tab on the Route panel. Click on the Payment id to view its details, and create a transfer.
>
> You can also use [Route Transfers APIs](https://razorpay.com/docs/my/api/payments/route.md) to transfer money.

> [accordion] How can I track the status of transactions initiated using Route?
>
> When a transfer is created from the Dashboard or using the Route APIs, you are notified if the transfer creation was successful or not.
>
> The transfer is processed asynchronously and on success, `transfer.processed` webhook is sent (if enabled). Know more about [setting up Webhooks](https://razorpay.com/docs/my/payments/route/subscribe-to-webhooks.md).

> [accordion] How can I track the status of funds transferred to linked accounts?
>
> The `transfer.processed` webhook is sent for every successful transfer. The webhook indicates that the requested transfer is processed, funds are debited from the business and credited to the linked account.
>
> Know more about [setting up Webhooks](https://razorpay.com/docs/my/payments/route/subscribe-to-webhooks.md).

> [accordion] Can you reverse a transfer?
>
> Yes, you can reverse transfers. You can initiate a reversal from the Dashboard or using APIs.
>
> **To create a reversal from the Dashboard**:
>
> 1. Log in to the Dashboard.
> 2. Go to **Route** → **Transfers**. Click on a **Transfer id** to view the details. Click on the **Create Reversal** button to reverse the transfer.
>    * You can also use the [Reverse Transfers from all Linked Accounts API](https://razorpay.com/docs/my/api/payments/route/reverse-a-transfer.md) to reverse money transfer.
>    * You can also [refund payment and simultaneously reverse](https://razorpay.com/docs/my/api/payments/route/refund-payments-and-reverse-transfer.md) all the transfers made on that payment.

> [accordion] Can I create transfers on an order for international currencies?
>
> No, you cannot create transfers on an order for international currencies. The transfer reversal is available only for **MYR**.

> [accordion] When should I initiate Transfer using Payments?
>
> You should initiate Transfer using Payments when information regarding payment split is decided post customer transaction and/or has some other approval/verification dependencies on the linked accounts. For example, in life insurance, you can only transfer funds to a linked account post-approval and policy issuance.

> [accordion] When should I initiate Direct Transfers?
>
> **Direct Transfers** is an on-demand feature. Raise a request with [our Support team](https://curlec.com/support/) to get it enabled for your account. You should initiate Direct Transfers when fund transfers to a linked account is not necessarily linked to any incoming payments. You can also use this feature for payouts.

> [accordion] I have created a linked account on the Dashboard in the Test mode. Can I use it on the Live mode?
>
> You can use a linked account created in the **Test** mode on the **Live** mode and vice versa.

> [accordion] Does Razorpay Curlec Route support international currencies?
>
> Currently, we support only **MYR** for Razorpay Curlec Route.

> [accordion] Should the linked account websites be whitelisted to use route?
>
> No. Your linked account websites do not need to be whitelisted to use Route. The only requirement is that your website, from which your customers will make the payment, must be whitelisted with Razorpay Curlec.

> [accordion] Can I use the same Razorpay Curlec API Keys on multiple websites or domains?
>
> Yes, you can use the same set of Live Mode API Keys on multiple websites or domains.
>
> The Live Mode keys are tied to your single Razorpay Curlec account, allowing them to process live transactions from any domain where they are implemented. Using the same keys on a new website **will not impact** the live payments running on your existing, whitelisted website.
>
> **For Testing:**
>
> We strongly recommend using your **Test Mode API Keys** when integrating Razorpay Curlec on any new website. Test payments are simulated and ensure that your live payment processing on existing sites remains unaffected during development.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Ensure your new website's domain is whitelisted in your Razorpay Curlec account to avoid payment disruptions once you switch to Live Mode.

> [accordion] How should I manage API Keys when working with a developer for integration?
>
> API Keys are generated and managed by the **Owner or Admin** roles in the Dashboard. Razorpay Curlec does not offer a separate Developer Access Role.
>
> To securely facilitate integration and testing (for example, for platforms like WooCommerce, where direct API key input might be required for some plugins), follow this standard workflow:
>
> * **Phase 1: Testing (Integration)**
>   The Owner or Admin must generate and securely share the **Test Mode API Keys** with the developer. The developer will use these keys to build and test the integration without affecting any live payments.
> * **Phase 2: Go-Live**
>   Once testing is complete, the Owner or Admin must generate the **Live Mode API Keys** and provide them to the developer to replace the Test Keys in the final application setup.
>
> This ensures security and maintains clear control over your live payment environment.

> [accordion] How do I transfer funds using the Route API after accepting a payment via a Razorpay Curlec Payment Link?
>
> You can transfer funds to Linked Accounts using the Route API by referencing the Payment id generated by the Payment Link transaction. This approach is called Create Transfers from Payments.
>
> You can execute the transfer in three ways:
>
> 1. **Dashboard:** Initiate a transfer directly from the specific Payment id within the Transactions or Route section of your Dashboard.
> 2. **API:** Use the **Create Transfers from Payments API**, where you specify the Payment id to be split among your Linked Accounts.
> 3. **Automatic:** If you set up an automatic split before the payment link is generated, the funds will be split instantly upon successful payment.
>
> Know more about the [Create Transfers from Payments API](https://razorpay.com/docs/my/api/payments/route/create-transfers-payments.md).

> [accordion] What are the different fees involved when splitting a payment using Razorpay Curlec Route?
>
> A Route transaction involves two distinct types of fees deducted from your account balance:
>
> 4. **Payment Gateway Fee:** This fee is charged on the **full Payment Amount** received from the customer, before any funds are split. This covers the cost of processing the original transaction.
> 5. **Transfer Fee:** This fee is charged on the **Amount Transferred** to each Linked Account. This covers the cost of facilitating the money transfer from your main account to the Linked Account(s).
>
> Both fees are calculated based on your agreed-upon pricing plan and are subject to GST (or local equivalent tax, where applicable). Your final commission or retained amount is the remaining balance after both fees and the transfer amount have been deducted.
>
> For detailed calculation examples, refer to our [Transfers and Related Fees Examples](https://razorpay.com/docs/my/payments/route/transfer-fees-example.md) page.
