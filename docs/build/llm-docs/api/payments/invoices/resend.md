# Send Notifications

**POST** `/v1/invoices/:id/notify_by/:medium`

Use this endpoint to send notifications with the short URL to the customer via email or SMS.

### Request

```cURL: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/invoices/inv_DAuFuwWYU3R9tg/notify_by/sms \

```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String invoiceId = "inv_DAuFuwWYU3R9tg";

String medium = "sms";

Invoice invoice = razorpay.invoices.notifyBy(invoiceId,medium);

```python: Python
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.invoice.notify_by(invoiceId,medium)

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

invoiceId = "inv_DAuFuwWYU3R9tg"

medium = "email"

Razorpay::Invoice.notifyBy(invoiceId,medium)

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Invoice.Notify("", "", nil, nil)

```php: PHP
$api = new Api($key_id, $secret);

$api->invoice->fetch($invoiceId)->notify($medium);

```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.invoices.notifyBy(invoiceId,medium)

```csharp: .NET
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]
");

string invoiceId = "inv_DAweOiQ7amIUVd";

string medium = "sms";

Invoice invoice = client.Invoice.Fetch(invoiceId).NotifyBy(medium);
```bash: CLI
# Via SMS
razorpay invoices notify inv_ABC123 --medium sms

# Via email
razorpay invoices notify inv_ABC123 --medium email
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
    "description": "The api key provided is invalid",
    "source": "NA",
    "step": "NA",
    "reason": "NA",
    "metadata": {}
  }
}
```

### Parameters

`id` _mandatory_
: `string` The unique identifier of the invoice whose link is to be sent by SMS or email.

`medium` _mandatory_
: `string` Possible values:
    - `sms`
    - `email`

### Parameters

`success`
: `boolean` Indicates whether the notifications were sent successfully. Possible values:
    - `true`: The notifications were successfully via SMS, email or both.
    - `false`: The notifications were not sent.

### Errors

The API `` provided is invalid.
* code: 4xx
* description: There is a mismatch between the API credentials passed in the API call and those generated on the Dashboard.
* solution:  - Ensure that the API Keys are active and entered correctly.
- There should be no whitespaces before or after the keys.

 
The id provided does not exist.
* code: 400
* description: The invoice id entered is either invalid or does not belong to the requester account.
* solution: Enter a valid invoice id.

\{medium\} is not a valid communication medium.
* code: 400
* description: The `medium` path parameter is not `sms` or `email`. The error echoes the actual invalid medium value.
* solution: Use either `sms` or `email` as the `medium` path parameter.

Email can not be sent since email address has not been provided.
* code: 400
* description: The notification request used `medium=email` but the invoice does not have a customer email address on file.
* solution: Update the invoice to include `customer.email`, or send the notification via `medium=sms` if a contact number is available.

SMS can not be sent since contact number has not been provided.
* code: 400
* description: The notification request used `medium=sms` but the invoice does not have a customer contact number on file.
* solution: Update the invoice to include `customer.contact`, or send the notification via `medium=email` if an email address is available.

Operation not allowed for Invoice in \{draft|paid|expired|cancelled\} status.
* code: 400
* description: Notifications can only be sent for invoices in the `issued` or `partially_paid` state. The error message echoes the invoice's actual current status. For example, `Operation not allowed for Invoice in cancelled status.`
* solution: Issue the invoice first (or wait for it to move to `partially_paid`) before sending notifications.
