> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch All Subscriptions

> Fetch all Subscriptions using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to fetch all the created Subscriptions.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET https://api.razorpay.com/v1/subscriptions \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject params = new JSONObject();
params.put("count","1");

List<Subscription> subscriptions = razorpay.subscriptions.fetchAll(params);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->subscription->all($options);
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.subscriptions.all(options)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

options = {"count": 1}

Razorpay::Subscription.all(options)
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.subscription.all(options)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

options := map[string]interface{}{
    "count": 2,
}
body, err := client.Subscription.All(options, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> paramRequest = new Dictionary<string, object>();
paramRequest.Add("count","1");

List<Subscription> subscription = client.Subscription.All(paramRequest);
```

```bash CLI theme={null}
razorpay subscriptions list --count 10 --skip 0 --plan-id plan_ABC123
```

```json Success theme={null}
{
  "entity": "collection",
  "count": 2,
  "items": [
  {
  "id": "sub_00000000000001",
  "entity": "subscription",
  "plan_id": "plan_00000000000001",
  "customer_id": "cust_D00000000000001",
  "status": "active",
  "current_start": 1577355871,
  "current_end": 1582655400,
  "ended_at": null,
  "quantity": 1,
  "notes":{
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  },
  "charge_at": 1577385991,
  "offer_id":"offer_JHD834hjbxzhd38d",
  "start_at": 1577385991,
  "end_at": 1603737000,
  "auth_attempts": 0,
  "total_count": 6,
  "paid_count": 1,
  "customer_notify": true,
  "created_at": 1577356081,
  "expire_by": 1577485991,
  "short_url": "https://rzp.io/i/z3b1R61A9",
  "has_scheduled_changes": false,
  "change_scheduled_at": null,
  "remaining_count": 5
  },
  {
  "id": "sub_00000000000002",
  "entity": "subscription",
  "plan_id": "plan_00000000000001",
  "customer_id":"cust_D00000000000001",
  "status": "active",
  "current_start": 1577355871,
  "current_end": 1577355871,
  "ended_at": null,
  "quantity": 1,
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  },
  "charge_at": 1561852800,
  "start_at": 1561852800,
  "end_at": 1590777000,
  "auth_attempts": 0,
  "total_count": 12,
  "paid_count": 1,
  "customer_notify": true,
  "created_at": 1560241235,
  "expire_by": 1561939199,
  "short_url": "https://rzp.io/i/m0y0f",
  "has_scheduled_changes": false,
  "change_scheduled_at": null,
  "source": "api",
  "offer_id":"offer_JHD834hjbxzhd38d",
  "remaining_count": 11
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

**plan\_id** `string`

The unique identifier of the plan for which you want to retrieve all the Subscriptions.

**from** `integer`

The Unix timestamp from when Subscriptions are to be fetched.

**to** `integer`

The Unix timestamp till when Subscriptions are to be fetched.

**count** `integer`

The number of Subscriptions to be fetched. Default value is `10`. Maximum value is 100. This can be used for pagination, in combination with `skip`.

**skip** `integer`

The number of Subscriptions to be skipped. Default value is `0`. This can be used for pagination, in combination with `count`.

## Response Parameters

**id** `string`

The unique identifier linked to a Subscription.

**entity** `string`

The entity being created. Here, it is `subscription`.

**plan\_id** `string`

The unique identifier of a plan that should be linked to the Subscription. For example, `plan_00000000000001`.

**customer\_id** `string`

The unique identifier of the customer who is subscribing to a plan. This is populated automatically after the customer completes the authorisation transaction.

**total\_count** `integer`

The number of billing cycles for which the customer should be charged. For example, if a customer is buying a 1-year subscription billed on a bi-monthly basis, this value should be `6`.

**customer\_notify** `boolean`

Indicates whether the communication to the customer would be handled by businesses or Razorpay. Possible values:

* `true` (default): Communication handled by Razorpay.
* `false`: Communication handled by businesses.

**start\_at** `integer`

The Unix timestamp, indicates from when the Subscription should start. If not passed, the Subscription starts immediately after the authorisation payment. For example, `1581013800`. For Subscriptions with a future start\_date, frequency is considered `as_presented`.

**quantity** `integer`

The number of times the customer should be charged the plan amount per invoice. For example, a customer subscribes to use software. The charges are S$100/month/license. The customer wants 5 licenses. You should pass 5 as the quantity. The customer is charged S$500 (5 x S\$100) monthly. By default, this value is set to `1`.

**notes** `object`

Object consisting of key value pairs as notes.

**status** `string`

Status of the Subscription. Possible values:

* `created`
* `authenticated`
* `active`
* `pending`
* `halted`
* `cancelled`
* `completed`
* `expired`

Know more about [Subscriptions States](https://razorpay.com/docs/sg/payments/subscriptions/states.md).

**paid\_count** `integer`

Indicates the number of billing cycles the customer has already been charged.

**current\_start** `integer`

Indicates the start time of the current billing cycle of a Subscription.

**current\_end** `integer`

Indicates the end time of the current billing cycle of a Subscription.

**ended\_at** `integer`

The Unix timestamp of when the Subscription has completed its period or has been cancelled midway.

**charge\_at** `integer`

The Unix timestamp of when the next charge on the Subscription should be made.

**auth\_attempts** `integer`

The number of times the charge for the current billing cycle has been attempted on the card.

**expire\_by** `integer`

The Unix timestamp that indicates till when the customer can make the authorisation payment. For example, `1581013800`. The default value is 30 years. Do not pass any value if you do not want to set an expiry date.

**addons** `array of objects`

Array that contains details of any upfront amount you want to collect as part of the authorisation transaction.

**item** `array`

Details of the upfront amount you want to charge your customer.

**name** `string`

A name for the upfront amount you want to charge the customer. For example, `Delivery Fee`.

**amount** `integer`

The upfront amount in the currency subunit you want to charge the customer. For example ,`30000`.

**currency** `string`

The currency in which you want to charge the customer. This has to match the plan currency. For example, `SGD`.

**offer\_id** `string`

The unique identifier of the offer that is linked to the Subscription. You can obtain this from the Dashboard. For example, `offer_JHD834hjbxzhd38d`.

**notes** `object`

Notes you can enter for the contact for future reference. This is a key-value pair. You can enter a maximum of 15 key-value pairs. For example, `"note_key": "Gym Membership Plan`.

**short\_url** `string`

URL that can be used to make the authorisation payment. For example, `https://rzp.io/i/PWtAiEo`.

**has\_scheduled\_changes** `boolean`

Indicates if the Subscription has any scheduled changes. Possible values:

* `true`: Subscription has scheduled changes.
* `false`: Subscription does not have scheduled changes.

**schedule\_change\_at** `string`

Represents when the Subscription should be updated. Possible values:

* `now` (default): Updates the Subscription immediately.
* `cycle_end`: Updates the Subscription at the end of the current billing cycle.

**remaining\_count** `integer`

Indicates the number of billing cycles remaining on the Subscription. For example, `2`.

**customer\_contact** `string`

The customer's phone number associated with the subscription.

**customer\_email** `string`

The customer's email address associated with the subscription.

**payment\_method** `string`

The payment method used for the subscription, such as card, emandate, or UPI.

**change\_scheduled\_at** `integer`

Timestamp, in Unix format, when a scheduled update on this subscription is set to take effect. `null` when no update is pending.

**end\_at** `integer`

Timestamp, in Unix format, when the subscription ended.

**created\_at** `integer`

Timestamp, in Unix format, when the subscription was created. For example, `1778024127`.

**source** `string`

The origin of the subscription. One of `api` (created via API), `dashboard`, or `links`.

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

> [accordion] \{any extra field} is/are not required and should not be sent.
>
> **Code:** `400`
>
> A query parameter that is not part of the fetch-subscriptions schema was passed.
>
> **Solution:** Only pass documented query parameters: `plan_id`, `from`, `to`, `count`, `skip`.

> [accordion] from and to must be UNIX-epoch integers.
>
> **Code:** `400`
>
> A non-integer value (for example a human-readable date like `2024-01-01`) was passed for `from` or `to`. The API returns `The from must be an integer.` or `The to must be an integer.` respectively.
>
> **Solution:** Pass `from` and `to` as UNIX-epoch integers in seconds.
