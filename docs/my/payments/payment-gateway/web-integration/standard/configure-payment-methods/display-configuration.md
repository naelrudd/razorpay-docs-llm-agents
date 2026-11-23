> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Display the Configuration

> Display the configured payment methods on Razorpay Curlec Checkout.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

The `display` configuration can be passed in the Checkout options.

You can use the `display` configuration to put together all the modules, that is, `blocks`, `sequence`, `preferences`, and `hide` instruments as shown below:

```javascript display configuration theme={null}
let config = {
  display: {
    blocks: {
      code: {
        name: "The name of the block", // The title of the block
        instruments: [instrument, instrument] // The list of instruments
      },

      anotherCode: {
        name: "Another block",
        instruments: [instrument]
      }
    },

    hide: [
      {
        method: "method"
      }
    ],

    sequence: ["block.code"], // The sequence in which blocks and methods should be shown

    preferences: {
      show_default_blocks: true // Should Checkout show its default blocks?
    }
  }
};
```

```javascript JavaScript Checkout options theme={null}
// beginning of the Checkout code
.....

let options = {
  key: "[YOUR_KEY_ID]",
  amount: 60000,
  currency: "MYR",

  config: {
    display: {
      // The display config
    }
  }
};

let razorpay = new Razorpay(options);

razorpay.open();
....
//rest of the Checkout code
```

## Checkout options

Descriptions for the checkout options parameters are present in the [Checkout Options](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/integration-steps.md#2-3-checkout-options) table.

## Orders API Sample Code

Given below is the sample code:

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X POST https://api.razorpay.com/v1/orders
-H "content-type: application/json"
-d '{
  "amount": 50000,
  "currency": "MYR",
  "receipt": "receipt#1",
  "checkout_config_id": "config_Ep0eOCwdSfgkco"
}'
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.order.create({
  "amount": 50000,
  "currency": "MYR",
  "receipt": "receipt#1",
  "checkout_config_id": "config_Ep0eOCwdSfgkco"
 })
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->order->create(array('receipt' => 'receipt#1', 'amount' => 50000, 'currency' => 'MYR', 'checkout_config_id' => 'config_Ep0eOCwdSfgkco'));
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> options = new Dictionary<string,object>();
options.Add("amount", 50000); // amount in the smallest currency unit
options.Add("receipt", "receipt#1");
options.Add("currency", "MYR");
options.Add("checkout_config_id", "config_Ep0eOCwdSfgkco");
Order order = client.Order.Create(options);
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.orders.create({
  amount: 50000,
  currency: "MYR",
  receipt: "receipt#1",
  checkout_config_id: "config_Ep0eOCwdSfgkco"
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
  "amount": 50000,
  "currency": "MYR",
  "receipt": "receipt#1",
  "checkout_config_id": "config_Ep0eOCwdSfgkco"
}
body, err := client.Order.Create(data, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

order = Razorpay::Order.create amount: 50000, currency: 'MYR', receipt: 'receipt#1', checkout_config_id: 'config_Ep0eOCwdSfgkco'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject orderRequest = new JSONObject();
orderRequest.put("amount", 50000); // amount in the smallest currency unit
orderRequest.put("currency", "MYR");
orderRequest.put("receipt", "receipt#1");
orderRequest.put("checkout_config_id", "config_Ep0eOCwdSfgkco");

Order order = razorpay.orders.create(orderRequest);
```

```json Response theme={null}
{
  "id": "order_EKwxwAgItmmXdp",
  "entity": "order",
  "amount": 50000,
  "amount_paid": 0,
  "amount_due": 50000,
  "currency": "MYR",
  "receipt": "receipt#1",
  "offer_id": null,
  "status": "created",
  "attempts": 0,
  "notes": [],
  "created_at": 1582628071
}
```

Know more about [Orders API](https://razorpay.com/docs/my/api/orders/create.md).

#### Request Parameters

Descriptions for the request parameters are present in the [Create an Order Request Parameters](https://razorpay.com/docs/my/api/orders/create.md) table.

#### Response Parameters

Descriptions for the response parameters are present in the [Orders Entity](https://razorpay.com/docs/my/api/orders/entity.md) parameters table.

### Related Information

* [Supported Methods](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods/supported-methods.md)
* [Sample Codes](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods/sample-code.md)
