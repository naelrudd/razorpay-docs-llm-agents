> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Superior Plan Integration Guide

> Send customer and order details with your international card payments to get the full benefit of the Razorpay Superior plan.

Available in
🇮🇳 India

The Superior plan raises your success rate on international card payments by approving more of them. It also covers fraud chargebacks on your international card payments, with no change to your settlement cycle. Superior was earlier called Chargeback Shield.

To get the full benefit, send a few extra details with each order: who the customer is, what they are buying and, for travel, who is travelling. Our risk model uses these details to approve genuine payments it would otherwise decline.

This page links to the integration guide for your checkout type and business category.

## Prerequisites

* Superior is active on your account. Turn it on or off from the **Superior Plan** card on your Razorpay Dashboard.
* Your business is in one of the [categories that need extra details](#categories-that-need-extra-details).

## Categories That Need Extra Details

Superior covers international card payments in every business category. The extra details on this page are needed today only for these categories:

* E-commerce
* Digital services, for example, edtech, SaaS, insurance and web development
* Airlines and online travel agencies (OTAs)
* Hotels

If your business is in another category, there are no extra details to send yet.

> [!NOTE]
>
> **Handy Tips**
>
> * You do not need to send extra details for recurring and subscription payments.
> * Shopify stores need no integration. We collect the details through the Shopify app, so you can skip this guide.

## Choose Your Integration Guide

Pick the row for how you accept payments and the column for what you sell. Each guide lists the exact fields to send and where to send them.

| How You Integrate | E-commerce and Digital Services | Airlines and OTAs | Hotels |
| - | - | - | - |
| Standard Checkout | [E-commerce and digital guide](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/chargeback/build-integration-ecommerce.md) | [Travel guide](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/chargeback/build-integration-travel.md) | [Hotel guide](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/chargeback/build-integration-hotel.md) |
| Custom Checkout | [E-commerce and digital guide](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/chargeback/build-integration-ecommerce.md) | [Travel guide](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/chargeback/build-integration-travel.md) | [Hotel guide](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/chargeback/build-integration-hotel.md) |
| S2S | [E-commerce and digital guide](https://razorpay.com/docs/payments/payment-gateway/s2s-integration/json/v2/build-integration/international-cards/e-commerce.md) | [Travel guide](https://razorpay.com/docs/payments/payment-gateway/s2s-integration/json/v2/build-integration/international-cards/travel.md) | [Hotel guide](https://razorpay.com/docs/payments/payment-gateway/s2s-integration/json/v2/build-integration/international-cards/hotel.md) |

### Category Tips

* **Digital services**: Follow the e-commerce and digital guide. Skip the shipping address, which does not apply to digital services.
* **Airlines**: Pass the full flight number in `carrier_code`.
* **Travel and hotels**: Pass the customer's billing address inside the `customer_details` object.
* **S2S integrations**: Add the Razorpay Shield JS script to your checkout page first. This is step 1.1 of each S2S guide.

## How the Integration Works

1. **Build**: Follow your guide from the table above. Send all mandatory fields. Recommended fields improve approvals further.
2. **Test**: Run test payments in test mode. Use the Test Integration page for [Standard Checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/chargeback/test-integration.md) or [Custom Checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/chargeback/test-integration.md).
3. **Go live**: Complete the Go-Live Checklist for [Standard Checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard/chargeback/go-live-checklist.md) or [Custom Checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/chargeback/go-live-checklist.md) and switch to live API keys. Once the details are flowing in production, tell your account manager or raise a support request from your Razorpay Dashboard.
4. **Integration audit**: Our team audits your orders to check that the fields are passing through correctly. We tell you if any further changes are needed.
5. **Enhanced approvals on**: Once your integration is complete and correct, you get the full benefit of the Superior plan.

### Related Information

* [International Payments](https://razorpay.com/docs/payments/international-payments)
* [Support for Non-3D Secure Transactions](https://razorpay.com/docs/payments/international-payments/support-non-3ds.md)
* [International Chargebacks](https://razorpay.com/docs/payments/disputes/international-chargebacks.md)
* [Visa Merchant Elevated Risk Program (MERP)](https://razorpay.com/docs/payments/international-payments/visa-merp.md)
