> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Instant Settlements

> Check Razorpay Capital Instant Settlement APIs (On-demand Settlement APIs).

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

This section has information on APIs used as part of Razorpay Capital. With [Instant Settlements](https://razorpay.com/docs/payments/settlements/instant.md) (earlier known as On-demand Settlement APIs), you get access to your funds as and when you want. You can manage Instant Settlements using APIs or from the [Dashboard](https://razorpay.com/docs/payments/settlements/instant.md#initiate-instant-settlements).

> [!NOTE]
>
> **Feature Request**
>
> This is an on-demand feature. Please raise a request with our [Support team](https://razorpay.com/support/#request) to get this feature activated on your Razorpay account.

Fork the Razorpay Postman Public Workspace and try the Instant Settlements APIs using your [Test API Keys](https://razorpay.com/docs/api/authentication.md#generate-api-keys).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-dbf2da3b-c795-4e57-b910-cf9a838ee5ea)

> [card] [Create an Instant Settlement](https://razorpay.com/docs/api/settlements/instant/create.md)
>
> `POST` `https://api.razorpay.com/v1/settlements/ondemand`
>
> Creates an instant settlement.

> [card] [Fetch All Instant Settlements](https://razorpay.com/docs/api/settlements/instant/fetch-all.md)
>
> `GET` `/v1/settlements/ondemand`
>
> Retrieves all instant settlements.

> [card] [Fetch Instant Settlement With ID](https://razorpay.com/docs/api/settlements/instant/fetch-with-id.md)
>
> `GET` `/v1/settlements/ondemand/:setlod_id`
>
> Retrieves instant settlements using id.

> [card] [Fetch All Instant Settlements With Payout Details](https://razorpay.com/docs/api/settlements/instant/fetch-all-payout.md)
>
> `GET` `/v1/settlements/ondemand/?expand[]=ondemand_payouts`
>
> Retrieves payout details as part of the response for all instant settlements.

> [card] [Fetch Instant Settlement With ID With Payout Details](https://razorpay.com/docs/api/settlements/instant/fetch-with-id-payout.md)
>
> `GET` `/v1/settlements/ondemand/:id?expand[]=ondemand_payouts`
>
> Retrieves payout details as part of the response for a specific instant settlement.

## Related Guides

* [About Instant Settlements](https://razorpay.com/docs/payments/settlements/instant.md)
