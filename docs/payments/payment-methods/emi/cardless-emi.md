> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# About Cardless EMI

> Offer automatic EMI payments without using credit or debit cards to your customers. Check the payment flow and supported Cardless EMI providers.

Available in
🇮🇳 India

> [card] [Cardless EMI Changelog](https://razorpay.com/docs/payments/changelog.md#products)
>
> Discover new features, updates and deprecations related to Cardless EMI (since Jan 2024).

Offer Cardless EMI as a payment method to convert their payment amount to EMIs without a debit or credit card. Customers enjoy the benefits of the EMI as the payments are made using credits approved by the supported Cardless EMI Payment Partners.

> [!WARNING]
>
> **Watch Out!**
>
> Instant Refunds are not supported on EMI, Cardless EMI and Pay Later.

> [!NOTE]
>
> **Feature Enablement**
>
> Cardless EMI as a payment method is not enabled by default. Raise a request with our [Support Team](https://razorpay.com/support/#request) to enable this feature.

## Supported Payment Partners

Following is the list of supported Payment Partners for Cardless EMI and the minimum order amount stipulated by them:

> [tab] Banks
>
> | Banks | Provider Code | Minimum Order Amount |
> | - | - | - |
> | ICICI Bank | `icic` | ₹7000 |
> | IDFC Bank | `idfb` | ₹5000 |
> | HDFC Bank | `hdfc` | ₹5000 |
> | Kotak Bank | `kkbk` | ₹3000 |
> | [axio](https://razorpay.com/docs/payments/payment-methods/emi/cardless-emi/axio.md) | `walnut369` | ₹900 |
> | Fibe | `earlysalary` | ₹3000 |
> | ZestMoney | `zestmoney` | ₹3000 |
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Check the standard [interest rates charged by Banks/Partners](https://razorpay.com/docs/payments/payment-gateway/emi²/faqs.md#1-what-are-the-standard-interest-rates-charged).

> [tab] Non-Banking Payment Partners
>
> | Payment Partners | Provider Code | Minimum Order Amount |
> | - | - | - |
> | axio | `walnut369` | ₹900 |
> | Fibe | `earlysalary` | ₹3000 |
> | ZestMoney | `zestmoney` | ₹3000 |
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Check the standard [interest rates charged by Pay Later Providers](https://razorpay.com/docs/payments/payment-gateway/emi²/faqs.md#2-what-are-the-standard-interest-rates-charged).

> [tab] Optimizer Providers
>
> | Payment Partners | Provider Code | Minimum Order Amount |
> | - | - | - |
> | [ShopSe](https://razorpay.com/docs/payments/payment-methods/emi/cardless-emi/shopse.md) | `shopse` | ₹3000 |
> | [Snapmint](https://razorpay.com/docs/payments/payment-methods/emi/cardless-emi/snapmint.md) | `snapmint` | None |
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Check the standard [interest rates charged by Pay Later Providers](https://razorpay.com/docs/payments/payment-gateway/emi²/faqs.md#2-what-are-the-standard-interest-rates-charged).

## Payment Flow

Given below is a diagram that explains the payment flow for Cardless EMI:

![payment flow for Cardless EMI](https://razorpay.com/docs/build/browser/assets/images/payment-flow-cardless_emi.jpg)

## Payment Flow on Standard Checkout

Customers select the products on your website or app and proceed to Checkout. On the Checkout page, the customers:

1. Enter their **Phone Number** and click **Continue**.
2. Select **EMI** as the payment method.

   ![Select emi payment option on checkout](https://razorpay.com/docs/build/browser/assets/images/emi-options-card.jpg)
3. Select **Cardless and Others**.

   ![Select Cardless and Others](https://razorpay.com/docs/build/browser/assets/images/emi-select-cardless.jpg)
4. Choose a payment instrument from the list and select the EMI tenure. Click **Continue**.

   ![EMI tenure and click Select Plan](https://razorpay.com/docs/build/browser/assets/images/emi-cardless-tenure.jpg)

After the successful payment, Razorpay redirects customers to your application or website. Customers' monthly statements will reflect the EMI amount with interest charged by the bank.

You will receive the entire payment amount from the Cardless EMI service provider. Based on the terms and conditions, the customer pays the total payment amount with additional interest (if any) as EMIs to the provider.

## Standard Checkout Integration

No additional integration is required to show Cardless EMI on your Standard Checkout page.

## FAQs

See: [Cardless EMI FAQs](https://razorpay.com/docs/payments/payment-methods/emi/faqs.md#cardless-emi).
