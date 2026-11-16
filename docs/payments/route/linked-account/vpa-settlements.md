> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# VPA Settlements

> Settle funds to beneficiaries using their UPI ids (VPA) via Razorpay Route. Enable instant, transaction-level payouts to your beneficiaries.

Available in
🇮🇳 India

Route supports VPA (Virtual Payment Address) as a settlement destination for Linked Accounts. Marketplace platforms can pay beneficiaries using their UPI id instead of requiring bank account details.

## How VPA Settlements Work

1. Create a Linked Account and **provide the beneficiary's VPA** instead of bank account details.
2. Route verifies the VPA instantly via API (under 3 seconds) and returns the account holder's name for you to perform name matching.
3. When a payment is received, Route creates a settlement and generates a payout to the beneficiary's VPA.

## When to Use VPA Settlements

| Use Case | Why VPA? |
| - | - |
| Rental payments | Landlords prefer UPI for sub-₹1 lakh rent and do not want to share full bank account details. |
| Education fees | Tutors and coaching centres want instant payouts without sharing bank details. |
| Gig economy payouts | Freelancers and delivery partners want immediate access to funds, 24×7. |
| Affiliate and referral payouts | Publishers prefer UPI for quick, low-friction withdrawals. |

## Prerequisites

* Your Razorpay Route account must be active.
* VPA Settlements must be enabled for your account. Contact our [Support team](https://razorpay.com/support/#request) to get this activated.
* Beneficiaries must have an active UPI id linked to an Indian bank account.
* VPA Linked Accounts can be created only in live mode. API requests made with test mode keys fail. To test your integration in test mode, use a bank account settlement destination instead.
* As a business, you are responsible for performing name matching between the VPA holder name (returned by Route during verification) and the beneficiary name in your records. This is a compliance requirement. Refer to [Name Matching Requirements](#name-matching-requirements).

## Limits

| Limit | Value | Notes |
| - | - | - |
| Per-transaction limit | ₹1,00,000 | Set by NPCI. Hard limit; cannot be overridden. |
| Daily limit per beneficiary VPA | ₹1,00,000 | Resets at midnight IST. |
| Settlement processing time (P95) | Under 60 seconds | From payment capture to payout completion. |
| VPA verification time (P95) | Under 3 seconds | During Linked Account creation. |

> [!WARNING]
>
> **Watch Out!**
>
> For transfers above ₹1 lakh, use **bank account settlement** instead. A single Linked Account cannot hold both a VPA and a bank account simultaneously. To support both, create **two separate Linked Accounts for the same beneficiary**, one with VPA and one with bank account details.

## Create a VPA Linked Account

To create a VPA-based Linked Account from the Dashboard:

1. Log in to the Dashboard and navigate to **Route** under **PAYMENT PRODUCTS**.
2. Click the **Accounts** tab, then **+ Add Account**.
3. Enter the **Account Name**, **Account Email** and **Phone Number**.
4. Under **Account Type**, select **VPA**.
5. Enter the beneficiary's UPI id in the **VPA Address** field. For example, `landlord@paytm` or `9876543210@ybl`.
6. Click **Verify VPA**. Route validates the VPA and returns the account holder's name from the beneficiary's bank.
7. Perform name matching between the returned name and your beneficiary records. Refer to [Name Matching Requirements](#name-matching-requirements).
8. Under **Settlement Configuration**, select **Instant** as the settlement schedule and **IMPS** as the mode.
9. Click **Create Linked Account**.

The Linked Account is created and activated immediately.

### Create a VPA Linked Account Using API

Use the [Create a Linked Account (Composite) API](https://razorpay.com/docs/api/payments/route/create-linked-account-composite.md) to create the Linked Account and its VPA settlement destination in a single call. Pass `method: upi` and the beneficiary's VPA in the `settlement_accounts` array. Use your live mode API keys.

For an `individual`, the `legal_info` and `stakeholder` objects are optional. Refer to the [minimum request for an individual](https://razorpay.com/docs/api/payments/route/create-linked-account-composite.md#minimum-request-for-an-individual).

## VPA Verification

When you submit a VPA during Linked Account creation, Route calls the RazorpayX VPA Verification API, which queries the NPCI network and returns the account holder's name as registered with the beneficiary's bank.

Verification states:

| Status | Meaning | Next Action |
| - | - | - |
| Valid | VPA exists and is active. | Proceed with name matching. |
| Invalid | VPA does not exist or has a formatting error. | Ask beneficiary to confirm their UPI id. |
| Inactive | VPA exists but the account is closed. | Ask beneficiary for an updated VPA. |
| Timeout | Network issue during verification. | Retry verification after a few seconds. |

## Name Matching Requirements

As a business, you must verify that the VPA belongs to the beneficiary you are onboarding. Route provides the VPA holder's name returned by the beneficiary's bank. You are responsible for comparing this name against your beneficiary records and documenting the outcome.

Name matching should account for common bank formatting differences such as uppercase names, surname-first ordering, abbreviated middle names or truncated names.

## Webhook Events

VPA Linked Accounts emit the standard account events. There are no VPA-specific events. Subscribe to the following events:

| Webhook Event | When It Is Sent |
| - | - |
| `account.activated` | The VPA Linked Account is activated. |
| `account.under_review` | The VPA Linked Account is under review. |
| `account.needs_clarification` | The VPA Linked Account needs clarification. |
| `account.updated` | The VPA Linked Account is updated. |

Refer to [Subscribe to Webhooks](https://razorpay.com/docs/payments/route/subscribe-to-webhooks.md) for setup instructions.

## Handle VPA Settlement Failures

A payout may fail if the beneficiary's VPA becomes inactive after onboarding. When this happens:

1. Find the failed settlement on the Dashboard under **Route** → **Settlements** → **Failed**.
2. Notify the beneficiary and ask them to confirm or update their UPI id.
3. Update the Linked Account with the new VPA via the Dashboard or API and re-verify.
4. Retry the settlement from the Dashboard under **Route** → **Settlements** → **Failed** → **Retry**.

> [!NOTE]
>
> **Handy Tips**
>
> Collect a bank account as a fallback during onboarding. If VPA settlement fails, you can create a second Linked Account for the same beneficiary with bank account details and process the settlement that way.

## Daily Limit Handling

If a beneficiary's VPA reaches the ₹1 lakh daily limit, the transfer is rejected with the error `daily_limit_exceeded`. The limit resets at midnight IST.

Options when the limit is reached:

* Queue the settlement for the next day.
* Switch to bank account settlement for that beneficiary (requires a separate Linked Account with bank details).
* If the beneficiary has multiple UPI ids, each VPA has an independent daily limit.

## Pricing

| Component | Cost |
| - | - |
| VPA Settlements feature | No additional platform fee beyond standard Route pricing. |
| VPA verification | Included (no extra charge). |
| IMPS transaction fee (per payout) | ₹2–₹5 + 18% GST, based on transaction amount. |

Standard Route pricing applies. No additional charges are levied for using VPA over bank account settlement.

## Comparison: VPA vs Bank Account Settlement

| Feature | VPA Settlement | Bank Account Settlement |
| - | - | - |
| Onboarding time | Under 1 minute (instant API verification) | 10–15 minutes (penny drop verification) |
| Per-transaction limit | ₹1,00,000 | No limit (subject to banking partner limits) |
| Daily limit per beneficiary | ₹1,00,000 | No limit |
| Beneficiary information required | UPI id and name | Account number, IFSC and beneficiary name |
| Best suited for | Rentals, gig economy, education (sub-₹1L) | Vendors, suppliers, large or corporate payouts |

## FAQs

> [accordion] Can a Linked Account have both a VPA and a bank account?
>
> No. You must choose one settlement method per Linked Account. To support both, create two separate Linked Accounts for the same beneficiary.

> [accordion] What happens if the beneficiary changes their VPA?
>
> Future payouts to the old VPA will fail. Update the Linked Account with the new VPA via the Dashboard or API and re-verify before retrying.

> [accordion] Can I cancel a VPA settlement once it is initiated?
>
> No. VPA settlements are processed instantly and cannot be cancelled once the payout is in the UPI network. If the payout fails, it can be retried or cancelled from the Dashboard.

> [accordion] Are VPA settlements available for international beneficiaries?
>
> No. VPA settlements are only available for beneficiaries with an active Indian UPI id linked to an Indian bank account.

> [accordion] Is VPA settlement supported in the batch upload flow?
>
> No. Batch upload for Linked Account creation supports bank account details only. VPA Linked Accounts must be created individually via the Dashboard or API.

### Related Information

* [Linked Accounts](https://razorpay.com/docs/payments/route/linked-account.md)
* [Schedule Settlements](https://razorpay.com/docs/payments/route/schedule-settlement.md)
* [Transfer Funds to Linked Accounts](https://razorpay.com/docs/payments/route/transfer-funds-to-linked-accounts.md)
* [Subscribe to Webhooks](https://razorpay.com/docs/payments/route/subscribe-to-webhooks.md)
* [Route APIs](https://razorpay.com/docs/api/payments/route.md)
