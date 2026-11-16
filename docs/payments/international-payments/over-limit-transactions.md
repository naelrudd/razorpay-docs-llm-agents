> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Accept Payments Above Your Transaction Limit

> Know how we accept and hold international card payments above your transaction limit instead of declining them, and how long we hold each one.

Available in
🇮🇳 India

International card payments above your transaction limit are no longer declined. We accept and hold the payment for a set period, then settle it to you.

A ceiling still applies. We decline any payment above your ceiling, as we did before. Your ceiling is set for your account and is usually higher than your limit. Most large payments that used to fail now reach you.

Your customer sees no difference. The payment succeeds as normal.

> [!NOTE]
>
> **Handy Tips**
>
> Every amount, percentage and hold period on this page is an example. Your own terms appear in your Razorpay Dashboard.

## Prerequisites

Over-limit payments apply to your account when:

* Your account is KYC approved and fully activated. Know more about [KYC Verification](https://razorpay.com/docs/payments/set-up#set-up-a-razorpay-account-and-complete-kyc).
* You have international payments enabled. Know more about [International Payments](https://razorpay.com/docs/payments/international-payments).
* We have enabled over-limit payments on your account and set your limits, hold periods and ceiling.

These limits and holds apply only to international card payments. Your domestic payments are unaffected, and their [transaction limits](https://razorpay.com/docs/payments/payment-methods/transaction-limits.md) are unchanged.

## Use Cases

* A customer places an order larger than your usual ticket size. Earlier we declined the payment. Now we accept it, hold it and settle it to you.
* You run a seasonal or high-value campaign where order values rise above your normal limit. Your customers complete payment as usual instead of seeing a failure.

## Your Transaction Limits

**Your limit** decides when we hold a payment. Above it, the payment still goes through. It only takes longer to settle.

**Your ceiling** decides whether we accept the payment at all. Above it, we decline the payment and it never reaches you.

You have 2 limits. One covers your **non-3DS payments**, which the customer's bank did not verify before they went through. The other covers your 3DS payments and is the higher of the two. A single ceiling sits on top of both. Know more about [Support for Non-3D Secure Transactions](https://razorpay.com/docs/payments/international-payments/support-non-3ds.md).

## How it Works

1. Your customer makes an international card payment above your transaction limit.
2. We accept and capture the payment as usual.
3. We hold the full payment for a set number of days. The period depends on which limit the payment crossed.
4. We release the amount to your balance on the release date.
5. The released amount settles on your normal settlement cycle.

We decline any payment above your ceiling at step 1, so it never reaches your balance.

## Hold Periods for Over-Limit Payments

For this section, take an account with the terms in the table below:

| Category | Amount |
| - | - |
| Limit on non-3DS payments | ₹3,00,000 |
| Limit on your 3DS payments | ₹5,00,000 |
| Ceiling | ₹20,00,000 |

The table below lists how long we hold a payment on this account:

| The Payment | What Happens |
| - | - |
| Over ₹3,00,000, if it is a non-3DS payment | We hold it for 90 days, then it settles |
| Over ₹5,00,000, if it is one of your 3DS payments | We hold it for 60 days, then it settles |
| Over ₹20,00,000 | We decline it |

We hold non-3DS payments for longer because disputes on them are more likely.

Keep these points in mind:

* **We hold the whole payment, not only the amount above your limit.** On a ₹6,00,000 3DS payment against a ₹5,00,000 limit, we hold all ₹6,00,000, not the ₹1,00,000 above the limit.
* **The hold period does not change with the amount.** A payment slightly above your limit is held for exactly as long as one well above it. The period depends on which limit the payment crossed, not by how much.

> [accordion] Example: 6 payments taken on day 1
>
> Your settlement cycle is T+7, so anything settling normally reaches you on day 8. The table below lists what happens to each payment:
>
> | S. No. | Payment | Amount | What Happens |
> | - | - | - | - |
> | 1 | 3DS | ₹2,00,000 | Within the limit. Settles on day 8. |
> | 2 | Non-3DS | ₹2,50,000 | Within the limit. Settles on day 8. |
> | 3 | Non-3DS | ₹4,00,000 | Above the ₹3,00,000 limit. Held in full, released on day 91. |
> | 4 | Non-3DS | ₹8,00,000 | Above the ₹3,00,000 limit. Held in full, released on day 91. |
> | 5 | 3DS | ₹8,00,000 | Above the ₹5,00,000 limit. Held in full, released on day 61. |
> | 6 | 3DS | ₹22,00,000 | Above the ₹20,00,000 ceiling. Declined. |
>
> Payments 1 and 2 behave as they did before. We would have declined payments 3, 4 and 5 before this change, and they now reach you, only later than usual. We still decline payment 6.
>
> Payments 3 and 4 differ in size but wait the same length of time. Payment 3 is smaller than payment 5 yet waits a month longer. It crossed the non-3DS limit, which carries the longer hold.

## When Your Non-3DS Payments Have a Lower Limit

If you asked us to enable non-3DS payments, they usually carry their own limit. That limit is lower than the one on the rest of your payments. Payments between that limit and your ceiling still go through.

These payments are not held. They settle on the timeline set for that band, which is longer than your normal cycle. The timeline depends on your terms.

The two accounts below show the range. Both carry their own limits and their own ceiling, different from the account used above.

> [accordion] Example 1: Your non-3DS payments settle on your normal cycle
>
> The table below lists the terms on this account:
>
> | Configuration | Your 3DS Payments | Your Non-3DS Payments |
> | - | - | - |
> | Limit | ₹5,00,000 | ₹3,00,000 |
> | Settlement timeline within its limit | T+7 | T+7 |
> | Settlement timeline in the band above its limit | None | 60 days |
> | Ceiling | ₹5,00,000 | ₹5,00,000 |
>
> The table below lists when each payment settles:
>
> | Payment Amount | If It Is One of Your 3DS Payments | If It Is a Non-3DS Payment |
> | - | - | - |
> | Up to ₹3,00,000 | Settles on day 8 | Settles on day 8 |
> | ₹3,00,001 to ₹5,00,000 | Settles on day 8 | Settles on day 61 |
> | Above ₹5,00,000 | Declined | Declined |
>
> Below ₹3,00,000 every payment settles on day 8. Only the ₹3,00,000 to ₹5,00,000 band behaves differently, and only for non-3DS payments.
>
> On this account the ceiling equals the limit on your 3DS payments. We therefore never hold a 3DS payment here. We decline it above ₹5,00,000.

> [accordion] Example 2: Your non-3DS payments already settle on a longer cycle
>
> Some accounts carry a [reserve](https://razorpay.com/docs/payments/settlements/reserves.md) on their non-3DS payments, so those payments settle on a longer cycle to begin with. The lower limit then sits inside that longer cycle. A payment in the band waits longer still, rather than waiting twice.
>
> The table below lists the terms on this account:
>
> | Configuration | Your 3DS Payments | Your Non-3DS Payments |
> | - | - | - |
> | Limit | ₹5,00,000 | ₹3,00,000 |
> | Settlement timeline within its limit | T+7 | T+50 |
> | Settlement timeline in the band above its limit | None | 120 days |
> | Ceiling | ₹5,00,000 | ₹5,00,000 |
>
> The table below lists when each payment settles:
>
> | Payment Amount | If It Is One of Your 3DS Payments | If It Is a Non-3DS Payment |
> | - | - | - |
> | Up to ₹3,00,000 | Settles on day 8 | Settles on day 51 |
> | ₹3,00,001 to ₹5,00,000 | Settles on day 8 | Settles on day 121 |
> | Above ₹5,00,000 | Declined | Declined |
>
> As in Example 1, the ceiling equals the limit on your 3DS payments. We therefore never hold a 3DS payment on this account.

In both examples, read the middle row. A ₹4,00,000 3DS payment sits inside the ₹5,00,000 limit and settles on day 8. The same ₹4,00,000 as a non-3DS payment falls in the band above ₹3,00,000 and settles later. The group the payment falls into decides the outcome, not its size.

## Raise Your Transaction Limit

Raise a support request from your Razorpay Dashboard to increase your transaction limit or your ceiling. We review your account and your use case before deciding, and may ask you for additional documents.

If we accept the request, your new limits and hold periods apply from that point. Raising your limit also raises your ceiling, because we work out the ceiling from your limit.

## Turn Off Over-Limit Payments

Raise a support request from your Razorpay Dashboard to turn this off. Once we action it, we decline over-limit international card payments and hold nothing, as we did before. Raise another request whenever you want it turned back on.

We may also turn it off on your account, for example where compliance or risk requirements call for it.

## Notifications

We email you when:

* We approve your request to raise your limit or your ceiling. The email confirms your new limits and hold periods.
* We turn off over-limit payments on your account.

## View Your Limits and Held Payments

Your Razorpay Dashboard shows your current limits and your ceiling under **Settings**. Any held amount appears under **Settlements**, with the date we release it. Each held payment links back to the payment it came from. Use it to see which payments are waiting and when we release each one.

Your settlement report shows the amount held against each settlement, so your books tie back. Know more about [settlement reports](https://razorpay.com/docs/payments/settlements/dashboard.md#reports).

## Frequently Asked Questions (FAQs)

> [accordion] Is there an amount you still decline?
>
> Yes. We decline anything above your ceiling. Your ceiling appears in your Razorpay Dashboard alongside your limits.

> [accordion] What is the difference between my limit and my ceiling?
>
> Your limit affects **when** you get the money. Your ceiling affects **whether** you get it. We accept a payment above your limit and settle it to you, only later than usual. We decline a payment above your ceiling.

> [accordion] Do you hold the whole payment, or only the part above my limit?
>
> The whole payment. On a ₹6,00,000 payment against a ₹5,00,000 limit, we hold all ₹6,00,000, not ₹1,00,000.

> [accordion] Why do you hold two payments of similar size for different lengths of time?
>
> Because they crossed different limits. Non-3DS payments carry a lower limit and a longer hold. Your Razorpay Dashboard shows which of your payments fell into which group.

> [accordion] Does the hold get longer the further above the limit I go?
>
> No. It is the same whether you are ₹1,000 above or ₹5,00,000 above.

> [accordion] Will my customer know anything is different?
>
> No, unless the payment is above your ceiling, in which case it fails as it would have before. Otherwise the payment goes through normally, and the hold affects only when the money reaches you.

> [accordion] Is the held amount a fee?
>
> No. It is your money. We hold it temporarily and settle it to you in full. We charge no fee on it and nothing accrues on it.

> [accordion] Does this apply to my domestic payments?
>
> No. These limits and holds apply only to international card payments.

> [accordion] Can I ask for an over-limit payment to be released early?
>
> Raise a request from your Razorpay Dashboard. Early release is at our discretion. We look at each request case by case, against the payment, your account history and your dispute record. If we approve it, the amount joins your normal settlement pipeline rather than being paid out immediately.

> [accordion] What happens if I need to refund the payment before it settles?
>
> We pay refunds from your live balance or your refund credits. You cannot refund from a held payment until we release it. Keep enough live balance available if you expect to refund large payments.

> [accordion] Can I have this turned off permanently?
>
> Yes. Raise a support request and we will turn it off, after which we decline over-limit payments as we did before.

### Related Information

* [Reserves on International Payments](https://razorpay.com/docs/payments/settlements/reserves.md)
* [Support for Non-3D Secure Transactions](https://razorpay.com/docs/payments/international-payments/support-non-3ds.md)
* [Transaction Limits for Payment Methods](https://razorpay.com/docs/payments/payment-methods/transaction-limits.md)
* [About Settlements](https://razorpay.com/docs/payments/settlements)
