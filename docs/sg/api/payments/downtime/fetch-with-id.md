> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch Payment Downtime Details With ID

> Fetch Payment Downtime Details With id using Razorpay Payments Downtime API.

Available in
🇮🇳 India
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to fetch downtime status if you have not received any webhook notifications due to technical issues. Usually, downtime webhook payloads are delivered within few seconds of the event. However, in some cases, this can be delayed by few minutes due to various reasons.

```bash Curl theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-X GET https://api.razorpay.com/v1/payments/downtimes/down_F1cxDoHWD4fkQt
-H "Content-Type: application/json" \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String DowntimeId = "down_F1cxDoHWD4fkQt";

Payment payment = razorpay.payments.fetchPaymentDowntimeById(DowntimeId);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.fetchPaymentDowntimeById(downtimeId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

downtimeId := "down_F1cxDoHWD4fkQt"

body, err := client.Payment.FetchPaymentDowntimeById(downtimeId, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetchPaymentDowntimeById($downtimeId);
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

downtimeId = "down_F1cxDoHWD4fkQt"

Razorpay::Payment.fetch_payment_downtime_by_id(downtimeId)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.fetchPaymentDowntimeById(downtimeId)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string downtimeId = "down_Z6t7VFTb9xHeOs";

Payment payment = client.Payment.FetchPaymentDowntimeById(downtimeId);
```

```bash CLI theme={null}
razorpay payments downtime fetch down_F1cxDoHWD4fkQt
```

```json Netbanking theme={null}
{
  "id": "down_F1cxDoHWD4fkQt",
  "method": "netbanking",
  "begin": 1591946222,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "bank": "COSB"
  },
  "created_at": 1591946223,
  "updated_at": 1591946297
}
```

```json UPI Handle theme={null}
{
  "id": "down_F8LCfthx90fMOo",
  "method": "upi",
  "begin": 1593412063,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "vpa_handle": "oksbi"
  },
  "created_at": 1593412092,
  "updated_at": 1593412092
}
```

```json UPI PSP theme={null}
{
  "id": "down_F8LCfthx90fMOo",
  "method": "upi",
  "begin": 1593412063,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "psp": "bhim",
    "flow": "collect"
  },
  "created_at": 1593412092,
  "updated_at": 1593412092
}
```

```json Turbo UPI theme={null}
{
  "id": "down_F1cxDoHWD4fkQt",
  "method": "upi",
  "begin": 1593412063,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "flow": "in_app"
  },
  "created_at": 1593412092,
  "updated_at": 1593412092
}
```

```json Card - Issuer theme={null}
{
  "id": "down_F7LroRQAAFuswd",
  "method": "card",
  "begin": 1593196031,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "issuer": "SBIN",
    "card_type": "credit"
  },
  "created_at": 1593196089,
  "updated_at": 1593196089
}
```

```json Card - Network theme={null}
{
  "id": "down_F7LroRQAAFuswd",
  "method": "card",
  "begin": 1593196031,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "network": "VISA",
    "card_type": "credit"
  },
  "created_at": 1593196089,
  "updated_at": 1593196089
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

```json Netbanking theme={null}
{
  "id": "down_F1cxDoHWD4fkQt",
  "method": "netbanking",
  "begin": 1591946222,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "vpa_handle": null,
  "instrument": {
    "bank": "COSB"
  },
  "created_at": 1591946223,
  "updated_at": 1591946297
}
```

```json UPI Handle theme={null}
{
  "id": "down_F8LCfthx90fMOo",
  "method": "upi",
  "begin": 1593412063,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "vpa_handle": "oksbi"
  },
  "created_at": 1593412092,
  "updated_at": 1593412092
}
```

```json UPI PSP theme={null}
{
  "id": "down_F8LCfthx90fMOo",
  "method": "upi",
  "begin": 1593412063,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "psp": "bhim"
  },
  "created_at": 1593412092,
  "updated_at": 1593412092
}
```

```json Card - Issuer theme={null}
{
  "id": "down_F7LroRQAAFuswd",
  "method": "card",
  "begin": 1593196031,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "issuer": "SBIN",
    "card_type": "credit"
  },
  "created_at": 1593196089,
  "updated_at": 1593196089
}
```

```json Card - Network theme={null}
{
  "id": "down_F7LroRQAAFuswd",
  "method": "card",
  "begin": 1593196031,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "network": "VISA",
    "card_type": "credit"
  },
  "created_at": 1593196089,
  "updated_at": 1593196089
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

```json FPX theme={null}
{
  "id": "down_F1cxDoHWD4fkQt",
  "method": "fpx",
  "begin": 1591946222,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "bank": "PHBM"
  },
  "created_at": 1591946223,
  "updated_at": 1591946297
}
```

```json Card - Issuer theme={null}
{
  "id": "down_F7LroRQAAFuswd",
  "method": "card",
  "begin": 1593196031,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "issuer": "HSBC",
    "card_type": "credit"
  },
  "created_at": 1593196089,
  "updated_at": 1593196089
}
```

```json Card - Network theme={null}
{
  "id": "down_F7LroRQAAFuswd",
  "method": "card",
  "begin": 1593196031,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "network": "VISA",
    "card_type": "credit"
  },
  "created_at": 1593196089,
  "updated_at": 1593196089
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

```json Card - Issuer theme={null}
{
  "id": "down_F7LroRQAAFuswd",
  "method": "card",
  "begin": 1593196031,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "issuer": "HSBC",
    "card_type": "credit"
  },
  "created_at": 1593196089,
  "updated_at": 1593196089
}
```

```json Card - Network theme={null}
{
  "id": "down_F7LroRQAAFuswd",
  "method": "card",
  "begin": 1593196031,
  "end": null,
  "status": "started",
  "scheduled": false,
  "severity": "high",
  "instrument": {
    "network": "VISA",
    "card_type": "credit"
  },
  "created_at": 1593196089,
  "updated_at": 1593196089
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

Unique identifier of the downtime.

## Response Parameters

**id** `string`

Unique identifier of the downtime's occurrence.

**entity** `string`

Here, it will be `payment.downtime`.

**method** `string`

The payment method that is experiencing the downtime. Possible values include:

* `card`
* `netbanking`
* `upi`

**begin** `integer`

Timestamp (in Unix) that indicates the start of the downtime. Applicable for both scheduled and unscheduled downtimes.

**end** `integer`

Timestamp (in Unix) that indicates the end of the downtime.\
&#x20;Available only for scheduled downtimes, where the end-time is known. Set to `null` when the end-time is unknown, possibly during unscheduled downtimes.

**status** `string`

Status of the downtime.\
Possible statuses are.

* `scheduled`: A downtime is scheduled to happen at a later time.
* `started`: The downtime has started and is ongoing.
* `resolved`: The downtime is resolved.
* `updated`: An ongoing downtime that has been updated after its start. For example, when the severity of the downtime changes from medium to high.

**scheduled** `boolean`

Possible values:

* `true`: This is a scheduled downtime by the issuer, network, or the bank, which was informed to Razorpay.
* `false`: This is an unscheduled downtime.

**severity** `string`

Severity of the downtime.\
Possible values:

* `high`: Possible when all the payment methods are affected by downtime. Observed when the issuer, bank or network is down.
* `medium`: Possible when a higher number of declines in transactions or low success rates are observed with the payment methods.
* `low`: Possible when the reason for the downtime is unknown. Impact on payment methods is minimal.

**instrument** `string`

Payment method that is underperforming.

**bank** `string`

Bank code of the affected bank. Possible values:

* `HDFC`
* `ICIC`
* `SBIN`
* `KKBK`
* `UTIB`
* `PUNB`

**network** `string`

Card network. Possible values:

* `AMEX`
* `DICL`
* `MC`
* `RUPAY`
* `VISA`
* `ALL`

**issuer** `string`

The 4-character issuer code unique to each issuing bank in India. Possible values:

* `SBIN`
* `HDFC`
* `ICIC`
* `UTIB`
* `CITI`
* `PUNB`
* `KKBK`
* `CNRB`
* `BKID`
* `BARB`
* `JAKA`
* `UBIN`

**psp** `string`

Code of the affected Payment Service Provider (PSP). This is populated only when VPA handles associated with the PSP are down. If a PSP is associated with multiple VPA handles, it is marked down only when **all** the handles associated with it are down. For example, `google_pay` is marked down only when all Google Pay handles - `oksbi`, `okhdfcbank`, `okicici` and `okaxis` are down. Possible values for this parameter are:

* `google_pay`
* `phonepe`
* `paytm`
* `bhim`

**vpa\_handle** `string`

Affected VPA handle. For example, `@oksbi`. To learn about the possible values, refer to the [list of handles supported by NPCI](https://www.npci.org.in/what-we-do/upi/3rd-party-apps). If the entire UPI system is experiencing a downtime, the value `ALL` is displayed.

**card\_type** `string`

The card type used to process the payment. Possible values:

* `credit`
* `debit`

**flow** `string`

Indicates the UPI payments flow being used during the downtime event. Possible values:

* `collect`
* `intent`
* `in_app` Only applicable for Turbo UPI payments.

**created\_at** `integer`

Timestamp (in Unix) that indicates the time at which the downtime was recorded in Razorpay servers.

**updated\_at** `integer`

Timestamp (in Unix) that indicates the time at which the downtime record was updated in Razorpay servers. \\

Know more about [the possible values](https://razorpay.com/docs/payments/payment-methods/upi.md).

## Errors

> [accordion] The API \{key/secret} provided is invalid.
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
> The downtime id passed in the URL is invalid or does not exist.
>
> **Solution:** Pass a valid downtime id (prefixed `down_`). Use `GET /v1/payments/downtimes` to list current downtime ids.
