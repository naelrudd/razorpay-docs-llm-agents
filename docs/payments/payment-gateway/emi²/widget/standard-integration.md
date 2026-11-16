> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integrate Checkout From Widget

> Integrate Checkout from Affordability Widget using Standard Integration and allow your customers to complete their purchase directly from the widget.

Available in
🇮🇳 India

Integrate Checkout from Affordability Widget using Standard Integration and provide customers with a direct and convenient avenue to complete their purchases within the widget itself. This helps businesses improve conversion rates and eliminate any friction or unnecessary steps in the buying process.

> [!NOTE]
>
> **Handy Tips**
>
> If you have a [custom-built checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom), integrate with checkout from widget using [Custom Integration](https://razorpay.com/docs/payments/payment-gateway/emi²/widget/custom-integration).

> [!WARNING]
>
> **Watch Out!**
>
> * This is an on-demand feature. Write to us at [affordability-widget@razorpay.com](mailto:affordability-widget@razorpay.com) to get this feature enabled on your account.
> * This feature is only supported on [Native Website](https://razorpay.com/docs/payments/payment-gateway/emi²/widget/native-web.md) integration.

> [accordion] Advantages
>
> * **Improved Conversion Rates** \\
>
>   The improved Affordability Widget simplifies the checkout process, leading to more customers completing their purchases, resulting in higher conversion rates.
>
> * **Frictionless Customer Experience** \\
>
>   The widget provides a seamless and hassle-free experience, boosting customer confidence and encouraging them to finalise their purchases easily.
>
> * **Auto-Selection Convenience** \\
>
>   The widget's auto-selection functionality automatically applies the chosen payment option or offer to the checkout, reducing confusion and making the process more convenient.

## Prerequisites

* Create a [Razorpay account](https://dashboard.razorpay.com/signup).
* Generate the [API keys](https://razorpay.com/docs/api/authentication.md#generate-api-keys) from the Dashboard. You can use the **Test Mode** keys to test the integration and preview the Widget. Later, switch to **Live Mode** of the Dashboard, generate the [Live API keys](https://razorpay.com/docs/api/authentication.md#live-mode-api-keys) and replace it with the test keys.
* Integrate with the [Razorpay Affordability Widget](https://razorpay.com/docs/payments/payment-gateway/emi²/widget/native-web.md).

## Integration Steps

Follow the integration steps given below on your website:

> [accordion] 1 Define Checkout Callback Function
>
> Define a callback function that receives the `affordabilityWidgetPrefill` as an argument. This function is invoked when the customer clicks the **Buy Now** button on the widget.
>
> The prefill data is a string that contains the payment instrument details or `offer_id` used to invoke checkout from the widget. You can use any custom logic to save this data for the future. After saving the prefill data, you can seamlessly initiate your website’s checkout process and redirect the customer to the preferred location as per your website’s checkout journey.
>
> ```javascript JavaScript theme={null}
> function checkoutCallback(affordabilityWidgetPrefill) {
>   // Your logic to save affordabilityWidgetPrefill 
>
>   // Perform redirection to cart page or any other preferred location as per your website’s checkout journey
> }
> ```
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > * Consider storing the prefill data as a component state if you use a frontend framework like React.
> > * Alternatively, you can store it in `localstorage` or use any other storage method.

> [accordion] 2 Pass Function in Affordability Widget Configuration
>
> Pass the callback function [previously defined](#1-define-checkout-callback-function) to `widgetConfig` as `checkout_callback`, when initialising Razorpay Affordability Widget.
>
> ```javascript JavaScript theme={null}
> window.addEventListener('DOMContentLoaded', () => {
>     const widgetConfig = {
>         key: 'YOUR_KEY_ID', // Replace it with your live Key ID generated from Razorpay Dashboard
>         amount: 400000, // Amount in paise
>         currency: 'INR', 
>         checkout_callback: checkoutCallback // new
>     };
>
>     const rzpAffordabilityWidget = new RazorpayAffordabilitySuite(widgetConfig);
>     rzpAffordabilityWidget.render();
> });
> ```
>
> `key` *mandatory*
> : `string` API Key ID generated from the Dashboard.
>
> `amount` *mandatory*
> : `integer` The amount to be paid by the customer in currency subunits. For example, if the amount is ₹500, enter `50000`.
>
> `currency` *mandatory*
> : `string` The currency in which the customer should make the payment. Check the list of [supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).
>
> `checkout_callback` *mandatory*
> : `function` The callback function is called when the user clicks the Buy button on the widget. This function receives `affordabilityWidgetPrefill` as an argument.

> [accordion] 3 Initiate Payment Checkout with Option Selected
>
> Before opening the payment checkout for your customer with the selected option on the widget, retrieve `affordabilityWidgetPrefill` from your global store/localstorage or anywhere you stored it and pass it in the checkout options that you use to open Razorpay Standard Checkout.
>
> ```javascript JavaScript theme={null}
> <button id="rzp-button1">Pay</button>
> <script src="https://checkout.razorpay.com/v1/checkout.js"></script>
> <script src="https://cdn.razorpay.com/widgets/emi²/affordability.js"> </script> // new
> <script>
>   var options = {
>     "key": "YOUR_KEY_ID", 
>     "amount": "400000", 
>     "currency": "INR"
>     // ... other options
>   };
>   options = RazorpayAffordabilitySuite.addPrefillToCheckoutOptions(options, affordabilityWidgetPrefill); // new
>   var rzp1 = new Razorpay(options);
>   document.getElementById('rzp-button1').onclick = function(e){
>     rzp1.open();
>     e.preventDefault();
>   }
> </script>
> ```
