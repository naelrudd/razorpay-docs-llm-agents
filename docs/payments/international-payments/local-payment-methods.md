> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Local Payment Methods

> Offer local payment methods as a payment method to customers at Razorpay Checkout.

Available in
🇮🇳 India

Razorpay supports the following local payment methods instruments to accept payments across different geographies and varied currencies.

* [Giropay](https://razorpay.com/docs/payments/payment-methods/giropay.md) for German customers.
* [Sofort](https://razorpay.com/docs/payments/payment-methods/sofort.md) for European customers.
* [Trustly](https://razorpay.com/docs/payments/payment-methods/trustly.md) for UK and European customers.
* [POLi](https://razorpay.com/docs/payments/payment-methods/poli.md) for Australian customers.

You can accept international payments from customers in the form of online local payment methods using the Razorpay Checkout form.

## Request Local Payment Method

To request Local Payment Method, follow these steps:

1. Log in to the Dashboard.
2. Navigate to **Account & Settings** → **International payments** (under Payment methods).
3. Click **Activate** beside **Local payment methods**.

   ![Razorpay Dashboard image of local payment method activation](https://razorpay.com/docs/build/browser/assets/images/local-payment-method-activate.jpg)
4. An **Instant Bank Transfers Activation** request form appears. Select the payment instrument to be enabled on your Checkout. Click **Save & Next**.

> [!NOTE]
>
> **Handy Tips**
>
> You can use one or multiple payment instruments as per your needs.

![Razorpay Dashboard image of bank transfer activation-form](https://razorpay.com/docs/build/browser/assets/images/instant-bank-transfer-activation-form.jpg)

5. Fill in the required details and click **Save & Next**.

> [!NOTE]
>
> **Handy Tips**
>
> * If you are an existing business, some of the required details will be auto-filled.
> * You can click the **Edit** button to fill in the incomplete details before submitting the form.

![Razorpay Dashboard image of bank transfer form details](https://razorpay.com/docs/build/browser/assets/images/instant-bank-transfer-form-details.jpg)

6. Fill in the **Management/Ownership** details in the form. When complete form details are filled, click **Submit form** button.

   ![Razorpay Dashboard image of bank transfer submit form](https://razorpay.com/docs/build/browser/assets/images/instant-bank-transfer-submit-form.jpg)

7. After the form is submitted, the request is sent to activate the selected payment instruments. The feature enablement request goes to our banking partners and will take 15 - 20 business days to be approved.

   ![Razorpay Dashboard image of bank transfer requested status](https://razorpay.com/docs/build/browser/assets/images/instant-bank-transfer-requested-status.jpg)

After the payment instrument is enabled, you will see the **Activated** status beside the selected one.

![Razorpay Dashboard image of bank transfer activated status](https://razorpay.com/docs/build/browser/assets/images/instant-bank-transfer-activated-status.jpg)

## Frequently Asked Questions (FAQs)

> [accordion] Am I eligible for this feature?
>
> All international-enabled businesses will have this feature on the  Dashboard.

> [accordion] What are the alternative payment methods available via Razorpay?
>
> Razorpay already supports PayPal, and has now launched POLi for Australians, Trustly for the UK and Europeans, Sofort for Europeans and Giropay for German customers.

> [accordion] What are the prices for Alternative Payment Methods?
>
> You will be charged 3.0% Platform fee for accepting payments via the **Local Payment Methods**.

> [accordion] Why is my request rejected?
>
> The request can be rejected due to multiple reasons:
>
> * Risky business category: The respective payment method (lets say, Trustly) is not comfortable with your business model.
> * Incorrect account details: The banking partner rejects your request if you have provided any incorrect information at the time of your application.
> * Outdated website: The customer-facing website is thoroughly checked by our banking partners. The banking partner can reject your request if the website is not updated or has a limited information, including details such as **Terms & Conditions**, **Delivery timelines**, **Refund & Cancellation** policies and so on.

> [accordion] Is this feature available on all Razorpay integrations?
>
> We will give early access to sellers on Razorpay Standard Checkout. The feature will be rolled out to custom and server-to-server (s2s) integration in the upcoming sprints.

> [accordion] How much time will it take for my request to get approved?
>
> The feature enablement request goes to our banking partners and will take 15 - 20 business days to be approved.
