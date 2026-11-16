> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch QR Codes for a Payment ID

> Fetch the details of a QR Codes using a Payment Id.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve the details of a QR Code by using a Payment Id.

```bash Curl theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-X GET https://api.razorpay.com/v1/payments/qr_codes?payment_id=pay_Di5iqCqA1WEHq6 \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject params = new JSONObject();
params.put("payment_id","pay_Di5iqCqA1WEHq6");

List<QrCode> qrcodes = razorpay.qrCode.fetchAll(params);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->qrCode->all(["payment_id" => $paymentId])
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.qrCode.all({"payment_id":paymentId})
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

 client.qrcode.all({"payment_id":paymentId})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

para_attr := map[string]interface{}{
	"payment_id" : "pay_HMtDKn3TnF4D8x",
}

body, err := client.QrCode.All(para_attr, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {"payment_id":paymentId}

Razorpay::QrCode.all(para_attr)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> paramRequest = new Dictionary<string, object>();
params.Add("payment_id","pay_Z6t7VFTb9xHeOs");

List<QrCode> paymentlink = client.QrCode.All(paramRequest);
```

```bash CLI theme={null}
razorpay qr-codes list --payment-id pay_ABC123
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 1,
  "items": [
    {
      "id": "qr_HMsqRoeVwKbwAF",
      "entity": "qr_code",
      "created_at": 1623661499,
      "name": "Fresh Groceries",
      "usage": "multiple_use",
      "type": "upi_qr",
      "image_url": "https://rzp.io/i/eI9XD54Q",
      "payment_amount": null,
      "status": "active",
      "description": "Buy fresh groceries",
      "fixed_amount": false,
      "payments_amount_received": 1000,
      "payments_count_received": 1,
      "notes": [],
      "customer_id": "cust_HKsR5se84c5LTO",
      "close_by": 1624472999,
      "close_reason": null
    }
  ]
}
```

```json Failure theme={null}
{
    "error": {
        "code": "BAD_REQUEST_ERROR",
        "description": "The api secret provided is invalid",
        "source": "NA",
        "step": "NA",
        "reason": "NA",
        "metadata": {}
    }
}
```

## Query Parameters

**id** `string` *required*

The unique identifier of the payment.

## Response Parameters

**id** `string`

The unique identifier of the QR Code. For example, `qr_HMsVL8HOpbMcjU`.

**entity** `string`

Indicates the type of entity. Here, it is `qr_code`.

**created\_at** `integer`

Unix timestamp at which the QR Code is created.

**name** `string`

Label entered to identify the QR Code. For example, `Store Front Display`.

**usage** `string`

Indicates if the QR Code should be allowed to accept single payment or multiple payments. Possible values:

* `single_use`: QR Code will accept only one payment and then close automatically.
* `multiple_use` (default): QR Code will accept multiple payments.

**type** `string`

The type of the QR Code. Possible value is `upi_qr`, which creates a QR Code that accepts only UPI payments. \\

> [!NOTE]
>
> **Feature Request**
>
> This is an on-demand feature. Please raise a request with our [Support team](https://razorpay.com/support/#request) to get this feature activated on your account.

**image\_url** `string`

The URL of the QR Code. For example, `http://rzp.io/l6MS`. Click the link to download the code.

**payment\_amount** `integer`

The amount allowed for a transaction. If this is specified, then any transaction of an amount less than or more than this value is not allowed. For example, if this amount is set as `500000`, the customer cannot pay an amount less than or more than ₹5000.

**status** `string`

Indicates the status of the QR Code. Possible values:

* `active`: Indicates that the QR Code has been created and is ready to accept payments.
* `closed`: Indicates that the QR Code has been closed.

**description** `string`

A brief description about the QR Code.

**fixed\_amount** `boolean`

Indicates if the QR Code should accept payments of specific amounts or any amount. Possible values:

* `true`: QR Code accepts only a specific amount.
* `false` (default): QR code accepts any amount.

> [!WARNING]
>
> **Watch Out!**
>
> When setting the `usage` to `single_use`, ensure that `fixed_amount` is `true` to generate the QR Code successfully.

**payments\_amount\_received** `integer`

The total amount received on the QR Code. Only captured payments are considered.

**payments\_count\_received** `integer`

The total number of payments received on the QR Code. All captured payments are considered.

**notes** `object`

Key-value pair that can be used to store additional information about the QR Code. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

**customer\_id** `string`

The unique identifier of the customer the QR Code is linked with. Know more about the [Customers API](https://razorpay.com/docs/api/customers.md).

**close\_by** `integer`

Unix timestamp at which the QR Code is scheduled to be automatically closed. The time must be at least 15 minutes after the current time. The date range can be set to `2147483647` in Unix timestamp format (equivalent to Tuesday, January 19, 2038 8:44:07 AM GMT+05:30).

> [!NOTE]
>
> **Handy Tips**
>
> * Any request beyond 2147483647 Unix timestamp will fail.

> [!WARNING]
>
> **Watch Out!**
>
> * This parameter is only available for QR codes with `usage` set as `single_use`. You will not be able to use this parameter for `multiple_use` QR codes as it will generate an error.
> * For `single_use` QR codes, the `close_by` date can be set for a maximum of 45 days. If no `close_by` date is specified, the QR code will automatically become inactive after 45 days. Conversely, `multiple_use` QR codes do not have an expiration date.

**closed\_at** `integer`

Unix timestamp at which the QR Code is automatically closed.

**close\_reason** `string`

The reason for the closure of the QR Code. Possible values:

* `on_demand`: When you close the QR Code using the APIs or the Dashboard.
* `paid`: If the QR Code is created with the `usage=single_payment` parameter, the QR Code closes automatically once the customer makes the payment, with the reason marked as `paid`.
* `null`: The QR Code has not been closed yet.

## Errors

> [accordion] The API \{key/secret} provided is invalid.
>
> **Code:** `4xx`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after.

> [accordion] We are facing some trouble completing your request at the moment. Please try again shortly.
>
> **Code:** `400`
>
> A GET API is executed by POST Method.
>
> **Solution:** Use the correct method, that is, GET.

> [accordion] \{Payment\_id} is not a valid id.
>
> **Code:** `400`
>
> A wrong Payment id is provided.
>
> **Solution:** Check if you have used a valid Payment id.

> [accordion] \{Payment\_id} is/are not required and should not be sent
>
> **Code:** `400`
>
> The URL is wrong or is missing something.
>
> **Solution:** Ensure that you use the correct and complete URL without any spelling mistakes.

> [accordion] The requested URL was not found on the server.
>
> **Code:** `400`
>
> The URL is wrong or is missing something.
>
> **Solution:** Ensure that you use the correct and complete URL without any spelling mistakes.

> [accordion] "count": 0
>
> **Code:** `400`
>
> No QR Code is found for the search criteria.
>
> **Solution:** There is no data for a particular Payment id. Try a different Payment id.
