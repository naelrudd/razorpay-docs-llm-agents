> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Razorpay Reviews

> Collect verified reviews from real, fulfilled Shopify orders over WhatsApp, SMS and email, then display them on your product pages with Razorpay Reviews.

Available in
🇮🇳 India

Razorpay Reviews asks your customers for a review after their order is delivered, over WhatsApp, SMS and email, then publishes those reviews on your product pages. Every review request goes out against a real, fulfilled order, so every review you collect is tied to a genuine purchase.

You manage everything from the **Reviews** section of your Razorpay Dashboard. It is included with your Razorpay account at no extra cost.

> [accordion] Why Razorpay Reviews
>
> * **Every review is tied to a real order.** Requests are issued per fulfilled order through a signed, single-use link. There is no open "write a review" form on your storefront, so there is no route for a review from someone who never bought from you.
> * **WhatsApp, SMS and email.** All three, which matters in India, where WhatsApp response rates lead email by a wide margin.
> * **Photos and videos included.** Up to five per review, at no extra cost.
> * **Start with the reviews you have already earned.** Request reviews for up to 90 days of past orders during setup, and migrate your existing Judge.me reviews across.
> * **No extra cost.** Included with your Razorpay account.

## How Reviews Works

Here is what happens between a delivered order and a published review:

1. **We check your orders once a day.** Every day, Razorpay Reviews reads your fulfilled Shopify orders from the last 30 days and works out which ones are due for a review request. It is a scheduled check rather than an instant one, so an order fulfilled at midday is picked up in the next day's run.
2. **We work out when to ask.** Each order gets a send time based on your two delays: 7 days after delivery if Shopify has reported it, otherwise 14 days after fulfilment. Both are adjustable between 1 and 30 days. Requests are held to a reasonable sending hour in your store's local time, so a request falling due overnight goes out the next morning.
3. **The request goes out** on each channel you have enabled, for example WhatsApp, SMS and email are all on unless you turn them off. Channels send independently rather than as a fallback chain, so a customer with both an email address and a phone number hears from you on every channel you have left on. A channel is skipped when the customer has no contact detail for it.
4. **Your customer leaves a review.** The message contains a one-tap link with no login and no password. A single link covers every item in the order, so a three-item order means one link and one flow. Links stay valid for 45 days. The form asks for:

   * **A star rating** - 1 to 5, required.
   * **Review text** - optional, up to 1,000 characters.
   * **Photos and videos** - optional, up to five files.

   Each link works once. If a customer opens it again after submitting, they are told they have already shared their experience for that order. No discount or coupon is issued for leaving a review.
5. **The review is published, or waits for you.** This follows your choice in **Settings > Review publish**:

   * **Automatically publish reviews** - reviews go live as soon as they arrive, according to your auto-publish rule. You can publish every review, or only those at or above a chosen star rating (2, 3, 4 stars and above, or 5 stars only). Anything below the rating you pick waits for you to approve it.
   * **Manually moderate reviews** - reviews with text or photos wait in your queue.

   > [!NOTE]
   >
   > Rating-only reviews always publish immediately, in either mode. Only reviews carrying text or photos enter the approval queue. So a bare 2-star rating with no comment appears even while you are moderating manually.
6. **It appears in your widgets.** Published reviews show in the review widget and count towards the rating badge on your product pages. Only published reviews are ever publicly visible.

## Get Started

To get started with Razorpay Reviews:

1. Go to **Reviews** in your Razorpay Dashboard and select **Start collecting reviews**.
2. Connect your Shopify store.
3. Set your branding.
4. Install the review widget in your theme.
5. Request reviews for past orders.
6. Check your timing and channels.

Refer to the sections below for detailed steps, and to [Collect Reviews](https://razorpay.com/docs/payments/reviews/collect.md) for how requests are scheduled, sent and displayed.

## Quickstart

### Before you start

You need:

* An active Razorpay account with Dashboard access.
* A Shopify store that you are an admin of.
* Your **Razorpay API key**. Generate or copy it from the [API keys page](https://dashboard.razorpay.com/app/keys).

### Step 1: Open Reviews in your Dashboard

Navigate to **Reviews** in your Razorpay Dashboard and select **Start collecting reviews**.

### Step 2: Connect your Shopify store

1. Install the **Razorpay Reviews** app on your Shopify store from the [Shopify App Store](https://apps.shopify.com/razorpay-trusted-badges).
2. Open the app and enter your **Razorpay API key** to link it to your Razorpay account. You can find your key on the [API keys page](https://dashboard.razorpay.com/app/keys).
3. Return to the Razorpay Dashboard. Your store now shows as connected and Reviews can read your orders.

> [!NOTE]
>
> **Handy Tips**
> Keep the Shopify tab open while you finish setup. If the connect step does not seem to complete, check that pop-ups are allowed for the Razorpay Dashboard. Authorisation opens in a new window.

### Step 3: Set your branding

This is what customers see when you ask them for a review.

1. **Brand name**: your store's name, as customers know it.
2. **Brand logo**: upload in 1:1 aspect ratio, maximum 5 MB, in JPG, PNG or WebP format.

### Step 4: Install the widget in your theme

Add the review widget to your Shopify theme so published reviews appear on your product pages. You can skip this step now and do it later from the **Widgets** tab. Refer to [Displaying reviews](https://razorpay.com/docs/payments/reviews/collect.md#displaying-reviews) for details.

### Step 5: Request reviews for past orders

Choose how far back to go: the last **90 days** (the default), 60 days, 30 days, or do not send to past orders at all. Select **Confirm & send**.

This is the fastest way to have reviews on your store from day one.

> [!WARNING]
>
> **Watch Out!**
> Backfill sends real messages to real customers. On a busy store, 90 days can mean a lot of WhatsApp and SMS messages going out at once. Choose a shorter window if you would rather start gently.

### Step 6: Check your timing and channels

Navigate to **Reviews > Settings > Review collection**.

* **Review request methods**: WhatsApp, SMS and email, all on by default. Switch off any you do not want to use.
* **Review request scheduling**: two delays, each between 1 and 30 days:
  * **After delivery**: 7 days by default.
  * **After fulfilment**: 14 days by default, used when Shopify does not report delivery.

Adjust the values if you want to, and save.

### Check it worked

* Open one of your product pages and confirm the review widget appears.
* Check **Reviews > Home** for submissions as they come in.

### Review states

| State | What it means |
| - | - |
| Submitted | Your customer has sent the review. |
| Published | Live on your store. The only publicly visible state. |
| Awaiting approval | Manual mode only, and only for reviews with text or photos. |
| Hidden | You have hidden it. Always reversible. |

Switching from manual approval back to auto-publish releases everything currently waiting, all at once. Every change is recorded, and hiding a review is never permanent - you can re-publish it at any time.

### Your queue does not stall

A review left awaiting approval for 7 days publishes automatically. This is deliberate: a queue you have not had time to work through should not quietly suppress genuine reviews your customers took the trouble to write. If you want to keep a review off your store, you can hide it.

## FAQs

> [accordion] How do I migrate my existing reviews?
>
> Connect your Judge.me account and we will pull them across, photos included. Coming from another platform? Email [reviews@razorpay.com](mailto:reviews@razorpay.com) and we will help you move. Refer to [Migrating your reviews](https://razorpay.com/docs/payments/reviews/collect.md#migrating-your-reviews) for details.

> [accordion] Why can't I upload a CSV of reviews?
>
> Razorpay Reviews keeps a verification trail behind every review, so shoppers can trust what they read. A spreadsheet carries no evidence that its rows came from real buyers, so we do not accept one - it would quietly weaken that guarantee for every other review on your page. A Judge.me import arrives with its own provenance, which is why it is supported.

> [accordion] When do reviews appear on my store?
>
> Immediately, if auto-publish is on - that is the default. In manual mode, reviews with text or photos wait for your approval, though rating-only reviews still publish straight away.

> [accordion] Do I need to edit my theme code?
>
> No. You add the widget once from your Shopify theme editor.

> [accordion] What does it cost?
>
> Nothing extra. Razorpay Reviews is included with your Razorpay account.

### Related Information

* [Collect Reviews](https://razorpay.com/docs/payments/reviews/collect.md)
