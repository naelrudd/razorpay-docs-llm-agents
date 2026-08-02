# Instant Settlements

This section has information on APIs used as part of Razorpay Capital. With [Instant Settlements](https://razorpay.com/docs/build/llm-docs/payments/settlements/instant.md) (earlier known as On-demand Settlement APIs), you get access to your funds as and when you want. You can manage Instant Settlements using APIs or from the [Dashboard](https://razorpay.com/docs/build/llm-docs/payments/settlements/instant.md#initiate-an-instant-settlement).

 

 

 
**INFO**

**Feature Request**

This is an on-demand feature. Please raise a request with our [Support team](https://razorpay.com/support/#request) to get this feature activated on your Razorpay account.

 Fork the Razorpay Postman Public Workspace and try the Instant Settlements APIs using your [Test API Keys](https://razorpay.com/docs/build/llm-docs/api/authentication.md#generate-api-keys).

 [](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-dbf2da3b-c795-4e57-b910-cf9a838ee5ea)
 

### Related Guides

[About Instant Settlements](https://razorpay.com/docs/build/llm-docs/payments/settlements/instant.md)

### Endpoints

 - **post** `https://api.razorpay.com/v1/settlements/ondemand` - Create an Instant Settlement: 
 Creates an instant settlement.
 

 - **get** `/v1/settlements/ondemand` - Fetch All Instant Settlements: 
 Retrieves all instant settlements.
 

 - **get** `/v1/settlements/ondemand/:setlod_id` - Fetch Instant Settlement With ID: 
 Retrieves instant settlements using id.
 

 - **get** `/v1/settlements/ondemand/?expand[]=ondemand_payouts` - Fetch All Instant Settlements With Payout Details: 
 Retrieves payout details as part of the response for all instant settlements.
 

 - **get** `/v1/settlements/ondemand/:id?expand[]=ondemand_payouts` - Fetch Instant Settlement With ID With Payout Details: 
 Retrieves payout details as part of the response for a specific instant settlement.
