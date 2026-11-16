> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Embedded Quick Buy: iOS Integration

> Integrate Embedded Quick Buy in your iOS app with the Razorpay Custom UI SDK and show customers their recommended payment instrument.

Available in
🇮🇳 India

Follow these steps to add [Embedded Quick Buy](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded.md) to your iOS app. The integration builds on the [iOS Custom UI SDK](https://razorpay.com/docs/payments/payment-gateway/ios-integration/custom/build-integration.md). You render your own payment screen in your `UIViewController` or SwiftUI view, and Razorpay processes the payment.

> [!NOTE]
>
> **Already on the iOS Custom UI SDK?**
>
> The steps specific to Quick Buy are [1.3 Create a Customer](#1-3-create-a-customer) and [1.4 Fetch Recommended Instruments](#1-4-fetch-recommended-instruments). All other steps follow the standard Custom UI SDK integration.

**1.1** [Add the SDK Dependency](#1-1-add-the-sdk-dependency).

**1.2** [Configure the SDK](#1-2-configure-the-sdk).

**1.3** [Create a Customer](#1-3-create-a-customer). New for Quick Buy.

**1.4** [Fetch Recommended Instruments](#1-4-fetch-recommended-instruments). New for Quick Buy.

**1.5** [Create an Order in Server](#1-5-create-an-order-in-server).

**1.6** [Initialise RazorpayCheckout in Your ViewController](#1-6-initialise-razorpaycheckout-in-your-viewcontroller).

**1.7** [Submit Payment](#1-7-submit-payment).

**1.8** [Store Fields in Your Server](#1-8-store-fields-in-your-server).

**1.9** [Verify Payment Signature](#1-9-verify-payment-signature).

**1.10** [Verify Payment Status](#1-10-verify-payment-status).

## 1.1 Add the SDK Dependency

> [tab] CocoaPods
>
> Add the Custom UI SDK to your `Podfile` and run `pod install`:
>
> ```ruby Podfile theme={null}
> pod 'razorpay-customui-pod'
> ```

> [tab] Manual (XCFramework)
>
> Download `Razorpay.xcframework` and add it in Xcode under **Target settings** → **General** → **Frameworks, Libraries, and Embedded Content**. Set the embed status to **Embed & Sign**.

> [!NOTE]
>
> **Handy Tips**
>
> Set **Always Embed Swift Standard Libraries** to **Yes** in **Build Settings**. Make sure the device supports TLS v1.1 or v1.2 for PCI compliance.

## 1.2 Configure the SDK

Update `Info.plist` to allow the SDK's WebView traffic and declare the URL schemes of the UPI apps the SDK should detect:

```xml Info.plist theme={null}
<key>NSAppTransportSecurity</key>
<dict>
    <key>NSAllowsArbitraryLoads</key>
    <true/>
</dict>

<!-- Required to detect installed UPI apps for the intent flow -->
<key>LSApplicationQueriesSchemes</key>
<array>
    <string>tez</string>      <!-- Google Pay -->
    <string>phonepe</string>
    <string>paytmmp</string>
    <string>credpay</string>
    <string>upi</string>
</array>
```

The SDK uses a `WKWebView` to complete flows such as card 3DS and bank OTP pages. You create the `WKWebView`, pass it to the SDK and forward its navigation callbacks in [step 1.6](#1-6-initialise-razorpaycheckout-in-your-viewcontroller).

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
* The SDK checks which UPI apps are installed on the device and returns only those.
* The response includes the logos you need to render the Quick Buy button: `app_logo`, `network_logo_url` and `issuer_logo_url`.
* Create an order first and pass its `order_id`, so that all instrument types are eligible. Without an `order_id`, the response is limited to UPI intent apps and `amount` and `currency` become mandatory.

```swift Swift theme={null}
let options: [String: Any] = [
    "order_id": "order_xxxxxx",     // recommended
    "customer_id": "cust_xxxxxx",   // from step 1.3
    "amount": 100,                  // mandatory if no order_id
    "currency": "INR",              // mandatory if no order_id
    "contact": "8050981760"         // pass if no customer_id
]

razorpay.getRecommendedInstruments(withOptions: options,
    withSuccessCallback: { response in
        guard let collection = response["get_recommended_instruments"] as? [String: Any],
              let items = collection["items"] as? [[String: Any]] else { return }

        for item in items {
            let method = item["method"] as? String

            if method == "card", let card = item["card"] as? [String: Any] {
                print(card["last4"] as? String ?? "")                    // display only
            }

            if method == "upi", let upi = item["upi"] as? [String: Any] {
                print(upi["app"] as? String ?? "")                       // for example, gpay
                print(upi["upi_app_package_name"] as? String ?? "")      // pass to authorize()
                print(upi["app_logo"] as? String ?? "")                  // CDN logo URL
            }
        }
    },
    withFailure: { error in
        // Fall back to Standard Checkout
    }
)
```

> [!WARNING]
>
> **Watch Out!**
>
> * Always show a **Change payment method** option next to the Quick Buy button. It should open the full Razorpay Checkout, as per the [iOS Standard Checkout integration](https://razorpay.com/docs/payments/payment-gateway/ios-integration/standard/integration-steps.md).
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
          "upi_app_package_name": "google_pay",
          "app_logo": "https://cdn.razorpay.com/app/gpay.svg"
        }
      },
      {
        "method": "upi",
        "upi": {
          "flow": "intent",
          "app": "phonepe",
          "upi_app_package_name": "phonepe",
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
| `card.network_logo_url` | string | CDN-hosted card network logo. | Load directly into a `UIImageView`. |
| `card.issuer_logo_url` | string | CDN-hosted issuing bank logo. | Load directly into a `UIImageView`. |
| `upi.flow` | string | Always `intent`. | Confirms the UPI flow. |
| `upi.app` | string | Short name of the UPI app. For example, `gpay`, `phonepe`, `paytm` or `bhim`. | Show on the button. |
| `upi.upi_app_package_name` | string | iOS SDK identifier of the UPI app. For example, `google_pay` or `phonepe`. | Pass as `upi_app_package_name` when you submit the payment. |
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

## 1.6 Initialise RazorpayCheckout in Your ViewController

Conform to `RazorpayPaymentCompletionProtocolWithData` and `WKNavigationDelegate`, create a `WKWebView` and initialise the SDK with your API Key ID.

```swift Swift theme={null}
import Razorpay

class ViewController: UIViewController,
                      RazorpayPaymentCompletionProtocolWithData,
                      WKNavigationDelegate {

    var webView: WKWebView!
    var razorpay: RazorpayCheckout!

    override func viewDidLoad() {
        super.viewDidLoad()
        self.webView = WKWebView(frame: self.view.frame)
        self.razorpay = RazorpayCheckout.initWithKey(
            "YOUR_KEY_ID",
            andDelegate: self,
            withPaymentWebView: self.webView
        )
        self.view.addSubview(self.webView)
        self.webView.navigationDelegate = self
    }
}
```

Forward the `WKNavigationDelegate` callbacks to the SDK:

```swift Swift theme={null}
func webView(_ webView: WKWebView, didCommit navigation: WKNavigation!) {
    self.razorpay.webView(webView, didCommit: navigation)
}
func webView(_ webView: WKWebView, didFail navigation: WKNavigation!, withError er: Error) {
    self.razorpay.webView(webView, didFail: navigation, withError: er)
}
func webView(_ webView: WKWebView, didFailProvisionalNavigation navigation: WKNavigation!, withError er: Error) {
    self.razorpay.webView(webView, didFailProvisionalNavigation: navigation, withError: er)
}
func webView(_ webView: WKWebView, didFinish navigation: WKNavigation!) {
    self.razorpay.webView(webView, didFinish: navigation)
}
```

## 1.7 Submit Payment

When the customer taps the Quick Buy button, build the payment options as a dictionary and pass them to `razorpay.authorize()`. The result is returned to your delegate:

* `onPaymentSuccess` for a successful payment.
* `onPaymentError` for a failed payment.

#### Common Parameters

`order_id` *mandatory*
: `string` The order ID created in [step 1.5](#1-5-create-an-order-in-server).

`amount` *mandatory*
: `integer` Payment amount in the smallest currency sub-unit.

`currency` *mandatory*
: `string` The 3-letter ISO currency code. For example, `INR`.

`email` *mandatory*
: `string` Customer's email address.

`contact` *mandatory*
: `string` Customer's phone number.

`method` *mandatory*
: `string` Payment method. Possible values: `upi`, `card`, `netbanking`, `wallet` or `emi`.

`notes` *optional*
: `object` Key-value pairs for additional information. Maximum 15 pairs of 256 characters each.

> [tab] UPI Intent
>
> Pass the `upi_app_package_name` returned by `getRecommendedInstruments()` in [step 1.4](#1-4-fetch-recommended-instruments).
>
> ```swift Swift theme={null}
> let options: [String: Any] = [
>     "amount": 29935,
>     "currency": "INR",
>     "order_id": "order_DBJOWzybf0sJbb",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9000090000",
>     "method": "upi",
>     "_[flow]": "intent",
>     "upi_app_package_name": "google_pay"
> ]
> razorpay.authorize(options)
> ```

> [tab] Saved Card
>
> Pass the `token` returned by `getRecommendedInstruments()` in [step 1.4](#1-4-fetch-recommended-instruments) and collect only the CVV from the customer.
>
> ```swift Swift theme={null}
> let options: [String: Any] = [
>     "amount": 29935,
>     "currency": "INR",
>     "order_id": "order_DBJOWzybf0sJbb",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9000090000",
>     "method": "card",
>     "token": "token_Hf7vKlM2NpQrSt",
>     "card[cvv]": "123"
> ]
> razorpay.authorize(options)
> ```

> [tab] Netbanking
>
> ```swift Swift theme={null}
> let options: [String: Any] = [
>     "amount": 29935,
>     "currency": "INR",
>     "order_id": "order_DBJOWzybf0sJbb",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9000090000",
>     "method": "netbanking",
>     "bank": "HDFC"
> ]
> razorpay.authorize(options)
> ```

> [tab] Wallet
>
> ```swift Swift theme={null}
> let options: [String: Any] = [
>     "amount": 29935,
>     "currency": "INR",
>     "order_id": "order_DBJOWzybf0sJbb",
>     "email": "gaurav.kumar@example.com",
>     "contact": "9000090000",
>     "method": "wallet",
>     "wallet": "mobikwik"
> ]
> razorpay.authorize(options)
> ```

#### Handle the Result

```swift Swift theme={null}
func onPaymentSuccess(_ payment_id: String, andData response: [AnyHashable: Any]) {
    // response contains razorpay_payment_id, razorpay_order_id and razorpay_signature.
    // Send these to your server for verification (step 1.9).
}

func onPaymentError(_ code: Int32, description str: String, andData response: [AnyHashable: Any]) {
    // Handle the failure. code maps to the SDK error enum.
}

// Call when the customer dismisses your payment screen
@IBAction func cancel(_ sender: Any) {
    self.razorpay.userCancelledPayment()
}
```

## 1.8 Store Fields in Your Server

A successful payment returns these fields in the delegate's `response`. Store them on your server and verify the signature in the next step.

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

* [Test your integration](https://razorpay.com/docs/payments/payment-gateway/ios-integration/custom/test-integration.md) in Test Mode.
* Complete the [go-live checklist](https://razorpay.com/docs/payments/payment-gateway/ios-integration/custom/go-live-checklist.md).
* Replace your test API keys with live keys when you are ready to go live.

## Related Information

* [Embedded Quick Buy](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded.md)
* [Embedded Quick Buy FAQs](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/faqs.md)
* [iOS Custom UI SDK Integration](https://razorpay.com/docs/payments/payment-gateway/ios-integration/custom/build-integration.md)
