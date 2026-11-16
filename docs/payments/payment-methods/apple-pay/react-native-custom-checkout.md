> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# React Native Integration

> Accept Apple Pay payments in your React Native app using Razorpay's Custom Checkout SDK. Build your own UI around the Apple Pay button with Razorpay handling payment processing.

Available in
🇮🇳 India

Use Razorpay Apple Pay to add Apple Pay to your React Native app. Razorpay handles payment processing while you build your own UI around the Apple Pay button.

> [!NOTE]
>
> **SDK Version**
>
> The Apple Pay feature is available in `react-native-customui` version `2.3.0` and later. Apple Pay runs on iOS only.

## Prerequisites

| Requirement | Details |
| - | - |
| Razorpay account | With Apple Pay enabled (**Dashboard → Account & Settings → Payment Methods**) |
| Razorpay API key | `rzp_live_*` (your live key) |
| Apple Developer account | Required to configure an Apple Pay Merchant ID |
| Apple Pay Merchant ID | For example, `merchant.com.yourcompany.app`, created in the Apple Developer Portal |
| Merchant ID certificate | Generated from the CSR that Razorpay shares and sent back to your Razorpay point of contact (see [One-Time Setup](#one-time-setup-before-code)) |
| React Native project | With the `react-native-customui` package installed |
| Apple Pay plugin pod | `razorpay-applepay-pod` 1.0.1+ added to your `ios/Podfile` (see [Step 2](#step-2-add-the-apple-pay-plugin-pod)) |
| Xcode 14+ and CocoaPods | iOS deployment target 12.0+ |
| Physical iOS device | Transactions can only complete on real devices |
| Server-side order | Created via the Razorpay Orders API |

> [!NOTE]
>
> **iOS Only**
>
> Apple Pay is available on iOS only. On Android, `canMakePayment()` resolves `false`, so hide the Apple Pay button there. Never call `open()` with `app.apple_pay` on Android.

## One-Time Setup (Before Code)

Complete this setup once before writing any integration code.

> [accordion] Apple Developer Portal Steps
>
> 1. **Create Apple Pay Merchant ID:** In the Apple Developer Portal, go to **Identifiers → + → Merchant IDs**. Use the format `merchant.com.yourcompany.app` and register.
>
> 2. **Share Merchant ID with Razorpay:** Send your Merchant ID to your Razorpay point of contact. The team will share a CSR file with you.
>
> 3. **Generate Certificate on Apple:** In the Apple Developer Portal, open your Merchant ID → **Create Certificate** under Apple Pay Payment Processing. Upload the `.csr`, then download the `apple_pay.cer`.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Certificates expire after 25 months. Set a reminder to renew before expiry.
>
> 4. **Share Certificate with Razorpay:** Send the `apple_pay.cer` file back to your Razorpay point of contact for configuration.

> [accordion] Xcode Steps
>
> 1. Open `ios/YourApp.xcworkspace` in Xcode.
> 2. Select your app target → **Signing & Capabilities**.
> 3. Click **+ Capability → Apple Pay**.
> 4. Tick the Merchant ID created above.
>
> This generates a `.entitlements` file. Sample output:
>
> ```xml Entitlements theme={null}
> <key>com.apple.developer.in-app-payments</key>
> <array>
>     <string>merchant.com.yourcompany.app</string>
> </array>
> ```
>
> The merchant identifier in this entitlement must be the same one you pass as `app.apple_pay.merchant_identifier` at runtime.

## Integration Steps

### Step 1: Install the SDK

Install the package from npm:

```sh Terminal theme={null}
npm install react-native-customui@^2.3.0
```

### Step 2: Add the Apple Pay Plugin Pod

The Apple Pay plugin is opt-in. Add it to your `ios/Podfile`, inside your app target:

```ruby Podfile theme={null}
pod 'razorpay-applepay-pod', '~> 1.0.1'
```

Then install the pods:

```sh Terminal theme={null}
cd ios && pod install
```

Existing apps that already have the pod should run `pod update razorpay-applepay-pod`.

> [accordion] Why is the plugin opt-in?
>
> Declaring the plugin as a hard dependency would force the Apple Pay pod on every app using `react-native-customui`, so you add it explicitly only when you need Apple Pay.
>
> The SDK resolves the plugin at runtime. If the pod is absent, your app still builds and Apple Pay degrades cleanly: `canMakePayment` returns `false` and `open()` rejects with `DEVICE_NOT_SUPPORTED`.

### Step 3: Initialise Once

```js JavaScript theme={null}
import Razorpay from 'react-native-customui';

Razorpay.initRazorpay(KEY_ID); // once, when your checkout screen mounts
```

Eligibility uses the key and SDK instance this creates. Calling `canMakePayment()` before it resolves `false` and logs a console warning; it does not reject. Do not `await` this call, as the promise returned by `initRazorpay` never settles.

### Step 4: Check if the Customer Can Pay

Call this before showing your Apple Pay button. It checks whether the user can pay via Apple Pay with your merchant account.

```js JavaScript theme={null}
import Razorpay from 'react-native-customui';

const eligible = await Razorpay.canMakePayment();
```

`canMakePayment` returns a boolean. It is merchant-aware, not a device probe: it fetches the card networks enabled for your Razorpay account and resolves `true` only when Apple Pay is live for your account and the customer's Wallet holds a card on an accepted network. It returns `false` on Android, and when `initRazorpay` has not been called. Hide the Apple Pay button when it is `false`.

### Step 5: Create an Order on Your Server

Create a Razorpay order via the Orders API on your backend and send the `order_id` to your app.

```bash Request theme={null}
curl -X POST https://api.razorpay.com/v1/orders \
  -u rzp_live_XXXXXXXXXX:your_secret \
  -H "Content-Type: application/json" \
  -d '{
    "amount": 50000,
    "currency": "INR",
    "receipt": "YOUR_ORDER_REF",
    "notes": { "orderId": "YOUR_ORDER_REF" }
  }'
```

The response returns an `order_id` such as `order_CuEzONfnOI86Ab`. Pass this to your app.

To carry your own order reference through an Apple Pay payment, set `receipt` and `notes` on the **order** (as shown above). See [Attaching Your Own Order Reference](#attaching-your-own-order-reference).

> [!WARNING]
>
> **Watch Out!**
>
> Never embed your API secret in the mobile app. Orders must be created by your own backend. A decompiled app bundle exposes any secret it contains, and with it your merchant account.

> [accordion] Order Parameters
>
> | Key | Required | Description |
> | - | - | - |
> | `amount` | Yes | Payment amount in the smallest currency subunit. For example, for ₹299, pass `29900`. For three-decimal currencies such as KWD, BHD and OMR, to accept 295.991, pass `295990`. For zero-decimal currencies such as JPY, to accept 295, pass `295`. |
> | `currency` | Yes | The currency in which the transaction should be made. |
> | `receipt` | Optional | Your internal order reference. Returned as `order_receipt` in settlement recon and reports. Use this to map an Apple Pay payment back to your own order. |
> | `notes` | Optional | Key-value notes stored on the order. Must be a nested JSON object, such as `{ "orderId": "YOUR_ORDER_REF" }`. Readable later via the Orders API. |

### Step 6: Load the Payment Button

Apple's Human Interface Guidelines require the use of `PKPaymentButton` (or a visually compliant variant). Custom buttons will lead to App Store rejection.

React Native has no built-in Apple Pay button. Expose `PKPaymentButton` to JavaScript with a small native view module (an `RCTViewManager` subclass that returns a `PKPaymentButton`), or use a community package that does the same. Whichever you use, it must render Apple's `PKPaymentButton` and call your payment handler on tap.

**Button constraints:**

* Use `PKPaymentButton`, not a generic button with an Apple Pay icon.
* Do not place text or icons inside it.
* Respect Apple's minimum height requirement.
* Use the `automatic` style on iOS 14+ for automatic light and dark mode adaptation.
* Disable the button while a payment is in flight (see Step 7).

> [!NOTE]
>
> **Test on a Real Device**
>
> Run on a physical iOS device. Transactions cannot complete on the simulator. Tap your Apple Pay button, authenticate with Face ID or Touch ID, then confirm the payment record appears in the Razorpay Dashboard.

### Step 7: Trigger the Payment on User Tap

This call must be made in response to a user gesture (such as a button tap). Do not call it on mount or from a timer. Use the existing `Razorpay.open(options)` API with an Apple Pay payload.

```js JavaScript theme={null}
import Razorpay from 'react-native-customui';

function onApplePayTapped() {
  Razorpay.open({
    key_id: 'rzp_live_XXXXXXXXXX',
    order_id: 'order_CuEzONfnOI86Ab',
    amount: '50000',          // in currency subunits (for example, paise)
    currency: 'INR',
    email: 'gaurav.kumar@example.com',
    contact: '9876543210',
    method: 'card',
    app: {
      name: 'apple_pay',
      apple_pay: {
        merchant_identifier: 'merchant.com.yourcompany.app',
      },
    },
    notes: { orderId: 'YOUR_ORDER_REF' },
  })
    .then(data => console.log(data.razorpay_payment_id))
    .catch(err => console.log(err.error));
}
```

> [!WARNING]
>
> **Guard Against Double Taps**
>
> Apple Pay will not present a second payment sheet while one is pending. If `open()` is called twice, both calls fail with `SHEET_PRESENTATION_FAILED`. Set a busy flag at the start of the tap handler, before any async work such as creating the order, and clear it only after the promise settles.

> [accordion] Payment Parameters
>
> | Key | Required | Description |
> | - | - | - |
> | `key_id` | Yes | Your Razorpay key ID. For example, `rzp_live_*xxxx`. |
> | `amount` | Yes | Payment amount in the smallest currency subunit. For example, for ₹299, pass `29900`. Must match the order amount. |
> | `currency` | Yes | The currency for the transaction. |
> | `contact` | Yes | Customer phone number. Maximum length 15 characters, inclusive of country code. |
> | `email` | Yes | Customer email address. Maximum length 40 characters. |
> | `order_id` | Yes | Unique identifier of the order created in Step 5. |
> | `method` | Yes | Must be `"card"`. |
> | `app.name` | Yes | Must be `"apple_pay"`. `method` must also be `"card"`, otherwise a normal card payment opens. |
> | `app.apple_pay.merchant_identifier` | Yes | Your Apple Pay Merchant ID from the Apple Developer Portal. |
> | `notes` | Optional | Requires `razorpay-applepay-pod` 1.0.1+. Key-value notes attached to the payment. Both nested (`{ "orderId": "YOUR_ORDER_REF" }`) and flat (`"notes[orderId]"`) formats are supported. You can also set a reference on the order instead (see [Attaching Your Own Order Reference](#attaching-your-own-order-reference)). |

### Step 8: Handle the Payment Result

`open()` returns a promise. It resolves with the payment payload on success and rejects with an error object on failure or cancellation.

```js JavaScript theme={null}
Razorpay.open(options)
  .then(data => {
    const { razorpay_payment_id, razorpay_order_id, razorpay_signature } = data;
    // Send payment_id, order_id and signature to your server
    // for signature verification.
  })
  .catch(err => {
    const code = err.error?.code;
    const description = err.error?.description ?? err.description;
    if (code === 'PAYMENT_CANCELLED') return; // customer closed the sheet
    // Show description to the customer, log code
  });
```

**Success response (promise resolves with):**

```json Response theme={null}
{
    "razorpay_payment_id": "pay_XXXXXXXXXX",
    "razorpay_order_id":   "order_XXXXXXXXXX",
    "razorpay_signature":  "9ef4dffbfd84f1318f6739a3ce19f9d85851857ae648f114332d8401e0949a3d"
}
```

**Failure response (promise rejects with):**

Customer cancels:

```json Response theme={null}
{
    "error": { "code": "PAYMENT_CANCELLED" },
    "code": 0,
    "description": "Payment cancelled by user"
}
```

Payment declined after it was created:

```json Response theme={null}
{
    "error": {
        "code": "PAYMENT_FAILED",
        "description": "Payment failed",
        "metadata": { "payment_id": "pay_XXXXXXXXXX" }
    },
    "code": 0,
    "description": "Payment failed"
}
```

`err.error.code` is always present. `err.error.description` is not: errors raised on the device carry only the code, and their message is in the top-level `err.description`. Read `err.error.description` first and fall back to `err.description`. `metadata.payment_id` is present only on `PAYMENT_FAILED` when a payment was created before the failure.

### Step 9: Verify Payment Signature on Your Server

Always verify the signature on your server before fulfilling the order. A successful `open()` is not a fulfilled order. Send `razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature` to your backend for HMAC verification.

> [!WARNING]
>
> **Watch Out!**
>
> Never fulfil an order based solely on the client-side result. Always verify the payment signature server-side.

See the [signature verification guide](https://razorpay.com/docs/payments/server-integration/nodejs/integration-steps.md) for Node.js and other language samples.

## Attaching Your Own Order Reference

To map payments back to your own order ID, pass `notes` in the `Razorpay.open()` options (requires `razorpay-applepay-pod` 1.0.1+). As an optional alternative, set the reference on the **order** instead.

Set it at order creation (Step 5):

```json Order theme={null}
{
  "amount": 50000,
  "currency": "INR",
  "receipt": "YOUR_ORDER_REF",
  "notes": { "orderId": "YOUR_ORDER_REF" }
}
```

Then read it back:

| Where you set it | Where it comes back |
| - | - |
| Order `receipt` | `order_receipt` in settlement recon and reports |
| Order `notes` | `notes` on the order, via the Orders API |

## Error Codes

Apple Pay uses the **same** `Razorpay.open()` promise, the same success and error events and the same error envelope as any other payment method in this SDK. If your app already handles card payments, your existing `.then()` and `.catch()` handle Apple Pay with no changes.

On failure, read the error code as a string from `err.error.code` in the rejected promise. The top-level `err.code` is a legacy number shared with other payment methods. For Apple Pay it is `0` for every failure, including cancellation, so check `err.error.code === 'PAYMENT_CANCELLED'` to detect a cancel.

| Error | When It Fires |
| - | - |
| `INVALID_OPTIONS` | Missing `app.apple_pay.merchant_identifier`, missing or invalid amount or a merchant key so malformed the request URL cannot be built. |
| `NO_SUPPORTED_CARD` | Device supports Apple Pay, but the Wallet has no card for the merchant's supported networks. |
| `DEVICE_NOT_SUPPORTED` | Apple Pay unavailable on the device: hardware, OS, region or restrictions. Also returned when the `razorpay-applepay-pod` is not installed. |
| `SHEET_PRESENTATION_FAILED` | PassKit declined to present the payment sheet, including when a sheet is already pending. |
| `PAYMENT_CANCELLED` | Customer dismissed the sheet or cancelled at the Face ID or Touch ID prompt. |
| `NETWORK_ERROR` | Connection loss, timeout or any transport-level failure. |
| `PAYMENT_FAILED` | Internal or processing failure (serialise failure, empty or unparseable response) and the normalised code for any backend decline. |

## Currency and Card Networks

American Express is accepted for INR payments only. For any other currency the SDK removes American Express from the payment sheet automatically. You do not need to do anything.

## Complete Working Example

```js JavaScript theme={null}
import React, { useEffect, useState } from 'react';
import { Platform, Text, View } from 'react-native';
import Razorpay from 'react-native-customui';
import ApplePayButton from './ApplePayButton'; // your PKPaymentButton bridge

const KEY_ID = 'rzp_live_XXXXXXXXXX';
const MERCHANT_IDENTIFIER = 'merchant.com.yourcompany.app';

export default function CheckoutScreen({ orderId, amount, currency }) {
  const [eligible, setEligible] = useState(false);
  const [busy, setBusy] = useState(false);
  const [status, setStatus] = useState('Ready');

  useEffect(() => {
    if (Platform.OS !== 'ios') return;
    Razorpay.initRazorpay(KEY_ID);
    Razorpay.canMakePayment().then(setEligible);
  }, []);

  function onApplePayTapped() {
    if (busy) return;
    setBusy(true);
    Razorpay.open({
      key_id: KEY_ID,
      order_id: orderId,
      amount: String(amount),
      currency,
      email: 'gaurav.kumar@example.com',
      contact: '9876543210',
      method: 'card',
      app: {
        name: 'apple_pay',
        apple_pay: { merchant_identifier: MERCHANT_IDENTIFIER },
      },
      notes: { orderId: orderId },
    })
      .then(data => setStatus(`Success: ${data.razorpay_payment_id}`))
      .catch(err => setStatus(`Error: ${err.error?.code}`))
      .finally(() => setBusy(false));
  }

  return (
    <View>
      <Text>{status}</Text>
      {eligible && (
        <ApplePayButton onPress={onApplePayTapped} disabled={busy} />
      )}
    </View>
  );
}
```

## Frequently Asked Questions

> [accordion] Can I test Apple Pay on the iOS Simulator or in Razorpay test mode?
>
> No. The Simulator has no Secure Element, so the Apple Pay token it produces is empty and the payment fails. Razorpay test mode does not process Apple Pay tokens. Test on a physical iOS device with a real card in Wallet, using your `rzp_live_*` key.

> [accordion] I show payment methods in a list where each expands on selection. How does Apple Pay fit?
>
> The SDK separates detection from payment. Use `canMakePayment` to decide whether to include the Apple Pay row at all. When the user selects that row, show the Apple Pay button. When they tap it, call `Razorpay.open(options)` with the Apple Pay payload.

> [accordion] The Apple Pay sheet appears but the transaction always fails. What should I check?
>
> * **Merchant ID alignment:** Does the Merchant ID you passed in `app.apple_pay.merchant_identifier` match the one in your `.entitlements` and the one you shared with Razorpay?
> * **Certificate uploaded:** Has your Razorpay point of contact confirmed that the certificate for that Merchant ID is configured?
> * **Network match:** Are you testing with a card whose network is enabled for your Razorpay account?
> * **Backend support:** Is Apple Pay enabled for your account in the Razorpay Dashboard?
> * **Real device:** Are you running on a physical device, not the Simulator?
>
> If all of these are correct, take `err.error.metadata.payment_id` (when present) from the rejected promise and look up that payment in the Razorpay Dashboard or through the Payments API for the decline reason.

> [accordion] canMakePayment returns false but the device has cards in Wallet. Why?
>
> `canMakePayment` checks your merchant account as well as the device. It returns `false` when Apple Pay is not enabled for your Razorpay account, when none of the cards in Wallet are on a network enabled for your account, when the `razorpay-applepay-pod` is not installed, when `initRazorpay` has not been called, or on Android.

### Related Information

* [Apple Pay Standard Checkout](https://razorpay.com/docs/payments/payment-methods/apple-pay.md)
* [Apple Pay - Custom Checkout](https://razorpay.com/docs/payments/payment-methods/apple-pay/custom-integration.md)
* [Apple Pay iOS Integration](https://razorpay.com/docs/payments/payment-methods/apple-pay/ios-custom-checkout.md)
* [Apple Pay Web Component Integration](https://razorpay.com/docs/payments/payment-methods/apple-pay/custom-integration/web-sdk/web-component.md)
