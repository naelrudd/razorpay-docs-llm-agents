> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payout Links

> List of Payout Links API endpoints to create, retrieve and cancel Payout Links.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

[Payout Links](https://razorpay.com/docs/x/payout-links) enable you to make payouts to those Contacts whose Fund Account details are not available. Allowlisting your IP is mandatory for using the Payout Link APIs. Know how to [allowlist your IP](https://razorpay.com/docs/x/dashboard/allowlist-ip.md).

Fork the Razorpay Postman Public Workspace and try the Payout Links APIs using your [Test API Keys](https://razorpay.com/docs/x/dashboard/api-keys.md).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-60f1103d-eb2b-454b-8b17-7911e3c9d2f5)

> [card] [Create a Payout Link (Contact Details)](https://razorpay.com/docs/api/x/payout-links/create/use-contact-details.md)
>
> `POST` `/v1/payout-links`
>
> Creates a Payout Link using contact details like email id/mobile number.

> [card] [Create a Payout Link (Contact ID)](https://razorpay.com/docs/api/x/payout-links/create/use-contact-id.md)
>
> `POST` `/v1/payout-links`
>
> Creates a Payout Link using Contact ID.

> [card] [Fetch All Payout Links](https://razorpay.com/docs/api/x/payout-links/fetch-all.md)
>
> `GET` `/v1/payout-links`
>
> Retrieves all Payout Links created.

> [card] [Fetch Payout Links With ID](https://razorpay.com/docs/api/x/payout-links/fetch-with-id.md)
>
> `GET` `/v1/payout-links/:id/`
>
> Retrieves a particular Payout Link.

> [card] [Cancel a Payout Link](https://razorpay.com/docs/api/x/payout-links/cancel.md)
>
> `POST` `/v1/payout-links/:id/post`
>
> Cancels a Payout Link.

## Related Guides

* [About Payout Links](https://razorpay.com/docs/x/payout-links)
* [Set Up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payouts.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/payout-links.md)
