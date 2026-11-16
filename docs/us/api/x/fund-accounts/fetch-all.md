> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch All Fund Accounts

> Fetch all Fund Accounts using API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to retrieve all fund accounts.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET https://api.razorpay.com/v1/fund_accounts
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 3,
  "items": [
  {
  "id": "fa_00000000000001",
  "entity": "fund_account",
  "contact_id": "cont_00000000000001",
  "account_type": "bank_account",
  "bank_account": {
    "ifsc": "HDFC0000053",
    "bank_name": "HDFC Bank",
    "name": "Gaurav Kumar",
    "account_number": "765432123456789",
    "notes": []
  },
  "active": false,
  "batch_id": null,
  "created_at": 1545312598
  },
  {
  "id": "fa_00000000000002",
  "entity": "fund_account",
  "contact_id": "cont_00000000000001",
  "account_type": "vpa",
  "vpa": {
    "username": "gaurav.kumar",
    "handle": "exampleupi",
    "address": "gaurav.kumar@exampleupi"
  },
  "active": true,
  "batch_id": null,
  "created_at": 1545313478
  },
  {
  "id": "fa_00000000000001",
  "entity": "fund_account",
  "contact_id": "cont_00000000000001",
  "account_type": "card",
  "card": {
    "name": "Gaurav Kumar",
    "last4": "6789",
    "network": "Visa",
    "type": "credit",
    "issuer": "HDFC"
  },
  "active": false,
  "batch_id": null,
  "created_at": 1545312598
  }
 ]
}
```

## Query Parameters

**account\_type** `string`

The fund account type to be retrieved. Possible values:

* `bank_account`
* `vpa`
* `card` (if [payouts to cards](https://razorpay.com/docs/x/payouts/cards.md) is enabled on your account)

**contact\_id** `string`

The unique contact ID for which fund accounts are to be retrieved. For example, `cont_00000000000001`.

**from** `integer`

Timestamp, in Unix, from when fund accounts are to be retrieved.

**to** `integer`

Timestamp, in Unix, till when fund accounts are to be retrieved.

**count** `integer`

The number of fund accounts to be retrieved. Default = `10`. Maximum = `100`. This can be used for pagination, in combination with `skip`.

**skip** `integer`

The number of fund accounts to be skipped. Default = `0`. This can be used for pagination, in combination with `count`.

## Response Parameters

**id** `string`

The unique identifier linked to the fund account validation. For example, `fav_0000000001`.

**entity** `string`

Here it is `fund_account.validation`.

**status** `string`

The status of the account validation transaction.
Possible values:

* `created`
* `completed`
* `failed`

**validation\_results** `object`

Details extracted from the results of the fund account validation.

**account\_status** `string`

Displays if the account is valid or not.
Possible values:

* `active`
* `invalid`

**registered\_name** `string`

The name linked to the account. For example,`Gaurav Kumar` or `null`.

**details** `string`

Brief description of the validation.

**name\_match\_score** `string`

The percentage score indicating how closely the account holder's name matches the records.

**validated\_account\_type** `string`

Here it is `bank_account`.

**bank\_account** `object`

The contact's bank account details.

**bank\_routing\_code** `string`

Beneficiary bank IFSC. For example, `HDFC0000053`.

**account\_number** `string`

Beneficiary account number. For example, `765432123456789`.

**bank\_name** `string`

The contact's bank name. For example, `HDFC`.

**account\_type** `string`

The account type being validated. For example `savings`, `current`.

**status\_details** `object`

Status of the fund account validation.

**description** `string`

A brief description stating if the validation is complete or not.

**source** `string`

The source from which validation was done. For example, `beneficiary_bank`

**reason** `string`

Reason for validation.

**reference\_id** `string`

Unique reference\_id generated for the validation transaction.

**fund\_account** `object`

The details of the fund account which was validated.

**id** `string`

The unique identifier linked to the fund account. For example, `fa_00000000000001`.

**entity** `string`

Here it is `fund_account`.

**account\_type** `string`

Fund account type.

**vpa** `object`

The details associated with the account holder's virtual payment address.

**address** `string`

The virtual payment address of the contact whose account is validated. For example, `gaurav.kumar@exampleupi`

**active** `boolean`

Possible values of fund account status:

* `true`: active
* `false`: inactive

**created\_at** `integer`

Timestamp, in unix, when the fund account was created. For example, `1543650891`.

**contact** `object`

The contact's details.

**id** `string`

The unique identifier linked to the contact. For example, `cont_00000000000001`.

**entity** `string`

Here it is `contact`

**name** `string`

Account holder's name. For example,`Gaurav Kumar`.

**email** `string`

Email address of the contact.

**contact** `string`

Phone number of the contact.

**type** `string`

Contact Type. For example, `employee`, `contractor`.

**reference\_id** `string`

Reference id associated with the contact.

**active** `boolean`

Possible values of contact status:

* `true`: active
* `false`: inactive

## Errors

> [accordion] `\<fund account id\>
> ` is not a valid id.
>
> **Code:** `4xx`
>
> The fund account ID entered is invalid.
>
> **Solution:** Re-check or find the Fund Account ID:
>
> * In the response body of [create a Fund Account](https://razorpay.com/docs/api/x/fund-accounts.md) API.
> * On the [RazorpayX Dashboard](https://x.razorpay.com/auth).
