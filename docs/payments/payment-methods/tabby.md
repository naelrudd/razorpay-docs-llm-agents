> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Tabby — BNPL Payment Method for UAE Customers

> Accept BNPL payments from UAE customers via Tabby Pay on Razorpay Standard Checkout. Split purchases into 4 interest-free AED payments or pay over time for up to 12 months.

Tabby is the leading Buy Now, Pay Later (BNPL) platform in the UAE and KSA. Enabling Tabby at checkout enables UAE customers to split their purchase into 4 interest-free payments or up to 12 months, for cart values over AED 2,000 with no late fees or interest, using a payment method they already know and trust.

Razorpay manages the end-to-end integration with Tabby. No separate contract with Tabby is required.

> [!NOTE]
>
> **Handy Tips**
>
> * Pay Later (Short Term Credit) is provided by Tabby LLC. Terms and conditions apply. Visit [tabby.ai](https://tabby.ai) for more information.
> * Tabby is currently available for **UAE** customers. Saudi Arabia support is coming soon.
> * Razorpay's [pay in native currency](https://razorpay.com/docs/payments/payment-methods/cards/dynamic-currency-conversion.md) feature ensures your UAE customer sees the amount in AED at checkout.

## Advantages

Merchants who enable Tabby report measurable uplift across key checkout metrics:

* **Higher Conversion Rate**: Customers who see BNPL at checkout are more likely to complete the purchase.

* **Reduced Card Abandonment**: When your customer sees Tabby at checkout, they likely already have an account and can complete payment in under 60 seconds.

* **Flexible Order Value Range**: Tabby can be used by your customers for a wide range of order values for a single order, depending on merchant category. For additional limits, please contact your Account Manager or [Razorpay Support](https://razorpay.com/support/).

## Prerequisites

Before enabling Tabby, ensure the following:

* Active Razorpay account with **International Payments** enabled.
* **KYB (Know Your Business)** verification completed on the Razorpay Dashboard.
* You are a **PFB (Platform Fee Bearer)** merchant. This means Razorpay's platform fees are borne by you (the merchant), not passed to the customer.

> [!NOTE]
>
> **Handy Tips**
>
> Merchants onboarded to Razorpay after January 2026 do not need to complete a separate KYB verification as your existing onboarding covers it. You just have to activate it on your Razorpay Dashboard.

## Restricted Categories

Tabby is not available for the following merchant categories. If your MCC falls in a restricted category, Tabby will not appear for activation on your Dashboard.

| Restricted Category | Examples |
| - | - |
| Gambling, Betting | Online casinos, sports betting, lotteries |
| Adult Content | Adult entertainment, dating services |
| Tobacco, Vaping | Cigarettes, e-cigarettes, vape products |
| Weapons, Ammunition | Firearms, knives, ammunition |
| Cryptocurrency | Crypto exchanges, NFT platforms, token sales |

## How to Enable Tabby

Tabby is activated via self-serve on the Razorpay Dashboard.

1. Log in to the [Razorpay Dashboard](https://dashboard.razorpay.com).
2. Navigate to **Settings → Payment Methods → International**.
3. Locate the **Tabby** row and click **Enable**.
4. Complete KYB verification if prompted.
5. Once approved, Tabby appears automatically in your checkout for eligible UAE customers.

> [!NOTE]
>
> **Handy Tips**
>
> Approval typically takes up to one week. Track your activation status on the same Dashboard page.

## Customer Eligibility

Tabby appears at checkout only when the customer meets all of the following conditions:

* Customers must have a UAE mobile number (+971) and pass Tabby's eligibility check.
* Wide range of order values range based on merchant category. Customers will pay in AED only.
* Real-time eligibility check by Tabby, instant and invisible to the customer.

## How It Works

Tabby works like any other payment method on Razorpay Checkout:

1. [Create Order](https://razorpay.com/docs/api/orders/create.md) with the required details.
2. Customer provides details such as name, email, phone and shipping address.
3. Customer completes payment on Tabby. Customer is redirected to Tabby's secure page for OTP verification and approval (if details were not passed during the order creation).
4. Razorpay auto-captures the payment. You receive a `payment.captured` webhook. No manual action required.
5. Customer is redirected to your success or failure page. Order is confirmed.

![Tabby as a Payment Method on Razorpay Checkout for UAE customers](https://mintlify.s3.us-west-1.amazonaws.com/razorpay-881012b3/assets/images/tabby-checkout.jpg)

## Create an Order for Tabby

When creating a Razorpay order that may be paid via Tabby, pass buyer information, shipping address, and line item data in your order API call. Tabby uses this data for real-time credit scoring. The more complete the data, the higher the approval rate.

Parameters without the *optional* tag are mandatory. Optional parameters are recommended for higher approval rates.

> [accordion] Order-Level Fields
>
> `amount`
> : `integer` Order amount in paise (INR). Razorpay converts to AED at checkout.
>
> `currency`
> : `string` The currency of the order. Razorpay automatically displays and collects the payment in AED on the checkout, converting at the time of the transaction.

> [accordion] Buyer Fields
>
> Passed via `notes` or `customer_details` in the Order API. If missing, Razorpay collects these from the customer inline at checkout.
>
> `phone`
> : `string` Customer phone with country code. For example, `+971501234567`.
>
> `name` *optional*
> : `string` Customer full name. Recommended for higher approval rates.
>
> `email` *optional*
> : `string` Customer email address. Recommended for higher approval rates. This information will be collected during checkout, if not passed here.

> [accordion] Address Fields
>
> Passed via `customer_details`. For platform merchants (Shopify, Magento), plugin data is used as a fallback.
>
> `shipping_address.city` *optional*
> : `string` Shipping city name. For example, `Dubai`. This information will be collected during checkout, if not passed here.
>
> `shipping_address.address` *optional*
> : `string` Street address, building name, apartment number.
>
> `shipping_address.zip` *optional*
> : `string` Postal or ZIP code.
>
> `billing_address` *optional*
> : `object` Billing address (city, address, zip). This information will be collected during checkout, if not passed here.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > For orders with no physical shipping, pass a shipping address and set `is_virtual = true` on each line item. This signals to Tabby that the shipping address is a billing address.

> [accordion] Line Items
>
> Passed via `line_items` in the Order API.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Do not use the `products` section of the Orders API.
>
> `line_items[].name` *optional*
> : `string` Product name or title.
>
> `line_items[].title` *optional*
> : `string` Display title (can be the same as `name`).
>
> `line_items[].unit_price` *optional*
> : `string` Unit price of the item.
>
> `line_items[].quantity` *optional*
> : `integer` Quantity ordered. Must be ≥ 1.
>
> `line_items[].category` *optional*
> : `string` Product category. For example, `Fashion` or `Electronics`. Used for risk scoring.
>
> `line_items[].product_id` *optional*
> : `string` SKU or product reference id.

## Webhooks

All Tabby payments are auto-captured. No manual capture step is required from your end. You receive standard Razorpay webhooks for each transaction.

| Status | Description | Webhook Event |
| - | - | - |
| `captured` | Payment captured successfully. Settlement to follow. | `payment.captured` |
| `failed` | Payment failed or customer rejected by Tabby. Alternate payment methods are shown. | `payment.failed` |
| `refund.created` | Refund has been initiated. | `refund.created` |
| `refund.processed` | Refund completed successfully. | `refund.processed` |

Configure webhooks under **Dashboard → Settings → Webhooks**. The `method` field in webhook payloads will show `tabby`.

## Settlement

Tabby payments are settled to your registered bank account on a **T+11 to T+13** cycle from the date of customer payment, in **INR**.

You receive the full captured amount (minus applicable MDR) regardless of whether the customer completes all future payments. Tabby absorbs the instalment risk entirely.

## Refunds

Both full and partial refunds are supported. Refunds are processed in INR. Refer to the table below to understand the refund rules.

| Rule | Details |
| - | - |
| Time limit | Refunds must be initiated within 180 days from the original payment creation date. |
| Minimum balance | Refunds are processed only when your running Tabby transaction volume exceeds the refund amount. If your Tabby balance is insufficient, the refund cannot be processed until new Tabby transactions bring the balance above the required amount. |
| Full refund | Entire order amount is refunded after deducting the applicable charges levied by Tabby. Use for cancellations, defective items or incorrect products. |
| Partial refund | A portion of the order is refunded after deducting the applicable charges levied by Tabby. Use for multi-item orders where some items are returned. |

To process a refund:

1. Go to **Dashboard → Transactions**
2. Select the Tabby transaction
3. Click **Process Refund via Tabby**.

> [!WARNING]
>
> **Watch Out!**
>
> If the refund amount exceeds your current running Tabby balance, the refund option will be greyed out. You will need to wait until transaction volume accumulates sufficiently before the refund can be processed.

## Testing

1. Switch to **Test Mode** in the Razorpay Dashboard.
2. Create a test order within the permitted amount range.
3. On the Checkout page, select **Tabby** and complete the test flow.
4. Verify the payment status via Dashboard and webhook.

> [!NOTE]
>
> **Handy Tips**
>
> Test mode simulates both approved and rejected scenarios. Use the test phone numbers provided in the Dashboard to trigger specific outcomes.

## Frequently Asked Questions (FAQs)

> [accordion] 1. Why is Tabby not showing in my checkout?
>
> Tabby appears only for eligible UAE customers (detected at Razorpay checkout) and within the supported order value range. Verify your Tabby activation status under **Settings → Payment Methods → International** on the Dashboard.

> [accordion] 2. How is customer eligibility determined?
>
> Tabby runs a real-time scoring check using the customer's phone, email and device signals. This is invisible to the customer and takes under 2 seconds. If rejected, a generic message is shown and alternate payment methods are offered automatically. Passing more order details when creating the order significantly improves approval rates.

> [accordion] 3. When do I get paid?
>
> Settlement follows a T+11 to T+13 cycle from the date of customer payment, in INR to your registered bank account. See [Settlement](#settlement) for details.

> [accordion] 4. Why can't I process a refund?
>
> Refunds require that your running Tabby transaction volume exceeds the refund amount. If your current Tabby balance is insufficient, the refund option will not be available. Additionally, refunds must be initiated within 180 days of the payment creation date. See [Refunds](#refunds) for details.

> [accordion] 5. Why was the customer rejected by Tabby?
>
> Tabby's underwriting is independent and specific rejection reasons are not shared with merchants. Razorpay shows a generic error and automatically offers alternate payment methods to the customer.

> [accordion] 6. What if the customer does not complete all payments?
>
> Tabby absorbs 100% of the instalment risk. You receive the full captured amount (minus applicable MDR) regardless of whether the customer completes subsequent payments.
