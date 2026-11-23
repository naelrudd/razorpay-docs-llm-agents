> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Pay Later

> Let your customers split a purchase into three interest-free instalments with Atome on Razorpay Curlec Checkout.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Pay Later lets your customers split a purchase into equal instalments while you are paid the full amount upfront. [Atome](https://www.atome.my/) is the Buy Now Pay Later provider available on Razorpay Curlec Checkout in Malaysia.

Your customer pays the first of three equal, interest-free instalments at checkout and repays the rest to Atome. Atome carries the credit risk, and you are settled in Malaysian ringgit for the full amount.

| Provider | Method Code | Provider Code |
| - | - | - |
| Atome | `paylater` | `atome` |

> [!NOTE]
>
> **Payment Method Enablement**
>
> Pay Later is not enabled by default, and it needs a registration with Atome. Contact your account manager or raise a request with our [Support team](https://curlec.com/support/) — we arrange the registration with Atome on your behalf, and we will confirm a date once it is underway.

## How Pay Later Works

1. The customer opens the **Pay Later** section at your checkout and selects Atome. Atome does not appear for amounts below RM 10.00.
2. The customer is sent to Atome's hosted page, or deep-linked into the Atome app.
3. Atome runs its own credit and eligibility check, shows the three-instalment schedule and collects the first instalment.
4. Atome confirms the payment back to us. Confirmation is asynchronous, so a payment can sit unconfirmed briefly before it is authorised.

You do not need to change your integration or write any code. Once Pay Later is enabled, Atome appears in the Pay Later section of your checkout on its own, including on Payment Links, Payment Pages and Invoices.

## Transaction Limits

| Limit | Value |
| - | - |
| Minimum transaction amount | RM 10.00 |
| Maximum transaction amount | Set by Atome per customer, based on their credit limit. |

## Frequently Asked Questions

> [accordion] Do I need to sign up with Atome separately?
>
> Atome registers you and provides us the credentials for your account. We arrange this with them — you do not need to approach Atome yourself.

> [accordion] Why do more Atome payments fail than my other methods?
>
> Atome approves or declines each customer on its own credit check. A decline appears as a failed payment on your side. This is expected behaviour, not a fault with your integration.

> [accordion] When do I get paid?
>
> Your existing [settlement](https://razorpay.com/docs/my/payments/settlements) cycle does not change when you add Pay Later. You receive the full purchase amount, and Atome collects the remaining instalments from your customer.

> [accordion] Can I refund a Pay Later payment?
>
> Yes, in full or in part. The refund comes off your next settlement batch.

> [accordion] Can I take subscriptions or recurring payments with Pay Later?
>
> No. Pay Later is for one-off purchases split into instalments. Know more about the methods supported for [Recurring Payments](https://razorpay.com/docs/my/payments/recurring-payments.md).

> [accordion] What other Buy Now Pay Later providers can I offer?
>
> Atome is the only Buy Now Pay Later provider live in Malaysia today.

### Related Information

* [About Payment Methods](https://razorpay.com/docs/my/payments/payment-methods)
* [About Instalments](https://razorpay.com/docs/my/payments/payment-methods/instalments)
