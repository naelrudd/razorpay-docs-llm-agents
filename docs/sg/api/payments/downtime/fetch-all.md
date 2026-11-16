> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch All Payment Downtime Details

> Fetch all payment downtime details using Razorpay Payment Downtime API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve details of all payment downtimes.

```bash Curl theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-X GET https://api.razorpay.com/v1/payments/downtimes
-H "Content-Type: application/json" \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

List<Payment> payment = razorpay.payments.fetchPaymentDowntime();
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.fetchPaymentDowntime()
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Payment.FetchPaymentDowntime(nil, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetchPaymentDowntime();
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

Razorpay::Payment.fetch_payment_downtime
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.fetchPaymentDowntime()
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

List<Payment> payment = client.Payment.FetchPaymentDowntime();
```

```bash CLI theme={null}
razorpay payments downtime list
```

```json Netbanking theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "down_F1cxDoHWD4fkQt",
      "entity": "payment.downtime",
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
    },
    {
      "id": "down_F1cxlArweEWitF",
      "entity": "payment.downtime",
      "method": "netbanking",
      "begin": 1591946222,
      "end": null,
      "status": "started",
      "scheduled": false,
      "severity": "high",
      "instrument": {
        "bank": "UTIB"
      },
      "created_at": 1591946254,
      "updated_at": 1591946298
    }
  ]
}
```

```json UPI Handle theme={null}
{
    "entity": "collection",
    "count": 1,
    "items": [
      {
        "id": "down_F8LCfthx90fMOo",
        "entity": "payment.downtime",
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
    ]
}
```

```json UPI PSP theme={null}
{
    "entity": "collection",
    "count": 1,
    "items": [
      {
        "id": "down_F8LCfthx90fMOo",
        "entity": "payment.downtime",
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
    ]
}
```

```json Turbo UPI theme={null}
{
  "entity": "collection",
  "count": 1,
  "items": [
    {
      "id": "down_F1cxDoHWD4fkQt",
      "entity": "payment.downtime",
      "method": "upi",
      "begin": 1591946222,
      "end": null,
      "status": "started",
      "scheduled": false,
      "severity": "high",
      "instrument": {
        "flow": "in_app"
      },
      "created_at": 1591946223,
      "updated_at": 1591946297
    }
  ]
}
```

```json Card - Network theme={null}
{
  "entity": "collection",
  "count": 1,
  "items": [
    {
      "id": "down_F7LroRQAAFuswd",
      "entity": "payment.downtime",
      "method": "card",
      "begin": 1593196031,
      "end": null,
      "status": "started",
      "scheduled": false,
      "severity": "high",
      "instrument": {
        "network": "VISA"
      },
      "created_at": 1593196089,
      "updated_at": 1593196089
    }
  ]
}
```

```json Card - Issuer theme={null}
{
  "entity": "collection",
  "count": 1,
  "items": [
    {
      "id": "down_F7LroRQAAFuswd",
      "entity": "payment.downtime",
      "method": "card",
      "begin": 1593196031,
      "end": null,
      "status": "started",
      "scheduled": false,
      "severity": "high",
      "instrument": {
        "issuer": "SBIN"
      },
      "created_at": 1593196089,
      "updated_at": 1593196089
    }
  ]
}
```

```json Card / Netbanking theme={null}
{
    "entity": "collection",
    "count": 2,
    "items": [
      {
        "id": "down_F7LroRQAAFuswd",
        "entity": "payment.downtime",
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
      },
      {
      "id": "down_F1cxDoHWD4fkQt",
      "entity": "payment.downtime",
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
    },
    ]
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
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "down_F1cxDoHWD4fkQt",
      "entity": "payment.downtime",
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
    },
    {
      "id": "down_F1cxlArweEWitF",
      "entity": "payment.downtime",
      "method": "netbanking",
      "begin": 1591946222,
      "end": null,
      "status": "started",
      "scheduled": false,
      "severity": "high",
      "vpa_handle": null,
      "instrument": {
        "bank": "UTBI"
      },
      "created_at": 1591946254,
      "updated_at": 1591946298
    }
  ]
}
```

```json UPI Handle theme={null}
{
  "payment_downtime": {
    "entity": "collection",
    "count": 1,
    "items": [
      {
        "id": "down_F8LCfthx90fMOo",
        "entity": "payment.downtime",
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
    ]
  }
}
```

```json UPI PSP theme={null}
{
  "payment_downtime": {
    "entity": "collection",
    "count": 1,
    "items": [
      {
        "id": "down_F8LCfthx90fMOo",
        "entity": "payment.downtime",
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
    ]
  }
}
```

```json Card - Network theme={null}
{
  "payment_downtime": {
    "entity": "collection",
    "count": 1,
    "items": [
      {
        "id": "down_F7LroRQAAFuswd",
        "entity": "payment.downtime",
        "method": "card",
        "begin": 1593196031,
        "end": null,
        "status": "started",
        "scheduled": false,
        "severity": "high",
        "instrument": {
          "network": "VISA"
        },
        "created_at": 1593196089,
        "updated_at": 1593196089
      }
    ]
  }
}
```

```json Card - Issuer theme={null}
{
  "payment_downtime": {
    "entity": "collection",
    "count": 1,
    "items": [
      {
        "id": "down_F7LroRQAAFuswd",
        "entity": "payment.downtime",
        "method": "card",
        "begin": 1593196031,
        "end": null,
        "status": "started",
        "scheduled": false,
        "severity": "high",
        "instrument": {
          "issuer": "SBIN"
        },
        "created_at": 1593196089,
        "updated_at": 1593196089
      }
    ]
  }
}
```

```json Card / Netbanking theme={null}
{
  "payment_downtime": {
    "entity": "collection",
    "count": 2,
    "items": [
      {
        "id": "down_F7LroRQAAFuswd",
        "entity": "payment.downtime",
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
      },
      {
      "id": "down_F1cxDoHWD4fkQt",
      "entity": "payment.downtime",
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
    },
    ]
  }
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
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "down_F1cxDoHWD4fkQt",
      "entity": "payment.downtime",
      "method": "fpx",
      "begin": 1591946222,
      "end": null,
      "status": "started",
      "scheduled": false,
      "severity": "high",
      "instrument": {
        "bank": "CIBB"
      },
      "created_at": 1591946223,
      "updated_at": 1591946297
    },
    {
      "id": "down_F1cxlArweEWitF",
      "entity": "payment.downtime",
      "method": "fpx",
      "begin": 1591946222,
      "end": null,
      "status": "started",
      "scheduled": false,
      "severity": "high",
      "instrument": {
        "bank": "PHBM"
      },
      "created_at": 1591946254,
      "updated_at": 1591946298
    }
  ]
}
```

```json Card - Network theme={null}
{
  "payment_downtime": {
    "entity": "collection",
    "count": 1,
    "items": [
      {
        "id": "down_F7LroRQAAFuswd",
        "entity": "payment.downtime",
        "method": "card",
        "begin": 1593196031,
        "end": null,
        "status": "started",
        "scheduled": false,
        "severity": "high",
        "instrument": {
          "network": "VISA"
        },
        "created_at": 1593196089,
        "updated_at": 1593196089
      }
    ]
  }
}
```

```json Card - Issuer theme={null}
{
  "payment_downtime": {
    "entity": "collection",
    "count": 1,
    "items": [
      {
        "id": "down_F7LroRQAAFuswd",
        "entity": "payment.downtime",
        "method": "card",
        "begin": 1593196031,
        "end": null,
        "status": "started",
        "scheduled": false,
        "severity": "high",
        "instrument": {
          "issuer": "HSBC"
        },
        "created_at": 1593196089,
        "updated_at": 1593196089
      }
    ]
  }
}
```

```json Card / FPX theme={null}
{
  "payment_downtime": {
    "entity": "collection",
    "count": 2,
    "items": [
      {
        "id": "down_F7LroRQAAFuswd",
        "entity": "payment.downtime",
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
      },
      {
      "id": "down_F1cxDoHWD4fkQt",
      "entity": "payment.downtime",
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
    },
    ]
  }
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

```json Card - Network theme={null}
{
  "payment_downtime": {
    "entity": "collection",
    "count": 1,
    "items": [
      {
        "id": "down_F7LroRQAAFuswd",
        "entity": "payment.downtime",
        "method": "card",
        "begin": 1593196031,
        "end": null,
        "status": "started",
        "scheduled": false,
        "severity": "high",
        "instrument": {
          "network": "VISA"
        },
        "created_at": 1593196089,
        "updated_at": 1593196089
      }
    ]
  }
}
```

```json Card - Issuer theme={null}
{
  "payment_downtime": {
    "entity": "collection",
    "count": 1,
    "items": [
      {
        "id": "down_F7LroRQAAFuswd",
        "entity": "payment.downtime",
        "method": "card",
        "begin": 1593196031,
        "end": null,
        "status": "started",
        "scheduled": false,
        "severity": "high",
        "instrument": {
          "issuer": "HSBC"
        },
        "created_at": 1593196089,
        "updated_at": 1593196089
      }
    ]
  }
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

> [accordion] Extra query parameters were sent in the request.
>
> **Code:** `400`
>
> An unsupported query parameter was included in the request. The Downtime list endpoint does not accept pagination or filtering parameters.
>
> **Solution:** Call `GET /v1/payments/downtimes` without any query parameters. The endpoint returns the full current collection.
