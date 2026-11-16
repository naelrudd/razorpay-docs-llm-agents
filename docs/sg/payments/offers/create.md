> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create Offers

> Create and manage Offers for customers from the Razorpay Dashboard.

Available in
🇮🇳 India
🇸🇬 Singapore

You can create offers from the Dashboard to promote your business. Some of the ways you can control offers at a granular level are:

* Configuring the payment methods permitted for the offer.
* Limiting the number of times the offer can be availed.

> [!NOTE]
>
> **Handy Tips**
>
> * You cannot edit an offer. To make changes, disable the previous offer and create a new one.
> * Only the owner and admin roles can create offers.

## Design Offers

You should consider the following while creating offers:

* Availability of the offer at Checkout.
* A maximum number of times an offer should be applied.
* Whether customers should be allowed to complete payments if validations are not met in the offers.
* Maximum discount that can be availed using the offer.

## Create Offers

To create an offer:

1. Log in to the Dashboard.

2. Navigate to **Offers** and click **+ Create New Offer**.

3. The **Create an Offer** window displays four sections. Complete all sections to create the offer:
   * [Description](#offer-description)
   * [Discount Type](#discount-type)
   * [Applicable On](#applicable-on)
   * [Offer Validity](#offer-validity)

You can review the offer configurations at the end under the [**Overview**](#offer-overview) tab.

### Offer Description

In the **Description** section, enter the following details. All the fields are mandatory.

1. **Offer Name**: Enter the name of the offer. For example, **Monsoon Offer**. This appears at Checkout.

2. **Display Text**: Enter a meaningful description for the offer. For example, **10% discount on PayNow payments**. This appears at Checkout.

3. **Terms**: Enter the terms and conditions for the offer.

4. **Offer Type**: Select the type of offer that you want to create. The possible value is:
   * **Instant**: The offer is applied instantly. That is, the customer pays only the discounted amount while making the payment.

5. Click **Next**.

### Discount Type

There is one type of discount that can be offered:

The following section explain the configuration in detail.

#### Instant

In the **Discount Type** section, enter the discount details that should be applied to the offer.

1. In the **Discount Type** field, select the type of discount that should be applied to the offer: **Percentage** or **Flat**
   * **Flat**: In this type, a fixed amount is deducted from the original amount.
     1. **Minimum Order amount**: Enter the minimum bill amount for which the offer can be applied.
     2. **Discount worth**: Enter an amount by which the original price should be reduced. For example, if \*\*\*\* is the **Flat** discount applied, then an amount of **30** is deducted from the original price.

   * **Percentage**: In this type, the offer is calculated in terms of percentage.
     1. **Minimum Order amount**: Enter the minimum bill amount for which the offer can be applied.
     2. **Discount Worth**: The percentage by which the original price should be reduced. For example, if **10** is the **Percentage** discount to be applied, on an order amount of **300**, **30** will be deducted.
     3. **Maximum Discount**: The maximum amount that can be deducted from the bill amount. For example, you can ensure that the customer cannot avail a discount higher than **500**, irrespective of the order amount.
2. Click **Next**.

### Applicable On

Under the **Applicable On** tab, enter details of the payment method you want to enable the offers. The fields depend upon the selected payment method.

1. Select the **Payment Method** and **Issuer**.
   * **Payment Method**: The payment method for which the created offer can be applied. Select from the available options, which are configured for your account:
     * **Card**
     * **PayNow**
   * **Card**: If you choose the payment method as **Card**, enter the card-related details as described below:
     * **Card Type**: Select the type of the card. The possible values are:
       * **Debit Card**
       * **Credit Card**
       * **Both Debit and Credit Cards** (This is applicable only if you choose **Card** as the payment method)
     * **Bank**: Select the bank that issued the card.
     * **Network**: Select the network of the card.
     * **IINs**: Enter the first six digits of the card (that is printed on the front of the card). In the case of Rupay cards, enter the tokenised IIN only.
2. Click **Next**.

### Offer Validity

Under the **Offer Validity** tab, set how long the offer should be valid and how you want to handle the payment failure situations.

1. **Starting On**: Select the **Starts Immediately** check box for the offer to come into effect immediately. Alternatively, you can select the date and the time from which the created offer should become active.
2. **Expires On**: Select the date and time at which the offer should end. For example, **31 Oct 2020** at **11:59pm**.
3. **On Payment Failure**: Define how to handle payment failure.
   * **Do not allow payment to go through**: The payment is failed.
   * **Allow customer to pay without availing offer**: The payment is allowed even though the set validations are not met. However, the offer is not applied to the bill amount. The customer will be charged the entire order amount.
     For this example, we will allow payments to go through.
4. **Max Usage**: Set the number of times the offer should be applied across all transactions. For example, **100**.
5. **Show Offer on Checkout**: Select this check box for the offer to be displayed for all Standard Checkout payments including [Payment Links](https://razorpay.com/docs/sg/payments/payment-links). Know more about the different ways to [display offers on Standard Checkout](https://razorpay.com/docs/sg/payments/offers/standard-integration.md).

> [!WARNING]
>
> **Watch Out!**
>
> If you are not using products and plugins like Razorpay Magento, Shopify, WooCommerce and Payment Links to accept payments, you **should** integrate offers with the [Orders API](https://razorpay.com/docs/api/orders.md) for the feature to work.

6. Click **Next**.

### Offer Overview

Click the **Overview** tab to view the summary of the offer that you just created.

1. **Terms and Conditions**: Select the check box after you have read the disclaimer.
2. Click **Create Offer**.

By default, all the created offers will be in the **enabled** state.

## Test the Offer

You can test the created offer for all Standard Checkout payments, including [Payment Links](https://razorpay.com/docs/sg/payments/payment-links).

> [!NOTE]
>
> **Handy Tips**
>
> * You can toggle between Live and Test Modes on your **Dashboard**. Navigate to the top menu ribbon and click the drop-down icon against **Live Mode**. Toggle to **Test Mode** and test the offers enabled.
>
> * You can make test payments using one of the payment methods at the Checkout. No money is deducted from your account as this is a simulated transaction.

For this example, we will test the offer on a valid Payment Link. Follow the steps given below:

1. Select the **Payment Link Id** you wish to test the created offer from the Dashboard.

2. Copy the **Payment Link** URL and open it in your browser.

3. Enter your contact details and click **Proceed**. The relevant offers appear upfront on checkout.

4. Select the offer you created from the Dashboard and click **Apply Offer**.

5. Select the payment option you created the offer on from the Dashboard. Enter the required [test details](https://razorpay.com/docs/sg/payments/payments/test-card-details.md) and click **PAY**.

6. Select Success or Failure, depending on which flow you wish to test.

7. You should see a confirmation message depending on the flow you have selected.

On successful payment, you should have received a discount on your payment. You can verify this by navigating to the Transactions → Payments tab and viewing the payment details.

## Integrate Offer with Standard Checkout

Now that an Offer is created, you should integrate Offers with Checkout for customers to avail the discounts and make payments.

Know how to [integrate Offers with Standard Checkout](https://razorpay.com/docs/sg/payments/offers/standard-integration.md).

## Disabling Offers

To disable an offer:

1. Log in to the Dashboard.
2. Navigate to **Offers** to view a summary of the existing offers.
3. Select the required Offer\_id.
4. In the pane that appears, go to the **Status** field and click **Disable**.

## Next Steps

After you create an offer, it needs to be integrated with Checkout for the customers to view and avail the offers while making payments. Know more about [integrating offers with Standard Checkout](https://razorpay.com/docs/sg/payments/offers/standard-integration.md).

### Related Information

* [Tutorial - How to Create Offers](https://razorpay.com/docs/sg/payments/offers/tutorial.md)
* [Integrate offers with Standard Checkout](https://razorpay.com/docs/sg/payments/offers/standard-integration.md)
* [Offers FAQs](https://razorpay.com/docs/sg/payments/offers/faqs.md)
