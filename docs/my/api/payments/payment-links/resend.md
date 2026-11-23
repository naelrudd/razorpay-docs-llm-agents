> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Send or Resend Notifications

> Send or resend Payment Link notifications to your customers by email using this endpoint.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to send or resend Payment Link notifications to your customers by email.

> [!WARNING]
>
> **Watch Out!**
>
> * SMS isn't available for Payment Links in Malaysia. Malaysian Communications and Multimedia Commission (MCMC) rules let telcos block SMS messages that contain links. The customer receives the SMS with the link replaced by asterisks (`*`), so they can't open it. Use `email` as the `medium`.
> * A resend uses only the notification channels enabled when you [created the Payment Link](https://razorpay.com/docs/my/api/payments/payment-links/create-standard.md), and you can't change them later. The link is sent by email only if `notify.email` was `true` at creation. If it was `false`, the API returns `"success": true` but no email is sent. Share the Payment Link URL with the customer yourself, or create a new Payment Link with `notify.email` set to `true`.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/payment_links/plink_Et2G7ymGcTTuM5/notify_by/email
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->paymentLink->fetch($paymentLinkId)->notifyBy($medium);
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.paymentLink.notifyBy(paymentLinkId, medium)
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment_link.notifyBy(paymentLinkId, medium)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.PaymentLink.NotifyBy("<paymentLinkId>", "<medium>", nil, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('key_id', 'key_secret')

paymentLinkId = "plink_ExjpAUN3gVHrPJ"

medium = "email"

Razorpay::PaymentLink.notify_by(paymentLinkId, medium)
```

```java Java theme={null}
import org.json.JSONObject;
import com.razorpay.Payment;
import com.razorpay.RazorpayClient;
import com.razorpay.RazorpayException;

RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
String paymentLinkId = "plink_FMbhpT6nqDjDei";

String medium = "email";

PaymentLink paymentlink = razorpay.paymentLink.notifyBy(paymentLinkId,medium);
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string paymentLinkId = "plink_Z6t7VFTb9xHeOs";

string medium = "email";

PaymentLink paymentlink = client.PaymentLink.Fetch(paymentLinkId).NotifyBy(medium);
```

```bash CLI theme={null}
razorpay payment-links notify plink_ABC123 --medium email
```

```json Success theme={null}
{
    "success": true
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "invalid input [id] = [plink_QX7wiVUHdcOOoW]",
    "metadata": [],
    "reason": null,
    "source": null,
    "step": null
  }
}
```

## Path Parameters

**id** `string` *required*

Unique identifier of the Payment Link that should be resent.

**medium** `string` *required*

Medium through which the Payment Link must be resent. Possible value is `email`.

SMS isn't available for Payment Links in Malaysia, so don't pass `sms`.

## Response Parameters

**success** `boolean`

Indicates whether the notification was sent successfully. Possible value is `true`, which means the notification was sent successfully.

## Errors

> [accordion] not a valid notification medium
>
> **Code:** `400`
>
> Occurs when you try to resend a Payment Link to customers and medium of notification is not valid.
>
> **Solution:** Ensure that you use the correct medium to resend a payment link.

> [accordion] The id provided does not exist.
>
> **Code:** `400`
>
> The Payment Link id passed in the URL does not exist or does not belong to the requesting merchant.
>
> **Solution:** Use a valid Payment Link id returned from `POST /v1/payment_links`. Confirm by fetching the link before retrying.

> [accordion] Length of id should be exactly 14.
>
> **Code:** `400`
>
> The Payment Link id in the URL is not 14 characters long (excluding the `plink_` prefix). Razorpay Curlec-issued ids are always exactly 14 characters.
>
> **Solution:** Use the Payment Link id exactly as it was returned in the create response (for example, `plink_HZbgjy1cnaCFqM`).

> [accordion] Request rate limit exceeded. Please try again later.
>
> **Code:** `429`
>
> You have exceeded the per-link / per-medium notification rate limit. Razorpay Curlec caps how often the same notification can be re-sent for a given Payment Link.
>
> **Solution:** Wait a short while before retrying. If you need a higher sustained rate, contact [Razorpay Curlec support](https://curlec.com/support/).
