> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch All Plans

> Fetch details of all plans created using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to fetch details of all plans.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET https://api.razorpay.com/v1/plans \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject params = new JSONObject();
params.put("count","1");

List<Plan> plans =  razorpay.plans.fetchAll(params);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->plan->all($options);
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.plans.all(options)
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.plan.all(options)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

options = {"count": 2}

Razorpay::Plan.all(options)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

options:= map[string]interface{}{
  "count": 1,
  "skip": 1,
}
body, err := client.Plan.All(options, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> paramRequest = new Dictionary<string, object>();
paramRequest.Add("count","1");

List<Plan> plan = client.Plan.All(paramRequest);
```

```bash CLI theme={null}
razorpay subscriptions plans list --count 10 --skip 0
```

```json Success theme={null}
{
  "entity":"collection",
  "count":2,
  "items":[
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
        "currency":"SGD",
        "type":"plan",
        "unit":null,
        "tax_inclusive":false,
        "hsn_code":null,
        "sac_code":null,
        "tax_rate":null,
        "tax_id":null,
        "tax_group_id":null,
        "created_at":1580220492,
        "updated_at":1580220492
      },
      "notes":{
        "notes_key_1":"Tea, Earl Grey, Hot",
        "notes_key_2":"Tea, Earl Grey… decaf."
      },
      "created_at":1580220492
    },
    {
      "id":"plan_00000000000002",
      "entity":"plan",
      "interval":1,
      "period":"monthly",
      "item":{
        "id":"item_00000000000002",
        "active":true,
        "name":"Test plan - Monthly",
        "description":null,
        "amount":79900,
        "unit_amount":79900,
        "currency":"SGD",
        "type":"plan",
        "unit":null,
        "tax_inclusive":false,
        "hsn_code":null,
        "sac_code":null,
        "tax_rate":null,
        "tax_id":null,
        "tax_group_id":null,
        "created_at":1580220483,
        "updated_at":1580220483
      },
      "notes":[],
      "created_at":1580220483
    }
  ]
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "The api key provided is invalid",
    "source": "NA",
    "step": "NA",
    "reason": "NA",
    "metadata": {}
  }
}
```

## Query Parameters

**from** `integer`

The Unix timestamp from when plans are to be fetched.

**to** `integer`

The Unix timestamp till when plans are to be fetched.

**count** `integer`

The number of plans to be fetched. Default value is 10. Maximum value is 100. This can be used for pagination in combination with `skip`.

**skip** `integer`

The number of plans to be skipped. Default value is 0. This can be used for pagination in combination with `count`.

## Response Parameters

**id** `string`

The unique identifier linked to a plan. For example, `plan_00000000000001`. This ID is used when creating a subscription for a customer.

**entity** `string`

The entity being created. Here, it is `plan`.

**interval** `integer`

Used together with `period` to define how often the customer should be charged.

**period** `string`

Used together with `interval` to define how often the customer should be charged. Possible values:

* `daily`
* `weekly`
* `monthly`
* `yearly`

**item** `array`

Details of the plan.

**id** `string`

The unique identifier linked to an item. For example, `item_00000000000001`.

**name** `string`

Name of the plan. For example, `Test Plan`.

**amount** `integer`

Amount for the plan. When you use this plan to create a subscription, the customer will be charged this amount periodically.

**currency** `string`

Currency for the payment. You can accept payment in any of the  [supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).

**description** `string`

Description for the plan. For example, `Description for the test plan`.

**notes** `object`

Notes you can enter of the contact for future reference. This is a key-value pair. You can enter a maximum of 15 key-value pairs. For example, `"note_key": "Monthly Gym"`.

**created\_at** `integer`

The Unix timestamp at which the plan was created.

## Errors

> [accordion] The API key/secret provided is invalid.
>
> **Code:** `4xx`
>
> This error occurs due to a mismatch between the API credentials passed in the API call and those generated on the Dashboard.
>
> **Solution:** Ensure that the API keys are active and correctly entered, with no whitespaces before or after the keys.

> [accordion] count must be an integer between 1 and 100.
>
> **Code:** `400`
>
> An invalid value was passed for the `count` query parameter. The API returns `The count must be at least 1.` (for `count=0` or negative), `The count may not be greater than 100.` (for values above 100), or `The count must be an integer.` (for non-integer values).
>
> **Solution:** Pass `count` as a positive integer between 1 and 100.

> [accordion] skip must be a non-negative integer.
>
> **Code:** `400`
>
> A negative value was passed for the `skip` query parameter.
>
> **Solution:** Pass `skip` as a non-negative integer (0 or higher).

> [accordion] from and to must be UNIX-epoch integers.
>
> **Code:** `400`
>
> A non-integer value (for example a human-readable date like `2024-01-01`) was passed for `from` or `to`. The API returns `from must be an integer.` or `to must be an integer.` respectively.
>
> **Solution:** Pass `from` and `to` as UNIX-epoch integers in seconds.

> [accordion] from and to must be between 946684800 and 5080579200.
>
> **Code:** `400`
>
> The `from` or `to` value is outside the accepted UNIX-timestamp range (corresponds to roughly 2000-01-01 to 2131-01-01). The API returns `from must be between 946684800 and 5080579200` or `to must be between 946684800 and 5080579200` respectively. The bounds are inclusive.
>
> **Solution:** Pass `from` and `to` as UNIX-epoch integers between `946684800` and `5080579200` (inclusive).
