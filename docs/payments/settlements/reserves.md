> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Reserves on International Payments

> Know how rolling and fixed reserves work on your international payments, how much we hold, for how long and where to track the release date.

Available in
🇮🇳 India

A reserve is money we hold in your Razorpay account for a set period, before we settle it to you. It covers any disputes raised on your payments, including chargebacks.

A reserve is your money. We hold it temporarily and then release it to you. We charge no fee on it, and you are not exposed to exchange rate movement while we hold it.

> [!NOTE]
>
> **Handy Tips**
>
> Every amount, percentage and hold period on this page is an example. Your own terms appear in your Razorpay Dashboard.

> [!WARNING]
>
> **Watch Out!**
>
> The **Reserve balance** on this page is not the [Reserve Balance](https://razorpay.com/docs/payments/dashboard/account-settings/balances.md#reserve-balance) under **Account & Settings** → **Balances**. That one is a buffer you add yourself to cover refunds. This one is money we hold back from your international payments. Both can apply to your account.

## Prerequisites

A reserve applies to your account when:

* Your account is KYC approved and fully activated. Know more about [KYC Verification](https://razorpay.com/docs/payments/set-up#set-up-a-razorpay-account-and-complete-kyc).
* You have international payments enabled. Know more about [International Payments](https://razorpay.com/docs/payments/international-payments).
* We have set reserve terms for your account based on your account profile.

Reserves apply only to international payments. Your domestic payments settle on your normal [settlement cycle](https://razorpay.com/docs/payments/settlements#settlement-cycle).

## How it Works

The reserve sits between the payment we capture and the amount we settle to you:

1. You accept an international payment. We capture it as usual.
2. We calculate the reserve on the amount remaining after our fees and taxes.
3. We hold either a percentage of the payment or the whole payment, depending on your terms.
4. We settle the remainder on your normal settlement cycle.
5. We release the held amount to your balance on its scheduled release date. The released amount then settles on your normal cycle.

## Types of Reserves

You are on one reserve type at a time, never both. The table below lists how the two types differ:

| Reserve Type | How Much We Hold | How It Comes Back |
| - | - | - |
| [Rolling reserve](#rolling-reserve) | A percentage of each payment in scope, or the whole payment | We release each held amount on its own date, one at a time |
| [Fixed reserve](#fixed-reserve) | A percentage of each payment until a target amount is reached, then nothing | We return the whole balance in one go, once we decide it is no longer needed |

## Rolling Reserve

Your rolling reserve depends on the payments it applies to, and on how much we hold and for how long.

### Payments in Scope

Some international payments are verified by the customer's bank before they go through. Others are not. Unverified payments are easier for your customers to complete. They are also more likely to be disputed later. These are your **non-3DS payments**. Know more about [Support for Non-3D Secure Transactions](https://razorpay.com/docs/payments/international-payments/support-non-3ds.md).

A reserve can apply to any of your international payments. Which ones it covers depends on your account profile. For some accounts it is only the non-3DS payments, for others it is all international payments. Your terms tell you which applies to you, and your Dashboard shows which of your payments contributed to the reserve.

### Hold Amount and Period

We hold either a percentage of each payment in scope, for example 30%, or the whole payment. The hold period is up to 75 days.

### Examples

Your settlement cycle is T+7, so a payment you take on day 1 reaches you on day 8. On day 1 you take 7 international payments adding up to ₹6,00,000. Of these, 5 are 3DS payments of ₹1,00,000 each and 2 are non-3DS payments of ₹50,000 each.

We calculate reserves on the amount remaining after our fees and taxes. The tables below ignore fees and taxes to keep the arithmetic readable.

> [accordion] Example 1: We hold your non-3DS payments in full, for 60 days
>
> The table below lists what happens to each payment:
>
> | Payment | Amount | Held | Settles on Day 8 | Released to Your Balance |
> | - | - | - | - | - |
> | 1 to 5 (3DS) | ₹1,00,000 each | None | ₹1,00,000 each | None |
> | 6 (non-3DS) | ₹50,000 | ₹50,000 | None | ₹50,000 on day 61 |
> | 7 (non-3DS) | ₹50,000 | ₹50,000 | None | ₹50,000 on day 61 |
> | **Total** | **₹6,00,000** | **₹1,00,000** | **₹5,00,000** | **₹1,00,000** |
>
> Only payments 6 and 7 are affected. They reach you about 2 months later than usual. The other 5 settle on day 8.

> [accordion] Example 2: We hold 40% of your non-3DS payments, for 45 days
>
> Same 7 payments, but we hold only part of each non-3DS payment. The table below lists what happens to each payment:
>
> | Payment | Amount | Held | Settles on Day 8 | Released to Your Balance |
> | - | - | - | - | - |
> | 1 to 5 (3DS) | ₹1,00,000 each | None | ₹1,00,000 each | None |
> | 6 (non-3DS) | ₹50,000 | ₹20,000 | ₹30,000 | ₹20,000 on day 46 |
> | 7 (non-3DS) | ₹50,000 | ₹20,000 | ₹30,000 | ₹20,000 on day 46 |
> | **Total** | **₹6,00,000** | **₹40,000** | **₹5,60,000** | **₹40,000** |
>
> You receive ₹30,000 of each non-3DS payment on day 8 and the remaining ₹20,000 about 6 weeks later. Your 3DS payments are unaffected.

> [accordion] Example 3: We hold 30% of every international payment, for 30 days
>
> Here the reserve covers your whole international volume, not only the non-3DS part of it. The table below lists what happens to each payment:
>
> | Payment | Amount | Held | Settles on Day 8 | Released to Your Balance |
> | - | - | - | - | - |
> | 1 to 5 (3DS) | ₹1,00,000 each | ₹30,000 each | ₹70,000 each | ₹30,000 each on day 31 |
> | 6 (non-3DS) | ₹50,000 | ₹15,000 | ₹35,000 | ₹15,000 on day 31 |
> | 7 (non-3DS) | ₹50,000 | ₹15,000 | ₹35,000 | ₹15,000 on day 31 |
> | **Total** | **₹6,00,000** | **₹1,80,000** | **₹4,20,000** | **₹1,80,000** |
>
> We hold no payment in full, and you have all of it back within a month.

## Fixed Reserve

A fixed reserve has a target amount. A percentage of each payment goes towards the target. Once the target is reached, we stop holding and every payment after that settles in full. This caps how much of your money we ever hold.

A fixed reserve also comes back differently. A rolling reserve releases one amount at a time. A fixed reserve sits as a single balance. We return it in one go, once we decide it is no longer needed. We review reserves on our own initiative. Where your business performs well, we may lower the target or lift the reserve altogether. A waiting period applies once that happens, and your terms tell you how long it is.

> [accordion] Example: We hold 10% of each payment until a ₹4,50,000 fixed reserve is built
>
> Your payments come in at different sizes, so 10% of each is a different amount. The table below lists how the reserve balance builds up:
>
> | Payment | Held | Reserve Balance | Settles on Normal Cycle |
> | - | - | - | - |
> | ₹2,00,000 | ₹20,000 | ₹20,000 | ₹1,80,000 |
> | ₹75,000 | ₹7,500 | ₹27,500 | ₹67,500 |
> | ₹3,20,000 | ₹32,000 | ₹59,500 | ₹2,88,000 |
> | ... | ... | ... | ... |
> | ₹1,10,000 | ₹11,000 | ₹4,42,000 | ₹99,000 |
> | ₹1,50,000 | ₹8,000 | **₹4,50,000, target met** | ₹1,42,000 |
> | ₹90,000 | ₹0 | ₹4,50,000 | ₹90,000 |
>
> We take only what the target still needs. On the ₹1,50,000 payment, 10% would have been ₹15,000, but only ₹8,000 was still needed. The reserve never goes past ₹4,50,000, and every payment after that settles in full.

## View Your Reserve Balance

Log in to the [Razorpay Dashboard](https://dashboard.razorpay.com/) and navigate to **Settlements**. Your balance appears as:

* **Total balance**: everything in your account.
* **Live balance**: available to settle.
* **Reserve balance**: currently held.

To see each hold, go to **Transactions** and open the **Reserves** tab. It lists each held amount, the payment it came from and the date we release it.

Your active reserve terms appear under **Account & Settings** → **International payments**. These terms cover the percentage, the payments the reserve covers and the hold period.

Download your settlement and reserve reports to reconcile: amount processed, less amount held, equals amount settled. Know more about [settlement reports](https://razorpay.com/docs/payments/settlements/dashboard.md#reports).

## How We Review Reserves

We review every reserve periodically, usually every 3 to 6 months. As your account performance improves, we can reduce your reserve, narrow its scope or remove it.

Any change applies to payments from that point onward. Amounts we already hold stay on their original release schedule.

To reduce the chances of a reserve being placed or increased:

* Deliver promptly and share tracking details with your customers.
* Keep customers informed about delays or changes to their order.
* Keep your dispute rate below 1% of your sales.
* Process refunds quickly rather than letting complaints build up.

## Frequently Asked Questions (FAQs)

> [accordion] Is a reserve a fee or a charge?
>
> No. It is your money. We hold it temporarily and release it to you after deducting any disputed amounts it covers. We charge no fee on it.

> [accordion] Do I earn interest on money held in reserve?
>
> No. We hold the funds as a buffer, not as a deposit.

> [accordion] Why is my settlement lower than the payment amount?
>
> The reserve sits between the two. Your settlement report shows the amount processed, the amount held and the amount settled, so the two tie back.

> [accordion] Will all my international payments be delayed?
>
> Not necessarily. Which payments your reserve covers depends on your account profile. For some accounts it is only the non-3DS payments, for others it is all international payments. Payments outside your reserve settle on your normal cycle. Your terms tell you which applies to you, and your Dashboard shows which of your payments contributed to the reserve.

> [accordion] Which of my payments contributed to my reserve?
>
> Every held amount in your **Reserves** tab links back to the payment it came from. Use it to see which payments contributed and when we release each one.

> [accordion] Can I choose which setup applies to me?
>
> No. We set your terms based on your account profile.

> [accordion] Can I refund a customer using my reserve balance?
>
> No. We pay refunds from your live balance, or from refund credits if your live balance is short. Your reserve stays in place to cover disputes. If you refund often, keep enough live balance or refund credits available.

> [accordion] What happens if a dispute comes in?
>
> We debit the disputed amount from your live balance, as we do today. If your live balance does not cover it, we recover the shortfall from your next payments. We also take it from your reserve when we release it.

> [accordion] Will the reserve be there forever?
>
> No. We review reserves periodically and can reduce or remove them as your account performance improves.

> [accordion] What happens if I turn off international payments?
>
> We hold no further amounts. We release anything already held on its existing schedule, so those payments stay covered for any disputes raised later.

> [accordion] What happens to held funds if I close my account?
>
> We hold them for a period to cover any late disputes. We then release the balance to your registered bank account.

> [accordion] Am I exposed to exchange rate movement on held funds?
>
> No. We hold reserves in INR, after we convert your payment. The amount we hold and the amount we release are the same.

> [accordion] My FIRS shows a higher amount than what reached my bank account. Why?
>
> We issue your FIRS on the full amount received from abroad and converted to INR, which is correct. The remittance did come in. Part of it sits in your reserve and settles to you later. For that period the FIRS reads higher than your bank credits.
>
> Your Internal FIRS bridges the two. It carries the amount currently held and the date we release it, alongside the settlement date and UTR for each entry. Use it to reconcile what was realised against what reached your account. Submit it with your FIRS when you claim export benefits. Regenerate the Internal FIRS once all the settlements for a month have gone through, so the mapping is complete. Know more about the [FIRS Automated Process](https://razorpay.com/docs/payments/international-payments/firs-automated-process.md).

> [accordion] Can I have both a rolling reserve and a fixed reserve?
>
> No. Only one applies to your account at a time.

### Related Information

* [Accept Payments Above Your Transaction Limit](https://razorpay.com/docs/payments/international-payments/over-limit-transactions.md)
* [Support for Non-3D Secure Transactions](https://razorpay.com/docs/payments/international-payments/support-non-3ds.md)
* [About Settlements](https://razorpay.com/docs/payments/settlements)
* [Settlement FAQs](https://razorpay.com/docs/payments/settlements/faqs.md)
