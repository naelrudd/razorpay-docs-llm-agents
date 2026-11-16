> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Fund Account for Externally Tokenised Card

> Create a Fund Account for saving an external Tokenised Card using API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create a fund account type `card` by saving the card as an external token.

```bash Curl theme={null}
curl -u <YOUR_KEY>:<YOUR_SECRET> \
-X POST https://api.razorpay.com/v1/fund_accounts \
-H "Content-Type: application/json" \
-d '{
  "contact_id": "cont_00000000000001",
  "account_type": "card",
  "card": {
    "number": "4854980604708430",
    "expiry_month": "12",
    "expiry_year": "21",
    "token_provider": "payu",
    "input_type": "service_provider_token"
  }
}'
```

```json Success theme={null}
{
  "id": "fa_00000000000001",
  "entity": "fund_account",
  "contact_id": "cont_00000000000001",
  "account_type": "card",
  "card": {
    "last4": "8430",
    "network": "Visa",
    "type": "credit",
    "issuer": "HDFC",
    "input_type": "service_provider_token",
  },
  "active": true,
  "batch_id": null,
  "created_at": 1543650891
}
```

## Request Parameters

**contact\_id** `string` *required*

The unique identifier of the contact for which you want to fetch payouts. For example, `cont_00000000000001`.

**account\_type** `string` *required*

The type of account linked to the contact id. Here, it will be `card`.

**card** `object` *required*

The details of the card used.

**number** `string` *required*

Same field can accept card numbers or card tokens. Here, the value is card token.

**expiry\_month** `string` *required*

The expiry month of the card numbers or card token. Here, the value is of card token.

**expiry\_year** `string` *required*

The expiry year of the card numbers or card token. Here, the value is of card token.

**input\_type** `string` *required*

Here, the value is `service_provider_token`.

**token\_provider** `string` *required*

The name of the aggregator that provided the token.

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
