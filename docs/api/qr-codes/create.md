> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a QR Code

> Create QR Codes with this endpoint and share with your customers.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create a QR Code.

* You can share the short URL with customers to accept payments.
* You can print and download it.
* You can create QR Codes for single or multiple use and for specific or all customers.

```bash Curl theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-X POST https://api.razorpay.com/v1/payments/qr_codes \
-H "Content-Type: application/json" \
-d '{
  "type": "upi_qr",
  "name": "Store Front Display",
  "usage": "single_use",
  "fixed_amount": true,
  "payment_amount": 300,
  "description": "For Store 1",
  "customer_id": "cust_HKsR5se84c5LTO",
  "close_by": 1681615838,
  "notes": {
    "purpose": "Test UPI QR Code notes"
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject qrRequest = new JSONObject();
qrRequest.put("type","upi_qr");
qrRequest.put("name","Store Front Display");
qrRequest.put("usage","single_use");
qrRequest.put("fixed_amount",true);
qrRequest.put("payment_amount",300);
qrRequest.put("description","For Store 1");
qrRequest.put("customer_id","cust_HKsR5se84c5LTO");
qrRequest.put("close_by",1681615838);
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
qrRequest.put("notes",notes);

QrCode qrcode = razorpay.qrCode.create(qrRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->qrCode->create(array("type" => "upi_qr","name" => "Store Front Display", "usage" => "single_use","fixed_amount" => true,"payment_amount" => 300,"customer_id" => "cust_HKsR5se84c5LTO","description" => "For Store 1","close_by" => 1681615838,"notes" => array("purpose" => "Test UPI QR code notes")));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.qrCode.create({
  type: "upi_qr",
  name: "Store Front Display",
  usage: "single_use",
  fixed_amount: true,
  payment_amount: 300,
  description: "For Store 1",
  customer_id: "cust_HKsR5se84c5LTO",
  close_by: 1681615838,
  notes: {
    purpose: "Test UPI QR Code notes"
  }
})
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.qrcode.create({
  "type": "upi_qr",
  "name": "Store Front Display",
  "usage": "single_use",
  "fixed_amount": True,
  "payment_amount": 300,
  "description": "For Store 1",
  "customer_id": "cust_HKsR5se84c5LTO",
  "close_by": 1681615838,
  "notes": {
    "purpose": "Test UPI QR Code notes"
  }
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

notes := map[string]interface{}{
  "purpose": "Test UPI QR Code notes",  
}  

data := map[string]interface{}{
  "type": "upi_qr",
  "name": "Store Front Display",
  "usage": "single_use",
  "fixed_amount": true,
  "payment_amount": 300,
  "description": "For Store 1",
  "customer_id": "cust_HKsR5se84c5LTO",
  "close_by": 1681615838,
  "notes": notes,
}
body, err := client.QrCode.create(data, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {
  "type": "upi_qr",
  "name": "Store Front Display",
  "usage": "single_use",
  "fixed_amount": true,
  "payment_amount": 300,
  "description": "For Store 1",
  "customer_id": "cust_HKsR5se84c5LTO",
  "close_by": 1681615838,
  "notes": {
    "purpose": "Test UPI QR Code notes"
  }
}
Razorpay::QrCode.create(para_attr)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> qrRequest = new Dictionary<string, object>();
qrRequest.Add("type", "upi_qr");
qrRequest.Add("name", "Store_1");
qrRequest.Add("usage", "single_use");
qrRequest.Add("fixed_amount", true);
qrRequest.Add("payment_amount", 300);
qrRequest.Add("description", "For Store 1");
qrRequest.Add("customer_id", "cust_MHYe2dVX323WYD");
qrRequest.Add("close_by", 1681615838);
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("notes_key_1", "Tea, Earl Grey, Hot");
notes.Add("notes_key_2", "Tea, Earl Grey… decaf.");
qrRequest.Add("notes", notes);

QrCode qrcode = client.QrCode.Create(qrRequest);
```

```bash CLI theme={null}
razorpay qr-codes create \
  --type upi_qr \
  --usage single_use \
  --name "Store Front Display" \
  --fixed-amount \
  --payment-amount 50000 \
  --description "Payment for Order #123" \
  --customer-id cust_ABC123 \
  --close-by 1776758130 \
  --note key1="Test QR"
```

```json Success theme={null}
{
  "id": "qr_HMsVL8HOpbMcjU",
  "entity": "qr_code",
  "created_at": 1623660301,
  "name": "Store Front Display",
  "usage": "single_use",
  "type": "upi_qr",
  "image_url": "https://rzp.io/i/BWcUVrLp",
  "payment_amount": 300,
  "status": "active",
  "description": "For Store 1",
  "fixed_amount": true,
  "payments_amount_received": 0,
  "payments_count_received": 0,
  "notes": {
    "purpose": "Test UPI QR Code notes"
  },
  "customer_id": "cust_HKsR5se84c5LTO",
  "close_by": 1681615838
}
```

```json Failure theme={null}
{
    "error": {
        "code": "BAD_REQUEST_ERROR",
        "description": "The requested URL was not found on the server.",
        "source": "NA",
        "step": "NA",
        "reason": "NA",
        "metadata": {}
    }
}
```

## Request Parameters

**type** `string` *required*

The type of the QR Code.

* `upi_qr`: Create a QR Code that accepts only UPI payments.

> [!NOTE]
>
> **Feature Request**
>
> This is an on-demand feature. Please raise a request with our [Support team](https://razorpay.com/support/#request) to get this feature activated on your account.

**name** `string`

Label entered to identify the QR Code. For example, `Store Front Display`.

**usage** `string` *required*

Indicates if the QR Code should be allowed to accept single payment or multiple payments. Possible values:

* `single_use`: QR Code will accept only one payment and then close automatically.
* `multiple_use` (default): QR Code will accept multiple payments.

**fixed\_amount** `boolean`

Indicates if the QR should accept payments of specific amounts or any amount. Possible values:

* `true`: QR Code accepts only a specific amount.
* `false` (default): QR Code accepts any amount.

> [!WARNING]
>
> **Watch Out!**
>
> When setting the `usage` to `single_use`, ensure that `fixed_amount` is `true` to generate the QR Code successfully.

**payment\_amount** `integer` *required*

The amount allowed for a transaction. If this is specified, then any transaction of an amount less than or more than this value is not allowed. For example, if this amount is set as `500000`, the customer cannot pay an amount less than or more than ₹5000.

**description** `string`

A brief description about the QR Code.

**customer\_id** `string`

The unique identifier of the customer the QR Code is linked with. Know more about the [Customers API](https://razorpay.com/docs/api/customers.md).

**close\_by** `integer`

Unix timestamp at which the QR Code is scheduled to be automatically closed. The time must be at least 2 minutes after the current time.

> [!WARNING]
>
> **Watch Out!**
>
> This parameter is available for single use QR codes only. You should ideally send a `close_by` value (expiry time less than or equal to 2 hours from QR generation).
>
> * The QR code has a minimum expiration time of 2 minutes and a maximum of 2 hours.
> * If `close_by` is `NULL`, the system sets a 2-hour expiry (returned in the response).
> * If `close_by` is greater than 2 hours, the system overrides it to 2 hours (returned in the response).
> * Use the returned `close_by` value for QR expiry. QR codes expire after the `close_by` time; you must regenerate them.
> * This parameter is only available for QR codes with `usage` set as `single_use`. You will not be able to use this parameter for `multiple_use` QR codes as it will generate an error.

**notes** `object`

Key-value pair that can be used to store additional information about the QR Code. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

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
> This is an on-demand feature. Please raise a request with our [Support team](https://razorpay.com/support/#request)  to get this feature activated on your account.

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

Unix timestamp at which the QR Code is scheduled to be automatically closed. The time must be at least 2 minutes after the current time.

> [!WARNING]
>
> **Watch Out!**
>
> This parameter is available for single use QR codes only. You should ideally send a `close_by` value (expiry time less than or equal to 2 hours from QR generation).
>
> * The QR code has a minimum expiration time of 2 minutes and a maximum of 2 hours.
> * If `close_by` is `NULL`, the system sets a 2-hour expiry (returned in the response).
> * If `close_by` is greater than 2 hours, the system overrides it to 2 hours (returned in the response).
> * Use the returned `close_by` value for QR expiry. QR codes expire after the `close_by` time; you must regenerate them.
> * This parameter is only available for QR codes with `usage` set as `single_use`. You will not be able to use this parameter for `multiple_use` QR codes as it will generate an error.

**closed\_at** `integer`

Unix timestamp at which the QR Code is automatically closed.

**close\_reason** `string`

The reason for the closure of the QR Code. Possible values:

* `on_demand`: When you close the QR Code using the APIs or the Dashboard.
* `paid`: If the QR Code is created with the `usage=single_payment` parameter, the QR Code closes automatically once the customer makes the payment, with the reason marked as `paid`.
* `null`: The QR Code has not been closed yet.

**tax\_invoice** `array`

Tax invoice details for GST-compliant QR codes. An array containing GST identification and supply information.

## Errors

> [accordion] The API \{key/secret} provided is invalid.
>
> **Code:** `4xx`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after.

> [accordion] The selected \{field name} is invalid.
>
> **Code:** `400`
>
> Data sent for a field is invalid. For example, when the data sent for `type` is `abc`, instead of the acceptable value.
>
> **Solution:** Ensure that the data sent for a field is valid. Re-check the acceptable values for that request parameter.

> [accordion] The \{field name} is required.
>
> **Code:** `400`
>
> A mandatory field is missing.
>
> **Solution:** Ensure all mandatory fields are present.

> [accordion] The payment amount must be at least 1.
>
> **Code:** `400`
>
> The amount specified is less than the minimum amount.
>
> **Solution:** Enter an amount equal to or greater than the minimum amount, that is 1.

> [accordion] \{Customer\_id} is not a valid id.
>
> **Code:** `400`
>
> Data entered for the Customer id field is invalid.
>
> **Solution:** Ensure that the Customer id is correct and valid.

> [accordion] type, usage, fixed\_amount, payment\_amount, description, close\_by is/are not required and should not be sent
>
> **Code:** `400`
>
> A POST API is executed by GET Method.
>
> **Solution:** Use the correct method, that is, POST.

> [accordion] \{close\_by} must be between 946684800 and 4765046400
>
> **Code:** `400`
>
> A wrong close by date is passed.
>
> **Solution:** Ensure you pass the correct close by date(Unix timestamp). It must be between 946684800 and 4765046400.

> [accordion] \{any extra field} ajshdas is/are not required and should not be sent
>
> **Code:** `400`
>
> An additional or unrequired parameter is passed.
>
> **Solution:** Ensure that you only pass the required parameters in the request body.
