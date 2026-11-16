> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Payment Link

> Create Standard Payment Links and UPI Payment Links.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can create 2 types of Payment Links using the Razorpay Dashboard:

* [Standard Payment Links](#create-a-standard-payment-link-from-dashboard)
* [UPI Payment Links](#create-a-upi-payment-link-from-dashboard)

## Create a Standard Payment Link From Dashboard

You can create a Standard Payment Link to accept payments from your customers. When you create a Payment Link, it moves to **Issued** state by default.

Watch this video to see how to create a Standard Payment Link.\


[YouTube video player](https://www.youtube.com/embed/_FrOVkuqGVo)

> [accordion] To create a Standard Payment Link:
>
> 1. Log in to the Dashboard.
> 2. Go to the **PAYMENT PRODUCTS** section and click **Payment Links**.
> 3. Click **+ Create Payment Link**.
> 4. Enter the required details in the Standard Payment Link pop-up page.
>
>    <ul>
>      <li>**Amount** (Mandatory): Select the currency and amount for the Payment Link. For example, select `₹` and enter`1000` for ₹1,000. You can also accept payments in [international currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).</li>
>      <li>**Payment For** (Optional): Enter a description entered. For example, `School fees for Gaurav Kumar - Class XII B`.</li>
>      <li>**Customer Details** (Optional): Enter the customer's email and phone number. For example, `9876543210` and `gaurav.kumar@example.com`.</li>
>      <li>**Notify via Email** (Optional): Select this option if you want us to send the Payment Link to the customer via email. Available only if you have entered the customer's email.</li> \
>      Customers receive email in the following format:
>
>      ![Payment link email format](https://razorpay.com/docs/build/browser/assets/images/payment-link-email-templete.jpg)
>
>      <li>**Notify via SMS** (Optional): Select this option if you want us to send the Payment Link to the customer via SMS. Available only if you have entered the customer's phone number. \
>      &#x20;Customers receive SMS in the following format:
>      For example, `Acme Corp has requested payment of INR 100. You can pay through this link: https://rzp.io/rzp/D6W1Xk3u - Razorpay`</li>
>      <li>**Reference Id** (Optional): Provide a unique reference number for the link. For example, `Adbb001`.</li>
>
>      <li>**Link Expiry** (Optional): The date and time at which the Payment Link should expire.</li>
>      <li>**Notes** (Optional): Provide the internal notes for the Payment Link. For example:\
>      <ul><li>Title (key): Acme Corp.</li><li>Description (value): Birthday cake Feb.</li></ul></li>
>      <li>Review the details and click **Create Payment Link**.</li>
>    </ul>

## Create a UPI Payment Link From Dashboard

You can create a UPI Payment Link to collect funds from your customers via the Dashboard. When you create a Payment Link, it moves to the **Issued** state by default.

Watch this video to see how to create a UPI Payment Link.\


[YouTube video player](https://www.youtube.com/embed/aBLKnhu-J14?si=sxFruRjb96YUQi0L)

> [accordion] To create a UPI Payment Link:
>
> 1. Log in to the Dashboard.
> 2. Navigate to **Payment Links**.
> 3. Click **Create Payment Link**.
> 4. Click **UPI Payment Link**.
> 5. Enter the required details in the UPI Payment Link pop-up page.
>
>    <ul>
>      <li>**Amount** (Mandatory): Select the currency and amount for the Payment Link. For example, select `₹` and enter`1000` for ₹1,000.</li>
>      <li>**Payment For**: Enter a description entered. For example, `School fees for Gaurav Kumar - Class XII B`.</li>
>      <li>**Customer Details**: Enter the customer's email and phone number. For example, `9876543210` and `gaurav.kumar@example.com`.</li>
>      <li>**Notify via Email** (Optional): Select this option if you want us to send the Payment Link to the customer via email. Available only if you have entered the customer's email.</li> \
>      Customers receive email in the following format:
>
>      ![Payment link email format](https://razorpay.com/docs/build/browser/assets/images/payment-link-email-templete.jpg)
>
>      <li>**Notify via SMS** (Optional): Select this option if you want us to send the Payment Link to the customer via SMS. Available only if you have entered the customer's phone number. \
>      Customers receive SMS in the following format:
>      For example, `Acme Corp has requested payment of INR 100. You can pay through this link: https://rzp.io/rzp/D6W1Xk3u - Razorpay`</li>
>      <li>**Reference Id**: Provide a unique reference number for the link. For example, `Adbb001`.</li>
>      <li>**Link Expiry**: The date and time at which the Payment Link should expire.</li>
>      <li>**Internal Notes**: Provide the internal notes for the Payment Link. For example:<ul><li>Title (key): Acme Corp.</li><li>Description (value): Birthday cake Feb.</li></ul></li>
>    </ul>
> 6. Review the details and click **Create Payment Link**.
>
> After a UPI Payment Link created, it appears in the list of Payment Links.

## Make Test Payments for Payment Links

> [!NOTE]
>
> **Handy Tips**
>
> We recommend you to create Payment Links in **Test Mode** for testing purposes.

> [!WARNING]
>
> **Test Mode Limit**
>
> In test mode, you can create up to 30 Payment Links per business. If you need to create more than 30 Payment Links for testing purposes, contact [Razorpay Support](https://razorpay.com/support/).

> [accordion] To make test payments for Payment Links:
>
> 1. Log in to the Dashboard.
> 2. Navigate to **Payment Links**.
> 3. Select the Payment Links you wish to test.
> 4. Copy the link URL and open it in your browser.
>
>    ![Payment Link Test Payment](https://razorpay.com/docs/build/browser/assets/images/pl-dashboard-test-payment.jpg)
> 5. Select the payment method of your choice and proceed with the payment.
> 6. Select **Success** or **Failure**, depending on which flow you wish to test.
>
>    ![Test Payment Success or Failure Flow](https://razorpay.com/docs/build/browser/assets/images/pl-test-payment-success.jpg)
> 7. You should see a confirmation message depending on the flow you have selected.
>
>    ![image title](https://razorpay.com/docs/build/browser/assets/images/pl-test-payments-success.jpg)

## Create a Payment Link Using API

You can create a Payment Link using:

* [Create a Standard Payment Link API](https://razorpay.com/docs/api/payments/payment-links/create-standard.md)
* [Create a UPI Payment Link API](https://razorpay.com/docs/api/payments/payment-links/create-upi.md)

#### Related Information

* [FAQs](https://razorpay.com/docs/payments/payment-links/faqs.md)
* [Payment Links APIs](https://razorpay.com/docs/payments/payment-links/apis.md)
