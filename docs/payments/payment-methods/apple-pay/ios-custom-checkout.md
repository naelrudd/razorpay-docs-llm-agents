> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# iOS Native Integration

> Accept Apple Pay payments in your native iOS app using Razorpay's Custom Checkout SDK. Build your own UI around the Apple Pay button with Razorpay handling payment processing.

Available in
🇮🇳 India

Use Razorpay Apple Pay to add Apple Pay to your iOS app. Razorpay handles payment processing; you build your own UI around the Apple Pay button.

> [!NOTE]
>
> **SDK Version**
>
> The Apple Pay feature is available in SDK version `2.2.0` and later.

## Prerequisites

| Requirement | Details |
| - | - |
| Razorpay account | With Apple Pay enabled (**Dashboard → Account & Settings → Payment Methods**) |
| Razorpay API key | `rzp_live_*` (your live key) |
| Apple Developer account | Required to configure an Apple Pay Merchant ID |
| Apple Pay Merchant ID | For example, `merchant.com.yourcompany.app` — created in the Apple Developer Portal |
| Merchant ID certificate | Uploaded to the Razorpay Dashboard so the backend can decrypt Apple Pay tokens |
| Xcode 14+ | iOS deployment target 13.0+ |
| Physical iOS device | Transactions can only complete on real devices |
| Server-side order | Created via the Razorpay Orders API |

## One-Time Setup (Before Code)

Complete this setup once before writing any integration code.

> [accordion] Apple Developer Portal Steps
>
> 1. **Create Apple Pay Merchant ID** — In the Apple Developer Portal, go to **Identifiers → + → Merchant IDs**. Use the format `merchant.com.yourcompany.app` and register.
>
> 2. **Share Merchant ID with Razorpay** — Send your Merchant ID to your Razorpay point of contact. The team will share a CSR file with you.
>
> 3. **Generate Certificate on Apple** — In the Apple Developer Portal, open your Merchant ID → **Create Certificate** under Apple Pay Payment Processing. Upload the `.csr`, then download the `apple_pay.cer`.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Certificates expire after 25 months. Set a reminder to renew before expiry.
>
> 4. **Share Certificate with Razorpay** — Send the `apple_pay.cer` file back to your Razorpay point of contact for configuration.

> [accordion] Xcode Steps
>
> 1. Open your `.xcodeproj`.
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

## Integration Steps

### Step 1 — Install via Swift Package Manager

The SDK is distributed as a Swift package at `https://github.com/razorpay/razorpay-customui-pod`.

1. In Xcode, select **File → Add Package Dependencies…**
2. Paste the package URL: `https://github.com/razorpay/razorpay-customui-pod`
3. Under **Dependency Rule**, choose **Exact Version** and enter `2.2.0`.
4. Click **Add Package**.
5. On the product selection screen, add the `RazorpayApplePay` library to your app target, then click **Add Package**.

`RazorpayApplePay` automatically pulls in its dependencies (`RazorpayCustom`, `RazorpayCore`) — you do not need to add those separately.

| Product | Add to Target? | Purpose |
| - | - | - |
| `RazorpayApplePay` | Yes | Apple Pay integration |
| `RazorpayCustomUI` | Yes | Umbrella product for the full Custom Checkout suite |

### Step 2 — Import and Conform to the Payment Completion Protocol

In your checkout view controller:

```swift Swift theme={null}
import UIKit
import WebKit
import Razorpay
import RazorpayApplePay

class CheckoutVC: UIViewController, RazorpayPaymentCompletionProtocol {
    // ...
}
```

| Protocol | Purpose |
| - | - |
| `RazorpayPaymentCompletionProtocol` | Payment success and error callbacks |

### Step 3 — Initialise the SDK with the Apple Pay Plugin

```swift Swift theme={null}
private var razorpay: RazorpayCheckout?
// Apple Pay runs through PassKit and requires a WKWebView.
// Pass a throwaway instance the SDK holds but never navigates.
private let dummyWebView = WKWebView()

override func viewDidLoad() {
    super.viewDidLoad()
    razorpay = RazorpayCheckout.initWithKey(
        "rzp_live_XXXXXXXXXX",
        andDelegate: self,
        withPaymentWebView: dummyWebView,
        ApplePay: ApplePay.pluginInstance()
    )
}
```

> [accordion] Initialisation Parameters
>
> | Parameter | Required | Description |
> | - | - | - |
> | `key` | Yes | Your Razorpay key ID — for example, `rzp_live_*xxxx` |
> | `andDelegate` | Yes | The object conforming to `RazorpayPaymentCompletionProtocol` |
> | `withPaymentWebView` | Yes | A `WKWebView` instance. Apple Pay does not use a webview, but Custom Checkout init requires one — pass a throwaway `WKWebView()` that you retain. |
> | `ApplePay` | Yes | An instance from `ApplePay.pluginInstance()` |

### Step 4 — Check if the Customer Can Pay

Call this before showing your Apple Pay button. It checks whether the user can pay via Apple Pay on their device.

```swift Swift theme={null}
applePayButton.isHidden = true

razorpay?.applePay?.canMakePayment { [weak self] canPay in
    DispatchQueue.main.async {
        self?.applePayButton.isHidden = !canPay
    }
}
```

### Step 5 — Create an Order on Your Server

Create a Razorpay order via the Orders API on your backend and send the `order_id` to your iOS app.

```bash Request theme={null}
curl -X POST https://api.razorpay.com/v1/orders \
  -u rzp_test_XXXXXXXXXX:your_secret \
  -H "Content-Type: application/json" \
  -d '{
    "amount": 50000,
    "currency": "INR"
  }'
```

The response returns an `order_id` such as `order_CuEzONfnOI86Ab`. Pass this to your iOS app.

> [accordion] Order Parameters
>
> | Key | Required | Description |
> | - | - | - |
> | `amount` | Yes | Payment amount in the smallest currency subunit. For example, for ₹299, pass `29900`. For three-decimal currencies such as KWD, BHD and OMR, to accept 295.991, pass `295990`. For zero-decimal currencies such as JPY, to accept 295, pass `295`. |
> | `currency` | Yes | The currency in which the transaction should be made. |

### Step 6 — Load the Payment Button

Apple's Human Interface Guidelines require the use of `PKPaymentButton` (or a visually compliant variant). Custom buttons will lead to App Store rejection.

```swift Swift theme={null}
import PassKit

private lazy var applePayButton: PKPaymentButton = {
    let btn = PKPaymentButton(
        paymentButtonType: .buy,
        paymentButtonStyle: .automatic
    )
    btn.addTarget(self,
                  action: #selector(applePayTapped),
                  for: .touchUpInside)
    return btn
}()
```

**Button constraints:**

* Use `PKPaymentButton`, not a generic `UIButton` with an Apple Pay icon.
* Do not place text or icons inside it.
* Respect Apple's minimum height requirement.
* Use `.automatic` style on iOS 14+ for automatic light/dark mode adaptation.

> [!NOTE]
>
> **Test on a Real Device**
>
> Run on a physical iOS device — transactions cannot complete on the simulator. Tap your Apple Pay button, authenticate with Face ID or Touch ID, then confirm the payment record appears in the Razorpay Dashboard.

### Step 7 — Trigger the Payment on User Tap

This call must be made in response to a user gesture (such as a button tap). Use the existing `razorpay.authorize(options)` API with an Apple Pay payload.

```swift Swift theme={null}
@objc func applePayTapped() {
    let options: [AnyHashable: Any] = [
        "amount":   50000,                        // in currency subunits (for example, paise)
        "currency": "INR",
        "email":    "test@example.com",
        "contact":  "+919898989898",
        "order_id": "order_xxxxxxxxx",
        "method":   "card",
        "app": [
            "name": "apple_pay",
            "apple_pay": [
                "merchant_identifier": "merchant.com.yourcompany.app"
            ]
        ]
    ]
    razorpay?.authorize(options)
}
```

> [accordion] Payment Parameters
>
> | Key | Required | Description |
> | - | - | - |
> | `amount` | Yes | Payment amount in the smallest currency subunit. For example, for ₹299, pass `29900`. |
> | `currency` | Yes | The currency for the transaction. |
> | `contact` | Yes | Customer phone number. Maximum length 15 characters, inclusive of country code. |
> | `email` | Optional | Customer email address. Maximum length 40 characters. |
> | `order_id` | Yes | Unique identifier of the order created in Step 5. |
> | `method` | Yes | Must be `"card"`. |
> | `app.name` | Yes | Must be `"apple_pay"`. |
> | `apple_pay.merchant_identifier` | Yes | Your Apple Pay Merchant ID from the Apple Developer Portal. |

### Step 8 — Handle the Payment Result

```swift Swift theme={null}
extension CheckoutVC: RazorpayPaymentCompletionProtocol {
    func onPaymentSuccess(_ payment_id: String,
                          andData response: [AnyHashable: Any]) {
        let orderId   = response["razorpay_order_id"]  as? String ?? ""
        let signature = response["razorpay_signature"] as? String ?? ""
        // Send payment_id, orderId, signature to your server
        // for signature verification.
    }

    func onPaymentError(_ code: Int32,
                        description str: String,
                        andData response: [AnyHashable: Any]) {
        // Handle failure or cancellation
    }
}
```

**Success response keys (in `andData`):**

```json Response theme={null}
{
    "razorpay_payment_id": "pay_XXXXXXXXXX",
    "razorpay_order_id":   "order_XXXXXXXXXX",
    "razorpay_signature":  "9ef4dffbfd84f1318f6739a3ce19f9d85851857ae648f114332d8401e0949a3d"
}
```

**Failure response keys (in `andData`):**

```json Response theme={null}
{
    "error": {
        "code":        "PAYMENT_CANCELLED",
        "description": "Customer dismissed the payment sheet.",
        "reason":      "payment_cancelled"
    }
}
```

### Step 9 — Verify Payment Signature on Your Server

Always verify the signature on your server before fulfilling the order. Send `razorpay_payment_id`, `razorpay_order_id`, and `razorpay_signature` to your backend for HMAC verification.

> [!WARNING]
>
> **Watch Out!**
>
> Never fulfil an order based solely on the client-side result. Always verify the payment signature server-side.

See the [signature verification guide](https://razorpay.com/docs/payments/server-integration/nodejs/integration-steps.md) for Node.js and other language samples.

## Error Codes

On failure, read the error code as a `String` from `response["error"]["code"]` inside the `andData` dictionary passed to `onPaymentError`.

> [!NOTE]
>
> **Handy Tips**
>
> The `code: Int32` parameter of `onPaymentError` is always `0` for Apple Pay — the actionable code is the `String` inside `andData`.

| Error | When It Fires |
| - | - |
| `INVALID_OPTIONS` | Missing `apple_pay.merchant_identifier`, missing or invalid amount, or a merchant key so malformed the request URL cannot be built. |
| `NO_SUPPORTED_CARD` | Device supports Apple Pay, but the Wallet has no card for the merchant's supported networks. |
| `DEVICE_NOT_SUPPORTED` | Apple Pay unavailable on the device — hardware, OS, region, or restrictions. |
| `SHEET_PRESENTATION_FAILED` | PassKit declined to present the payment sheet. |
| `PAYMENT_CANCELLED` | Customer dismissed the sheet or cancelled at the Face ID or Touch ID prompt. |
| `NETWORK_ERROR` | Connection loss, timeout, or any transport-level failure. |
| `PAYMENT_FAILED` | Internal or processing failure (serialise failure, empty or unparseable response) and the normalised code for any backend decline. |

## Complete Working Example

> [tab] UIKit
>
> ```swift Swift theme={null}
> import UIKit
> import WebKit
> import PassKit
> import Razorpay
> import RazorpayApplePay
>
> class CheckoutVC: UIViewController, RazorpayPaymentCompletionProtocol {
>     private var razorpay: RazorpayCheckout?
>     private let dummyWebView = WKWebView()
>     @IBOutlet weak var statusLabel: UILabel!
>
>     private lazy var applePayButton: PKPaymentButton = {
>         let btn = PKPaymentButton(paymentButtonType: .buy, paymentButtonStyle: .automatic)
>         btn.cornerRadius = 8
>         btn.translatesAutoresizingMaskIntoConstraints = false
>         btn.addTarget(self, action: #selector(applePayTapped), for: .touchUpInside)
>         return btn
>     }()
>
>     override func viewDidLoad() {
>         super.viewDidLoad()
>         razorpay = RazorpayCheckout.initWithKey(
>             "rzp_live_XXXXXXXXXX",
>             andDelegate: self,
>             withPaymentWebView: dummyWebView,
>             ApplePay: ApplePay.pluginInstance()
>         )
>         view.addSubview(applePayButton)
>         NSLayoutConstraint.activate([
>             applePayButton.centerXAnchor.constraint(equalTo: view.centerXAnchor),
>             applePayButton.centerYAnchor.constraint(equalTo: view.centerYAnchor),
>             applePayButton.widthAnchor.constraint(equalToConstant: 250),
>             applePayButton.heightAnchor.constraint(equalToConstant: 48)
>         ])
>         applePayButton.isHidden = true
>         razorpay?.applePay?.canMakePayment { [weak self] canPay in
>             DispatchQueue.main.async { self?.applePayButton.isHidden = !canPay }
>         }
>     }
>
>     @objc func applePayTapped() {
>         let options: [AnyHashable: Any] = [
>             "amount": 50000, "currency": "INR",
>             "email": "gaurav.kumar@example.com", "contact": "+919876543210",
>             "order_id": "order_CuEzONfnOI86Ab", "method": "card",
>             "app": [
>                 "name": "apple_pay",
>                 "apple_pay": ["merchant_identifier": "merchant.com.yourcompany.app"]
>             ]
>         ]
>         razorpay?.authorize(options)
>     }
>
>     func onPaymentSuccess(_ payment_id: String, andData response: [AnyHashable: Any]) {
>         statusLabel.text = "Success: \(payment_id)"
>     }
>
>     func onPaymentError(_ code: Int32, description str: String, andData response: [AnyHashable: Any]) {
>         statusLabel.text = "Error: \(str)"
>     }
> }
> ```

> [tab] SwiftUI
>
> ```swift Swift theme={null}
> import SwiftUI
> import WebKit
> import PassKit
> import Razorpay
> import RazorpayApplePay
>
> struct ApplePayButton: UIViewRepresentable {
>     let action: () -> Void
>     func makeUIView(context: Context) -> PKPaymentButton {
>         let btn = PKPaymentButton(paymentButtonType: .buy, paymentButtonStyle: .automatic)
>         btn.addTarget(context.coordinator, action: #selector(Coordinator.tap), for: .touchUpInside)
>         return btn
>     }
>     func updateUIView(_ uiView: PKPaymentButton, context: Context) {}
>     func makeCoordinator() -> Coordinator { Coordinator(action: action) }
>     class Coordinator: NSObject {
>         let action: () -> Void
>         init(action: @escaping () -> Void) { self.action = action }
>         @objc func tap() { action() }
>     }
> }
>
> struct CheckoutView: View {
>     @StateObject private var coordinator = CheckoutCoordinator()
>     var body: some View {
>         VStack {
>             Text(coordinator.status)
>             if coordinator.applePayAvailable {
>                 ApplePayButton { coordinator.startPayment() }.frame(height: 48)
>             }
>         }.onAppear { coordinator.setup() }
>     }
> }
>
> class CheckoutCoordinator: NSObject, ObservableObject, RazorpayPaymentCompletionProtocol {
>     @Published var status = "Ready"
>     @Published var applePayAvailable = false
>     private var razorpay: RazorpayCheckout?
>     private let dummyWebView = WKWebView()
>
>     func setup() {
>         razorpay = RazorpayCheckout.initWithKey(
>             "rzp_live_XXXXXXXXXX",
>             andDelegate: self,
>             withPaymentWebView: dummyWebView,
>             ApplePay: ApplePay.pluginInstance()
>         )
>         razorpay?.applePay?.canMakePayment { [weak self] canPay in
>             DispatchQueue.main.async { self?.applePayAvailable = canPay }
>         }
>     }
>
>     func startPayment() {
>         let options: [AnyHashable: Any] = [
>             "amount": 50000, "currency": "INR",
>             "email": "gaurav.kumar@example.com", "contact": "+919876543210",
>             "order_id": "order_CuEzONfnOI86Ab", "method": "card",
>             "app": [
>                 "name": "apple_pay",
>                 "apple_pay": ["merchant_identifier": "merchant.com.yourcompany.app"]
>             ]
>         ]
>         razorpay?.authorize(options)
>     }
>
>     func onPaymentSuccess(_ payment_id: String, andData response: [AnyHashable: Any]) {
>         status = "Success: \(payment_id)"
>     }
>     func onPaymentError(_ code: Int32, description str: String, andData response: [AnyHashable: Any]) {
>         status = "Error: \(str)"
>     }
> }
> ```

## Frequently Asked Questions

> [accordion] I use a table view or collection view where payment methods expand on selection. How does the plugin fit?
>
> The plugin separates detection from payment. Use `canMakePayment` to decide whether to include the Apple Pay row at all. When the user selects that row, show the Apple Pay button. When they tap your CTA, call `razorpay.authorize(options)` with the Apple Pay payload.
>
> ```swift Swift theme={null}
> // On view setup
> razorpay?.applePay?.canMakePayment { [weak self] canPay in
>     DispatchQueue.main.async {
>         if canPay { self?.paymentMethods.append(.applePay) }
>         self?.tableView.reloadData()
>     }
> }
>
> // When user taps the CTA inside the expanded row
> @IBAction func payTapped() {
>     let options: [AnyHashable: Any] = [ /* full Apple Pay payload */ ]
>     razorpay?.authorize(options)
> }
> ```

> [accordion] Do I need to import PassKit?
>
> Yes. PassKit provides Apple's `PKPaymentButton` for the button UI. It is part of iOS, so it adds no dependency weight. You will also need to import `WebKit` since Custom Checkout init requires a `WKWebView` instance.

> [accordion] The Apple Pay sheet appears but the transaction always fails. What should I check?
>
> * **Merchant ID alignment** — Does the Merchant ID you passed in `options["app"]["apple_pay"]["merchant_identifier"]` match the one in your `.entitlements` and the one uploaded to the Razorpay Dashboard?
> * **Certificate uploaded** — Is the CSR-signed certificate for that Merchant ID present in the Razorpay Dashboard?
> * **Network match** — Are you testing with a card whose network is enabled for your Razorpay account?
> * **Backend support** — Is Apple Pay enabled for your account in the Razorpay Dashboard?
>
> If all four are correct, check the response in `onPaymentError`'s `andData` for the specific failure reason from the backend.

### Related Information

* [Apple Pay Standard Checkout](https://razorpay.com/docs/payments/payment-methods/apple-pay.md)
* [Apple Pay – Custom Checkout](https://razorpay.com/docs/payments/payment-methods/apple-pay/custom-integration.md)
* [Apple Pay Web Component Integration](https://razorpay.com/docs/payments/payment-methods/apple-pay/custom-integration/web-sdk/web-component.md)
