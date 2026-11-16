> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Linked Account

> Create a Linked Account using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create a Linked Account.

> [!NOTE]
>
> **Composite Onboarding Available**
>
> You can now create a Linked Account together with its settlement destination (UPI VPA or bank account) in a single atomic call. See [Create a Linked Account (Composite)](https://razorpay.com/docs/api/payments/route/create-linked-account-composite.md) for details.

> [!NOTE]
>
> **VPA (UPI id) as settlement destination**
>
> You can create a Linked Account with a VPA (UPI id) as the settlement destination instead of a bank account. Funds are settled to the beneficiary's UPI-linked bank account within a few minutes of a transfer being created. Refer to the **VPA (UPI id) settlement** request and response samples below.
>
> Before creating a VPA-based Linked Account, verify the VPA using the [Validate VPA API](https://razorpay.com/docs/api/x/account-validation/vpa.md). The verification response returns the account holder's name, which you must match against your beneficiary records as a compliance requirement. Refer to [Name Matching Requirements](https://razorpay.com/docs/payments/route/linked-account/vpa-settlements.md#name-matching-requirements).

> [!WARNING]
>
> **Watch Out!**
>
> * The per-transaction limit for VPA settlements is ₹1,00,000 (set by NPCI). Transfers above this amount are rejected. Use bank account settlement for larger amounts.
> * A Linked Account can be configured with either a VPA or a bank account, not both. To support both settlement methods for the same beneficiary, create two separate Linked Accounts.
> * VPA Linked Accounts must be created individually. Batch upload does not support VPA as an account type.

```bash cURL - Bank Account theme={null}
curl -X POST 'https://api.razorpay.com/v2/accounts' \
     -u [YOUR_KEY_ID]:[YOUR_SECRET] \
     -H "Content-type: application/json" \
     -d '{
   "email":"gaurav.kumar@example.com",
   "phone":"9000090000",
   "type":"route",
   "reference_id":"124124",
   "legal_business_name":"Acme Corp",
   "business_type":"partnership",
   "contact_name":"Gaurav Kumar",
   "profile":{
      "category":"healthcare",
      "subcategory":"clinic",
      "addresses":{
         "registered":{
            "street1":"507, Koramangala 1st block",
            "street2":"MG Road",
            "city":"Bengaluru",
            "state":"KARNATAKA",
            "postal_code":"560034",
            "country":"IN"
         }
      }
   },
   "legal_info":{
      "pan":"AAACL1234C",
      "gst":"18AABCU9603R1ZM"
   }
}'
```

```bash CLI - Bank Account theme={null}
razorpay route accounts create \
  --email merchant@example.com \
  --phone 9876543210 \
  --legal-business-name "Acme Pvt Ltd" \
  --business-type route \
  --contact-name "Jane Doe" \
  --customer-facing-business-name "Acme Store" \
  --profile-category financial_services \
  --profile-subcategory accounting \
  --profile-business-model "Online marketplace for services" \
  --registered-street1 "12 Main St" \
  --registered-street2 "Floor 2" \
  --registered-city Mumbai \
  --registered-state Maharashtra \
  --registered-postal-code 400001 \
  --registered-country IN \
  --pan AAAPL1234C \
  --gst 29ABCDE1234F1Z5 \
  --website https://acme.example.com \
  --support-email support@acme.example.com \
  --support-phone 9876543210 \
  --note internal_id=acme_001
```

```bash cURL - VPA (UPI ID) theme={null}
curl -X POST 'https://api.razorpay.com/v2/accounts' \
     -u [YOUR_KEY_ID]:[YOUR_SECRET] \
     -H "Content-type: application/json" \
     -d '{
  "email": "gaurav.kumar@example.com",
  "phone": "9000090000",
  "type": "route",
  "reference_id": "landlord_123",
  "legal_business_name": "Gaurav Kumar",
  "business_type": "individual",
  "contact_name": "Gaurav Kumar",
  "profile": {
    "category": "housing",
    "subcategory": "rentals",
    "addresses": {
      "registered": {
        "street1": "507, Koramangala 1st block",
        "street2": "MG Road",
        "city": "Bengaluru",
        "state": "KARNATAKA",
        "postal_code": "560034",
        "country": "IN"
      }
    }
  },
  "account_details": {
    "account_type": "vpa",
    "vpa": {
      "address": "gaurav.kumar@paytm"
    }
  },
  "settlement_details": {
    "settlement_schedule": "instant",
    "settlement_mode": "imps"
  }
}'
```

```json Success - Bank Account theme={null}
{
   "id":"acc_GRWKk7qQsLnDjX",
   "type":"route",
   "status":"created",
   "email":"gaurav.kumar@example.com",
   "profile":{
      "category":"healthcare",
      "subcategory":"clinic",
      "addresses":{
         "registered":{
            "street1":"507, Koramangala 1st block",
            "street2":"MG Road",
            "city":"Bengaluru",
            "state":"KARNATAKA",
            "postal_code":"560034",
            "country":"IN"
         }
      }
   },
   "notes":[

   ],
   "created_at":1611136837,
   "phone":"9000090000",
   "contact_name":"Gaurav Kumar",
   "reference_id":"124124",
   "business_type":"partnership",
   "legal_business_name":"Acme Corp",
   "customer_facing_business_name":"Acme Corp",
   "legal_info":{
      "pan":"AAACL1234C",
      "gst":"18AABCU9603R1ZM"
   }
}
```

```json Failure - Bank Account theme={null}
{
    "error": {
        "code": "BAD_REQUEST_ERROR",
        "description": "Invalid business type: xyz",
        "source": "business",
        "step": "payment_initiation",
        "reason": "input_validation_failed",
        "metadata": {},
        "field": "business_type"
    }
}
```

```json Success - VPA (UPI ID) theme={null}
{
  "id": "acc_HjKlMnOpQrStUv",
  "type": "route",
  "status": "created",
  "email": "gaurav.kumar@example.com",
  "phone": "9000090000",
  "contact_name": "Gaurav Kumar",
  "reference_id": "landlord_123",
  "business_type": "individual",
  "legal_business_name": "Gaurav Kumar",
  "customer_facing_business_name": "Gaurav Kumar",
  "profile": {
    "category": "housing",
    "subcategory": "rentals",
    "addresses": {
      "registered": {
        "street1": "507, Koramangala 1st block",
        "street2": "MG Road",
        "city": "Bengaluru",
        "state": "KARNATAKA",
        "postal_code": "560034",
        "country": "IN"
      }
    }
  },
  "account_details": {
    "account_type": "vpa",
    "vpa": {
      "address": "gaurav.kumar@paytm",
      "vpa_holder_name": "GAURAV KUMAR"
    }
  },
  "settlement_details": {
    "settlement_schedule": "instant",
    "settlement_mode": "imps"
  },
  "notes": [],
  "created_at": 1706800837
}
```

```json VPA not found - VPA (UPI ID) theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "The VPA provided does not exist or is inactive.",
    "source": "business",
    "step": "payment_initiation",
    "reason": "input_validation_failed",
    "metadata": {},
    "field": "account_details.vpa.address"
  }
}
```

```json Limit exceeded - VPA (UPI ID) theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "Transfer amount exceeds the maximum allowed limit of ₹1,00,000 for VPA settlements.",
    "source": "business",
    "step": "payment_initiation",
    "reason": "amount_exceeds_vpa_limit",
    "metadata": {}
  }
}
```

```json Invalid VPA format - VPA (UPI ID) theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "The VPA address format is invalid. Expected format: username@bankname.",
    "source": "business",
    "step": "payment_initiation",
    "reason": "input_validation_failed",
    "metadata": {},
    "field": "account_details.vpa.address"
  }
}
```

## Request Parameters

**email** `string` *required*

The Linked Account's business email address.

**phone** `integer` *required*

The Linked Account's business phone number. The minimum length is 8 characters and the maximum length is 15.

**legal\_business\_name** `string` *required*

The name of the Linked Account's business. For example, `Acme Corp`. The minimum length is 4 characters and the maximum length is 200.

**customer\_facing\_business\_name** `string`

The Linked Account billing label as it appears on the Dashboard. The minimum length is 1 character and the maximum length is 255.

**business\_type** `string` *required*

The type of business operated by the Linked Account holder. List of possible values are available [here](https://razorpay.com/docs/payments/route/integration-guide.md#business-type).

**reference\_id** `string`

Partner's external account reference id. The minimum length is 1 character and the maximum length is 512.

**profile** `object` *required*

The business details of the Linked Account's account.

**category** `string` *required*

The business category of the Linked Account. Possible values: [List of Business Categories](https://razorpay.com/docs/payments/route/integration-guide.md#business-category).

**subcategory** `string` *required*

The business sub-category of the Linked Account. Possible values: [List of Business Sub-Categories](https://razorpay.com/docs/payments/route/integration-guide.md#business-sub-category).

**business\_model** `string`

The business description. The character limit between 1-255 characters.

**addresses** `object` *required*

Details of Linked Account's address.

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

Below are the list of supported Indian states:

| State Name | State Code |
| - | - |
| ANDAMAN & NICOBAR ISLANDS | AN |
| ANDAMAN AND NICOBAR ISLANDS | AN |
| ANDHRA PRADESH | AP |
| ARUNACHAL PRADESH | AR |
| ASSAM | AS |
| BIHAR | BI |
| CHANDIGARH | CH |
| CHHATTISGARH | CT |
| DADRA & NAGAR HAVELI | DN |
| DADRA AND NAGAR HAVELI | DN |
| DAMAN & DIU | DD |
| DAMAN AND DIU | DD |
| DELHI | DL |
| GOA | GO |
| GUJARAT | GJ |
| HARYANA | HA |
| HIMACHAL PRADESH | HP |
| JAMMU & KASHMIR | JK |
| JAMMU AND KASHMIR | JK |
| JHARKHAND | JH |
| KARNATAKA | KA |
| KERALA | KE |
| LAKSHADWEEP | LD |
| MADHYA PRADESH | MP |
| MAHARASHTRA | MH |
| MANIPUR | MA |
| MEGHALAYA | ME |
| MIZORAM | MI |
| NAGALAND | NA |
| ODISHA | OR |
| PONDICHERRY | PO |
| PUNJAB | PB |
| RAJASTHAN | RJ |
| SIKKIM | SK |
| TAMIL NADU | TN |
| TRIPURA | TR |
| TELANGANA | TG |
| UTTAR PRADESH | UP |
| UTTARAKHAND | UT |
| WEST BENGAL | WB |

**postal\_code** `integer`

The postal code. This should be exactly 6 characters.

**country** `string`

The country. The minimum length is 2 and the maximum length is 64. This can either be a country code in capital letters or the full name of the country in lower case letters. For example, for India, you must write either `IN` or `india`.

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

Below are the list of supported Indian states:

| State Name | State Code |
| - | - |
| ANDAMAN & NICOBAR ISLANDS | AN |
| ANDAMAN AND NICOBAR ISLANDS | AN |
| ANDHRA PRADESH | AP |
| ARUNACHAL PRADESH | AR |
| ASSAM | AS |
| BIHAR | BI |
| CHANDIGARH | CH |
| CHHATTISGARH | CT |
| DADRA & NAGAR HAVELI | DN |
| DADRA AND NAGAR HAVELI | DN |
| DAMAN & DIU | DD |
| DAMAN AND DIU | DD |
| DELHI | DL |
| GOA | GO |
| GUJARAT | GJ |
| HARYANA | HA |
| HIMACHAL PRADESH | HP |
| JAMMU & KASHMIR | JK |
| JAMMU AND KASHMIR | JK |
| JHARKHAND | JH |
| KARNATAKA | KA |
| KERALA | KE |
| LAKSHADWEEP | LD |
| MADHYA PRADESH | MP |
| MAHARASHTRA | MH |
| MANIPUR | MA |
| MEGHALAYA | ME |
| MIZORAM | MI |
| NAGALAND | NA |
| ODISHA | OR |
| PONDICHERRY | PO |
| PUNJAB | PB |
| RAJASTHAN | RJ |
| SIKKIM | SK |
| TAMIL NADU | TN |
| TRIPURA | TR |
| TELANGANA | TG |
| UTTAR PRADESH | UP |
| UTTARAKHAND | UT |
| WEST BENGAL | WB |

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

The app details of the account holder's business.

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

The following parameters are required only when you create a Linked Account with a VPA (UPI id) as the settlement destination, as shown in the **VPA (UPI id)** request sample above.

**account\_details** `object`

The settlement destination details for the Linked Account. Required for VPA-based Linked Accounts.

**account\_type** `string` *required*

The type of settlement destination. Pass `vpa` to configure a UPI id as the settlement destination.

**vpa** `object` *required*

The VPA details of the beneficiary.

**address** `string` *required*

The beneficiary's UPI id. The format is `username@bankname`. For example, `gaurav.kumar@paytm` or `9000090000@ybl`. The maximum length is 100 characters.

**settlement\_details** `object`

The settlement configuration for the Linked Account. Required for VPA-based Linked Accounts.

**settlement\_schedule** `string` *required*

The settlement schedule for the Linked Account. Pass `instant` for transaction-level instant settlement to the VPA. Instant settlement is the only supported mode for VPA-based Linked Accounts.

**settlement\_mode** `string` *required*

The banking mode used to process the payout. Pass `imps` for VPA settlements.

## Response Parameters

**id** `string`

The unique identifier of the account generated by Razorpay. The maximum length is 18 characters. For example, `acc_GLGeLkU2JUeyDZ`.

**type** `string`

The account type. Possible value is `route`.

**reference\_id** `string`

The internal reference ID. This value can be maximum of 20 characters. For example, `123123`.

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

The type of business operated by the account holder. Possible values: [Business Types](https://razorpay.com/docs/payments/route/integration-guide.md#business-type).

**profile** `object`

The account holder's business details.

**category** `string`

The business category of the account holder. For example, `healthcare`. Possible values: [Business Category](https://razorpay.com/docs/payments/route/integration-guide.md#business-category).

**subcategory** `string`

The business sub-category of the account holder. For example, `clinic`. Possible values: [Business Sub-Category](https://razorpay.com/docs/payments/route/integration-guide.md#business-sub-category).

**addresses** `object`

Details of account holder's address.

**registered** `object`

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

**legal\_info** `object`

The legal details about the account holder's business. The mandatory [KYC requirement](https://razorpay.com/docs/payments/route/integration-guide.md#kyc-requirements) parameters should be passed depending on the business requirements.

**pan** `string`

Valid PAN number details of the account holder's business.

* This is a 10-digit alphanumeric code. For example, `AVOJB1111K`.
* The 4th digit should be either of 'C', 'H', 'F', 'A', 'T', 'B', 'J', 'G', 'L'.
* The regex for Company PAN is `/^[a-zA-z]{5}\d{4}[a-zA-Z]{1}$/`.

This parameter might be required to complete the KYC process. However, it is optional for this API.

**gst** `string`

Valid GSTIN number details of the account holder.

* This is a 15-digit PAN-based unique identification number.
* The Regex for GSTIN is `/^[0123][0-9][a-z]{5}[0-9]{4}[a-z][0-9][a-z0-9][a-z0-9]$/gi`.

**notes** `object`

Contains user-defined fields stored by the partner for reference purposes.

**contact\_name** `string`

The name of the contact. The minimum length is 4 and the maximum length is 255 characters.

The following parameters are returned only for a Linked Account created with a VPA (UPI id) as the settlement destination.

**account\_details** `object`

The settlement destination details of the Linked Account.

**account\_type** `string`

The type of settlement destination. Value is `vpa`.

**vpa** `object`

The VPA details of the beneficiary.

**address** `string`

The beneficiary's UPI id. For example, `gaurav.kumar@paytm`.

**vpa\_holder\_name** `string`

The account holder's name as returned by the beneficiary's bank during VPA verification. For example, `GAURAV KUMAR`. Use this value to perform name matching against your beneficiary records before completing onboarding.

**settlement\_details** `object`

The settlement configuration of the Linked Account.

**settlement\_schedule** `string`

The settlement schedule. Value is `instant`.

**settlement\_mode** `string`

The banking mode used to process the payout. Value is `imps`.

**created\_at** `integer`

The Unix timestamp at which the Linked Account was created.

## Errors

> [accordion] The api key/secret provided is invalid
>
> **Code:** `4xx`
>
> This error occurs when there is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
>
> **Solution:** Make sure the API Keys are active and entered correctly. Also, there should not be any whitespaces before or after the keys.

> [accordion] The input field is required
>
> **Code:** `400`
>
> This error occurs when a mandatory field is empty.
>
> **Solution:** Make sure to fill in all the mandatory fields.

> [accordion] The requested URL was not found on the server.
>
> **Code:** `400`
>
> This error occurs when Marketplace feature is not enabled for merchants using private auth.
>
> **Solution:** Ensure to enable Marketplace feature for merchants using private auth.

> [accordion] Invalid type: route
>
> **Code:** `400`
>
> This error occurs when the value of a parameter is invalid. For example, when the value of the `type` parameter is other than `route`.
>
> **Solution:** Ensure to send correct values for parameters.

> [accordion] Route code Support feature not enabled to add account code.
>
> **Code:** `400`
>
> This error occurs when you pass the value for the `reference_id` parameter, but the `route_code_support` feature is not enabled for merchants.
>
> **Solution:** Ensure to enable the `route_code_support` feature for merchants before passing the value for the `reference_id` parameter.

> [accordion] Merchant email already exists for account - BbHKlnuyZkf0xa.
>
> **Code:** `400`
>
> This error occurs when you try to create a Linked Account with an existing email address.
>
> **Solution:** Make sure the email address is unique while creating a Linked Account.

> [accordion] Invalid IFSC Code
>
> **Code:** `400`
>
> This error occurs when you pass an invalid IFSC code.
>
> **Solution:** Make sure you pass a valid IFSC code.

> [accordion] The name may only contain alphabets, digits and spaces
>
> **Code:** `400`
>
> This error occurs when the name field has anything other than alphabets, digits and spaces.
>
> **Solution:** Make sure you enter a valid name without special characters.

> [accordion] The bank account number must be between 5 and 35 characters
>
> **Code:** `400`
>
> This error occurs when you pass an invalid bank account number.
>
> **Solution:** Make sure to pass a valid account number.

> [accordion] Account\_code -account\_code is not allowed for this merchant
>
> **Code:** `400`
>
> This error occurs when the `account_code` feature is not enabled for the merchant.
>
> **Solution:** Make sure to enable the correct feature for the merchant - `route_code_support`.

> [accordion] Please enter a valid name. Links, emails and HTML tags are not allowed.
>
> **Code:** `400`
>
> This error occurs when the Linked Account name contains URLs, HTML tags, emails and so on.
>
> **Solution:** Ensure you don't send URLs, HTML tags and emails in the Linked Account name.

> [accordion] The code format is invalid.
>
> **Code:** `400`
>
> This error occurs when the `reference_id` format is invalid.
>
> **Solution:** Ensure the `reference_id` format is valid.

> [accordion] The code must be at least 3 characters.
>
> **Code:** `400`
>
> This error occurs when the `reference_id` value has less than a minimum of 3 characters.
>
> **Solution:** The `reference_id` value should be between 3 to 20 characters.

> [accordion] The VPA provided does not exist or is inactive
>
> **Code:** `400`
>
> This error occurs when the VPA address passed in `account_details.vpa.address` does not exist on the UPI network or has been deactivated.
>
> **Solution:** Ask the beneficiary to confirm their UPI id is active. You can also pre-validate the VPA using the [Validate VPA API](https://razorpay.com/docs/api/x/account-validation/vpa.md) before creating the Linked Account.

> [accordion] The VPA address format is invalid
>
> **Code:** `400`
>
> This error occurs when the value passed in `account_details.vpa.address` does not follow the `username@bankname` format.
>
> **Solution:** Make sure the VPA is in the correct format. For example, `gaurav.kumar@paytm` or `9000090000@ybl`.

> [accordion] Transfer amount exceeds the maximum allowed limit for VPA settlements
>
> **Code:** `400`
>
> This error occurs when a transfer to this Linked Account exceeds ₹1,00,000, which is the NPCI-mandated per-transaction limit for UPI payouts.
>
> **Solution:** For amounts above ₹1,00,000, create a separate Linked Account with bank account details and use bank account settlement.

> [accordion] Daily VPA limit exceeded
>
> **Code:** `400`
>
> This error occurs when the cumulative transfers to the beneficiary's VPA have reached the ₹1,00,000 daily limit set by NPCI. The limit resets at midnight IST.
>
> **Solution:** Queue the transfer for processing after midnight, switch to bank account settlement for this beneficiary or ask the beneficiary if they have an alternate UPI id.

> [accordion] Invalid account type
>
> **Code:** `400`
>
> This error occurs when the value passed in `account_details.account_type` is not a recognised account type.
>
> **Solution:** Pass `vpa` as the value for `account_details.account_type` for UPI-based settlement.

> [accordion] VPA Settlements feature not enabled
>
> **Code:** `400`
>
> This error occurs when VPA Settlements have not been enabled for your Route account.
>
> **Solution:** Contact our [Support team](https://razorpay.com/support/#request) to enable VPA Settlements for your account.
