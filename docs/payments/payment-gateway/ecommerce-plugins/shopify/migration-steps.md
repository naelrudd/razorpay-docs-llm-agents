> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Migration Steps for Existing Users

> Follow the step-by-step guide on migrating from the existing Razorpay App to Razorpay Secure on your Shopify store.

Available in
🇮🇳 India

If you are using Razorpay to accept payments, you can now upgrade to the **Razorpay Secure** app on your Shopify store. Watch the [video tutorial](#video-tutorial) or follow the [migration steps](#migration-steps) to migrate to Razorpay Secure. Know more about why you need to [upgrade to Razorpay Secure](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/faqs.md#why-do-i-need-to-upgrade-to-razorpay-secure).

## Video Tutorial

Watch this video to know how to migrate from the existing Razorpay App to Razorpay Secure on your Shopify store.

[How to migrate from existing Razorpay App to Razorpay Secure App on Shopify Store](https://www.youtube.com/embed/3mUfBE9WkCo)

## Migration Steps

Follow the steps given below to migrate from the existing Razorpay App to Razorpay Secure.

> [accordion] Migration
>
> 1. Click on [this link](https://accounts.shopify.com/store-login?redirect=settings%2Fpayments%2Falternative-providers%2F1058839) to access the **01 Cards, UPI, NB, Wallets by Razorpay** app on your Shopify store.
>
> 2. Click **Install**.
>
>    ![Shopify Install](https://razorpay.com/docs/build/browser/assets/images/shopify-1-razorpay-install-new.jpg)
>
> 3. You will be redirected to a landing page. Click **I am an existing user**.
>
>    ![Existing Merchant Shopify](https://razorpay.com/docs/build/browser/assets/images/shopify-existing-merchant.jpg)
>
> 4. Scroll down and click **Login**.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Make sure you log in with **owner** credentials to connect Razorpay with Shopify successfully.
>
> ![Shopify login](https://razorpay.com/docs/build/browser/assets/images/shopify-login-v2.gif)
>
> 5. Click **Activate** on the activation screen on your Shopify Dashboard. \\
>
>    ![Shopify Activate](https://razorpay.com/docs/build/browser/assets/images/shopify-1razorpay-activate.jpg)
>
> **Razorpay Secure (UPI, Card, Int'l Card, Apple Pay)** now appears as a Payment Gateway on your Shopify Store checkout.\\
>
> ![Shopify Checkout](https://razorpay.com/docs/build/browser/assets/images/shopify-v2-checkout.jpg)
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Ensure you deactivate the existing Razorpay App after activating the new **Razorpay Secure** App.

> [accordion] Deactivation
>
> To deactivate the existing Razorpay App:
>
> 1. Click on [this link](https://accounts.shopify.com/store-login?redirect=settings/payments/alternative-providers/1030400) to access the existing Razorpay App on your Shopify store.
> 2. Click **Deactivate Razorpay** to deactivate the existing Razorpay App on your Shopify store.
>
>    ![Deactivate Shopify v1](https://razorpay.com/docs/build/browser/assets/images/shopify-deactivate-v1-final.jpg)
>
> For more information, see [Shopify FAQs](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/faqs.md).

## Reconcile Payments on Razorpay Secure

You can reconcile payments for Razorpay Secure using the **Payment Id** provided at the Shopify checkout.
Know more about how to [reconcile Shopify orders on the Dashboard](https://razorpay.com/docs/payments/payment-gateway/ecommerce-plugins/shopify/reconcile-payments.md).

## Difference in Order Information Between Old Razorpay App and Razorpay Secure

Check the table below to understand the difference in data about the gateway provided by the Old Razorpay App and Razorpay Secure.

| **Old Razorpay App** | **Razorpay Secure** |
| - | - |
| <ul><li>Razorpay account details.</li><li>Razorpay reference number.</li><li> Currency</li><li>Amount</li><li> Gateway reference Id</li><li> Timestamp</li><li>Signature</li></ul> | <ul><li>Payment Id</li></ul> |

The image below shows the difference in data provided by the old Razorpay App and Razorpay Secure.

![Old New difference](https://razorpay.com/docs/build/browser/assets/images/old-new-plugin.jpg)

> [!NOTE]
>
> **Handy Tips**
>
> In the case of the old Razorpay app, multiple data were available to track payments, whereas, in the case of the Razorpay Secure app, only a single piece of data, the `Payment Id`, is provided by Shopify. Know more about [how to process a payment](https://shopify.dev/apps/payments/processing-a-payment#resolve-a-payment) on Shopify.
