> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Set Up Magic Checkout on Your Shopify Store

> Which Shopify setup you have, how to put Magic Checkout live on your store yourself, how to check it is live and why buyers may still see Shopify checkout.

Available in
🇮🇳 India

Magic Checkout replaces the Shopify checkout on your store with Razorpay's one-page checkout. This page covers Shopify stores. For WooCommerce, Magento or your own website, see [Magic Checkout](https://razorpay.com/docs/payments/magic-checkout).

## Which Shopify setup you have

Razorpay runs two different Shopify setups. Check which one you are on before you follow any steps on this site.

| Setup | What it is | How to tell |
| - | - | - |
| **Magic Checkout** (custom app) | Razorpay creates a custom app for your store and you install it in Shopify. Razorpay's checkout pop-up replaces the Shopify checkout, takes the payment and creates the order in Shopify. This is the setup new Shopify stores get. | **Setup & Settings** on your Razorpay Dashboard shows **Checkout Setup**. The Dashboard calls the app **Razorpay Magic Checkout Pro**; in your Shopify admin it appears as your merchant ID followed by **MagicCheckout**. The theme Magic Checkout was added to has **Magic Checkout** in its name. |
| **Shopify One-page Checkout(MagicX)** (public app) | The **Razorpay COD & Magic Checkout App** from the Shopify App Store. Razorpay's window collects the buyer's phone number, OTP and saved address, then opens Shopify's own checkout with those details filled in. The buyer pays on Shopify. | **Setup & Settings** shows **Checkout Settings** and **Control Center**. When Razorpay has offered you the upgrade, the menu shows a **Magic Checkout Pro** card (**Set up in 2 minutes!**). If both apps are installed, **Checkout Setup** shows **Toggle checkout platform:** with **Shopify One-page Checkout(MagicX)** as one option. |

Shopify One-page Checkout is being retired. Existing stores keep it until they move to Magic Checkout through the **Magic Checkout Pro** card on the Dashboard (**Start setup**, then **Start upgrade**), which uninstalls the public app. New stores set up Magic Checkout, as on this page. The settings pages for One-page Checkout are under [COD & Magic Checkout](https://razorpay.com/docs/payments/cod-magic-checkout/shopify).

| What differs | Magic Checkout | Shopify One-page Checkout(MagicX) |
| - | - | - |
| Where the buyer pays | Razorpay's checkout pop-up | Shopify's own checkout |
| Cash On Delivery page, Advanced COD Workflows, Partial COD, Convert COD to Prepaid, RTO Analytics | Yes | No. COD on this setup is Razorpay COD, set on its own COD Settings page and applied as a Shopify shipping rate and payment customisation |
| Shipping rates set on the Razorpay Dashboard | Yes | No, only where you ship; the buyer pays Shopify's rate |
| Checkout Setup, Checkout Config, Additional Fee, GSTIN capture | Yes | A smaller Checkout Settings page; no GSTIN |
| Orders list with refunds, Edit Orders | Yes | No |
| Segments, Analytics and ads setup, Order analytics, Magic Cart | Yes | No |
| Control Center | No | Yes |

## When Magic Checkout is live for your buyers

Buyers see the Magic Checkout pop-up only when all of these are true:

1. Your Razorpay account is activated, so you have Live API keys, and your Dashboard is in Live mode when you start setup. Setup writes your Live key into the store and checks for keys in the mode the Dashboard is in; without the Live key Magic Checkout cannot run.
2. Magic Checkout is switched on for your Razorpay account, either by you through the setup on this page or by Razorpay.
3. The buyer is viewing your store in Indian Rupees. Magic Checkout does not load on a page shown in another currency, for example through a Shopify Markets currency selector. A display-only converter app does not affect this.
4. The theme Magic Checkout was added to, the one with **Magic Checkout** in its name, is your **published** theme in Shopify. Magic Checkout lives inside one theme. Any other theme does not have it.
5. On Shopify One-page Checkout(MagicX) only: **Enable Magic Checkout** is on under **Setup & Settings** → **Checkout Settings**. Magic Checkout on the custom app has no on/off switch.
6. Shipping is set up under **Setup & Settings** → **Shipping Setup**. Home shows **Shipping is required to start Magic Checkout** until it is.
7. Every product in the cart is in stock, published, and available to the Magic Checkout app in Shopify. Otherwise Magic Checkout opens, shows **Uh-oh!**, and **Go to cart** takes the buyer to the Shopify checkout.

If any one of these fails, buyers land on the Shopify checkout page. See [Why is this not working?](#why-is-this-not-working).

## What setup switches on for you

Self-serve setup turns on Magic Checkout for your account with these defaults: taxes included in prices, the email field shown at checkout, the Razorpay coupon engine, Partial COD, the Magic Checkout button on product pages (off in the cart), and your Shopify shipping rates imported into Magic Checkout. Change any of them later under **Setup & Settings**.

## Before you start

* Finish KYC on the Razorpay Dashboard and wait for activation. Live API keys exist only after activation, and setup needs them.
* Switch the Dashboard to Live mode and generate API keys under **Account & Settings** → **Website and app settings** → **API keys**. Without a key in the current mode, setup stops at **API key not found!**.
* Use an owner or admin login on the Razorpay Dashboard. Other roles do not see **Setup & Settings**.
* Use a Shopify login that can install apps and manage themes.
* Leave room for one more theme in your Shopify theme library. Setup makes a copy of your live theme and adds Magic Checkout to that copy.
* Connect one Shopify store to one Razorpay account. Connecting a second store to the same account replaces the first.

## Set up Magic Checkout yourself

Every Razorpay account can set up Magic Checkout on Shopify itself. The Magic Checkout page on the Dashboard shows **Try Magic Checkout now**. Your progress is saved, so you can close the Dashboard and come back; after the app is installed the store URL is locked.

> [accordion] Step 1: Start setup and connect your store
>
> 1. Log in to the [Razorpay Dashboard](https://dashboard.razorpay.com/) and open **Magic Checkout**.
> 2. Click **Try Magic Checkout now**. If you started earlier, the button reads **Resume setup** and shows your progress.
>
>    ![Try Magic Checkout now](https://mintcdn.com/razorpay-881012b3/5gQNTic0lHgA-ZJy/static/docs-home/assets/magic-shopify-setup-start.jpg?fit=max\&auto=format\&n=5gQNTic0lHgA-ZJy\&q=85\&s=7163842202475c11b001c1d635e690e8)
> 3. If **API key not found!** opens, click **Open Settings**, generate your Live API keys, come back and click **Try Magic Checkout now** again.
> 4. Under **What's your store URL?**, type your store address in **Enter Shopify URL** or pick it from **Shopify store URL**. Wait for **Valid Shopify URL**.
>
>    ![What's your store URL](https://mintcdn.com/razorpay-881012b3/5gQNTic0lHgA-ZJy/static/docs-home/assets/magic-shopify-setup-url.jpg?fit=max\&auto=format\&n=5gQNTic0lHgA-ZJy\&q=85\&s=9a2e04fb681600d1d3538d07e36717d5)
> 5. Click **Proceed to install app**.

> [accordion] Step 2: Install the app on Shopify
>
> 1. On the **Razorpay Magic Checkout Pro** card, click **Install App**. Shopify opens; install the app there.
>
>    ![Install the Razorpay Magic Checkout Pro app](https://mintcdn.com/razorpay-881012b3/5gQNTic0lHgA-ZJy/static/docs-home/assets/magic-shopify-setup-install.jpg?fit=max\&auto=format\&n=5gQNTic0lHgA-ZJy\&q=85\&s=4a88079f62b0671e4a25cc101f475124)
> 2. Come back to the Razorpay tab and click **Next**.
> 3. If you see **Do you levy taxes on your products?**, pick the answer that fits your store and click **Proceed to create theme**. On the shorter setup the tax setting is read from your Shopify store and the question appears only if that read fails.

> [accordion] Step 3: Add Magic Checkout to a copy of your theme
>
> 1. Under **Shopify theme creation**, check the theme marked **Created for you**. It is a copy of your live theme.
>
>    ![Shopify theme creation](https://mintcdn.com/razorpay-881012b3/5gQNTic0lHgA-ZJy/static/docs-home/assets/magic-shopify-setup-theme.png?fit=max\&auto=format\&n=5gQNTic0lHgA-ZJy\&q=85\&s=61a0860e6980cc10d0c27285d319ad62)
>
> 2. If you see **You're out of themes!**, delete an unused theme in Shopify, then click **Refresh**. Never delete your live theme; deleting a theme cannot be undone.
>
> 3. Click **Integrate Magic Checkout** and wait for it to finish. The page may reload once or twice; wait a minute, then refresh.
>
> > [!NOTE]
> >
> > **Magic Checkout is in the copy, not in your live theme yet**
> >
> > Nothing changes for your buyers until you publish the copy in Step 5. Test it first.

> [accordion] Step 4: Set up shipping
>
> On **Home**, under **Complete your setup**, open **Shipping setup** and click **View all shipping settings**. Switch on **Magic Shipping** and set up your zones and methods. **Home** ticks this step when **Magic Shipping** is on. Magic Checkout does not start without shipping. See [Shipping Options](https://razorpay.com/docs/payments/magic-checkout/shopify/features#shipping-options).

> [accordion] Step 5: Test, then publish the theme
>
> 1. In Shopify admin, go to **Online Store** → **Themes**. Find the copy under **Draft themes**; its name contains **Magic Checkout**. Click **Preview**, add a product to the cart, click **Checkout** and place a test order. The Magic Checkout pop-up should open and the order should land in Shopify as you expect. Orders placed on a preview theme do not count in Magic Checkout Analytics. [Watch how to test and publish](https://www.youtube.com/watch?v=onRhGmippxY).
>
> 2. Happy with the test? Publish the copy: click **Publish** on it and confirm. On **Home**, under **Complete your setup**, **Publish theme on Shopify** opens the Shopify themes page for you.
>
> 3. Back on **Home**, click **I've done it**. The step turns complete only when the Magic theme is your live theme. If **Home** does not show this step, see [Check that Magic Checkout is live](#check-that-magic-checkout-is-live) instead.
>
>    ![Complete your setup checklist on Home](https://mintcdn.com/razorpay-881012b3/5gQNTic0lHgA-ZJy/static/docs-home/assets/magic-shopify-setup-home-checklist.jpg?fit=max\&auto=format\&n=5gQNTic0lHgA-ZJy\&q=85\&s=537adccf97faa7487b08795252ee4734)
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > * The copy was made at setup time, so any edits you made to your live theme since then are not in it. Make them again on the copy before you publish.
> > * Shopify does not switch other apps' embeds on in a newly published theme. Check your other apps after publishing.

## Check that Magic Checkout is live

"Live" has two parts: Magic Checkout is on for your Razorpay account, and Magic Checkout is on the theme your buyers see. Both must be true.

1. On the Dashboard, open **Magic Checkout**. **Home** should greet you with **Welcome to Magic checkout**. If you still see **Try Magic Checkout now** or **Resume setup**, setup is not finished.
2. In Shopify admin, **Online Store** → **Themes**: the published theme must be the one with **Magic Checkout** in its name, not a draft and not another theme.
3. Open your store in a private window, add a product to the cart and click **Checkout**. The Magic Checkout pop-up should open, not the Shopify checkout page. Do this on the preview of the copy theme before you publish, and again on the live store after.

> [!NOTE]
>
> **On Shopify One-page Checkout(MagicX)**
>
> Check **Enable Magic Checkout** is on under **Setup & Settings** → **Checkout Settings**. Then in Shopify, open your live theme's editor, click **App embeds** and check the Razorpay embed is on. Test as in step 3: Razorpay's window should open before the Shopify checkout.

## Change your Shopify theme

Magic Checkout's code sits inside one theme, the one with **Magic Checkout** in its name. A new or changed theme does not have it, so buyers go back to the Shopify checkout. Your Razorpay settings are not affected.

1. Write to [magic-checkout-support@razorpay.com](mailto:magic-checkout-support@razorpay.com) with your store URL and the name of the new theme. Razorpay adds Magic Checkout to that theme itself, not to a copy.
2. If the theme is not published yet, preview it, place a test order, then publish it, as in Step 5 above.
3. Add back any other custom code your old theme had, or ask whoever added it.

> [!NOTE]
>
> **On Shopify One-page Checkout(MagicX)**
>
> This setup runs as a Shopify app embed, and Shopify does not switch app embeds on in a newly published theme. In Shopify admin, open **Online Store**, click **Customize** on the new theme, click **App embeds**, switch the Razorpay embed on and click **Save**. Or on the Dashboard, under **Setup & Settings** → **Checkout Settings**, check **Enable Magic Checkout** is on and click **Save Settings**, which opens the theme editor for you. Click **Save** there.

## Turn Magic Checkout off

Magic Checkout on the custom app has no switch on the Dashboard. To turn it off, write to [magic-checkout-support@razorpay.com](mailto:magic-checkout-support@razorpay.com) with your store URL. Buyers then go to the normal Shopify checkout. Do not uninstall the Shopify app to pause Magic Checkout: uninstalling turns Magic Checkout off on your Razorpay account and you would have to set it up again. When Razorpay switches Magic Checkout off for you, the theme code stays in place.

On Shopify One-page Checkout(MagicX): under **Setup & Settings** → **Checkout Settings**, switch off **Enable Magic Checkout** and click **Save Settings**.

## Why is this not working?

> [accordion] Buyers see the Shopify checkout instead of Magic Checkout.
>
> Check these in order and stop at the first one that fails.
>
> 1. Magic Checkout is on for your account: **Home** greets you with **Welcome to Magic checkout**. On Shopify One-page Checkout(MagicX): **Enable Magic Checkout** is on under **Setup & Settings** → **Checkout Settings**, and the Razorpay app embed is on in your live theme's editor.
> 2. The published theme in Shopify is the one with **Magic Checkout** in its name. If you changed or published another theme, see [Change your Shopify theme](#change-your-shopify-theme).
> 3. The buyer is viewing the store in Indian Rupees. A Shopify Markets currency selector set to another currency stops Magic Checkout from loading on that page.
> 4. The products in the cart are in stock, published and available to the Magic Checkout app. If not, Magic Checkout opens with **Uh-oh!** and **Go to cart** sends the buyer to the Shopify checkout.
> 5. If both Razorpay apps are installed: **Toggle checkout platform:** under **Setup & Settings** → **Checkout Setup** is set to the checkout you want.
> 6. If **Enable International Shipping** is on under **Setup & Settings** → **Shipping Setup** and the buyer confirms an address outside India, Magic Checkout sends them to the Shopify checkout on purpose. With it off, buyers cannot pick another country.
> 7. Theme code was edited. If the file `snippets/razorpay-magic-checkout.liquid` was changed or removed from the theme, Magic Checkout does not load. Write to support with the theme name; re-adding Magic Checkout rewrites the file.
> 8. Other apps take the first click. Upsell apps such as SellEasy and Zepto handle the first click on the checkout or Buy it now button and Magic Checkout opens on the second. Carts with a Recurpay subscription go to Recurpay's checkout, and a cart with a total of zero goes to the Shopify checkout.
> 9. If only some products fail: open the product in Shopify admin and under **Publishing** make sure the **Magic Checkout** sales channel is selected.
>
> If every check passes, write to [magic-checkout-support@razorpay.com](mailto:magic-checkout-support@razorpay.com) with your store URL, a product link, the time it happened and a screen recording. Six causes only Razorpay can see: a traffic split on your account that sends a share of buyers to the Shopify checkout, a missing or malformed key in the theme code, an unsupported bundle app in the cart, a failure creating the Shopify checkout or order, a failure fetching taxes, or a failure applying additional fees.

> [accordion] I do not know whether Razorpay has turned Magic Checkout on for my account.
>
> Open **Magic Checkout** on the Dashboard. **Try Magic Checkout now** or **Resume setup** means Magic Checkout is not live yet: finish the setup yourself. **Welcome to Magic checkout** on **Home** means it is on and setup is done.

> [accordion] Setup stops at API key not found!
>
> You have no Live API keys. Click **Open Settings**, generate them and start again with **Try Magic Checkout now**.

> [accordion] Setup stops at You're out of themes!
>
> Your Shopify theme library is full. Delete an unused theme in Shopify, never the live one, then click **Refresh**.

> [accordion] Home says the Magic theme is not live on my store yet.
>
> The copy theme with **Magic Checkout** in its name is still a draft. Publish it in Shopify under **Online Store** → **Themes**, then click **I've done it** again. **Your live theme is ... Magic is set up on a different theme.** means you published another theme: publish the Magic Checkout theme again, or follow [Change your Shopify theme](#change-your-shopify-theme) if you want Magic on the new one.

> [accordion] My store is not on Shopify.
>
> On the Magic Checkout page, click **Not on Shopify?**, choose your platform under **Choose your platform** and click **Continue**. WooCommerce and Magento stores then follow their own setup pages; a custom website needs a developer and the [website integration](https://razorpay.com/docs/payments/magic-checkout/web.md).

> [accordion] My menu shows Checkout Settings, not Checkout Setup.
>
> You are on Shopify One-page Checkout(MagicX). Use the **Magic Checkout Pro** card in the menu, when Razorpay has offered it, to move to Magic Checkout, or see [COD & Magic Checkout](https://razorpay.com/docs/payments/cod-magic-checkout/shopify) for its settings.

> [accordion] Where do I see my orders and conversions after going live?
>
> Orders placed through Magic Checkout appear in Shopify as usual and under **Magic Checkout** → **Orders** on the Razorpay Dashboard. Conversion numbers are under **Magic Checkout** → **Analytics**.

## What to set up next

* [Shipping Options](https://razorpay.com/docs/payments/magic-checkout/shopify/features#shipping-options): zones, methods and rates. Required before Magic Checkout starts.
* [Cash on Delivery](https://razorpay.com/docs/payments/magic-checkout/shopify/features#cash-on-delivery): turn COD on and set where and when it shows.
* [Coupons](https://razorpay.com/docs/payments/magic-checkout/shopify/features#coupons) and [Login with Razorpay](https://razorpay.com/docs/payments/magic-checkout/shopify/features#login-with-razorpay).
* [Google Analytics](https://razorpay.com/docs/payments/magic-checkout/shopify/features#google-analytics), [Google Ads](https://razorpay.com/docs/payments/magic-checkout/shopify/features#google-ads) and [Facebook Ads](https://razorpay.com/docs/payments/magic-checkout/shopify/features#facebook-ads) under **Setup & Settings** → **Analytics and ads setup**.
* [Abandoned Sessions](https://razorpay.com/docs/payments/magic-checkout/abandoned-sessions.md): recover buyers who dropped off.
