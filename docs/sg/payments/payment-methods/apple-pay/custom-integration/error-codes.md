> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Error Codes

> Reference for Apple Pay Custom Checkout error responses, canMakePayment reasons, payment error responses, client errors and a handling guide.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

This page lists the error responses you can encounter while integrating Apple Pay on Custom Checkout, what triggers each one and how to handle them.

## canMakePayment Reasons

When `canMakePayment()` returns `{ available: false }`, the `reason` field indicates why:

| Reason | When is this triggered? |
| - | - |
| `no_session` | The browser does not support the Apple Pay JS API (`ApplePaySession` is not available). The customer is on a non-Apple device or an unsupported browser. |
| `version_3_not_supported` | The browser supports Apple Pay but does not support version 3 of the Apple Pay API. The customer's OS or browser is too old. |
| `merchant_disabled` | Apple Pay is not enabled for this merchant on the Razorpay dashboard. Contact Razorpay to enable it. |
| `cannot_make_payments` | The device supports Apple Pay but the customer has no cards set up in their Wallet, or Apple Pay is restricted by parental controls / device management. |
| `no_credentials_found_in_mobile` | The customer is on a mobile device and has Apple Pay supported but no payment credentials (cards) configured in their Wallet. |
| `unsupported country - {list}` | The customer's country is not supported for Apple Pay transactions. |

## Error Response Structure

```json Response theme={null}
{
  "status": "failure",
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "Payment failed due to insufficient funds",
    "step": "payment_authentication",
    "reason": "insufficient_funds",
    "source": "customer",
    "metadata": { "payment_id": "pay_xxx", "order_id": "order_xxx" }
  }
}
```

| Field | Type | Description |
| - | - | - |
| `code` | string | Error category. |
| `description` | string | Human-readable error message. |
| `step` | string | Which step in the payment flow the error originated from. |
| `reason` | string | Machine-readable reason for the failure. |
| `source` | string | Who is responsible — `customer`, `merchant`, or `razorpay`. |
| `metadata` | object | Additional context (for example, `payment_id`, `order_id`). |

## Payment Error Responses

Returned from `createPayment()` or the `onFailure` callback:

| code | reason | source | description | When is this triggered? |
| - | - | - | - | - |
| `PAYMENT_CANCELLED` | `payment_cancelled` | `customer` | Payment was cancelled. | The customer dismisses the native Apple Pay payment sheet (taps Cancel, fails Face ID, etc.) without completing authorization. |
| `PAYMENT_FAILED` | `payment_already_completed` | `merchant` | Payment already completed. | `createPayment()` was called again after a payment already completed successfully on this wallet instance. Each instance supports only one successful payment. |
| `PAYMENT_FAILED` | `payment_already_in_progress` | `merchant` | Payment already in progress. | `createPayment()` was called while a previous `createPayment()` invocation is still in progress (the wallet sheet is still open or the authorization hasn't resolved). |

For backend payment failures (for example, card declined, insufficient funds, invalid order), all error fields (`code`, `reason`, `description`, `source`, `step`, `metadata`) are propagated directly from the Razorpay backend. Refer to the [Razorpay Payment Error Codes](https://razorpay.com/docs/sg/errors) documentation for the full list of possible values.

## Client Error Responses

Thrown as exceptions during initialization and setup — before any payment flow. Merchants should wrap these calls in `try/catch`:

| code | reason | source | description | When is this triggered? |
| - | - | - | - | - |
| `PAYMENT_FAILED` | `invalid_params` | `merchant` | `rzpKey` is required. | `RazorpayCheckoutBlocks()` called without `rzpKey` or `rzpKey` is not a string. |
| `PAYMENT_FAILED` | `invalid_params` | `merchant` | `rzpKey` must start with `rzp_test_` or `rzp_live_`. | `RazorpayCheckoutBlocks()` called with an `rzpKey` that doesn't match `rzp_test_*` or `rzp_live_*` format. |
| `PAYMENT_FAILED` | `invalid_params` | `merchant` | `customerContactNumber` is required. | `RazorpayCheckoutBlocks()` called without `customerContactNumber` or it is not a string. |
| `PAYMENT_FAILED` | `invalid_params` | `merchant` | Unsupported method: `{method}`. Supported methods are: `apple_pay`. | `createDigitalWallet()` called with a `method` value that isn't `apple_pay`. |

## Handling Guide

| source | What it means | Recommended action |
| - | - | - |
| `merchant` | Integration error — the SDK was called incorrectly. | Fix your integration code. These are fully preventable with correct parameter validation. |
| `customer` | Customer cancelled or their device doesn't support the method. | Show a fallback payment option or a retry prompt. Do not retry automatically. |
| `razorpay` | Backend rejection or transient infrastructure issue. | For `create_payment_failed` / `authorise_payment_failed`: display the `description` to the customer and let them retry. For persistent issues: contact Razorpay support. |
