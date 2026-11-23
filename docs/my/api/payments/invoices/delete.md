> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Delete an Invoice

> Delete an invoice using this endpoint.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to delete invoices. You can only delete an invoice that is in the `draft` state.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X DELETE https://api.razorpay.com/v1/invoices/inv_DAuFuwWYU3R9tg \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String invoiceId = "inv_DAuFuwWYU3R9tg";

List<Invoice> invoice = razorpay.invoices.delete(InvoiceId);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.invoice.delete(invoiceId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Invoice.Delete("<invoiceId>", nil, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay::Invoice.delete(invoiceId)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->invoice->fetch($invoiceId)->delete();
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.invoices.delete(invoiceId)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]
");

string invoiceId = "inv_DAweOiQ7amIUVd";

List<Invoice> invoice = client.Invoice.Fetch(invoiceId).Delete();
```

```bash CLI theme={null}
razorpay invoices delete inv_ABC123
```

```json Success theme={null}
[]
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "Operation not allowed for Invoice in cancelled status.",
    "source": "business",
    "step": "payment_initiation",
    "reason": "input_validation_failed",
    "metadata": {}
  }
}
```

## Path Parameters

**id** `string` *required*

The unique identifier of the invoice.

## Errors

> [accordion] Operation not allowed for Invoice in \{issued|paid|partially\_paid|cancelled|expired} status.
>
> **Code:** `400`
>
> Deletion is only allowed on invoices in the `draft` state.
>
> **Solution:** You can only delete invoices that have not yet been issued. Once issued, cancel the invoice using `POST /v1/invoices/:id/cancel` instead.

> [accordion] The api \{key/secret} provided is invalid.
>
> **Code:** `4xx`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after.

> [accordion] The id provided does not exist.
>
> **Code:** `400`
>
> The invoice id passed in the URL does not exist or does not belong to the requesting merchant.
>
> **Solution:** Use a valid invoice id returned from `POST /v1/invoices`. Confirm by fetching the invoice before retrying.
