> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Stakeholder APIs

> Use the Stakeholder APIs to add stakeholders for an account.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

You can use the Stakeholder APIs to add a stakeholder for an account. Each stakeholder will have their KYC. A stakeholder can be a signatory or an owner of the business.

Fork the Razorpay Postman Public Workspace and try the Stakeholder APIs using your [Test API Keys](https://razorpay.com/docs/partners/aggregators/onboarding-api#api-authentication).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-d1f55eac-11ca-49b6-92cc-2fb96ceb0f5e)

> [card] [Create a Stakeholder](https://razorpay.com/docs/api/partners/stakeholder/create.md)
>
> `POST` `/v2/accounts/:account_id/stakeholders`
>
> Creates a stakeholder.

> [card] [Fetch a Stakeholder With ID](https://razorpay.com/docs/api/partners/stakeholder/fetch-with-id.md)
>
> `GET` `/v2/accounts/:account_id/stakeholders/:stakeholder_id`
>
> Retrieves the details of a stakeholder.

> [card] [Fetch All Stakeholders](https://razorpay.com/docs/api/partners/stakeholder/fetch-all.md)
>
> `GET` `/v2/accounts/:account_id/stakeholders`
>
> Retrieves the details of all stakeholders.

> [card] [Update a Stakeholder](https://razorpay.com/docs/api/partners/stakeholder/update.md)
>
> `PATCH` `/v2/accounts/:account_id/stakeholders/:stakeholder_id`
>
> Updates a stakeholder.

## Related Guides

* [Sub-merchant Onboarding APIs](https://razorpay.com/docs/partners/aggregators/onboarding-api)
* [Set Up Webhooks](https://razorpay.com/docs/partners/aggregators/onboarding-api/webhooks.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/partners.md)
