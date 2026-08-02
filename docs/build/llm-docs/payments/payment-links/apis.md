# Payment Links APIs

Payment Links help you to receive payments from customers by sending them links via email and SMS. Use our APIs to create Payment Links. You can enter details such as amount, link expiry time, and more and send the link to the customer via email or SMS. The customer can select their desired payment method and complete the payment. Once the customer makes the payment, you will receive the amount in your bank account according to your settlement cycle.

There are two types of Payment Links:

- **Standard Payment Links**: Customers can make payments through netbanking, cards, wallets, UPI and bank transfer payment methods using Standard Payment Links.

- **UPI Payment Links**: Customers can select the UPI app of your choice to make payments using UPI Payment Links.

## Payment Link APIs

You can create, update, cancel, fetch, and resend payment links using APIs. Check the [API Reference Guide](https://razorpay.com/docs/build/llm-docs/api/payments/payment-links.md) for endpoints, sample codes and parameter descriptions.

### Using Callback URL Parameter

Upon successful payment, customers can be directed to a designated URL through the `callback_url` and `callback_method` parameters. For example, you can redirect customers to `https://example-callback-url.com/`.

Parameter | Description
---
`razorpay_payment_id` | Payment ID of the successful payment.
---
`razorpay_payment_link_id` | Payment Link ID generated at the time of link creation.
---
`razorpay_payment_link_reference_id` | Internal order ID set by you for business reference using the `reference_id` parameter at the time of link creation. No value is returned if `reference_id` parameter was not used.
---
`razorpay_payment_link_status` | Current status of the link.
---
`razorpay_signature` | Signature for server-side validation to be calculated as HMAC hex digest using SHA256 algorithm. This is described below with a sample code.

The query parameters are added to the URL as shown:

```json: Query Parameters
https://example-callback-url.com/?razorpay_payment_id=pay_Fc8mUeDrEKf08Y&razorpay_payment_link_id=plink_Fc8lXILABzQL7M&
razorpay_payment_link_reference_id=TSsd1989&
razorpay_payment_link_status=partially_paid&razorpay_signature=b0ea302006
```

### Verify Signature

You can verify the `razorpay_signature` parameter to validate that it is authentic and sent from Razorpay servers.

The `razorpay_payment_link_id​` attribute should be stored in your system against an order, right after it is returned in the create [Payment Link](https://razorpay.com/docs/build/llm-docs/api/payments/payment-links.md) response. This is displayed as just `id` (for example, `"id": "plink_FKeEiabyAAiSVQ"`) in the response.

- The `razorpay_signature` should be validated by your server. In order to verify the signature, you need to create a signature using 
  - `razorpay_payment_link_id` 
  - `razorpay_payment_link_reference_id` 
  - `razorpay_payment_link_status`
  - `razorpay_payment_id​` 
  as payload and your `key_secret​` (your API secret) as secret.

```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String secret = "EnLs21M47BllR3X8PSFtjtbd";

JSONObject options = new JSONObject();
options.put("payment_link_reference_id", "TSsd1989");
options.put("razorpay_payment_id", "pay_IH3d0ara9bSsjQ");
options.put("payment_link_status", "paid");
options.put("payment_link_id", "plink_IH3cNucfVEgV68");
options.put("razorpay_signature", "07ae18789e35093e51d0a491eb9922646f3f82773547e5b0f67ee3f2d3bf7d5b");

boolean status =  Utils.verifyPaymentLink(options, secret);

```python: Python
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.utility.verify_payment_link_signature({
   'payment_link_id': payment_link_id,
   'payment_link_reference_id': payment_link_reference_id,
   'payment_link_status':payment_link_status,
   'razorpay_payment_id': razorpay_payment_id,
   'razorpay_signature': razorpay_signature
   })

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

payment_response = {
  payment_link_id: 'plink_IH3cNucfVEgV68',
  payment_link_reference_id: 'TSsd1989',
  payment_link_status: 'paid',
  razorpay_payment_id: 'pay_IH3d0ara9bSsjQ',
  razorpay_signature: '07ae18789e35093e51d0a491eb9922646f3f82773547e5b0f67ee3f2d3bf7d5b'
}
Razorpay::Utility.verify_payment_link_signature(payment_response)

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

params := map[string]interface{} {
	"payment_link_id": "plink_IH3cNucfVEgV68",
	"razorpay_payment_id": "pay_IH3d0ara9bSsjQ",
	"payment_link_reference_id": "TSsd1989",
	"payment_link_status": "paid",
}
signature := "07ae18789e35093e51d0a491eb9922646f3f82773547e5b0f67ee3f2d3bf7d5b";
secret := "EnLs21M47BllR3X8PSFtjtbd";
utils.VerifyPaymentLinkSignature(params, signature, secret)

```php: PHP
$api = new Api($key_id, $secret);

$api->utility->verifyPaymentSignature(array('razorpay_payment_link_id' => $razorpayPaymentlinkId, 'razorpay_payment_id' => $razorpayPaymentId, 'razorpay_payment_link_reference_id' => $razorpayPaymentLinkReferenceId, 'razorpay_payment_link_status' => $razorpayPaymentLinkStatus, 'razorpay_signature' => $razorpayPaymentLinkSignature));

```javascript: Node.js 
import { validatePaymentVerification } from 'razorpay/dist/utils/razorpay-utils';
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

validatePaymentVerification({
  "payment_link_id": PaymentlinkId,
  "payment_id": PaymentId,
  "payment_link_reference_id": PaymentLinkReferenceId,
  "payment_link_status": PaymentLinkStatus,
}, signature , secret);

```csharp: .NET
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary options = new Dictionary();
options.Add("payment_link_reference_id", "TSsd1989");
options.Add("razorpay_payment_id", "pay_IH3d0ara9bSsjQ");
options.Add("payment_link_status", "paid");
options.Add("payment_link_id", "plink_IH3cNucfVEgV68");
options.Add("razorpay_signature", "07ae18789e35093e51d0a491eb9922646f3f82773547e5b0f67ee3f2d3bf7d5b");

Utils.verifyPaymentLinkSignature(options);

```

After validating the signature, you should fetch the order in your system corresponding to the `razorpay_payment_link_id`​ and mark this order as successful.

### Related Information

- [Payment Links APIs](https://razorpay.com/docs/build/llm-docs/api/payments/payment-links.md)
- [Subscribe to Webhooks](https://razorpay.com/docs/build/llm-docs/payments/payment-links/subscribe-to-webhooks.md)
