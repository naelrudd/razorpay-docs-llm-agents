# Create a Standard Payment Link

**POST** `/v1/payment_links`

Use this endpoint to create a Payment Link using basic details such as amount, expiry date, reference id, description, customer details and so on.

- **Basic Payment Links** 

These are regular Payment Links, which are not customised.

- **Customised Payment Links** 

You can [customise Payment Links](https://razorpay.com/docs/build/llm-docs/payments/payment-links/customise.md) as per your business requirements.

**INFO**

**Handy Tips**

As per Razorpay's updated security policy, even if the customer's email address and phone number are provided while creating the Payment Link, these details are not auto-populated on the Checkout section of the Payment Link hosted page. The customer will have to enter these details manually while making the payment.

**WARN**

**Test Mode Limit**

In test mode, you can create up to 30 Payment Links per business. If you need to create more than 30 Payment Links for testing purposes, contact [Razorpay Support](https://razorpay.com/support/).

- After successful completion of the payment, customers can be redirected to a specific URL using the `callback_url` and `callback_method` parameters. Know more about how to use [these paramaters](https://razorpay.com/docs/build/llm-docs/api/payments/payment-links.md#using-callback-url-parameter).

- Verify the `razorpay_signature` parameter to validate that it is authentic and sent from Razorpay servers. Know more about how to [Verify Signature](https://razorpay.com/docs/build/llm-docs/payments/payment-links/apis.md#verify-signature).

### Request

```curl: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/payment_links/ \
-H 'Content-type: application/json' \
-d '{
  "amount": 1000,
  "currency": "INR",
  "accept_partial": true,
  "first_min_partial_amount": 100,
  "expire_by": 1691097057,
  "reference_id": "TS1989",
  "description": "Payment for policy no #23456",
  "customer": {
    "name": "Gaurav Kumar",
    "contact": "+919876543210",
    "email": "gaurav.kumar@example.com"
  },
  "notify": {
    "sms": true,
    "email": true
  },
  "reminder_enable": true,
  "notes": {
    "policy_name": "Life Insurance Policy"
  },
  "callback_url": "https://example-callback-url.com/",
  "callback_method": "get"
}'

```php: PHP 
$api = new Api($key_id, $secret);

$api->paymentLink->create(array('amount'=>500, 'currency'=>'INR', 'accept_partial'=>true,
'first_min_partial_amount'=>100, 'description' => 'For XYZ purpose', 'customer' => array('name'=>'Gaurav Kumar',
'email' => 'gaurav.kumar@example.com', 'contact'=>'+919876543210'),  'notify'=>array('sms'=>true, 'email'=>true) ,
'reminder_enable'=>true ,'notes'=>array('policy_name'=> 'Life Insurance Policy'),'callback_url' => 'https://example-callback-url.com/',
'callback_method'=>'get'));

```javascript: Node.js 
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.paymentLink.create({
  amount: 500,
  currency: "INR",
  accept_partial: true,
  first_min_partial_amount: 100,
  description: "For XYZ purpose",
  customer: {
    name: "Gaurav Kumar",
    email: "gaurav.kumar@example.com",
    contact: "+919876543210"
  },
  notify: {
    sms: true,
    email: true
  },
  reminder_enable: true,
  notes: {
    policy_name: "Life Insurance Policy"
  },
  callback_url: "https://example-callback-url.com/",
  callback_method: "get"
})

```python: Python 
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment_link.create({
  "amount": 500,
  "currency": "INR",
  "accept_partial": true,
  "first_min_partial_amount": 100,
  "description": "For XYZ purpose",
  "customer": {
    "name": "Gaurav Kumar",
    "email": "gaurav.kumar@example.com",
    "contact": "+919876543210"
  },
  "notify": {
    "sms": True,
    "email": True
  },
  "reminder_enable": true,
  "notes": {
    "policy_name": "Life Insurance Policy"
  },
  "callback_url": "https://example-callback-url.com/",
  "callback_method": "get"
})

```go: Go 
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
    "amount": 1000,
    "currency": "INR",
    "accept_partial": true,
    "first_min_partial_amount": 100,
    "expire_by": 1691097057,
    "reference_id": "TS1989",
    "description": "Payment for policy no #23456",
    "customer": map[string]interface{}{
        "name": "Gaurav Kumar",
        "contact": "+919876543210",
        "email": "gaurav.kumar@example.com",
    },
    "notify": map[string]interface{}{
        "sms": true,
        "email": true,
    },
    "reminder_enable": true,
    "notes": map[string]interface{}{
        "policy_name": "Life Insurance Policy",
    },
    "callback_url": "https://example-callback-url.com/",
    "callback_method": "get",
}
body, err := client.PaymentLink.Create(data, nil)

```ruby: Ruby
require "razorpay"
Razorpay.setup('key_id', 'key_secret')
Razorpay.headers = {"Content-type" => "application/json"}

para_attr = {
  "amount": 500,
  "currency": "INR",
  "accept_partial": true,
  "first_min_partial_amount": 100,
  "description": "For XYZ purpose",
  "customer": {
    "name": "Gaurav Kumar",
    "email": "gaurav.kumar@example.com",
    "contact": "+919876543210"
  },
  "notify": {
    "sms": true,
    "email": true
  },
  "reminder_enable": true,
  "notes": {
    "policy_name": "Life Insurance Policy"
  },
  "callback_url": "https://example-callback-url.com/",
  "callback_method": "get"
}

Razorpay::PaymentLink.create(para_attr.to_json)

```java: Java
import org.json.JSONObject;
import com.razorpay.Payment;
import com.razorpay.RazorpayClient;
import com.razorpay.RazorpayException;

RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
JSONObject paymentLinkRequest = new JSONObject();
paymentLinkRequest.put("amount",1000);
paymentLinkRequest.put("currency","INR");
paymentLinkRequest.put("accept_partial",true);
paymentLinkRequest.put("first_min_partial_amount",100);
paymentLinkRequest.put("expire_by",1691097057);
paymentLinkRequest.put("reference_id","TS1989");
paymentLinkRequest.put("description","Payment for policy no #23456");
JSONObject customer = new JSONObject();
customer.put("name","+919876543210");
customer.put("contact","Gaurav Kumar");
customer.put("email","gaurav.kumar@example.com");
paymentLinkRequest.put("customer",customer);
JSONObject notify = new JSONObject();
notify.put("sms",true);
notify.put("email",true);
paymentLinkRequest.put("notify",notify);
paymentLinkRequest.put("reminder_enable",true);
JSONObject notes = new JSONObject();
notes.put("policy_name","Life Insurance Policy");
paymentLinkRequest.put("notes",notes);
paymentLinkRequest.put("callback_url","https://example-callback-url.com/");
paymentLinkRequest.put("callback_method","get");
              
PaymentLink payment = razorpay.paymentLink.create(paymentLinkRequest);

```csharp: .NET
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary paymentLinkRequest = new Dictionary();
paymentLinkRequest.Add("amount", 1000);
paymentLinkRequest.Add("currency", "INR");
paymentLinkRequest.Add("accept_partial", true);
paymentLinkRequest.Add("first_min_partial_amount", 100);
paymentLinkRequest.Add("expire_by", 1691097057);
paymentLinkRequest.Add("reference_id", "TS1989");
paymentLinkRequest.Add("description", "Payment for policy no #23456");
Dictionary customer = new Dictionary();
customer.Add("contact", "+919876543210");
customer.Add("name", "Gaurav Kumar");
customer.Add("email", "gaurav.kumar@example.com");
paymentLinkRequest.Add("customer", customer);
Dictionary notify = new Dictionary();
notify.Add("sms", true);
notify.Add("email", true);
paymentLinkRequest.Add("reminder_enable", true);
Dictionary notes = new Dictionary();
notes.Add("policy_name", "Life Insurance Policy");
paymentLinkRequest.Add("notes", notes);
paymentLinkRequest.Add("callback_url", "https://example-callback-url.com/");
paymentLinkRequest.Add("callback_method", "get");

PaymentLink paymentlink = client.PaymentLink.Create(paymentLinkRequest);

```bash: CLI
razorpay payment-links create \
  --amount 1000 \
  --currency INR \
  --description "Payment for Order #123" \
  --reference-id "ref#001" \
  --customer-name "Gaurav Kumar" \
  --customer-contact "+919123456780" \
  --customer-email "gaurav.kumar@example.com" \
  --notify-sms \
  --notify-email \
  --reminder-enable \
  --expire-by 1776758130 \
  --callback-url "https://example.com/payment-callback" \
  --callback-method get \
  --note key1="Test payment link"
```

### Response

```json: Success
{
  "accept_partial": true,
  "amount": 1000,
  "amount_paid": 0,
  "callback_method": "get",
  "callback_url": "https://example-callback-url.com/",
  "cancelled_at": 0,
  "created_at": 1591097057,
  "currency": "INR",
  "customer": {
    "contact": "+919876543210",
    "email": "gaurav.kumar@example.com",
    "name": "Gaurav Kumar"
  },
  "description": "Payment for policy no #23456",
  "expire_by": 1691097057,
  "expired_at": 0,
  "first_min_partial_amount": 100,
  "id": "plink_ExjpAUN3gVHrPJ",
  "notes": {
    "policy_name": "Jeevan Bima"
  },
  "notify": {
    "email": true,
    "sms": true
  },
  "payments": null,
  "reference_id": "TS1989",
  "reminder_enable": true,
  "reminders": [],
  "short_url": "https://rzp.io/i/nxrHnLJ",
  "status": "created",
  "updated_at": 1591097057,
  "user_id": ""
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

`amount` _mandatory_
: `integer` Amount to be paid using the Payment Link. Must be in the smallest unit of the currency. For example, if you want to receive a payment of , you must enter the value `30000`. In the case of three decimal currencies, such as KWD, BHD and OMR, to refund a payment of 295.991, pass the value as 295990. And in the case of zero decimal currencies such as JPY, to refund a payment of 295, pass the value as 295.

  
**WARN**

**Watch Out!**

As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to refund a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.

`currency` _optional_
: `string` A three-letter ISO code for the currency in which you want to accept the payment. For example, INR. Refer to the list of [supported currencies](https://razorpay.com/docs/build/llm-docs/payments/international-payments.md#supported-currencies).

  
**INFO**

**Handy Tips**

Razorpay has added support for zero decimal currencies, such as JPY, and three decimal currencies, such as KWD, BHD, and OMR, allowing businesses to accept international payments in these currencies. Know more about [Currency Conversion](https://razorpay.com/docs/build/llm-docs/payments/international-payments/currency-conversion.md) (May 2024).

.

`accept_partial` _optional_
: `boolean` Indicates whether customers can make [partial payments](https://razorpay.com/docs/build/llm-docs/payments/payment-links/partial-payments.md) using the Payment Link. Possible values:
  - `true`: Customer can make partial payments.
  - `false` (default): Customer cannot make partial payments.

`first_min_partial_amount` _conditionally mandatory_
: `integer` Minimum amount, in currency subunits, that must be paid by the customer as the first partial payment. Default value is `100`. Default currency is `INR`. For example, if an amount of  is to be received from the customer in two installments of #1 - , #2 - , then you can set this value as `500000`. Must be passed along with `accept_partial` parameter.

`upi_link` _mandatory for creating UPI Payment Link_
: `boolean` Must be set to `true` for creating UPI Payment Link. If the `upi_link` parameter is not passed or passed with value as false, a Standard Payment Link will be created. Possible values:
  - `true`: Creates a UPI Payment Link.
  - `false`: Creates a Standard Payment Link.
  

`description` _optional_
: `string` A brief description of the Payment Link. The maximum character limit supported is 2048.

`reference_id` _optional_
: `string` Reference number tagged to a Payment Link. Must be a unique number for each Payment Link. The maximum character limit supported is 40.

`customer` _optional_
: `json object` Customer details

  `name` _optional_
  : `string` The customer's name.

  `email` _optional_
  : `string` The customer's email address.

  `contact` _optional_
  : `string` The customer's phone number.

`expire_by` _optional_
: `integer` Timestamp, in Unix, at which the Payment Link will expire. By default, a Payment Link will be valid for six months from the date of creation. Please note that the expire by date cannot exceed more than six months from the date of creation.

`notify` _optional_
: `array` Defines who handles Payment Link notification.

  `sms` _optional_
  : `boolean` Defines who handles the SMS notification. Possible values:
    - `true`: Razorpay handles the notification.
    - `false`: You handle the notification.

  `email` _optional_
  : `boolean` Defines who handles the email notification. Possible values:
    - `true`: Razorpay handles the notification.
    - `false`: You handle the notification.

`notes` _optional_
: `json object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Payment Link for Groceries.”`.

`callback_url` _optional_
: `string` If specified, adds a redirect URL to the Payment Link. Once customers completes the payment, they are redirected to the specified URL.

   
**INFO**

**Handy Tips** 

If the `callback_url` is passed, it must be passed in the correct format. That is, it should contain a URL.

`callback_method` _conditionally mandatory_
: `string` If `callback_url` parameter is passed, callback_method must be passed with the value `get`.

`reminder_enable` _optional_
: `boolean` Used to send [reminders](https://razorpay.com/docs/build/llm-docs/payments/payment-links/reminders.md) for the Payment Link. Possible values:
    - `true`: To send reminders.
    - `false`: To disable reminders.

### Parameters

`accept_partial` 
: `boolean` Indicates whether customers can make [partial payments](https://razorpay.com/docs/build/llm-docs/payments/payment-links/partial-payments.md) using the Payment Link. Possible values:
  - `true`: Customer can make partial payments.
  - `false` (default): Customer cannot make partial payments.

`amount`
: `integer` Amount to be paid using the Payment Link. Must be in the smallest unit of the currency. For example, if you want to receive a payment of , you must enter the value `30000`. In the case of three decimal currencies, such as KWD, BHD and OMR, to refund a payment of 295.991, pass the value as 295990. And in the case of zero decimal currencies such as JPY, to refund a payment of 295, pass the value as 295.

  
**WARN**

**Watch Out!**

As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to refund a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.

`amount_paid`
: `integer` Amount paid by the customer.

`callback_url`
: `string` If specified, adds a redirect URL to the Payment Link. Once the customer completes the payment, they are redirected to the specified URL.

`callback_method`
: `string` If `callback_url` parameter is passed, `callback_method` must be passed with the value `get`.

`cancelled_at`
: `integer` Timestamp, in Unix, at which the Payment Link was cancelled by you.

`created_at`
: `integer` Timestamp, in Unix, indicating when the Payment Link was created.

`currency`
: `string` Defaults to INR. We accept payments in [international currencies.](https://razorpay.com/docs/build/llm-docs/payments/international-payments.md#supported-currencies)

  
**INFO**

**Handy Tips**

Razorpay has added support for zero decimal currencies, such as JPY, and three decimal currencies, such as KWD, BHD, and OMR, allowing businesses to accept international payments in these currencies. Know more about [Currency Conversion](https://razorpay.com/docs/build/llm-docs/payments/international-payments/currency-conversion.md) (May 2024).

.

`customer`
: `json object` Customer details.

  `name`
  : `string` The customer's name.

  `email`
  : `string` The customer's email address.

  `contact`
  : `string` The customer's phone number.

`description`
: `string` A brief description of the Payment Link.

`expire_by`
: `integer` Timestamp, in Unix, when the Payment Link will expire. By default, a Payment Link will be valid for six months from the date of creation. Please note that the expire by date cannot exceed more than six months from the date of creation.

`expired_at`
: `integer` Timestamp, in Unix, at which the Payment Link expired.

`first_min_partial_amount`
: `integer` Minimum amount that must be paid by the customer as the first partial payment. For example, if an amount of  is to be received from the customer in two installments of #1 - , #2 - , then you can set this value as `500000`.

`id`
: `string` Unique identifier of the Payment Link. For example, `plink_ERgihyaAAC0VNW`.

`upi_link`
: `boolean` Indicates whether the Payment Link is a UPI Payment Link.
  - `true`: A UPI Payment Link has been created.
  - `false`: It is a Standard Payment Link.

`notes`
: `object` Set of key-value pairs that you can use to store additional information. You (Businesses) can enter a maximum of 15 key-value pairs, with each value having a maximum limit of 256 characters.

`notify`
: `array` Defines who handles Payment Link notification.

  `sms`
  : `boolean` Defines who handles the SMS notification.
    - `true`: Razorpay handles the notification.
    - `false`: Businesses handle the notification.

  `email`
  : `boolean` Defines who handles the email notification.
    - `true`: Razorpay handles the notification.
    - `false`: Businesses handle the notification.

`payments`
: `array` Payment details such as amount, payment id, Payment Link id and more are stored in this array. It is populated only after a payment is successfully captured by the customer. Only captured payments will be shown here. Until then, the value is `null`.

  `amount`
  : `integer` The amount paid by the customer using the Payment Link.

  `created_at`
  : `integer` Timestamp, in Unix, indicating when the payment was made.

  

  `method`
  : `string` The payment method used to make the payment. Possible values:
    - `netbanking`
    - `card`
    - `wallet`
    - `upi`
    - `emi`
    - `bank_transfer`
  
  

  

  

  

  `payment_id`
  : `string` Unique identifier of the payment made against the Payment Link.

  `plink_id`
  : `string` Unique identifier of the Payment Link. For example, `plink_ERgihyaAAC0VNW`.

  `status`
  : `string` The payment state. Possible value is `captured`.

  `updated_at`
  : `integer` Timestamp, in Unix, indicating when the payment was updated.

`reference_id`
: `string` Reference number tagged to a Payment Link. Must be a unique number for each Payment Link. The maximum character limit supported is 40.

`short_url`
: `string` The unique short URL generated for the Payment Link.

`status`
: `string` Displays the current state of the Payment Link. Possible values:
  - `created`
  - `partially_paid`
  - `expired`
  - `cancelled`
  - `paid`

`updated_at`
: `integer` Timestamp, in Unix, indicating when the Payment Link was updated.

`reminder_enable`
: `boolean` Used to send [reminders](https://razorpay.com/docs/build/llm-docs/payments/payment-links/reminders.md) for the Payment Link. Possible values:
    - `true`: To send reminders.
    - `false`: To disable reminders.

`user_id`
: `string` A unique identifier for the user role through which the Payment Link was created. For example, `HD1JAKCCPGDfRx`.
`whatsapp_link`
: `boolean` Whether the payment link is whatsapp link. For example, `false`.

`reminders`
: `object` Reminder dispatch state for the payment link. Contains `status` (one of `pending`, `in_progress`, `failed`).

`options`
: `array` Custom checkout options applied to this payment link (theme, prefill, etc.). Empty when none.

### Errors

The \{input field\} is required
* code: 4xx
* description: A mandatory field is empty.
* solution: Ensure all mandatory fields and values are present.

wrong input fields sent.
* code: 400
* description: When wrong input fields are sent during Payment Link creation.
* solution: Ensure that the input fields are added correctly. Refer to these [request parameters](https://razorpay.com/docs/build/llm-docs/api/payments/payment-links.md#request-parameters) on how to add correct input fields.

payment link creation with reference ID already attempted
* code: 400
* description: An existing reference id has been passed.
* solution: Ensure that a unique reference id is used for all Payment Links.

UPI Payment Links is not supported in Test Mode. Please experience the product in Live Mode.
* code: 400
* description: The UPI link parameter has been passed with the Test API keys.
* solution: Ensure that you use [Live API keys](/api/authentication#live-mode-api-keys) while passing UPI links.

upi is currently supported only in indian currency
* code: 400
* description: Occurs when you try to create a UPI Payment Link using an international currency.
* solution: Ensure that you create a UPI payment link only in indian currency.

partial payment not supported in upi link
* code: 400
* description: Occurs when you try to create a UPI Payment Link with partial payments enabled.
* solution: Please do not enable partial payments for UPI Payment Links. 

timestamp must be atleast 15 minutes in future
* code: 400
* description: The epoch time passed is less than 15 minutes from the current time.
* solution: The `close_by` time should be more than 15 minutes from the current time.

Invalid access: Cannot create a payment link in live mode, as live mode is disabled for merchant.
* code: 400
* description: Occurs when you try to create a Payment Link in Live mode, but live mode is disabled for you
* solution: Raise a request to our [support team](https://razorpay.com/support/) to get live mode enabled for you.

Invalid access: Cannot create a payment link, as Merchant is Suspended.
* code: 400
* description: Occurs when you try to create a Payment Link when you have been been suspended.
* solution: Raise a request to our [support team](https://razorpay.com/support/) to be reinstated.

value: the length must not be greater than 255.
* code: 400
* description: When the notes length is greater than 255 characters during Payment Link creation.
* solution: Please create a payment link with notes values less than 255 characters.

amount: cannot be blank.
* code: 400
* description: The request body is missing the `amount` field, or the body is empty.
* solution: Always include `amount` (in currency subunits) in the request body.

amount: amount should be minimum 100 for INR.
* code: 400
* description: The `amount` value is below the per-currency minimum. For INR, the minimum is `100` (₹1.00) in currency subunits.
* solution: Pass `amount` greater than or equal to the per-currency minimum (`100` for INR).

amount, should be a whole number for e.g. 2234 to create a payment link for INR 22.34.
* code: 400
* description: A decimal value was passed for `amount`. Amounts must be integers in currency subunits. For example, `2234` represents ₹22.34, not `22.34`.
* solution: Pass `amount` as an integer in currency subunits (paise for INR).

amount: currency: wrong input field, please find the list of supported currencies on the documentation.
* code: 400
* description: The `currency` value is not one of the supported ISO currency codes.
* solution: Use a supported 3-letter ISO currency code (for example, `INR`).

email: must be in a valid format for e.g. abcxyz@domain.com.
* code: 400
* description: The value passed for `customer.email` is not in a valid email format.
* solution: Pass `customer.email` as a valid email address.

contact: the length must be between 8 and 14.
* code: 400
* description: The `customer.contact` value is shorter than 8 characters or longer than 14 characters.
* solution: Pass `customer.contact` as a phone number between 8 and 14 characters, including the country code prefix.

incorrect JSON object received - faulty key: expire_by.
* code: 400
* description: The `expire_by` field was passed as a non-integer value (for example, an ISO date string `2024-01-01`).
* solution: Pass `expire_by` as a UNIX-epoch integer in seconds.

first_min_partial_amount must be less than or equal to amount.
* code: 400
* description: The `first_min_partial_amount` value exceeds the total `amount`. The first partial payment cannot be more than the full link amount.
* solution: Ensure `first_min_partial_amount` is less than or equal to `amount`.

first_min_partial_amount: amount should be minimum 100 for INR.
* code: 400
* description: `first_min_partial_amount` is below the per-currency minimum. Returned both when the value is below the minimum and when `accept_partial` is `false` but `first_min_partial_amount` is set.
* solution: Pass `first_min_partial_amount` greater than or equal to the per-currency minimum, and only when `accept_partial` is `true`.

reference_id: the length must be no more than 40.
* code: 400
* description: The `reference_id` value exceeds the 40-character limit.
* solution: Keep `reference_id` to 40 characters or fewer.

callback_url: URL should be sent in callback_url field.
* code: 400
* description: The value passed for `callback_url` is not a valid URL (for example, missing scheme).
* solution: Pass `callback_url` as a fully-qualified URL starting with `https://` (or `http://`).

callback_method: must be a valid value.
* code: 400
* description: The value passed for `callback_method` is not supported. Only `get` is accepted.
* solution: Set `callback_method` to `get`.

extra fields sent.
* code: 400
* description: The request body contains fields that are not part of the Payment Links API schema.
* solution: Only include documented fields. Remove any unknown keys from the request body.

customer name is a mandatory field.
* code: 400
* description: The `customer` object is present in the request but the `name` field inside it is missing or empty. Some organisations enforce customer name as mandatory.
* solution: Pass `customer.name` as a non-empty string in the request body.

expires by is a mandatory field.
* code: 400
* description: The `expire_by` field is missing from the request. Some organisations enforce `expire_by` as mandatory for payment-link creation.
* solution: Pass `expire_by` as a Unix-epoch integer at least 15 minutes in the future.
