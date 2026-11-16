> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Migrate from BharatQR APIs to QR Codes APIs

> Migrate from our BharatQR APIs to QR Code APIs. Compare features, API Parameters and Webhook events.

Available in
🇮🇳 India

Given below is the high-level migration process.

1. Explore the QR Codes APIs using the Postman collection.
2. Understand the QR Code API Request and Response structure and the webhook payloads.
3. Integrate with QR Code APIs. You can refer to the provided sample codes.

> [accordion] Feature Comparison
>
> The table below lists the features availability on BharatQR API and QR Codes API:
>
> | Feature | BharatQR API | QR Codes API |
> | - | - | - |
> | Dynamic BharatQR | x | ✓ |
> | Static BharatQR | ✓ | ✓ |
> | Dynamic UPI QR | ✓ | ✓ |
> | Static UPI QR | x | ✓ |
> | Get count of payments collected on QR Code | x | ✓ |
> | Dashboard access | x | ✓ |
> | Your business branding on QR image | x | ✓ |
> | Dedicated VPA for your business | x | ✓ |

> [accordion] Comparison of API Parameters
>
> Compare BharatQR and QR Code API parameters.
>
> > [tab] Create QR Codes
> >
> > | BharatQR Parameter | QR Codes Parameter | Description |
> > | - | - | - |
> > | receivers.types | type | The type of QR Code. Possible values: <ul><li>`upi_qr`: Create a QR Code that accepts only UPI payments.</li><li>`bharat_qr`: Create a QR Code that accepts UPI and card payments.</li></ul>  For `receivers.types`, the only possible value was `qr_code`. |
> > | description | description | A brief description of the QR Code. |
> > | customer\_id | customer\_id | Unique identifier of the customer the QR Code is linked with. |
> > | close\_by | close\_by | UNIX timestamp at which the QR Code is scheduled to be automatically closed. The time must be at least 15 minutes after the current time. |
> > | notes | notes | Key-value pair that can be used to store additional information about the QR Code. Maximum 15 key-value pairs, 256 characters (maximum) each. |
> > | amount\_expected | NA | The maximum amount you expect to receive in this virtual account. |
> > | NA | name | Label entered to identify the QR Code. For example, `Store Front Display`. |
> > | NA | usage | Indicates if the QR Code should be allowed to accept single payment or multiple payments. Possible values: <ul><li>`single_use`: QR Code will accept only one payment and then close automatically.</li><li>`multiple_use` (default): QR Code will accept multiple payments.</li></ul> |
> > | NA | fixed\_amount | Indicates if the QR should accept payments of specific amounts or any amount. Possible values: <ul><li>`true`: QR Code accepts only a specific amount. </li><li>`false` (default): QR Code will accept any amount.</li></ul> |
> > | NA | payment\_amount | This parameter is mandatory if fixed\_amount parameter is in use. The amount allowed for a transaction. If this is specified, then any transaction of amount less than or more than this value will not be allowed. For example, if this amount is set as `500000`, the customer cannot pay an amount less than or more than ₹5000. |
> >
> > **API Reference Links**
> >
> > * BharatQR: [Create a virtual account](https://razorpay.com/docs/payments/payment-methods/bharatqr/api.md#create)
> > * QR Code: [Create a QR Code](https://razorpay.com/docs/api/qr-codes/create.md)
>
> > [tab] Close QR Codes
> >
> > For this action, only one path parameter needs to be passed, the QR Code id.
> >
> > | BharatQR Parameter | QR Codes Parameter | Description |
> > | - | - | - |
> > | Virtual Account ID | QR Code ID | The unique identifier of the virtual account/QR Code that is to be closed. |
> >
> > **API Reference Links**
> >
> > * BharatQR: [Close a virtual account](https://razorpay.com/docs/payments/payment-methods/bharatqr/api.md#close)
> > * QR Code: [Close a QR Code](https://razorpay.com/docs/api/qr-codes/close.md)
>
> > [tab] Fetch All QR Codes
> >
> > The fetch query parameters remain the same across the APIs as given below:
> >
> > | BharatQR Parameter | QR Codes Parameter | Description |
> > | - | - | - |
> > | from | from | Timestamp, in seconds, from when QR Codes are to be fetched. |
> > | to | to | Timestamp, in seconds, till when QR Codes are to be fetched. |
> > | count | count | Number of QR Codes to be fetched. The default value is 10 and the maximum value is 100. This can be used for pagination, in combination with skip. |
> > | skip | skip | Number of records to be skipped while fetching the QR Codes. This can be used for pagination, in combination with count. |
> >
> > **API Reference Links**
> >
> > * BharatQR: [Fetch all virtual accounts](https://razorpay.com/docs/payments/payment-methods/bharatqr/api.md#fetch-all-payments)
> > * QR Code: [Fetch all QR Codes](https://razorpay.com/docs/api/qr-codes/fetch-all.md)
>
> > [tab] Fetch a QR Code
> >
> > For this action, only one path parameter needs to be passed, the QR Code id.
> >
> > | BharatQR Parameter | QR Codes Parameter | Description |
> > | - | - | - |
> > | Virtual Account ID | QR Code ID | The unique identifier of the virtual account/QR Code whose details are to be fetched. |
> >
> > **API Reference Links**
> >
> > * BharatQR: [Fetch a virtual account](https://razorpay.com/docs/payments/payment-methods/bharatqr/api.md#fetch-a-payment)
> > * QR Code: [Fetch a QR Code](https://razorpay.com/docs/api/qr-codes/fetch-with-id.md)
>
> > [tab] Fetch Payments made to a QR Code
> >
> > For this action, only one path parameter needs to be passed, the QR Code identifier.
> >
> > | BharatQR Parameter | QR Codes Parameter | Description |
> > | - | - | - |
> > | Virtual Account ID | QR Code ID | The unique identifier of the virtual account/QR Code whose payment details are to be fetched. |
> >
> > **API Reference Links**
> >
> > * BharatQR: [Fetch payments by id](https://razorpay.com/docs/payments/payment-methods/bharatqr/api.md#fetch-a-payment)
> > * QR Code: [Fetch payments made to a QR Code](https://razorpay.com/docs/api/qr-codes/fetch-payments.md)

> [accordion] Comparison of Webhook Events
>
> Given below is a comparison of BharatQR and QR Codes webhook events:
>
> | Webhook Events | BharatQR | QR Codes |
> | - | - | - |
> | QR Code created | [virtual\_account.created](https://razorpay.com/docs/webhooks/smart-collect.md#virtual-account-created) | [qr\_code.created](https://razorpay.com/docs/webhooks/qr-codes.md#qr-code-created) |
> | QR Code credited | [virtual\_account.credited](https://razorpay.com/docs/payments/payment-methods/bharatqr/notification.md#webhooks) | [qr\_code.credited](https://razorpay.com/docs/webhooks/qr-codes.md#qr-code-credited) |
> | QR Code closed | [virtual\_account.closed](https://razorpay.com/docs/webhooks/smart-collect.md#virtual-account-closed) | [qr\_code.closed](https://razorpay.com/docs/webhooks/qr-codes.md#qr-code-closed) |
