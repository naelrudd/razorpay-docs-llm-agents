# UPI Autopay

UPI Autopay allows businesses to set up recurring mandates on a customer's UPI id, enabling automatic debits at a defined frequency without requiring the customer to approve each payment manually. This is ideal for subscriptions, loan repayments, SIP investments and other recurring payment use cases.

**INFO**

**Recommended Integration**

We strongly recommend using the **UPI Intent** flow for mandate registration. Intent provides a seamless native app experience where customers are redirected to their preferred UPI app to approve the mandate. For iOS users, you may continue to use the UPI Collect flow as a fallback.

## How UPI Autopay Works

UPI Autopay works in three stages:

1. **Mandate Registration**: You create a customer, create an order with mandate details and then create an authorisation payment. At each step, you receive identifiers that feed into the next:
    - **Create a Customer** — You receive a `customer_id` that uniquely identifies the customer.
    - **Create an Order** — You send the `customer_id` along with token details (amount, frequency, expiry). You receive an `order_id`.
    - **Create an Authorisation Payment** — You send the `order_id` and `customer_id`. On successful mandate approval, you receive a `payment_id` and a `token_id`. The `token_id` represents the registered mandate and is used for all future debits.
1. **Subsequent Debits**: On the scheduled dates, you use the `token_id` and a new `order_id` to execute debits against the registered mandate without requiring customer intervention (subject to AFA limits).
1. **Token Management**: You can fetch, cancel or delete tokens (mandates) through Razorpay APIs at any point during the mandate lifecycle.

## Use Cases

Razorpay supports UPI Autopay across a range of industries with customised mandate configurations:

    
### Subscriptions and Recurring Services

         OTT platforms, SaaS products, meal delivery services and other subscription businesses can set up monthly or custom-frequency mandates to collect recurring payments automatically.
        

    
### Lending and Loan Repayments

         Lending businesses can use UPI Autopay to collect EMI repayments. Razorpay supports irrevocable mandates for the lending category. Know more under [Custom Autopay](#custom-autopay) below.
        

    
### Investments and SIPs

         Mutual fund distributors and investment platforms can set up mandates for Systematic Investment Plans (SIPs). Investment merchants benefit from extended mandate limits and AFA exemptions (see [Mandate Limits and AFA](#mandate-limits-and-afa) below).
        

    
### Insurance Premium Collection

         Insurance companies can automate premium collection on a monthly, quarterly or yearly basis using UPI Autopay mandates.
        

## Mandate Limits and AFA
 
UPI Autopay mandates are subject to limits defined by NPCI. These limits vary by industry category (MCC). Additional Factor of Authentication (AFA) is required by the RBI for subsequent debits above certain thresholds. When AFA is required, the customer receives a notification on their UPI app and must enter their UPI PIN to approve the payment.
 

Category | MCC Codes | Maximum Mandate Amount | AFA-Free Limit (per debit)
---
Financial Services (Lending, Investments) | 6211, 6300, 7322, 6529 | ₹2,00,000 | ₹1,00,000
---
Insurance Services | 5960 | ₹2,00,000 | ₹1,00,000
---
All other categories | — | ₹99,999 | ₹15,000

 
The minimum mandate amount across all categories is ₹1.
 

**INFO**

**Handy Tips**

- For regular industries, any subsequent debit above ₹15,000 requires the customer to approve the transaction via UPI PIN.
- For lending and investment categories (MCCs 6211, 6300, 7322, 6529, 5960), AFA is not required for debits up to ₹1,00,000. This exemption helps investment platforms process SIP amounts and lenders process EMIs without requiring customer intervention.
- If the subsequent debit amount exceeds the mandate's `max_amount`, the payment will fail.

 
## Custom Autopay
 
Razorpay supports customised Autopay configurations for specific industries. These features are available on request.

    
For investment and lending merchants, Razorpay supports Third-Party Validation (TPV) on UPI Autopay. TPV ensures that the customer's bank account is validated against a pre-approved list before the mandate is registered. This adds a layer of security by confirming that the payment source matches the expected account.
 
Know more about [UPI Autopay with TPV](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/s2s-integration/recurring-payments/upi-tpv/authorization-transaction.md).
    
    
For lending merchants, Razorpay supports irrevocable mandates. When an irrevocable mandate is set up, the customer cannot cancel the mandate from their UPI app. This is important for loan repayment use cases where mandate cancellation could lead to payment defaults.
 
If you want to set up irrevocable mandates, please reach out to our [Support team](https://razorpay.com/support/#request).
    

 
## Integration Steps
 
To integrate UPI Autopay using the S2S (server-to-server) flow, follow these steps:
 
1. [Initiate Mandate Registration](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/s2s-integration/recurring-payments/upi/authorization-transaction.md) - Create a customer, create an order with mandate details and create an authorisation payment. You receive a `token_id` on successful registration.
1. [Fetch and Manage Tokens](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/s2s-integration/recurring-payments/upi/tokens.md) - Retrieve token details, check token states, cancel or delete tokens as needed.
1. [Create Subsequent Payments](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/s2s-integration/recurring-payments/upi/subsequent-payments.md) - Create orders and charge the customer on a recurring basis using the `token_id`.
1. [Webhooks](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/s2s-integration/recurring-payments/upi/webhooks.md) - Set up webhook listeners to receive real-time notifications for mandate and payment events. Integrating with webhooks is strongly recommended as it is the most efficient method for tracking payment and token status changes.
