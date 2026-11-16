> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Embedded Quick Buy: Flutter Integration

> Integrate Embedded Quick Buy in your Flutter app with the Razorpay Flutter Custom UI SDK and show customers their recommended payment instrument.

Available in
🇮🇳 India

Follow these steps to add [Embedded Quick Buy](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded.md) to your Flutter app. The integration builds on the [Flutter Custom UI SDK](https://razorpay.com/docs/payments/payment-gateway/flutter-integration/custom/build-integration.md). You render your own payment UI, and Razorpay processes the payment.

> [!NOTE]
>
> **Already on the Flutter Custom UI SDK?**
>
> The steps specific to Quick Buy are [1.3 Create a Customer](#1-3-create-a-customer) and [1.4 Fetch Recommended Instruments](#1-4-fetch-recommended-instruments). All other steps follow the standard Flutter integration.

**1.1** [Install the SDK](#1-1-install-the-sdk).

**1.2** [Add ProGuard Rules](#1-2-add-proguard-rules).

**1.3** [Create a Customer](#1-3-create-a-customer). New for Quick Buy.

**1.4** [Fetch Recommended Instruments](#1-4-fetch-recommended-instruments). New for Quick Buy.

**1.5** [Create an Order in Server](#1-5-create-an-order-in-server).

**1.6** [Import the Razorpay Module](#1-6-import-the-razorpay-module).

**1.7** [Submit Payment](#1-7-submit-payment).

**1.8** [Store Fields in Your Server](#1-8-store-fields-in-your-server).

**1.9** [Verify Payment Signature](#1-9-verify-payment-signature).

**1.10** [Verify Payment Status](#1-10-verify-payment-status).

## 1.1 Install the SDK

Add the Razorpay Flutter Custom UI SDK to the dependencies in your app's `pubspec.yaml` file:

```yaml pubspec.yaml theme={null}
dependencies:
  razorpay_flutter_customui: ^1.4.2
```

Run this command in your app's root directory to install the package:

```bash Terminal theme={null}
flutter packages get
```

#### Minimum Requirements

| Platform | Requirement |
| - | - |
| Android | API level 19 or higher. Set `minSdkVersion 19` in `android/app/build.gradle`. |
| iOS | Deployment target iOS 10.0 or higher, with bitcode enabled. |

## 1.2 Add ProGuard Rules

If you use ProGuard on Android, add these rules so that the SDK classes are not obfuscated:

```text proguard-rules.pro theme={null}
-keepattributes *Annotation*
-dontwarn com.razorpay.**
-keep class com.razorpay.** {*;}
-optimizations !method/inlining/
-keepclasseswithmembers class * {
  public void onPayment*(...);
}
```

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

Call `getRecommendedInstruments()` to get the customer's recommended payment instruments.

* The response contains up to 3 instruments, ranked by how likely the customer is to complete the payment. `items[0]` is the strongest recommendation.
* The SDK checks which UPI apps are installed on the device and returns only those. If no UPI app is installed and there is no other recommendation, `items` is empty. Open your regular checkout in that case.
* The response includes the logos you need to render the Quick Buy button.
* Pass the `order_id` so that all instrument types are eligible. Without an `order_id`, the response is limited to UPI intent apps.
* Pass the customer's contact number in `customer.contact`. It is mandatory by default, although this depends on your account configuration.

```dart Dart theme={null}
import 'package:razorpay_flutter_customui/razorpay_flutter_customui.dart' as customui;

customui.Razorpay _customUiRazorpay = customui.Razorpay();
_customUiRazorpay.on(
    customui.Razorpay.EVENT_PAYMENT_SUCCESS, _onPaymentSuccess,
    unwrapData: true);
_customUiRazorpay.on(
    customui.Razorpay.EVENT_PAYMENT_ERROR, _onPaymentError,
    unwrapData: true);
_customUiRazorpay.initilizeSDK('rzp_test_xxxxxxxxxx');

try {
  final options = {
    'key': '<YOUR_KEY_ID>',
    'order_id': 'order_xxxxxx',
    'amount': 100,
    'currency': 'INR',
    'customer': {
      'contact': '+919876543210',
    },
  };
  final result = await _customUiRazorpay.getRecommendedInstruments(options);
  final items = result['items'] as List<dynamic>? ?? [];

  debugPrint('Recommended instruments: ${items.length}');
} catch (e) {
  // Fall back to your regular checkout
  debugPrint('getRecommendedInstruments failed: $e');
}
```

> [!WARNING]
>
> **Watch Out!**
>
> * Always show a **Change payment method** option next to the Quick Buy button. It should open the full Razorpay Checkout of your existing integration, Custom or Standard. Know more about the [Flutter Standard integration](https://razorpay.com/docs/payments/payment-gateway/flutter-integration/standard/integration-steps.md).
> * If `items` is empty, or the call fails, show your regular checkout instead of the Quick Buy button.

#### Sample Response

```json Response theme={null}
{
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
```

#### Response Parameters

| Parameter | Type | Description | How to use it |
| - | - | - | - |
| `entity` | string | Always `collection`. | Standard Razorpay collection identifier. |
| `count` | integer | Number of instruments in `items`. Maximum 3. | Check before you render the button. |
| `items` | array | Recommended instruments in order. Index 0 is the strongest recommendation. | Render the Quick Buy button from `items[0]`. |
| `items.method` | string | `card` or `upi`. | Decides which UI to render and which payment fields to send. |
| `token` | string | Razorpay token ID of the saved card. | Pass as `token` when you submit the payment. |
| `card.last4` | string | Last 4 digits of the card. For display only. | Render a masked label, such as **HDFC Debit ••••4242**. Never pass it to payment APIs. |
| `card.network` | string | `Visa`, `MasterCard`, `RuPay`, `Amex` or `Diners`. | Show the network name. |
| `card.issuer` | string | 4-character issuer code. For example, `HDFC`, `ICIC` or `SBIN`. | Show the issuer name. |
| `card.type` | string | `credit`, `debit` or `prepaid`. | Show the card type on the button. |
| `card.sub_type` | string | `consumer`, `business` or `unknown`. | Optional. Use it if business cards need a different treatment. |
| `card.international` | boolean | `true` if the card is international. | Flag international cards if needed. |
| `card.network_logo_url` | string | CDN-hosted card network logo. | Use directly in an `Image.network` widget. |
| `card.issuer_logo_url` | string | CDN-hosted issuing bank logo. | Use directly in an `Image.network` widget. |
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
  "receipt": "rcptid_11"
}'
```

## 1.6 Import the Razorpay Module

Import the Razorpay Custom UI module into your widget, create an instance and register the payment event listeners:

```dart Dart theme={null}
import 'package:razorpay_flutter_customui/razorpay_flutter_customui.dart' as customui;

late customui.Razorpay _customUiRazorpay;

@override
void initState() {
  super.initState();
  _customUiRazorpay = customui.Razorpay();

  _customUiRazorpay.on(customui.Razorpay.EVENT_PAYMENT_SUCCESS, _onPaymentSuccess, unwrapData: true);
  _customUiRazorpay.on(customui.Razorpay.EVENT_PAYMENT_ERROR, _onPaymentError, unwrapData: true);

  _customUiRazorpay.initilizeSDK('rzp_test_xxxxxxxxxx');
}

void _onPaymentSuccess(dynamic response) {
  // Payment successful. Send the response to your server for verification.
}

void _onPaymentError(dynamic response) {
  // Payment failed
}

@override
void dispose() {
  super.dispose();
  _customUiRazorpay.clear(); // Removes all listeners
}
```

## 1.7 Submit Payment

When the customer taps the Quick Buy button, call `submit()` with the payment options for the recommended instrument. For a recommended UPI app, pass `method: 'upi'`, `_[flow]: 'intent'` and the app's package name in `upi_app_package_name`:

```dart Dart theme={null}
void submitCheckout() {
  var options = {
    'key': '<YOUR_KEY_ID>',
    'amount': 50000,
    'currency': 'INR',
    'name': 'Acme Corp.',
    'order_id': 'order_EMBFqjDHEEn80l',
    'method': 'upi',
    '_[flow]': 'intent',
    'upi_app_package_name': 'com.phonepe.app'
  };
  try {
    _customUiRazorpay.submit(options);
  } catch (e) {
    debugPrint(e.toString());
  }
}
```

For other payment methods, see the [Flutter Custom UI payment methods](https://razorpay.com/docs/payments/payment-gateway/flutter-integration/custom/payment-methods).

## 1.8 Store Fields in Your Server

A successful payment returns these fields to your `_onPaymentSuccess` handler. Store them on your server and verify the signature in the next step.

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

Verify the signature on your server to confirm the payment is authentic. This step is mandatory.

1. Use the `order_id` stored on your server. Do not use the `razorpay_order_id` returned to the app.
2. Create an HMAC-SHA256 hex digest of `order_id + "|" + razorpay_payment_id` using your API key secret.
3. If the digest matches `razorpay_signature`, the payment is authentic.

```text Pseudocode theme={null}
generated_signature = hmac_sha256(order_id + "|" + razorpay_payment_id, secret);

if (generated_signature == razorpay_signature) {
    // payment is authentic
}
```

> [!WARNING]
>
> **Watch Out!**
>
> Always verify the signature on your server, never in the Flutter app. Never ship your API key secret in the app bundle.

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

* [Test your integration](https://razorpay.com/docs/payments/payment-gateway/flutter-integration/custom/test-integration.md) in Test Mode.
* Set up webhooks for real-time payment events.
* Replace your test API keys with live keys when you are ready to go live.

## Related Information

* [Embedded Quick Buy](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded.md)
* [Embedded Quick Buy FAQs](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/faqs.md)
* [Flutter Custom UI SDK Integration](https://razorpay.com/docs/payments/payment-gateway/flutter-integration/custom/build-integration.md)
