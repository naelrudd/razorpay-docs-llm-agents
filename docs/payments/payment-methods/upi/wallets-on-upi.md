> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Prepaid Wallets on UPI

> Offer Prepaid Wallets on UPI as a payment method to your customers.

Available in
🇮🇳 India

Leverage the full potential of UPI Payments by integrating Prepaid Payment Instruments.

Watch this video to know more about Prepaid Wallets on UPI.

[YouTube video player](https://www.youtube.com/embed/2z5vI3SL7uY?si=EPw3-M2404o34YNy)

### Advantages

> [tab] For Customers
>
> * Increased touch points to make payments via their prepaid wallets irrespective of the wallets integrated with your business.
> * Ease of completing wallet payments with better reach on UPI.
> * Store money in their wallet without worrying about the amount being stuck in the wallet.

> [tab] For Businesses
>
> * Accept prepaid digital wallet payments without the costs of integration with a wallet issuer.
> * Experience a high success rate of one-step wallet transactions on UPI.
> * Enhance the payment experience for customers, ensuring a smoother process.

## Frequently Asked Questions (FAQs)

> [accordion] How can customers link their digital wallets to UPI?
>
> To link a wallet to UPI, customers need to:
>
> 1. Head over to the wallet issuer app (Amazon Pay, PhonePe) on their smartphone.
>
> 2. Secure a VPA address issued by the wallet issuer through mobile number verification.
>
> 3. Once the VPA address is assigned, the registration of the wallet on UPI is complete.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Only those who have completed the KYC verification process can link their wallets with UPI.

> [accordion] How will the customer make a UPI payment with wallets?
>
> To make a payment via digital wallets on UPI:
>
> 1. The customer can scan the UPI QR through their wallet app and make wallet payments on UPI. No UPI PIN is required while making a wallet transaction on UPI.
>
> 2. The customer can also enter the VPA address or the phone number linked to their registered wallet on the checkout page to make UPI payments.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > The mobile number linked to UPI should be in use on the smartphone and should be the same number linked to the wallet.

> [accordion] How can I identify UPI payments made using prepaid wallets?
>
> You can retrieve the details of the account type (bank account or credit card) used for UPI payments through the Payment Webhook, Fetch Payment API, and the Dashboard.
>
> * **Payment Webhook**: The payment entity will now include the payer account type details. Refer to the [Payment Authorized Payload](https://razorpay.com/docs/webhooks/payments.md#payment-authorised).
> * **Fetch Payment API**: The payment entity will now include the payer account type details. Refer to the [Fetch API sample code](https://razorpay.com/docs/api/payments/fetch-with-id.md).
> * **On the Dashboard** :
>   1. Click on a UPI payment to look at the payment details.
>   2. The payment drawer will display the following information for wallet payments on UPI:
>      1. Payment Method: UPI
>      2. Paid from: Wallet
>
> ![Image shows Wallet payment via UPI on Razorpay Dashboard](https://razorpay.com/docs/build/browser/assets/images/wallet-upi-dashboard.jpg)

> [accordion] What is the coverage of wallet acceptance via UPI?
>
> The following wallet issuers support linking wallets to UPI:
>
> * Amazon Pay
> * PhonePe
> * Fampay
> * OneCard
>
> In terms of bank coverage, the following banks will identify wallet transactions on UPI from **30th August 2023**:
>
> * Axis Bank
> * HDFC Bank
> * Yes Bank
> * ICICI Bank

> [accordion] How do I enable wallet transactions via UPI for my business?
>
> Razorpay will take care of enabling this feature for you.

> [accordion] Will I be charged for wallet transactions via UPI?
>
> A Platform fee of 2% is levied for all wallet transactions via UPI. This pricing is determined by rates shared by banks and a wallet issuer service charge.

> [accordion] Which businesses are currently not supported from accepting wallet payments on UPI?
>
> You will not be able to accept wallet payments on UPI if you fall under the [**businesses on Customer fee bearer (CFB)**](https://razorpay.com/docs/payments/dashboard/account-settings/configuration/convenience-fees) category.
