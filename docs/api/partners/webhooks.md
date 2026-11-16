> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Webhooks

> Use the Webhook APIs to receive event notifications or subscribe to events happening in a sub-merchant's account as per their integration.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Use the Webhooks APIs to receive event notifications or subscribe to events happening in a sub-merchant's account for the integration installed.

Fork the Razorpay Postman Public Workspace and try the Webhooks APIs using your [Test API Keys](https://razorpay.com/docs/partners/aggregators/onboarding-api#api-authentication).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-9d7fe39c-c63f-4f25-9bc8-09bcb59c7f26)

> [card] [Create a Webhook](https://razorpay.com/docs/api/partners/webhooks/create.md)
>
> `POST` `/v2/accounts/:account_id/webhooks`
>
> Creates a webhook.

> [card] [Fetch a Webhook With ID](https://razorpay.com/docs/api/partners/webhooks/fetch-with-id.md)
>
> `GET` `/v2/accounts/:account_id/webhooks/:webhook_id`
>
> Retrieves the details of a webhook.

> [card] [Fetch all Webhooks](https://razorpay.com/docs/api/partners/webhooks/fetch-all.md)
>
> `GET` `/v2/accounts/:account_id/webhooks`
>
> Retrieves the details of all webhooks.

> [card] [Update a Webhook](https://razorpay.com/docs/api/partners/webhooks/update.md)
>
> `PATCH` `/v2/accounts/:account_id/webhooks/:webhook_id`
>
> Updates a webhook.

> [card] [Delete a Webhook](https://razorpay.com/docs/api/partners/webhooks/delete.md)
>
> `DELETE` `/v2/accounts/:account_id/webhooks/:webhook_id`
>
> Deletes a webhook.

## Related Guides

* [Sub-merchant Onboarding APIs](https://razorpay.com/docs/partners/aggregators/onboarding-api)
* [Set Up Webhooks](https://razorpay.com/docs/partners/aggregators/onboarding-api/webhooks.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/partners.md)
