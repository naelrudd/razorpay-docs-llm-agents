> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Payout Without Saving Card

> Create a Payout without Saving Card using API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create a payout to fund account type `card` without saving the card.

To understand the status of the payouts, refer to [Payout Status Details](https://razorpay.com/docs/errors/x/payout-status-details.md).

> [!WARNING]
>
> **Watch Out!**
>
> Ensure you [allowlist IPs](https://razorpay.com/docs/x/dashboard/allowlist-ip.md) and pass the [idempotency key](https://razorpay.com/docs/api/x/payout-idempotency/make-request.md) to make a successful payout.

```bash Curl theme={null}
curl -u <YOUR_KEY>:<YOUR_SECRET> \
-X POST https://api.razorpay.com/v1/payouts \
-H "Content-Type: application/json" \
-H "X-Payout-Idempotency: 53cda91c-8f81-4e77-bbb9-7388f4ac6bf4" \
-d '{
  "account_number": "7878780080316316",
  "amount": 1000000,
  "currency": "INR",
  "mode": "NEFT",
  "purpose": "refund",
  "fund_account": {
    "account_type": "card",
    "card": {
      "number": "765432123456789",
      "name": "Gaurav Kumar",
      "input_type": "card"
    },
    "contact": {
      "email": "gaurav.kumar@example.com",
      "contact": "9876543210",
      "type": "employee",
      "reference_id": "Acme Contact ID 12345",
      "notes": {
        "notes_key_1": "Tea, Earl Grey, Hot",
        "notes_key_2": "Tea, Earl Grey… decaf."
      }
    }
  },
  "queue_if_low_balance": true,
  "reference_id": "Acme Transaction ID 12345",
  "narration": "Acme Corp Fund Transfer",
  "notes": {
    "notes_key_1": "Beam me up Scotty",
    "notes_key_2": "Engage"
  }
}'
```

```json Success theme={null}
{
  "id": "pout_00000000000001",
  "entity": "payout",
  "fund_account_id": "fa_00000000000001",
  "fund_account": {
    "id": "fa_00000000000001",
    "entity": "fund_account",
    "contact_id": "cont_00000000000001",
    "contact": {
      "id": "cont_00000000000001",
      "entity": "contact",
      "contact": "9876543210",
      "email": "gaurav.kumar@example.com",
      "type": "employee",
      "reference_id": "Acme Contact ID 12345",
      "batch_id": null,
      "active": true,
      "notes": {
        "notes_key_1": "Tea, Earl Grey, Hot",
        "notes_key_2": "Tea, Earl Grey… decaf."
      },
      "created_at": 1580817353
    },
    "account_type": "card",
    "card": {
      "last4": "6789",
      "network": "Visa",
      "type": "credit",
      "issuer": "HDFC",
      "input_type": "card"
    },
    "batch_id": null,
    "active": true,
    "created_at": 1581080272
  },
  "amount": 1000000,
  "currency": "INR",
  "notes": {
    "notes_key_1": "Beam me up Scotty",
    "notes_key_2": "Engage"
  },
  "fees": 590,
  "tax": 90,
  "status": "processed",
  "purpose": "payout",
  "utr": null,
  "mode": "NEFT",
  "reference_id": "Acme Transaction ID 12345",
  "narration": "Acme Corp Fund Transfer",
  "batch_id": null,
  "failure_reason": null,
  "created_at": 1581499319,
  "fee_type": "",
  "error": {
    "description": null,
    "source": null,
    "reason": null
  }
}
```

## Request Parameters

**account\_number** `string` *required*

The account from which you want to make the payout.\
Account details can be found on the RazorpayX Dashboard. For example, `7878780080316316`.

* Pass your customer identifier if you want money to be deducted from RazorpayX Lite.
* Pass your Current Account number if you want money to be deducted from your Current Account.

> [!WARNING]
>
> **Watch Out!**
>
> * This is **not** your contact's bank account number. Log in to your [**RazorpayX Dashboard**](https://x.razorpay.com/auth/?intent=current_account) and go to **My Account & Settings → Banking → Customer Identifier**.
> * This value is different for Test Mode and Live Mode.
> * RazorpayX Lite is currently not available for new merchants. To set up a new RazorpayX account, refer to [Current Account](https://razorpay.com/docs/x/account-types/current-account.md).

**amount** `integer` *required*

The payout amount, in paise. For example, if you want to transfer ₹10000, pass `1000000`. Minimum value is `100`.

**currency** `string` *required*

The payout currency. Here, it is `INR`.

**mode** `string` *required*

The mode to be used to create the payout. Available modes:

* `NEFT`
* `RTGS`
* `IMPS`
* `UPI`
* `card` \\

The payout modes are case-sensitive. When creating payouts using APIs, ensure payout modes are entered in upper case.

**purpose** `string` *required*

The purpose of the payout that is being created. The following classifications are available in the system by default:

* `refund`
* `cashback`
* `payout`
* `salary`
* `utility bill`
* `vendor bill` \\

Additional purposes for payouts can be created via the [Dashboard](https://x.razorpay.com/) and then used in the API. However, it is not possible to create a new purpose for the payout via the API.

**queue\_if\_low\_balance** `boolean`

Possible values:

* `true` : The payout is queued when your business account does not have sufficient balance to process the payout.
* `false` (default) : The payout is never queued. The payout fails if your business account does not have sufficient balance to process the payout.

**fund\_account** `object` *required*

The account to which you want to make the payout.

**account\_type** `string` *required*

The type of account linked to the contact id. Here, it will be `card`.

**card** `object` *required*

The details of the card used.

**input\_type** `string` *required*

Here, the value is `card`.

**number** `string` *required*

Same field can accept card numbers or card tokens.

**name** `string`

The name on the card.

**expiry\_month** `string`

The expiry month of the entered card.

**expiry\_year** `string`

The expiry year of the entered card.

**contact** `object` *required*

The Contact's details.

**name** `string` *required*

Name of the contact. This field is case-sensitive. A minimum of 3 characters and a maximum of 50 characters are allowed. Name cannot end with a special character, except `.`. Supported characters: a-z, A-Z, 0-9, space, `’` , `-` , `_` , `/ `, `( , )` and `.`. For example, `Gaurav Kumar`.

**email** `string`

The contact's email address. For example, `gaurav.kumar@example.com`.

**contact** `string`

The contact's phone number. For example, `9000090000`.

**type** `string`

Classification for the contact being created. For example, employee. Possible values: `vendor`, `customer`, `employee`, `self`.

**reference\_id** `string`

A user-generated reference given to the contact. For example, `Acme Contact ID 12345`. This field can have a maximum length of 40 characters.

**notes** `object`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

**reference\_id** `string`

Maximum length is 40 characters. A user-generated reference given to the payout. For example, `Acme Transaction ID 12345`. You can use this field to store your own transaction ID, if any.

**narration** `string`

Maximum length 30 characters. Allowed characters: `a-z`, `A-Z`, `0-9` and space. This is a custom note that also appears on the bank statement. If no value is passed for this parameter, it defaults to the Merchant Billing Label. \
&#x20;\
&#x20;Enter the important text in the first 9 characters as banks truncate the rest as per their standards.

**notes** `array of objects`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

## Response Parameters

**id** `string`

The unique identifier linked to the payout. For example, `pout_00000000000001`.

**entity** `string`

The entity being created. For example, `payout`.

**fund\_account\_id** `string`

The unique identifier linked to the fund account. For example, `fa_00000000000001`.

**fund\_account** `object`

The account to which you want to make the payout.

**id** `string`

The unique identifier linked to the fund account. For example, `fa_00000000000001`.

**account\_type** `string`

The type of account linked to the contact id. Here, it will be `card`.

**contact\_id** `string`

The unique identifier linked to the contact. For example, `cont_00000000000001`.

**contact** `object`

**id** `string`

The unique identifier linked to the contact. For example, `cont_00000000000001`.

**entity** `string`

The entity being created. Here, it will be `contact`.

**name** `string`

The contact's name. For example, `Gaurav Kumar`.

**contact** `string`

The contact's phone number. For example, `9000090000`.

**email** `string`

The contact's email address. For example, `gaurav.kumar@example.com`.

**type** `string`

A classification for the contact being created. For example, `employee`.

**reference\_id** `string`

A user-entered reference for the contact. For example, `Acme Contact ID 12345`.

**batch\_id** `string`

This value is returned if the contact was created as part of a bulk upload. For example, `batch_00000000000001`.

**active** `boolean`

Possible values:

* `true` (default): active
* `false`: inactive

**notes** `object`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

**created\_at** `integer`

Timestamp, in Unix, when the contact was created. For example, `1545320320`.

**card** `object`

The details of the card used.

**last4** `string`

The last 4 digits of the card number. If the input\_type = `service_provider_token` then it is the last 4 digits of the card token.

**network** `string`

The network operator that has issued the card. For example, `Mastercard`, `Visa`.

**type** `string`

The type of card. For example, `credit` or `debit`.

**issuer** `string`

The bank that has issued the card. For example, `ICIC`, `HDFC`.

**input\_type** `string`

Possible values:

* `service_provider_token` : When the token number used is provided by an external service.
* `card` : When a card number is provided.
* `razorpay_token` : When the token id used is provided by Razorpay.

**amount** `integer`

The payout amount, in paise. For example, if you want to transfer ₹10,000, pass `1000000`. Minimum value `100`. \
&#x20;\
&#x20;The value passed here does not include fees and tax. Fees and tax, if any, are deducted from your account balance.

**currency** `string`

The payout currency. Here, it is `INR`.

**notes** `array of objects`

Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

**fees** `integer`

The fees for the payout. This value is returned only when the payout moves to the `processing` state. For example, `5`.

**tax** `integer`

The tax that is applicable for the fee being charged. This value is returned only when the payout moves to the `processing` state. For example, `1`.

**status** `string`

The status of the payout. Possible payout states:

* `queued`
* `pending` (if you have [Approval Workflow](https://razorpay.com/docs/x/manage-teams/approval-workflow.md) enabled)
* `rejected` (if you have [Approval Workflow](https://razorpay.com/docs/x/manage-teams/approval-workflow.md) enabled)
* `processing`
* `processed`
* `cancelled`
* `reversed`

**purpose** `string`

The purpose of the payout that is being created. The following classifications are available in the system by default:

* `refund`
* `cashback`
* `payout`
* `salary`
* `utility bill`
* `vendor bill`

**utr** `string`

The unique transaction number linked to a payout. For example, `HDFCN00000000001`.

**mode** `string`

The mode used to make the payout. Available modes:

* `NEFT`
* `RTGS`
* `IMPS`
* `UPI`
* `card` \\

The payout modes are case-sensitive.

**reference\_id** `string`

Maximum length is 40 characters. A user-generated reference given to the payout. For example, `Acme Transaction ID 12345`. You can use this field to store your own transaction ID, if any.

**narration** `string`

Maximum length 30 characters. Allowed characters: `a-z`, `A-Z`, `0-9` and space. This is a custom note that also appears on the bank statement. If no value is passed for this parameter, it defaults to the Merchant Billing Label. \
&#x20;\
&#x20;Enter the important text in the first 9 characters as banks truncate the rest as per their standards.

**batch\_id** `string`

This value is returned if the contact was created as part of a bulk upload. For example, `batch_00000000000001`.

**status\_details** `object`

This parameter returns the current status of the payout. For example, `IMPS is not enabled on beneficiary account, Retry with different mode.`

**description** `string`

A description for the error. For example, `IMPS is not enabled on beneficiary account, please retry with different mode`.

**source** `string`

Possible values:

* `gateway`: Technical error at Razorpay Partner bank.
* `beneficiary_bank`: Technical error at beneficiary bank.
* `business`: Merchant action required.
* `internal`: Technical error at Razorpay's server.

**reason** `string`

The error reason. For example, `imps_not_allowed`. Know more about [Payout Status Details and Next Steps](https://razorpay.com/docs/errors/x/payout-status-details.md).

**created\_at** `integer`

Timestamp, in Unix, when the contact was created. For example, `1545320320`.

**fee\_type** `string`

Indicates the fee type charged for the payout. Possible value is `free_payout`.
