# UPI Number

Razorpay's TPAP Pro - UPI Number APIs let you check availability, create, port, update, resolve, and fetch UPI Numbers for your customers.

Below are the steps to integrate TPAP Pro. You can also refer to our comprehensive [TPAP Pro integration guide](https://razorpay.com/docs/build/llm-docs/payments/tpap-pro/integration-guide.md).

1. [Customer Onboarding](https://razorpay.com/docs/build/llm-docs/api/payments/tpap-pro/customer-onboarding.md)  
2. [Manage Funds and Account](https://razorpay.com/docs/build/llm-docs/api/payments/tpap-pro/funds-account-management.md)  
3. [Payments](https://razorpay.com/docs/build/llm-docs/api/payments/tpap-pro/payments-flow.md)  
4. [Manage Mandates](https://razorpay.com/docs/build/llm-docs/api/payments/tpap-pro/mandate-flow.md)  
5. [Manage Complaints](https://razorpay.com/docs/build/llm-docs/api/payments/tpap-pro/complaints-flow.md)
6. Manage UPI Numbers
7. [Manage Fundsource Lite](https://razorpay.com/docs/build/llm-docs/api/payments/tpap-pro/fundsource-lite.md)
 

### Related Guides

[About TPAP Pro](https://razorpay.com/docs/build/llm-docs/payments/tpap-pro.md)
[Integrate With TPAP Pro](https://razorpay.com/docs/build/llm-docs/payments/tpap-pro/integration-guide.md)

### Endpoints

- **post** `/v1/upi/tpap/upi_number/available` - Check UPI Number Availability: 
Check if a UPI number is available to create or port.

- **post** `/v1/upi/tpap/upi_number` - Create or Port UPI Number: 
Create a new UPI number or port an existing one to your VPA.

- **patch** `/v1/upi/tpap/upi_number` - Update UPI Number: 
Update or deactivate a UPI number.

- **get** `/v1/upi/tpap/upi_number` - Fetch UPI Numbers: 
Fetch all UPI numbers linked to a customer.

- **post** `/v1/upi/tpap/upi_number/resolve` - Resolve UPI Number: 
Resolve UPI number to fetch linked VPA and merchant info.
