> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Offers on Apple Pay

> Apply card offers to Apple Pay payments on Razorpay Standard Checkout, with no changes to your integration.

Available in
🇮🇳 India

Card offers you run on Razorpay Standard Checkout also apply when customers pay with [Apple Pay](https://razorpay.com/docs/payments/payment-methods/apple-pay.md). Apple Pay does not share the actual card number with Razorpay. Instead, Razorpay identifies the card the customer picks in their Apple Wallet and checks the offer against it. Bank, network, card type and IIN offers work the same way they do on a regular card payment, and the discount is itemised on Checkout.

For example, if you run an instant discount on a bank's credit cards, customers who pay with that bank's credit card through Apple Pay now get the discount too.

> [!NOTE]
>
> **No Changes Needed**
>
> You do not need to change your integration or create new offers. Any card offer that is active on your account applies to Apple Pay payments.

## Prerequisites

* [Apple Pay enabled on Standard Checkout](https://razorpay.com/docs/payments/payment-methods/apple-pay.md).
* One or more [card offers](https://razorpay.com/docs/payments/offers/create.md) created on the Dashboard and [integrated with Standard Checkout](https://razorpay.com/docs/payments/offers/standard-integration).

## How It Works

1. The customer selects a card offer on Checkout, or Checkout applies one automatically. Checkout shows the discounted amount.
2. The customer taps **Apple Pay**. The offer carries over to the Apple Pay payment.
3. In the Apple Pay sheet, the customer chooses a card and authenticates with Face ID or Touch ID.
4. Razorpay identifies the card behind the Apple Pay token and checks that it is eligible for the offer.
5. If the card is eligible, the payment completes at the discounted amount. If it is not, the payment fails and the customer sees the reason on Checkout.

![A card offer applied on Checkout with the Apple Pay button](https://mintcdn.com/razorpay-881012b3/MLemAp0myTxAmFg0/static/docs-home/assets/apple-pay-offers-checkout.png?fit=max\&auto=format\&n=MLemAp0myTxAmFg0\&q=85\&s=a8a7d8e7e48b74ceab64fdf6b27aec4b)

> [!NOTE]
>
> **Offer Validation Happens After Authentication**
>
> On a regular card payment, Razorpay checks the offer when the customer enters their card details. On Apple Pay, the card details are only available after the customer authenticates in the Apple Pay sheet, so the offer is checked at that point.

## Supported Offers

| Offer type | Applies on Apple Pay |
| - | - |
| Card offers by bank, network or card type (credit or debit) | Yes |
| Card offers on specific IINs | Yes |
| Card offers with a **Maximum Usage Per Card** limit | Yes. Usage is counted per card across Apple Pay and regular card payments. |
| Offers on other payment methods, such as UPI, netbanking and wallets | No. These offers are removed when the customer chooses Apple Pay. |

If you [force an offer](https://razorpay.com/docs/payments/offers/standard-integration#method-3-force-offer) that is not a card offer, Apple Pay is not shown on Checkout for that order.

## Limitations

* Offers on Apple Pay are available only on Razorpay Standard Checkout, for domestic payments in India. They are not available on Custom Checkout or Server-to-Server (S2S) integrations.
* Apple Pay does not work in test mode, so you cannot test offers on Apple Pay in test mode.
* If an Apple Pay payment fails, Checkout removes all offers applied to it. When the customer retries, the payment goes through without an offer, at the full amount.

## Frequently Asked Questions

> [accordion] Why did a customer's Apple Pay payment fail after they applied an offer?
>
> The card the customer chose in the Apple Pay sheet was not eligible for the offer. For example, the offer is for one bank's cards and the customer paid with another bank's card, or the customer has already used the offer the maximum number of times on that card.
>
> Checkout shows the customer why the offer could not be applied. The Apple Pay sheet itself shows only a general payment failure, as Apple does not allow Razorpay to show its own messages there. If the customer tries again, the payment goes through without the offer.

> [accordion] Do I need to create separate offers for Apple Pay?
>
> No. Your existing card offers apply to Apple Pay payments. There is no separate offer type or setting for Apple Pay.

> [accordion] How do I find Apple Pay payments that used an offer?
>
> Apple Pay payments have `"provider": "apple_pay"` in the payment `notes` field. To see the offer applied on a payment, use the [Fetch Payment With Expanded Offers API](https://razorpay.com/docs/api/payments/fetch-payment-expanded-offers.md).

### Related Information

* [Apple Pay Standard Checkout](https://razorpay.com/docs/payments/payment-methods/apple-pay.md)
* [Create Offers](https://razorpay.com/docs/payments/offers/create.md)
* [Integrate Offers with Standard Checkout](https://razorpay.com/docs/payments/offers/standard-integration)
* [Offers FAQs](https://razorpay.com/docs/payments/offers/faqs.md)
