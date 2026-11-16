> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# About Third-Party Validation (TPV)

> Know how Razorpay performs Third-Party Validation (TPV) of your customers' bank accounts in real-time using Razorpay Standard Integration.

Available in
🇮🇳 India

> [card] [Third-Party Validation Changelog](https://razorpay.com/docs/payments/changelog.md#products)
>
> Discover new features, updates and deprecations related to Third Party Validation (since Jan 2024).

Third-Party Validation (TPV) of bank accounts is a mandatory requirement for businesses in the BFSI (Banking, Financial Services and Insurance) sector dealing with Securities, Broking and Mutual Funds. As per Securities and Exchange Board of India (SEBI) guidelines, transactions must be made by the investors **only** from those bank accounts provided when they registered with your business.

With Razorpay, you can comply with the SEBI guidelines for online payment collections by offering TPV integrations with [major banks](https://razorpay.com/docs/payments/third-party-validation/bank-list.md) at Checkout. Investors can make payments using netbanking, debit card or UPI. Know [how to integrate TPV on Razorpay Standard Integration](https://razorpay.com/docs/payments/third-party-validation/standard-integration.md).

> [!NOTE]
>
> **Feature Request**
>
> This is an on-demand feature. Please raise a request with our [Support team](https://razorpay.com/support/#request) to get this feature activated on your Razorpay account.

> [accordion] How it Works
>
> 1. At the Checkout, investors complete the payment using the bank account details passed during the order creation.
> 2. The payment is marked as successful only when the bank account details entered in the order match those entered by the investor on the Checkout. If the investor tries to make a payment with an account other than the registered account, Razorpay fails the transaction.
>
> ![TPV Standard Checkout](https://razorpay.com/docs/build/browser/assets/images/tpv-standard-checkout.jpg)

## Supported Products

TPV is supported on the following products:

* [Payment Links](https://razorpay.com/docs/api/payments/payment-links/third-party-validation.md)
* [Payment Gateway](https://razorpay.com/docs/payments/payment-gateway)

## Supported Platforms

TPV is supported on the following platforms:

> [tab] Standard Checkout
>
> | Web | Android | iOS | Webview |
> | - | - | - | - |
> | ✓ | ✓ | ✓ | ✓ |

> [tab] Custom Checkout
>
> | Web | Android | iOS | Webview |
> | - | - | - | - |
> | ✓ | ✓ | ✓ | ✓ |

## Integration Flow

Know [how to integrate TPV on Razorpay Standard Integration](https://razorpay.com/docs/payments/third-party-validation/standard-integration.md).

### Related Information

* [Webhooks](https://razorpay.com/docs/webhooks) (Recommended)
* [Error Codes](https://razorpay.com/docs/errors) (Recommended)
* [How Payment Gateway Works](https://razorpay.com/docs/payments/payment-gateway/how-it-works.md)
* [Payment States](https://razorpay.com/docs/payments/payments)
* [Settlements](https://razorpay.com/docs/payments/settlements)
* [Refunds](https://razorpay.com/docs/payments/refunds)
