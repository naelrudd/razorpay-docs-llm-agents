> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Embedded Quick Buy

> Show a customer's recommended payment instrument directly on your cart or product page and let them pay in one tap with Embedded Quick Buy.

Available in
🇮🇳 India

Embedded Quick Buy is an extension of [QuickBuy](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy.md) that brings a customer's recommended payment instrument onto your own pages. Instead of a generic **Pay Now** button that opens Razorpay Checkout, you show the instrument the customer is most likely to pay with, such as a saved card or a UPI app, on your cart, product or order summary page. The customer taps it and pays.

Razorpay's payment instrument ranking model picks the instrument. You design and place the button.

## How It Differs From QuickBuy on Standard Checkout

| | QuickBuy on Standard Checkout | Embedded Quick Buy |
| - | - | - |
| Where it appears | Inside the Razorpay Checkout modal. | Directly on your page, such as the cart, product page or order summary. |
| What the customer sees first | A generic **Pay Now** button on your page. | The recommended instrument, for example **HDFC Debit ••••4242** or **Google Pay**. |
| Integration effort | None. It is enabled by default for eligible customers. | Integrate the lightweight Razorpay Custom SDK and build the button UI. |
| Control over UI | Razorpay Checkout styling. | Full control over the button's design and placement. |

### See the Difference

<video controls muted playsInline preload="metadata" aria-label="QuickBuy on Standard Checkout: the customer taps a generic Pay button, the Razorpay Checkout sheet opens with PhonePe pre-selected and the customer taps Pay.">
  <source src="https://mintcdn.com/razorpay-881012b3/tXyKSJTlOhQL9SK9/static/docs-home/assets/quickbuy-standard-checkout-demo.mp4?fit=max&auto=format&n=tXyKSJTlOhQL9SK9&q=85&s=1f33dd5d722f314612fb385dc17f654f" type="video/mp4" />
</video>

**QuickBuy on Standard Checkout**\
The customer taps a generic **Pay** button. Razorpay Checkout opens with the recommended instrument pre-selected.

<video controls muted playsInline preload="metadata" aria-label="Embedded Quick Buy: the merchant's cart page shows Paying via PhonePe next to a Place Order button, and the customer pays without opening the full checkout.">
  <source src="https://mintcdn.com/razorpay-881012b3/tXyKSJTlOhQL9SK9/static/docs-home/assets/quickbuy-embedded-demo.mp4?fit=max&auto=format&n=tXyKSJTlOhQL9SK9&q=85&s=314122f5ddad95b7da48c31c032d63e0" type="video/mp4" />
</video>

**Embedded Quick Buy**\
The recommended instrument, here PhonePe, appears on the merchant's own cart page. The customer taps **Place Order** to pay.

## Advantages

> [tab] Businesses
>
> * **Higher conversion**: Customers see their preferred instrument upfront and pay in fewer steps.
> * **Recommendations for new customers**: Razorpay recognises customers from across its network, so you get a recommendation even for a customer who has never paid on your site or app.
> * **No PCI-DSS overhead**: Saved cards reach you as Razorpay tokens. You never store card data.
> * **Ready-made assets**: The response includes CDN-hosted logos for UPI apps, card networks and issuing banks.
> * **No changes to your existing checkout**: Your current checkout stays as the fallback. Orders, signature verification, webhooks and settlements work as they do today.

> [tab] Customers
>
> * **One-tap payment**: Pay with the preferred instrument without opening the full checkout.
> * **Clear details**: See the card's last four digits, network and issuer, or the UPI app, before paying.
> * **Freedom to switch**: Choose **Change payment method** to open the full checkout at any time.

## How It Works

1. **Create a customer**: Create a customer with the [Customers API](https://razorpay.com/docs/api/customers/create.md) when you capture their details, for example at sign-up.
2. **Fetch recommended instruments**: Call `getRecommendedInstruments()` from the Razorpay Custom SDK with the `customer_id` or the customer's contact number. Razorpay returns up to 3 instruments ranked by how likely the customer is to complete the payment, along with logos to display.
3. **Render your button**: Show the top instrument (`items[0]`) as a Quick Buy button on your page. Add a **Change payment method** option beside it.
4. **Create an order and pay**: When the customer taps the button, create an order on your server and submit the payment with the recommended instrument.
5. **Verify the payment**: Verify the payment signature on your server and confirm the payment status, as in any Razorpay integration.

If the customer taps **Change payment method**, or no instrument is returned, open your existing Razorpay Checkout.

> [!NOTE]
>
> **Handy Tips**
>
> * Recommended instruments can be saved cards or UPI apps.
> * On native SDKs, Razorpay checks which UPI apps are installed on the device and returns only those. On mobile web, the browser cannot check this, so all returned UPI apps are shown.
> * If you do not pass an `order_id`, the response is limited to UPI intent apps.

## Who Can Integrate

Businesses on Razorpay Standard Checkout, Custom Checkout and S2S integrations can use Embedded Quick Buy. In each case, you add the Razorpay Custom SDK to power the Quick Buy button. If you already use Custom Checkout, the only new step is fetching recommended instruments.

## Integration Guides

Choose your platform:

> [card] [Mobile Web](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/mobile-web.md)
>
> Integrate with `razorpay.js` on your mobile website.

> [card] [Android](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/android.md)
>
> Integrate with the Android Custom UI SDK.

> [card] [iOS](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/ios.md)
>
> Integrate with the iOS Custom UI SDK.

> [card] [React Native](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/react-native.md)
>
> Integrate with the React Native Custom UI SDK.

> [card] [Flutter](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/flutter.md)
>
> Integrate with the Flutter Custom UI SDK.

> [card] [FAQs](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/faqs.md)
>
> Common questions about Embedded Quick Buy.
