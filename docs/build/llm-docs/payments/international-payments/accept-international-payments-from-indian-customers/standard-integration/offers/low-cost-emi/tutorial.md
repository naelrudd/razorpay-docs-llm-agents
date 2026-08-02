# Tutorial - How to Create Low Cost EMI Offers

Let us create an offer from the Dashboard. For example, let us assume you are the manager of Acme Mobiles and Accessories, an online smartphone store. You want to offer discounts on online purchases to attract customers and increase sales.

You want to create a Diwali Offer with the following settings:

Offer Criteria | Offer Information
---
Offer Name | Diwali Dhamaka 
---
Display Text | Low Cost EMI Offers
---
Offer Type | Instant
---
Minimum Order Amount | ₹4,000
---
Maximum Order Amount | ₹1,00,000
---
Issuing Bank | ICICI Bank 
---
EMI Tenures | 6, 9 and 12 months

## Create Low Cost EMI Offers

Watch this video to see how to create an offer.

To create Low Cost EMI offers:

1. Log in to the Dashboard.
2. Navigate to **Offers** and click **+ Create No & Low Cost EMI**.
    
3. The **Create an Offer** wizard appears with the following four sections. Enter details in all these sections for the offer to be created:
    - [**Description**](#description)
    - [**Discount Type**](#discount-type)
    - [**Applicable On**](#applicable-on)
    - [**Offer Validity**](#offer-validity)

You can review the offer configurations at the end under the [**Overview**](#overview) tab.

### Description

In the **Description** section, enter the following details. All the fields are mandatory.

1. **Offer Name**: Enter the name of the offer. For example, **Diwali Dhamaka**.
2. **Display Text**: Enter a meaningful description for the offer. For example, **Low Cost EMI Offers**. This appears at the Checkout.
3. **Terms**: Enter the terms and conditions for the offer.
4. Click **Next**.
    

### Discount Type

In the **Discount Type** section, enter the discount details that should be applied for the offer.

1. **Minimum Order amount**: Enter the minimum bill amount for which the Low Cost EMI offer can be applied. For example, a customer must purchase an article of at least **₹4,000** to avail Low Cost EMI. This is a mandatory field.
2. **Maximum Order amount**: Enter the maximum bill amount for which the Low Cost EMI offer can be applied. For example, customers can avail Low Cost EMI if they purchase a phone worth a maximum of **₹1,00,000**.
3. Click **Next**.
    

### Applicable On

In the **Applicable On** tab, fill in the following details:

1. **Issuer**: Select the bank that will be issuing the Low Cost EMI. For example, `ICICI Bank`.
2. **EMI Tenure**: Select the tenure to be listed at the Checkout. For this example, we will select 6, 9 and 12 months as the supported tenures.
3. **EMI Offer Type**: Select **Low Cost EMI** from the drop-down list and configure the interest rate that you will bear for each tenure. The remaining interest rate is auto-filled and is borne by the customer. For example, enter **2.55** in the **Interest % borne by merchant (you**)** field. The remaining **1.95**** is auto-filled in the **Interest % borne by your customer** field.
4. Click **Next**.
    

### Offer Validity

Under the **Offer Validity** tab, set how long the offer should be valid and how you want to handle the payment failure situations:

1. **Starting On**: Select the **Starts Immediately** check box for the offer to come into effect immediately.
2. **Expires On**: Select the date and time the offer should end. For example, **30 Nov 2023** at **11:59pm**.
3. **On Payment Failure**: Define how to handle payment failure.
    - **Do not allow payment to go through**: The payment has failed.
    - **Allow customer to pay without availing offer**: The payment is allowed even though the set validations are not met. However, the offer is not applied to the bill amount. The customer will be charged the entire order amount. 

    We will allow payments to go through without an offer being availed.
4. **Max Usage**: Set the number of times the offer should be applied across all transactions. For example, **100**.
5. **Show Offer on Checkout**: Select this check box for the created offer to be displayed for all Standard Checkout payments including [Payment Links](https://razorpay.com/docs/build/llm-docs/payments/payment-links.md).
6. Click **Next**.
    

### Overview

Click the **Overview** tab to view the offer summary you just created.

1. **Terms and Conditions**: Select the check box after you have read the disclaimer.
2. Click **Create Low Cost EMI**.
    

By default, all the created offers are in the **enabled** state.

## Integrate Low Cost EMI Offer with Standard Checkout

After the offer is created, you should integrate it with Checkout so that customers can avail discounts while making payments. Know more about [integrating offers with Standard Checkout](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers/standard-integration/offers/low-cost-emi/standard-integration.md).

### Related Information

- [About Low Cost EMI Offers](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers/standard-integration/offers/low-cost-emi.md)
- [Low Cost EMI FAQs](https://razorpay.com/docs/build/llm-docs/payments/international-payments/accept-international-payments-from-indian-customers/standard-integration/offers/low-cost-emi/faqs.md)
