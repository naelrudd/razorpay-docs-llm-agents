> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create an Instant Settlement

> Create an Instant Settlement using Razorpay Payments API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create an Instant Settlement.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/settlements/ondemand \
-H "content-type: application/json" \
-d '{
  "amount": 200000,
  "settle_full_balance": false,
  "description": "Need this to make vendor payments.",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject settlementRequest = new JSONObject();
settlementRequest.put("amount", 200000);
settlementRequest.put("settle_full_balance", false);
settlementRequest.put("description", "Need this to make vendor payments.");
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
settlementRequest.put("notes", notes);       

Settlement settlement = razorpay.settlement.create(settlementRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.settlement.create_ondemand_settlement({
  "amount": 200000,
  "settle_full_balance": False,
  "description": "Need this to make vendor payments.",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "amount": 200000,
  "settle_full_balance": false,
  "description": "Need this to make vendor payments.",
  "notes": map[string]interface{}{
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf.",
  },
}
body, err := client.Settlement.CreateOnDemandSettlement(data, nil)
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->settlement->createOndemandSettlement(array("amount"=> 200000, "settle_full_balance"=> false, "description"=>"Need this to make vendor payments.","notes" => array("notes_key_1"=> "Tea, Earl Grey, Hot","notes_key_2"=> "Tea, Earl Grey… decaf.")));
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

param_attr = {
  "amount": 200000,
  "settle_full_balance": 0,
  "description": "Need this to make vendor payments.",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
}
Razorpay::Settlement.create(param_attr)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.settlements.createOndemandSettlement({
  "amount": 200000,
  "settle_full_balance": false,
  "description": "Need this to make vendor payments.",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
})
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> settlementRequest = new Dictionary<string, object>();
settlementRequest.Add("amount", 100);
settlementRequest.Add("settle_full_balance", false);
settlementRequest.Add("description", "Testing");
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("notes_key_1", "Tea, Earl Grey, Hot");
notes.Add("notes_key_2", "Tea, Earl Grey� decaf.");
settlementRequest.Add("notes", notes);

Settlement settlement = client.Settlement.Create(settlementRequest);
```

```bash CLI theme={null}
razorpay settlements instant-create --amount 50000 --description "Test settlement" --note key1="note value"
```

```json Success theme={null}
{
  "id": "setlod_FNj7g2YS5J67Rz",
  "entity": "settlement.ondemand",
  "amount_requested": 200000,
  "amount_settled": 0,
  "amount_pending": 199410,
  "amount_reversed": 0,
  "fees": 590,
  "tax": 90,
  "currency": "INR",
  "settle_full_balance": false,
  "status": "initiated",
  "description": "Need this to make vendor payments.",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  },
  "created_at": 1596771429,
  "ondemand_payouts": {
    "entity": "collection",
    "count": 1,
    "items": [
      {
        "id": "setlodp_FNj7g2cbvw8ueO",
        "entity": "settlement.ondemand_payout",
        "initiated_at": null,
        "processed_at": null,
        "reversed_at": null,
        "amount": 200000,
        "amount_settled": null,
        "fees": 590,
        "tax": 90,
        "utr": null,
        "status": "created",
        "created_at": 1596771429
      }
    ]
  }
}
```

```json Failure theme={null}
{
    "error": {
        "code": "BAD_REQUEST_ERROR",
        "description": "Minimum amount that can be settled is ₹ 1.",
        "source": "NA",
        "step": "NA",
        "reason": "NA",
        "metadata": {}
    }
}
```

## Request Parameters

**amount** `integer` *required*

The amount, in paise, you want to instantly settle.

> [!TIP]
>
> **What's New**
>
> Settlement amounts of ₹1 or lower are now supported.

**settle\_full\_balance** `boolean`

Indicates whether full balance is settled. Possible values:

* `true`:  Razorpay will settle the maximum amount possible. Values passed in the `amount` parameter are ignored.
* `false` (default): Razorpay will settle the amount requested in the `amount` parameter.

**description** `string`

This is a custom note you can pass for the instant settlement for your reference. For example, `Need this to make vendor payments.`.

* Maximum length: 30 characters.
* Allowed characters: a-z, A-Z, 0-9 and space.

**notes** `object`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `Beam me up Scotty`.

## Response Parameters

**id** `string`

The unique identifier of the instant settlement transaction. For example, `setlod_FNj7g2YS5J67Rz`.

**entity** `string`

Indicates the type of entity. Here it is `settlement.ondemand`.

**amount\_requested** `integer`

The settlement amount, in paise, requested by you. For example, `200000`.

**amount\_settled** `integer`

Total amount (minus fees and tax), in paise, settled to the bank account. For example, `199410`.

**amount\_pending** `integer`

Portion of the requested amount, in paise, yet to be settled to you.

**amount\_reversed** `integer`

Portion of the requested amount, in paise, that was not settled to you. This amount is reversed to your PG current balance.

**fees** `integer`

Total amount (fees+tax), in paise, deducted for the instant settlement. For example, `590`.

**tax** `integer`

Total tax, in paise, charged for the fee component. For example, `90`.

**currency** `string`

The 3-letter ISO currency code for the settlement. Here it is `INR`.

**settle\_full\_balance** `boolean`

Indicates whether full balance is settled. Possible values:

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

The amount, in paise, settled through this payout. For example, `200000`.

**amount\_settled** `integer`

Amount (minus fees and tax), in paise, settled through this payout. For example, `199410`.

**fees** `integer`

Amount (fees+tax), in paise, deducted for this payout. For example, `590`.

**tax** `integer`

Tax charged, in paise, for the fee component. For example, `90`.

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
> **Solution:** Enable Instant Settlements from the Razorpay Dashboard before calling this API. See the Instant Settlements onboarding guide.

> [accordion] Minimum amount that can be settled is ₹ 1.
>
> **Code:** `400`
>
> The `amount` requested is below the minimum allowed for an Instant Settlement.
>
> **Solution:** Pass `amount` as an integer of at least `100` (₹ 1 in paise).

> [accordion] Minimum amount that can be settled is ₹ 2000.
>
> **Code:** `400`
>
> Returned for merchants who do not have Instant Settlements set to "automatic" mode — for such accounts, the minimum per-request amount is higher than the default.
>
> **Solution:** Pass an `amount` of at least `200000` (₹ 2,000 in paise), or contact Razorpay support to enable automatic Instant Settlements.

> [accordion] Amount requested is more than the max limit for ondemand settlement.
>
> **Code:** `400`
>
> The `amount` exceeds the per-request hard cap for Instant Settlements (₹ 5 Cr). The API may also return this as `Maximum amount that can be settled is ₹ 5 Cr.`
>
> **Solution:** Split the requested amount into multiple Instant Settlement requests, each at or below ₹ 5 Cr.

> [accordion] Amount requested for the ondemand settlement exceeds the settlement balance.
>
> **Code:** `400`
>
> The requested amount is greater than the unsettled balance available for Instant Settlement. The API may also return this as `Amount exceeds the available balance` or `Insufficient balance`.
>
> **Solution:** Check your available settlement balance from the Dashboard and request an amount within that limit.

> [accordion] Your Instant Settlements is disabled for using Money Saver.
>
> **Code:** `400`
>
> The merchant has the Money Saver / B2B Export product enabled, which is incompatible with Instant Settlements.
>
> **Solution:** Instant Settlements cannot be used in conjunction with Money Saver. Use the standard settlement cycle instead, or contact Razorpay support to discuss alternatives.

> [accordion] Please provide an amount less than 2 Lacs to get a settlement at this point of time.
>
> **Code:** `400`
>
> Instant Settlement is being requested outside banking hours, when only IMPS-based payouts are available. IMPS has a per-transaction cap of ₹ 2 lakh.
>
> **Solution:** Either lower the `amount` to ₹ 2,00,000 or below, or retry the Instant Settlement during banking hours so RTGS becomes available.

> [accordion] Currency is not supported.
>
> **Code:** `400`
>
> The `currency` field is set to a value other than the supported settlement currency.
>
> **Solution:** Use `INR` (the only currency supported for Instant Settlement at the moment).

> [accordion] Another payout operation for merchant is in progress. Please try again later.
>
> **Code:** `400`
>
> A merchant-scoped payout is currently being processed, blocking new Instant Settlement requests.
>
> **Solution:** Retry after a short delay.

> [accordion] Payout amount including fees should be greater than Re 1.
>
> **Code:** `400`
>
> The amount requested, once fees are deducted, would result in a payout below ₹ 1. The net amount sent to your bank account must exceed ₹ 1.
>
> **Solution:** Increase the requested `amount` so that the post-fee net is greater than ₹ 1.

> [accordion] Duplicate ondemand settlement request.
>
> **Code:** `400`
>
> An Instant Settlement request with the same characteristics (amount, idempotency key, or other request signature) was already submitted recently.
>
> **Solution:** If the previous request succeeded, use its response. If it failed, change the request payload or wait briefly before retrying.

> [accordion] Amount that can be settled for the day is exhausted, please try again on the next working day.
>
> **Code:** `400`
>
> The merchant's daily Instant Settlement limit has been fully consumed.
>
> **Solution:** Wait until the next working day. The daily Instant Settlement limit resets each working day.

> [accordion] Minimum amount that can be settled via smart settlement is below the threshold.
>
> **Code:** `400`
>
> For Smart Settlements, the requested `amount` is below the minimum threshold configured for the merchant. The API may return either `Minimum amount that can be settled via smart settlement is ₹ 5,00,000.` or `Minimum amount that can be settled using Smart Settlements is ₹ 2 L`, depending on the merchant configuration.
>
> **Solution:** Check the Smart Settlements minimum from your Dashboard and pass an `amount` at or above that threshold.

> [accordion] Maximum amount that can be settled using Smart Settlements is ₹ 50 Cr.
>
> **Code:** `400`
>
> For Smart Settlements, the requested `amount` is above the per-request maximum of ₹ 50 Cr.
>
> **Solution:** Split the request into multiple Smart Settlement requests, each at or below ₹ 50 Cr.

> [accordion] Smart settlements not enabled.
>
> **Code:** `400`
>
> The merchant account does not have the Smart Settlements feature enabled.
>
> **Solution:** Use the standard Instant Settlement flow, or contact Razorpay support to enable Smart Settlements.

> [accordion] The value provided for settle\_full\_balance field is invalid.
>
> **Code:** `400`
>
> The `settle_full_balance` field contains a value that is not a valid boolean.
>
> **Solution:** Pass `true` or `false` for the `settle_full_balance` field.

> [accordion] The amount should be between 100 and \{max} paise.
>
> **Code:** `400`
>
> The `amount` value is outside the allowed range when `settle_full_balance` is `false`.
>
> **Solution:** Pass an `amount` integer between `100` and the maximum allowed paise value for your account.

> [accordion] The description may not be greater than 30 characters.
>
> **Code:** `400`
>
> The `description` field exceeds the maximum allowed length of 30 characters.
>
> **Solution:** Shorten the `description` to 30 characters or fewer.

> [accordion] The value should be a valid type.
>
> **Code:** `400`
>
> The `type` field contains an invalid value.
>
> **Solution:** Use a valid type value: `settlement_payout_type_instant` or `settlement_payout_type_smart`.

> [accordion] The value should be a valid product type.
>
> **Code:** `400`
>
> The `product_type` field contains an invalid value.
>
> **Solution:** Use a valid product type value: `ondemand`, `scheduled`, or `linked`.

> [accordion] Your Instant Settlements has been disabled.
>
> **Code:** `400`
>
> Instant Settlements has been disabled for the merchant due to delayed LOC, Loan, or Card repayments.
>
> **Solution:** Clear outstanding repayments and contact Razorpay support to re-enable Instant Settlements.

> [accordion] Instant Settlements has been blocked for a while.
>
> **Code:** `400`
>
> A global on-demand settlement block is currently active for the merchant.
>
> **Solution:** Contact Razorpay support to understand the reason for the block and the steps to resolve it.

> [accordion] Requested amount is greater than available limit.
>
> **Code:** `400`
>
> The requested amount exceeds the daily merchant or global Instant Settlement limit.
>
> **Solution:** Reduce the `amount` to be within the available daily limit, or wait until the next working day when the limit resets.

> [accordion] No more attempts left for today.
>
> **Code:** `400`
>
> The merchant has exhausted the maximum number of Instant Settlement attempts allowed for the day.
>
> **Solution:** Wait until the next working day when the attempt limit resets.

> [accordion] Smart Settlement timing is 2:00 AM to 9:00 PM. Holidays are Jan 26, Aug 15 and Apr 1.
>
> **Code:** `400`
>
> The Smart Settlement request was made outside of banking hours or on a holiday when RTGS is unavailable.
>
> **Solution:** Retry the Smart Settlement between 2:00 AM and 9:00 PM on a working day (excluding Jan 26, Aug 15, and Apr 1).

> [accordion] You are not enabled for Linked Instant Settlements.
>
> **Code:** `400`
>
> The merchant account does not have the Linked Instant Settlements feature enabled.
>
> **Solution:** Contact Razorpay support to enable Linked Instant Settlements on your account.
