> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Update a Linked Account

> Update Linked Accounts using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to update a Linked Account details.

You can update all other fields except `business_type` and `email` on the created Linked Account.

```bash Curl theme={null}
curl -X PATCH https://api.razorpay.com/v2/accounts/acc_LWXFUBYnysbYFV \
-u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-H "Content-type: application/json" \
-d '{
  "legal_business_name": "Acme Corp V2",
  "profile": {
    "addresses": {
      "operation": {
        "street1": "5071, Koramangala 6th block",
        "street2": "Kormanagala",
        "city": "Bengaluru",
        "state": "Karnataka",
        "postal_code": 560047,
        "country": "IN"
      }
    }
  },
  "legal_info": {
    "pan": "BAACL1234C",
    "gst": "10AABCU9603R1ZM"
  }
}'
```

```bash CLI theme={null}
razorpay route accounts update acc_IEIkSOM5VJb2Lm \
  --phone 9000000000 \
  --customer-facing-business-name "Acme New Name" \
  --profile-category healthcare \
  --profile-subcategory diagnostics \
  --support-email newsupport@acme.example.com \
  --pan AAAPL1234C
```

```json Success theme={null}
{
  "id": "acc_LWXFUBYnysbYFV",
  "type": "route",
  "status": "created",
  "email": "gaurava.kumar@example.com",
  "profile": {
    "category": "healthcare",
    "subcategory": "clinic",
    "addresses": {
      "registered": {
        "street1": "507, Koramangala 1st block",
        "street2": "MG Road",
        "city": "Bengaluru",
        "state": "KARNATAKA",
        "postal_code": "560034",
        "country": "IN"
      },
      "operation": {
        "street1": "5071, Koramangala 6th block",
        "street2": "Kormanagala",
        "city": "Bengaluru",
        "state": "KARNATAKA",
        "country": "IN",
        "postal_code": 560047
      }
    }
  },
  "notes": [],
  "created_at": 1679917193,
  "phone": "+919000090000",
  "contact_name": "Alex Lim",
  "reference_id": "124126",
  "business_type": "partnership",
  "legal_business_name": "Acme Corp V2",
  "customer_facing_business_name": "Acme Corp V2",
  "legal_info": {
    "pan": "BAACL1234C",
    "gst": "10AABCU9603R1ZM"
  }
}
```

```json Failure theme={null}
{
   "error":{
      "code":"BAD_REQUEST_ERROR",
      "description":"Linked account does not exist",
      "source":"",
      "step":"",
      "reason":"linked_account_id_does_not_exist",
      "metadata":{

      }
   }
}
```

## Path Parameters

**account\_id** `string` *required*

Unique identifier of the Linked Account whose details you need to update.

## Request Parameters

**phone** `integer` *required*

The Linked Account's business phone number. The minimum length is 8 characters and the maximum length is 15.

**legal\_business\_name** `string` *required*

The name of the Linked Account's business. For example, `Acme Corp`. The minimum length is 4 characters and the maximum length is 200.

**customer\_facing\_business\_name** `string`

The Linked Account billing label as it appears on the Dashboard. The minimum length is 1 character and the maximum length is 255.

**reference\_id** `string`

Partner's external account reference id. The minimum length is 1 character and the maximum length is 512.

**profile** `object` *required*

The business details of the Linked Account's account.

**category** `string` *required*

The business category of the Linked Account. Possible values: [List of Business Categories](https://razorpay.com/docs/sg/api/payments/route.md).

**subcategory** `string` *required*

The business sub-category of the Linked Account. Possible values: [List of Business Sub-Categories](https://razorpay.com/docs/sg/api/payments/route.md).

**business\_model** `string`

The business description. The character limit between 1-255 characters.

**addresses** `object` *required*

Details of Linked Account's address.

**operation** `object`

Details of the Linked Account's operational address.

**street1** `string`

Address, line 1. The maximum length is 100 characters.

**street2** `string`

Address, line 2. The maximum length is 100 characters.

**city** `string`

The city. The maximum length is 100 characters.

**state** `string`

The state. The minimum length is 2 and the maximum length is 32.

**postal\_code** `integer`

The postal code. This should be exactly 6 characters.

**country** `string`

The country. The minimum length is 2 and the maximum length is 64. This can either be a country code in capital letters or the full name of the country in lower case letters. For example, for India, you must write either `IN` or `india`.

**registered** `object` *required*

Details of the Linked Account's registered address.

**street1** `string`

Address, line 1. The maximum length is 100 characters.

**street2** `string`

Address, line 2. The maximum length is 100 characters.

**city** `string`

The city. The maximum length is 100 characters.

**state** `string`

The state. The minimum length is 2 and the maximum length is 32.

**postal\_code** `integer`

The postal code. This should be exactly 6 characters.

**country** `string`

The country. The minimum length is 2 and the maximum length is 64. This can either be a country code in capital letters or the full name of the country in lower case letters. For example, for India, you must write either `IN` or `india`.

**legal\_info** `object`

The legal details about the Linked Account's business. The mandatory [KYC requirement](https://razorpay.com/docs/payments/route/integration-guide.md#kyc-requirements) parameters should be passed depending on the business requirements.

**pan** `string`

Valid PAN number details of the Linked Account's business.

* This is a 10-digit alphanumeric code. For example, `AVOJB1111K`.
* The 4th digit should be either of 'C', 'H', 'F', 'A', 'T', 'B', 'J', 'G', 'L'.
* The regex for Company PAN is `/^[a-zA-z]{5}\d{4}[a-zA-Z]{1}$/`.

**gst** `string`

Valid GSTIN number details of the Linked Account.

* This is a 15-digit PAN-based unique identification number.
* The Regex for GSTIN is `/^[0123][0-9][a-z]{5}[0-9]{4}[a-z][0-9][a-z0-9][a-z0-9]$/gi`.

**contact\_info** `object`

Options available for contact support.

**chargeback** `object`

The type of contact support.

**email** `string`

The email id of chargeback POC. The maximum length is:

* local part (before @): 64 characters.
* domain part (after @): 68 characters. \
  &#x20;The total character length supported is 132.

**phone** `integer`

The phone number of chargeback POC. The maximum length is 10 characters.

**policy\_url** `string`

The URL of chargeback policy. Regex is (protocol://`razorpay.com`:port/resource path?querystring#fragementid)\
&#x20;protocol-both http/https allowed. Only domain name is mandatory.

**refund** `object`

The type of contact support.

**email** `string`

The email id of refund POC. The maximum length is:

* local part (before @): 64 characters.
* domain part (after @): 68 characters. \
  &#x20;The total character length supported is 132.

**phone** `integer`

The phone number of refund POC. The maximum length is 10 characters.

**policy\_url** `string`

The URL of refund policy. Regex is (protocol://`razorpay.com`:port/resource path?querystring#fragementid) \
&#x20;protocol-both http/https allowed.

**support** `array`

The type of contact support.

**email** `string`

The email id of support POC. The maximum length is:

* local part (before @): 64 characters.
* domain part (after @): 68 characters. \
  &#x20;The total character length supported is 132.

**phone** `integer`

The phone number of support POC. The maximum length is 10 characters.

**policy\_url** `string`

The URL of support policy. Regex is (protocol://`razorpay.com`:port/resource path?querystring#fragementid) \
&#x20;protocol-both http/https allowed.

**apps** `object`

The app details of the account holder's business

**websites** `array`

The website/app for the account holder's business. A minimum of 1 website is required.

**android** `array`

Android app details

**url** `string`

The link of the Android app. Regex is (protocol://`razorpay.com`:port/resource path?querystring#fragementid) \
&#x20;protocol-both http/https allowed.

**name** `string`

The name of the Android app.

**ios** `array`

iOS app details

**url** `string`

The link of the iOS app. Regex is (protocol://`razorpay.com`:port/resource path?querystring#fragementid) \
&#x20;protocol-both http/https allowed.

**name** `string`

The name of the iOS app.

## Response Parameters

**id** `string`

The unique identifier of the account generated by Razorpay. The maximum length is 18 characters. For example, `acc_GLGeLkU2JUeyDZ`.

**type** `string`

The account type. Possible value is `route`.

**status** `string`

The status of the account. Possible values:

* `created`
* `suspended`

**email** `string`

The account holder's email address.

**phone** `integer`

The account holder's phone number. The minimum length is 8 characters and the maximum length is 15.

**legal\_business\_name** `string`

The name of the account holder's business. For example, `Acme Corp`. The minimum length is 4 characters and the maximum length is 200.

**business\_type** `string`

The type of business operated by the account holder. Possible values: [Business Types](https://razorpay.com/docs/sg/api/payments/route.md).

**profile** `object`

The account holder's business details.

**category** `string`

The business category of the account holder. For example, `healthcare`. Possible values: [Business Category](https://razorpay.com/docs/sg/api/payments/route.md).

**subcategory** `string`

The business sub-category of the account holder. For example, `clinic`. Possible values: [Business Sub-Category](https://razorpay.com/docs/sg/api/payments/route.md).

**addresses** `object` *required*

Details of account holder's address.

**registered** `object` *required*

Details of the account holder's registered address.

**street1** `string`

Address, line 1. The maximum length is 100 characters.

**street2** `string`

Address, line 2. The maximum length is 100 characters.

**city** `string`

The city. The maximum length is 100 characters.

**state** `string`

The state. The minimum length is 2 and the maximum length is 100.

**postal\_code** `integer`

The postal code. This should be exactly 6 characters.

**country** `string`

The country. The minimum length is 2 and the maximum length is 64. This can either be a country code in capital letters or the full name of the country in lower case letters. For example, for India, you must write either `IN` or `india`.

**operation** `object`

Details of the account holder's operational address. This parameter might be required to complete the KYC process. However, it is optional for this API.

**street1** `string`

Address, line 1. The maximum length is 100 characters.

**street2** `string`

Address, line 2. The maximum length is 100 characters.

**city** `string`

The city. The maximum length is 100 characters.

**state** `string`

The state. The minimum length is 2 and the maximum length is 100.

**postal\_code** `integer`

The postal code. This should be exactly 6 characters.

**country** `string`

The country. The minimum length is 2 and the maximum length is 64. This can either be a country code in capital letters or the full name of the country in lower case letters. For example, for India, you must write either `IN` or `india`.

**legal\_info** `object`

The legal details about the account holder's business. The mandatory [KYC requirement](https://razorpay.com/docs/sg/api/payments/route.md) parameters should be passed depending on the business requirements.

**pan** `string`

Valid PAN number details of the account holder's business.

* This is a 10-digit alphanumeric code. For example, `AVOJB1111K`.
* The 4th digit should be either of 'C', 'H', 'F', 'A', 'T', 'B', 'J', 'G', 'L'.
* The regex for Company PAN is `/^[a-zA-z]{5}\d{4}[a-zA-Z]{1}$/`. This parameter might be required to complete the KYC process. However, it is optional for this API.

**gst** `string`

Valid GSTIN number details of the account holder.

* This is a 15-digit PAN-based unique identification number.
* The Regex for GSTIN is `/^[0123][0-9][a-z]{5}[0-9]{4}[a-z][0-9][a-z0-9][a-z0-9]$/gi`.

**notes** `object`

Contains user-defined fields stored by the partner for reference purposes.

**contact\_name** `string`

The name of the contact. The minimum length is 4 and the maximum length is 255 characters.

**contact\_info** `object`

Options available for contact support.

## Errors

> [accordion] Linked account does not exist.
>
> **Code:** `400`
>
> This error occurs when the requester is not the parent of the child account, or the child account does not exist.
>
> **Solution:** Ensure the Linked Account id exists before proceeding with the update API.

> [accordion] Merchant activation form has been locked for editing by admin.
>
> **Code:** `400`
>
> This error occurs when the submitted extra fields are under the review stage.
>
> **Solution:** You can wait for the review to be successful.
