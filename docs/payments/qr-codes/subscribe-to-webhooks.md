> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Subscribe to Webhooks

> Subscribe to various webhook events related to QR Codes to receive instant notifications.

Available in
🇮🇳 India

Follow these steps to subscribe to webhook events:

1. Log in to the Dashboard.
2. Navigate to **Account & Settings** → **Webhooks** to subscribe to any of the events mentioned in the following section.

## Webhook Events and Descriptions

| Webhook Events | Description |
| - | - |
| `qr_code.created` | Triggered when a QR Code is created. |
| `qr_code.credited` | Triggered when a payment is made using a QR Code. |
| `qr_code.closed` | Triggered when a QR Code is closed. |

### Signature Validation

If you need to validate QR Code webhook payloads, please use the following Node.js code:

```javascript Node.js theme={null}
const {validateWebhookSignature} = require('razorpay/dist/utils/razorpay-utils')

webhookBodyNew = JSON.stringify(webhookBody).replace(/\//g, "\\/") 

validateWebhookSignature(webhookBodyNew, webhookSignature, webhookSecret)
```

Know more about [Webhooks](https://razorpay.com/docs/webhooks) and check the [sample payloads](https://razorpay.com/docs/webhooks/qr-codes.md).

### Related Information

* [QR Code States](https://razorpay.com/docs/payments/qr-codes/states.md)
* [QR Code APIs](https://razorpay.com/docs/payments/qr-codes/apis.md)
