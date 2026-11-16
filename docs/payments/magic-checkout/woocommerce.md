> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integrate Magic Checkout With WooCommerce Website

> Steps to integrate Magic Checkout on your WooCommerce Website.

Available in
🇮🇳 India

> [card] [WooCommerce Integration Changelog](https://razorpay.com/docs/payments/changelog.md#products)
>
> Discover new features, updates and deprecations related to the WooCommerce Integration with Magic Checkout (since Jan 2024).

> [card] [Troubleshooting & FAQs](https://razorpay.com/docs/payments/magic-checkout/troubleshooting-faqs.md)
>
> Troubleshoot common error scenarios and find answers to frequently asked questions about WooCommerce Integration.

Follow the steps given below to integrate Razorpay Magic Checkout with your WooCommerce Website.

> [!NOTE]
>
> **Feature Request**
>
> This is an on-demand feature. Please raise a request with our [Support team](https://razorpay.com/support/#request) to get this feature activated on your Razorpay account.

> [!WARNING]
>
> **Watch Out!**
>
> If you are integrating with our plugin for the first time, refer to the [FAQs](https://razorpay.com/docs/payments/magic-checkout/troubleshooting-faqs.md#woocommerce).

## Integration Steps

Follow the steps given below:

> [accordion] Enable Features on Razorpay Dashboard
>
> To configure settings on Razorpay Dashboard:
>
> 1. Log in to the [WordPress account](https://wordpress.com/log-in) and navigate to **Settings** → **General**.
> 2. Copy the **WordPress Address** or **Site Address**.
>
>    ![Copy the checkout URL](https://razorpay.com/docs/build/browser/assets/images/magic-checkout-url.jpg)
> 3. Log in to the Razorpay Dashboard and navigate to **Magic Checkout**.
> 4. Select **WooCommerce** from the drop-down list. Paste the **WordPress Address** or **Site Address** in the **Domain hyperlink** field.
>
>    ![Enter WooCommerce domain hyperlink on Magic Checkout Settings](https://razorpay.com/docs/build/browser/assets/images/magic-checkout-settings-domain-hyperlink.jpg)

> [accordion] Enable Features on WordPress Dashboard
>
> To configure settings on WordPress Dashboard:
>
> 1. Log in to your **WordPress account** and activate the **Razorpay plugin** in the WordPress Plugin Manager.
> 2. Log in to your **WooCommerce account**, navigate to **Settings** and click the **Payments** tab.
> 3. In the **Payments** tab, scroll down to **Razorpay** and click **Manage** to edit the settings.
>
>    ![Edit the settings on the WooCommerce Dashboard](https://razorpay.com/docs/build/browser/assets/images/magic-razorpay-edit.jpg)
>
>    * **Activate Magic Checkout**: Enable Magic Checkout to start displaying Magic Checkout instead of Native Checkout. Disable it to use Native Checkout.
>
>      ![Enable Magic Checkout](https://razorpay.com/docs/build/browser/assets/images/magic-checkout-other-settings.jpg)
>
>      * **Activate Test Mode**: Enable Test mode to test the flow without impacting customers. This will show the button only to users who have admin permissions.
>
>      * **Activate Buy Now Button**: Display the Buy Now button on the product display page. Customers can directly purchase a single product by clicking the **Buy Now** button on the product display page and they will be directed to the Checkout for the payment. Only the Add to Cart button will appear to the customers if this is not selected.
>
>        ![Activate the Buy Now button](https://razorpay.com/docs/build/browser/assets/images/magic-checkout-buy-now.jpg)
>
>      * **Activate Mini Cart Checkout**: Display the Mini Cart Checkout button. Once a customer adds a product to the cart, they can hover over the cart and proceed to the Checkout section by clicking the **Checkout** button.
>
>        ![Activate the Mini Cart Checkout](https://razorpay.com/docs/build/browser/assets/images/magic-checkout-mini-cart.jpg)
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > * Before accepting live payments, test the Buy Now, Mini Cart, and Checkout buttons to ensure the integration works as expected.
> >   In case of any queries, contact our [support team](https://razorpay.com/support/).
> > * Webhooks are auto-configured when you enter and save the API key ID and secret on the plugin settings page. You need to verify if webhooks are enabled on your [Razorpay Dashboard](https://razorpay.com/docs/payments/magic-checkout/troubleshooting-faqs.md#how-can-i-verify-if-webhooks-are-enabled). However, for versions lower than 3.5.0, you need to [configure webhooks manually](https://razorpay.com/docs/payments/magic-checkout/troubleshooting-faqs.md#my-webhooks-are-not-auto-configured-since-i-am-not-using-the-upgraded-version-of-woocommerce-how-do-i-manually-configure-webhooks).

> [accordion] Accept Live Payments
>
> Disable the Test mode enabled in [Step 2](https://razorpay.com/docs/payments/magic-checkout/woocommerce.md#enable-features-on-wordpress-dashboard:~:text=use%20Native%20Checkout.-,Activate%20Test%20Mode,-%3A%20Enable%20Test%20mode) and click **Save Settings** to accept live payments.
>
> ![Disable the test mode enabled previously](https://razorpay.com/docs/build/browser/assets/images/magic-checkout-test-disable.jpg)

> [!NOTE]
>
> **Handy Tips**
>
> To disable Magic Checkout, refer to our [FAQs](https://razorpay.com/docs/payments/magic-checkout/troubleshooting-faqs.md#can-i-disable-magic-checkout).

## Next Steps

## Next Steps

After successfully integrating your WooCommerce website with Magic Checkout, you can perform the following configurations on the Razorpay Dashboard to suit your business needs:

* [Cash on Delivery](https://razorpay.com/docs/payments/magic-checkout/woocommerce/features.md#cash-on-delivery): Enable COD and configure rules for specific locations, products, and order amounts, catering to customer preferences and logistical needs to increase sales.
* [RTO](https://razorpay.com/docs/payments/magic-checkout/woocommerce/features.md#rto): Use automated COD intelligence or manual review to decide whether to offer COD based on customer buying history, thus reducing RTO rates.
* [Convert COD Orders to Prepaid](https://razorpay.com/docs/payments/magic-checkout/woocommerce/features.md#convert-cod-orders-to-prepaid): Encourage COD customers to switch to prepaid by offering discounts or incentives, reducing cash handling risks.
* [Shipping Options](https://razorpay.com/docs/payments/magic-checkout/woocommerce/features.md#shipping-options): Set up shipping rates at the product, zone and method levels to optimise costs and improve delivery efficiency.
* [International Shipping](https://razorpay.com/docs/payments/magic-checkout/woocommerce/features.md#international-shipping): Allow customers to enter international PIN codes, expanding your market reach globally.
* [Coupons](https://razorpay.com/docs/payments/magic-checkout/woocommerce/features.md#coupons): Provide discounts via coupons to enhance engagement and reduce cart abandonment.
* [Google and Facebook Analytics](https://razorpay.com/docs/payments/magic-checkout/woocommerce/features.md#google-and-facebook-analytics): Integrate Google and Facebook Analytics for insights into customer behaviour and optimised marketing strategies.

### Related Information

[Troubleshooting and FAQs](https://razorpay.com/docs/payments/magic-checkout/troubleshooting-faqs.md#woocommerce)
