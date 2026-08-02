# Import Flow Recurring Payments API

Import Flow is a payment solution designed for International (non-Indian) businesses to accept payments from Indian customers without any additional paperwork or registration. 

Your Indian customers can make recurring payments via local payment methods such as cards and UPI. The funds are settled in your overseas bank account. Know more about [Import Flow](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers.md).

**INFO**

**Feature Request**

This is an on-demand feature. Please raise a request with our [Support team](https://razorpay.com/support/#request) to get this feature activated on your Razorpay account.

 to get this feature activated on your account.

Recurring Payments lets you charge your customers automatically on a schedule, whether daily, weekly, monthly or yearly, without them having to pay again each time. The customer authorises once. You debit whenever you need to.

## What are Recurring Payments?

Think of any service where a customer pays regularly: a streaming subscription, a gym membership, a loan EMI or a SIP investment. These businesses do not ask their customers to manually transfer money every month. Instead, they collect it automatically, on a fixed schedule, from the payment method the customer set up once.

That is exactly what Razorpay Recurring Payments lets you build. Your customer authorises their UPI ID, card or bank account once. Razorpay creates a mandate, a standing instruction, and from that point forward you control when to debit them. No customer action is required for subsequent payments (unless the amount crosses AFA limits, more on that in [AFA limits](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers/standard-integration/recurring-payments.md#afa-limits)).

**INFO**

**How is this different from EMI?**

EMI (Equated Monthly Instalment) is a financing arrangement where a bank or NBFC lends money and the borrower repays in fixed instalments. Recurring Payments is the payment collection mechanism: it is how lenders actually collect those EMI payments from the borrower's bank account automatically. You are not lending money. You are building the rails to collect what is owed. EMI is the use case. Recurring Payments is how it gets done.

### When should you use Recurring Payments instead of one-time payments?

One-time payments are great for individual purchases: a user pays, you deliver, done. But if your business model depends on customers paying you regularly, one-time payments create friction at every billing cycle. The customer might forget, ignore the payment request or just churn. Recurring Payments eliminates that friction entirely.

Use Recurring Payments when:

- You charge customers on a defined schedule (monthly, quarterly, annually).
- Your revenue depends on customers staying subscribed and drop-offs hurt.
- You are collecting loan repayments, SIP investments or insurance premiums where debit reliability is critical.
- You want to automate billing so your team is not manually chasing payments.

### What is Inside a Mandate

Every mandate has four key parameters that you define at setup time. These are locked once the mandate is registered. You cannot change them later without creating a fresh mandate.

  - **Max Amount (token.max_amount)**: The maximum amount that can be debited in a single charge. The customer sees this at approval time. Individual debits must not exceed this value.

  - **First Payment (order.amount)**: The amount debited during mandate registration to activate the mandate. The minimum amount is ₹1 for UPI and Cards, and ₹0 for eMandate. Without a successful first payment, the mandate is not confirmed.

  - **Frequency (token.frequency)**: How often the customer can be debited: daily, weekly, monthly, quarterly, yearly or as_presented. For UPI, NPCI enforces this strictly. Only one debit per frequency cycle is allowed.

  - **Expiry (token.expire_at)**: When the mandate expires, as a Unix timestamp. After this date, no further debits can be collected. Defaults to 10 years if not set. Maximum 30 years for UPI.

**INFO**

**Handy Tips**

Every registered mandate is uniquely identified by a `token_id` issued by Razorpay. This is the key you use for all future debit calls. Before attempting any debit, always check the token's current state: debiting against a paused or cancelled token will fail. Store the `token_id` securely against the customer record in your system.

## Common Use Cases

Recurring Payments is used across industries wherever predictable, scheduled collections matter.

  - **OTT and Streaming**: Monthly subscriptions for streaming platforms, auto-debited with zero friction.

  - **Loan EMIs**: NBFCs and lending apps collect repayments automatically from the borrower's bank account or UPI.

  - **SIP Investments**: Mutual fund platforms collect monthly SIP amounts without the customer needing to approve each time.

  - **Insurance Premiums**: Annual or quarterly premium collection, auto-debited from the policyholder's account.

  - **SaaS and B2B**: Monthly or annual software subscriptions billed automatically to the customer's card.

  - **Memberships**: Gyms, clubs and learning platforms billing monthly or annually without manual renewals.

  - **Utility Bills**: Electricity, broadband and gas bills auto-collected from the customer's registered payment method.

  - **Meal Plans and D2C**: Weekly or monthly meal subscription deliveries billed at a fixed cadence.

## How a Merchant Sets This Up

Here is what the end-to-end flow looks like when a customer signs up for a monthly subscription on your platform.

1. **Customer picks a plan and billing frequency**: Your customer selects a plan and chooses to pay via UPI Autopay, card or bank account. Supported frequencies include `daily`, `weekly`, `monthly`, `quarterly` and `yearly`.
1. **Your server creates an order with mandate details**: You tell Razorpay the max amount, the billing frequency and when the mandate should expire. Razorpay prepares an authorisation payment for the customer. `POST /v1/orders`
1. **Customer approves the mandate, once**: The customer is taken to their UPI app, card form or netbanking portal to approve the mandate. A small first payment (₹1 for UPI and cards, ₹0 for eMandate) is collected to activate it. This is the only time the customer needs to take action. On success, a `token_id` is generated.
1. **Mandate confirmed, you are ready to charge**: Razorpay sends you a `token.confirmed` webhook. The mandate is active. From this point, you debit the customer on your schedule with no customer action required. `webhook: token.confirmed`
1. **You debit automatically on each billing date**: On the scheduled date, your server creates a new order and triggers a payment using the `token_id`. Razorpay handles the debit in the background and notifies you when it is done. `POST /v1/payments/create/recurring` → `webhook: payment.captured`

## Performing Recurring Debits

Once the mandate is confirmed, all future debits are backend operations. You initiate them from your server with no customer interaction needed.

When you trigger a debit, Razorpay first sends a **Pre-Debit Notification (PDN)** to the customer through the issuing bank. This is an RBI-mandated notification that informs the customer of the upcoming debit, including the merchant name, amount and scheduled date. For UPI, this must be sent at least 24 hours before the actual debit. Razorpay handles this automatically.

After the PDN window, the actual debit happens backend. The customer's account is debited directly with no MPIN or OTP required, unless the amount exceeds the AFA limits set by RBI (see [AFA Limits](#afa-limits) below).

### Pre-Debit Notification Timeline

Timeline | Event
---
T + 0 | You call Create Order + Create Payment.
---
T + 0 to T + 24h | PDN sent to NPCI. Bank notifies the customer.
---
T + 25h | Debit executed (1-hour buffer after notification window).

 
### Step 1: Create a Debit Order

   Create a new order for every debit. The amount must not exceed the `max_amount` set at mandate registration. Set `payment_capture: true` for automatic capture. `POST /v1/orders`
  

 
### Step 2: Create the Recurring Payment

   Call the Recurring Payment endpoint with the `order_id`, `customer_id` and `token_id`. This is fully server-side. There is no UI and the customer is not redirected anywhere. Razorpay queues the debit, sends the PDN and executes the debit after the notification window. `POST /v1/payments/create/recurring`
  

 
### Step 3: Payment is confirmed

   Razorpay sends a `payment.captured` webhook when the debit succeeds. For UPI, this typically arrives 24 to 36 hours after you trigger the payment due to the PDN window. For Cards and eMandate, it is typically faster. Avoid creating another debit for the same token until you have received a terminal status (`payment.captured` or `payment.failed`) via webhook.
  

**WARN**

**Watch Out!**

Avoid creating a debit on the last day of the mandate's frequency cycle. Creating a subsequent payment on the last day of the cycle (for example, last day of the month for a monthly mandate) will fail because the pre-debit notification takes 24 hours and the actual debit attempt falls into the next billing cycle. Always allow at least one business day of buffer before the cycle resets.

## AFA Limits
 
AFA (Additional Factor of Authentication) is an extra layer of approval required for high-value recurring debits. When AFA is triggered, the customer receives a notification from their bank and must enter their UPI MPIN or card OTP before the debit is processed. This is an RBI mandate, not a Razorpay policy, and applies across all Recurring Payment methods.
 
For UPI Autopay, NPCI enforces both the **maximum mandate amount** you can register and the **per-debit silent threshold** below which AFA is not required. Two parameters drive the applicable limits:
 
- **Your Merchant Category Code (MCC)**: Assigned to your business by Razorpay during onboarding. The MCC determines both the maximum mandate amount you can register and the AFA-free per-debit threshold.
- **The mandate frequency**: Variable-amount mandates (`frequency: as_presented`) have lower maximum mandate ceilings than fixed-schedule mandates (`daily`, `weekly`, `monthly`, `quarterly`, `yearly`).

   
For most merchant categories, debits up to **₹15,000** are processed silently with no customer action needed. For debits above ₹15,000, the customer must approve via UPI MPIN before the debit executes.
 
   
   
For insurance, financial services, security brokers, grocery and a few other notified categories, debits up to **₹1,00,000** are processed silently per RBI directive and NPCI circular OC-151A (December 2023). See the MCC table below for the full list.
 
   

## Choose Your Integration Type

Your integration type determines who owns the payment UI and how your frontend and backend communicate with Razorpay. The tabs below explain each integration type in detail, including platform support and what your team will own.

   

**Razorpay-hosted UI. Least code. Fastest to go live.**

You initialise the Razorpay JavaScript SDK with an `order_id` and `customer_id`. Razorpay renders the full payment sheet, including UPI app selection, intent deep-linking, card form and netbanking redirect, and handles all the edge cases. You receive the result in a callback. You can set your brand colour, logo and name. The layout and payment method ordering are managed by Razorpay.

Platform | Support | Notes
---
Desktop web | Supported | Full support. Recommended integration path for web.
---
Mobile web (mWeb) | Supported | Full support. UPI intent works on Android mWeb.
---
Android SDK | Supported | Razorpay Android Standard SDK. Integrate via Maven.
---
iOS SDK | Supported | Razorpay iOS Standard SDK. UPI Collect is permitted on iOS (NPCI exemption).
---
React Native / Flutter | Supported | Use the Razorpay wrapper for your framework.
---
WebView | Partial | Works but not recommended. Requires extra configuration for UPI intent.

**WARN**

**Watch Out!**

WebView integration reuses web code but introduces issues with UPI intent, popup flows and bank page redirects. Use the Android or iOS SDK for native mobile apps.

   
   

**Your UI. Razorpay processes the payment behind it.**

You build your own payment screen, including UPI app selector, card input fields and bank list, and use the Razorpay JS library (`razorpay.js`) to initiate the payment in the background. Razorpay returns an intent URL or redirect URL that you handle. Full control over what the customer sees. Razorpay handles what they do not.

For UPI, always pass the TPAP name (for example, `gpay`, `phonepe`) in the `notes` object since you own the UPI app selection UI and know which app the customer chose. Razorpay uses this for routing and mandate quality analytics.

Platform | Support | Notes
---
Desktop and mWeb | Supported | Use `razorpay.js` + `createPayment()`.
---
Android SDK (Custom) | Supported | Use Razorpay Android Custom SDK for full UI control.
---
iOS Custom | Supported | Use Razorpay iOS Custom SDK. UPI Collect is permitted on iOS.
---
UPI Intent | Supported | You handle the intent URL returned in the API response.
---
Card recurring | Supported | Pass card details via `razorpay.js`. Never route raw card data through your server.

   
   

**Fully server-side. No client-side SDK. Maximum control.**

All communication with Razorpay is server-to-server. You call `POST /v1/payments/create/json` from your backend, receive an intent or redirect URL in the response and manage the entire redirect and callback flow on your own. No Razorpay JavaScript loads in the browser or app at all.

S2S card integration requires your business to be PCI-DSS compliant and explicitly approved by Razorpay since raw card data passes through your servers. For most merchants, Custom Checkout is the better path for card UI control without the compliance burden.

Platform | Support | Notes
---
Desktop and mWeb | Supported | Full support.
---
Native Android / iOS | Supported | Ideal for apps with strict no-third-party-SDK requirements.
---
UPI Intent | Supported | You manage the intent redirect and `callback_url`.
---
React Native / Flutter | Supported | Call Razorpay APIs from your backend. Handle UI natively in the app.

   

**INFO**

**Handy Tips**

Standard Checkout, Custom Checkout and S2S are available for UPI Autopay, Cards and eMandate. TPV and Irrevocable Mandates are available for UPI Autopay only. Registration Links are available across all methods.

## Integration Steps

Follow these integration steps:

### Cards

1. [Create the Authorisation Transaction](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers/standard-integration/recurring-payments/cards/authorization-transaction.md)
2. [Fetch and Manage Tokens](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers/standard-integration/recurring-payments/cards/tokens.md)
3. [Create Subsequent Payments](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers/standard-integration/recurring-payments/cards/subsequent-payments.md)

### UPI

1. [Create the Authorisation Transaction](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers/standard-integration/recurring-payments/upi/authorization-transaction.md)
2. [Fetch and Manage Tokens](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers/standard-integration/recurring-payments/upi/tokens.md)
3. [Create Subsequent Payments](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers/standard-integration/recurring-payments/upi/subsequent-payments.md)

### UPI with TPV

1. [Create the Authorisation Transaction](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers/standard-integration/recurring-payments/upi-tpv/authorization-transaction.md)
2. [Fetch and Manage Tokens](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers/standard-integration/recurring-payments/upi-tpv/tokens.md)
3. [Create Subsequent Payments](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers/standard-integration/recurring-payments/upi-tpv/subsequent-payments.md)
