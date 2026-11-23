> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Cancel an Update

> Cancel an update using the Razorpay Curlec API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to cancel a pending update. This happens when a Subscription is updated using the `end of cycle` option for the `schedule_change_at` parameter.\


**Example**\


A Subscription is to be charged on the 1st of every month. It was charged on January 01, 2021. On January 15, 2021, it was updated using the `end of cycle` option for the `schedule_change_at` parameter. In this case, the update goes live after the Subscription is charged on February 01, 2021. Such updates are said to be scheduled updates and can be cancelled using this API.

> [!NOTE]
>
> **Handy Tips**
>
> You can only cancel a pending update for a subscription. You cannot cancel an update once it is live.

```bash Curl theme={null}
curl -u <YOUR_KEY>:<YOUR_SECRET> \
-X POST https://api.razorpay.com/v1/subscriptions/sub_00000000000001/cancel_scheduled_changes \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String subscriptionId = "sub_00000000000001";

Subscription subscription = razorpay.subscription.cancelPendingUpdate(subscriptionId);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->subscription->fetch($subscriptionId)->cancelScheduledChanges();
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.subscriptions.cancelScheduledChanges(subscriptionId)
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.subscription.cancel_scheduled_changes(subscriptionId)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

subscriptionId = "sub_00000000000001"

Razorpay::Subscription.cancel_scheduled_changes(subscriptionId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Subscription.CancelScheduledChanges("<subscriptionId>", nil, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string subscriptionId = "sub_00000000000001";

Subscription subscription = client.Subscription.Fetch(subscriptionId).CancelPendingUpdate();
```

```bash CLI theme={null}
razorpay subscriptions cancel-update sub_ABC123
```

```json Success theme={null}
{
  "id": "sub_00000000000001",
  "entity": "subscription",
  "plan_id": "plan_00000000000003",
  "customer_id": "cust_00000000000001",
  "status": "active",
  "current_start": 1580284732,
  "current_end": 1580841000,
  "ended_at": null,
  "quantity": 1,
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  },
  "charge_at": 1580841000,
  "start_at": 1580284732,
  "end_at": 1611081000,
  "auth_attempts": 0,
  "total_count": 6,
  "paid_count": 1,
  "customer_notify": true,
  "created_at": 1580284702,
  "expire_by": 1580626111,
  "short_url": "https://rzp.io/i/fFWTkbf",
  "has_scheduled_changes": false,
  "change_scheduled_at": 1527858600,
  "source": "api",
  "offer_id":"offer_JHD834hjbxzhd38d",
  "remaining_count": 5,
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

Status of the subscription. Refer to the [life cycle section](https://razorpay.com/docs/my/payments/subscriptions/states.md) for more details. Possible values:

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

The number of times the plan should be linked to the subscription. For example, if the plan is RM 100/user/month and the customer has 5 users, you should pass 5 as the quantity to have the customer charged RM 500 (5 x RM 100) monthly. By default, this value is set to 1.

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

Indicates whether the communication to the customer would be handled by businesses or Razorpay Curlec.

* `true`: Communication handled by Razorpay Curlec. Defaults to `true`.
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

## Errors

> [accordion] The API key/secret provided is invalid.
>
> **Code:** `4xx`
>
> This error occurs due to a mismatch between the API credentials passed in the API call and those generated on the Dashboard.
>
> **Solution:** Ensure that the API keys are active and correctly entered, with no whitespaces before or after the keys.

> [accordion] No Pending update for this subscription.
>
> **Code:** `400`
>
> There is no scheduled update on the subscription to cancel. This endpoint is only meaningful after a `PATCH /v1/subscriptions/:id` with a `schedule_change_at` value.
>
> **Solution:** Schedule an update first via the Update Subscription endpoint, then call this endpoint to cancel it before it takes effect.

> [accordion] The id provided is invalid or could not be found.
>
> **Code:** `400`
>
> The subscription id in the URL is malformed (for example a wrong-prefix id like `pay_...`) or does not exist.
>
> **Solution:** Pass a valid subscription id (`sub_<14 alphanumeric chars>`).
