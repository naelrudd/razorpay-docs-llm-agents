> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Fund Account of Type VPA

> Create a Fund Account with VPA details using APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create a fund account with VPA details.

* A new fund account is created if any combination of the following details is unique: `contact_id` and `vpa.address`.
* If **all** the above details match the details of an existing fund account, the API returns details of the existing fund account.
* You cannot edit the details of a fund account.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/fund_accounts \
-H "Content-Type: application/json" \
-d '{
  "account_type":"vpa",
  "contact_id":"cont_00000000000001",
  "vpa":{
    "address":"gaurav.kumar@exampleupi"
  }
}'
```

```json Success theme={null}
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
  "created_at": 1545223741
}
```

## Request Parameters

**contact\_id** `string` *required*

This is the unique identifier linked to a contact. For example, `cont_00000000000001`.

**account\_type** `string` *required*

The fund account type you want to link to the contact ID. Here it is `vpa`.

**vpa** `object` *required*

The contact's virtual payment address (VPA) details.

**address** `string` *required*

Between 3 and 100 characters. Supported characters: `a-z`, `A-Z`, `0-9`, `.`, `-` and one `@`. The virtual payment address. For example, `gauravkumar@exampleupi`.

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

> [accordion] The contact ID provided does not exist.
>
> **Code:** `4xx`
>
> The contact id provided is incorrect.
>
> **Solution:** Enter the correct Contact ID. Check if this contact already exists in your RazorpayX account using [Fetch Contact id API](https://razorpay.com/docs/api/x/contacts/fetch-with-id.md) or use the [search option](https://razorpay.com/docs/x/dashboard/global-search.md) on the Dashboard. Or find the Contact ID:
>
> * In the response body of [create a Contact](https://razorpay.com/docs/api/x/contacts/create.md) API.
> * On the [Contacts](https://razorpay.com/docs/x/contacts) Dashboard.
