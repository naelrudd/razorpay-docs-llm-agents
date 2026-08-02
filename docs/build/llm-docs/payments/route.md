# About Route

Razorpay Route simplifies complex payment flows by enabling you to easily split incoming funds among multiple third-parties, sellers or bank accounts. This solution is ideally suited for businesses, such as marketplaces or platforms, that operate on a `one-to-many` disbursement model.

  
### Features

    - Add and manage Linked Accounts.
    - Split payments and transfer funds to multiple Linked Accounts.
    - Reverse transferred funds and manage customer refunds with automated reversals.
    - Manage Linked Account settlements.
    - Move from manual and file-based reconciliation to an entirely API-driven process.
   

  
### Advantages

    - **Instant Transfers**: Instant transfers, ensuring recipients receive payments promptly. Beneficial for businesses and individuals who rely on timely disbursements.
    - **Multiple Payment Transfers**: Splits payments into various portions for seamless transfer to multiple parties, ideal for marketplaces where sellers, service providers and platform owners receive their respective shares.
    - **Easy Integration**: Seamlessly integrates into existing payment systems via APIs, enhancing payment capabilities without major system changes.
    - **Transparent Reporting and Settlements**: Comprehensive reporting and analytics for tracking transactions, transfers and settlements.
   

## Prerequisites

You should add Linked Accounts using the [Dashboard](https://razorpay.com/docs/build/llm-docs/payments/route/linked-account.md#add-and-manage-linked-accounts) or [APIs](https://razorpay.com/docs/build/llm-docs/api/payments/route/create-linked-account.md) before using Route.

## Eligibility Requirements

As per RBI Payment Aggregator guidelines issued in September 2025, businesses must meet the following criteria to access or continue using Route.

### Minimum Financial Turnover

Your business must meet at least one of the following thresholds in either the current (FY26) or preceding (FY25) financial year:

Turnover Type | Minimum Threshold | Accepted Document
---
Domestic | > ₹40 Lakhs | GST-3B returns (cumulative taxable outward supplies)
---
Export | > ₹5 Lakhs | Bank-issued FIRC (INR equivalent of inward remittances)

### Payer-Payee Transparency

The third party listed as your linked account must directly interface with your customers to provide goods or services. To meet this requirement, submit a written confirmation describing your Route use case. Razorpay will review the submission and, once approved, it will be treated as a valid declaration of Payer-Payee Transparency for your account.

**WARN**

**Watch Out!**

The deadline to submit compliance information was **December 31, 2025**. If you were using Route before this date and did not submit the required proofs, your Route access has been disabled. Please reach out to [Razorpay Support team](https://razorpay.com/support/) for getting Route re-enabled.

For answers to common questions about these requirements, refer to the [RBI Compliance FAQs](https://razorpay.com/docs/build/llm-docs/payments/route/faqs.md#rbi-compliance-requirements-for-route).

## How Route Works

Given below is the funds flow in Route:

1. A customer makes a purchase on your site.
2. You can choose to:
   - Initiate transfer of funds to Linked Accounts.
   - Defer the transfer settlement.
   - Define a custom delay period for settlement.
3. Razorpay settles funds to the Linked Account and sends a webhook notification to you.

## Get Started

To get started with Route:

1. Log in to the Dashboard and click **Route** under **PAYMENT PRODUCTS**.
1. After log in, you should add linked accounts to start using Route. Refer to the [Linked Accounts](https://razorpay.com/docs/build/llm-docs/payments/route/linked-account.md) page for more information.
1. Once Linked Accounts are added, you can then start creating transfers to those accounts. Refer to the [Transfer Funds to Linked Accounts](https://razorpay.com/docs/build/llm-docs/payments/route/transfer-funds-to-linked-accounts.md) page for more information.

Explore the [Route Use Cases](https://razorpay.com/docs/build/llm-docs/payments/route/use-cases.md) to gain insights into the practical applications of Route.

### Supported Platforms

Route is supported on the following platforms:

   
      
      Web | Android | iOS | Webview
      ---
      ✓ | ✓ | ✓ | ✓
      
   
   
      
      Web | Android | iOS | Webview
      ---
      ✓ | ✓ | ✓ | ✓
      
   

### Related Information

- [Linked Accounts](https://razorpay.com/docs/build/llm-docs/payments/route/linked-account.md)
- [Transfer Funds to Linked Accounts](https://razorpay.com/docs/build/llm-docs/payments/route/transfer-funds-to-linked-accounts.md)
- [Initiate Refund](https://razorpay.com/docs/build/llm-docs/payments/route/linked-account/initiate-refund.md)
- [Reports](https://razorpay.com/docs/build/llm-docs/payments/route/view-reports.md)
- [RBI Compliance FAQs](https://razorpay.com/docs/build/llm-docs/payments/route/faqs.md#rbi-compliance-requirements-for-route)
