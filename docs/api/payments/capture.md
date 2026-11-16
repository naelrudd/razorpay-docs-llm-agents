> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Capture a Payment

> Create a Payment using Razorpay Payments API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to change the payment status from `authorized` to `captured`. Attempting to capture a payment whose status is not `authorized` will produce an error.

* After the customer's bank authorises the payment, you must verify if the authorised amount deducted from the customer's account is the same as the amount paid by the customer on your website or app.
* You can [configure automatic capture](https://razorpay.com/docs/payments/payments/capture-settings.md#auto-capture-all-payments) of payments on the Dashboard.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-H 'content-type: application/json' \
-X POST https://api.razorpay.com/v1/payments/pay_29QQoUBi66xm2f/capture \
-d '{
  "amount": 1000,
  "currency": "INR"
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_29QQoUBi66xm2f";

JSONObject paymentRequest = new JSONObject();
paymentRequest.put("amount", 1000);
paymentRequest.put("currency", "INR");

Payment payment = razorpay.payments.capture(paymentId, paymentRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.capture(paymentId,{
  "amount" : 1000,
  "currency" : "INR"
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

paymentId := "pay_29QQoUBi66xm2f"
amount := 1000

data := map[string]interface{}{
  "currency": "INR",
}

body, err := client.Payment.Capture(paymentId, amount, data, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetch($paymentId)->capture(array('amount'=>$amount,'currency' => 'INR'));
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymentId = "pay_29QQoUBi66xm2f"

para_attr = {
    "amount": 1000,
    "currency" : "INR"
}
Razorpay::Payment.capture(paymentId, para_attr)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.capture(pay_29QQoUBi66xm2f, 1000, INR)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
Payment payment = client.Payment.Fetch(paymentId);

Dictionary<`string`, object> options = new Dictionary<`string`, object>();
options.Add("amount", "<amount>");
options.Add ("currency", "INR");
Payment paymentCaptured = payment.Capture(options);
```

```bash CLI theme={null}
razorpay payments capture pay_ABC123 --amount 50000 --currency INR
```

```json Success theme={null}
{
  "id": "pay_G3P9vcIhRs3NV4",
  "entity": "payment",
  "amount": 1000,
  "currency": "INR",
  "status": "captured",
  "order_id": "order_GjCr5oKh4AVC51",
  "invoice_id": null,
  "international": false,
  "method": "card",
  "amount_refunded": 0,
  "refund_status": null,
  "captured": true,
  "description": "Payment for Adidas shoes",
  "card_id": "card_KOdY30ajbuyOYN",
  "bank": null,
  "wallet": null,
  "vpa": null,
  "email": "gaurav.kumar@example.com",
  "contact": "9000090000",
  "customer_id": "cust_K6fNE0WJZWGqtN",
  "token_id": "token_KOdY$DBYQOv08n",
  "notes": [],
  "fee": 1,
  "tax": 0,
  "error_code": null,
  "error_description": null,
  "error_source": null,
  "error_step": null,
  "error_reason": null,
  "acquirer_data": {
    "authentication_reference_number": "100222021120200000000742753928"
  },
  "created_at": 1605871409,
  "provider": null,
  "upi": {
      "payer_account_type": "credit_card",
      "vpa": "gaurav.kumar@examplebank",
      "flow": "intent"
  },
  "reward": null
}
```

```json Failure theme={null}
{
    "error": {
        "code": "BAD_REQUEST_ERROR",
        "description": "The amount must be an integer.",
        "source": "business",
        "step": "payment_initiation",
        "reason": "input_validation_failed",
        "metadata": {},
        "field": "amount"
    }
}
```

## Path Parameters

**id** `string` *required*

Unique identifier of the payment to be captured.

## Request Parameters

**amount** `integer` *required*

The amount to be captured (should be equal to  the order amount, in the smallest unit of the currency). While creating a capture request, in the `amount` field, enter only the amount associated with the order that is stored in your database.

**currency** `string` *required*

ISO code of the currency in which the payment was made. Refer to the [list of supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).

> [!NOTE]
>
> **Handy Tips**
>
> Razorpay has added support for zero decimal currencies, such as JPY, and three decimal currencies, such as KWD, BHD, and OMR, allowing businesses to accept international payments in these currencies. Know more about [Currency Conversion](https://razorpay.com/docs/payments/international-payments/currency-conversion.md) (May 2024).

## Response Parameters

**id** `string`

Unique identifier of the payment.

**entity** `string`

Indicates the type of entity.

**amount** `integer`

The payment amount in currency subunits. For example, for an amount of ₹1 enter 100.

**currency** `string`

The currency in which the payment is made. Refer to the list of [international currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies) that we support.

**status** `string`

The status of the payment. Possible values:

* `created`
* `authorized`
* `captured`
* `refunded`
* `failed`

**method** `string`

The payment method used for making the payment. Possible values:

* `card`
* `netbanking`
* `wallet`
* `emi`
* `upi`

**order\_id** `string`

Order id, if provided. Know more about [Orders](https://razorpay.com/docs/payments/orders).

**description** `string`

Description of the payment, if any.

**international** `boolean`

Indicates whether the payment is done via an international card or a domestic one. Possible values:

* `true`: Payment made using international card.
* `false`: Payment not made using international card.

**refund\_status** `string`

The refund status of the payment. Possible values:

* `null`
* `partial`
* `full`

**amount\_refunded** `integer`

The amount refunded in currency subunits. For example, if `amount_refunded = 100`, it is equal to ₹1.

**captured** `boolean`

Indicates if the payment is captured. Possible values:

* `true`: Payment has been captured.
* `false`: Payment has not been captured.

**email** `string`

Customer email address used for the payment.

**contact** `string`

Customer contact number used for the payment.

**fee** `integer`

Fee (including GST) charged by Razorpay.

**tax** `integer`

GST charged for the payment.

**error\_code** `string`

Error that occurred during payment. For example, `BAD_REQUEST_ERROR`.

**error\_description** `string`

Description of the error that occurred during payment. For example, `Payment processing failed because of incorrect OTP`.

**error\_source** `string`

The point of failure. For example, `customer`.

**error\_step** `string`

The stage where the transaction failure occurred. The stages can vary depending on the payment method used to complete the transaction. For example, `payment_authentication`.

**error\_reason** `string`

The exact error reason. For example, `incorrect_otp`.

**notes** `json object`

Contains user-defined fields, stored for reference purposes.

**created\_at** `integer`

Timestamp, in UNIX format, on which the payment was created.

**card\_id** `string`

The unique identifier of the card used by the customer to make the payment.

**card** `object`

Details of the card used to make the payment.

**id** `string`

The unique identifier of the card used by the customer to make the payment.

**entity** `string`

The name of the entity. Here, it is `card`.

**name** `string`

Name of the cardholder.

**last4** `integer`

The last 4 digits of the card number.

**network** `string`

The card network. Possible values:

* `American Express`
* `Diners Club` (Only available for private limited and registered businesses)
* `Maestro`
* `MasterCard`
* `RuPay`
* `Unknown`
* `Visa`

**type** `string`

The card type. Possible values:

* `credit`
* `debit`
* `prepaid`
* `unknown`

**issuer** `string`

The card issuer. The 4-character code denotes the issuing bank. This attribute will not be set for the card issued by a foreign bank.

**emi** `boolean`

Indicates whether the card can be used for EMI payment method. Possible values:

* `true`: Card can be used for EMI payments.
* `false`: Card cannot be used for EMI payments.

**sub\_type** `string`

The sub-type of the customer's card. Possible values:

* `customer`
* `business`\\

Know how to accept payments made by customers using [corporate cards](https://razorpay.com/docs/payments/payment-methods/cards/corporate-cards).

**upi** `object`

Details of the UPI payment received. Only applicable if `method` is `upi`.

**payer\_account\_type** `string`

The payment method used for making the payment. Possible values:

* `bank_account`
* `credit_card`
* `wallet`
* `credit_line`

**vpa** `string`

The customer's VPA (Virtual Payment Address) or UPI id used to make the payment. For example, `gauravkumar@exampleupi`.

**flow** `string`

The type of UPI flow. Possible values:

* `intent`: When a UPI app is selected and user is redirected to it.
* `collect`: The user enters their UPI ID and receives a notification from the UPI app. They open the app and complete the payment.
* `in_app` In case of Turbo UPI Payments.

**bank** `string`

The 4-character bank code which the customer's account is associated with. For example, `UTIB` for Axis Bank.

**vpa** `string`

The customer's VPA (Virtual Payment Address) or UPI id used to make the payment. For example, `gauravkumar@exampleupi`.

**wallet** `string`

The name of the wallet used by the customer to make the payment. For example, `payzapp`.

**acquirer\_data** `array`

A dynamic array consisting of a unique reference numbers.

**rrn** `string`

A unique bank reference number provided by the banking partner when a refund is processed. This reference number can be used by the customer to track the status of the refund with the bank.

**authentication\_reference\_number** `string`

A unique reference number generated for RuPay card payments.

**bank\_transaction\_id** `string`

A unique reference number provided by the banking partner in case of netbanking payments.

## Errors

> [accordion] The API `\<key/secret\>
> ` provided is invalid.
>
> **Code:** `4xx`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after.

> [accordion] Capture amount must be equal to the amount authorized.
>
> **Code:** `400`
>
> * The capture amount is incorrect.
> * The amount you are trying to capture differs from the authorised amount .
>
> **Solution:**
>
> * Enter the correct capture amount.
> * Ensure that the amount to be captured is equal to the authorised amount.

> [accordion] Your payment has been declined as the order is already paid. Please initiate the payment with a new order.
>
> **Code:** `400`
>
> This payment has already been captured.
>
> **Solution:** Ensure that the payment is in the `authorized` state to capture it successfully.

> [accordion] The id provided does not exist
>
> **Code:** `400`
>
> The `payment_id` provided is incorrect.
>
> **Solution:** Enter the correct `payment_id`.

> [accordion] The requested URL was not found on the server.
>
> **Code:** `400`
>
> The URL is incorrect.
>
> **Solution:** Use the correct URL.

> [accordion] The amount must be an integer
>
> **Code:** `400`
>
> The amount specified is incorrect.
>
> **Solution:** Enter the correct amount without any decimal points.

> [accordion] Could not validate payment capture request due to: amount: cannot be blank.
>
> **Code:** `400`
>
> The `amount` field was omitted from the capture request body.
>
> **Solution:** Always include `amount` (in currency subunits) in the capture request body.

> [accordion] Could not validate payment capture request due to: amount: required key is missing.
>
> **Code:** `400`
>
> The capture request body is empty or missing the `amount` key.
>
> **Solution:** Send a JSON body containing both `amount` and `currency`.

> [accordion] Capture request currency must be same as payment currency.
>
> **Code:** `400`
>
> The `currency` passed in the capture request does not match the currency of the underlying payment.
>
> **Solution:** Pass the same `currency` that was used when the payment was created. Capture currency cannot be changed.

> [accordion] The payment has already been either captured or voided.
>
> **Code:** `400`
>
> A capture was attempted on a payment that has already moved out of the `authorized` state. It is either already captured or has been voided.
>
> **Solution:** Fetch the payment using `GET /v1/payments/:id` and check `status`. Only retry capture if the payment is still in `authorized` state.

> [accordion] Payment is not in authorized state.
>
> **Code:** `400`
>
> Capture can only be performed on payments in the `authorized` state. The payment is currently in a different state (`failed`, `created`, `refunded` or already `captured`).
>
> **Solution:** Confirm the payment status using the Fetch Payment API before capturing.

> [accordion] Only payments which have been authorized and not yet captured can be captured.
>
> **Code:** `400`
>
> The payment is not in a captureable state. This message surfaces for payments that have already settled, been voided or failed.
>
> **Solution:** Inspect the payment status. Only `authorized` payments are eligible for capture.

> [accordion] Payment is pending authorization from approver.
>
> **Code:** `400`
>
> For corporate-card payments and other approval-flow gateways, the payment is waiting for an internal approver and is not yet authorised.
>
> **Solution:** Wait for the approver to complete the authorisation. Retry capture once `status` moves to `authorized`.

> [accordion] Payment amount is greater than the amount due for order.
>
> **Code:** `400`
>
> The capture amount exceeds the order's outstanding `amount_due`. This typically happens when partial payments have already been captured on the order.
>
> **Solution:** Capture an amount less than or equal to the order's `amount_due`. Fetch the order to confirm the remaining due amount.

> [accordion] Payment already done for this order.
>
> **Code:** `400`
>
> The order linked to this payment is already in the `paid` state. Another payment has already been captured against it.
>
> **Solution:** Create a new order for the next transaction. An order in the `paid` state cannot accept additional captures.

> [accordion] Request failed because another payment operation is in progress.
>
> **Code:** `400`
>
> A concurrent operation (another capture or a refund) is already running for this payment.
>
> **Solution:** Wait a few seconds and retry. Fetch the payment to confirm its current state before retrying.

> [accordion] The payment has already been processed.
>
> **Code:** `400`
>
> The payment has already moved to a final state (such as `captured` or `refunded`) and cannot be processed again.
>
> **Solution:** Use the Fetch Payment API to check the current status. No further capture is required.
