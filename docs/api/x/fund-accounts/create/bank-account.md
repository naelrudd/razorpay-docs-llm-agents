> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Fund Account of Type Bank Account

> Create a Fund Account with Bank Account details using APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create a fund account with bank account details.

* A new fund account is created if any combination of the following details is unique: `contact_id`, `bank_account.name`, `bank_account.ifsc` and `bank_account.account_number`.
* If **all** the above details match the details of an existing fund account, the API returns details of the existing fund account.
* You cannot edit the details of a fund account.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/fund_accounts \
-H "Content-Type: application/json" \
-d '{
  "contact_id":"cont_00000000000001",
  "account_type":"bank_account",
  "bank_account":{
    "name":"Gaurav Kumar",
    "ifsc":"HDFC0000053",
    "account_number":"765432123456789"
  }
}'
```

```json Success theme={null}
{
  "id" : "fa_00000000000001",
  "entity": "fund_account",
  "contact_id" : "cont_00000000000001",
  "account_type": "bank_account",
  "bank_account": {
    "ifsc": "HDFC0000053",
    "bank_name": "HDFC Bank",
    "name": "Gaurav Kumar",
    "account_number": "765432123456789",
    "notes": []
  },
  "active": true,
  "batch_id": null,
  "created_at": 1543650891
}
```

## Request Parameters

**contact\_id** `string` *required*

This is the unique identifier linked to a contact. For example, `cont_00000000000001`.

**account\_type** `string` *required*

The account type you want to link to the contact ID. Here it is `bank_account`.

**bank\_account** `object` *required*

The contact's bank account details.

**name** `string` *required*

Account holder's name. Name must be between 3 - 120 characters. This field is case-sensitive. Name cannot end with a special character, except `.`. Supported characters: `a-z`, `A-Z`, `0-9`, `space`, `’` , `-` , `_` , `/` , `(` , `)` and , `.`. For example,`Gaurav Kumar`.

**ifsc** `string` *required*

Beneficiary bank IFSC. Has to be 11 characters. Unique identifier of a bank branch. For example, `HDFC0000053`.

**account\_number** `string` *required*

Beneficiary account number. Between 5 and 35 characters. Supported characters: `a-z`, `A-Z` and `0-9`. Beneficiary account number. For example, `765432123456789`.

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

> [accordion] The contact id provided does not exist.
>
> **Code:** `4xx`
>
> The contact ID provided is incorrect.
>
> **Solution:** Enter the correct Contact ID. Check if this contact already exists in your RazorpayX account using [Fetch Contact id API](https://razorpay.com/docs/api/x/contacts/fetch-with-id.md) or use the [search option](https://razorpay.com/docs/x/dashboard/global-search.md) on the Dashboard. Or find the Contact ID:
>
> * In the response body of [create a Contact](https://razorpay.com/docs/api/x/contacts/create.md) API.
> * On the [Contacts](https://razorpay.com/docs/x/contacts) Dashboard.

> [accordion] The IFSC must be 11 characters.
>
> **Code:** `4xx`
>
> The IFSC code provided is either incorrect or does not have 11 characters.
>
> **Solution:** Check and pass the correct 11 characters IFSC.

> [accordion] The account number format is invalid.
>
> **Code:** `4xx`
>
> The account number is incorrect.
>
> **Solution:** Enter the beneficiary account number between 5 and 35 characters. Supported characters- a-z, A-Z, and 0-9.
