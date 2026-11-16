> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# FAQs (Frequently Asked Questions)

> Find answers to frequently asked questions about Razorpay Payment Links.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

## For Businesses

> [accordion] I do not have a website or app. Can I still use Payment Links to accept payments from customers?
>
> Yes, you can. You do not need a website or mobile app to use Payment Links. You can create and send Payment Links in 3 easy steps:
>
> 1. Log in to the Dashboard and create a Payment Link.
> 2. Send it to the customer via SMS and/or email.
> 3. The customer opens the link and completes the payment.

> [accordion] Can I create a Payment Link using which customers can pay an amount of their choice?
>
> No. You can create Payment Links with fixed amounts only. Customers cannot enter an amount of their choice.

> [accordion] Can I accept recurring payments using Payment Links?
>
> No. Payment Links can only be used to accept one-time payments. Use [Razorpay Subscriptions](https://razorpay.com/docs/sg/payments/subscriptions/) to collect recurring payments from customers.

> [accordion] Can I show support details such as helpline, support webpage and email address on the Payment Link?
>
> Yes, you can show support details on the Payment Link.
>
> Follow these steps:
>
> 1. Log in to the Dashboard
> 2. Navigate to **Account & Settings** → **Business settings**.
> 3. In the **Customer support details** section, enter these details:
>    * **Phone Number**
>    * **Email id**
>    * **Website/Contact us link**
> 4. Click **Submit**.

> [accordion] Why is there a Report Payment Link option on a Payment Link created for my business?
>
> As per Razorpay's risk policy, the **Report Payment Link** option will be displayed by default for all Payment Links.

> [accordion] Why is the customer email address and phone number I specified during Payment Link creation not auto-populating on the hosted payment page?
>
> As per our updated security policy, even if the customer's email address and phone number are provided while creating the Payment Link, these details are not auto-populated on the Checkout section of the Payment Link hosted page. The customer will have to enter these details manually while making the payment.

> [accordion] Why is there a Report Payment Link option on a Payment Link request email sent for my business?
>
> As per our risk policy, the **Report Payment Link** option will be displayed by default on all Payment Link request emails.

> [accordion] Can I set a minimum upfront payment amount when I enable Partial Payments for a Payment Link on the Dashboard?
>
> Currently, you can set a minimum upfront amount only through APIs. Refer to this [API endpoint](https://razorpay.com/docs/sg/api/payments/payment-links/create-standard.md#request-parameters) for more information. To enabled this feature for your account, raise a ticket to the support team.

> [accordion] Can I cancel a Payment Link if it is in "partially\_paid" state?
>
> No. You cannot cancel a payment link if it is in `paid` or `partially_paid` state. You can only cancel a payment link if it is in `issued` state.

> [accordion] Can I automatically send an invoice to customers after they complete payment via a Payment Link using Razorpay Invoices?
>
> No, you cannot send an invoice automatically. [Razorpay's Invoices](https://razorpay.com/docs/payments/invoices) is designed to initiate payments, not for post-payment invoicing. You need to handle invoice generation on your end after receiving payment confirmation.

## For Customers

> [accordion] I have received a Payment Link that looks suspicious and fraudulent. How can I report it?
>
> There are two ways by which you can report a fraudulent Payment Link:
>
> * Using the Payment Link hosted page.
> * Using the email notification you received.
>
> **Using the Payment Link Hosted Page** \\
>
> Follow these steps:
>
> 1. Click the Payment Link and open the hosted page.
> 2. Click **Report Payment Link**.
>
> **Using an Email Notification You Received** \\
>
> Follow these steps:
>
> 1. Open the email received from the business.
> 2. Click **Report Email**.
>
> **On Clicking Report Option** \\
>
> After you click the report link, a form is displayed. Enter the following details:
>
> 1. **Reason to report this merchant**: Click the drop-down list to select the relevant reason. For example, **Reporting fake website/company**.
> 2. **Email ID**: Enter your email address at which we can contact you for additional information.
> 3. **Contact No** (optional): Enter your contact number.
> 4. **Name** (optional): Enter your name.
> 5. Complete the captcha step and click **SUBMIT REPORT**.
>
> **Additional Steps** \\
>
> If you have already completed the payment, you can choose to:
>
> * Request a refund by contacting the business' support team. The support details are available on the Payment Link hosted page.
> * File a dispute against the business. Know more about [Disputes](https://razorpay.com/docs/payments/disputes).
