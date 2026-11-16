> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Route

> Use Razorpay Route to split payments between third parties and manage settlements, refunds and reconciliation by creating Linked Accounts.

Available in
🇮🇳 India

Razorpay Route allows you to split payments between third parties, sellers or bank accounts. Using Route, you can easily manage settlements, refunds, reconciliation and make vendor payments. It is helpful for businesses that disburse payments in a `one-to-many` model.

## Features

Using Razorpay Route, you can:

* Add and manage Linked Accounts.
* Split payments and transfer funds to multiple Linked Accounts.
* Reverse transferred funds and manage customer refunds with automated reversals.
* Manage Linked Account settlements.
* Move from manual and file-based reconciliation to an entirely API-driven one and more.

![What We Offer](https://razorpay.com/docs/build/browser/assets/images/route-route_what_we_offer.jpg)

## Advantages

> [accordion] Instant Transfers
>
> Razorpay Route facilitates instant transfers, ensuring recipients receive their payments promptly. This benefits businesses and individuals relying on timely payments for their operations or financial needs.

> [accordion] Multiple Payment Transfers
>
> Razorpay Route splits payments into various portions, allowing for seamless funds transfer to different parties involved in a transaction. This is particularly useful in marketplaces, where sellers, service providers, and platform owners receive their respective shares.

> [accordion] Easy Integration
>
> You can easily integrate Razorpay Route within the existing payment system and platform. Its API-driven approach allows businesses to seamlessly incorporate Razorpay Route into their systems by enhancing payment capabilities without significant disruptions.

> [accordion] Transparent Reporting and Settlements
>
> Razorpay provides comprehensive reporting and analytics, allowing us to track transactions, transfers, and settlements.

## How Route Works

Given below is the funds flow in Route:

![Route Flow](https://razorpay.com/docs/build/browser/assets/images/route_flow.gif)

1. The customer makes a purchase on your site.
2. You can choose to do any one of the following:
   * Initiate transfer of funds to Linked Accounts.
   * Defer the transfer from being settled.
   * Define a time until which the transfer settlement should be delayed.
3. Razorpay settles funds to the Linked Account and sends a webhook payload to you.

## Prerequisites

You should add Linked Accounts using [Dashboard](https://razorpay.com/docs/payments/route/linked-account.md#add-linked-accounts).

## Get Started

To get started with Route:

1. Log in to the Dashboard and click **Route** under **PAYMENT PRODUCTS**.
2. After login, you should add linked accounts to start using Route. Refer to the [Linked Accounts](https://razorpay.com/docs/payments/route/linked-account.md) page for more information.
3. Once linked accounts are added, you can then start creating transfers to those accounts. Refer to the [Transfer Funds to Linked Accounts](https://razorpay.com/docs/payments/route/transfer-funds-to-linked-accounts.md) page for more information.

Know more about [Route](https://razorpay.com/docs/payments/route) and the [Dashboard actions](https://razorpay.com/docs/payments/route/batch-upload.md).

### Related information

[Route Use Cases](https://razorpay.com/docs/payments/route/use-cases.md)
