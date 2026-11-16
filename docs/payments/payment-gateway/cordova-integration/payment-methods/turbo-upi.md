> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integrate with Turbo UPI

> Steps to integrate Razorpay Turbo UPI with your app.

Available in
🇮🇳 India

> [card] [Turbo UPI Cordova Standard SDK](https://razorpay.com/docs/payments/changelog.md#products)
>
> Discover new features, updates and deprecations related to Turbo UPI on Cordova Standard Checkout (since Jan 2024).

With Razorpay Turbo UPI, businesses experience faster and simpler payments. It condenses the payment process from 5 steps to just 1, eliminating app redirections. Enjoy a seamless in-app payment experience, reduce dependencies on third-party UPI apps, and gain complete visibility of the payment journey.

You can seamlessly integrate Turbo UPI with Razorpay Cordova Standard SDK. Explore the full potential of [Razorpay Turbo UPI](https://razorpay.com/docs/payments/payment-methods/upi/turbo-upi.md) and know how it works.

![Turbo UPI Standard Checkout Flow](https://razorpay.com/docs/build/browser/assets/images/turbo-upi-flow.jpg)

> [accordion] Prerequisites
>
> 1. Integrate with [Razorpay Cordova Standard SDK](https://razorpay.com/docs/payments/payment-gateway/cordova-integration.md).
>
> 2. Import the following frameworks:
>    * Razorpay Cordova Standard SDK
>    * Razorpay Turbo Wrapper Plugin SDK (maven)
>    * Razorpay Turbo Core SDK
>    * Razorpay Turbo UI SDK
>    * Razorpay SecureComponent SDK
>    * Bank SDK
>
> 3. Enable data binding in your `app.gradle`.
>
> ```json Data binding theme={null}
> {
>  "android": {
>      // Containing other settings
>      "buildFeatures": {
>          "dataBinding": true
>      }
>   }
> }
> ```

## Onboarding Flow

Ensure your customers [onboard with Razorpay Turbo UPI](https://razorpay.com/docs/payments/payment-methods/upi/turbo-upi.md#onboarding-flow) to get started.

## Turbo UPI SDK Integration

Follow these steps to integrate with Razorpay Turbo UPI:

1. Use the code given below to initialise the SDK.

```java Initialise theme={null}
RazorpayCheckout.initUpiTurbo("rzp_test_0wFRWIZnH65uny")
```

2. Use the following code to link the newly created UPI account with your app. This function can be called from anywhere in the application, providing multiple entry points for customers to link their UPI account with your app.

```javascript Link New UPI Account theme={null}
RazorpayCheckout.upiTurbo.linkNewUpiAccount("mobileNo", "color", function (upiAccounts) {
    // handle data
}, function(error) {
    // handle error
});
```

> [accordion] Request Parameters
>
> `mobileNumber` *mandatory*
> : `string` Mobile number of the customer.
>
> `color` *optional*
> : `string` Colour in HEX format.

> [accordion] Response Parameters
>
> | Parameters | Description |
> | - | - |
> | `function(upiAccounts)` | This function is triggered if the list is fetched successfully. The `upiAccounts` can be empty to indicate that no accounts have been linked yet. |
> | `function(error)` | This function is triggered in case of an error, and the error object will be received. |

* Handle payment failure responses, displaying important details such as error codes, error descriptions, and metadata. This function is responsible for handling and logging information in the event of a payment error.

```javascript Payment Failure Response Handling theme={null}
var cancelCallback = function(error) {
    /**
     * error contains two values:
     * 1. Error Code
     * 2. Error Description
    **/
  
    // handle failure
};
```

* Handle successful payment responses, displaying key information like order id, payment id, and signature. This code manages and logs details when a payment transaction is successful.

```javascript Payment Success Response Handling theme={null}
var successCallback = function(response) {
    /**
     * response contains three values:
     * 1. Order ID
     * 2. Payment ID
     * 3. Signature
    **/
  
    // handle success
};
```

3. To accept payments, call Standard Checkout’s `submit` method with the following payload:

```javascript Submit Payment Details theme={null}
var rzpOptions = {
    amount: 2000,
    currency: "INR",
    prefill: {
        contact: "1234567890",
        email: "gaurav.kumar@example.com"
    },
    theme: {
        color: "#063970"
    },
    send_sms_hash: true,
    retry: {
        enabled: false,
        max_count: 4
    }
};

RazorpayCheckout.open(rzpOptions, successCallback, cancelCallback);
```

> [accordion] Request Parameter
>
> `payload` *mandatory*
> : `variable` Payload for initiating transaction.

> [accordion] Response Parameters
>
> | Parameters | Description |
> | - | - |
> | `successCallback` | It is triggered upon successful completion of the payment, providing access to a response object. |
> | `cancelCallback` | It is invoked in the event of a failure, providing access to an error object. |

### Non-Transactional Flow

Razorpay provides a single exposed function that allows you to manage linked UPI accounts and access all non-transactional flows seamlessly.

![View the non-transactional flow](https://razorpay.com/docs/build/browser/assets/images/turbo-upi-non-transactional.jpg)

> [accordion] Manage UPI Accounts
>
> The SDK manages the linked `UpiAccounts` on the application by triggering `manageUpiAccounts()`. The sequence of steps is as given below:
>
> * **Fetch balance**: Check the customer's account balance.
> * **Change UPI PIN**: Provide the customer the ability to change their UPI PIN.
> * **Reset UPI PIN**: Let your customers reset the PIN for their account.
> * **Delete the account from the application**: Let your customers delink, that is, remove a selected UPI account from your application.
>
> ```javascript Java theme={null}
> RazorpayCheckout.upiTurbo.manageUpiAccounts("mobileNo", "color", function(error) {
>     // handle error
> });
> ```
>
> > [accordion] Request Parameters
> >
> > `mobileNumber` *mandatory*
> > : `string` Mobile number of the customer.
> >
> > `color` *optional*
> > : `string` Colour in HEX format.
>
> > [accordion] Response Parameter
> >
> > | Parameters | Description |
> > | - | - |
> > | `function(error)` | This function is triggered in case of an error, and the error object will be received. |

### Models Exposed from the SDKs

The SDKs given below provide access to exposed models for seamless integration.

> [accordion] Error
>
> | Error | Description |
> | - | - |
> | `errorCode` | Types of error codes <ul><li>`BAD_REQUEST_ERROR`: Failure from the client's end (SDK).</li><li>`GATEWAY_ERROR`: Failure either from the Secure Component or the Bank.</li><li>`SERVER_ERROR`: Failure at PSP.</li></ul> |
> | `errorDescription` | Brief description of the error. |
> | `errorReason` | Specifies the specific reason for the error. |
> | `errorSource` | Indicates the origin of the error. |
> | `errorStep` | Highlights the stage where the error occurred. |
>
> [Refer to the list of possible error reasons](https://razorpay.com/docs/payments/payment-gateway/cordova-integration/payment-methods/turbo-upi/error-codes.md).

> [accordion] UpiAccount
>
> | Fields | Return Type | Description |
> | - | - | - |
> | `accountNumber` | String | Masked account number. |
> | `ifsc` | String | IFSC of the bank. |
> | `bankLogoUrl` | String | Image URL of the bank logo. |
> | `bankName` | String | Name of the bank. |
> | `bankPlaceholderUrl` | String | Image URL of the bank logo placeholder. |

> [accordion] Response
>
> | Fields | Return Type | Description |
> | - | - | - |
> | `paymentId` | String | Payment id. |
> | `orderId` | String | Order id. |
> | `signature` | String | Signature of the transaction. |
