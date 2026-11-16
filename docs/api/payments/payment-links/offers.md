> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Offers on Payment Links

> Provide offers to customers using Payment Links APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to provide offers on Payment Links. Razorpay Offers provides discounts or cashback on Payment Links issued to customers. You can restrict the payment methods on which the Offers are applied and limit their usage to a defined time period.

> [!WARNING]
>
> **Watch Out!**
>
> Ensure you do not enable partial payments on Payment Links on which offer is being applied.

Know more about how to show [Offers Payment Links](https://razorpay.com/docs/payments/payment-links/offers.md) via the Dashboard.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/payment_links
-H 'content-type: application/json'
-d '{
 "amount": 3400,
 "currency": "INR",
 "accept_partial": false,
 "reference_id": "#425",
 "description": "Payment for policy no #23456",
 "customer": {
   "name": "Gaurav Kumar",
   "contact": "+919000090000",
   "email": "gaurav.kumar@example.com"
 },
 "notify": {
   "sms": true,
   "email": true
 },
 "reminder_enable": false,
 "options": {
   "order": {
     "offers": [
       "offer_F4WMTC3pwFKnzq",
       "offer_F4WJHqvGzw8dWF"
     ]
   }
 }
}'
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->paymentLink->create(array('amount'=>20000, 'currency'=>'INR', 'accept_partial'=>false, 'description' => 'For XYZ purpose', 'customer' => array('name'=>'Gaurav Kumar', 'email' => 'gaurav.kumar@example.com', 'contact'=>'+919000090000'),  'notify'=>array('sms'=>true, 'email'=>true) ,'reminder_enable'=>false , 'options'=>array('order'=>array('offers'=>array('offer_I0PqexIiTmMRnA'))));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.paymentLink.create({
 "amount": 3400,
 "currency": "INR",
 "accept_partial": false,
 "reference_id": "#425",
 "description": "Payment for policy no #23456",
 "customer": {
   "name": "Gaurav Kumar",
   "contact": "+919000090000",
   "email": "gaurav.kumar@example.com"
 },
 "notify": {
   "sms": true,
   "email": true
 },
 "reminder_enable": false,
 "options": {
   "order": {
     "offers": [
       "offer_F4WMTC3pwFKnzq",
       "offer_F4WJHqvGzw8dWF"
     ]
   }
 }
})
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment_link.create({
 "amount": 3400,
 "currency": "INR",
 "accept_partial": false,
 "reference_id": "#425",
 "description": "Payment for policy no #23456",
 "customer": {
   "name": "Gaurav Kumar",
   "contact": "+919000090000",
   "email": "gaurav.kumar@example.com"
 },
 "notify": {
   "sms": true,
   "email": true
 },
 "reminder_enable": false,
 "options": {
   "order": {
     "offers": [
       "offer_F4WMTC3pwFKnzq",
       "offer_F4WJHqvGzw8dWF"
     ]
   }
 }
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
    "amount": 3400,
    "currency": "INR",
    "accept_partial": false,
    "reference_id": "#425",
    "description": "Payment for policy no #23456",
    "customer": map[string]interface{}{
      "name": "Gaurav Kumar",
      "contact": "+919000090000",
      "email": "gaurav.kumar@example.com",
    },
    "notify": map[string]interface{}{
      "sms": true,
      "email": true,
    },
    "reminder_enable": false,
    "options": map[string]interface{}{
      "order": map[string]interface{}{
        "offers": []string{
          "offer_JGQvQtvJmVDRIA",
        },
      },
    },
  }
body, err := client.PaymentLink.Create(data, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('key_id', 'key_secret')

para_attr = {
 "amount": 3400,
 "currency": "INR",
 "accept_partial": false,
 "reference_id": "#425",
 "description": "Payment for policy no #23456",
 "customer": {
   "name": "Gaurav Kumar",
   "contact": "+919000090000",
   "email": "gaurav.kumar@example.com"
 },
 "notify": {
   "sms": true,
   "email": true
 },
 "reminder_enable": false,
 "options": {
   "order": {
     "offers": [
       "offer_F4WMTC3pwFKnzq",
       "offer_F4WJHqvGzw8dWF"
     ]
   }
 }
}

Razorpay.headers = {"Content-type" => "application/json"}

Razorpay::PaymentLink.create(para_attr.to_json)
```

```java Java theme={null}
import org.json.JSONObject;
import com.razorpay.Payment;
import com.razorpay.RazorpayClient;
import com.razorpay.RazorpayException;

RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
JSONObject paymentLinkRequest = new JSONObject();
paymentLinkRequest.put("amount",3400);
paymentLinkRequest.put("currency","INR");
paymentLinkRequest.put("accept_partial",false);
paymentLinkRequest.put("reference_id","#aasasw8");
paymentLinkRequest.put("description","Payment for policy no #23456");
JSONObject customer = new JSONObject();
customer.put("name","+919000090000");
customer.put("contact","Gaurav Kumar");
customer.put("email","gaurav.kumar@example.com");
paymentLinkRequest.put("customer",customer);
JSONObject notify = new JSONObject();
notify.put("sms",true);
notify.put("email",true);
paymentLinkRequest.put("notify",notify);
paymentLinkRequest.put("reminder_enable",false);
JSONObject options = new JSONObject();
JSONObject transferRequest = new JSONObject();
List<Object> transfers = new ArrayList<>();
List<Object> offerParams = new ArrayList<>();
offerParams.add("offer_JTUADI4ZWBGWur");
offerParams.add("offer_F4WJHqvGzw8dWF");
JSONObject order = new JSONObject();
order.put("offers",offerParams);
options.put("order",order);
paymentLinkRequest.put("options",options);

PaymentLink payment = razorpay.paymentLink.create(paymentLinkRequest);
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> paymentLinkRequest = new Dictionary<string, object>();
paymentLinkRequest.Add("amount", 3400);
paymentLinkRequest.Add("currency", "INR");
paymentLinkRequest.Add("accept_partial", false);
paymentLinkRequest.Add("reference_id", "#aasasw8");
paymentLinkRequest.Add("description", "Payment for policy no #23456");
Dictionary<string, object> customer = new Dictionary<string, object>();
customer.Add("contact", "+919999999999");
customer.Add("name", "Gaurav Kumar");
customer.Add("email", "gaurav.kumar@example.com");
paymentLinkRequest.Add("customer", customer);
Dictionary<string, object> notify = new Dictionary<string, object>();
notify.Add("sms", true);
notify.Add("email", true);
paymentLinkRequest.Add("notify", notify);
paymentLinkRequest.Add("reminder_enable", false);
Dictionary<string, object> options = new Dictionary<string, object>();
List<string> offerParams = new List<string>();
offerParams.Add("offer_JTUADI4ZWBGWur");
offerParams.Add("offer_F4WJHqvGzw8dWF");
Dictionary<string, object> order = new Dictionary<string, object>();
order.Add("offers", offerParams);
options.Add("order", order);

PaymentLink paymentlink = client.PaymentLink.Create(paymentLinkRequest);
```

```bash CLI theme={null}
razorpay payment-links create \
  --amount 1000 \
  --currency INR \
  --offer offer_ABC123 \
  --offer offer_XYZ456
```

```json Success theme={null}
{
 "accept_partial": false,
 "amount": 3400,
 "amount_paid": 0,
 "cancelled_at": 0,
 "created_at": 1600183040,
 "currency": "INR",
 "customer": {
   "contact": "+919000090000",
   "email": "gaurav.kumar@example.com",
   "name": "Gaurav Kumar"
 },
 "description": "Payment for policy no #23456",
 "expire_by": 0,
 "expired_at": 0,
 "first_min_partial_amount": 0,
 "id": "plink_FdLt0WBldRyE5t",
 "notes": null,
 "notify": {
   "email": true,
   "sms": true
 },
 "payments": null,
 "reference_id": "#425",
 "reminder_enable": false,
 "reminders": [],
 "short_url": "https://rzp.io/i/CM5ohDC",
 "status": "created",
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

## Request Parameters

**amount** `integer` *required*

Amount to be paid using the Payment Link. Must be in the smallest unit of the currency. For example, if you want to receive a payment of , you must enter the value `30000`. In the case of three decimal currencies, such as KWD, BHD and OMR, to refund a payment of 295.991, pass the value as 295990. And in the case of zero decimal currencies such as JPY, to refund a payment of 295, pass the value as 295.

> [!WARNING]
>
> **Watch Out!**
>
> As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to refund a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.

**currency** `string`

A three-letter ISO code for the currency in which you want to accept the payment. For example, INR. Refer to the list of [supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).

> [!NOTE]
>
> **Handy Tips**
>
> Razorpay has added support for zero decimal currencies, such as JPY, and three decimal currencies, such as KWD, BHD, and OMR, allowing businesses to accept international payments in these currencies. Know more about [Currency Conversion](https://razorpay.com/docs/payments/international-payments/currency-conversion.md) (May 2024).

**accept\_partial** `boolean`

Indicates whether customers can make [partial payments](https://razorpay.com/docs/payments/payment-links/partial-payments.md) using the Payment Link. Possible values:

* `true`: Customer can make partial payments.
* `false` (default): Customer cannot make partial payments.

**first\_min\_partial\_amount** `integer` *required*

Minimum amount, in currency subunits, that must be paid by the customer as the first partial payment. Default value is `100`. Default currency is `INR`. For example, if an amount of  is to be received from the customer in two installments of #1 - , #2 - , then you can set this value as `500000`. Must be passed along with `accept_partial` parameter.

**upi\_link** `boolean` *required*

Must be set to `true` for creating UPI Payment Link. If the `upi_link` parameter is not passed or passed with value as false, a Standard Payment Link will be created. Possible values:

* `true`: Creates a UPI Payment Link.
* `false`: Creates a Standard Payment Link.

**description** `string`

A brief description of the Payment Link. The maximum character limit supported is 2048.

**reference\_id** `string`

Reference number tagged to a Payment Link. Must be a unique number for each Payment Link. The maximum character limit supported is 40.

**customer** `json object`

Customer details

**name** `string`

The customer's name.

**email** `string`

The customer's email address.

**contact** `string`

The customer's phone number.

**expire\_by** `integer`

Timestamp, in Unix, at which the Payment Link will expire. By default, a Payment Link will be valid for six months from the date of creation. Please note that the expire by date cannot exceed more than six months from the date of creation.

**notify** `array`

Defines who handles Payment Link notification.

**sms** `boolean`

Defines who handles the SMS notification. Possible values:

* `true`: Razorpay handles the notification.
* `false`: You handle the notification.

**email** `boolean`

Defines who handles the email notification. Possible values:

* `true`: Razorpay handles the notification.
* `false`: You handle the notification.

**notes** `json object`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Payment Link for Groceries.”`.

**callback\_url** `string`

If specified, adds a redirect URL to the Payment Link. Once customers completes the payment, they are redirected to the specified URL.

> [!NOTE]
>
> **Handy Tips**
>
> If the `callback_url` is passed, it must be passed in the correct format. That is, it should contain a URL.

**callback\_method** `string` *required*

If `callback_url` parameter is passed, callback\_method must be passed with the value `get`.

**reminder\_enable** `boolean`

Used to send [reminders](https://razorpay.com/docs/payments/payment-links/reminders.md) for the Payment Link. Possible values:

* `true`: To send reminders.
* `false`: To disable reminders.

**options** `array` *required*

Options to associate the `offer_id` with the Payment Link. Parent parameter under which the `order` child parameter must be passed.

**order** `array` *required*

The parameter under which the `offer_id` must be passed.

**offer\_id** `string` *required*

Unique identifier of the offer created in the previous step. For example, `offer_F4WMTC3pwFKnzq`.

## Response Parameters

**accept\_partial** `boolean`

Indicates whether customers can make [partial payments](https://razorpay.com/docs/payments/payment-links/partial-payments.md) using the Payment Link. Possible values:

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

Defaults to INR. We accept payments in [international currencies.](https://razorpay.com/docs/payments/international-payments#supported-currencies)

> [!NOTE]
>
> **Handy Tips**
>
> Razorpay has added support for zero decimal currencies, such as JPY, and three decimal currencies, such as KWD, BHD, and OMR, allowing businesses to accept international payments in these currencies. Know more about [Currency Conversion](https://razorpay.com/docs/payments/international-payments/currency-conversion.md) (May 2024).

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

Minimum amount that must be paid by the customer as the first partial payment. For example, if an amount of  is to be received from the customer in two installments of #1 - , #2 - , then you can set this value as `500000`.

**id** `string`

Unique identifier of the Payment Link. For example, `plink_ERgihyaAAC0VNW`.

**upi\_link** `boolean`

Indicates whether the Payment Link is a UPI Payment Link.

* `true`: A UPI Payment Link has been created.
* `false`: It is a Standard Payment Link.

**notes** `object`

Set of key-value pairs that you can use to store additional information. You (Businesses) can enter a maximum of 15 key-value pairs, with each value having a maximum limit of 256 characters.

**notify** `array`

Defines who handles Payment Link notification.

**sms** `boolean`

Defines who handles the SMS notification.

* `true`: Razorpay handles the notification.
* `false`: Businesses handle the notification.

**email** `boolean`

Defines who handles the email notification.

* `true`: Razorpay handles the notification.
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

Used to send [reminders](https://razorpay.com/docs/payments/payment-links/reminders.md) for the Payment Link. Possible values:

* `true`: To send reminders.
* `false`: To disable reminders.

**user\_id** `string`

A unique identifier for the user role through which the Payment Link was created. For example, `HD1JAKCCPGDfRx`.

## Errors

> [accordion] The api \{key/secret} provided is invalid
>
> **Code:** `4xx`
>
> There is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
>
> **Solution:** Make sure that:
>
> * The API Keys are active and entered correctly.
> * There are no white-spaces before or after the keys.

> [accordion] The \{input field} is required
>
> **Code:** `4xx`
>
> A mandatory field is empty.
>
> **Solution:** Ensure all mandatory fields and values are present.

> [accordion] wrong input fields sent.
>
> **Code:** `400`
>
> When wrong input fields are sent during Payment Link creation.
>
> **Solution:** Ensure that the input fields are added correctly. Refer to these [request parameters](https://razorpay.com/docs/api/payments/payment-links/create-standard.md#request-parameters) on how to add correct input fields.

> [accordion] payment link creation with reference ID already attempted
>
> **Code:** `400`
>
> An existing reference id has been passed.
>
> **Solution:** Ensure that a unique reference id is used for all Payment Links.

> [accordion] timestamp must be atleast 15 minutes in future
>
> **Code:** `400`
>
> The epoch time passed is less than 15 minutes from the current time.
>
> **Solution:** The `close_by` time should be more than 15 minutes from the current time.

> [accordion] Invalid access: Cannot create a payment link in live mode, as live mode is disabled for merchant.
>
> **Code:** `400`
>
> Occurs when you try to create a Payment Link in Live mode, but live mode is disabled for you
>
> **Solution:** Raise a request to our [support team](https://razorpay.com/support/) to get live mode enabled for you.

> [accordion] Invalid access: Cannot create a payment link, as Merchant is Suspended.
>
> **Code:** `400`
>
> Occurs when you try to create a Payment Link when you have been been suspended.
>
> **Solution:** Raise a request to our [support team](https://razorpay.com/support/) to be reinstated.

> [accordion] value: the length must not be greater than 255.
>
> **Code:** `400`
>
> When the notes length is greater than 255 characters during Payment Link creation.
>
> **Solution:** Please create a payment link with notes values less than 255 characters.
