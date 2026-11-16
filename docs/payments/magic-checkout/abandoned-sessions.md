> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Abandoned Sessions

> See every recognised shopper who dropped off — Browsing, Cart or Checkout — in one Magic Checkout worklist, and act to win them back.

Available in
🇮🇳 India

**Abandoned Sessions** shows every recognised shopper who visited your store and left without buying, across the full funnel — those who only browsed, those who added to cart, and those who reached Magic Checkout. It gives your recovery team one worklist, one set of filters and one set of actions to win these shoppers back.

> [!NOTE]
>
> **Abandoned Orders is now Abandoned Sessions.**
>
> The page previously called **Abandoned Orders** — nested under **Orders** — is now called **Abandoned Sessions** and appears as its own entry in the left navigation. The old link redirects to the new page, and the data you had before is unchanged. What is new is two additional journey types (Browsing and Cart) alongside the abandoned checkouts you already worked.

![The Abandoned Sessions entry in the Magic Checkout left navigation, with the list of abandoned sessions on the right](https://razorpay.com/docs/build/browser/assets/images/magic-7e9e-image-3.png)

> [!NOTE]
>
> **About the screenshots on this page.** The dashboard is mid-rename, so some screens still read **Abandoned Orders** and use the older labels **Session** (the *Browsing* journey type) and **Browse** (the *Browsing* drop-off stage). These map directly to the terms used here — **Session / Browse → Browsing**. Only the labels are changing; the data and actions are the same.

> [!WARNING]
>
> **Watch Out!**
>
> Abandoned Sessions is available for **Shopify stores only**. On other platforms, abandoned checkouts continue to work exactly as before; the Browsing and Cart journey types are not available yet.

## The Three Journey Types

Abandoned Sessions covers the whole drop-off funnel. Every row is tagged with the stage at which the shopper left:

![The Abandoned Sessions list showing rows across all three journey types — Checkout, Cart and Session (Browsing) — each with its type and drop-off stage](https://razorpay.com/docs/build/browser/assets/images/magic-ee12-image-4.png)

| Journey type | The shopper… | Available from |
| - | - | - |
| **Browsing** | Browsed the store and left without adding anything to the cart. | From rollout on your store |
| **Cart** | Added items to the cart but never opened checkout. | From rollout on your store |
| **Checkout** | Entered Magic Checkout but dropped off before placing the order. | Full history |

> [!NOTE]
>
> Browsing and Cart are the new journey types. They start populating from the date the feature is enabled on your store, so your **Available from** date depends on when your store was onboarded. Checkout journeys retain their full history.

> [!NOTE]
>
> **One journey, one row**
>
> A shopper who browses, adds to the cart, and then abandons at checkout appears as a **single row**, not three. The row is classified by how far the shopper got: if a checkout was started it is a **Checkout** journey; otherwise, if a cart exists it is a **Cart** journey; otherwise it is a **Browsing** journey.

**Checkout** journeys also retain their sub-stages — `cart`, `address`, `payment` and `checkout_summary` — so you can see exactly where a checkout drop-off happened.

Once a cart exists on a journey (a Cart or Checkout journey, or a Browsing journey after you [build a cart](#build-a-cart-for-browsing-sessions)), the full action set applies: edit the cart, edit customer details, apply a discount, place a COD order, or generate a Magic Link.

![A session detail view showing customer details, cart items and payment details, with Edit, Add New Products and Place COD Order actions](https://razorpay.com/docs/build/browser/assets/images/magic-d1c6-image-5.png)

When you place a COD order for a shopper whose pincode is not normally eligible for Cash on Delivery, the dashboard shows an inline notice under **Place COD Order** and lets you override the restriction to place the order anyway.

![A COD not available for this Zipcode notice shown inline under the Place COD Order button, explaining the restriction can be overridden to place a COD order](https://razorpay.com/docs/build/browser/assets/images/magic-a8f6-image-10.png)

## Who Appears in the List

Abandoned Sessions lists **only shoppers Razorpay can recognise** — a shopper who has logged in through [Razorpay ID](https://razorpay.com/docs/payments/magic-checkout/login-with-razorpay.md), or who has transacted through Magic Checkout before. Anonymous visitors are counted in aggregate but never listed, because a row you cannot contact is not one you can act on.

Abandoned cart and session data is only provided for customers that have provided their marketing consent. The **Marketing Consent** column shows each shopper's consent state, so your team can see who you are permitted to contact before reaching out — a `–` means no marketing-consent state is recorded for that shopper. Check this column (and your own Shopify consent fields) before you contact anyone.

> [!NOTE]
>
> **Why are my counts lower than my store analytics?**
>
> Abandoned Sessions lists only shoppers we can identify — those who have logged in through Magic or bought through Magic Checkout before. Store analytics counts every visitor, including anonymous ones. Every row here is a person you can actually contact.

This is by design: the more shoppers Magic recognises, the larger and more actionable your Abandoned Sessions list becomes.

## Build a Cart for Browsing Sessions

A **Browsing** session has no cart, because the shopper never added anything. To recover it, build a cart on the shopper's behalf:

1. Open the Browsing session and click **Build cart**.

2. Search your catalogue and add products. Products the shopper viewed during their session are surfaced first, where available.

   ![The Add Products dialog: a search-by-name-or-SKU box with catalogue products, live prices and available inventory, and per-product quantity steppers](https://razorpay.com/docs/build/browser/assets/images/magic-e3af-image-9.png)

3. Once the cart exists, the full action set applies — edit the cart, apply a discount, place a COD order, or generate a Magic Link.

> [!NOTE]
>
> **Handy Tips**
>
> Prices and inventory shown while building a cart are **live Shopify values at build time**, not the values the shopper saw earlier. If a viewed product has since been repriced or gone out of stock, the current Shopify value applies.

## Filters and Drop-off Stage

The list supports filtering and searching across all three journey types:

![The Drop-off Stage filter open as a multi-select — Address, Payment, Contact, Checkout Summary, Browse and Cart — above the list, alongside the Status, Source, Type and Date Range filters, Manage Columns and Export](https://razorpay.com/docs/build/browser/assets/images/magic-860c-image-6.png)

* **Journey type** — a multi-select filter for **Browsing**, **Cart** and **Checkout**. All three are selected by default.
* **Drop-off stage** — the journey-level stage (Browsing / Cart / Checkout). For Checkout journeys, the sub-stages (`cart`, `address`, `payment`, `checkout_summary`) are also available.
* **Status**, **Source (UTM)** and **Date range** — as before.
* **Search** — across customer name, email and phone.

Sorting, search, pagination and export behave identically across all journey types.

## Shopify Tags and Automations

Every recognised abandoner is written to your Shopify customer list with a tag, and every order you place from Abandoned Sessions carries a tag. This turns Shopify — and every tool wired to it — into a retargeting surface with nothing to integrate.

### Tags

| Tag | Applied to | Meaning |
| - | - | - |
| `magic-session-abandoner` | Shopify customer | Browsed the store and left without adding to cart. |
| `magic-cart-abandoner` | Shopify customer | Added to cart, never opened checkout. |
| `magic-checkout-abandoner` | Shopify customer | Entered Magic Checkout, dropped before order. |
| `magic-agent-placed` | Shopify order | Order placed from the Abandoned Sessions dashboard (COD or Magic Link). |

Marketing consent captured through Magic is synced to the customer's Shopify marketing consent fields and is **never downgraded**. If the customer already exists in Shopify, only tags and consent are updated — no other customer data is changed.

### Automations You Can Build Today

Using these tags, you can build recovery flows in Shopify Flow, Shopify Email, Klaviyo and similar tools:

1. **Browsing win-back email** — Trigger on the `magic-session-abandoner` tag with email consent subscribed. Wait 2 hours, then send a "still thinking about it?" email featuring the collection they browsed. Low intent — one message, no discount.
2. **Cart reminder with a nudge** — Segment on `magic-cart-abandoner` with no order in the last day. Send a reminder at 1 hour, then an offer at 24 hours if there is still no order. Medium intent — the second message earns the discount.
3. **Checkout abandoner SMS** — Segment on `magic-checkout-abandoner` with SMS consent subscribed. Send an SMS with the store link within 30 minutes. Highest intent — speed beats incentive.
4. **Stop double-contact after recovery** — Trigger on order created with the `magic-agent-placed` tag. Add a `magic-recovered` customer tag (one you create in this flow, not a tag Razorpay applies) and exclude `magic-recovered` from flows 1–3, so an agent recovery and an automated nudge don't both land on the same shopper.
5. **Recovered-revenue report** — In Shopify, filter Orders by the `magic-agent-placed` tag and export. This is the revenue your recovery team produced, in your own numbers.
6. **Retargeting audiences** — Use `magic-cart-abandoner` or `magic-checkout-abandoner` as high-intent retargeting audiences, and `magic-session-abandoner` as a low-cost prospecting or lookalike seed.

### Rules to Follow

* **Consent first.** Tags identify; consent permits. Always check marketing consent before a flow sends — a flow that ignores consent is a compliance risk.
* **Don't over-contact Browsing abandoners.** One message. They showed the least intent.
* **Tags accumulate.** A shopper can carry more than one abandoner tag. Flows should key on the highest-intent tag present.
* **Tag names are stable.** These tags are a public interface and will not be renamed, so you can safely build long-lived segments and flows on them.

## Export to CSV

You can export the filtered list to CSV, as before. The export now includes a **journey-type column** so you can distinguish Browsing, Cart and Checkout rows offline. The file also carries a note about the date from which Browsing and Cart data is available for your store.

## Reach WhatsApp and CRM Partners Automatically

The same journeys you see in Abandoned Sessions can be pushed to your retargeting partners as events, using **Magic Webhooks**:

| Event | Fires when | Status |
| - | - | - |
| `checkout.abandoned` | The shopper opened checkout and went quiet for about 30 minutes. | Live |
| `cart.abandoned` | The shopper added to cart, never opened checkout, and went quiet for about 45 minutes. | Coming soon |
| `cart.session_abandoned` | The shopper browsed, added nothing, and went quiet for about 30 minutes. | Coming soon |

> [!NOTE]
>
> **Retargeting webhooks are coming soon.**
>
> Only `checkout.abandoned` is live today. The new retargeting events for the Browsing and Cart journeys — `cart.abandoned` and `cart.session_abandoned` — are coming soon; this page will be updated once they are released. Until then, the setup guide below covers the existing abandoned-checkout webhook only.

**Bitespeed, BusinessOnBot and Intelliticks** are pre-integrated — select one from the dropdown when configuring webhooks. The dashboard is for your own recovery team; the webhooks are for the tools you already use. Same shoppers, two routes.

For setup of the existing abandoned-checkout webhook, see [Abandoned Cart Webhook](https://razorpay.com/docs/payments/magic-checkout/abandoned-cart.md).

## Availability

* **Platform:** Shopify stores only. On other platforms, abandoned checkouts continue to work as before; Browsing and Cart journeys are not available.
* **Data:** Browsing and Cart data is available from the day the feature is enabled on your store. Checkout history is unchanged.

### Related Information

* [Automatic Customer Tagging for Retargeting](https://razorpay.com/docs/payments/magic-checkout/login-with-razorpay/automation-tags.md)
* [Abandoned Cart Webhook](https://razorpay.com/docs/payments/magic-checkout/abandoned-cart.md)
* [Razorpay ID](https://razorpay.com/docs/payments/magic-checkout/login-with-razorpay.md)
