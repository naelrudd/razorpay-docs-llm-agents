> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Additional Support for Payment Methods

> Additional support features available for card, netbanking, wallets and more.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use the Razorpay Android Standard SDK to integrate supported payment methods on the Checkout form of your Android app as per your business requirements. Here are some additional methods provided by the SDK for the integration and usage of payment methods:

<ul>
  <li>[UPI Intent support on Target SDK Version 30 and above](#upi-intent-support-target-sdk-version-30+)</li>
  <li>[UPI Intent on Recurring Payments](#upi-intent-on-recurring-payments)</li>
  <li>[Card Utilities](#card-utilities)</li>
  <li>[Fetch Logo](#fetch-bank-logo-url)</li>
  <li>[Validate Data](#data-validation)</li>
  <li>[Custom `WebViewClient` and `WebChromeClient`](#custom-webviewclient-and-webchromeclient)</li>
</ul>

## UPI Intent Support: Target SDK Version 30+

If your application `targetSdkVersion` is 30 or above, add the following code in your app's manifest file to support the UPI Intent flow.

```xml AndroidManifest.xml theme={null}
<queries>
    <!-- List of apps which you want to support for Intent pay -->
    <package android:name="com.google.android.apps.nbu.paisa.user" />
    <package android:name="com.phonepe.app"/>
    <!--
         Specific intents you query for,
         eg: for a custom share UI
    -->
    <intent>
        <action android:name="android.intent.action.SEND" />
    </intent>
</queries>
```

> [!NOTE]
>
> **Handy Tips**
>
> * Refer to the list of [supported UPI apps](https://razorpay.com/docs/payments/payment-methods/upi/supported-apps.md).
> * Additionally, we recommend you to create 2 sections - **Primary** and **Others**. Under **Primary**, display the following 4 apps:
>   * GPay
>   * PhonePe
>   * Paytm
>   * BHIM

## UPI Intent on Recurring Payments

Configure and initiate a recurring payment transaction on UPI Intent:

> [!WARNING]
>
> **Watch Out!**
>
> This is an on-demand feature. Please raise a request with our [Support team](https://razorpay.com/support/#request) to get it enabled on your Razorpay account.

```java Java theme={null}
JSONObject options = new JSONObject();
options.put("name", "Gaurav Kumar");
options.put("description", "Reference No. #123456");
options.put("image", "http://example.com/image/rzp.jpg");
options.put("order_id", "order_DBJOWzybf0XXXX"); // from response of order creation step
options.put("theme.color", "#3399cc");
options.put("currency", "INR");
options.put("amount", "50000"); // pass amount in currency subunits
options.put("prefill.email", "gaurav.kumar@example.com");
options.put("prefill.contact", "9000090000");

JSONObject retryObj = new JSONObject();
retryObj.put("enabled", true);
retryObj.put("max_count", 4);
options.put("retry", retryObj);

options.put("recurring", 1);
options.put("customer_id", "cust_xxxxxxxxx");

options.put("method", new JSONObject().put("upi", true));
```

```kotlin Kotlin theme={null}
val options = JSONObject()

options.put("name", "Gaurav Kumar")
options.put("description", "Reference No. #123456")
options.put("image", "http://example.com/image/rzp.jpg")
options.put("order_id", "order_DBJOWzybf0XXXX") // from response of order creation step
options.put("theme.color", "#3399cc")
options.put("currency", "INR")
options.put("amount", "50000") // pass amount in currency subunits
options.put("prefill.email", "gaurav.kumar@example.com")
options.put("prefill.contact", "9000090000")

val retryObj = JSONObject()
retryObj.put("enabled", true)
retryObj.put("max_count", 4)
options.put("retry", retryObj)

options.put("recurring", 1)
options.put("customer_id", "cust_xxxxxxxxx")
options.put("method", JSONObject().put("upi", true))
```

## Card Utilities

You can use these methods for card payment method integration.

* [Fetch card network](#fetch-card-network)
* [Validate card number](#validate-card-number)
* [Fetch card number length of a card network](#fetch-card-number-length-for-card-network)

#### Fetch Card Network

The SDK provides a method to get the card network name of the provided card number. \


* At least 6 digits of the card number are required to identify the network. \

* Possible values returned by this method are `visa`, `mastercard` and `unknown`.\

* If it is not able to identify the network it returns `unknown`.

```java Fetch Card Network theme={null}
razorpay.getCardNetwork(cardNumber);
```

#### Validate Card Number

You can determine the validity of the card number entered using the `isValidCardNumber` method. This is a checksum-based method to determine if the entered card number is valid or not.

```java Card Number Validation theme={null}
razorpay.isValidCardNumber(cardNumber);
```

#### Fetch Card Number Length for Card Network

You can fetch the length of a card number for a specific card network using the `getCardNetworkLength` method.

```java Fetch Length for Card Network theme={null}
razorpay.getCardNetworkLength(cardNetworkName);
```

## Logo

You can use the respective methods to fetch:

* [Bank Logo URL](#fetch-bank-logo-url)

* [Wallet Logo URL](#fetch-wallet-logo-url)

* [Square-shaped Wallet Logo URL](#fetch-wallet-square-logo-url)

#### Fetch Bank Logo URL

The SDK provides a method to fetch the bank logo's URL, here `bankCode` is the code of bank, you will be able to get it from the response received in `onPaymentMethodsReceived` callback.

```java Fetch Bank Logo URL theme={null}
razorpay.getBankLogoUrl(bankCode);
```

#### Fetch Wallet Logo URL

The SDK provides a method to get the wallet logo's URL.

```java Fetch Wallet Logo URL theme={null}
razorpay.getWalletLogoUrl(walletName);
```

#### Fetch Wallet Square Logo URL

The SDK provides a method to get the wallet's square-shaped logo's URL.

```java Fetch Wallet Square Logo URL theme={null}
razorpay.getWalletSqLogoUrl(walletName);
```

## Data Validation

The SDK provides basic validation for the payment data `JSONObject`. In case of a validation error, the SDK returns an error map in the `onValidationError` callback function.

#### Sample Code

The sample code shown below describes a validation error on the `contact` field:

```java Data Validation theme={null}
razorpay.validateFields(payload, new Razorpay.ValidationListener() {
	@Override
	public void onValidationSuccess() {
		try {
		  razorpay.submit(payload);
		} catch (Exception exception){}
	}

	@Override
	public void onValidationError(Map<String, String> error) {
		/**
		 * The format for returned map is:
		 *   "field" : "contact"
		 *   "description" : "Descriptive error message"
		 */
		Toast.makeText(activity, "Validation: " + error.get("field") + " " + error.get("description"), Toast.LENGTH_SHORT).show();
	}
});
```

## Custom `WebViewClient` and `WebChromeClient`

Our SDK sets an instance of `RazorpayWebViewClient` and `RazorpayWebChromeClient` to the Webview passed to facilitate bank page optimizations. If you want to set your own custom `WebViewClient` you have to extend `RazorpayWebViewClient` and pass it to our SDK.

> [!WARNING]
>
> **Watch Out!**
>
> This step is optional and is only required when you want to set a custom `WebViewClient`/`WebChromeClient`

#### Sample Code

The sample code given below shows how to customize the `RazorpayWebViewClient`:

```java Customize RazorpayWebViewClient theme={null}
/**
 * Extend the RazorpayWebViewClient for your custom hooks
 */
razorpay.setWebviewClient(new RazorpayWebViewClient(razorpay){

  @Override
  public void onPageStarted(WebView view, String url, Bitmap favicon) {
      // Make sure you do not forget to call the super method
      super.onPageStarted(view, url, favicon);
      Log.d(TAG, "Custom client onPageStarted");
  }

  @Override
  public void onPageFinished(WebView view, String url) {
      // Make sure you do not forget to call the super method
      super.onPageFinished(view, url);
      Log.d(TAG, "Custom client onPageFinished");
  }
});
```

Similarly, you can set your own `WebChromeClient`:

```java Set WebChromeClient theme={null}
/**
 * Extend the RazorpayWebChromeClient for your custom hooks
 */
razorpay.setWebChromeClient(new RazorpayWebChromeClient() {
	@Override
	public void onProgressChanged(WebView view, int newProgress) {
		// Make sure you do not forget to call the super method
		super.onProgressChanged(view, newProgress);
		customProgressBar.setProgress(newProgress);
	}
});
```
