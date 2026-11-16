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

```bash Curl theme={null}
curl -X POST 'https://api.razorpay.com/v2/accounts' \
     -u [YOUR_KEY_ID]:[YOUR_SECRET] \
     -H "Content-type: application/json" \
     -d '{
   "email":"alex.lim@example.com",
   "phone":"9000090000",
   "type":"route",
   "reference_id":"124124",
   "legal_business_name":"Acme Corp",
   "business_type":"partnership",
   "contact_name":"Alex Lim",
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

```bash CLI theme={null}
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

```json Success theme={null}
{
   "id":"acc_GRWKk7qQsLnDjX",
   "type":"route",
   "status":"created",
   "email":"alex.lim@example.com",
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
   "contact_name":"Alex Lim",
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

```json Failure theme={null}
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
