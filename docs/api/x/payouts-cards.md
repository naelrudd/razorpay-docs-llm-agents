> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payouts to Cards

> Make payouts directly to a credit, debit or prepaid card using APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

With Payouts to Cards APIs, you can make payouts directly to a credit card, debit card or prepaid card. Payouts via **Visa Direct** and **MasterCard Send** are temporarily unavailable. Know more about the [supported networks](https://razorpay.com/docs/x/payouts/cards.md#supported-networks-and-banks).

> [!NOTE]
>
> **Feature Request**
>
> This is an on-demand feature and available only to PCI-compliant merchants. To enable this feature, raise a request using the [support form](https://razorpay.com/support/) on the RazorpayX Dashboard.

Adhering to the RBI guidelines, you can either make a payout without saving card details or save a card details with a tokenisation service - [Razorpay TokenHQ](https://razorpay.com/card-tokenisation/) or any external token provider. Payouts to these tokenised cards can be made using the mode `card`.

[Allowlist IPs](https://razorpay.com/docs/x/dashboard/allowlist-ip.md) that you use while making payouts via APIs and pass the [idempotency key](https://razorpay.com/docs/api/x/payout-idempotency.md). [Create a Contact](https://razorpay.com/docs/api/x/contacts/create.md) and [Fund Account](https://razorpay.com/docs/api/x/fund-accounts.md) before creating payouts.

Fork the Razorpay Postman Public Workspace and try the Payouts to Cards APIs using your [Test API Keys](https://razorpay.com/docs/x/dashboard/api-keys.md).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/f960539b-c56c-41e5-810b-63d2a89d447e/folder/12492020-0a7f8d61-ca43-439c-80db-a6fb08877a5f)

> [card] [Create a Payout](https://razorpay.com/docs/api/x/payouts-cards/create/without-saving-card.md)
>
> `POST` `/v1/payouts`
>
> Make a payout to a card without saving the card details.

> [card] [Create Fund Account](https://razorpay.com/docs/api/x/payouts-cards/create/save-card/external-token/fund-account.md)
>
> `POST` `/v1/fund_accounts`
>
> Creates a fund account for a card tokenised by external token providers.

> [card] [Create a Payout](https://razorpay.com/docs/api/x/payouts-cards/create/save-card/external-token/payout.md)
>
> `POST` `/v1/payouts`
>
> Makes a payout to a card tokenised by external token providers.

> [card] [Create Fund Account](https://razorpay.com/docs/api/x/payouts-cards/create/save-card/razorpay-tokenhq/fund-account.md)
>
> `POST` `/v1/fund_accounts`
>
> Creates a fund account for a card tokenised by Razorpay TokenHQ.

> [card] [Create a Payout](https://razorpay.com/docs/api/x/payouts-cards/create/save-card/razorpay-tokenhq/payout.md)
>
> `POST` `/v1/payouts`
>
> Makes a payout to a card tokenised by Razorpay TokenHQ.

## Related Guides

* [About Payout to Cards](https://razorpay.com/docs/x/payouts/cards.md)
* [Set up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payouts.md)
* [Webhooks Payloads](https://razorpay.com/docs/webhooks)
* [Status Details](https://razorpay.com/docs/errors/x/payout-status-details.md)
