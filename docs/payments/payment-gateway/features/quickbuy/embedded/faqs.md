> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Embedded Quick Buy FAQs

> Answers to common questions about Embedded Quick Buy: eligibility, PCI-DSS, supported platforms, recommended instruments, testing and SDK troubleshooting.

Available in
🇮🇳 India

## General

> [accordion] 1. How is Embedded Quick Buy different from QuickBuy on Standard Checkout?
>
> QuickBuy on Standard Checkout shows a generic **Pay Now** button on your page. When the customer taps it, the recommended instrument opens in the Razorpay Checkout modal.
>
> Embedded Quick Buy shows the recommended instrument directly on your page, wherever you choose to place it.

> [accordion] 2. Can I integrate Embedded Quick Buy if I use Standard Checkout, Custom Checkout or an S2S integration?
>
> Yes. Businesses on all three integrations can use Embedded Quick Buy. You need to add the lightweight Razorpay Custom SDK, which powers the Quick Buy button.

> [accordion] 3. Do I need to be PCI-DSS compliant to show card details?
>
> No. You do not store any card data. You fetch the recommended instrument from Razorpay, and saved cards reach you as Razorpay tokens. So there is no PCI-DSS requirement.

> [accordion] 4. Which platforms support Embedded Quick Buy?
>
> Embedded Quick Buy is available on:
>
> * [Mobile web](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/mobile-web.md)
> * [Android](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/android.md)
> * [iOS](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/ios.md)
> * [React Native](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/react-native.md)
> * [Flutter](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/flutter.md)

> [accordion] 5. Does Embedded Quick Buy affect my existing checkout integration?
>
> No. Embedded Quick Buy is an addition to your current checkout. It appears before checkout and hands over to your existing Razorpay Checkout when the customer taps **Change payment method** or has no recommended instrument. Your current checkout flow is unaffected until you deploy the Quick Buy button. You do not need to change your Orders API integration.

> [accordion] 6. How many instruments are returned, and can I choose which ones?
>
> Razorpay returns up to 3 instruments, ranked by how likely the customer is to complete the payment. Razorpay decides the count and the instruments. You cannot configure them.
>
> To offer more options than the top recommendation, send the customer to the full checkout through **Change payment method** rather than showing all 3 as separate buttons.

> [accordion] 7. What happens if I do not pass an order\_id or a customer\_id?
>
> * Without an `order_id`, the response is limited to UPI intent apps. Saved cards are not returned.
> * Without a `customer_id`, pass the customer's contact number. If neither is available, or the customer has no recommended instruments, the response returns an empty `items` array. Treat this as a normal response, not an error, and show your regular checkout button.

> [accordion] 8. Should I show an intermediate screen when the customer changes the payment method?
>
> No. Take the customer straight to the full Razorpay Checkout. An extra screen adds a step and can cause drop-offs. Razorpay Checkout already shows recommended instruments at the top, along with all other payment methods.

> [accordion] 9. Is Cash on Delivery (COD) part of Quick Buy?
>
> No. COD is not part of the Quick Buy flow, and you handle COD separately by default. If you want to offer COD on Razorpay Checkout, you can enable it separately.

> [accordion] 10. Can I test Embedded Quick Buy before going live?
>
> Yes. You can test the full flow, including fetching recommended instruments, creating orders and submitting payments, in Test Mode with your test API keys. Going live with Quick Buy does not affect your existing checkout. It takes effect only when you deploy the Quick Buy button to production.

## Mobile Web

> [accordion] 1. I use Standard Checkout (checkout.js). What else do I need for Quick Buy on mobile web?
>
> Quick Buy on mobile web is built on Custom Checkout (`razorpay.js`). Include `razorpay.js`, create customers and fetch recommended instruments to power the Quick Buy button. Your Standard Checkout remains the fallback when the customer taps **Change payment method**. Know more about the [mobile web integration](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/mobile-web.md).

> [accordion] 2. How do I handle a UPI app that is not installed on the customer's device?
>
> On mobile web, the browser cannot check which apps are installed. Native SDKs can, and they drop apps that are not installed. On mobile web, show every UPI app returned. If the app is not installed, the device handles the failed deep link. You do not need to handle this case.

## React Native SDK

> [accordion] 1. I use react-native-razorpay. Do I also need react-native-customui?
>
> Yes. Quick Buy is powered by the Custom UI SDK. Use `react-native-customui` to fetch recommended instruments and power the Quick Buy button. Continue to use `react-native-razorpay` to open the full Standard Checkout when the customer taps **Change payment method**.

> [accordion] 2. Which SDK version do I need?
>
> Use [react-native-customui](https://www.npmjs.com/package/react-native-customui) version 2.2.9 or later. It includes `getRecommendedInstruments()`, the fix for the iOS `pod install` framework conflict and consistent UPI app detection on Android.

> [accordion] 3. Do I need to link react-native-customui manually on Android?
>
> No. React Native autolinking handles the Android module. Linking it manually in `settings.gradle`, `app/build.gradle` or `MainApplication` conflicts with autolinking and fails the Gradle build.
>
> The `com.razorpay.rn.RazorpayPackage` import belongs to `react-native-razorpay`, not `react-native-customui`.

> [accordion] 4. The Android Gradle build fails with an implicit dependency error. How do I fix it?
>
> You may see this error:
>
> ```text Error theme={null}
> Task ':react-native-razorpay:packageDebugResources' uses this output of
> task ':react-native-customui:generateDebugResValues' without declaring an
> explicit or implicit dependency.
> ```
>
> It occurs when `react-native-customui` is linked manually while autolinking also picks it up. To fix it, remove the manual linking.
>
> 1. From `android/settings.gradle`, remove:
>    ```groovy settings.gradle theme={null}
>    include ':react-native-customui'
>    project(':react-native-customui').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-customui/android')
>    ```
> 2. From `android/app/build.gradle`, remove:
>    ```groovy build.gradle theme={null}
>    implementation project(':react-native-customui')
>    ```
> 3. From `MainApplication.kt`, remove the package if you added it only for the Custom UI SDK:
>    ```kotlin MainApplication.kt theme={null}
>    add(RazorpayPackage()) // remove if added only for customui
>    ```
> 4. Clean and rebuild:
>    ```bash Terminal theme={null}
>    rm -rf android/.gradle android/build android/app/build
>    rm -rf node_modules/react-native-customui/android/build
>    rm -rf node_modules/react-native-razorpay/android/build
>    cd android && ./gradlew clean
>    ```

> [accordion] 5. pod install fails with conflicting frameworks razorpay.xcframework and razorpaycore.xcframework. Why?
>
> This can happen when both `react-native-razorpay` and `react-native-customui` are installed. Update the pods by running `pod install` again to pull the latest SDK version, which resolves the conflict. No other change is needed.

> [accordion] 6. getRecommendedInstruments() crashes because the SDK instance is null. Why?
>
> On Android, `initRazorpay()` initialises the SDK on the UI thread and does not return a promise. If you call `getRecommendedInstruments()` immediately after it, initialisation may not be complete.
>
> Call `initRazorpay()` earlier in the flow, for example when the checkout screen loads or when you first fetch your API key. Call `getRecommendedInstruments()` after a short delay or in a later interaction.

> [accordion] 7. getRecommendedInstruments() fails even though the SDK is initialised. Why?
>
> Check that the options include a `customer` object with a `contact` field. It is mandatory by default, although this depends on your account configuration. If it is required and missing, the call fails.
>
> ```javascript JavaScript theme={null}
> Razorpay.getRecommendedInstruments({
>   amount: 100,
>   currency: 'INR',
>   customer: {
>     contact: '+919123456780'
>   }
> });
> ```

> [accordion] 8. When the customer taps a recommended UPI app, a different app opens. Why?
>
> There are two possible causes:
>
> * **Inconsistent app detection on the device**: Some UPI apps respond inconsistently when the device checks whether they are ready. Upgrade to `react-native-customui` 2.2.9 or later, which keeps UPI app detection consistent on Android.
> * **Incomplete payment payload**: Make sure the payment request includes the selected app's package name in `upi_app_package_name`.

## Related Information

* [Embedded Quick Buy](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded.md)
* [QuickBuy](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy.md)
