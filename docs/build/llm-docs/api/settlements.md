# Settlements

Razorpay [Settlements](https://razorpay.com/docs/build/llm-docs/payments/settlements.md) is the process in which the money received from your customers is settled to your bank account. You can manage settlements using APIs or from the [Dashboard](https://razorpay.com/docs/build/llm-docs/payments/settlements/dashboard.md).

Captured payments are automatically settled to the bank account submitted to us as part of your KYC verification as per your [settlement cycle](https://razorpay.com/docs/build/llm-docs/payments/settlements.md#settlement-cycle).

 Fork the Razorpay Postman Public Workspace and try the Settlements APIs using your [Test API Keys](https://razorpay.com/docs/build/llm-docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys).

### Related Guides

[About Settlements](https://razorpay.com/docs/build/llm-docs/payments/settlements.md)

### Endpoints

- **get** `/v1/settlements/` - Fetch All Settlements: 
 Retrieves all settlements.

- **get** `/v1/settlements/:id` - Fetch Settlements With ID: 
 Retrieves settlements with id.

- **get** `/v1/settlements/recon/combined?year=yyyy&month=mm` - Fetch Settlement Recon Details: 
 Retrieves details of all Settlement Recon.
