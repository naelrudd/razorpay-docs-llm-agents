> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Embedded Quick Buy: React Native Integration

> Integrate Embedded Quick Buy in your React Native app with the Razorpay Custom UI SDK and show customers their recommended payment instrument.

Available in
🇮🇳 India

Follow these steps to add [Embedded Quick Buy](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded.md) to your React Native app. The integration builds on the [React Native Custom UI SDK](https://razorpay.com/docs/payments/payment-gateway/react-native-integration/custom/build-integration.md). You render your own payment UI, and Razorpay processes the payment.

> [!NOTE]
>
> **Already on the React Native Custom UI SDK?**
>
> The steps specific to Quick Buy are [1.3 Create a Customer](#1-3-create-a-customer) and [1.4 Fetch Recommended Instruments](#1-4-fetch-recommended-instruments). All other steps follow the standard Custom UI SDK integration.
>
> If you use the React Native Standard SDK (`react-native-razorpay`), add `react-native-customui` alongside it. The Custom UI SDK powers the Quick Buy button. Your Standard Checkout continues to open when the customer taps **Change payment method**.

**1.1** [Install the SDK](#1-1-install-the-sdk).

**1.2** [Link the SDK](#1-2-link-the-sdk).

**1.3** [Create a Customer](#1-3-create-a-customer). New for Quick Buy.

**1.4** [Fetch Recommended Instruments](#1-4-fetch-recommended-instruments). New for Quick Buy.

**1.5** [Create an Order in Server](#1-5-create-an-order-in-server).

**1.6** [Import the Razorpay Module](#1-6-import-the-razorpay-module).

**1.7** [Submit Payment](#1-7-submit-payment).

**1.8** [Store Fields in Your Server](#1-8-store-fields-in-your-server).

**1.9** [Verify Payment Signature](#1-9-verify-payment-signature).

**1.10** [Verify Payment Status](#1-10-verify-payment-status).

## 1.1 Install the SDK

Install `react-native-customui` version 2.2.9 or later. Earlier versions do not support `getRecommendedInstruments()`.

```bash npm theme={null}
npm install --save react-native-customui
```

```bash yarn theme={null}
yarn add react-native-customui
```

```bash Expo theme={null}
npx expo install react-native-customui
```

## 1.2 Link the SDK

> [tab] iOS
>
> **Automatic linking**
>
> 1. Install the SDK:
>    ```bash Terminal theme={null}
>    npm install react-native-customui --save
>    ```
>
> 2. Go to the `ios` folder and run `pod install`.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Make sure `Razorpay.framework` is added in the **Embedded Binaries** section and that **Always Embed Swift Standard Libraries** is set to **Yes** in **Build Settings**.
>
> **Manual linking with CocoaPods**
>
> 1. Add this line to your build targets in your `Podfile`:
>    ```ruby Podfile theme={null}
>    pod 'react-native-customui', :path => '../node_modules/react-native-customui'
>    ```
> 2. Run `pod install`.
>
> **Manual linking without CocoaPods**
>
> 1. In Xcode, right-click **Libraries** → **Add Files to \[your project's name]**. Go to `node_modules/react-native-customui` and add the `.xcodeproj` file.
> 2. Select your project in the navigator. Add `libRNDeviceInfo.a` from the `deviceinfo` project to **Build Phases** → **Link Binary With Libraries**.
> 3. In **Build Settings**, select **All**. Under **Header Search Paths**, check that `$(SRCROOT)/../react-native/React` and `$(SRCROOT)/../../React` are present and set to `recursive`.
> 4. Run the project with **Cmd + R**.
>
> **Expo**
>
> After adding the package, prebuild the app to generate the native iOS folders:
>
> ```bash Terminal theme={null}
> npx expo prebuild
> npx expo run:ios --device
> ```
>
> **M1 Mac**
>
> If you build on an Apple Silicon (M1) Mac, add this inside `post_install do |installer|` in your `Podfile`:
>
> ```ruby Podfile theme={null}
> installer.pods_project.build_configurations.each do |config|
>   config.build_settings["EXCLUDED_ARCHS[sdk=iphonesimulator*]"] = "arm64"
> end
> ```

> [tab] Android
>
> React Native autolinking links the Android module for `react-native-customui`. No manual steps are needed.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Do not link `react-native-customui` manually in `android/settings.gradle`, `android/app/build.gradle` or `MainApplication`. Manual linking conflicts with autolinking and fails the Gradle build. Know how to [fix this error](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/faqs.md#react-native-sdk) if you see it.
>
> **Expo**
>
> ```bash Terminal theme={null}
> npx expo prebuild
> npx expo run:android --device
> ```

## 1.3 Create a Customer

Create a customer on your server with the [Customers API](https://razorpay.com/docs/api/customers/create.md). You can do this asynchronously, for example when you collect the customer's details. Use the `customer_id` returned in the response to fetch recommended instruments in [step 1.4](#1-4-fetch-recommended-instruments).

```bash Request theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/customers \
-H "Content-Type: application/json" \
-d '{
  "name": "Gaurav Kumar",
  "contact": "9123456780",
  "email": "gaurav.kumar@example.com",
  "fail_existing": "0",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
}'
```

```json Response theme={null}
{
  "id": "cust_1Aa00000000004",
  "entity": "customer",
  "name": "Gaurav Kumar",
  "email": "gaurav.kumar@example.com",
  "contact": "9123456780",
  "gstin": null,
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  },
  "created_at": 1234567890
}
```

## 1.4 Fetch Recommended Instruments

Initialise the SDK with `Razorpay.initRazorpay()`, then call `Razorpay.getRecommendedInstruments()` to get the customer's recommended payment instruments.

* The response contains up to 3 instruments, ranked by how likely the customer is to complete the payment. `items[0]` is the strongest recommendation.
* The SDK checks which UPI apps are installed on the device and returns only those.
* The response includes the logos you need to render the Quick Buy button.
* Pass the `order_id` so that all instrument types are eligible. Without an `order_id`, the response is limited to UPI intent apps and `amount` and `currency` become mandatory.
* Pass the customer's contact number in `customer.contact`. It is mandatory by default, although this depends on your account configuration. If it is required and missing, the call fails.

```javascript JavaScript theme={null}
import Razorpay from 'react-native-customui';

// Call early, for example when the checkout screen loads
Razorpay.initRazorpay('<YOUR_KEY_ID>');

const options = {
  order_id: 'order_xxxxxx',        // recommended
  customer_id: 'cust_xxxxxx',      // from step 1.3
  amount: 100,                     // mandatory if no order_id
  currency: 'INR',                 // mandatory if no order_id
  customer: {
    contact: '+919123456780'       // mandatory by default
  }
};

Razorpay.getRecommendedInstruments(options).then(response => {
  const items = response.get_recommended_instruments.items;

  items.forEach(item => {
    if (item.method === 'card') {
      console.log(item.card.last4);
    }
    if (item.method === 'upi') {
      console.log(item.upi.app);
      console.log(item.upi.app_package);
      console.log(item.upi.app_logo);
    }
  });
}).catch(error => {
  // Fall back to Standard Checkout
});
```

> [!WARNING]
>
> **Watch Out!**
>
> * `initRazorpay()` does not return a promise. On Android, the SDK initialises on the UI thread, so calling `getRecommendedInstruments()` immediately after it can fail. Call `initRazorpay()` earlier in the flow, for example when the checkout screen loads, and fetch recommendations after it.
> * Always show a **Change payment method** option next to the Quick Buy button. It should open the full Razorpay Checkout, as per the [React Native Standard Checkout integration](https://razorpay.com/docs/payments/payment-gateway/react-native-integration/standard/integration-steps-android.md). Take the customer straight to the full checkout rather than to an intermediate screen.
> * If the response has no instruments, or the call fails, show your regular checkout instead of the Quick Buy button.

#### Sample Response

```json Response theme={null}
{
  "actions": ["get_recommended_instruments"],
  "get_recommended_instruments": {
    "entity": "collection",
    "count": 3,
    "items": [
      {
        "method": "card",
        "token": "token_Hf7vKlM2NpQrSt",
        "card": {
          "last4": "4242",
          "network": "Visa",
          "issuer": "HDFC",
          "type": "debit",
          "sub_type": "consumer",
          "international": false,
          "network_logo_url": "https://cdn.razorpay.com/app/visa.svg",
          "issuer_logo_url": "https://cdn.razorpay.com/app/hdfc.svg"
        }
      },
      {
        "method": "upi",
        "upi": {
          "flow": "intent",
          "app": "gpay",
          "app_package": "com.google.android.apps.nbu.paisa.user",
          "app_logo": "https://cdn.razorpay.com/app/gpay.svg"
        }
      },
      {
        "method": "upi",
        "upi": {
          "flow": "intent",
          "app": "phonepe",
          "app_package": "com.phonepe.app",
          "app_logo": "https://cdn.razorpay.com/app/phonepe.svg"
        }
      }
    ]
  }
}
```

#### Response Parameters

| Parameter | Type | Description | How to use it |
| - | - | - | - |
| `actions` | array | Always `get_recommended_instruments`. | Check that the response matches the action you called. |
| `get_recommended_instruments.entity` | string | Always `collection`. | Standard Razorpay collection identifier. |
| `get_recommended_instruments.count` | integer | Number of instruments in `items`. Maximum 3. | Check before you render the button. |
| `get_recommended_instruments.items` | array | Recommended instruments in order. Index 0 is the strongest recommendation. | Render the Quick Buy button from `items[0]`. |
| `items.method` | string | `card` or `upi`. | Decides which UI to render and which payment fields to send. |
| `token` | string | Razorpay token ID of the saved card. | Pass as `token` when you submit the payment. |
| `card.last4` | string | Last 4 digits of the card. For display only. | Render a masked label, such as **HDFC Debit ••••4242**. Never pass it to payment APIs. |
| `card.network` | string | `Visa`, `MasterCard`, `RuPay`, `Amex` or `Diners`. | Show the network name. |
| `card.issuer` | string | 4-character issuer code. For example, `HDFC`, `ICIC` or `SBIN`. | Show the issuer name. |
| `card.type` | string | `credit`, `debit` or `prepaid`. | Show the card type on the button. |
| `card.sub_type` | string | `consumer`, `business` or `unknown`. | Optional. Use it if business cards need a different treatment. |
| `card.international` | boolean | `true` if the card is international. | Flag international cards if needed. |
| `card.network_logo_url` | string | CDN-hosted card network logo. | Use directly in an `Image` component. |
| `card.issuer_logo_url` | string | CDN-hosted issuing bank logo. | Use directly in an `Image` component. |
| `upi.flow` | string | Always `intent`. | Confirms the UPI flow. |
| `upi.app` | string | Short name of the UPI app. For example, `gpay`, `phonepe`, `paytm` or `bhim`. | Show on the button. |
| `upi.app_package` | string | Package name of the UPI app. For example, `com.google.android.apps.nbu.paisa.user`. | Pass as `upi_app_package_name` when you submit the payment. |
| `upi.app_logo` | string | CDN-hosted UPI app logo. | Show on the button. |

## 1.5 Create an Order in Server

Create an order on your server using the [Orders API](https://razorpay.com/docs/api/orders/create.md) when the customer taps the Quick Buy button, or earlier if you pass the `order_id` in [step 1.4](#1-4-fetch-recommended-instruments).

> [!WARNING]
>
> **Watch Out!**
>
> Create an order for every payment, server-side, using your API Key ID and secret. Payments made without an `order_id` cannot be captured and are automatically refunded.

```bash Request theme={null}
curl -X POST https://api.razorpay.com/v1/orders \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-H 'content-type:application/json' \
-d '{
  "amount": 50000,
  "currency": "INR",
  "customer_id": "cust_1Aa00000000004",
  "receipt": "rcptid_11",
  "notes": {
    "key1": "value3",
    "key2": "value2"
  }
}'
```

```json Response theme={null}
{
  "id": "order_IluGWxBm9U8zJ8",
  "entity": "order",
  "amount": 50000,
  "amount_paid": 0,
  "amount_due": 50000,
  "currency": "INR",
  "receipt": "rcptid_11",
  "status": "created",
  "attempts": 0,
  "notes": [],
  "created_at": 1642662092
}
```

#### Request Parameters

`amount` *mandatory*
: `integer` Payment amount in the smallest currency sub-unit. For example, pass `50000` for ₹500.

`currency` *mandatory*
: `string` The 3-letter ISO currency code. For example, `INR`.

`customer_id` *mandatory*
: `string` The customer ID returned in [step 1.3](#1-3-create-a-customer).

`receipt` *optional*
: `string` Your receipt number for the order. Maximum 40 characters.

`notes` *optional*
: `object` Key-value pairs for additional information. Maximum 15 pairs of 256 characters each.

`partial_payment` *optional*
: `boolean` Set to `true` to accept partial payments. Defaults to `false`.

`first_payment_min_amount` *optional*
: `integer` Minimum amount for the first partial payment. Use only when `partial_payment` is `true`.

## 1.6 Import the Razorpay Module

Import the Razorpay module into your React Native component:

```javascript JavaScript theme={null}
import Razorpay from 'react-native-customui';
```

## 1.7 Submit Payment

When the customer taps the Quick Buy button, call `Razorpay.open()` with the payment options for the recommended instrument. The method returns a promise:

* `then` handles a successful payment.
* `catch` handles a failed payment.

For a recommended UPI app, pass `method: 'upi'`, `_[flow]: 'intent'` and the app's package name in `upi_app_package_name`:

```javascript JavaScript theme={null}
Razorpay.open({
  key_id: '<YOUR_KEY_ID>',
  amount: '50000',
  currency: 'INR',
  order_id: 'order_IluGWxBm9U8zJ8',
  email: 'gaurav.kumar@example.com',
  contact: '9123456780',
  method: 'upi',
  '_[flow]': 'intent',
  upi_app_package_name: 'com.google.android.apps.nbu.paisa.user'
}).then((data) => {
  // Send data.razorpay_payment_id, data.razorpay_order_id and
  // data.razorpay_signature to your server for verification (step 1.9)
}).catch((error) => {
  // Handle the failure: error.code, error.description
});
```

For other payment methods, use the same payloads as your existing [React Native Custom UI integration](https://razorpay.com/docs/payments/payment-gateway/react-native-integration/custom/build-integration.md).

#### Checkout Parameters

`order_id` *mandatory*
: `string` The order ID created in [step 1.5](#1-5-create-an-order-in-server).

`description` *optional*
: `string` Description of the purchase. Must start with an alphanumeric character.

`image` *optional*
: `string` URL or base64 string of your business logo.

`notes` *optional*
: `object` Key-value pairs for additional information. Maximum 15 pairs of 256 characters each.

`callback_url` *optional*
: `string` URL to redirect the customer to after payment. It must accept POST requests. On success, it receives `razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature`.

`redirect` *conditional*
: `boolean` Mandatory if you pass `callback_url`. Set to `true` to redirect the customer to `callback_url` or `false` to keep them in the app.

## 1.8 Store Fields in Your Server

A successful payment returns these fields. Store them on your server and verify the signature in the next step.

```json Success Response theme={null}
{
  "razorpay_payment_id": "pay_29QQoUBi66xm2f",
  "razorpay_order_id": "order_9A33XWu170gUtm",
  "razorpay_signature": "9ef4dffbfd84f1318f6739a3ce19f9d85851857ae648f114332d8401e0949a3d"
}
```

`razorpay_payment_id`
: `string` Unique identifier of the payment. Returned only for successful payments.

`razorpay_order_id`
: `string` Unique identifier of the order.

`razorpay_signature`
: `string` Signature used to verify that the payment is authentic.

## 1.9 Verify Payment Signature

Verify the signature on your server to confirm the payment is authentic. This step is mandatory. Never verify the signature in the app.

1. Use the `order_id` stored on your server. Do not use the `razorpay_order_id` returned to the app.
2. Create an HMAC-SHA256 hex digest of `order_id + "|" + razorpay_payment_id` using your API key secret.
3. If the digest matches `razorpay_signature`, the payment is authentic.

```text Pseudocode theme={null}
generated_signature = hmac_sha256(order_id + "|" + razorpay_payment_id, secret);

if (generated_signature == razorpay_signature) {
    // payment is authentic
}
```

```java Java (server-side) theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
String secret = "[YOUR_KEY_SECRET]";

JSONObject options = new JSONObject();
options.put("razorpay_order_id", "order_IEIaMR65cu6nz3");
options.put("razorpay_payment_id", "pay_IH4NVgf4Dreq1l");
options.put("razorpay_signature", "0d4e745a1838664ad6c9c9902212a32d627d68e917290b0ad5f08ff4561bc50f");

boolean status = Utils.verifyPaymentSignature(options, secret);
```

## 1.10 Verify Payment Status

Confirm that the payment status is `captured`. You can track it in 3 ways:

* **Dashboard**: Log in to the Dashboard and go to **Transactions** → **Payments**. A successful payment has a payment ID and the status **Captured**.
* **Webhooks**: Subscribe to [payment webhook events](https://razorpay.com/docs/webhooks/payments.md) for real-time updates.
* **API**: Poll the [Fetch a Payment API](https://razorpay.com/docs/api/payments/fetch-with-id.md) with the `razorpay_payment_id`.

> [!NOTE]
>
> **Handy Tips**
>
> Use [Payment Capture Settings](https://razorpay.com/docs/payments/payments/capture-settings.md) to capture payments automatically.

## Next Steps

* [Test your integration](https://razorpay.com/docs/payments/payment-gateway/react-native-integration/custom/test-integration.md) in Test Mode.
* Set up webhooks for real-time payment events.
* Replace your test API keys with live keys when you are ready to go live.

## Related Information

* [Embedded Quick Buy](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded.md)
* [Embedded Quick Buy FAQs](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/faqs.md)
* [React Native Custom UI SDK Integration](https://razorpay.com/docs/payments/payment-gateway/react-native-integration/custom/build-integration.md)
