> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Standard Web Integration - Configurability of Payment Methods

> Configure and restrict the payment methods of your choice on Razorpay Curlec Checkout.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Razorpay Curlec Standard Checkout hosts a variety of payment methods for customers to make payments. The order of these payment methods on the Checkout used to be fixed and could not be interchanged. There can be situations where you want certain payment methods to be shown more prominently, or to rearrange the order in which they are displayed on the Checkout.

You can configure the payment methods of your choice on the Checkout to provide a personalised experience for your customers, and you can restrict payments to only the instruments you want to accept.

## Use Cases

You can configure the payment methods depending on your use case.

* Highlighting certain payment instruments on the Checkout.\
  For example, **Maybank** could be displayed outside the FPX block as a separate payment method. Similarly, **Touch 'n Go** can be pulled out of the wallet block.
* Restricting the network, issuer, BIN and card type to accept payments from.\
  For example, you can choose to accept payments only from **CIMB Visa Debit cards** on the Checkout.
* Removing a certain payment method or instrument.\
  For example, **Boost** can be removed as a payment method from wallets. The entire **FPX** block, or a certain bank within FPX, can be removed from the Checkout.
* Reordering of payment methods on the Checkout.\
  You can choose to have **FPX** as the first section instead of **Cards** on the Checkout.
* Grouping of payment instruments.\
  For example, you can group the **FPX** and **card** payment methods of a bank into a block labelled **Pay via Bank** on the Checkout.

## Configuring Payment Methods

Depending on how you want to control the payment methods on the Checkout, there are different ways in which the configuration can be passed to the Checkout:

* Pass the configuration in the `options` parameter of the Checkout code at run time.\
  This is useful when you want to modify the order of the payment methods for a particular set of payments while rendering the Checkout. See the [sample code](#sample-code) for details.
* Create a global setting of the payments as a **Configuration ID** and pass these values while creating the Order.\
  This is useful when you want to fix the order of the payment methods across all Checkout renders.

> [!NOTE]
>
> **Note**
>
> Contact our [Support team](https://curlec.com/support/) for more details about the Configuration ID.

## Understanding the Configuration

The building blocks of a configuration — payment methods, payment instruments, blocks, sequence and preferences — are documented in [Understand the Configuration](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods/understand-configuration.md), along with the instruments available for each method in Malaysia.

## Building the Configuration

This section contains details about the `display` configuration and the `restrictions` configuration.

### Display Configuration

Using the `display` config, you can put together all the modules, that is, `blocks`, `sequence`, `preferences` and `hide` instruments, as shown below.

The `display` config can be passed in the Checkout options or in the [Orders API](https://razorpay.com/docs/my/api/orders/create.md) request using the `checkout_config_id` parameter.

> [!NOTE]
>
> **Handy Tips**
>
> Contact our [Support team](https://curlec.com/support/) to get your `checkout_config_id` parameter.

```javascript display config theme={null}
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
  key: "<YOUR_KEY_ID>",
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

```bash Orders Sample Request theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_SECRET> \
-X POST https://api.razorpay.com/v1/orders \
-H "content-type: application/json" \
-d '{
  "amount": 50000,
  "currency": "MYR",
  "receipt": "receipt#1",
  "checkout_config_id": "config_Ep0eOCwdSfgkco",
  "notes": {
    "reference_no": "IBFA10106201500002"
    }
}'
```

### Restrictions Configuration

Using the `display` config, you can reorder, highlight or hide instruments and methods and display the modules on the Checkout. Using the `restrictions` config, you can accept payments using only certain instruments.

For example, you can use it to accept payments only from specific card networks such as Visa or Mastercard, only from CIMB or Maybank cards, or only from cards of a particular BIN.

To restrict payments, we recommend using the `restrictions` config.

> [!NOTE]
>
> **Feature Request**
>
> This feature is not enabled by default. Raise a request with our [Support team](https://curlec.com/support/) to have it enabled on your account.

The `restrictions` config must be sent in the Orders API request as shown below:

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

Know more about the [Orders API](https://razorpay.com/docs/my/api/orders/create.md).

### Sample Code

Let us assume you want to list all the payment methods offered by **CIMB**, allow card payments for **RHB** only, and hide the `wallet` payment method from the Checkout. You can do so using the code given below:

```html Checkout Code theme={null}
<html>
<button id="rzp-button1" class="btn btn-outline-dark btn-lg"><i class="fas fa-money-bill"></i> Own Checkout</button>
<script src="https://checkout.razorpay.com/v1/checkout.js"></script>
<script>
  var options = {
    "key": "<YOUR_KEY_ID>", // Enter the Key ID generated from the Dashboard
    "amount": "1000",
    "currency": "MYR",
    "description": "Acme Corp",
    "image": "https://cdn.razorpay.com/logos/F9Yhfb7ZXjXmIQ_medium.jpg",
    "prefill":
    {
      "email": "gaurav.kumar@example.com",
      "contact": "+60123456789",
    },
    config: {
      display: {
        blocks: {
          cimb: { //name for CIMB block
            name: "Pay using CIMB Bank",
            instruments: [
              {
                method: "card",
                issuers: ["CIBB"]
              },
              {
                method: "fpx",
                banks: ["CIBB"]
              },
            ]
          },
          other: { //  name for other block
            name: "Other Payment modes",
            instruments: [
              {
                method: "card",
                issuers: ["RHBB"]
              },
              {
                method: 'fpx',
              }
            ]
          }
        },
        hide: [
          {
          method: "wallet"
          }
        ],
        sequence: ["block.cimb", "block.other"],
        preferences: {
          show_default_blocks: false // Should Checkout show its default blocks?
        }
      }
    },
    "handler": function (response) {
      alert(response.razorpay_payment_id);
    },
    "modal": {
      "ondismiss": function () {
        if (confirm("Are you sure, you want to close the form?")) {
          txt = "You pressed OK!";
          console.log("Checkout form closed by the user");
        } else {
          txt = "You pressed Cancel!";
          console.log("Complete the Payment")
        }
      }
    }
  };
  var rzp1 = new Razorpay(options);
  document.getElementById('rzp-button1').onclick = function (e) {
    rzp1.open();
    e.preventDefault();
  }
</script>
</html>
```

## Reference

The banks, card types, wallets and pay later providers you can use in a configuration are listed in [Supported Methods](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods/supported-methods.md).

### Related Information

* [About Payment Methods Configuration](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods.md)
* [Understand the Configuration](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods/understand-configuration.md)
* [Display the Configuration](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods/display-configuration.md)
* [Sample Codes](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods/sample-code.md)
