> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Stakeholder

> Create a Stakeholder using Razorpay Partners APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this API endpoint to create a stakeholder. Know about the [various error responses](https://razorpay.com/docs/api/partners/errors) for this API.

```bash Curl theme={null}
curl -X POST https://api.razorpay.com/v2/accounts/acc_GLGeLkU2JUeyDZ/stakeholders \
-u <ACCESS_TOKEN> \
-H "Content-Type: application/json" \
-d '{
  "percentage_ownership": 10,
  "name": "Gaurav Kumar",
  "email": "gaurav.kumar@example.com",
  "relationship": {
    "director": true,
    "executive": false
  },
  "phone": {
    "primary": "9000090000",
    "secondary": "9000090000"
  },
  "addresses": {
    "residential": {
      "street": "506, Koramangala 1st block",
      "city": "Bengaluru",
      "state": "Karnataka",
      "postal_code": "560034",
      "country": "IN"
    }
  },
  "kyc": {
    "pan": "AVOPB1111K"
  },
  "notes": {
    "random_key_by_partner": "random_value"
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[ACCESS_TOKEN]");

String accountId = "acc_GP4lfNA0iIMn5B";

JSONObject StakeRequest = new JSONObject();
StakeRequest.put("email","gauri.kumari@example.com");
StakeRequest.put("percentage_ownership",10);
StakeRequest.put("name","Gauri Kumari");

JSONObject relationship = new JSONObject();
relationship.put("director",true);
relationship.put("executive",false);

StakeRequest.put("relationship",relationship);

JSONObject phone = new JSONObject();
phone.put("primary","9000090000");
phone.put("secondary","9000090000");

StakeRequest.put("phone",phone);

JSONObject residential = new JSONObject();
residential.put("street","507, Koramangala 6th block");
residential.put("city","Bengaluru");
residential.put("state","Karnataka");
residential.put("postal_code","560047");
residential.put("country","IN");

JSONObject addresses = new JSONObject();
addresses.put("residential",residential);
StakeRequest.put("addresses",addresses);

JSONObject kyc = new JSONObject();
kyc.put("pan","AVOPB1111K");

StakeRequest.put("kyc",kyc);

JSONObject notes = new JSONObject();
notes.put("random_key_by_partner","random_value");

StakeRequest.put("notes",notes);

Stakeholder stakeholder = instance.stakeholder.create(accountId, StakeRequest);
```

```php PHP theme={null}
$api = new Api(null, null, "<ACCESS_TOKEN>");

$accountId = "acc_GP4lfNA0iIMn5B";

$stakeholders = $api->account->fetch($accountId)->stakeholders();

$stakeholders->create(array(
   "percentage_ownership" => 10,
   "name" => "Gaurav Kumar",
   "email" => "gaurav.kumarr@example.com",
   "relationship" => array(
       "director" => true,
       "executive" => false
   ),
   "phone" => array(
       "primary" => "7474747474",
       "secondary" => "7474747474"
   ),
   "addresses" => array(
       "residential" => array(
           "street" => "506, Koramangala 1st block",
           "city" => "Bengaluru",
           "state" => "Karnataka",
           "postal_code" => "560034",
           "country" => "IN"
       )
   ),
   "kyc" => array(
       "pan" => "AVOPB1111K"
   ),
   "notes" => array(
       "random_key_by_partner" => "random_value"
   )
));
```

```javascript Node.js theme={null}
const instance = new Razorpay({
  oauthToken: "<ACCESS_TOKEN>"
);

const accountId = "acc_GP4lfNA0iIMn5B";

instance.stakeholders.create(accountId, {
  "percentage_ownership": 10,
  "name": "Gaurav Kumar",
  "email": "gaurav.kumar@example.com",
  "relationship": {
    "director": true,
    "executive": false
  },
  "phone": {
    "primary": "7474747474",
    "secondary": "7474747474"
  },
  "addresses": {
    "residential": {
      "street": "506, Koramangala 1st block",
      "city": "Bengaluru",
      "state": "Karnataka",
      "postal_code": "560034",
      "country": "IN"
    }
  },
  "kyc": {
    "pan": "AVOPB1111K"
  },
  "notes": {
    "random_key_by_partner": "random_value"
  }
});
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('ACCESS_TOKEN')
accountId = "acc_GP4lfNA0iIMn5B"

Razorpay::Stakeholder.create(accountId, {
  "percentage_ownership": 10,
  "name": "Gaurav Kumar",
  "email": "gaurav.kumar@example.com",
  "relationship": {
    "director": 1,
    "executive": 0
  },
  "phone": {
    "primary": "7474747474",
    "secondary": "7474747474"
  },
  "addresses": {
    "residential": {
      "street": "506, Koramangala 1st block",
      "city": "Bengaluru",
      "state": "Karnataka",
      "postal_code": "560034",
      "country": "IN"
    }
  },
  "kyc": {
    "pan": "AVOPB1111K"
  },
  "notes": {
    "random_key_by_partner": "random_value"
  }
})
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[ACCESS_TOKEN]");

string accountId = "acc_ua2tBezhcEBvap";

Dictionary<string, object> StakeRequest = new Dictionary<string, object>();
StakeRequest.Add("email", "gauriagain.kumar@example.org");
StakeRequest.Add("percentage_ownership", 10);
StakeRequest.Add("name", "Gaurav Kumar");

Dictionary<string, object> relationship = new Dictionary<string, object>();
relationship.Add("director", true);
relationship.Add("executive", false);

StakeRequest.Add("relationship", relationship);

Dictionary<string, object> phone = new Dictionary<string, object>();
phone.Add("primary", "9999999999");
phone.Add("secondary", "9999999999");

StakeRequest.Add("phone", phone);

Dictionary<string, object> residential = new Dictionary<string, object>();
residential.Add("street", "507, Koramangala 6th block");
residential.Add("city", "Bengaluru");
residential.Add("state", "Karnataka");
residential.Add("postal_code", "560047");
residential.Add("country", "IN");

Dictionary<string, object> addresses = new Dictionary<string, object>();
addresses.Add("residential", residential);
StakeRequest.Add("addresses", addresses);

Dictionary<string, object> kyc = new Dictionary<string, object>();
kyc.Add("pan", "AVOPB1111K");

StakeRequest.Add("kyc", kyc);

Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("random_key_by_partner", "random_value");

StakeRequest.Add("notes", notes);

Stakeholder stakeholder = client.Stakeholder.Create(accountId, StakeRequest);
```

```json Success theme={null}
{
  "entity": "stakeholder",
  "relationship": {
    "director": true
  },
  "phone": {
    "primary": "9000090000",
    "secondary": "9000090000"
  },
  "notes": {
    "random_key_by_partner": "random_value"
  },
  "kyc": {
    "pan": "AVOPB1111K"
  },
  "id": "sth_GLGgm8fFCKc92m",
  "name": "Gaurav Kumar",
  "email": "gaurav.kumar@example.com",
  "percentage_ownership": 10,
  "addresses": {
    "residential": {
      "street": "506, Koramangala 1st block",
      "city": "Bengaluru",
      "state": "Karnataka",
      "postal_code": "560034",
      "country": "IN"
    }
  }
}
```

## Path Parameters

**account\_id** `string`

The unique identifier of the sub-merchant account generated by Razorpay. For example, `acc_GLGeLkU2JUeyDZ`. This id is used to fetch or update a stakeholder. The stakeholder is created for this sub-merchant account id.

## Request Parameters

**name** `string` *required*

The stakeholder's name as per the PAN card. The maximum length is 255 characters.

**email** `string`

The stakeholder's email address. The maximum length is:

* local part (before @): 64 characters.
* domain part (after @): 68 characters. \
  &#x20;The total character length supported is 132.

**percentage\_ownership** `float`

The stakeholder's ownership of the business in percentage. Only two decimal places are allowed. For example, `87.55`. The maximum length is 100 characters.

**relationship** `object`

The stakeholder's relationship with the account's business.

**director** `boolean`

Determines if stakeholder is a director of the account's legal entity.

* `true`: Stakeholder is a director.
* `false` (default): Stakeholder is not a director.

**executive** `boolean`

Determines if the stakeholder is an executive of the account's legal entity.

* `true`: Stakeholder is an executive.
* `false` (false): Stakeholder is not an executive.

**phone** `object`

The stakeholder's phone number.

**primary** `integer`

The primary contact number of the stakeholder. The minimum length is 8 characters and the maximum length is 11.

**secondary** `integer`

The secondary contact number of the stakeholder. The minimum length is 8 characters and the maximum length is 11.

**addresses** `object`

Details of stakeholder's address.

**residential** `object`

Details of the stakeholder's residential address.

**street** `string`

The stakeholder's street address. The minimum length is 10 characters and maximum length is 255.

**city** `string`

The city. The minimum length is 2 and maximum length is 32.

**state** `string`

The state. The minimum length is 2 and maximum length is 32.

**postal\_code** `string`

The postal code. The minimum length is 2 and maximum length is 10.

**country** `string`

The country. The minimum length is 2 and maximum length is 64. This can either be a country code in capital letters or the full name of the country in lower case letters. For example, for India, you must write either `IN` or `india`. [List of supported Countries](https://razorpay.com/docs/partners/aggregators/onboarding-api/appendix.md#country-list).

**kyc** `object`

The type of document required to establish the stakeholder's identity.

**pan** `string`

The PAN number of the stakeholder.\\

* This is a 10-digit alphanumeric code. For example, `AVOPB1111K`.
* **Regex to validate Stakeholder PAN**: `/^[a-zA-z]{5}\d{4}[a-zA-Z]{1}$/`.
* **Validation for Stakeholder PAN**: The 4th digit should be 'P'.
* If the business type is HUF, the karta's PAN should be provided.

**notes** `object`

Contains user-defined fields stored by the partner for reference purposes. Maximum 15 key-value pairs, 512 characters (maximum) each.

## Response Parameters

**id** `string`

The unique identifier of the stakeholder whose details are created. For example, `sth_GLGgm8fFCKc92m`.

**percentage\_ownership** `float`

The stakeholder's ownership of the business in percentage. Only two decimal places are allowed. For example, `87.55`. The maximum length is 100 characters.

**name** `string`

The stakeholder's name as per the PAN card. The maximum length is 255 characters.\\

**email** `string`

The stakeholder's email address. The maximum length is:

* local part (before @): 64 characters.
* domain part (after @): 68 characters. \
  &#x20;The total character length supported is 132.

**relationship** `object`

The stakeholder's relationship with the account's business.

**director** `boolean`

Determines if stakeholder is a director of the account's legal entity.

* `true`: Stakeholder is a director.
* `false` (default): Stakeholder is not a director.

**executive** `boolean`

Determines if the stakeholder is an executive of the account's legal entity.

* `true`: Stakeholder is an executive.
* `false` (false): Stakeholder is not an executive.

**phone** `object`

The stakeholder's phone number.

**primary** `integer`

The primary contact number of the stakeholder. The minimum length is 8 characters and the maximum length is 11.

**secondary** `integer`

The secondary contact number of the stakeholder. The minimum length is 8 characters and the maximum length is 11.

**addresses** `object`

Details of stakeholder's address.

**residential** `string`

Details of the stakeholder's residential address.

**street** `string`

The stakeholder's street address. The minimum length is 10 characters and maximum length is 255.

**city** `string`

The city. The minimum length is 2 and maximum length is 32.

**state** `string`

The state. The minimum length is 2 and maximum length is 32.

**postal\_code** `string`

The postal code. The minimum length is 2 and maximum length is 10.

**country** `string`

The country. The minimum length is 2 and maximum length is 64. This can either be a country code in capital letters or the full name of the country in lower case letters. For example, for India, you must write either `IN` or `india`. [List of supported Countries](https://razorpay.com/docs/partners/aggregators/onboarding-api/appendix.md#country-list).

**kyc** `object`

The type of document required to establish the stakeholder's identity.

**pan** `string`

The PAN number of the stakeholder.\\

* This is a 10-digit alphanumeric code. For example, `AVOPB1111K`.

* **Regex to validate Stakeholder PAN**: `/^[a-zA-z]{5}\d{4}[a-zA-Z]{1}$/`

* **Validation for Stakeholder PAN**: The 4th digit should be 'P'.\\

* If the business type is HUF, the karta's PAN should be provided.

* This API parameter might be required to complete the KYC process, however, it is optional for this API.

**notes** `object`

Contains user-defined fields stored by the partner for reference purposes. It can hold a maximum of 15 key-value pairs, 512 characters (maximum) each. For example, "note\_key": "Beam me up Scotty”.
