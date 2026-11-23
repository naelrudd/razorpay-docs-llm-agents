> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Resend a Payment Link

> Resend a Payment Link to a customer by email.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can resend a Payment Link in the **Issued** state to your customer by email only if you selected **Notify via Email** when you created it. A resend uses only the notification channels selected at creation, and you can't change them later.

> [!WARNING]
>
> **Watch Out!**
>
> * Payment Links can't be sent by SMS in Malaysia. Malaysian Communications and Multimedia Commission (MCMC) rules let telcos block SMS messages that contain links. The customer receives the SMS with the link replaced by asterisks (`*`), so they can't open it. Resend the link by email instead.
> * If you didn't select **Notify via Email** when you created the Payment Link, the Dashboard doesn't show the resend option for it. Copy the Payment Link URL and share it with the customer yourself, or create a new Payment Link with **Notify via Email** selected.

## Resend Payment Links From Dashboard

To resend a Payment Link:

1. Log in to the Dashboard.
2. Navigate to **Payment Links**.
3. Select the Payment Link which you wish to resend. The details appear on the right-side pane.
4. Click the resend icon. It appears only if you selected **Notify via Email** when you created the link.
5. Select **Email**. Don't select SMS, as SMS isn't available in Malaysia.
6. Click **Send Link**.

## Resend Payment Links Using API

You can resend a Payment Link in `issued` state by email using the [Send or Resend Notifications](https://razorpay.com/docs/my/api/payments/payment-links/resend.md) API.

#### Related Information

* [Payment Links States](https://razorpay.com/docs/my/payments/payment-links/states.md)
* [Create a Payment Link](https://razorpay.com/docs/my/payments/payment-links/create.md)
* [FAQs](https://razorpay.com/docs/my/payments/payment-links/faqs.md)
* [Subscribe to Webhooks](https://razorpay.com/docs/my/payments/payment-links/subscribe-to-webhooks.md)
