> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payouts

> Create, fetch and cancel Payouts using APIs. Set up webhooks for notifications.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

A [payout](https://razorpay.com/docs/x/payouts) is a transfer of funds from your business account to a Contact's Fund Account(s). You can create and process payouts both on the RazorpayX Dashboard and via the Payouts API. Ensure to [create a contact](https://razorpay.com/docs/api/x/contacts/create.md) and add a [fund account](https://razorpay.com/docs/api/x/fund-accounts.md).

> [!TIP]
>
> **What's New**
>
> [Idempotency Key](https://razorpay.com/docs/api/x/payout-idempotency.md) is mandatory for all payout requests starting March 15, 2025.

To make payouts, you must [allowlist IPs](https://razorpay.com/docs/x/dashboard/allowlist-ip.md) and pass the [idempotency key](https://razorpay.com/docs/api/x/payout-idempotency.md).

Making payouts from [RazorpayX Lite](https://razorpay.com/docs/x/account-types/razorpayx-lite.md) account to RazorpayX Lite Customer Identifiers or Razorpay [Customer identifiers](https://razorpay.com/docs/payments/smart-collect) is not supported.

Fork the Razorpay Postman Public Workspace and try the Payouts APIs using your [Test API Keys](https://razorpay.com/docs/x/dashboard/api-keys.md).
[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-117c93d1-1a79-4958-9067-eb97a3459f08)

> [card] [Creates a Payout to a Bank Account](https://razorpay.com/docs/api/x/payouts/create/bank-account.md)
>
> `POST` `
>     /v1/payouts`
>
> Create a payout to a bank account.

> [card] [Create a Payout to a VPA](https://razorpay.com/docs/api/x/payouts/create/vpa.md)
>
> `POST` `
>     /v1/payouts`
>
> Creates a payout to a VPA.

> [card] [Fetch all Payouts](https://razorpay.com/docs/api/x/payouts/fetch-all.md)
>
> `GET` `/v1/payouts?account_number=\{account number\}`
>
> Retrieves details of all the payouts.

> [card] [Fetch a Payout with ID](https://razorpay.com/docs/api/x/payouts/fetch-with-id.md)
>
> `GET` `/v1/payouts/:id`
>
> Retrieves details of one payout via ID.

> [card] [Cancel a Queued Payout](https://razorpay.com/docs/api/x/payouts/cancel.md)
>
> `PATCH` `/v1/payouts/:id/cancel`
>
> Cancels a payout in `queued` state.

## Related Guides

* [About Payouts](https://razorpay.com/docs/x/payouts)
* [Set up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payouts.md)
* [Webhooks Payloads](https://razorpay.com/docs/webhooks)
