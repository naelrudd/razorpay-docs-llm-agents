> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Product Configuration APIs

> Use the Product Configuration APIs to enable sub-merchants request for a product.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

You can use the Product Configuration APIs to configure and activate Razorpay products for a sub-merchant account according to their requirements. For example, if you need our Payment Gateway product for all sub-merchants or Payment Gateway for one sub-merchant and Payment Link product for another sub-merchant, you can do so using this API.

You can even accept terms and conditions for the requested product using these APIs. You can fetch the terms and conditions using the [Fetch Terms and Conditions API](https://razorpay.com/docs/api/partners/terms-conditions/fetch.md).

The products Payment Links and Payment Gateway have similar requirements. If a requirement is submitted through a product configuration for `payment_gateway`, the same will be applicable for `payment_links`, and vice versa.

Fork the Razorpay Postman Public Workspace and try the Product Configuration APIs using your [Test API Keys](https://razorpay.com/docs/partners/aggregators/onboarding-api#api-authentication).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-07bc4970-f967-4020-922f-8adb7ea407e8)

> [card] [Request a Product Configuration](https://razorpay.com/docs/api/partners/product-configuration/request.md)
>
> `POST` `/v2/accounts/:account_id/products`
>
> Requests a product configuration for Payment Gateway and Payment Links.

> [card] [Fetch a Product Configuration](https://razorpay.com/docs/api/partners/product-configuration/fetch.md)
>
> `GET` `/v2/accounts/:account_id/products/:product_id`
>
> Retrieves the details of an account.

> [card] [Update Settlement Account Details](https://razorpay.com/docs/api/partners/product-configuration/update-settlement-account-details.md)
>
> `PATCH` `/v2/accounts/:account_id/products/:product_id`
>
> Updates settlement account details.

> [card] [Request Payment Methods](https://razorpay.com/docs/api/partners/product-configuration/update-request-payment-methods.md)
>
> `PATCH` `/v2/accounts/:account_id/products/:product_id`
>
> Requests Payment Methods.

## Related Guides

* [Sub-merchant Onboarding APIs](https://razorpay.com/docs/partners/aggregators/onboarding-api)
* [Set Up Webhooks](https://razorpay.com/docs/partners/aggregators/onboarding-api/webhooks.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/partners.md)
