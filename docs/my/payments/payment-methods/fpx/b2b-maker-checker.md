> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# FPX B2B Maker-Checker

> Hold FPX payments made from a corporate bank account until the company's authorised checker approves them.

Available in
🇲🇾 Malaysia

An FPX B2B payment is made from a company bank account. One person at the company — the maker — raises the payment, and a separate authorised person — the checker — approves it inside the company's own bank portal.

By default, a payment that is waiting on a checker fails immediately. With maker-checker enabled, the payment instead stays in the `created` state for up to five days, giving the checker time to act.

> [!WARNING]
>
> **Watch Out!**
>
> This feature changes the payment status your systems receive for the same event, so it is enabled only on request and only with your explicit agreement. Confirm that your integration can handle a payment staying in `created` for up to five days before asking for it.

> [!NOTE]
>
> **Payment Method Enablement**
>
> FPX must already be live on your account. Contact your account manager or raise a request with our [Support team](https://curlec.com/support/) to enable maker-checker.

## What Changes

* Only payments from the 24 corporate FPX banks are held. Retail FPX payments and every other payment method behave exactly as before.
* A held payment stays in `created` for up to five days. The window is fixed and cannot be shortened or extended for an individual business.
* Your customer receives no emails while the payment is waiting. Emails resume at the final outcome.
* A waiting payment cannot be cancelled. Treat it as pending until an outcome webhook arrives.

## Identify a Waiting Payment

A payment waiting for approval and a payment abandoned at checkout both show the `created` status. A waiting payment also carries the following on [Payment Fetch](https://razorpay.com/docs/my/api/payments/fetch-with-id.md) and in the `payment.created` payload:

```json theme={null}
"internal_error_code": "BAD_REQUEST_PAYMENT_PENDING_AUTHORIZATION"
```

An abandoned payment does not carry this.

## Webhooks

| Webhook | When it is sent |
| - | - |
| `payment.created` | When the payment is raised and starts waiting, if you subscribe to this event. |
| `payment.authorized` / `payment.captured` | When the checker approves the payment. |
| `payment.failed` | When the checker rejects the payment, or the five-day window lapses. |

Know more about [setting up webhooks](https://razorpay.com/docs/my/webhooks).

## Payment Outcomes

| What happens | Result | Refund |
| - | - | - |
| The checker approves within five days | The payment is authorised and then captured, like any on-time payment. | Not applicable. |
| The checker rejects the payment | The payment moves to `failed` and you receive `payment.failed`. | Not applicable. |
| Five days lapse with no decision | The payment fails with `BAD_REQUEST_PAYMENT_TIMED_OUT`. | Not applicable. |
| The approval arrives after the window | The payment has already failed. The late approval is recorded and refunded to your customer automatically. | Automatic. You never raise this refund yourself. |

## Supported Banks

Payments from the following 24 corporate FPX banks are held for approval:

`PHBM_C` · `MFBB_C` · `ARBK_C` · `AGOB_C` · `BNPA_C` · `BIMB_C` · `BKRM_C` · `BMMB_C` · `CIBB_C` · `CITI_C` · `DEUT_C` · `HSBC_C` · `HLBB_C` · `KFHO_C` · `MBBE_C` · `OCBC_C` · `PBBE_C` · `PBBN_C` · `RHBB_C` · `SCBL_C` · `UOVB_C` · `SBIA_C` · `SBIB_C` · `SBIC_C`

## Frequently Asked Questions

> [accordion] Can Razorpay Curlec approve or chase a payment that is waiting?
>
> No. The approval sits with your customer's finance team, in their own bank's portal. Only their checker can approve or reject it.

> [accordion] Can the five-day window be shortened for my business?
>
> No. The window is fixed and is not configurable.

> [accordion] Does this affect my retail FPX payments?
>
> No. Only payments from the 24 corporate FPX banks are held. Retail FPX and every other payment method are unaffected.

> [accordion] Can I test this before going live?
>
> No. Maker-checker is not available in test mode — it can only be seen working on a live corporate payment.

### Related Information

* [FPX](https://razorpay.com/docs/my/payments/payment-methods/fpx)
* [About Payment Methods](https://razorpay.com/docs/my/payments/payment-methods)
