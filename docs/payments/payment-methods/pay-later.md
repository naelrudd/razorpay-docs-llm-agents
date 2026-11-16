> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Pay Later

> Offer Pay Later (Buy Now, Pay Later) payment method at Razorpay Checkout. Check providers and payment flow.

Available in
🇮🇳 India
🇸🇬 Singapore

> [card] [Pay Later Changelog](https://razorpay.com/docs/payments/changelog.md#products)
>
> Discover new features, updates and deprecations related to Pay Later (since Jan 2024).

Accept payments from your customers using the **Pay Later** service offered by various third-party providers.

* Know about [how to enable/disable Pay Later](https://razorpay.com/docs/payments/dashboard/account-settings/payment-methods.md#request-payment-methods) as a payment method for your account.
* No additional integration is required to show Pay Later on your Standard Checkout integration.

> [!WARNING]
>
> **Watch Out!**
>
> Instant Refunds are not supported on EMI, Cardless EMI and Pay Later.

## How it Works

Based on the concept [Buy Now, Pay Later](https://en.wikipedia.org/wiki/Buy_now,_pay_later):

1. The customers get a running line of credit by registering with any providers.
2. When customers buy goods or services on your website or apps, no money is debited from their accounts.
3. You receive the payments from their providers.
4. The customer pays back to the provider as per the fixed schedule defined by the provider.

**At Razorpay Checkout:**

1. At the Checkout, customers enter their contact details and from the displayed list of **Pay Later** providers, customers select their preferred provider.

![Pay Later payment method on Checkout screen](https://razorpay.com/docs/build/browser/assets/images/pm-paylater-checkout.jpg)

2. Customers authorise their accounts via the OTP sent to their registered phone numbers.

3. Payment is completed after successful validation.

## Supported Pay Later Providers

| **Provider name** | **Provider Code** |
| - | - |
| LazyPay | `lazypay` |
| PayPal | `paypal` |

> [!NOTE]
>
> **Handy Tips**
>
> * PayPal now supports the Pay Later feature. You should enable both [PayPal](https://razorpay.com/docs/payments/payment-methods/wallets/paypal.md#to-enable-paypal) and the Pay Later options under Account & Settings → Pay Later (under Payment methods) on the Dashboard to enable the Pay Later feature.
> * Check the standard interest rates charged by [Pay Later providers](https://razorpay.com/docs/payments/payment-gateway/emi²/faqs.md#2-what-are-the-standard-interest-rates-charged).
