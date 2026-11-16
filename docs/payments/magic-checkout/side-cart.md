> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Magic Cart Setup | Razorpay Magic Checkout

> Configure the Magic Cart experience for your Shopify store with theme colours, order instructions, message banners, gift cards, milestone, cross-sell and free gift widgets to increase average order value.

Available in
🇮🇳 India

Magic Cart is a fully customisable cart experience for your Shopify store, powered by Razorpay Magic Checkout. It opens when a customer clicks the cart button on your storefront. It appears one step before checkout, giving you a new space to surface offers, recommend products and nudge customers towards higher-value orders.

Magic Cart helps you:

* **Increase average order value (AOV)**: Milestone incentives, cross-sell recommendations, add-ons and free gifts encourage customers to add more items to their cart.
* **Improve conversion rate**: Customers can view available coupons, savings and delivery nudges before they reach checkout, reducing the drop-off between cart and checkout.
* **Replace third-party cart plugins**: Configure everything from the Razorpay Dashboard instead of relying on paid, third-party Shopify apps that may not integrate smoothly with Magic Checkout.

> [!WARNING]
>
> **Watch Out!**
>
> Magic Cart is available only for Shopify users.

## Get Started

Follow the steps given below to enable and configure Magic Cart:

1. Log in to the [Razorpay Dashboard](https://dashboard.razorpay.com/) and navigate to **Magic Checkout** → **Setup & Settings**.
2. Click **Magic Cart**.
3. Configure the [Cart Configurations](#cart-configurations) and [Widgets](#widgets) as required.
4. Click **Publish changes**.

> [!NOTE]
>
> **Handy Tips**
>
> * The first time you publish, you are prompted to select the Shopify theme on which Magic Cart should be enabled. We recommend selecting a test theme first, previewing the experience yourself and then publishing it on your live theme.
> * The **Preview** panel on the right updates in real time as you make changes. Use it to verify how your cart looks before you publish.
> * The **Publish changes** button appears whenever you make an unsaved change. Your changes go live on the selected theme only after you publish.

## Cart Configurations

You can configure the following:

> [accordion] Cart Theme Colour
>
> Pick a theme colour that best reflects your brand. This colour is applied to key cart elements such as buttons and the message banner. The milestone progress indicator uses a lighter shade of the same colour.
>
> 1. Under **Basic settings**, click **Edit** next to **Cart theme colour**.
>
> 2. Select a colour using the colour picker or enter a hex code.
>
> 3. Click **Publish changes**.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > If you do not configure a custom colour, the cart inherits the theme colour set in your Magic Checkout modal settings.

> [accordion] Order Instructions
>
> Allow your customers to add delivery notes or special requests before they proceed to checkout.
>
> 1. Toggle on **Order instructions**.
> 2. An **Order instructions** text box appears in the cart for customers to fill in.
> 3. Click **Publish changes**.
>
> Customers can use this field to communicate details such as gift wrap requests or specific delivery preferences.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Order instructions are disabled by default. Customers can enter plain text only.

> [accordion] Gift Card
>
> Allow customers who want to redeem a Shopify gift card to complete their purchase through the Shopify checkout flow.
>
> 1. Toggle on **Gift card**.
> 2. Click **Publish changes**.
>
> When enabled, a **Redeem gift card?** check box appears in the cart. When a customer selects this and clicks **Checkout**, they are redirected to the Shopify checkout page instead of Magic Checkout to complete the payment.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > This setting is intended for businesses who accept gift card payments but are not on the Shopify Plus plan. Magic Checkout does not support gift card redemption for stores below the Shopify Plus plan, so these customers are routed to the Shopify checkout flow instead.

> [accordion] Message Banner
>
> Display a promotional banner at the top of the cart to highlight offers, shipping thresholds or key information.
>
> 1. Toggle on **Message banner**.
> 2. In the **Text on banner** field, enter the message you want to display. You can include emojis.
> 3. Click **Publish changes**.
>
> The banner appears at the top of the Magic Cart and is visible whenever the cart is open.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > The banner is disabled by default. Use it to surface time-sensitive promotions or free shipping thresholds directly in the cart.

## Widgets

Magic Cart offers the following widgets that you can enable and configure to enrich the cart experience:

* [Milestone Widget](#milestone-widget)
* [Cross-sell Widget](#cross-sell-widget)
* [Coupons Widget](#coupons-widget)
* [Free Gift Widget](#free-gift-widget)
* [Add-Ons Widget](#add-ons-widget)

### Milestone Widget

The Milestone Widget gamifies the cart experience by showing customers how close they are to unlocking a reward, such as free shipping, a free gift or a discount, based on their cart value or item quantity. This encourages customers to add more items, increasing your average order value (AOV).

> [!NOTE]
>
> **Handy Tips**
>
> The Milestone Widget is an informational nudge only. It displays progress towards a reward but does not apply the reward itself. You must configure the actual reward separately, for example, set up free shipping in your shipping settings, configure a coupon for a discount or use the [Free Gift Widget](#free-gift-widget) for a free gift.

To configure the Milestone Widget:

1. Under **Widgets**, click **Configure** next to **Milestone widget**.
2. Toggle on **Milestone widget**.
3. Select how milestones are measured:

   * **Cart Value**: Milestones are triggered based on the total value of products in the cart.
   * **Cart Quantity**: Milestones are triggered based on the number of items in the cart.

   > [!WARNING]
   >
   > **Watch Out!**
   >
   > You cannot use both types within the same milestone configuration.
4. For each milestone, configure the following:
   1. **Cart Value**/**Quantity**: Enter the threshold at which the milestone is triggered. Each milestone value must be greater than the previous one.
   2. **Type**: Select the type of reward to display from the drop-down list, for example, free gift, free shipping or discount.
   3. **Reward**: Enter a short description of the reward, for example, `Free gift worth ₹300`.
   4. **Message**: Enter the nudge message shown to the customer in the cart. You can use the remaining cart value or quantity as a variable in this message.

      > [accordion] Example messages:
      >
      > * **Cart Value**: If the milestone is set at ₹2099 with the reward *Free gift worth ₹300* and the customer's cart value is ₹1500, you can enter the message as: *Add products worth ₹599 more to get a free gift worth ₹300.*
      > * **Cart Quantity**: If the milestone is set at 5 items with the reward *15% off* and the customer has 3 items in their cart, you can enter the message as: *Add 2 more products to get 15% off.*
5. Click **+ Add Milestone** to add another milestone.
6. Click **Publish changes**.

> [!NOTE]
>
> **Handy Tips**
>
> * At least 1 milestone is required to enable the **Milestone widget**.
> * You can configure up to 3 milestones. Once you add the third milestone, the option to add more is disabled.
> * Milestone values must be configured in ascending order. For example, if **Milestone 1** is set at ₹1000, **Milestone 2** must be set at a value greater than ₹1,000.
> * To remove a milestone, click **Remove** on the corresponding milestone.

### Cross-sell Widget

The Cross-sell Widget recommends additional products in the cart as quick-add suggestions, helping customers discover complementary items and increasing your average order value.

To configure the Cross-sell Widget:

1. Under **Widgets**, click **Configure** next to **Cross-sell widget**.
2. Toggle on **Cross-sell widget**.
3. Enter a **Title** for the widget, for example, `You may also like`.
4. Select how recommended products are determined:

   > [accordion] Shopify Recommendation Engine
   >
   > Let Shopify automatically recommend products based on your catalogue. No additional configuration is required.

   > [accordion] Custom Rules
   >
   > Click **Customize** to create your own recommendation rules. For each rule:
   >
   > 1. Set the **pre-conditions** that determine when the rule applies. You can set conditions based on:
   >    * **Cart state**: For example, show the recommendation only when the cart value is above ₹1000 or when the cart contains at least 5 items.
   >    * **Products in the cart**: For example, recommend a tie when the cart contains a shirt or recommend a belt when the cart contains trousers.
   >
   > 2. Select the products you want to recommend when the pre-conditions are met.
   >
   > 3. Add more rules as required. Recommendations are evaluated against the cart and shown based on the matching rule.
   >
   > > [!NOTE]
   > >
   > > **Handy Tips**
   > >
   > > You can create multiple such rules. Each rule currently supports up to 3 recommended products. The widget is horizontally scrollable when multiple products are recommended.
5. Click **Publish changes**.

### Coupons Widget

The Coupons Widget displays your active coupons directly in the cart, so customers can see the discounts available to them before they reach checkout.

1. Under **Widgets**, toggle on **Coupons**.
2. Click **Coupons** to open the coupon settings and configure which coupons are shown, active or deactivated.
3. Click **Publish changes**.

> [!NOTE]
>
> **Handy Tips**
>
> The Coupons Widget is only an entry point to your existing Magic Checkout coupon settings. The coupons shown in the cart are the same ones you configure in the **Coupons** tab. To create and manage coupons, see [Magic Checkout Coupons](https://razorpay.com/docs/payments/magic-checkout/shopify/features#coupons).

### Free Gift Widget

The Free Gift Widget lets you reward customers with a free or nominally priced gift when their cart meets a defined value or quantity. Unlike the Milestone Widget, this widget enforces the reward by adding the gift to the cart.

To configure the Free Gift Widget:

1. Under **Widgets**, click **Configure** next to **Free gift** (freebies).
2. Create a rule and select how it is triggered:
   * **Cart Value**: The gift is unlocked when the cart value reaches the configured threshold, for example, ₹4000.
   * **Cart Quantity**: The gift is unlocked when the cart contains the configured number of items.
3. Select the gift products to offer:
   * Select a single product to add it automatically when the customer becomes eligible.
   * Select up to 3 products to let the customer choose one of them as their free gift.
4. Set the price of the gift:
   * **Free**: Offer the product at zero value.
   * **Fixed price**: Charge a small nominal amount, for example, ₹1 or ₹10. Many merchants prefer this option because a product added at absolute zero value is not tax-friendly.
5. Add more rules as required. You can create up to 3 rules.
6. Click **Publish changes**.

> [!NOTE]
>
> **Handy Tips**
>
> * You can create up to 3 rules, including overlapping ones. For example, if you set one rule at ₹4,000 and another at ₹6,000, a customer with a cart value of ₹7,000 becomes eligible for both gifts.
> * A gift unlocked by one rule is offered independently of any other rule the customer qualifies for.

### Add-Ons Widget

The Add-Ons Widget lets you offer supplementary products, such as gift wrap or a low-cost complementary item, that customers can add to their order in one click. Unlike cross-sell recommendations, the Add-Ons Widget is sticky and remains visible in the cart at all times.

You can offer add-ons at two levels:

* **Item add-on**: The add-on is tied to a specific product in the cart. For example, offer gift wrap for a particular item.
* **Order add-on**: The add-on applies to the entire order. For example, offer a low-cost product, such as a sunscreen, that customers can add to any order.

To configure the Add-Ons Widget:

1. Under **Widgets**, click **Configure** next to **Add-ons**.
2. Toggle on **Add-ons**.
3. Select the add-on level: **Item** or **Order**.
4. Select the products you want to offer as add-ons.
5. Click **Publish changes**.

> [!NOTE]
>
> **Handy Tips**
>
> You can set an add-on to be pre-selected, so it appears checked by default when the cart opens. Customers can uncheck it if they do not want it.

## Related Information

* [Magic Checkout Coupons](https://razorpay.com/docs/payments/magic-checkout/shopify/features#coupons)
* [Login with Razorpay Setup](https://razorpay.com/docs/payments/magic-checkout/login-with-razorpay.md)
* [Checkout Setup](https://razorpay.com/docs/payments/magic-checkout/shopify.md)
