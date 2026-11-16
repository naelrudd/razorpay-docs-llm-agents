> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integration Steps

> Steps to integrate your Bagisto store with Razorpay Payment Gateway.

Available in
🇮🇳 India

Follow the steps given below to integrate Razorpay Payment Gateway with your Bagisto website.\


> [card] [1. Build Integration](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/bagisto/integration-steps.md#build-integration)
>
> Install and configure the Bagisto Commerce plugin.

> [card] [2. Test Integration](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/bagisto/integration-steps.md#test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-Live Checklist](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/bagisto/integration-steps.md#go-live-checklist)
>
> Check the go-live checklist.

> [!NOTE]
>
> For
>
> * **Platform:** Bagisto (open-source e-commerce)
> * **Payment method:** Razorpay (built into Bagisto)
>
> This guide covers **core Bagisto only** (single-store checkout). It does not cover the Bagisto Marketplace (multi-vendor) extension.

## Overview

Razorpay is available in Bagisto as a **built-in payment method** — it comes with Bagisto, so there is nothing extra to install. As a store owner, you have to simply enable and configure it from the admin panel. At checkout, customers pay through Razorpay (cards, UPI, netbanking, wallets) and are returned to the store once the payment is done.

Payment is confirmed automatically the moment the customer returns from Razorpay and successful payments are **captured automatically**. The store owner does not need to capture them manually.

### Prerequisites

| Requirement | Detail |
| - | - |
| Razorpay account | An active account with Test and Live API keys, available from the Razorpay Dashboard |
| Bagisto store | A running Bagisto 2.x store with admin access |
| Store currency | INR — Razorpay in Bagisto supports INR only |
| Public store URL | The storefront must be reachable on the internet so customers can return after paying |

### Supported

* **Checkout:** Razorpay Standard Checkout (the Razorpay payment window).
* **Currency:** INR only. If the store/cart is in any other currency, Razorpay is not offered and a `currency not supported` message is shown.
* **Capture:** Automatic — successful payments are captured right away; there is no manual capture step.

### Payment flow (what the customer sees)

1. The customer selects Razorpay at checkout and places the order.
2. The Razorpay payment window opens, with the amount and the customer's name, email and phone pre-filled.
3. The customer pays using a card, UPI, netbanking or a wallet.
4. On success, the customer is returned to the store and the order is confirmed.
5. On cancel or failure, the customer is returned to the cart to try again.

## Integration steps

The flow has three phases: **Build → Test → Go live**.

## Build Integration

Razorpay comes with Bagisto, so there is nothing to install.

1. Log in to the Bagisto admin.
2. Go to **Configuration → Sales → Payment Methods → Razorpay**.
3. Fill in the fields (see the table below) and **Save**.

#### Configuration fields

| Field | What it's for |
| - | - |
| Status | Turn Razorpay on or off at checkout |
| Title | The name customers see for this method at checkout (default "Razorpay") |
| Description | Short text shown under the title |
| Logo | The image shown on the Razorpay payment window |
| Merchant Name | Your business name, shown on the Razorpay payment window |
| Merchant Description | A short description shown on the Razorpay payment window |
| Client ID | Your Razorpay Live API key — used when Sandbox is off |
| Client Secret | Your Razorpay Live API secret — used when Sandbox is off |
| Sandbox (Test mode) | Switch between test and live. On = your test keys are used; Off = your live keys are used |
| Test Client ID | Your Razorpay Test API key — used when Sandbox is on |
| Test Client Secret | Your Razorpay Test API secret — used when Sandbox is on |
| Sort Order | Where Razorpay appears in the list of payment methods |

**Where to get your keys:** In the Razorpay Dashboard, go to [Account & Settings → API Keys → Generate Key](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md). Generate separate keys for Test Mode and Live Mode.

**Scope of the settings:** The Razorpay settings are saved per store (sales channel), so a multi-store merchant configures the keys separately for each store. Title and Description can also be translated per store language.

Razorpay appears at checkout only when it is enabled, the correct keys are filled for the active mode (Test vs Live), and the store currency is INR.

## Test Integration

1. Turn **Sandbox (Test mode) On** and enter your Test keys.
2. Make sure the store currency is INR.
3. Place a test order and choose Razorpay. On the payment window, use Razorpay's test payment details (test UPI / test cards from the Razorpay documentation) — no real money is charged.
4. In the Razorpay Dashboard (**Transactions → Payments**), the payment should appear and show as captured.
5. Confirm the order appears in the Bagisto admin under **Sales → Orders**.

## Go-Live Checklist

1. In the Razorpay Dashboard, switch to **Live Mode** and generate your Live API keys.
2. In Bagisto, turn **Sandbox (Test mode) Off** and enter your Live keys, then **Save**.
3. Real payments are now accepted. Successful payments are captured automatically.

## Troubleshooting

Before contacting support, have the following ready:

* Your Bagisto version.
* Whether the issue is in Test or Live mode.
* The affected order (and the Razorpay payment id from the dashboard).
* A description or screenshots / screen recording of what happened.

## FAQs

> [accordion] Which currencies are supported?
>
> Only INR. If the store/cart is in any other currency, checkout is blocked with a message naming the currency — for example, for a USD cart: "The currency USD is not supported. Supported Currencies: INR." Set the store currency to INR.

> [accordion] Why am I not able to see the Razorpay method at checkout?
>
> Confirm all three of the following:
>
> * Razorpay is enabled (Status is on).
> * The correct keys are entered for the active mode (Test keys if Sandbox is on, Live keys if Sandbox is off).
> * The store currency is INR.

> [accordion] The Razorpay payment window does not open, or shows `Something went wrong`
>
> Make sure the correct keys are entered for the active mode and were saved. Re-open the payment page after saving.

> [accordion] I switched to live mode but payments still behave like test mode (or the other way round).
>
> The Sandbox (Test mode) toggle decides which keys are used — On uses your test keys, Off uses your live keys. Make sure the matching key pair is filled for the mode you want.

> [accordion] Do refunds made in the Razorpay Dashboard show up in Bagisto?
>
> No — a refund created directly in the Razorpay Dashboard does not update the order in Bagisto. Process refunds from the Bagisto admin → Sales so your store records stay in sync.

> [accordion] Do I need to capture payments manually?
>
> No. Successful payments are captured automatically.

> [accordion] The amount shown looks different from the order total.
>
> Razorpay displays the amount in the currency's smallest unit (paise for INR). The order total in Bagisto is the correct value — only the way Razorpay shows it differs.

## Related Information

* [Bagisto — Payment Methods (user docs)](https://docs.bagisto.com/payment-method/payment-methods.html)
* [Bagisto — Installation (developer docs)](https://devdocs.bagisto.com/getting-started/installation.html)
* [Bagisto — GitHub repository](https://github.com/bagisto/bagisto)
