> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# UPI

> Accept payments from customers in India paying with any UPI app on Razorpay Curlec Checkout.

Available in
🇮🇳 India
🇲🇾 Malaysia

UPI lets your Malaysian business accept payments from customers in India. Your customer pays in Indian rupees from the UPI app they already use, and you are settled in Malaysian ringgit, net of fees, on your usual [settlement schedule](https://razorpay.com/docs/my/payments/settlements).

Razorpay Curlec connects to UPI through NPCI International Payments Limited (NIPL), the arm of NPCI that lets a UPI payment reach a payment provider outside India. You need no account, registration or agreement of your own in India.

> [!NOTE]
>
> **Payment Method Enablement**
>
> UPI is not enabled by default. Contact your account manager or raise a request with our [Support team](https://curlec.com/support/) to have it switched on for your account.

## How UPI Works

1. The customer selects **UPI** at your checkout. On mobile they are handed straight into their UPI app; on desktop they scan a QR code.
2. The customer approves the payment in their UPI app, in Indian rupees, against their Indian bank account.
3. The payment reaches Razorpay Curlec through NIPL.
4. The amount is converted and settled to you in Malaysian ringgit, net of fees.

Your customers can pay with any UPI app, such as Google Pay, PhonePe, Paytm, BHIM or their bank's own app.

## Supported Flows

| Flow | Description | Availability |
| - | - | - |
| Dynamic Intent | The customer is handed into their UPI app to approve the payment. Used on mobile. | ✓ |
| Dynamic QR | The customer scans a QR code with their UPI app. Used on desktop. | ✓ |
| Static QR | A single reusable QR code. | Not supported. |

## Availability by Integration

| Integration | Availability |
| - | - |
| Standard Checkout, Payment Links, Payment Pages, Invoices and plugins | ✓ |
| S2S integration | ✓ |
| Mobile SDKs | Not available. |
| Custom Checkout | Not available. |

You do not need to change your integration or write any code. Once UPI is enabled, it appears at your checkout on its own, including on Payment Links, Payment Pages and Invoices.

## Enable UPI

Raise a request with your account manager or our [Support team](https://curlec.com/support/). Share the following:

* The UPI ID you would like your customers to see. This is your business name followed by `@curlecsbi`, for example `yourbusiness@curlecsbi`. Use letters and digits only — no dashes, dots or other special characters.
* Your agreed UPI rate.
* Whether you want UPI enabled on your live account or your test account first.

## Test UPI Payments

You can test UPI on your test account before going live.

> [!WARNING]
>
> **Watch Out!**
>
> When you scan the test QR code with a real UPI app, the app shows an error while your checkout reports success. This is expected: test mode demonstrates the Razorpay Curlec checkout experience, not the UPI app's.

## Frequently Asked Questions

> [accordion] What currency does my customer pay in, and what do I receive?
>
> Your customer pays in Indian rupees. You receive Malaysian ringgit, net of fees, like any other payment on your account.

> [accordion] When am I paid?
>
> UPI payments settle to you in ringgit on your usual [settlement schedule](https://razorpay.com/docs/my/payments/settlements). If you need the exact timing for a specific payment, share the payment ID with our [Support team](https://curlec.com/support/).

> [accordion] Do I need to register with NPCI or an Indian bank?
>
> No. Razorpay Curlec handles the registration on your behalf when UPI is switched on for your account.

> [accordion] Can I accept recurring payments or subscriptions over UPI?
>
> No. UPI payments from customers in India are one-time payments only. Know more about the methods supported for [Recurring Payments](https://razorpay.com/docs/my/payments/recurring-payments.md).

> [accordion] My customer says the payment failed in their app, but my Dashboard shows it succeeded. Which is right?
>
> The Dashboard. The payment went through. Share the payment ID with our [Support team](https://curlec.com/support/) and we will look into the mismatch.

### Related Information

* [About Payment Methods](https://razorpay.com/docs/my/payments/payment-methods)
* [Payment Methods on the Dashboard](https://razorpay.com/docs/my/payments/dashboard/account-settings/payment-methods.md)
