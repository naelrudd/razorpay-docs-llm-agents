> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Troubleshooting & FAQs

> Troubleshoot common error scenarios and find answers to frequently asked questions about Standard Android integration.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

> [accordion] Android app is crashing every time I invoke `RazorpayCheckout.open API`. How to resolve this?
>
> The Android App crashes because the theme color parameter is passed in curly braces.
>
> Use the code given below to resolve the problem:
>
> ```java theme={null}
> JSONObject options = new JSONObject();
>     options.put("name", "Acme Corp");
>     options.put("description", "Reference No. #123456");
>     options.put("image", "http://example.com/image/rzp.jpg");
>     options.put("order_id", "order_DBJOWzybf0sJbb");//from response of step 3.
>     options.put("theme.color", "#3399CC");
> ```

> [accordion] During checkout, the **Paying To** name reflects my company name. Is it possible to change the **Paying To** name from my company name to my product name?
>
> No. **Paying to** gives your business name and not the product name. It is a standard flow. So you cannot change it.

> [accordion] Does Razorpay support Xamarin for SDK integration?
>
> No, we do not support Xamarin. However, since Xamarin is essentially a wrapper around Android and iOS, you can create your own Xamarin wrapper using our [Android](https://razorpay.com/docs/us/payments/payment-gateway/android-integration/standard.md) and [iOS](https://razorpay.com/docs/us/payments/payment-gateway/ios-integration/standard.md) SDKs.
>
> You can refer to Xamarin for integrating native [Android](https://docs.microsoft.com/en-us/xamarin/android/platform/binding-java-library/) and [iOS](https://docs.microsoft.com/en-us/xamarin/ios/platform/binding-objective-c/) libraries. Alternatively, you can use web integration to open the checkout form in a web view.

> [accordion] How can I check the Razorpay Android Standard SDK version?
>
> To check the SDK version:
>
> 1. Open your Android project in Android Studio.
> 2. Navigate to the `build.gradle` file of your app module (usually `app/build.gradle`).
> 3. Locate the `dependencies` block in the file.
> 4. Find the line that includes the Razorpay SDK dependency. The version number will be alongside the SDK name in the format`x.y.z`.
>
> ```java build.gradle theme={null}
>  repositories {
>      mavenCentral()
>  }
>
>  dependencies {
>      implementation 'com.razorpay:checkout:1.6.40'
>  }
> ```
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > From version 1.6.40 onwards, the latest version is automatically updated, eliminating the need for manual updates.

> [accordion] How can I update the Razorpay Android Standard SDK version?
>
> To update the Standard Android SDK, follow these steps:
>
> 1. Check the [latest SDK version](https://mvnrepository.com/artifact/com.razorpay/checkout).
>
> 2. In the app-level gradle build file, update the SDK version to the latest release.
>    dependencies \{
>    //    … other dependencies
>    //  For Razorpay checkout SDK
>    implementation ‘com.razorpay:checkout:\<latest-version-name-goes-here>’
>    //    … other dependencies
>
>    }
>
> 3. After updating, sync gradle and check for any compile-time errors.
>
> 4. Ensure all changes are correctly integrated and the application functions as expected.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > From version 1.6.40 onwards, the latest version is automatically updated, eliminating the need for manual updates.
