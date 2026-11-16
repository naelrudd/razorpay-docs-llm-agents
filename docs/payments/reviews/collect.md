> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Collect Reviews

> Configure when review requests are sent, how reviews are displayed on your Shopify store, and how to migrate reviews from Judge.me.

Available in
🇮🇳 India

Decide when your customers are asked, how they hear from you, where reviews show up on your store, and how to bring across reviews you have already collected elsewhere.

## Scheduling

In **Settings > Review collection**, set two delays:

* **After delivery** - 7 days by default. Used whenever Shopify reports the order as delivered.
* **After fulfilment** - 14 days by default. The fallback, used when delivery is not reported.

Both accept 1 to 30 days. Timing is worked out by a daily job, so treat your delay as the day after which review alert is sent rather than an exact hour.

## Channels

WhatsApp, SMS and email, all on by default. Switch off any you do not want to use.

Each channel you turn on, sends messages independently. This ensures a customer with both an email address and a phone number hears from you on every channel you have enabled. If you would rather reach people once, turn the others off.

## The review form

Hosted by Razorpay and built for mobile. One link per order, valid for 45 days, covering every item in that order. A star rating is required, review text is optional. Customers can add up to 1,000 characters in the review text and can attach up to five photos or videos.

## Requesting reviews for past orders

During setup, you can request reviews for orders from the last 30, 60 or 90 days - the quickest way to build up reviews on a store that has been trading for a while.

## Displaying Reviews

| Widget | Where it goes | What it shows |
| - | - | - |
| Review widget | Your product page | The full review list - rating summary and individual reviews, with photos. |
| Rating badge | Next to your product title | Average star rating and review count, at a glance. |

### Adding them to your theme

Go to **Reviews > Widgets** in your Razorpay Dashboard and follow the steps to add each widget to your Shopify theme. There is no code to write and no snippet to paste. You place them from the theme editor and they know which product they are rendering for.

Most stores put the review widget directly below the product description and the rating badge just under the product title so shoppers see the score before they scroll.

### If nothing appears

The widgets only show **published** reviews. A new store with no reviews yet, or one in manual mode with everything still awaiting approval, shows nothing at all.

## Migrating Your Reviews

### From Judge.me

1. Go to **Reviews > Import reviews**.
2. Enter your Judge.me private API token.
3. We check the connection straight away. If the token is wrong, you will know immediately rather than an hour later.
4. The import runs in the background. You can leave the page while it works.

**What comes across:** star rating, title, review text, reviewer name, review date, photos and verified-buyer status where Judge.me recorded it.

> [!NOTE]
>
> **Handy Tips**
>
> * **Your photos keep working.** Review images are copied to Razorpay's own storage, so they do not break when you disconnect Judge.me.
> * **Re-running is safe.** Anything already imported is skipped, so you can run it again later to pick up newer reviews.
> * **Reviewer email addresses are never stored.** They are converted to a one-way hash as they arrive, so we can recognise a returning reviewer without holding their address.

### Coming from another platform?

Judge.me is the only direct migration today. If you are on Yotpo, Loox, Stamped, Ali Reviews or Shopify's own product reviews, email [reviews@razorpay.com](mailto:reviews@razorpay.com) and the team will work through it with you.

### Why we don't accept a CSV upload

Razorpay Reviews is built so that every review can be traced back to a real order. That verification trail is what lets shoppers trust the ratings on your store and it is what separates these reviews from ones anyone could type into a spreadsheet. A CSV carries no evidence of where its rows came from, so accepting one would quietly weaken that guarantee for every other review on the page. Judge.me reviews arrive with their own provenance, which is why that route is supported.

> [!WARNING]
>
> **Watch Out!**
> Import before you disconnect Judge.me. Photo links in an export from a disconnected app often point at images that no longer load.

### Related Information

* [Razorpay Reviews](https://razorpay.com/docs/payments/reviews.md)
