> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Update Standard Payment Link

> Update the details of a Standard Payment Link using this endpoint.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to edit the Standard Payment Link details such as the reference id, expiry date and so on.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X PATCH https://api.razorpay.com/v1/payment_links/plink_Et2G7ymGcTTuM5 \
-H 'Content-type: application/json' \
-d '{
    "reference_id": "TS35",
    "expire_by": 1653347540,
    "reminder_enable":false,
    "notes":{
      "policy_name": "Life Insurance Policy"
    }
}'
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->paymentLink->fetch($paymentLinkId)->edit(array("reference_id"=>"TS42", "expire_by"=>"1640270451" , "reminder_enable"=>0, "notes"=>["policy_name"=>"Life Insurance Policy 2"]));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.paymentLink.edit(paymentLinkId, {
    "reference_id": "TS35",
    "expire_by": 1653347540,
    "reminder_enable":false,
    "notes":{
      "policy_name": "Life Insurance Policy"
    }
})
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment_link.edit(paymentLinkId, {
    "reference_id": "TS35",
    "expire_by": 1653347540,
    "reminder_enable":false,
    "notes":{
      "policy_name": "Life Insurance Policy"
    }
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
    "reference_id": "TS35",
    "expire_by": 1653347540,
    "reminder_enable":false,
    "notes":map[string]interface{}{
      "policy_name": "Life Insurance Policy",
    },
}
body, err := client.PaymentLink.Update("<paymentLinkId>", data, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('key_id', 'key_secret')

Razorpay.headers = {"Content-type" => "application/json"}

paymentLinkId = "plink_ExjpAUN3gVHrPJ"

para_attr = {
    "reference_id": "TS35",
    "expire_by": 1653347540,
    "reminder_enable":false,
    "notes":{
      "policy_name": "Life Insurance Policy"
    }
}

Razorpay::PaymentLink.edit(paymentLinkId, para_attr.to_json)
```

```java Java theme={null}
import org.json.JSONObject;
import com.razorpay.Payment;
import com.razorpay.RazorpayClient;
import com.razorpay.RazorpayException;

RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
String paymentLinkId = "plink_FMbhpT6nqDjDei";

JSONObject paymentLinkRequest = new JSONObject();
paymentLinkRequest.put("reference_id","TS35");
paymentLinkRequest.put("expire_by",1653347540);
paymentLinkRequest.put("reminder_enable",true);
JSONObject notes = new JSONObject();
notes.put("policy_name","Life Insurance Policy");
paymentLinkRequest.put("notes",notes);

PaymentLink paymentlink = razorpay.paymentLink.edit(PaymentLinkId,paymentLinkRequest);
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string paymentLinkId = "plink_Z6t7VFTb9xHeOs";

Dictionary<string, object> paymentLinkRequest = new Dictionary<string, object>();
paymentLinkRequest.Add("reference_id","TS35");
paymentLinkRequest.Add("expire_by",1653347540);
paymentLinkRequest.Add("reminder_enable",true);
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("policy_name", "Life Insurance Policy");
paymentLinkRequest.Add("notes", notes);

PaymentLink paymentlink = client.PaymentLink.Fetch(paymentLinkId).Edit(paymentLinkRequest);
```

```bash CLI theme={null}
razorpay payment-links update plink_ABC123 \
  --accept-partial \
  --expire-by 1776758130 \
  --reference-id "ref#updated" \
  --note key1="Updated note"
```

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X PATCH https://api.razorpay.com/v1/payment_links/plink_Et2G7ymGcTTuM5 \
-H 'Content-type: application/json' \
-d '{
    "reference_id": "TS35",
    "expire_by": 1653347540,
    "reminder_enable":false,
    "notes":{
      "policy_name": "Life Insurance Policy"
    }
}'
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->paymentLink->fetch($paymentLinkId)->edit(array("reference_id"=>"TS42", "expire_by"=>"1640270451" , "reminder_enable"=>0, "notes"=>["policy_name"=>"Life Insurance Policy 2"]));
```

```java Java theme={null}
import org.json.JSONObject;
import com.razorpay.Payment;
import com.razorpay.RazorpayClient;
import com.razorpay.RazorpayException;

RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
String paymentLinkId = "plink_FMbhpT6nqDjDei";

JSONObject paymentLinkRequest = new JSONObject();
paymentLinkRequest.put("reference_id","TS35");
paymentLinkRequest.put("expire_by",1653347540);
paymentLinkRequest.put("reminder_enable",true);
JSONObject notes = new JSONObject();
notes.put("policy_name","Life Insurance Policy");
paymentLinkRequest.put("notes",notes);

PaymentLink paymentlink = razorpay.paymentLink.edit(PaymentLinkId,paymentLinkRequest);
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string paymentLinkId = "plink_Z6t7VFTb9xHeOs";

Dictionary<string, object> paymentLinkRequest = new Dictionary<string, object>();
paymentLinkRequest.Add("reference_id","TS35");
paymentLinkRequest.Add("expire_by",1653347540);
paymentLinkRequest.Add("reminder_enable",true);
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("policy_name", "Life Insurance Policy");
paymentLinkRequest.Add("notes", notes);

PaymentLink paymentlink = client.PaymentLink.Fetch(paymentLinkId).Edit(paymentLinkRequest);
```

```bash CLI theme={null}
razorpay payment-links update plink_ABC123 \
  --accept-partial \
  --expire-by 1776758130 \
  --reference-id "ref#updated" \
  --note key1="Updated note"
```

```json Success theme={null}
{
  "accept_partial": false,
  "amount": 1000,
  "amount_paid": 0,
  "callback_method": "",
  "callback_url": "",
  "cancelled_at": 0,
  "created_at": 1596194425,
  "currency": "MYR",
  "customer": {
    "contact": "<phone>",
    "email": "<email>",
    "name": "<name>"
  },
  "description": "Payment for policy no #23456",
  "expire_by": 1653347540,
  "expired_at": 0,
  "first_min_partial_amount": 100,
  "id": "plink_FL5HCrWEO112OW",
  "notes": [
    {
      "key": "policy_name",
      "value": "Life Insurance Policy"
    }
  ],
  "notify": {
    "email": true,
    "sms": false
  },
  "payments": [],
  "reference_id": "TS35",
  "reminder_enable": false,
  "reminders": {
    "status": "failed"
  },
  "short_url": "https://rzp.io/i/O8CYyZ2",
  "status": "created",
  "updated_at": 1596194683,
  "user_id": ""
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

```json Success theme={null}
{
  "amount": 1000,
  "amount_paid": 0,
  "callback_method": "",
  "callback_url": "",
  "cancelled_at": 0,
  "created_at": 1596194425,
  "currency": "MYR",
  "customer": {
    "contact": "<phone>",
    "email": "<email>",
    "name": "<name>"
  },
  "description": "Payment for policy no #23456",
  "expire_by": 1653347540,
  "expired_at": 0,
  "id": "plink_FL5HCrWEO112OW",
  "notes": [
    {
      "key": "policy_name",
      "value": "Life Insurance Policy"
    }
  ],
  "notify": {
    "email": true,
    "sms": false
  },
  "payments": [],
  "reference_id": "TS35",
  "reminder_enable": false,
  "reminders": {
    "status": "failed"
  },
  "short_url": "https://rzp.io/i/O8CYyZ2",
  "status": "created",
  "updated_at": 1596194683,
  "user_id": ""
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

Unique identifier of the Payment Link.

## Request Parameters

**accept\_partial** `boolean`

Indicates whether customers can make [partial payments](https://razorpay.com/docs/my/payments/payment-links/partial-payments.md) using the Payment Link. Possible values:

* `true`: Customer can make partial payments.
* `false` (default): Customer cannot make partial payments.

**reference\_id** `string`

Adds a unique reference number to an existing link.

**expire\_by** `integer`

Timestamp, in Unix format, when the payment links should expire.

**notes** `object`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Payment Link for Groceries”`.

## Response Parameters

**accept\_partial** `boolean`

Indicates whether customers can make [partial payments](https://razorpay.com/docs/my/payments/payment-links/partial-payments.md) using the Payment Link. Possible values:

* `true`: Customer can make partial payments.
* `false` (default): Customer cannot make partial payments.

**amount** `integer`

Amount to be paid using the Payment Link. Must be in the smallest unit of the currency. For example, if you want to receive a payment of , you must enter the value `30000`. In the case of three decimal currencies, such as KWD, BHD and OMR, to refund a payment of 295.991, pass the value as 295990. And in the case of zero decimal currencies such as JPY, to refund a payment of 295, pass the value as 295.

> [!WARNING]
>
> **Watch Out!**
>
> As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to refund a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.

**amount\_paid** `integer`

Amount paid by the customer.

**callback\_url** `string`

If specified, adds a redirect URL to the Payment Link. Once the customer completes the payment, they are redirected to the specified URL.

**callback\_method** `string`

If `callback_url` parameter is passed, `callback_method` must be passed with the value `get`.

**cancelled\_at** `integer`

Timestamp, in Unix, at which the Payment Link was cancelled by you.

**created\_at** `integer`

Timestamp, in Unix, indicating when the Payment Link was created.

**currency** `string`

Defaults to MYR. We accept payments in [international currencies.](https://razorpay.com/docs/my/payments/international-payments#malaysian-businesses)

> [!NOTE]
>
> **Handy Tips**
>
> Razorpay Curlec has added support for zero decimal currencies, such as JPY, and three decimal currencies, such as KWD, BHD, and OMR, allowing businesses to accept international payments in these currencies. Know more about Currency Conversion (May 2024).

**customer** `json object`

Customer details.

**name** `string`

The customer's name.

**email** `string`

The customer's email address.

**contact** `string`

The customer's phone number.

**description** `string`

A brief description of the Payment Link.

**expire\_by** `integer`

Timestamp, in Unix, when the Payment Link will expire. By default, a Payment Link will be valid for six months from the date of creation. Please note that the expire by date cannot exceed more than six months from the date of creation.

**expired\_at** `integer`

Timestamp, in Unix, at which the Payment Link expired.

**first\_min\_partial\_amount** `integer`

Minimum amount that must be paid by the customer as the first partial payment. For example, if an amount of RM7,000 is to be received from the customer in two instalments of #1 - RM5,000, #2 - RM2,000, then you can set this value as `500000`.

**id** `string`

Unique identifier of the Payment Link. For example, `plink_ERgihyaAAC0VNW`.

**upi\_link** `boolean`

Indicates whether the Payment Link is a UPI Payment Link. UPI Payment Links are not available for businesses in Malaysia, so this value is always `false`.

**notes** `object`

Set of key-value pairs that you can use to store additional information. You (Businesses) can enter a maximum of 15 key-value pairs, with each value having a maximum limit of 256 characters.

**notify** `array`

Defines who handles Payment Link notification.

**sms** `boolean`

Defines who handles the SMS notification.

* `true`: Razorpay Curlec handles the notification.
* `false`: Businesses handle the notification.

**email** `boolean`

Defines who handles the email notification.

* `true`: Razorpay Curlec handles the notification.
* `false`: Businesses handle the notification.

**payments** `array`

Payment details such as amount, payment id, Payment Link id and more are stored in this array. It is populated only after a payment is successfully captured by the customer. Only captured payments will be shown here. Until then, the value is `null`.

**amount** `integer`

The amount paid by the customer using the Payment Link.

**created\_at** `integer`

Timestamp, in Unix, indicating when the payment was made.

**method** `string`

The payment method used to make the payment. Possible values:

* `netbanking`
* `card`
* `wallet`
* `upi`
* `emi`
* `bank_transfer`

**payment\_id** `string`

Unique identifier of the payment made against the Payment Link.

**plink\_id** `string`

Unique identifier of the Payment Link. For example, `plink_ERgihyaAAC0VNW`.

**status** `string`

The payment state. Possible value is `captured`.

**updated\_at** `integer`

Timestamp, in Unix, indicating when the payment was updated.

**reference\_id** `string`

Reference number tagged to a Payment Link. Must be a unique number for each Payment Link. The maximum character limit supported is 40.

**short\_url** `string`

The unique short URL generated for the Payment Link.

**status** `string`

Displays the current state of the Payment Link. Possible values:

* `created`
* `partially_paid`
* `expired`
* `cancelled`
* `paid`

**updated\_at** `integer`

Timestamp, in Unix, indicating when the Payment Link was updated.

**reminder\_enable** `boolean`

Used to send [reminders](https://razorpay.com/docs/my/payments/payment-links/reminders.md) for the Payment Link. Possible values:

* `true`: To send reminders.
* `false`: To disable reminders.

**user\_id** `string`

A unique identifier for the user role through which the Payment Link was created. For example, `HD1JAKCCPGDfRx`.

**whatsapp\_link** `boolean`

Whether the payment link is whatsapp link. For example, `false`.

**reminders** `object`

Reminder dispatch state for the payment link. Contains `status` (one of `pending`, `in_progress`, `failed`).

## Errors

> [accordion] update can only be made in created or partially paid state
>
> **Code:** `400`
>
> A payment link has been passed in `paid` state.
>
> **Solution:** Ensure that the Payment Link is in the `created` state or `partially paid` state to update the Payment Link.

> [accordion] wrong input fields sent.
>
> **Code:** `400`
>
> When wrong input fields are sent while updating the Payment Link.
>
> **Solution:** Ensure that the input fields are added correctly. Refer to these [request parameters](https://razorpay.com/docs/my/api/payments/payment-links/create-standard.md#request-parameters) on how to add correct input fields.

> [accordion] The id provided does not exist
>
> **Code:** `400`
>
> The Payment Link does not belong to the requestor business, or it doesn't exist.
>
> **Solution:** Ensure that the Payment Link is valid and belongs to the requestor business.

> [accordion] The api \{key/secret} provided is invalid
>
> **Code:** `4xx`
>
> There is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
>
> **Solution:** Ensure that the API Keys are active and entered correctly. Also, make sure there are no white-spaces before or after the keys.

> [accordion] an update is already in progress.
>
> **Code:** `400`
>
> Another update or cancel operation is currently in progress for the same Payment Link. Razorpay Curlec holds a short-lived lock against the link id to prevent concurrent state changes.
>
> **Solution:** Wait a few seconds and retry. If the issue persists, fetch the link to confirm its current state before retrying.

> [accordion] extra fields sent in state \{status}.
>
> **Code:** `400`
>
> The request body contains a field that is not editable while the Payment Link is in the current status. The error message echoes the actual status. For example, `extra fields sent in state partially_paid`. The set of editable fields varies based on the link's status.
>
> **Solution:** Restrict the PATCH body to the fields editable in the link's current status. Fetch the link first to confirm its status, then only send fields allowed for that status.
