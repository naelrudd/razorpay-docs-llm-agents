> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create an Order

> Create an Order using Razorpay Curlec Orders API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create an order with basic details such as amount and currency.

> [!WARNING]
>
> **Watch Out: Create a new order for every payment attempt**
>
> A Razorpay Curlec Order ID maps 1:1 to a payment attempt. If a customer's payment fails and they try again, you must create a new Order on your server and pass the new `order_id` to Checkout. Reusing the previous order ID will cause an error.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/orders \
-H "content-type: application/json" \
-d '{
  "amount": 5000,
  "currency": "MYR",
  "receipt": "receipt#1",
  "notes": {
    "key1": "value3",
    "key2": "value2"
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject orderRequest = new JSONObject();
orderRequest.put("amount",5000);
orderRequest.put("currency","MYR");
orderRequest.put("receipt", "receipt#1");
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_1","Tea, Earl Grey, Hot");
orderRequest.put("notes",notes);

Order order = razorpay.orders.create(orderRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.order.create({
  "amount": 5000,
  "currency": "MYR",
  "receipt": "receipt#1",
  "notes": {
    "key1": "value3",
    "key2": "value2"
  }
})
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$$api->order->create(array('receipt' => '123', 'amount' => 100, 'currency' => 'MYR', 'notes'=> array('key1'=> 'value3','key2'=> 'value2')));
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> options = new Dictionary<string,object>();
options.Add("amount", 5000); // amount in the smallest currency unit
options.Add("receipt", "order_rcptid_11");
options.Add("currency", "MYR");
Order order = client.Order.Create(options);
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {
  "amount": 5000,
  "currency": "MYR",
  "receipt": "receipt#1",
  "notes": {
    "key1": "value3",
    "key2": "value2"
  }
}

Razorpay::Order.create(para_attr)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.orders.create({
  amount: 50000,
  currency: "MYR",
  receipt: "receipt#1",
  notes: {
    key1: "value3",
    key2: "value2"
  }
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
  "amount": 5000,
  "currency": "MYR",
  "receipt": "some_receipt_id",
  "partial_payment": false,
  "notes": map[string]interface{}{
      "key1": "value1",
      "key2": "value2",
    } 
}
body, err := client.Order.Create(data, nil)
```

```bash CLI theme={null}
razorpay orders create \
  --amount 50000 \
  --currency INR \
  --receipt "receipt#001" \
  --note key1="Beam me up Scotty"
```

```json Success theme={null}
{
  "amount": 5000,
  "amount_due": 5000,
  "amount_paid": 0,
  "attempts": 0,
  "created_at": 1756455561,
  "currency": "INR",
  "entity": "order",
  "id": "order_RB58MiP5SPFYyM",
  "notes": {
      "key1": "value3",
      "key2": "value2"
  },
  "offer_id": null,
  "receipt": "receipt#1",
  "status": "created"
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "The amount must be at least MYR 1.00",
    "source": "business",
    "step": "payment_initiation",
    "reason": "input_validation_failed",
    "metadata": {},
    "field": "amount"
  }
}
```

> [!WARNING]
>
> **Watch Out: Always verify the payment signature server-side**
>
> After a payment completes, Razorpay Curlec sends `razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature` to your handler. You must verify the signature on your server before fulfilling the order.
>
> Skipping this step means anyone can fake a successful payment by sending a POST request to your callback. This is the most common cause of payment disputes and fraudulent orders.

## Request Parameters

**amount** `integer` *required*

Payment amount in the smallest currency sub-unit. For example, if the amount to be charged is , then pass `29900` in this field. In the case of three decimal currencies, such as KWD, BHD and OMR, to accept a payment of 295.991, pass the value as `295990`. And in the case of zero decimal currencies such as JPY, to accept a payment of 295, pass the value as `295`.

> [!WARNING]
>
> **Watch Out!**
>
> As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to charge a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.

**currency** `string` *required*

ISO code for the currency in which you want to accept the payment. The default length is 3 characters. Refer to the [list of supported currencies](https://razorpay.com/docs/my/payments/international-payments#malaysian-businesses).

> [!NOTE]
>
> **Handy Tips**
>
> Razorpay Curlec has added support for zero decimal currencies, such as JPY, and three decimal currencies, such as KWD, BHD, and OMR, allowing businesses to accept international payments in these currencies. Know more about Currency Conversion (May 2024).

**receipt** `string`

Receipt number that corresponds to this order, set for your internal reference. Can have a maximum length of 40 characters and has to be unique.

**notes** `json object`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

## Response Parameters

**id** `string`

The unique identifier of the order.

**amount** `integer`

The amount for which the order was created, in currency subunits. For example, for an amount of , enter `29500`.

**entity** `string`

Name of the entity. Here, it is `order`.

**amount\_paid** `integer`

The amount paid against the order.

**amount\_due** `integer`

The amount pending against the order.

**currency** `string`

ISO code for the currency in which you want to accept the payment. The default length is 3 characters.

**receipt** `string`

Receipt number that corresponds to this order. Can have a maximum length of 40 characters and has to be unique.

**status** `string`

The status of the order. Possible values:

* `created`: When you create an order it is in the `created` state. It stays in this state till a payment is attempted on it.
* `attempted`: An order moves from `created` to `attempted` state when a payment is first attempted on it. It remains in the `attempted` state till one payment associated with that order is captured.
* `paid`: After the successful capture of the payment, the order moves to the `paid` state. No further payment requests are permitted once the order moves to the `paid` state. The order stays in the `paid` state even if the payment associated with the order is refunded.

**attempts** `integer`

The number of payment attempts, successful and failed, that have been made against this order.

**notes** `json object`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

**created\_at** `integer`

Indicates the Unix timestamp when this order was created.

**offer\_id** `string`

Unique identifier of the offer associated with this order.

## Errors

> [accordion] Authentication failed.
>
> **Code:** `400`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard. Possible reasons:
>
> * Different keys for test mode and live modes.
> * Expired API key.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after the keys.

> [accordion] The amount must be at least INR 1.00.
>
> **Code:** `400`
>
> The amount specified is less than the minimum amount. Currency subunits, such as paise (in the case of INR), should always be greater than 100.
>
> **Solution:** Enter an amount equal to or greater than the minimum amount, that is 100.

> [accordion] The field name is required.
>
> **Code:** `400`
>
> A mandatory field is missing.
>
> **Solution:** Ensure all mandatory fields and values are present.

> [accordion] amount: must be no less than 0.
>
> **Code:** `400`
>
> A negative `amount` was sent in the request body.
>
> **Solution:** `amount` must be a non-negative integer.

> [accordion] The amount must be an integer.
>
> **Code:** `400`
>
> `amount` was sent as a string, float or other non-integer type.
>
> **Solution:** Pass `amount` as a JSON integer (for example, `100`, not `"100"` or `100.0`).

> [accordion] Amount exceeds maximum amount allowed.
>
> **Code:** `400`
>
> `amount` exceeds the per-order maximum configured for the account or currency.
>
> **Solution:** Check your account-level transaction limit. For large orders, split into multiple smaller orders or contact Razorpay Curlec support to raise the limit.

> [accordion] currency: validation\_failure: BAD\_REQUEST\_INVALID\_CURRENCY.
>
> **Code:** `400`
>
> An unsupported `currency` value was sent (for example, `XYZ`) or a currency that is not enabled for your account.
>
> **Solution:** Use a supported ISO-4217 currency code. To accept currencies other than your default, enable **International payments** under **Account & Settings** on the Razorpay Curlec Dashboard.

> [accordion] receipt: the length must be no more than 40.
>
> **Code:** `400`
>
> `receipt` value exceeds 40 characters.
>
> **Solution:** Keep `receipt` to 40 characters or fewer. Use an internal short id or hash if your reference is longer.

> [accordion] The receipt: validation\_failure: BAD\_REQUEST\_ENCODING\_VALIDATION\_FAILED.
>
> **Code:** `400`
>
> `receipt` contains characters outside the supported encoding (for example, emoji or non-ASCII characters).
>
> **Solution:** Use only ASCII characters in `receipt`. Restrict to alphanumerics, underscores and hyphens for maximum compatibility.

> [accordion] first\_payment\_min\_amount should be greater than or equal to 0.
>
> **Code:** `400`
>
> `first_payment_min_amount` was set to a negative value while `partial_payment: true`.
>
> **Solution:** Use a `first_payment_min_amount` that is greater than or equal to 0 and less than or equal to `amount`.

> [accordion] EOF.
>
> **Code:** `400`
>
> The request body is malformed JSON. It may be truncated, missing a closing brace or otherwise unparseable.
>
> **Solution:** Ensure the request body is valid JSON. Validate locally with `jq .` or a JSON linter before sending.

> [accordion] Duplicate request. This request has already been processed.
>
> **Code:** `400`
>
> An order with the same `receipt` value has already been created on this account. `receipt` is treated as an idempotency key, so a second create call with the same value is rejected.
>
> **Solution:** Use a unique value for `receipt` on every order, or fetch the existing order created with the same receipt and reuse it.

> [accordion] Request failed because another order operation is in progress.
>
> **Code:** `400`
>
> A concurrent create or update is already running against this order. Razorpay Curlec locks the order to prevent state corruption.
>
> **Solution:** Wait a few seconds and retry. If the issue persists, fetch the order to confirm its current state before retrying.

> [accordion] Bank code provided is invalid.
>
> **Code:** `400`
>
> For TPV (third-party validation) orders, the `bank` value passed is not a recognised IFSC bank code.
>
> **Solution:** Pass a valid 4-letter bank code (for example, `HDFC`, `ICIC`). See the supported bank codes in the Razorpay Curlec Dashboard.

> [accordion] The requested bank is not enabled for the merchant.
>
> **Code:** `400`
>
> For TPV orders, the `bank` passed is valid but not enabled on your account.
>
> **Solution:** Contact Razorpay Curlec support to enable the requested bank for your account, or pass a bank that is already enabled.

> [accordion] Bank code should be provided in input if account number is sent.
>
> **Code:** `400`
>
> For TPV orders, an `account_number` was passed without the accompanying `bank` field.
>
> **Solution:** Always pass `bank` alongside `account_number` for TPV orders.

> [accordion] Account number is mandatory for this merchant.
>
> **Code:** `400`
>
> Your account is configured to require an `account_number` on every order (TPV-enforced merchants), but the field is missing from the request.
>
> **Solution:** Include `account_number` in the order create request.
