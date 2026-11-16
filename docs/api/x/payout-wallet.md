> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payout Wallet - Amazon

> Find APIs to make payouts via an Amazon Pay Gift Card.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

With Payout Wallet APIs, make payouts to your Contact's Amazon Pay Gift Card wallet from [RazorpayX Lite](https://razorpay.com/docs/x/account-types/razorpayx-lite.md). You can process payouts up to ₹10,000 per transaction multiple times in a day. Know more about [Amazon Gift Cards](https://razorpay.com/docs/x/payout-wallet/amazon.md).

Creating the Contact and Fund account before making a payout helps you improve payout processing time. You can continue to use the Contact and Fund account details (instead of Ids) in the composite API to make payouts. This does not create duplicate Contacts or Fund accounts in your system.

Idempotency allows you to safely retry or send the same request multiple times without the fear of performing the same action more than once. Know more about [Payout Idempotency](https://razorpay.com/docs/api/x/payout-idempotency.md).

Fork the Razorpay Postman Public Workspace and try the Payout Wallet API using your [Test API Keys](https://razorpay.com/docs/x/dashboard/api-keys.md).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-1706cd68-1bcc-4879-ba60-90b4289449bd)

> [card] [Create a Contact](https://razorpay.com/docs/api/x/payout-wallet/create/contact.md)
>
> `POST` `/v1/contacts`
>
> Creates contact for Amazon Pay Gift Card.

> [card] [Create a Fund Account of type `wallet`](https://razorpay.com/docs/api/x/payout-wallet/create/fund-account)
>
> `POST` `/v1/fund-accounts/`
>
> Creates a `wallet` fund account for your Contact to receive Amazon Pay Gift Card.

> [card] [Create a Payout](https://razorpay.com/docs/api/x/payout-wallet/create/payout.md)
>
> `POST` `/v1/payouts`
>
> Creates a normal payout to your Contact's Amazon Pay Gift Card.

> [card] [Make Payouts to Amazon Pay Wallet Using Composite API](https://razorpay.com/docs/api/x/payout-wallet/create/payout-composite.md)
>
> `POST` `/v1/payouts`
>
> Create a Contact, Fund Account and make the payout to your Contact's Amazon Pay Gift Card in a single API call.

## Related Guides

* [About Amazon Payout Wallet](https://razorpay.com/docs/x/payout-wallet/amazon.md)
* [Set Up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payouts.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks)
* [Amazon Brand Guidelines](https://razorpay.com/docs/x/payout-wallet/amazon/branding-guidelines.md)
