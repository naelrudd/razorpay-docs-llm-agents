# Send or Resend Notifications

**POST** `/v1/payment_links/:id/notify_by/:medium`

Use this endpoint to send or resend notifications to your customers via email and SMS.

### Request

```curl: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/payment_links/plink_Et2G7ymGcTTuM5/notify_by/sms \

```php: PHP
$api = new Api($key_id, $secret);

$api->paymentLink->fetch($paymentLinkId)->notifyBy($medium));

```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.paymentLink.notifyBy(paymentLinkId, medium)

```python: Python
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment_link.notifyBy(paymentLinkId, medium)

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.PaymentLink.NotifyBy("", "", nil, nil)

```ruby: Ruby
require "razorpay"
Razorpay.setup('key_id', 'key_secret')

paymentLinkId = "plink_ExjpAUN3gVHrPJ"

medium = "email"

Razorpay::PaymentLink.notify_by(paymentLinkId, medium)

```java: Java
import org.json.JSONObject;
import com.razorpay.Payment;
import com.razorpay.RazorpayClient;
import com.razorpay.RazorpayException;

RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
String paymentLinkId = "plink_FMbhpT6nqDjDei";

String medium = "email";

PaymentLink paymentlink = razorpay.paymentLink.notifyBy(paymentLinkId,medium);

```csharp: .NET
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string paymentLinkId = "plink_Z6t7VFTb9xHeOs";

string  = "email";

PaymentLink paymentlink = client.PaymentLink.Fetch(paymentLinkId).NotifyBy(medium);

```bash: CLI
# Via SMS
razorpay payment-links notify plink_ABC123 --medium sms

# Via email
razorpay payment-links notify plink_ABC123 --medium email
```

### Response

```json: Success
{
    "success": true
}
```json: Failure
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "invalid input [id] = [link_QX7wiVUHdcOOoW]",
    "metadata": [],
    "reason": null,
    "source": null,
    "step": null
  }
}
```

### Parameters

`id` _mandatory_
: `string` Unique identifier of the Payment Link that should be resent.

`medium` _mandatory_
: `string` Medium through which the Payment Link must be resent. Possible values:
    - `sms`
    - `email`

### Parameters

`success` 
: `boolean` Indicates whether the notification was sent successfully. Possible value is `true`, which means the notification was sent successfully.

### Errors

not a valid notification medium
* code: 400
* description: Occurs when you try to resend a Payment Link to customers and medium of notification is not valid.
* solution: Ensure that you use the correct medium to resend a payment link.

The id provided does not exist.
* code: 400
* description: The Payment Link id passed in the URL does not exist or does not belong to the requesting merchant.
* solution: Use a valid Payment Link id returned from `POST /v1/payment_links`. Confirm by fetching the link before retrying.

Length of id should be exactly 14.
* code: 400
* description: The Payment Link id in the URL is not 14 characters long (excluding the `plink_` prefix). Razorpay-issued ids are always exactly 14 characters.
* solution: Use the Payment Link id exactly as it was returned in the create response (for example, `plink_HZbgjy1cnaCFqM`).

Request rate limit exceeded. Please try again later.
* code: 429
* description: You have exceeded the per-link / per-medium notification rate limit. Razorpay caps how often the same notification can be re-sent for a given Payment Link.
* solution: Wait a short while before retrying. If you need a higher sustained rate, contact [Razorpay support](https://razorpay.com/support/).
