> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Offers on Payment Links

> Provide offers to customers making payments using Payment Links.

Available in
🇮🇳 India

Use Razorpay Offers to provide discounts or cashback on Payment Links issued to customers. You can restrict the payment methods on which the Offers are applied and limit their usage to a defined period.

> [!WARNING]
>
> **Watch Out!**
>
> Offers are not available for UPI Payment Links.

## Enable Offers for Payment Links

Select the **Checkout Visibility** option to display discount and cashback offers on Payment Links.

![show offers on payment links](https://razorpay.com/docs/build/browser/assets/images/payment-links-offers-checkout-visibility.jpg)

## How Offers Appear for Payment Links

Watch this video to see how offers appear for Payment Links when customers want to make payments using Payment Links.

<video width="650" controls>
  <source src="https://razorpay.com/docs/build/browser/assets/images/payment-links-pl-offer.mp4" type="video/mp4" />

  offers on payment links
</video>

## SKU and Brand Offers on Payment Links

Add the products (SKUs) a customer is paying for to a Payment Link, so that [SKU and Brand Offers](https://razorpay.com/docs/payments/offers/sku-offers.md) configured for those products apply at checkout. For example, a bank discount on a specific phone model applies only when that model's SKU is on the link.

> [!NOTE]
>
> **Feature Request**
>
> SKU and Brand Offers on Payment Links is an on-demand feature. Contact your Razorpay account manager to enable it on your account. Razorpay configures the offers and the SKUs they apply to for you.

To create a Payment Link with product details:

1. Log in to the Dashboard.
2. Go to the **PAYMENT PRODUCTS** section and click **Payment Links**.
3. Click **+ Create Payment Link**.
4. In the **Product details** section, turn on **Add product details**.
5. Enter the details of each product:
   * **SKU id** (Mandatory): The SKU identifier. It must match the SKU configured in the offer.
   * **Unit price** (Mandatory): The price of one unit of the product.
   * **Quantity** (Mandatory): The number of units.
   * **Name** (Optional): The product name. For example, `Smartphone 128 GB`.
6. Click **Add product** to add more products to the link.
7. Enter the other link details, such as customer details and link expiry, and click **Generate Link**.

Watch this video to see how to add product details to a Payment Link.

<video controls muted playsInline preload="metadata" width="500" aria-label="Create Payment Link form: the merchant turns on Add product details, enters a SKU id, unit price, quantity and product name, and the products total updates to 53,940 rupees.">
  <source src="https://mintcdn.com/razorpay-881012b3/1HTwZNb6MPt43Eps/static/docs-home/assets/payment-links-sku-offers-demo.mp4?fit=max&auto=format&n=1HTwZNb6MPt43Eps&q=85&s=0b42789ae2ae5cb12688d26ddfc3ead9" type="video/mp4" />
</video>

The Payment Link amount is calculated from the products you add and is shown as **Products total**. When the customer opens the link, Checkout shows the products and the offers that apply to them, and applies the best offers for the payment method the customer selects.

> [!WARNING]
>
> **Watch Out!**
>
> * SKU and Brand Offers on Payment Links work only in live mode. Payment Links created in test mode do not carry product details.
> * You can add product details only when you create the link from the Dashboard.

#### Related Information

* [About Offers](https://razorpay.com/docs/payments/offers)
* [Create Offers](https://razorpay.com/docs/payments/offers/create.md)
* [SKU and Brand Offers on Standard Checkout](https://razorpay.com/docs/payments/offers/sku-offers.md)
