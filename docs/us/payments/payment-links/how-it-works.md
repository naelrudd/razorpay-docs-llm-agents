> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# How Payment Link Works

> Create Payment Links and send them to customers to receive payments and perform other actions.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Understand the complete end-to-end flow about how you can use Razorpay Payment Links.

![payment link flow](https://razorpay.com/docs/build/browser/assets/images/payment-links-pl-workflow.jpg)

## Workflow

The steps given below give a detailed view on the lifecycle of a Payment Link.

> [accordion] Step 1: Create a Payment Link
>
> [Create a Payment Link](https://razorpay.com/docs/us/payments/payment-links/create.md) by providing all the required details. You can set an expiry date and enable partial payments.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > You can [update](https://razorpay.com/docs/us/payments/payment-links/edit.md) or create a [duplicate](https://razorpay.com/docs/us/payments/payment-links/duplicate.md) Payment Link.
> >
> > **Payment Links APIs** \\
> >
> > * [Create a Payment Link](https://razorpay.com/docs/us/api/payments/payment-links/create-standard.md)
> > * [Edit a Payment Link](https://razorpay.com/docs/us/api/payments/payment-links/update-standard.md)
> > * [Cancel a Payment Link](https://razorpay.com/docs/us/api/payments/payment-links/cancel-standard.md)

> [accordion] Step 2: Send a Payment Link
>
> Send a Payment Link to a customer via email and/or SMS. The customer receives the link via SMS and email. They can open the link and pay using one of the available [payment methods](https://razorpay.com/docs/us/payments/payment-links#list-of-supported-payment-methods).

> [accordion] Step 3: Receive Payments
>
> The customer clicks the Payment Link and tries to make the payment.
>
> * The customer makes the payment. If [partial payment](https://razorpay.com/docs/us/payments/payment-links/partial-payments.md) is enabled, the customer can choose the amount to be paid.
> * The customer chooses the mode of payment.
>
> The customer makes a successful payment. The Payment Link is marked as `paid` or `partially` paid. You receive a notification about the payment.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > After the payment is captured, the amount is settled to your account as per the settlement schedule. Know more about [payments](https://razorpay.com/docs/us/payments/payments), [settlements](https://razorpay.com/docs/us/payments/settlements)  and [refunds](https://razorpay.com/docs/us/payments/refunds)  .

> [accordion] Step 4: Track Payment Links and Reports
>
> * **Notifications:** You receive notifications regarding activity on Payment Links via emails and webhook. Know more about [subscribing to Webhooks](https://razorpay.com/docs/us/payments/payment-links/subscribe-to-webhooks.md).
> * **Track Payments:** Track payments made against the issued Payment Links on Dashboard. Click **Payment Links** from the left menu. All the links are listed with their status under Payment Links.
> * **Reports:** Detailed insights can be gained using reports and real-time data on the Dashboard. These reports can then be used for accounting and reconciliation purposes. Know more about [reports](https://razorpay.com/docs/us/payments/dashboard/reports/list-of-reports.md#payment-links).

#### Related Information

<ul>
  <li>[Payment Links](https://razorpay.com/docs/us/payments/payment-links)</li>
  <li>[FAQs](https://razorpay.com/docs/us/payments/payment-links/faqs.md)</li>
  <li>[Payment Links APIs](https://razorpay.com/docs/us/payments/payment-links/apis.md)</li>
</ul>
