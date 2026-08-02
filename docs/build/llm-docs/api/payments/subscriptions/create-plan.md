# Create a Plan

**POST** `/v1/plans`

Use this endpoint to create a plan.

### Request

```curl: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/plans \
-H "Content-Type: application/json" \
-d '{
  "period": "weekly",
  "interval": 1,
  "item": {
    "name": "Test plan - Weekly",
    "amount": 69900,
    "currency": "INR",
    "description": "Description for the test plan"
  },
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
}'

```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject planRequest = new JSONObject();
planRequest.put("period","weekly");
planRequest.put("interval",1);
JSONObject item = new JSONObject();
item.put("name","Test plan - Weekly");
item.put("amount",69900);
item.put("currency","INR");
item.put("description","Description for the test plan");
planRequest.put("item",item);
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
planRequest.put("notes",notes);
              
Plan plan = razorpay.plans.create(planRequest);

```php: PHP
$api = new Api($key_id, $secret);

$api->plan->create(array('period' => 'weekly', 'interval' => 1, 'item' => array('name' => 'Test Weekly 1 plan', 'description' => 'Description for the weekly 1 plan', 'amount' => 600, 'currency' => 'INR'),'notes'=> array('key1'=> 'value3','key2'=> 'value2')));

```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.plans.create({
  period: "weekly",
  interval: 1,
  item: {
    name: "Test plan - Weekly",
    amount: 69900,
    currency: "INR",
    description: "Description for the test plan"
  },
  notes: {
    notes_key_1: "Tea, Earl Grey, Hot",
    notes_key_2: "Tea, Earl Grey… decaf."
  }
})

```python: Python
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.plan.create({
    'period': 'weekly',
    'interval': 1,
    'item': {
        'name': 'Test plan - Weekly',
        'amount': 69900,
        'currency': 'INR',
        'description': 'Description for the test plan',
        },
    'notes': {'notes_key_1': 'Tea, Earl Grey, Hot',
              'notes_key_2': 'Tea, Earl Grey... decaf.'}
    })

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {
  "period": "weekly",
  "interval": 1,
  "item": {
    "name": "Test plan - Weekly",
    "amount": 69900,
    "currency": "INR",
    "description": "Description for the test plan"
  },
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  }
}

Razorpay::Plan.create(para_attr)

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data:= map[string]interface{}{
  "period": "weekly",
  "interval": 1,
  "item": map[string]interface{}{
    "name": "Test plan - Weekly",
    "amount": 69900,
    "currency": "INR",
    "description": "Description for the test plan",
  },
  "notes": map[string]interface{}{
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf.",
  },
}
body, err := client.Plan.Create(data, nil)

```csharp: .NET
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary planRequest = new Dictionary();
planRequest.Add("period", "weekly");
planRequest.Add("interval", 1);
Dictionary item = new Dictionary();
item.Add("name", "Test plan - Weekly");
item.Add("amount", 69900);
item.Add("currency", "INR");
item.Add("description", "Description for the test plan");
planRequest.Add("item", item);
Dictionary notes = new Dictionary();
notes.Add("notes_key_1", "Tea, Earl Grey, Hot");
notes.Add("notes_key_2", "Tea, Earl Grey… decaf.");
planRequest.Add("notes", notes);

Plan plan = client.Plan.Create(planRequest);
```bash: CLI
razorpay subscriptions plans create \
  --period monthly \
  --interval 1 \
  --item-name "Monthly Plan" \
  --item-amount 50000 \
  --item-currency INR \
  --item-description "Basic monthly subscription" \
  --note key1="Monthly gym membership"
```

### Response

```json: Success
{
  "id":"plan_00000000000001",
  "entity":"plan",
  "interval":1,
  "period":"weekly",
  "item":{
    "id":"item_00000000000001",
    "active":true,
    "name":"Test plan - Weekly",
    "description":"Description for the test plan - Weekly",
    "amount":69900,
    "unit_amount":69900,
    "currency":"INR",
    "type":"plan",
    "unit":null,
    "tax_inclusive":false,
    "hsn_code":null,
    "sac_code":null,
    "tax_rate":null,
    "tax_id":null,
    "tax_group_id":null,
    "created_at":1580219935,
    "updated_at":1580219935
  },
  "notes":{
    "notes_key_1":"Tea, Earl Grey, Hot",
    "notes_key_2":"Tea, Earl Grey… decaf."
  },
  "created_at":1580219935
}
```json: Failure
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "offer_id is/are not required and should not be sent"
  }
}
```

### Parameters

`period` _mandatory_
: `string` This, combined with `interval`, defines the frequency of the plan. Possible values:
    - `daily`
    - `weekly`
    - `monthly`
    - `quarterly`
    - `yearly`

  
  
**INFO**

**Handy Tips**

You can create custom frequencies while creating a plan. For example, once in 3 weeks.
- For UPI, all undefined frequencies except `daily`, `weekly`, `monthly`, `quarterly` and `yearly` are considered `as-presented`.
- For domestic cards, all undefined frequencies except `weekly`, `monthly` and `yearly` are considered `as-presented` while registering the mandate with banks.
- For Emandate, all defined and undefined frequencies are considered `as-presented` while registering the mandate with banks.

  

`interval` _mandatory_
: `integer` This, combined with `period`, defines the frequency of the plan. If the billing cycle is 2 months, the value should be `2`. For daily plans, the minimum value should be `7`.

`item`
: `object` Details of the plan.

    `name` _mandatory_
    : `string` Name of the plan. For example, `Test Plan`.

    `amount` _mandatory_
    : `integer` Amount for the plan that is to be charged to the subscription in the next billing cycle. For example, `69900` translates to 699.

    `currency` _mandatory_
    : `string` Currency for the payment. For example, `INR`. You can accept payment in any of the [supported currencies](https://razorpay.com/docs/build/llm-docs/payments/international-payments.md#supported-currencies).

    `description` _optional_
    : `string` Description for the plan. For example, `Description for the test plan`.

`notes` _optional_
: `object` Notes you can enter of the contact for future reference. This is a key-value pair. You can enter a maximum of 15 key-value pairs. For example, `"note_key": "Monthly gym membership"`.

### Parameters

`id`
: `string` The unique identifier linked to a plan. For example, `plan_00000000000001`. This ID is used when creating a subscription for a customer.

`entity`
: `string` The entity being created. Here, it is `plan`.

`interval`
: `integer` Used together with `period` to define how often the customer should be charged.

`period`
: `string` Used together with `interval` to define how often the customer should be charged. Possible values:
    - `daily`
    - `weekly`
    - `monthly`
    - `yearly`

`item`
: `array` Details of the plan.

    `id`
    : `string` The unique identifier linked to an item. For example, `item_00000000000001`.

    `name`
    : `string` Name of the plan. For example, `Test Plan`.

    `amount`
    : `integer` Amount for the plan. When you use this plan to create a subscription, the customer will be charged this amount periodically.

    `currency`
    : `string` Currency for the payment. You can accept payment in any of the  [supported currencies](https://razorpay.com/docs/build/llm-docs/payments/international-payments.md#supported-currencies).

    `description`
    : `string` Description for the plan. For example, `Description for the test plan`.

`notes`
: `object` Notes you can enter of the contact for future reference. This is a key-value pair. You can enter a maximum of 15 key-value pairs. For example, `"note_key": "Monthly Gym"`.

`created_at`
: `integer` The Unix timestamp at which the plan was created.

### Errors

Authentication failed
* code: 401
* description: This error occurs when you use incorrect or invalid API Keys.
* solution: Use the right set of API keys.

`offer_id` is/are not required and should not be sent
* code: 400
* description: This error occurs when you are passing `offer_id` parameter in the request body.
* solution: `offer_id` should not be passed in the request body.

 
The amount must be at least INR 1.00.
* code: 400
* description: The amount specified is less than the minimum amount. Currency subunits, such as paise (in the case of INR), should always be greater than 100.
* solution: Enter an amount equal to or greater than the minimum amount, that is 100.

The period field is required.
* code: 400
* description: The `period` field was not included in the request body.
* solution: Pass `period` as one of the supported values (for example `daily`, `weekly`, `monthly`, `yearly`).

Invalid argument for period passed.
* code: 400
* description: The value passed for `period` is not one of the supported values.
* solution: Use one of the supported `period` values: `daily`, `weekly`, `monthly`, `yearly`.

The interval field is required.
* code: 400
* description: The `interval` field was not included in the request body.
* solution: Pass `interval` as a positive integer specifying how many `period` units between each billing cycle.

The interval must be at least 1.
* code: 400
* description: The `interval` value is `0` or negative.
* solution: Pass `interval` as an integer greater than or equal to 1.

The interval must be an integer.
* code: 400
* description: A non-integer value was passed for `interval`.
* solution: Pass `interval` as an integer.

The item id field is required when item is not present.
* code: 400
* description: Neither the `item` object nor an `item_id` was included in the request body.
* solution: Pass either an inline `item` object (with `name`, `amount`, `currency`) or an existing `item_id`.

The name field is required.
* code: 400
* description: The `item.name` field was not included in the inline `item` object.
* solution: Always include `item.name` when passing an inline item.

The amount field is required when unit amount is not present.
* code: 400
* description: Neither `item.amount` nor `item.unit_amount` was included in the request body.
* solution: Pass `item.amount` (in currency subunits) or `item.unit_amount`.

The amount must be valid integer between 0 and 4294967295.
* code: 400
* description: A negative or out-of-range value was passed for `item.amount`.
* solution: Pass `item.amount` as a non-negative integer below `4294967295`.

Currency provided is not supported.
* code: 400
* description: The `item.currency` value is not one of the supported ISO currency codes.
* solution: Use a supported 3-letter ISO currency code (for example, `INR`).

\{any extra field\} is/are not required and should not be sent.
* code: 400
* description: The request body contains fields that are not part of the Plans API schema.
* solution: Only include documented fields in the request body.
