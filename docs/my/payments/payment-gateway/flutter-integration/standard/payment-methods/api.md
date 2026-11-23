> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# API Classes and Methods

> API classes and methods available for the Flutter plugin.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Documented below is the API package for the plugin.

## Razorpay Curlec Class

### Method

`open(map<String, dynamic> options)`
: Opens the checkout.

`on(String eventName, Function listener)`
: Registers event listeners for payment events.<ul><li>`eventName`: The name of the event.</li><li>`listener`: The function to be called. The listener should accept a single argument of the following type: <ul><li>[PaymentSuccessResponse](#paymentsuccessresponse) for EVENT\_PAYMENT\_SUCCESS.</li><li>[PaymentFailureResponse](#paymentfailureresponse) for EVENT\_PAYMENT\_FAILURE.</li><li>[ExternalWalletResponse](#externalwalletresponse) for EVENT\_EXTERNAL\_WALLET. </li></ul> </li></ul>

`clear()`
: Clears all listeners.

> [!NOTE]
>
> **Handy Tips**
>
> The `options` map has `key` as a required property in the open checkout method. All other properties are optional. Know about all the [options available on checkout form](https://razorpay.com/docs/my/payments/payment-gateway/flutter-integration/standard/integration-steps.md#5-add-checkout-options).

### Event Names

The event names have been exposed as `strings` by the `Razorpay` class.

| Event Name | Description |
| - | - |
| EVENT\_PAYMENT\_SUCCESS | The payment was successful. |
| EVENT\_PAYMENT\_ERROR | The payment was not successful. |
| EVENT\_EXTERNAL\_WALLET | An external wallet was selected. |

#### PaymentSuccessResponse

| Field Name | Data Type | Description |
| - | - | - |
| `paymentId` | `string` | The ID for the payment. |
| `orderId` | `string` | The order ID if the payment was for an order, otherwise `null`. |
| `signature` | `string` | The signature to be used for payment verification. Only valid for orders, otherwise `null`. |

#### PaymentFailureResponse

| Field Name | Data Type | Description |
| - | - | - |
| `code` | `integer` | The [error code](#error-codes). |
| `message` | `string` | The [error message](#error-codes). |

#### ExternalWalletResponse

| Field Name | Data Type | Description |
| - | - | - |
| `walletName` | `string` | The name of the external wallet selected. |

## Error Codes

The error codes are exposed as integers by the `Razorpay` class. The error code is available as the code field of the `PaymentFailureResponse` instance passed to the callback.

| Error Code | Description |
| - | - |
| NETWORK\_ERROR | There was a network error. For example, loss of internet connectivity. |
| INVALID\_OPTIONS | An issue with options passed in `Razorpay.open`. |
| PAYMENT\_CANCELLED | User cancelled the payment. |
| TLS\_ERROR | Device does not support TLS v1.1 or TLS v1.2. |
| UNKNOWN\_ERROR | An unknown error occurred. |
