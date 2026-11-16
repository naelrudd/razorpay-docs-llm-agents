> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch a Subscription With ID

> Fetch a Subscription using the unique identifier.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to fetch a Subscription by the unique identifier.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET https://api.razorpay.com/v1/subscriptions/sub_00000000000001 \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String subscriptionId = "sub_00000000000001";

Subscription subscription = razorpay.subscriptions.fetch(subscriptionId);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->subscription->fetch($subscriptionId);
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.subscriptions.fetch(subscriptionId)
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.subscription.fetch(subscriptionId)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

subscriptionId = "sub_00000000000001"

Razorpay::Subscription.fetch(subscriptionId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Subscription.Fetch("<subscriptionId>", nil, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String subscriptionId = "sub_00000000000001";

Subscription subscription = client.Subscription.Fetch(subscriptionId);
```

```bash CLI theme={null}
razorpay subscriptions fetch sub_ABC123
```

```json Success theme={null}
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
  "source": "api",
  "offer_id":"offer_JHD834hjbxzhd38d",
  "remaining_count": 5
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "ub_id%7D is not a valid id"
  }
}
```

## Path Parameters

**id** `string` *required*

The unique identifier linked to a Subscription. For example, `sub_00000000000001`.

## Response Parameters

**id** `string`

The unique identifier of the subscription created. For example, `sub_00000000000001`.

**entity** `string`

The entity being created. Here, it will be `subscription`.

**plan\_id** `string`

The unique identifier for a plan that is linked to the created subscription. For example, `plan_00000000000001`.

**customer\_id** `string`

The unique identifier of the customer linked to the subscription. This is populated automatically once the customer completes the authorisation transaction. For example, `cust_00000000000001`.

**status** `string`

Status of the subscription. Refer to the [life cycle section](https://razorpay.com/docs/payments/subscriptions/states.md) for more details. Possible values:

* `created`
* `authenticated`
* `active`
* `pending`
* `halted`
* `cancelled`
* `completed`
* `expired`

**current\_start** `integer`

Unix timestamp. The start time of the current billing cycle of the subscription. For example, `1581013800`.

**current\_end** `integer`

Unix timestamp. The end time of the current billing cycle of the subscription. For example, `1581013800`.

**ended\_at** `integer`

The timestamp, in Unix format, when the subscription was completed or was cancelled. For example, `1581013800`.

**quantity** `integer`

The number of times the plan should be linked to the subscription. For example, if the plan is ₹100/user/month and the customer has 5 users, you should pass 5 as the quantity to have the customer charged ₹500 (5 x ₹100) monthly. By default, this value is set to 1.

**notes** `object`

Notes you can enter for the contact for future reference. This is a key-value pair. You can enter a maximum of 15 key-value pairs. For example, `"note_key": "Beam me up Scotty”`.

**charge\_at** `integer`

Unix timestamp. This indicates when the next charge on the subscription should be made. For example, `1581013800`.

**offer\_id** `string`

The unique identifier of the offer that should be linked to the subscription. For example, `offer_JHD834hjbxzhd38d`.

**start\_at** `integer`

The timestamp, in Unix format, when the subscription should start. If not passed, the subscription starts immediately after the authorisation payment. For example, `1581013800`.

**end\_at** `integer`

The timestamp, in Unix format, when the subscription should end. For example, `1581013800`.

**auth\_attempts** `integer`

The number of times that the charge for the current billing cycle has been attempted on the card. For example, `2`.

**total\_count** `integer`

The number of billing cycles for which the customer should be charged. For example, `2`. We support subscriptions for a maximum duration of 100 years. The number of billing cycles depends if the subscription is daily, weekly, monthly or yearly.

**paid\_count** `integer`

This indicates the number of billing cycles for which the customer has already been charged. For example, `2`.

**customer\_notify** `boolean`

Indicates whether the communication to the customer would be handled by businesses or Razorpay.

* `true`: Communication handled by Razorpay. Defaults to `true`.
* `false`: Communication handled by businesses.

**created\_at** `integer`

The timestamp, in Unix format, when the subscription was created. For example, `1581013800`.

**expire\_by** `integer`

The timestamp, in Unix format, till when the customer can make the authorisation payment. For example, `1581013800`.

**short\_url** `string`

URL that can be used to make the authorisation payment. For example, `https://rzp.io/i/PWtAiEo`.

**has\_scheduled\_changes** `boolean`

Indicates if the subscription has any scheduled changes. Possible values:

* `true`: Subscription has scheduled changes.
* `false`: Subscription does not have scheduled changes.

**schedule\_change\_at** `string`

Represents when the subscription should be updated. Possible values:

* `now` (default): Updates the subscription immediately.
* `cycle_end`: Updates the subscription at the end of the current billing cycle.

**remaining\_count** `integer`

This indicates the number of billing cycles remaining on the subscription. For example, `2`.

**customer\_contact** `string`

The customer's phone number associated with the subscription.

**customer\_email** `string`

The customer's email address associated with the subscription.

**payment\_method** `string`

The payment method used for the subscription, such as card, emandate, or UPI.

**change\_scheduled\_at** `integer`

Timestamp, in Unix format, when a scheduled update on this subscription is set to take effect. `null` when no update is pending.

**source** `string`

The origin of the subscription. One of `api` (created via API), `dashboard`, or `links`.

## Errors

> [accordion] ub\_id%7D is not a valid id
>
> **Code:** `400`
>
> This error occurs when you are not passing the right `subscription_id` in the API endpoint to fetch a plan based on the id.
>
> **Solution:** Ensure that you are passing the right `subscription_id` in the API endpoint. \
> &#x20;For example, `https://api.razorpay.com/v1/subscriptions/sub_KA8rfWnXwyEw0j`.

> [accordion] The API key/secret provided is invalid.
>
> **Code:** `4xx`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after.

> [accordion] The ID provided is invalid or could not be found.
>
> **Code:** `400`
>
> The `subscription_id` passed in the URL is well-formed but does not exist or does not belong to the requesting merchant.
>
> **Solution:** Use a valid `subscription_id` returned from `POST /v1/subscriptions`. Confirm by fetching the subscription list before retrying.
