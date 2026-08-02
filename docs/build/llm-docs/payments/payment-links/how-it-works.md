# How Payment Link Works

Understand the complete end-to-end flow about how you can use Razorpay Payment Links.

## Workflow 

The steps given below give a detailed view on the lifecycle of a Payment Link.

  
### Step 1: Create a Payment Link

     [Create a Payment Link](https://razorpay.com/docs/build/llm-docs/payments/payment-links/create.md) by providing all the required details. You can set an expiry date and enable partial payments. 

      

      
**INFO**

**Handy Tips**

You can [update](https://razorpay.com/docs/build/llm-docs/payments/payment-links/edit.md) or create a [duplicate](https://razorpay.com/docs/build/llm-docs/payments/payment-links/duplicate.md) Payment Link.

**Payment Links APIs** 

- [Create a Payment Link](https://razorpay.com/docs/build/llm-docs/api/payments/payment-links/create-standard.md)
- [Edit a Payment Link](https://razorpay.com/docs/build/llm-docs/api/payments/payment-links/update-standard.md)
- [Cancel a Payment Link](https://razorpay.com/docs/build/llm-docs/api/payments/payment-links/cancel-standard.md)

      
    

  
### Step 2: Send a Payment Link

     Send a Payment Link to a customer via email and/or SMS. The customer receives the link via SMS and email. They can open the link and pay using one of the available [payment methods](https://razorpay.com/docs/build/llm-docs/payments/payment-links.md#list-of-supported-payment-methods).
    

  
### Step 3: Receive Payments

     The customer clicks the Payment Link and tries to make the payment.

      - The customer makes the payment. If [partial payment](https://razorpay.com/docs/build/llm-docs/payments/payment-links/partial-payments.md) is enabled, the customer can choose the amount to be paid. 
      - The customer chooses the mode of payment.

      The customer makes a successful payment. The Payment Link is marked as `paid` or `partially` paid. You receive a notification about the payment.

      
**INFO**

**Handy Tips**

After the payment is captured, the amount is settled to your account as per the settlement schedule. Know more about [payments](https://razorpay.com/docs/build/llm-docs/payments/payments.md), [settlements](https://razorpay.com/docs/build/llm-docs/payments/settlements.md)   [, refunds](https://razorpay.com/docs/build/llm-docs/payments/refunds.md) and [disputes](https://razorpay.com/docs/build/llm-docs/payments/disputes.md).

    

  
### Step 4: Track Payment Links and Reports

     - **Notifications:** You receive notifications regarding activity on Payment Links via emails and webhook. Know more about [subscribing to Webhooks](https://razorpay.com/docs/build/llm-docs/payments/payment-links/subscribe-to-webhooks.md).
     - **Track Payments:** Track payments made against the issued Payment Links on Dashboard. Click **Payment Links** from the left menu. All the links are listed with their status under Payment Links.
     - **Reports:** Detailed insights can be gained using reports and real-time data on the Dashboard. These reports can then be used for accounting and reconciliation purposes. Know more about [reports](https://razorpay.com/docs/build/llm-docs/payments/dashboard/reports.md#payment-links).
    

#### Related Information

- [Payment Links](https://razorpay.com/docs/build/llm-docs/payments/payment-links.md)

- [FAQs](https://razorpay.com/docs/build/llm-docs/payments/payment-links/faqs.md)

- [Payment Links APIs](https://razorpay.com/docs/build/llm-docs/payments/payment-links/apis.md)
