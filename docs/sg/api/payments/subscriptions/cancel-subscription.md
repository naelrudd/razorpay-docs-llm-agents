> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Cancel a Subscription

> Cancel a Subscription using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to cancel a Subscription. You can either cancel the Subscription immediately or at the end of the current billing cycle. Once cancelled, you cannot renew or reactivate it.

* When you cancel a Subscription, the status changes to `cancelled`.
* If you choose to cancel a Subscription at the end of a billing cycle, its status changes to `cancelled` only at the end of the current billing cycle.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/subscriptions/sub_00000000000001/cancel \
-H "Content-Type: application/json" \
-d '{
  "cancel_at_cycle_end": false
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String subscriptionId = "sub_00000000000001";

JSONObject params = new JSONObject();
params.put("cancel_at_cycle_end", true);

Subscription subscription = razorpay.subscriptions.cancel(subscriptionId, params);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$options = array("cancel_at_cycle_end" => true)

$api->subscription->fetch($subscriptionId)->cancel($options);
```

```javascript Node.js theme={null}
var instance = new Razorpay({
  key_id: "YOUR_KEY_ID",
  key_secret: "YOUR_SECRET",
});

var subscriptionId = "sub_00000000000001";

instance.subscriptions.cancel(subscriptionId, {
  cancel_at_cycle_end: true,
});
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

subscriptionId = "sub_1N6I3dbbIrc3wUG"

client.subscription.cancel(subscriptionId, {
 "cancel_at_cycle_end": True
})
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

subscriptionId = "sub_00000000000001"

options = {"cancel_at_cycle_end":0}

Razorpay::Subscription.cancel(subscriptionId,options)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
  "cancel_at_cycle_end": true,
}
body, err := client.Subscription.Cancel("<subscriptionId>", data, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String subscriptionId = "sub_00000000000001";

Dictionary<string, object> param = new Dictionary<string, object>();
param.Add("cancel_at_cycle_end", true);

Subscription subscription = client.Subscription.Fetch(subscriptionId).Cancel(param);
```

```bash CLI theme={null}
# Cancel immediately
razorpay subscriptions cancel sub_ABC123

# Cancel at end of current billing cycle
razorpay subscriptions cancel sub_ABC123 --cancel-at-cycle-end
```

```json Success theme={null}
{
  "id": "sub_00000000000001",
  "entity": "subscription",
  "plan_id": "plan_00000000000001",
  "customer_id": "cust_D00000000000001",
  "status": "cancelled",
  "current_start": 1580453311,
  "current_end": 1581013800,
  "ended_at": 1580288092,
  "quantity": 1,
  "notes":{
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  },
  "charge_at": 1580453311,
  "start_at": 1577385991,
  "end_at": 1603737000,
  "auth_attempts": 0,
  "total_count": 6,
  "paid_count": 1,
  "customer_notify": true,
  "created_at": 1580283117,
  "expire_by": 1581013800,
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
    "description": "Subscription is not cancellable in expired status.",
    "field": "status"
  }
}
```

## Path Parameters

**id** `string` *required*

The unique identifier linked to a Subscription. For example, `sub_00000000000001`.

## Request Parameters

**cancel\_at\_cycle\_end** `boolean`

Use this parameter to cancel a Subscription at the end of a billing cycle. Possible values:

* `true`: Cancel the subscription at the end of the current billing cycle.
* `false` (default): Cancel the subscription immediately.

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

Status of the subscription. Refer to the [life cycle section](https://razorpay.com/docs/sg/payments/subscriptions/states.md) for more details. Possible values:

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

The number of times the plan should be linked to the subscription. For example, if the plan is S$100/user/month and the customer has 5 users, you should pass 5 as the quantity to have the customer charged S$500 (5 x S\$100) monthly. By default, this value is set to 1.

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

> [accordion] Subscription is not cancellable in expired status.
>
> **Code:** `400`
>
> This error occurs when you are trying to cancel a Subscription which is in the expired state.
>
> **Solution:** You cannot cancel a Subscription in the expired state. Ensure that the Subscription is in the active or authenticated state to cancel.

> [accordion] Subscription is not cancellable in cancelled status.
>
> **Code:** `400`
>
> The Subscription has already been cancelled.
>
> **Solution:** Cancel can only be called once per subscription. No further action is needed.

> [accordion] The cancel at cycle end field must be true or false.
>
> **Code:** `400`
>
> A non-boolean value (for example a string like `"yes"`) was passed for `cancel_at_cycle_end`.
>
> **Solution:** Pass `cancel_at_cycle_end` as a boolean (`true`/`false`) or as `1`/`0`.

> [accordion] Subscription cannot be cancelled since no billing cycle is going on.
>
> **Code:** `400`
>
> `cancel_at_cycle_end: true` was passed on a Subscription that does not yet have an active billing cycle (typically when the Subscription is still in the `created` or `authenticated` state and the first charge hasn't fired).
>
> **Solution:** Either cancel immediately by passing `cancel_at_cycle_end: false`, or wait for the first billing cycle to start before requesting cycle-end cancellation.

> [accordion] The subscription is in its final cycle and cannot be cancelled now.
>
> **Code:** `400`
>
> `cancel_at_cycle_end: true` was passed but the Subscription is already in its last billing cycle, so there is no subsequent cycle at the end of which to cancel.
>
> **Solution:** Cancel immediately by passing `cancel_at_cycle_end: false`, or allow the Subscription to complete naturally.

> [accordion] Request failed because another subscription operation is in progress.
>
> **Code:** `400`
>
> A concurrent update, cancel or pause/resume operation is already running for the same Subscription.
>
> **Solution:** Wait a few seconds and retry. Fetch the Subscription to confirm its current state before retrying.
