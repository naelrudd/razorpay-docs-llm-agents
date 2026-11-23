> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Send Notifications

> Send notifications to your customers via SMS and Email using this endpoint.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to send notifications with the short URL to the customer via email or SMS.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/invoices/inv_DAuFuwWYU3R9tg/notify_by/sms \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String invoiceId = "inv_DAuFuwWYU3R9tg";

String medium = "sms";

Invoice invoice = razorpay.invoices.notifyBy(invoiceId,medium);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.invoice.notify_by(invoiceId,medium)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

invoiceId = "inv_DAuFuwWYU3R9tg"

medium = "email"

Razorpay::Invoice.notifyBy(invoiceId,medium)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Invoice.Notify("<invoiceId>", "<medium>", nil, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->invoice->fetch($invoiceId)->notify($medium);
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.invoices.notifyBy(invoiceId,medium)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]
");

string invoiceId = "inv_DAweOiQ7amIUVd";

string medium = "sms";

Invoice invoice = client.Invoice.Fetch(invoiceId).NotifyBy(medium);
```

```bash CLI theme={null}
# Via SMS
razorpay invoices notify inv_ABC123 --medium sms

# Via email
razorpay invoices notify inv_ABC123 --medium email
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
    "description": "The api key provided is invalid",
    "source": "NA",
    "step": "NA",
    "reason": "NA",
    "metadata": {}
  }
}
```

## Path Parameters

**id** `string` *required*

The unique identifier of the invoice whose link is to be sent by SMS or email.

**medium** `string` *required*

Possible values:

* `sms`
* `email`

## Response Parameters

**success** `boolean`

Indicates whether the notifications were sent successfully. Possible values:

* `true`: The notifications were successfully via SMS, email or both.
* `false`: The notifications were not sent.

## Errors

> [accordion] The API `\<key/secret\>
> ` provided is invalid.
>
> **Code:** `4xx`
>
> There is a mismatch between the API credentials passed in the API call and those generated on the Dashboard.
>
> **Solution:**
>
> * Ensure that the API Keys are active and entered correctly.
> * There should be no whitespaces before or after the keys.

> [accordion] The id provided does not exist.
>
> **Code:** `400`
>
> The invoice id entered is either invalid or does not belong to the requester account.
>
> **Solution:** Enter a valid invoice id.

> [accordion] \{medium} is not a valid communication medium.
>
> **Code:** `400`
>
> The `medium` path parameter is not `sms` or `email`. The error echoes the actual invalid medium value.
>
> **Solution:** Use either `sms` or `email` as the `medium` path parameter.

> [accordion] Email can not be sent since email address has not been provided.
>
> **Code:** `400`
>
> The notification request used `medium=email` but the invoice does not have a customer email address on file.
>
> **Solution:** Update the invoice to include `customer.email`, or send the notification via `medium=sms` if a contact number is available.

> [accordion] SMS can not be sent since contact number has not been provided.
>
> **Code:** `400`
>
> The notification request used `medium=sms` but the invoice does not have a customer contact number on file.
>
> **Solution:** Update the invoice to include `customer.contact`, or send the notification via `medium=email` if an email address is available.

> [accordion] Operation not allowed for Invoice in \{draft|paid|expired|cancelled} status.
>
> **Code:** `400`
>
> Notifications can only be sent for invoices in the `issued` or `partially_paid` state. The error message echoes the invoice's actual current status. For example, `Operation not allowed for Invoice in cancelled status.`
>
> **Solution:** Issue the invoice first (or wait for it to move to `partially_paid`) before sending notifications.
