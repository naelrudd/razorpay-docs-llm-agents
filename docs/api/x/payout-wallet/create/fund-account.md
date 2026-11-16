> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Fund Account of Type Wallet

> Create a Fund Account of type the wallet via API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create a Fund Account of the type `wallet`. A new Fund Account is created if any combination of the following details is unique: `contact_id`, `wallet.phone.number`, `wallet.phone.country_code`, and `wallet.email`.

* If **all** the above details match the details of an existing Fund Account, the API returns details of the existing Fund Account.
* You cannot edit the details of a Fund Account.

```bash Curl theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-X POST https://api.razorpay.com/v1/fund_accounts \
-H "Content-Type: application/json" \
-d '{
  "contact_id": "cont_00000000000001",
  "account_type": "wallet",
  "wallet": {
    "provider": "amazonpay",
    "phone": "+919876543210",
    "email": "gaurav.kumar@example.com",
    "name": "Gaurav Kumar"
  }
}'
```

```json Success theme={null}
{
  "id": "fa_00000000000001",
  "entity": "fund_account",
  "contact_id": "cont_00000000000001",
  "account_type": "wallet",
  "wallet": {
    "provider": "amazonpay",
    "phone": "+919876543210",
    "email": "gaurav.kumar@example.com",
    "name": "Gaurav Kumar"
  },
  "active": true,
  "batch_id": null,
  "created_at": 1543650891
}
```

## Request Parameters

**contact\_id** `string` *required*

The unique identifier linked to a contact. For example, `cont_00000000000001`.

**account\_type** `string` *required*

The account type you want to link to the contact ID. Here, it is `wallet`.

**wallet** `object` *required*

The contact's wallet details.

**provider** `string` *required*

The wallet provider. Here, it is `amazonpay`.

**phone** `string` *required*

Beneficiary phone details. 10 digit beneficiary phone number with the country code. For example, `+919876543210 `.

**email** `string`

Beneficiary email address. For example, `gaurav.kumar@example.com`.

**name** `string`

Wallet holder's name. Name must be between 4 - 120 characters. This field is case-sensitive. Name cannot end with a special character, except `.`. Supported characters: `a-z`, `A-Z`, `0-9`, `space`, `’` , `-` , `_` , `/` , `(` , `)` and , `.`. For example, `Gaurav Kumar`.

## Response Parameters

**id** `string`

The unique identifier linked to the fund account. For example, `fa_00000000000001`.

**entity** `string`

Here it will be `fund_account`.

**contact\_id** `string`

The unique identifier linked to the contact. For example, `cont_00000000000001`.

**account\_type** `string`

The fund account type created. Here it is `wallet`.

**wallet** `object`

The contact's wallet details.

**provider** `string`

The wallet provider. Here, it is `amazonpay`.

**phone** `string`

10 digit beneficiary phone number with the country code. For example, `+919876543210 `.

**email** `string`

Beneficiary email address. For example, `gaurav.kumar@example.com`.

**name** `string`

Wallet holder's name. For example, `Gaurav Kumar`.

**active** `boolean`

Possible values:

* `true`: active
* `false`: inactive

**batch\_id** `string`

This parameter is populated if the fund account was created as part of a bulk upload. For example, `batch_00000000000001`.

**created\_at** `integer`

Timestamp, in Unix, when the fund account was created. For example, `1545320320`.
