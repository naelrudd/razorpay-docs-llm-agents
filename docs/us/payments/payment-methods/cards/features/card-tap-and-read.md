> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Card Tap & Read at Standard Checkout

> Let customers add a card by tapping it on their NFC-enabled Android phone at Razorpay Checkout. Card number and expiry auto-fill instantly.

Available in
🇮🇳 India
🇸🇬 Singapore
🇺🇸 United States

Card Tap & Read lets your customers add a new card by tapping their physical card on the back of their NFC-enabled Android phone at [Standard Checkout](https://razorpay.com/docs/us/payments/payment-gateway/android-integration/standard.md). The card number and expiry auto-fill instantly, removing the need to type a 16-digit number.

Built on NFC (Near Field Communication) and fully PCI-DSS compliant, it reduces manual entry errors and helps improve card payment success rates.

> [!NOTE]
>
> **Handy Tips**
>
> Tapping a card only reads the card number and expiry. It does not trigger a payment. Customers still enter the CVV and complete OTP authentication.

## Advantages

> [tab] For Your Business
>
> * **Higher success rates**: Fewer failures from incorrect card numbers and expiry details.
> * **Zero setup cost**: Included at no additional charge.
> * **No code changes**: Available out of the box on the latest Android [Standard Checkout](https://razorpay.com/docs/us/payments/payment-gateway/android-integration/standard.md) SDK.

> [tab] For Your Customers
>
> * **1-tap card entry**: Auto-fill card number and expiry, no typing required.
> * **Fewer errors**: Skip manual entry of long card numbers.
> * **Always optional**: Switch to manual entry anytime.
> * **Secure and compliant**: Tapping only reads the card number and expiry, never the CVV, and the feature is fully PCI-DSS compliant.

## Prerequisites

Your customers can use Card Tap & Read if they have:

* An Android device with NFC support.
* A physical card that supports contactless reading.
* Your app on the latest [Android Standard Checkout SDK](https://razorpay.com/docs/us/payments/payment-gateway/android-integration/standard.md).

> [!NOTE]
>
> **Handy Tips**
>
> The feature is available out of the box for all merchants on the latest [Android Standard Checkout SDK](https://razorpay.com/docs/us/payments/payment-gateway/android-integration/standard.md), with no integration changes required. To opt out, contact our [Support team](https://razorpay.com/support/#request).

## How Card Tap & Read Works

To pay using Card Tap & Read at [Standard Checkout](https://razorpay.com/docs/us/payments/payment-gateway/android-integration/standard.md):

1. Select **Card**, then choose **Add New Card**.
2. Tap the card on the back of the phone. The card number and expiry auto-fill within about a second.
3. Enter the CVV and cardholder name.
4. Choose whether to save the card.
5. Complete the payment through the standard authentication and authorisation flow.

<video width="400" controls>
  <source src="https://razorpay.com/docs/build/browser/assets/images/card-tap-and-read.mp4" title="Card Tap & Read at Standard Checkout" type="video/mp4" />

  Card Tap & Read at Standard Checkout
</video>

> [!NOTE]
>
> **Handy Tips**
>
> Select **Enter card details manually** at any time. From the manual screen, choose **Enter card details via NFC** to return to the tap flow.

### Fields Captured

| Detail | How it is captured |
| - | - |
| Card number | Auto-filled via NFC tap |
| Expiry | Auto-filled via NFC tap |
| CVV | Entered manually |
| Cardholder name | Entered manually |

## How Different Scenarios Are Handled

The [Checkout](https://razorpay.com/docs/us/payments/payment-gateway/android-integration/standard.md) handles device and card scenarios gracefully, so customers can always complete a payment:

| Scenario | What happens | Solution |
| - | - | - |
| Device does not support NFC | Card Tap & Read is not shown. | The customer enters card details manually. |
| NFC is turned off | The customer is prompted to turn on NFC, with a shortcut to settings. | The customer turns on NFC and returns to Checkout. |
| Card is not contactless | The card cannot be read on tap. | The customer can retry up to 3 times, after which the manual entry screen opens automatically. |
| Card is read partially | Only some card details are captured. | The customer completes the remaining fields manually. |
| Tap is not detected | A retry option with guidance appears. | After 3 failed attempts, the flow falls back to manual entry. |
| Browser (mobile web) checkout | Card Tap & Read is not shown, as NFC is not supported in mobile browsers. | The customer enters card details manually. |

## Frequently Asked Questions (FAQs)

> [accordion] Does tapping the card start a payment?
>
> No. Tapping only reads the card number and expiry. The customer must enter the CVV and complete OTP authentication to pay.

> [accordion] Which details are auto-filled when the card is tapped?
>
> Only the card number and expiry. The CVV and cardholder name are entered manually, as these are not shared over NFC.

> [accordion] Is Card Tap & Read available on iOS and mobile web?
>
> No. It is supported only in the in-app Android [Standard Checkout](https://razorpay.com/docs/us/payments/payment-gateway/android-integration/standard.md) SDK flow, as NFC is not supported on iOS or mobile web in India yet.

> [accordion] Do I need to make any code changes to enable this feature?
>
> No. It is available automatically on the latest Android Standard Checkout SDK. To opt out, contact our [Support team](https://razorpay.com/support/#request).
