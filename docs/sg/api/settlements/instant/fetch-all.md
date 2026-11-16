> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch All Instant Settlements

> Fetch All Instant Settlements using Razorpay Payments API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve the details of all Instant Settlements.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]\
- X GET \
https://api.razorpay.com/v1/settlements/ondemand
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

List<Settlement> settlement = razorpay.settlement.fetchAllDemand(options)
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.settlement.fetch_all_ondemand_settlement(options)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {"count":1}

Razorpay::Settlement.fetch_all_ondemand_settlement(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Settlement.FetchAllOnDemandSettlement(options, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->settlement->fetchAllOndemandSettlement($options);
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.settlements.fetchAllOndemandSettlement(options)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

List<Settlement> settlement = client.Settlement.FetchAllDemand();
```

```bash CLI theme={null}
razorpay settlements instant-list --count 10 --skip 0
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
    {
      "id": "setlod_FNj7g2YS5J67Rz",
      "entity": "settlement.ondemand",
      "amount_requested": 200000,
      "amount_settled": 199410,
      "amount_pending": 0,
      "amount_reversed": 0,
      "fees": 590,
      "tax": 90,
      "currency": "SGD",
      "settle_full_balance": false,
      "status": "processed",
      "description": "Need this to make vendor payments.",
      "notes": {
        "notes_key_1": "Tea, Earl Grey, Hot",
        "notes_key_2": "Tea, Earl Grey, decaf."
      },
      "created_at": 1596771429
    },
    {
      "id": "setlod_FJOp0jOWlalIvt",
      "entity": "settlement.ondemand",
      "amount_requested": 300000,
      "amount_settled": 299114,
      "amount_pending": 0,
      "amount_reversed": 0,
      "fees": 886,
      "tax": 136,
      "currency": "SGD",
      "settle_full_balance": false,
      "status": "processed",
      "description": "Need this to buy stock.",
      "notes": {
        "notes_key_1": "Tea, Earl Grey, Hot",
        "notes_key_2": "Tea, Earl Grey, decaf."
      },
      "created_at": 1595826576
    }
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

## Response Parameters

**id** `string`

The unique identifier of the instant settlement transaction. For example, `setlod_FNj7g2YS5J67Rz`.

**entity** `string`

Indicates the type of entity. Here it is `settlement.ondemand`.

**amount\_requested** `integer`

The settlement amount, in cents, requested by you. For example, `200000`.

**amount\_settled** `integer`

Total amount (minus fees and tax), in cents, settled to the bank account. For example, `199410`.

**amount\_pending** `integer`

Portion of the requested amount, in cents, yet to be settled to you.

**amount\_reversed** `integer`

Portion of the requested amount, in cents, that was not settled to you. This amount is reversed to your PG current balance.

**fees** `integer`

Total amount (fees+tax), in cents, deducted for the instant settlement. For example, `590`.

**tax** `integer`

Total tax, in cents, charged for the fee component. For example, `90`.

**currency** `string`

The 3-letter ISO currency code for the settlement. Here it is `SGD`.

**settle\_full\_balance** `boolean`

Possible values:

* `true`:  Razorpay will settle the maximum amount possible. Values passed in the `amount` parameter are ignored.
* `false` (default): Razorpay will settle the amount requested in the `amount` parameter.

**status** `string`

Indicates the state of the instant settlement. Possible values:

* `created`: The instant settlement request has been created.
* `initiated`: The instant settlement process has been initiated.
* `partially_processed`: The instant settlement is being processed.
* `processed`: The instant settlement has been processed and the amount has been transferred to your bank account.
* `reversed`: The instant settlement could not be processed for some reason and the amount has been transferred back to your PG balance.

**description** `string`

This is a custom note you can pass for the instant settlement for your reference. For example, `Need this to make vendor payments.`.

**notes** `object`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

**created\_at** `integer`

Unix timestamp at which the instant settlement was created. For example, `1596771429`.

**ondemand\_payouts** `object`

List of payouts created for the instant settlement.

**entity** `string`

Indicates the type of `ondemand_payouts` entity. Here it is `collection`.

**count** `integer`

The number of items in the array. For example, `1`.

**items** `array`

List of payouts created for the instant settlement.

**id** `string`

The unique identifier for the payout. For example, `setlodp_FNj7g2cbvw8ueO`.

**entity** `string`

Indicates the type of `items` entity. Here it is `settlement.ondemand_payout`.

**initiated\_at** `integer`

Unix timestamp at which the payout was initiated. For example, `1596771430`.

**processed\_at** `integer`

Unix timestamp at which the payout was processed. For example, `1596778752`.

**reversed\_at** `integer`

Unix timestamp at which the payout was reversed. For example, `1596778752`.

**amount** `integer`

The amount, in cents, settled through this payout. For example, `200000`.

**amount\_settled** `integer`

Amount (minus fees and tax), in cents, settled through this payout. For example, `199410`.

**fees** `integer`

Amount (fees+tax), in cents, deducted for this payout. For example, `590`.

**tax** `integer`

Tax charged, in cents, for the fee component. For example, `90`.

**utr** `string`

The unique transaction number linked to a payout.

**status** `string`

Status of the payout. Possible values:

* `created`: The payout has been created.
* `initiated`: The payout has been initiated.
* `processed`: The payout has been processed. The amount has been transferred to your bank account.
* `reversed`: The payout has been reversed. The amount has been transferred back to your PG balance.

**created\_at** `integer`

Unix timestamp at which the payout was created.

## Errors

> [accordion] The API \{key/secret} provided is invalid.
>
> **Code:** `4xx`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after.

> [accordion] The requested URL was not found on the server.
>
> **Code:** `400`
>
> Instant Settlement is not enabled on the merchant account, so the endpoint is not routable.
>
> **Solution:** Enable Instant Settlements from the Razorpay Dashboard before calling this API.

> [accordion] The expand array must contain 'ondemand\_payouts'.
>
> **Code:** `400`
>
> The `expand[]` parameter contains an invalid value.
>
> **Solution:** Pass `expand[]=ondemand_payouts` as the only supported expand option for this endpoint.
