> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# About Subscriptions

> Use Razorpay Subscriptions to accept recurring payments from your customers. Check the available billing models and the supported currencies.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use Razorpay Subscriptions to set up and manage recurring payments.

* Create a plan with your pricing and billing schedule, then create a subscription for customers. Razorpay automatically charges them at regular intervals.

* Manage all Subscriptions directly from the Dashboard - create plans, manage customer subscriptions, handle upgrades/downgrades, or pause billing.

* Receive near real-time notifications by subscribing to Webhook events.

## Advantages

* **Automated Billing**: Create a plan once and Razorpay automatically charges customers on schedule.
* **Multiple Billing Models**: Support fixed amounts, usage-based billing or add-ons for extra services.
* **Flexible Plans**: Set up trial periods, upfront charges and multiple pricing tiers.
* **Customer Management**: Allow customers to upgrade, downgrade, pause or cancel subscriptions.
* **Smart Payment Retries**: Automatic retry logic maximises successful collections.
* **Seamless Integration**: Integrate using Dashboard links or APIs.
* **Auto-Invoicing**: Invoices are automatically generated for every billing cycle.

## When to Use Subscriptions vs Recurring Payments

**Subscriptions** are plan-based recurring payments. You create a plan (pricing and billing schedule), create a subscription for each customer and Razorpay automatically charges them at the defined intervals. Billing is fully automated and managed from the Dashboard.

**Recurring Payments** let you charge customers repeatedly after they authorise their payment method once. You control when each charge is initiated using tokens. There is no built-in plan or automatic schedule; you trigger charges via API based on your business logic.

> [accordion] Choose Subscriptions when you have:
>
> * Fixed billing schedules (weekly, monthly, quarterly, yearly)
> * Multiple pricing plans for customers to choose from
> * Need for automated, hands-off billing

> [accordion] Choose Recurring Payments when you need:
>
> * Flexible billing based on usage or milestones
> * Manual control over when to charge each payment
> * On-demand or variable payment amounts
>
> See [Recurring Payments](https://razorpay.com/docs/sg/payments/recurring-payments.md) for flexible, usage-based billing.

## Supported Payment Methods

Customers can make payments using cards.

See [Supported Payment Methods](https://razorpay.com/docs/sg/payments/subscriptions/supported-payment-methods.md) for complete details on limits and supported banks.

## Get Started

1. Log in to the Dashboard and navigate to **Subscriptions** under **PAYMENT PRODUCTS**.
2. [Create a Plan](https://razorpay.com/docs/payments/subscriptions/plugins/magento/test-it-out.md#plan) to define your product, pricing and billing frequency.
3. [Create a Subscription](https://razorpay.com/docs/sg/payments/subscriptions/create.md#2-create-a-subscription) to link a customer to a plan using Dashboard or APIs.
4. Verify your subscription flow in [test mode](https://razorpay.com/docs/sg/payments/subscriptions/test.md).

## Integrate With Your Systems

You can integrate Razorpay Subscriptions with your existing systems:

> [tab] Dashboard
>
> Create [Plans](https://razorpay.com/docs/sg/payments/subscriptions/create-plans.md) and [Subscription Links](https://razorpay.com/docs/sg/payments/subscriptions/create-subscription-links.md) and share via email/SMS - no coding required.

> [tab] API Integration
>
> Integrate Subscriptions with your website or app using [Subscriptions APIs](https://razorpay.com/docs/sg/api/payments/subscriptions.md).

> [tab] Webhooks
>
> Set up [webhooks](https://razorpay.com/docs/sg/payments/subscriptions/subscribe-to-webhooks.md) to receive real-time notifications for subscription events.

#### Related Information

* [How Subscriptions Work](https://razorpay.com/docs/sg/payments/subscriptions/workflow.md)
* [Subscription Use Cases](https://razorpay.com/docs/sg/payments/subscriptions/use-cases.md)
* [Subscription States](https://razorpay.com/docs/sg/payments/subscriptions/states.md)
* [Create Subscriptions](https://razorpay.com/docs/sg/payments/subscriptions/create.md)
* [Integration Guide](https://razorpay.com/docs/sg/payments/subscriptions/integration-guide.md)

- [Subscriptions APIs](https://razorpay.com/docs/sg/payments/subscriptions/apis.md)

* [FAQs](https://razorpay.com/docs/sg/payments/subscriptions/faqs.md)
