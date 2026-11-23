> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Payment Link

> Create Standard Payment Links from the Dashboard or using APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can create Payment Links using:

* [Razorpay Curlec Dashboard](#create-a-standard-payment-link-from-dashboard)
* [API](https://razorpay.com/docs/my/api/payments/payment-links/create-standard.md)

## Create a Standard Payment Link From Dashboard

You can create a Standard Payment Link to accept payments from your customers. When you create a Payment Link, it moves to **Issued** state by default.

> [accordion] To create a Standard Payment Link:
>
> 1. Log in to the Dashboard.
> 2. Navigate to **Payment Links**.
> 3. Click **+ Create Payment Link**.
> 4. Click **Standard Payment Link**.
> 5. Enter the required details in the Standard Payment Link pop-up page.
>    <ul>
>      <li>**Amount** (Mandatory): Select the currency and amount for the Payment Link. For example, select `RM` and enter`1000` for `RM1,000`.</li>
>      <li>**Payment For** (Optional): Enter a description entered. For example, `School fees for Siti Aisyah`.</li>
>      <li>**Customer Details** (Optional): Enter the customer's email and phone number. For example, `+60123456789` and `siti.aisyah@example.com`.</li>
>      <li>**Notify via Email** (Optional): Select this option if you want us to send the Payment Link to the customer via email. Available only if you have entered the customer's email. You can't change this after the link is created, and you can [resend the link](https://razorpay.com/docs/my/payments/payment-links/resend.md) by email only if you select it here.</li>
>      <li>**Notify via SMS**: Don't select this option. SMS isn't available for Payment Links in Malaysia, as Malaysian Communications and Multimedia Commission (MCMC) rules let telcos block SMS messages that contain links. The customer would receive the SMS with the link replaced by asterisks (`*`). Select **Notify via Email** instead.</li>
>      <li>**Reference Id** (Optional): Provide a unique reference number for the link. For example, `Adbb001`.</li>
>      <li>**Link Expiry** (Optional): The date and time at which the Payment Link should expire. This must be at least 15 minutes after the time you create the link.</li>
>      <li>**Notes** (Optional): Provide the internal notes for the Payment Link. For example:<ul><li>Title (key): Acme Corp.</li><li>Description (value): Birthday cake Feb.</li></ul></li>
>    </ul>
> 6. Review the details and click **Create Payment Link**.

## Make Test Payments for Payment Links

> [!NOTE]
>
> **Handy Tips**
>
> We recommend you to create Payment Links in **Test Mode** for testing purposes.

> [!WARNING]
>
> **Test Mode Limit**
>
> In test mode, you can create up to 30 Payment Links per business. If you need to create more than 30 Payment Links for testing purposes, contact  [Razorpay Curlec Support](https://curlec.com/support/).

> [accordion] To make test payments for Payment Links:
>
> 1. Log in to the Dashboard.
>
> 2. Navigate to **Payment Links**.
>
> 3. Select the Payment Links you wish to test.
>
> 4. Copy the link URL and open it in your browser.
>
> 5. Select the payment method of your choice and proceed with the payment.
>
> 6. Select **Success** or **Failure**, depending on which flow you wish to test.
>
> 7. You should see a confirmation message depending on the flow you have selected.

## Create a Payment Link Using API

You can create a Payment Link using the [Create a Standard Payment Link API](https://razorpay.com/docs/my/api/payments/payment-links/create-standard.md).

#### Related Information

* [FAQs](https://razorpay.com/docs/my/payments/payment-links/faqs.md)
* [Payment Links APIs](https://razorpay.com/docs/my/payments/payment-links/apis.md)
