# Customisation Options

After you successfully integrate the widget on your Android app, create a JSON Object as per your customisation requirements and add it as an additional parameter in the `loadwidget()` method. Check all the [customisation options](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/emi²/widget/native-web/customise.md) available.

```java: Java
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

```kotlin: Kotlin
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

- [FAQs](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/emi²/faqs.md)
- [About Affordability Widget](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/emi²/widget.md)
