> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Web JS Integration

> Integrate Apple Pay using the headless Razorpay JS SDK with amount and currency passed at initialisation, with full control over button rendering and payment flow.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

The headless JS integration gives you full control over the Apple Pay button and payment flow. You initialise the Razorpay JS object with the amount and currency at start, then check eligibility and trigger the payment yourself. Know more about [Apple Pay](https://www.apple.com/apple-pay/).

> [!NOTE]
>
> **Availability in Singapore**
>
> Apple Pay on Custom Checkout is available on the web, on Safari (iPhone, iPad and Mac) and Chrome (Mac). It is not yet available for native mobile app integrations, such as the iOS Custom SDK or React Native, or for businesses on the Customer Fee Bearer (CFB) model.

> [accordion] Advantages
>
> Integrating Apple Pay using the headless JS SDK offers you the following advantages:
>
> * **Full control**: Render your own button or let Razorpay render one for you using `mount()`.
> * **Flexible initialisation**: Pass amount and currency at init time when the cart total is known upfront.
> * **Device-aware eligibility**: Use `canMakePayment()` to check Apple Pay support before showing the button.
> * **Event-driven results**: Handle payment success, failure and errors through event listeners.
> * **No extra script for existing merchants**: The SDK ships with the Custom Checkout script you already use.

## Prerequisites

Before starting the integration, ensure you have the following:

* Apple Pay enabled on your account. Contact the [Support team](https://razorpay.com/sg/support/) to enable it.
* An existing Razorpay Custom Checkout integration.
* Cards enabled on your Razorpay account in Live Mode.
* Your API Key Id available. Know how to generate [API Keys from the Dashboard](https://razorpay.com/docs/sg/payments/dashboard/account-settings/api-keys.md#generate-api-keys).
* An HTTPS-enabled domain (TLS 1.2 or higher). Apple Pay requires a secure context and will not function over HTTP.
* Server-side capability to create orders via the Razorpay Orders API.
* Every domain your customers see at checkout verified in the Dashboard for Apple Pay.

## Integration Steps

Follow the steps given below.

> [accordion] Step 1: Domain Verification
>
> Verify every domain your customers see at checkout for Apple Pay before you go live. A missing domain is the most common reason the Apple Pay button does not appear. To find the list of these domains, log in to the [Dashboard](https://dashboard.razorpay.com/app/payment-methods/apple-pay).
>
> > [!NOTE]
> >
> > **Handy Tip**
> >
> > Only domains whitelisted with the accounts service will be visible here. Similar domains are visible as well. Please contact our [Support team](https://razorpay.com/sg/support/) if you cannot find your Apple Pay showing domain here. You need to whitelist your URL.
>
> Dashboard Configuration and Verification
>
> * Log in to the Dashboard and open the [**Apple Pay**](https://dashboard.razorpay.com/app/payment-methods/apple-pay) settings.
> * You will see a list of domains associated with your business account:
>   * **Verified domains**: Ready for Apple Pay.
>   * **Unverified domains**: Need to be verified.
> * Click **Verify domains** for any unverified domains.

> [accordion] Step 2: Load the Script
>
> Include the Razorpay Custom Checkout script in your page's `<head>` tag.
>
> ```html HTML theme={null}
> <head>
>     <script src="https://checkout.razorpay.com/v1/razorpay.js"></script>
> </head>
> ```
>
> > [!NOTE]
> >
> > **Handy Tip**
> >
> > Load this script on every page where you intend to use the Apple Pay integration. Existing Custom Checkout merchants already load this script.

> [accordion] Running Alongside Standard Checkout
>
> Both `razorpay.js` (headless Apple Pay) and `checkout.js` (Standard Checkout) register their constructor on the same `window.Razorpay` global. If your page uses both, whichever script loads last overwrites the other's constructor on `window.Razorpay`. Capture the headless constructor as soon as `razorpay.js` loads, and let `checkout.js` load after it so `window.Razorpay` is restored to Standard Checkout's constructor for the rest of your page.
>
> ```html HTML theme={null}
> <head>
>     <script src="https://checkout.razorpay.com/v1/razorpay.js" onload="window.__rzpApplePay = window.Razorpay;"></script>
>     <script src="https://checkout.razorpay.com/v1/checkout.js"></script>
> </head>
> ```
>
> If you cannot guarantee this load order (for example, scripts injected dynamically or loaded in parallel), queue the captures instead and resolve them once both scripts have loaded:
>
> ```js JavaScript theme={null}
> window.__rzpQueue = window.__rzpQueue || [];
>
> function enqueueRazorpayCtor(name) {
>   window.__rzpQueue.push({ name, ctor: window.Razorpay });
>   if (window.__rzpQueue.length === 2) {
>     // Both scripts have loaded — headless SDK loaded first, Standard Checkout loaded second.
>     const [applePay, standard] = window.__rzpQueue;
>     window.__rzpApplePay = applePay.ctor;
>     window.Razorpay = standard.ctor;
>   }
> }
> ```
>
> Use `window.__rzpApplePay` (instead of `window.Razorpay`) to instantiate the headless Apple Pay object in Step 3, and leave `window.Razorpay` untouched for your existing Standard Checkout code.
>
> ```js JavaScript theme={null}
> const razorpay = new window.__rzpApplePay({ ... });
> ```

> [accordion] Step 3: Initialise with Amount and Currency
>
> Pass the amount and currency when you initialise Razorpay. Use the `on_payment_initiate_create_order` callback to create the order on your server right before the payment sheet opens.
>
> ```js JavaScript theme={null}
> const razorpay = new Razorpay({
>   key: 'rzp_test_XXXXXXXXXX',
>   prefill: {
>     contact: '+6591234567', // This is your customer's contact number.
>   },
>   amount: 1000,
>   currency: 'SGD',
>   on_payment_initiate_create_order: async () => {
>     // Called right before the payment sheet opens.
>     // Create the order on your server here, then:
>     razorpay.set('order_id', orderIdFromYourServer);
>   },
> });
> ```
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > `on_payment_initiate_create_order` is where you create the Razorpay order. You must call `razorpay.set('order_id', ...)` inside it before it resolves — the payment cannot be authorised without an order id.

> [accordion] Step 4: Listen for the Result
>
> Register event listeners for payment success and failure.
>
> ```js JavaScript theme={null}
> razorpay.on('payment.success', (response) => {
>   // response.paymentData.razorpay_payment_id
>   // response.paymentData.razorpay_order_id
>   // response.paymentData.razorpay_signature
> });
>
> razorpay.on('payment.failure', (response) => {
>   // response.error -> { code, description, source, reason }
> });
> ```

> [accordion] Step 5: Check Availability and Trigger the Payment
>
> Check whether the customer's device supports Apple Pay using `canMakePayment()`, then trigger the payment using one of the following options.
>
> > [tab] Option 1: mount() (Recommended)
> >
> > Use `mount()` to have Razorpay render an Apple Pay button into a container element you provide. This is the recommended default — it needs the least code, and the SDK starts the Apple Pay session on click and handles the payment for you.
> >
> > ```js JavaScript theme={null}
> > razorpay.mount({
> >   method: 'card',
> >   app: { name: 'apple_pay' },
> >   container: document.getElementById('apple-pay-container'),
> >   buttonLabel: 'pay',
> >   buttonTheme: 'dark',
> >   buttonWidth: '148px',
> >   buttonHeight: '32px',
> > });
> > ```
> >
> > `mount()` creates the button, appends it to the container and wires up the click to payment lifecycle for you. The result still comes via the `payment.success` / `payment.failure` events from Step 3.
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > Call `canMakePayment()` before `mount()` if you want to avoid mounting a button the customer cannot actually use (for example, hide the container on `available: false`).
>
> > [tab] Option 2: Your Own Button + createPayment()
> >
> > Use this option only if you need full control over the button's markup and rendering. Use `canMakePayment()` to check eligibility, then call `createPayment()` inside your button's click handler.
> >
> > ```js JavaScript theme={null}
> > const { available, reason } = await razorpay.canMakePayment({
> >   method: 'card',
> >   app: { name: 'apple_pay' },
> > });
> >
> > if (!available) {
> >   // hide your Apple Pay button, show alternatives
> > } else {
> >   // show your button
> > }
> >
> > myButton.addEventListener('click', () => {
> >   razorpay.createPayment({
> >     method: 'card',
> >     app: { name: 'apple_pay' },
> >   });
> > });
> > ```
> >
> > > [!NOTE]
> > >
> > > **Handy Tip**
> > >
> > > `createPayment()` is fire-and-forget — the outcome always comes through the `payment.success` / `payment.failure` events registered in Step 3.

> [accordion] Step 6: Verify the Payment Signature on Your Server
>
> After a successful payment (the `payment.success` event fires), verify the payment signature on your server before fulfilling the order.
>
> Send the following fields to your backend:
>
> * `razorpay_payment_id`
> * `razorpay_order_id`
> * `razorpay_signature`
>
> Verify them using the standard [Razorpay signature verification process](https://razorpay.com/docs/sg/payments/server-integration/python/integration-steps.md#4-verify-payment-signature).
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Never fulfil an order based solely on the client-side `payment.success` event. Signature verification ensures the payment was genuinely processed by Razorpay and has not been tampered with.

## Error Handling Reference

Every failure — from `payment.failure` events or a caught exception — carries the same shape:

```js JavaScript theme={null}
{
  code: 'PAYMENT_CANCELLED' | 'PAYMENT_FAILED' | 'INTERNAL_ERROR',
  description: string,  // safe to show to the customer
  source: 'customer' | 'merchant' | 'bank' | 'internal',
  reason: string,        // machine-readable, for logging
}
```

| Code | Meaning | Suggested Handling |
| - | - | - |
| `PAYMENT_CANCELLED` | Customer closed the sheet, or you called `abort()` | Return to the product/cart page |
| `PAYMENT_FAILED` | Payment was attempted but declined/failed | Show description, offer retry or another method |
| `INTERNAL_ERROR` | Something went wrong on our end (network, script load, etc.) | Show a generic "try again later" message |

## Quick Checklist

* Load `https://checkout.razorpay.com/v1/razorpay.js`
* Initialise `new Razorpay({ amount, currency, ... })`
* Implement order creation inside `on_payment_initiate_create_order`
* Wire up `payment.success` / `payment.failure` handling
* Test `canMakePayment()` handling for devices/browsers where Apple Pay is not available
* Verify the payment signature on your server before fulfilling the order

### Related Information

* [Web Component Integration](https://razorpay.com/docs/sg/payments/payment-methods/apple-pay/custom-integration/web-sdk/web-component.md)
* [Apple Pay Standard Checkout](https://razorpay.com/docs/sg/payments/payment-methods/apple-pay.md)
