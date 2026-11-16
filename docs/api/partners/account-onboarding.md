> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Account

> Use the Account APIs to onboard sub-merchants.

Available in
🇮🇳 India

You can use the Account APIs to create a sub-merchant account. After an account gets created, an `account_id` is assigned. Check the [account activation flow and states](https://razorpay.com/docs/partners/aggregators/onboarding-api#account-activation).

Fork the Razorpay Postman Public Workspace and try the Account APIs using your [Test API Keys](https://razorpay.com/docs/api/authentication.md#generate-api-keys).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-51a4958d-ae00-4717-9ec4-64cb7c1bf7fb)

> [card] [Create an Account](https://razorpay.com/docs/api/partners/account-onboarding/create.md)
>
> `POST` `/v2/accounts`
>
> Creates a sub-merchant account.

> [card] [Fetch an Account](https://razorpay.com/docs/api/partners/account-onboarding/fetch.md)
>
> `GET` `/v2/accounts/:account_id`
>
> Retrieves the details of an account.

> [card] [Update an Account](https://razorpay.com/docs/api/partners/account-onboarding/update.md)
>
> `PATCH` `/v2/accounts/:account_id`
>
> Updates an account for different product activation statuses.

> [card] [Delete an Account](https://razorpay.com/docs/api/partners/account-onboarding/delete.md)
>
> `DELETE` `/v2/accounts/:account_id`
>
> Deletes a sub-merchant account.

## Related Guides

* [Sub-merchant Onboarding APIs](https://razorpay.com/docs/partners/aggregators/onboarding-api)
* [Set Up Webhooks](https://razorpay.com/docs/partners/aggregators/onboarding-api/webhooks.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/partners.md)
