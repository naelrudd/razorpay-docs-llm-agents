> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Customisation Options

> Customise the Affordability Widget on your Android App.

Available in
🇮🇳 India

After you successfully integrate the widget on your Android app, create a JSON Object as per your customisation requirements and add it as an additional parameter in the `loadwidget()` method. Check all the [customisation options](https://razorpay.com/docs/payments/payment-gateway/emi²/widget/native-web/customise.md) available.

```java Java theme={null}
JSONObject widgetConfig = new JSONObject(
    "{" +
        "\"key\": \"YOUR_KEY_ID\"," + // Enter your Live Key ID generated from the Dashboard
        "\"amount\": 400000," +
        "\"currency\": \"INR\"," +
        "\"display\": {" +
            "\"offers\": false" +
        "}" +
    "}"
);

widget.render(this, widgetConfig);
```

```kotlin Kotlin theme={null}
val widgetConfig = JSONObject(
    """
    {
        "key": "YOUR_KEY_ID", // Enter your Live Key ID generated from the Dashboard
        "amount": 400000,
        "currency": "INR",
        "display": {
            "offers": false
        }
    }
    """.trimIndent()
)

widget.render(this, widgetConfig)
```

### Related Information

* [FAQs](https://razorpay.com/docs/payments/payment-gateway/emi²/faqs.md)
* [About Affordability Widget](https://razorpay.com/docs/payments/payment-gateway/emi²/widget.md)
