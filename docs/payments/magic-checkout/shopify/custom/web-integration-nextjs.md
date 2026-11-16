> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integrate Magic Checkout on Headless - Shopify Website

> Steps to integrate Magic Checkout on your headless Shopify website using a custom React (Next.JS) frontend.

Available in
🇮🇳 India

Follow these steps to integrate the Razorpay Magic Checkout on your React (Next.JS) Website when using Shopify as your e-commerce platform. This integration treats the platform as Shopify while using a custom frontend, allowing unified order management in Shopify admin.

## Prerequisites

* Ensure you enable [Magic Checkout](https://razorpay.com/docs/payments/magic-checkout/troubleshooting-faqs.md#how-do-i-check-if-magic-checkout-is-enabled-on-my-account) on your account.
* Integrate [Magic Checkout With Shopify Store](https://razorpay.com/docs/payments/magic-checkout/shopify.md).
* Generate [Live API Keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md) from the Dashboard.

> [!WARNING]
>
> **Watch Out!**
>
> Before you start this integration, the Razorpay Integration Team must connect your Shopify store with your Razorpay MID by creating the Magic app on the store and linking it to the MID. You can access the APIs only after the store is connected and authorisation is complete. Until then, API requests return an `Authorization Failed` error.

> [card] [1. Build Integration](https://razorpay.com/docs/payments/magic-checkout/shopify/custom/web-integration-nextjs.md#1-build-integration)
>
> Integrate with React (Next.JS) Website for Shopify.

> [card] [2. Test Integration](https://razorpay.com/docs/payments/magic-checkout/shopify/custom/web-integration-nextjs.md#2-test-integration)
>
> Test the integration by making a test payment.

## 1. Build Integration

Follow the steps given below:

> [accordion] 1 Create a Checkout id
>
> Generate a unique cart identifier to initiate the Magic Checkout process.
>
> > [!NOTE]
> >
> > **Important**
> >
> > Ensure you create the Shopify cart before making this request as the cart token must be included in the payload.
>
> `POST /magic/checkout/shopify?key_id=rzp_live_XXXXXX`
>
> ```bash Request theme={null}
> curl -X POST https://api.razorpay.com/v1/magic/checkout/shopify?key_id=rzp_live_XXXXXX \
>   -H "Content-Type: application/json" \
>   -H "Accept: application/json" \
>   -d '{
>     "cart": {
>       "token": "ashgad?key=abasab",
>       "note": null,
>       "attributes": {},
>       "item_count": 1,
>       "items": [
>         {
>           "id": 100000000001,
>           "quantity": 1,
>           "product_id": 832938123321,
>           "variant_id": 100000000001,
>           "properties": {}
>         }
>       ]
>     }
>   }'
> ```
>
> ```json Response theme={null}
> {
>   "shopify_checkout_id": "gid://shopify/Cart/ashgad?key=abasab",
>   "tax_details": {
>     "total_tax": 0,
>     "taxes_included": true
>   }
> }
> ```
>
> > [accordion] Request Parameters
> >
> > `cart` *mandatory*
> > : `object` Complete cart object from Shopify.
> >
> > `cart.token` *mandatory*
> > : `string` Unique cart token from Shopify cart creation.
> >
> > `cart.note` *optional*
> > : `string|null` Customer notes or special instructions.
> >
> > `cart.attributes` *optional*
> > : `object` Custom attributes for the cart (key-value pairs).
> >
> > `cart.item_count` *mandatory*
> > : `integer` Total number of items in the cart.
> >
> > `cart.items` *mandatory*
> > : `array` Array of cart items.
> >
> > `cart.items[].id` *mandatory*
> > : `integer` Unique item identifier.
> >
> > `cart.items[].quantity` *mandatory*
> > : `integer` Quantity of the item.
> >
> > `cart.items[].product_id` *mandatory*
> > : `integer` Shopify product identifier.
> >
> > `cart.items[].variant_id` *mandatory*
> > : `integer` Shopify variant identifier.
> >
> > `cart.items[].properties` *optional*
> > : `object` Custom item properties.
>
> > [accordion] Response Parameters
> >
> > `shopify_checkout_id`
> > : `string` Unique checkout identifier for Shopify integration.
> >
> > `tax_details`
> > : `object` Tax information for the checkout.
> >
> > `total_tax`
> > : `integer` Total tax amount in smallest currency unit (paise).
> >
> > `taxes_included`
> > : `boolean` Whether taxes are included in item prices. Possible values:
> >
> > * `true`: Taxes are included in item prices.
> > * `false`: Taxes are separate from item prices.

> [accordion] 2 Create Order id on Server
>
> Create a Razorpay order id required for the payment modal. This API requires the `shopify_checkout_id` from [Step 1.1](#1-create-a-checkout-id).
>
> `POST /magic/order/shopify?key_id=rzp_live_XXXXXX`
>
> ```bash Request theme={null}
> curl -X POST https://api.razorpay.com/v1/magic/order/shopify?key_id=rzp_live_XXXXXX \
>   -H "Content-Type: application/json" \
>   -H "Accept: */*" \
>   -H "Origin: https://api.razorpay.com" \
>   -d '{
>     "shopify_checkout_id": "gid://shopify/Cart/ashgad?key=abasab",
>     "ga_id": "GA1.1.xxxxxxx.xxxxxxxx",
>     "fb_analytics": {
>       "external_id": "unique_fb_external_id",
>       "fbp": "fb.1.xxxxxxx.xxxxxxxx",
>       "fbc": "",
>       "event_source_url": "https://your-store.com/"
>     },
>     "utm_parameters": {
>       "landing_page_url": "https://your-store.com/",
>       "user_agent": "Mozilla/5.0 (Linux; Android 12; SM-G991B)...",
>       "utm_campaign": "feeding_bottle_sp",
>       "utm_content": "ct", 
>       "utm_medium": "product_sync",
>       "utm_source": "google"
>     },
>     "analytics": {
>       "fb_analytics": {
>         "external_id": "unique_fb_external_id",
>         "fbp": "fb.1.xxxxxxx.xxxxxxxx",
>         "fbc": ""
>       },
>       "ga4": {
>         "session_ids": {
>           "_ga_XXXXXXXXXX": "GS1.1.xxxxxxxx.x.x.x.x.x"
>         },
>         "client_id": "GA1.1.xxxxxxxx.xxxxxxxx"
>       },
>       "source_url": "https://your-store.com/"
>     }
>   }'
> ```
>
> ```json Response theme={null}
> {
>   "preferences": null,
>   "order_id": "order_EKwxwAgItmmXdp"
> }
> ```
>
> > [accordion] Request Parameters
> >
> > `shopify_checkout_id` *mandatory*
> > : `string` Checkout id from [Step 1.1](#1-create-a-checkout-id).
> >
> > `ga_id` *optional*
> > : `string` Google Analytics client identifier.
> >
> > `fb_analytics` *optional*
> > : `object` Facebook Analytics parameters.
> >
> > `external_id` *optional*
> > : `string` Unique external id for Facebook tracking.
> >
> > `fbp` *optional*
> > : `string` Facebook browser pixel id.
> >
> > `fbc` *optional*
> > : `string` Facebook click id.
> >
> > `event_source_url` *optional*
> > : `string` Source URL for the event.
> >
> > `utm_parameters` *optional*
> > : `object` UTM tracking parameters.
> >
> > `landing_page_url` *optional*
> > : `string` Landing page URL.
> >
> > `user_agent` *optional*
> > : `string` Browser user agent string.
> >
> > `analytics` *optional*
> > : `object` Comprehensive analytics data.
> >
> > `fb_analytics` *optional*
> > : `object` Facebook Analytics configuration.
> >
> > `external_id` *optional*
> > : `string` Unique external id for Facebook tracking.
> >
> > `fbp` *optional*
> > : `string` Facebook browser pixel id.
> >
> > `fbc` *optional*
> > : `string` Facebook click id.
> >
> > `ga4` *optional*
> > : `object` Google Analytics 4 configuration.
> >
> > `session_ids` *optional*
> > : `object` GA4 session identifiers.
> >
> > `client_id` *optional*
> > : `string` GA4 client identifier.
> >
> > `source_url` *optional*
> > : `string` Source URL for analytics.
>
> > [accordion] Response Parameters
> >
> > `preferences`
> > : `object|null` Customer preferences. Returns `null` if no preferences are set.
> >
> > `order_id`
> > : `string` Unique Razorpay order identifier. For example, `order_EKwxwAgItmmXdp`.

> [accordion] 3 Integrate Magic Checkout Web SDK
>
> After successfully creating the order id, integrate the Magic Checkout Web SDK to display the payment interface and handle the checkout process.
>
> > [accordion] 3.1 Load the Magic Checkout Script
> >
> > You can add the Razorpay Magic Checkout script to your Next.JS application in two ways:
> >
> > > [tab] Using next/script (Recommended)
> > >
> > > ```javascript JavaScript theme={null}
> > > // In your _app.js or specific page component
> > > import Script from 'next/script';
> > >
> > > export default function App({ Component, pageProps }) {
> > > return (
> > >     <>
> > >     <Script 
> > >         src="https://checkout.razorpay.com/v1/magic-checkout.js"
> > >         strategy="lazyOnload"
> > >     />
> > >     <Component {...pageProps} />
> > >     </>
> > > );
> > > }
> > > ```
> >
> > > [tab] Dynamic Loading in Component
> > >
> > > ```javascript JavaScript theme={null}
> > > // In your checkout component
> > > import { useEffect } from 'react';
> > >
> > > useEffect(() => {
> > > const script = document.createElement('script');
> > > script.src = 'https://checkout.razorpay.com/v1/magic-checkout.js';
> > > script.async = true;
> > > document.body.appendChild(script);
> > >
> > > return () => {
> > >     document.body.removeChild(script);
> > > };
> > > }, []);
> > > ```
>
> > [accordion] 3.2 Initialise and Open Magic Checkout
> >
> > Create a function to initialise Magic Checkout with the required configuration options and open the payment modal.
> >
> > ```javascript Checkout Options theme={null}
> > const openMagicCheckout = () => {
> >   const options = {
> >     key: 'rzp_live_XXXXXX', // Enter the Key id generated from the Dashboard
> >     name: 'Acme Corp', // Your business name
> >     order_id: 'order_EKwxwAgItmmXdp', // Order id from Step 2
> >     show_coupons: true, // default true; false if coupon widget should be hidden
> >     prefill: {
> >       name: 'Gaurav Kumar',
> >       email: 'gauravkumar@example.com',
> >       contact: '9000090000',
> >       coupon_code: 'MY_COUPON_20', // Coupon from your cart to auto-apply
> >     },
> >     handler: function (response) {
> >       // Handle successful payment
> >       // response.razorpay_payment_id
> >       // response.razorpay_order_id
> >       // response.razorpay_signature
> >
> >       // Call Complete Checkout API (Step 5)
> >       completeCheckout(response);
> >     },
> >     modal: {
> >       ondismiss: function () {
> >         // Handle checkout modal close
> >         console.log('Checkout modal closed');
> >       },
> >     },
> >   };
> >   const rzp = new window.Razorpay(options);
> >   rzp.open();
> > };
> > ```
> >
> > > [accordion] Checkout Options
> > >
> > > You must pass these parameters in Checkout to initiate the payment.
> > >
> > > `key` *mandatory*
> > > : `string` API Key id generated from the Razorpay Dashboard.
> > >
> > > `name` *mandatory*
> > > : `string` Your business name shown on the Checkout form. For example, **Your Store Name**.
> > >
> > > `order_id` *mandatory*
> > > : `string` Order id from [Step 1.2](#2-create-order-id-on-server).
> > >
> > > `show_coupons` *optional*
> > > : `boolean` Determines whether to show coupons to customer on checkout. Possible values:
> > >
> > > * `true` (default): Enables the Coupon feature.
> > > * `false`: Disables the Coupon feature.
> > >
> > > `prefill` *optional*
> > > : `object` You can prefill the following details at Checkout.
> > >
> > > `name` *optional*
> > > : `string` Customer's name to be prefilled. For example, **Customer Name**.
> > >
> > > `email` *optional*
> > > : `string` Customer's email address.
> > >
> > > `contact` *optional*
> > > : `string` Customer's phone number. The expected format is `+ {country code}{phone number}`. If country code is not specified, `91` will be used as default.
> > >
> > > `coupon_code` *optional*
> > > : `string` Coupon code from your cart to auto-apply during checkout.
> > >
> > > `handler` *mandatory*
> > > : `function` Function called on successful payment. Returns payment response with `razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature`.
> > >
> > > > [!WARNING]
> > > >
> > > > **Watch Out!**
> > > >
> > > > Ensure you handle the payment response in the `handler` function and call the Complete Checkout API to finalise the order in Shopify.
> > >
> > > > [!WARNING]
> > > >
> > > > **Watch Out!**
> > > >
> > > > To support theme colour in the progress bar, please pass HEX colour values only.

> [accordion] 4 Coupon Handling
>
> Since this is an SDK integration, Shopify coupons will not auto-apply like they do on the website. You must explicitly pass coupon codes to Magic Checkout. When initialising Magic Checkout, include the coupon code in the prefill options:
>
> ```javascript theme={null}
> const options = {
> key: 'rzp_live_XXXXXX',
> order_id: 'order_EKwxwAgItmmXdp',
> // ... other options
>
> prefill: {
>     coupon_code: 'MY_COUPON_NAME',  // Coupon from your cart to auto-apply
> },
> };
>
> // Initialise Magic Checkout with options
> MagicCheckout.open(options);
> ```
>
> Your app captures the coupon applied on the cart page, then passes the coupon code in the `prefill.coupon_code` field. The SDK internally calls `applyCoupon('MY_COUPON_NAME')` and if the coupon is valid, it is automatically applied in Magic Checkout.

> [accordion] 5 Complete Checkout Call
>
> After a successful payment, call the complete checkout API to create the order in Shopify. You must make the call from the callback handler implemented when importing the React SDK. Ensure you redirect the user to the `order_status_url` to show them the order success page on Shopify.
>
> `POST /1cc/shopify/complete?key_id=rzp_live_XXXXXX`
>
> ```bash Request theme={null}
> curl -X POST https://api.razorpay.com/v1/1cc/shopify/complete?key_id=rzp_live_XXXXXX \
>   -H "Content-Type: application/json" \
>   -H "Accept: application/json" \
>   -d '{
>     "razorpay_payment_id": "pay_Rk3b76fSqXXXXX",
>     "razorpay_order_id": "order_Rk3UmCXXW5XXXX"
>   }'
> ```
>
> ```json Response theme={null}
> {
>   "id": 65157213390123,
>   "order_id": "#32697",
>   "payment_id": "pay_Rk3b76fSqXXXXX",
>   "payment_method": "netbanking",
>   "payment_currency": "INR",
>   "total_amount": 659430,
>   "total_tax": "543.91",
>   "shipping_fee": 700,
>   "cod_fee": 0,
>   "promotions": [
>     {
>       "reference_id": "Auto Order Amount Discount",
>       "code": "Auto Order Amount Discount",
>       "type": "automatic",
>       "value": 100000,
>       "source": "shopify"
>     }
>   ],
>   "shipping_country": "in",
>   "customer_details": {
>     "email": "<email>",
>     "contact": "<phone>",
>     "shipping_address": {
>       "name": "<name>",
>       "line1": "123 Main Street",
>       "city": "Bengaluru",
>       "state": "KARNATAKA",
>       "zipcode": "560049",
>       "country": "in"
>     }
>   },
>   "order_status_url": "https://your-store.myshopify.com/orders/...",
>   "is_new_customer": false
> }
> ```
>
> > [accordion] Request Parameters
> >
> > `razorpay_payment_id` *mandatory*
> > : `string` Unique payment identifier. Format: `pay_` followed by 14 characters.
> >
> > `razorpay_order_id` *mandatory*
> > : `string` Unique order identifier from Step 1.2. Format: `order_` followed by 14 characters.
>
> > [accordion] Response Parameters
> >
> > `id`
> > : `integer` Unique Shopify order identifier. For example, `65157213390123`.
> >
> > `order_id`
> > : `string` Human-readable order number. For example, `#32697`.
> >
> > `payment_id`
> > : `string` Razorpay payment identifier. For example, `pay_Rk3b76fSqXXXXX`.
> >
> > `payment_method`
> > : `string` Payment method used. Possible values include:
> >
> > * `netbanking`
> > * `upi`
> > * `card`
> > * `wallet`
> >
> > `payment_currency`
> > : `string` The 3-letter ISO currency code. For example, `INR`.
> >
> > `total_amount`
> > : `integer` Total order amount in smallest currency unit (paise). For example, `659430` for ₹6594.30.
> >
> > `total_tax`
> > : `string` Total tax amount as string. For example, `543.91`.
> >
> > `shipping_fee`
> > : `integer` Shipping charges in smallest currency unit (paise). For example, `700` for ₹7.
> >
> > `cod_fee`
> > : `integer` Cash on Delivery fee in smallest currency unit (paise). For example, `0` indicates no COD fee.
> >
> > `promotions`
> > : `array` Array of applied promotions/discounts.
> >
> > `reference_id`
> > : `string` Internal reference for the promotion.
> >
> > `code`
> > : `string` Promotion code used.
> >
> > `type`
> > : `string` Type of promotion. Possible values:
> >
> > * `automatic`: Automatically applied discount.
> > * `coupon`: Coupon-based discount.
> >
> > `value`
> > : `integer` Discount value in smallest currency unit (paise). For example, `100000` for ₹1000.
> >
> > `source`
> > : `string` Source of the promotion. For example, `shopify`.
> >
> > `shipping_country`
> > : `string` Country code for shipping destination. For example, `in`.
> >
> > `customer_details`
> > : `object` Complete customer information.
> >
> > `email`
> > : `string` Customer's email address.
> >
> > `contact`
> > : `string` Customer's phone number.
> >
> > `shipping_address`
> > : `object` Complete shipping address information.
> >
> > `name`
> > : `string` Recipient name.
> >
> > `line1`
> > : `string` Address line 1.
> >
> > `city`
> > : `string` City name.
> >
> > `state`
> > : `string` State name.
> >
> > `zipcode`
> > : `string` Postal code.
> >
> > `country`
> > : `string` Country code. For example, `in`.
> >
> > `order_status_url`
> > : `string` Shopify order status page URL for customer.
> >
> > `is_new_customer`
> > : `boolean` Whether this is a new customer's first order. Possible values:
> >
> > * `true`: New customer's first order.
> > * `false`: Existing customer order.

#### Pass Additional Attributes to Shopify Orders

Shopify orders support Tags and Additional Attributes (note attributes). Include the attributes in the Shopify cart's attributes object before initiating checkout:

```javascript theme={null}
// When creating/updating Shopify cart
const cartPayload = {
  cart: {
    token: "your_cart_token",
    note: "Customer special instructions",
    attributes: {
      "Source": "Mobile App",
      "App Version": "2.1.0",
      "Campaign": "Summer Sale 2025",
      "Custom Field": "Your custom value"
    },
    item_count: 1,
    items: [/* ... */]
  },
  key: "rzp_live_XXXXXX"
};
```

These attributes will flow through to the Shopify order and appear in the additional attributes section in Shopify Admin.

## 2. Test Integration

Check the following checklist below:

* Shopify cart creation is working correctly.
* Checkout id is generated successfully.
* Order id is created with analytics parameters.
* Magic Checkout SDK opens without errors.
* Coupons apply correctly via prefill.
* Payment flow completes successfully.
* Complete Checkout API creates order in Shopify.
* Order appears in Shopify Admin with correct details.
* Additional attributes appear correctly in Shopify order.

## Error Handling

| Error Scenario | Recommended Action |
| - | - |
| Invalid cart token | Ensure Shopify cart exists before [Step 1.1](#1-create-a-checkout-id). |
| Payment not captured | Verify payment status before complete checkout. |
| Invalid signature | Regenerate signature using Razorpay's signature verification. |
| Coupon invalid | Handle error callback and notify user. |

> [!WARNING]
>
> **Fallback to Shopify Checkout**
>
> If any Magic Checkout API fails, redirect users to the standard Shopify checkout to ensure customers can still complete their purchase.

## Support

For integration support, reach out to your Razorpay account manager or raise a request with our [support team](https://razorpay.com/support/#request).
