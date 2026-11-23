> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Modify Settlement Hold for Transfers

> Modify Settlement Hold for Transfers using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇺🇸 United States

Use this endpoint to modify the settlement configuration for a particular `transfer_id`.

* Set `on_hold` to `true` to put the settlement on hold. When a settlement is on hold, the funds are not settled to the Linked Account even after the settlement schedule is complete.

* Set `on_hold` to `false` to release the settlement.

* Use `on_hold_until` to specify the time until which the settlement must remain on hold. If no value is passed, the settlement is put on hold indefinitely.

```bash Curl theme={null}
curl -X PATCH https://api.razorpay.com/v1/transfers/trf_JJD536GI6wuz3m \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-H 'content-type: application/json' \
-d '{
  "on_hold": true,
  "on_hold_until": 1679691505
}'
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.transfers.edit(transferId,{
  "on_hold": true,
  "on_hold_until": "1679691505"
})
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.transfer.edit(transferId,{
  "on_hold": True,
  "on_hold_until": "1679691505"
})
```

```json Success theme={null}
{
  "id": "trf_JJD536GI6wuz3m",
  "entity": "transfer",
  "status": "processed",
  "source": "pay_JGmCgTEa9OTQcX",
  "recipient": "acc_IRQWUleX4BqvYn",
  "amount": 300,
  "currency": "MYR",
  "amount_reversed": 0,
  "fees": 1,
  "tax": 0,
  "notes": {
    "name": "Nur Aisyah",
    "roll_no": "IEC2011026"
  },
  "linked_account_notes": ["roll_no"],
  "on_hold": true,
  "on_hold_until": 1649971331,
  "settlement_status": "on_hold",
  "recipient_settlement_id": null,
  "created_at": 1649933574,
  "processed_at": 1649933579,
  "error": {
    "code": null,
    "description": null,
    "reason": null,
    "field": null,
    "step": null,
    "id": "trf_JJD536GI6wuz3m",
    "source": null,
    "metadata": null
  }
}
```

```json Failure theme={null}
{
   "error":{
      "code":"BAD_REQUEST_ERROR",
      "description":"The api key provided is invalid",
      "source":"NA",
      "step":"NA",
      "reason":"NA",
      "metadata":{

      }
   }
}
```

## Path Parameters

**id** `string` *required*

Unique identifier of the transfer for which the settlement configuration should be modified.

## Request Parameters

**on\_hold** `boolean` *required*

Indicates whether the account settlement for the transfer is on hold. Possible values:

* `true`: Puts the settlement on hold.
* `false`: Releases the settlement.

**on\_hold\_until** `integer`

Timestamp, in Unix format, indicates until when the settlement of the transfer must be put on hold. If no value is passed, the settlement is put on hold indefinitely. The settlement is processed on the next working day after the hold expires.

## Response Parameters

**id** `string`

Unique identifier of the transfer.

**entity** `string`

The name of the entity. Here, it is `transfer`.

**status** `string`

The status of the transfer. Possible values are:

* `created`
* `pending`
* `processed`
* `failed`
* `reversed`
* `partially_reversed`

**settlement\_status** `string`

The status of the settlement. Possible values are:

* `pending`
* `on_hold`
* `settled`

**source** `string`

Unique identifier of the transfer source. The source can be a `payment` or an `order`.

**recipient** `string`

Unique identifier of the transfer destination, that is, the Linked Account.

**amount** `integer`

The amount to be transferred to the Linked Account, in sen. For example, for an amount of RM200.35, the value of this field should be 20035.

**currency** `string`

ISO currency code. We support route transfers only in `MYR`.

**amount\_reversed** `integer`

Amount reversed from this transfer for refunds.

**notes** `json object`

Set of key-value pairs that can be associated with an entity. These pairs can be useful for storing additional information about the entity. A maximum of 15 key-value pairs, each of 256 characters (maximum), are supported.

**linked\_account\_notes** `array`

List of keys from the `notes` object which needs to be shown to Linked Accounts on their Dashboard. For example, `"region", "city"`. Only the keys will be shown, not values.

**on\_hold** `boolean`

Indicates whether the account settlement for transfer is on hold. Possible values:

* `true`: Puts the settlement on hold.
* `false`: Releases the settlement.

**on\_hold\_until** `integer`

Timestamp, in Unix format, indicates until when the settlement of the transfer must be put on hold. If no value is passed, the settlement is put on hold indefinitely.

**recipient\_settlement\_id** `string`

Unique identifier of the settlement.

**created\_at** `integer`

Timestamp, in Unix, at which the record was created.

**error** `object`

Provides error details that may occur during the transfer.

## Errors

> [accordion] The api key/secret provided is invalid
>
> **Code:** `4xx`
>
> This error occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
>
> **Solution:** Make sure the API Keys are active and entered correctly. Also, there should not be any whitespaces before or after the keys.

> [accordion] transfer\_id is not a valid id
>
> **Code:** `400`
>
> This error occurs when you pass an invalid `transfer_id` in the API endpoint.
>
> **Solution:** Make sure to pass a valid `transfer_id`.
