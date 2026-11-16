> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Cash on Delivery

> Offer Cash on Delivery (COD) as a payment method on the Razorpay Checkout page.

Available in
🇮🇳 India

You can now offer Cash on Delivery (COD) as a payment method on the Razorpay Checkout page. Customers can choose COD directly on the Checkout page, alongside UPI, cards, netbanking and more. This flow increases accessibility and builds trust among first-time buyers and high-value orders.

## Ways to Offer COD

| **Checkout product** | **How COD works** | **Guide** |
| - | - | - |
| **Standard Checkout** | COD appears as a payment method in Standard Checkout. You set the convenience fee per order using `cod_fee`, control where COD appears, and receive a `payment.pending` webhook when an order is placed. COD must be activated on your account. | [COD on Standard Checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/cod.md) |
| **Magic Checkout** | COD is supported by default. The checkout flow includes an address section, which you can hide using `show_address`. | This page |

> [!NOTE]
>
> **Handy Tips**
>
> [Razorpay Magic Checkout](https://razorpay.com/docs/payments/magic-checkout) supports Cash on Delivery (COD) by default. For a simplified experience without the address section, use the flow described below that directly opens the payment page. Both flows support COD as a payment method.

## COD on Magic Checkout

The rest of this page describes COD on Magic Checkout. If you use Standard Checkout, see [COD on Standard Checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/cod.md) instead.

## Prerequisites

* [Create a Razorpay account](https://dashboard.razorpay.com/).
* Generate [API Keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys) from the Dashboard. To go live with the integration and start accepting real payments, generate Live Mode API Keys and replace them in the integration.
* Integrate with Razorpay Magic Checkout:
  * [Native (Web)](https://razorpay.com/docs/payments/magic-checkout/web.md)
  * [Android](https://razorpay.com/docs/payments/magic-checkout/android-integration.md)
  * [iOS](https://razorpay.com/docs/payments/magic-checkout/ios-integration.md)
  * [React Native: Android](https://razorpay.com/docs/payments/magic-checkout/react-native-android-integration.md)
  * [React Native: iOS](https://razorpay.com/docs/payments/magic-checkout/react-native-ios-integration.md)
  * [Flutter](https://razorpay.com/docs/payments/magic-checkout/flutter-integration.md)
  * [Capacitor](https://razorpay.com/docs/payments/magic-checkout/capacitor-integration.md)

> [!WARNING]
>
> **Watch Out!**
>
> This feature is currently supported only for native Razorpay integrations. It is not available on third-party platforms such as Shopify, WooCommerce and so on.

## Integration Steps

Follow the integration steps given below:

1. Use your existing Magic Checkout integration. While configuring the checkout options, pass the `show_address` parameter as shown below to control the visibility of the address section:

```javascript json theme={null}
"options": {
    "show_address": false
    }
```

`show_address`
: `boolean` Determines whether the shipping address section appears on the Checkout page. Possible values

* `true` (default): Show the address form.
* `false`: Hide the address form.

> [!NOTE]
>
> **Handy Tips**
>
> Magic Checkout supports **Cash on Delivery (COD)** by default and the checkout flow includes an address section. Use the `show_address` parameter to remove this step and maintain a simplified checkout experience.

2. **Cash on Delivery** appears as one of the available payment methods on the Checkout interface. Customers can select COD and confirm the order.

## Customer Experience

The flow below displays how customers can view and select **Cash on Delivery** during Checkout:

![COD on checkout - customer experience](https://razorpay.com/docs/build/browser/assets/images/payment-methods-cod.gif)

### Related Information

* [COD on Standard Checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/cod.md)
* [Payment Configuration](https://razorpay.com/docs/payments/dashboard/account-settings/payment-configuration.md#configure-payment-options)
