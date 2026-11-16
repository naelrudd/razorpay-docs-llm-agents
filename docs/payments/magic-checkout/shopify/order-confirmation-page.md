> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Order Confirmation

> Razorpay-hosted order confirmation (thank you) page shown to buyers on the Shopify Basic plan after every successful Magic Checkout order.

Available in
🇮🇳 India

If your store is on the Shopify **Basic** plan, your buyers now land on a Razorpay-hosted order confirmation (thank you) page after every successful order, instead of Shopify's native order status page. This page is on by default and needs no setup or configuration from your end.

## What Changed

| Earlier | Now |
| - | - |
| <ul><li>After a successful payment, Magic Checkout redirected the buyer to Shopify's native order status page.</li><li>For each order, Shopify generated a unique, authenticated confirmation URL.</li><li>Magic Checkout used this URL to send the buyer to that page.</li></ul> | <ul><li>Shopify now classifies this confirmation URL as protected customer data and blocks access to it for stores on the Basic plan.</li><li>The URL is created fresh for every order and cannot be recreated, so Magic Checkout can no longer redirect buyers to Shopify's order status page.</li><li>Instead, Magic Checkout builds and shows its own order confirmation page right after payment, so your buyers still get a clear confirmation.</li></ul> |

## What the Page Shows the Buyer

* **Personalised order confirmation header** containing a greeting with your customer's name.
* **Full order summary** with your Shopify order number, listing every item ordered, along with quantities, unit prices and the order total.
* **Shipping and payment methods** used for the order.
* **Shipping address and contact details** exactly as the buyer entered them at checkout, so they can verify the details.
* **Your store's brand logo**, pulled from your Magic Checkout Dashboard configuration.
* A **Continue Shopping** button to return to your store.
* A **Contact Us** link to reach out for help with the order.

The page uses a mobile responsive layout, since most Magic Checkout buyers shop on mobile.

![razorpay-hosted order confirmation thank you page for shopify magic checkout on the basic plan](https://razorpay.com/docs/build/browser/assets/images/magic-shopify-thank-you-page.jpg)

For any queries, write to us at [magic-checkout-support@razorpay.com](mailto:magic-checkout-support@razorpay.com).

## Frequently Asked Questions

> [accordion] Why do my buyers now see a Razorpay-hosted confirmation page?
>
> Earlier, Shopify hosted its own native order status page, and after a buyer paid, Magic Checkout redirected them to it using the Order status page URL that Shopify provided. Shopify now classifies the URL as protected customer data and restricts access to it for stores on the Basic plan. As Shopify moves all apps to its new API standard, the URL can no longer be accessed for stores on the Basic plan. To make sure your buyers still see a clear confirmation after they pay, Magic Checkout now renders its own order confirmation page automatically.

> [accordion] Which stores are affected by this change?
>
> This change is specific to stores on the Shopify **Basic** plan. Stores on higher Shopify plans are not affected and can continue to use the legacy order status page method.

> [accordion] I am not on the Shopify Basic plan. Does this change affect me?
>
> No. Stores on higher Shopify plans are not affected and can continue to use Shopify's native order status page. To compare plans or upgrade, see [Shopify Pricing](https://www.shopify.com/pricing).

> [accordion] Do I need to enable or configure this page?
>
> No. The page is on by default for all affected Basic plan stores and needs no setup, dashboard toggle, or configuration from your end. Your brand logo is pulled automatically from your [Magic Checkout Dashboard](https://razorpay.com/docs/payments/magic-checkout/shopify/features) configuration.

> [accordion] Will my third-party Shopify apps still work on this page?
>
> Third-party Shopify apps that display on the native order status page, such as review request, loyalty point, or post-purchase upsell apps, do not carry over to the Razorpay-hosted page, as they rely on Shopify's native thank you page. If these integrations are critical for your store, consider upgrading your Shopify plan. To compare plans, see [Shopify Pricing](https://www.shopify.com/pricing).

> [accordion] Can I switch back to Shopify's native order status page?
>
> On the Basic plan, Shopify enforces this restriction and it cannot be changed at the app level. If the native order status page or its third-party app integrations are critical for your store, consider upgrading your Shopify plan. For any queries, write to us at [magic-checkout-support@razorpay.com](mailto:magic-checkout-support@razorpay.com).
