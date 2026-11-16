> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Subscription Link

> Create a Subscription link using the Razorpay API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to create a Subscription link.

> [!WARNING]
>
> **Test Mode Limit**
>
> In test mode, you can create up to 30 Subscription Links per business. If you need to create more than 30 Subscription Links for testing purposes, contact  [Razorpay Support](https://razorpay.com/support/).

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/subscriptions \
-H "Content-Type: application/json" \
-d '{
  "plan_id": "plan_00000000000001",
  "total_count": 12,
  "quantity": 1,
  "start_at": 1561852800,
  "expire_by": 1561939199,
  "customer_notify": true,
  "addons": [
    {
    "item": {
      "name": "Delivery charges",
      "amount": 30000,
      "currency": "SGD"
      }
    }
  ],
  "offer_id":"offer_JHD834hjbxzhd38d",
  "notes": {
    "notes_key_1":"Tea, Earl Grey, Hot",
    "notes_key_2":"Tea, Earl Grey… decaf."
  },
  "notify_info":{
    "notify_phone": "<phone>",
    "notify_email": "<email>"
  }
}'
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
Dictionary<string, object> subscriptionRequest = new Dictionary<string, object>();
subscriptionRequest.Add("plan_id", "plan_Z6t7VFTb9xHeOs");
subscriptionRequest.Add("total_count", 12);
subscriptionRequest.Add("quantity", 1);
subscriptionRequest.Add("customer_notify", true);
subscriptionRequest.Add("start_at", 1580453311);
subscriptionRequest.Add("expire_by", 1580626111);
List<Dictionary<string, object>> addons = new List<Dictionary<string, object>>();
Dictionary<string, object> linesItem = new Dictionary<string, object>();
Dictionary<string, object> item = new Dictionary<string, object>();
item.Add("name", "Delivery charges");
item.Add("amount", 30000);
item.Add("currency", "SGD");
linesItem.Add("item", item);
addons.Add(linesItem);
subscriptionRequest.Add("addons", addons);
subscriptionRequest.Add("offer_id", "offer_Z6t7VFTb9xHeOs");
Dictionary<string, object> notes = new Dictionary<string, object>();
notes.Add("notes_key_1", "Tea, Earl Grey, Hot");
notes.Add("notes_key_2", "Tea, Earl Grey… decaf.");
subscriptionRequest.Add("notes", notes);
Dictionary<string, object> notifyInfo = new Dictionary<string, object>();
notifyInfo.Add("notify_phone", "<phone>");
notifyInfo.Add("notify_email", "<email>");
subscriptionRequest.Add("notify_info", notifyInfo);

Subscription subscription = client.Subscription.Create(subscriptionRequest);
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject subscriptionRequest = new JSONObject();
subscriptionRequest.put("plan_id", "plan_HoYg68p5kmuvzD");
subscriptionRequest.put("total_count", 12);
subscriptionRequest.put("quantity", 1);
subscriptionRequest.put("customer_notify", true);
subscriptionRequest.put("start_at", 1580453311);
subscriptionRequest.put("expire_by", 1580626111);
List<Object> addons = new ArrayList<>();
JSONObject linesItem = new JSONObject();
JSONObject item = new JSONObject();
item.put("name","Delivery charges");
item.put("amount",30000);
item.put("currency","SGD");
linesItem.put("item",item);
addons.add(linesItem);
subscriptionRequest.put("addons",addons);
subscriptionRequest.put("offer_id","offer_JTUADI4ZWBGWur");
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_2","Tea, Earl Grey… decaf.");
subscriptionRequest.put("notes", notes);
JSONObject notifyInfo = new JSONObject();
notifyInfo.put("notify_phone","<phone>");
notifyInfo.put("notify_email","<email>");
subscriptionRequest.put("notify_info",notifyInfo);

Subscription subscription = razorpay.subscriptions.create(subscriptionRequest);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->subscription->create(array('plan_id' => 'plan_HoYg68p5kmuvzD','total_count' => 12,'quantity' => 1,'expire_by' => 1633237807,'customer_notify' => true, 'addons' => array(array('item'=>array('name' => 'Delivery charges','amount' => 30000,'currency' => 'SGD'))),'notes'=>array('notes_key_1'=>'Tea, Earl Grey, Hot','notes_key_2'=>'Tea, Earl Grey… decaf.'),'notify_info'=>array('notify_phone' => '<phone>','notify_email'=> '<email>')));
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.subscriptions.create({
  plan_id: "plan_HoYg68p5kmuvzD",
  total_count: 12,
  quantity: 1,
  expire_by: 1633237807,
  customer_notify: true,
  addons: [
    {
      item: {
        name: "Delivery charges",
        amount: 30000,
        currency: "SGD"
      }
    }
  ],
  notes: {
    notes_key_1: "Tea, Earl Grey, Hot",
    notes_key_2: "Tea, Earl Grey… decaf."
  },
  notify_info: {
    notify_phone: "<phone>",
    notify_email: "<email>"
  }
})
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.subscription.create({
    'plan_id': 'plan_HoYg68p5kmuvzD',
    'total_count': 12,
    'quantity': 1,
    'expire_by': 1633237807,
    'customer_notify': True,
    'addons': [{'item': {'name': 'Delivery charges', 'amount': 30000,
               'currency': 'SGD'}}],
    'notes': {'notes_key_1': 'Tea, Earl Grey, Hot',
              'notes_key_2': 'Tea, Earl Grey\xe2\x80\xa6 decaf.'},
    'notify_info': {'notify_phone': '<phone>',
                    'notify_email': '<email>'}
    })
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {
  "plan_id": "plan_HoYg68p5kmuvzD",
  "total_count": 12,
  "quantity": 1,
  "expire_by": 1633237807,
  "customer_notify": 1,
  "addons": [
    {
      "item": {
        "name": "Delivery charges",
        "amount": 30000,
        "currency": "SGD"
      }
    }
  ],
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  },
  "notify_info": {
    "notify_phone": "<phone>",
    "notify_email": "<email>"
  }
}

Razorpay::Subscription.create(para_attr)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
  "plan_id": "plan_00000000000001",
  "total_count": 12,
  "quantity": 1,
  "start_at": 1561852800,
  "expire_by": 1561939199,
  "customer_notify": true,
  "addons": []interface{}{
    map[string]interface{}{
    "item": map[string]interface{}{
      "name": "Delivery charges",
      "amount": 30000,
      "currency": "SGD",
      },
    },
  },
  "offer_id":"offer_JHD834hjbxzhd38d",
  "notes": map[string]interface{}{
    "notes_key_1":"Tea, Earl Grey, Hot",
    "notes_key_2":"Tea, Earl Grey… decaf.",
  },
  "notify_info":map[string]interface{}{
    "notify_phone": "<phone>",
    "notify_email": "<email>",
  },
}
body, err := client.Subscription.Create(data, nil)
```

```bash CLI theme={null}
razorpay subscriptions create \
  --plan-id plan_ABC123 \
  --total-count 6 \
  --notify-info-email "customer@example.com" \
  --notify-info-phone "9999999999" \
  --offer-id offer_ABCD123
```

```json Success theme={null}
{
  "id":"sub_00000000000002",
  "entity":"subscription",
  "plan_id":"plan_00000000000001",
  "status":"created",
  "current_start":null,
  "current_end":null,
  "ended_at":null,
  "quantity":1,
  "notes":{
    "notes_key_1":"Tea, Earl Grey, Hot",
    "notes_key_2":"Tea, Earl Grey… decaf."
  },
  "charge_at":1580453311,
  "start_at":1580453311,
  "end_at":1587061800,
  "auth_attempts":0,
  "total_count":12,
  "paid_count":0,
  "customer_notify":true,
  "created_at":1580283117,
  "expire_by":1581013800,
  "short_url":"https://rzp.io/i/m0y0f",
  "has_scheduled_changes":false,
  "change_scheduled_at":null,
  "source": "api",
  "offer_id":"offer_JHD834hjbxzhd38d",
  "remaining_count":12
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "Link expire by cannot be lesser than the current time."
  }
}
```

## Request Parameters

**plan\_id** `string` *required*

The unique identifier of a plan that should be linked to the Subscription. For example, `plan_00000000000001`.

**total\_count** `integer` *required*

The number of billing cycles for which the customer should be charged. For example, if a customer is buying a 1-year subscription billed on a bi-monthly basis, this value should be `6`.

**quantity** `integer`

The number of times the customer should be charged the plan amount per invoice. For example, a customer subscribes to use software. The charges are S$100 /month/license. The customer wants 5 licenses. You should pass `5` as the quantity. The customer is charged S$500 (5 x S\$100) monthly. By default, this value is set to `1`.

**start\_at** `integer`

Unix timestamp that indicates from when the Subscription should start. If not passed, the Subscription starts immediately after the authorisation payment. For example, `1581013800`. For Subscriptions with a future start\_date, frequency is considered `as_presented`.

**expire\_by** `integer`

Unix timestamp that indicates till when the customer can make the authorisation payment. For example, `1581013800`. The default value is 30 years. Do not pass any value if you do not want to set an expiry date.

**customer\_notify** `boolean`

Indicates whether the communication to the customer would be handled by businesses or Razorpay. Possible values:

* `true` (default): Communication handled by Razorpay.
* `false`: Communication handled by businesses.

**addons** `object`

Array that contains details of any upfront amount you want to collect as part of the authorisation transaction.

**item** `object`

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

Notes you can enter for the contact for future reference. This is a key-value pair. You can enter a maximum of 15 key-value pairs. For example, `"note_key": "Beam me up Scotty”`.

**notify\_info** `object`

The customer's email and phone number to which notifications are to be sent. Use this array only if you have set the `customer_notify` parameter to `true`. That is, Razorpay sends notifications to the customer. The customer details entered in the API request are only to notify the customer about the Subscription. The same will not be prefilled in the checkout as per the government guidelines.

**notify\_phone** `string`

The customer's phone number.

**notify\_email** `string`

The customer's email.

You can perform various actions related to Subscriptions using the Dashboard.

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

## Errors

> [accordion] Link expire by cannot be lesser than the current time.
>
> **Code:** `400`
>
> This error occurs when the time mentioned in the `expire_by` parameter has already passed. For example, if today's date is December 12, 2022, but the expiry date is mentioned as December 10, 2022.
>
> **Solution:** Ensure that the time passed in the `expiry_by` parameter occurs after the current time at the time of creating the Subscription link.

> [accordion] The requested URL was not found on the server.
>
> **Code:** `400`
>
> This error occurs when the Subscriptions feature is not enabled.
>
> **Solution:** Ensure that the [Subscriptions feature](https://razorpay.com/docs/payments/dashboard/account-settings/checkout-features.md#flash-checkout) is enabled both in the test and live modes before creating a Subscription.

> [accordion] The id provided does not exist
>
> **Code:** `400`
>
> This error occurs when passing an incorrect `plan_id`.
>
> **Solution:** Ensure that you are passing the correct `plan_id`. The plan should be active and created using the same API key and Secret.

> [accordion] Offer Not Found
>
> **Code:** `400`
>
> This error occurs when you are linking an invalid/expired offer to a Subscription.
>
> **Solution:** Ensure that the Subscription offer created on the Dashboard is valid and has not expired.

> [accordion] Offer not applicable for this Subscription
>
> **Code:** `400`
>
> This error occurs when you are linking/passing an `offer_id` to a Subscription on which the offer doesn't apply.
>
> **Solution:** Ensure that the plan amount is greater than the minimum amount set for the offer.

> [accordion] The plan id field is required.
>
> **Code:** `400`
>
> The `plan_id` was not included in the request body.
>
> **Solution:** Pass `plan_id` (the id of an active plan in the same account).

> [accordion] The plan id must be 19 characters.
>
> **Code:** `400`
>
> The value passed for `plan_id` is not 19 characters long (the expected `plan_<14 alphanumeric chars>` format).
>
> **Solution:** Pass `plan_id` in the form `plan_<14 alphanumeric chars>`.

> [accordion] The plan id must be at least 14 characters.
>
> **Code:** `400`
>
> The value passed for `plan_id` is shorter than the minimum-id payload length. Returned for short or malformed plan ids.
>
> **Solution:** Pass a well-formed `plan_id`.

> [accordion] The total count field is required when end at is not present.
>
> **Code:** `400`
>
> Neither `total_count` nor `end_at` was included in the request body. At least one is required to bound the subscription.
>
> **Solution:** Pass either `total_count` (number of billing cycles) or `end_at` (UNIX timestamp).

> [accordion] The total count must be at least 1.
>
> **Code:** `400`
>
> `total_count` was passed as `0` or a negative value.
>
> **Solution:** Pass `total_count` as a positive integer (1 or higher).

> [accordion] The total count must be an integer.
>
> **Code:** `400`
>
> A non-integer value was passed for `total_count`.
>
> **Solution:** Pass `total_count` as an integer.

> [accordion] The quantity must be at least 1.
>
> **Code:** `400`
>
> `quantity` was passed as `0` or a negative value.
>
> **Solution:** Pass `quantity` as a positive integer (1 or higher).

> [accordion] start\_at cannot be lesser than the current time.
>
> **Code:** `400`
>
> `start_at` is set to a past UNIX timestamp.
>
> **Solution:** Pass `start_at` as a UNIX timestamp in the future.

> [accordion] The customer notify field must be true or false.
>
> **Code:** `400`
>
> A non-boolean value (for example a string like `"maybe"`) was passed for `customer_notify`.
>
> **Solution:** Pass `customer_notify` as a boolean (`true`/`false`) or as `1`/`0`.

> [accordion] \{any extra field} is/are not required and should not be sent.
>
> **Code:** `400`
>
> The request body contains fields that are not part of the Subscriptions API schema.
>
> **Solution:** Only include documented fields in the request body.

> [accordion] Please provide either an end date or a total count, but not both.
>
> **Code:** `400`
>
> Both `end_at` and `total_count` were sent together. The subscription end can be defined either by an explicit end date or by a count of cycles, not both.
>
> **Solution:** Pass either `end_at` or `total_count`, but not both.
