> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payment Downtime Entity

> Know about the Payment Downtime entity parameters and their description.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

The Downtime entity has the following parameters:

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

**id** `string`

Unique identifier of the downtime's occurrence.

**entity** `string`

Here, it will be `payment.downtime`.

**method** `string`

The payment method that is experiencing downtime. Possible values include:

* `card`
* `paynow`

**begin** `integer`

Timestamp (in Unix) that indicates the start of the downtime. Applicable for both scheduled and unscheduled downtimes.

**end** `integer`

Timestamp (in Unix) that indicates the end of the downtime.\
&#x20;Available only for scheduled downtimes, where the end-time is known. Set to `null` when the end-time is unknown, possibly during unscheduled downtimes.

**status** `string`

Status of the downtime. Possible statuses:

* `scheduled`: A downtime is scheduled to happen at a later time.
* `started`: The downtime has started and is ongoing.
* `resolved`: The downtime is resolved.
* `updated`: An ongoing downtime that has been updated after its start. For example, when the severity of the downtime changes from medium to high.

**scheduled** `boolean`

Indicates if the downtime is scheduled or unscheduled. Possible values:

* `true`: This is a scheduled downtime by the issuer, network, or the bank, which was informed to Razorpay.
* `false`: This is an unscheduled downtime.

**severity** `string`

Severity of the downtime. Possible values:

* `high`: Possible when all the payment methods are affected by downtime. Observed when the issuer, bank or network is down.
* `medium`: Possible when a higher number of declines in transactions or low success rates are observed with the payment methods.
* `low`: Possible when the reason for the downtime is unknown. Impact on payment methods is minimal.

**instrument** `string`

Payment method that is underperforming.

**issuer** `string`

Issuer bank code. For example, `HSBC`.

**network** `string`

Card network. Possible values:

* `MasterCard`
* `VISA`
* `UnionPay`
* `Amex`

**created\_at** `integer`

Timestamp (in Unix) that indicates the time at which the downtime was recorded in Razorpay servers.

**updated\_at** `integer`

Timestamp (in Unix) that indicates the time at which the downtime record was updated in Razorpay servers.

**card\_type** `string`

The card type used to process the payment. Possible values:

* `credit`
* `debit`
