# Merchant Onboarding Status

You can retrieve a merchant's account onboarding status. Using this information, you can:
- Nudge your sub-merchants to complete their onboarding and get payments enabled.
- Know when the merchant account is activated to manage their payments. 

There are two ways to fetch the status of merchant onboarding:

- [Using API](#using-apis)
- [Using Webhooks](#using-webhooks)

## Using API

Use the [Fetch account API](https://razorpay.com/docs/build/llm-docs/api/partners/account-onboarding/fetch.md) to get the onboarding status of the sub-merchant. 

## Using Webhooks

[Subscribe to webhook events](https://razorpay.com/docs/build/llm-docs/partners/aggregators/onboarding-api/webhooks.md) to receive real-time notifications about the merchant account activation status. 

    
    Webhook Event | Payload
    ---
    `account.activated` | [Sample Payload](https://razorpay.com/docs/build/llm-docs/webhooks/partners/activated.md#account-activated)
    ---
    `account.under_review` | [Sample Payload](https://razorpay.com/docs/build/llm-docs/webhooks/partners/under-review.md#account-under-review)
    ---
    `account.needs_clarification` | [Sample Payload](https://razorpay.com/docs/build/llm-docs/webhooks/partners/needs-clarification.md#account-needs-clarification)
    ---
    `account.suspended` | [Sample Payload](https://razorpay.com/docs/build/llm-docs/webhooks/partners/suspended.md#account-suspended)
    ---
    `account.rejected` | [Sample Payload](https://razorpay.com/docs/build/llm-docs/webhooks/partners/rejected.md#account-rejected)
    ---
    `account.activated_kyc_pending` | [Sample Payload](https://razorpay.com/docs/build/llm-docs/webhooks/partners/activated-kyc-pending.md#account-activated-kyc-pending)
    ---
    `account.funds_hold` | [Sample Payload](https://razorpay.com/docs/build/llm-docs/webhooks/partners/funds-onhold.md#account-funds-on-hold)
    ---
    `account.funds_unhold` | [Sample Payload](https://razorpay.com/docs/build/llm-docs/webhooks/partners/funds-unhold.md#account-funds-unhold)
    ---
    `account.activated_kyc_pending` | [Sample Payload](https://razorpay.com/docs/build/llm-docs/webhooks/partners/activated-kyc-pending.md#account-activated-kyc-pending)
    ---
    `account.instantly_activated` | [Sample Payload](https://razorpay.com/docs/build/llm-docs/webhooks/partners/instantly-activated.md#account-instantly-activated)
    ---
    `account.payments_enabled` | [Sample Payload](https://razorpay.com/docs/build/llm-docs/webhooks/partners/payment-enabled.md#account-payment-enabled)
