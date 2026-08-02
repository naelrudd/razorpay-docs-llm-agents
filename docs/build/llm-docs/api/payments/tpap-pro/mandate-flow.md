# Mandates

Razorpay's TPAP Pro - Mandate APIs let you create and manage your mandates. You can create, update, pause/resume, approve, reject and fetch mandates using APIs.

 

 
 Below are the steps to integrate TPAP Pro. You can also refer to our comprehensive [TPAP Pro integration guide](https://razorpay.com/docs/build/llm-docs/payments/tpap-pro/integration-guide.md).

1. [Customer Onboarding](https://razorpay.com/docs/build/llm-docs/api/payments/tpap-pro/customer-onboarding.md)  
2. [Manage Funds and Account](https://razorpay.com/docs/build/llm-docs/api/payments/tpap-pro/funds-account-management.md)  
3. [Payments](https://razorpay.com/docs/build/llm-docs/api/payments/tpap-pro/payments-flow.md)  
4. Mandates
5. [Complaints](https://razorpay.com/docs/build/llm-docs/api/payments/tpap-pro/complaints-flow.md)
6. [UPI Numbers](https://razorpay.com/docs/build/llm-docs/api/payments/tpap-pro/upi-number.md)  
7. [UPI Lite](https://razorpay.com/docs/build/llm-docs/api/payments/tpap-pro/fundsource-lite.md)
 

### Related Guides

[About TPAP Pro](https://razorpay.com/docs/build/llm-docs/payments/tpap-pro.md)
[Integrate With TPAP Pro](https://razorpay.com/docs/build/llm-docs/payments/tpap-pro/integration-guide.md)

### Endpoints

- **post** `/v1/upi/tpap/mandates` - Create Mandates: 
 Creates a mandate.

- **patch** `/v1/upi/tpap/mandates/:umn` - Update or Revoke a Mandate: 
 Updates or revokes a payment.

- **patch** `/v1/upi/tpap/mandates/:umn` - Pause or Resume a Mandate: 
 Pauses or resumes a mandate.

- **post** `/v1/mandates/:umn` - Approve a Mandate: 
 Approves a collect request.

- **post** `/v1/mandates/:umn` - Reject Mandates: 
 Rejects a Mandate.

- **get** `/v1/upi/tpap/mandate?umn=&refresh=true` - Fetch Mandates: 
 Fetch all mandates.
