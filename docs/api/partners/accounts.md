> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Accounts API

> Create, fetch and update sub-merchant accounts and their KYC documents using Razorpay Accounts API.

Available in
🇮🇳 India

Use the Accounts APIs to onboard and manage sub-merchants from your own platform. Create an account, send the KYC details Razorpay asks for and keep managing the account after its products activate. Webhooks tell you whenever an account changes or Razorpay needs something from the sub-merchant.

Every account response lists the `requirements` still due for each product, computed on every call. Build your forms from these requirements instead of hard-coding rules. Know more about the [Requirement entity](https://razorpay.com/docs/api/partners/accounts/requirement-entity.md).

## Authentication

Authenticate every request with HTTP Basic auth. Generate 2 key and secret pairs for your app on the Razorpay Partner Dashboard, one for test mode and one for live mode:

* **Key:** The key of the pair for the mode. A test key starts with `rzp_test_partner_` and a live key with `rzp_live_partner_`.
* **Secret:** The secret of the same pair. The Partner Dashboard shows it only once, when you generate it.

The pair you send decides the mode. The prefix only helps you tell the keys apart. Live mode and test mode share one base URL, `https://api.razorpay.com`. A test pair never reaches a live account. You need no token. Each pair works for every account you onboard in its mode.

> [!WARNING]
>
> **Watch Out!**
>
> * Keep the secret on your servers, never in a browser or mobile app.
> * Razorpay accepts requests only from the IP ranges you allowlist for your app in each mode. Any other address gets `403` with `ip_not_allowed`. In test mode, the allowlist applies once it has an entry.
> * To change the secret, rotate it on the Partner Dashboard. The old secret keeps working for up to 24 h or until you end that window. A revoked secret stops working at once.

### Idempotency

Send the `X-Idempotency-Key` header on every write: `POST`, `PATCH` and `DELETE`. Do not send it on a `GET`. Generate a unique key for each operation, 16-64 printable ASCII characters long. A Universally Unique Identifier (UUID) works.

The table below lists how Razorpay handles the key:

| Request | Response |
| - | - |
| A write without the key | `400` with `missing_header`. |
| A retry with the same key and body within 24 h | The original response, with the `Idempotent-Replayed: true` header. The operation does not run twice. |
| The same key with a different body | `400` with `idempotency_key_reused`. |
| The same key while the first request is still running | `409` with `idempotency_in_progress` and a `Retry-After` header. |
| A retry after a `5xx` or `409` with `idempotency_in_progress` | The request runs again. Razorpay stores only finished requests. |

To repeat an operation on purpose, such as sending a new One-Time Password (OTP), use a new key.

## Endpoints

> [card] [Create an Account](https://razorpay.com/docs/api/partners/accounts/create.md)
>
> `POST` `/v1/accounts`
>
> Creates a sub-merchant account and its owner user.

> [card] [Fetch Accounts](https://razorpay.com/docs/api/partners/accounts/fetch.md)
>
> `GET` `/v1/accounts` and `/v1/accounts/:account_id`
>
> Retrieves the accounts mapped to your app, or one account with its status and requirements.

> [card] [Update an Account](https://razorpay.com/docs/api/partners/accounts/update.md)
>
> `PATCH` `/v1/accounts/:account_id`
>
> Sends what a requirement asks for and submits the product.

> [card] [Run an Action](https://razorpay.com/docs/api/partners/accounts/run-action.md)
>
> `POST` `/v1/accounts/:account_id/actions/:action`
>
> Sends an OTP or creates a verification link.

> [card] [Upload a Document](https://razorpay.com/docs/api/partners/accounts/upload-document.md)
>
> `POST` `/v1/accounts/:account_id/documents`
>
> Stores a KYC file and returns its file ID.

> [card] [Fetch All Documents](https://razorpay.com/docs/api/partners/accounts/fetch-all-documents.md)
>
> `GET` `/v1/accounts/:account_id/documents`
>
> Retrieves the documents of an account.

> [card] [Fetch One Document](https://razorpay.com/docs/api/partners/accounts/fetch-document.md)
>
> `GET` `/v1/accounts/:account_id/documents/:file_id`
>
> Retrieves a stored document.

> [card] [Delete a Document](https://razorpay.com/docs/api/partners/accounts/delete-document.md)
>
> `DELETE` `/v1/accounts/:account_id/documents/:file_id`
>
> Deletes a file you uploaded.

Manage the sub-merchant's payment methods, such as cards, netbanking and UPI, with the [Payment Method APIs](https://slashdocs.razorpay.com/app/d/doc_oe6rsftby5u6uww6).

## Entities, Webhooks and Errors

Refer to these pages for the entities, webhooks and errors:

* [Account Entity](https://razorpay.com/docs/api/partners/accounts/entity.md)
* [Requirement Entity](https://razorpay.com/docs/api/partners/accounts/requirement-entity.md)
* [Business Model Questions](https://razorpay.com/docs/api/partners/accounts/business-model-questions.md)
* [Business Categories](https://razorpay.com/docs/api/partners/accounts/business-categories.md)
* [Document Entity](https://razorpay.com/docs/api/partners/accounts/document-entity.md)
* [Onboarding APIs Webhook Events](https://razorpay.com/docs/webhooks/partners/onboarding-apis.md)
* [Errors](https://razorpay.com/docs/api/partners/accounts/errors.md)

## Related Guides

Refer to these guides for the integration flow:

* [Onboarding APIs Integration](https://razorpay.com/docs/partners/aggregators/onboarding-api)
* [Test Your Integration](https://razorpay.com/docs/partners/aggregators/onboarding-api/test-integration)
