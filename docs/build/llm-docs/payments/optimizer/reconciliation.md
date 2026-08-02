# Single Reconciliation View

On the Dashboard, you can view:
- [Transaction details for payments and refunds](https://razorpay.com/docs/build/llm-docs/payments/optimizer/reconciliation.md#transactions-details).
- [Settlement details of the external payment gateways](https://razorpay.com/docs/build/llm-docs/payments/optimizer/reconciliation.md#settlement-details).

## Transactions Details

### Payments

You can view the payment details on the Dashboard by specifying various filters.

    
### Filters

         

            Filter | Description
            ---
            Payment Id | The ID of the payment done.
            ---
            Processed by | Payment gateway through which the payment was processed.
            ---
            Duration | The time period for which you want to view the payments.
            ---
            Status | The state of the payment. Know more about [Payment states](https://razorpay.com/docs/build/llm-docs/payments/payments.md#payment-life-cycle).
            ---
            Email | The email id linked to the payment.
            
        

To view the transaction details of Payments:
1. Log in to the Dashboard.
2. Select **Transactions** from the left menu and click **Payments**.
3. Select the Payment Id to view the:
    - Payment details
    - Fee collected 
    - Tax collected 
    - Settlement id within which the transaction was settled.
    - Optimizer Details

### Refunds

You can view the refund details on the Dashboard by specifying various filters.

    
### Filters

         

            Filter | Description
            ---
            Payment Id | The ID of the payment done.
            ---
            Processed by | List of gateways through which the payment was processed.
            ---
            Status | The state of the refund (processed, processing and failed).
            ---
            Refund Id | The unique id of the processed refund.
            
        

To view the transactions details of Refunds:
1. Log in to the Dashboard.
2. Select **Transactions** from the left menu and click **Refunds**.
3. Select the Refund Id to view the:
    - Status and history of the refund
    - Amount
    - Refund type
    - Optimizer Details

## Settlement Details

You can [download](https://razorpay.com/docs/build/llm-docs/payments/dashboard/reports.md#download-reports) or [schedule](https://razorpay.com/docs/build/llm-docs/payments/dashboard/reports.md#schedule-reports) the **Optimizer Single View Recon Report** from the Dashboard to view the settlement details.

**INFO**

**Handy Tips**

You can contact the [Support team](https://razorpay.com/support/#request) for a customised report that meets your business requirements.

## Supported Payment Gateways

Payment Gateway | Availability
---
PayU | Live
---
Paytm | Live
---
Billdesk | Live
---
Cashfree | Live
---
PineLabs | Coming Soon

 
### Related Information

- [Add Payment Providers](https://razorpay.com/docs/build/llm-docs/payments/optimizer/add-payment-providers.md)
- [SR Analytics Dashboard](https://razorpay.com/docs/build/llm-docs/payments/optimizer/success-rate.md)
- [Roles and Permissions](https://razorpay.com/docs/build/llm-docs/payments/optimizer/roles-and-permissions.md)
- [Tokenisation for Optimizer](https://razorpay.com/docs/build/llm-docs/payments/optimizer/tokenisation.md)
- [Supported Gateways and Aggregators](https://razorpay.com/docs/build/llm-docs/payments/optimizer/supported-gateways-aggregators.md)
- [FAQs](https://razorpay.com/docs/build/llm-docs/payments/optimizer/faqs.md)
