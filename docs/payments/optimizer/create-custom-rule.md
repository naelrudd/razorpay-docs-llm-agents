> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create Custom Rules

> Create custom rules on Optimizer.

Available in
🇮🇳 India

You can create a set of custom rules for transactions using different parameters such as payment method, card type, and so on. Also, you can add gateways in priority order and split traffic between gateways.

Let us assume you want to set up a custom rule wherein:

| Priority Levels | Transaction Split - Payment Gateway/Provider |
| - | - |
| Priority 1 | • 80% of transactions to be routed via Razorpay • 20% of transactions to be routed via ABC |
| Priority 2 | • 100% of transactions to be routed via XYZ |

This means that if the success rate of Razorpay and ABC drops below a certain level, all transactions will automatically be routed to XYZ.

## Steps

To set up the custom rule:

1. Click **+Add New Rule**.
2. In the **Create Rule** screen, add the rule details:
   1. **Rule Name** - Add a name for the rule. For example, `VISA Card Transactions`.
   2. **Rule Description** - Enter a description. For example, `Route 80% of all VISA card transactions via Razorpay`. \


![Create Custom Rules](https://razorpay.com/docs/build/browser/assets/images/optimizer-create-custom-rule.jpg)

3. Click **Next**.
4. Add the rule conditions:

| Field | Possible Values |
| - | - |
| When | • Channels (Website, Android, iOS) • Payment Method (Card, Netbanking and UPI) • BIN Number (Card IIN Number) • Card Type (Debit, Credit, Prepaid, Corporate) • Card Brand (American Express, Diners Club, Discover and so on) • Card Issuer (SBIN, HDFC, ICIC, UTIB, KKBK) • Banks (SBIN, HDFC, ICIC, UTIB) • Amount (In Rupees) • Custom Identifier 1 • Custom Identifier 2 • Custom Identifier 3  |

> [!NOTE]
>
> **Custom Identifiers**  \
> &#x20;Know more about [custom identifiers](#custom-identifiers).

|
\| Is | \
• One of \
• Equal to \
• Not equal to \
• Between \
• Starting with \
• Ending with \
• Less than \
• Greater than \
• Contains \
• Greater than equal \
• Less than equal |
\| Select Comparing Value | Depends on the **When** field value. |

Continuing with our VISA card rule example, the values will be as follows:

1. **When** - Select `Card Brand`.
2. **is** - Select `Equal to`.
3. **Select Comparing Value** - Select `VISA`.
4. Click **Next**.

![Add Custom Rule Conditions](https://razorpay.com/docs/build/browser/assets/images/optimizer-add-custom-rule-condition.jpg)

5. Add the target payment provider through which the transactions should be routed:
   1. Click **Edit Target Provider** to set the priority.
   2. Enter the following details:
      1. For example, for Razorpay gateway, provide the values for **Route** as 80 and **payment via** as `Razorpay`.
      2. Click **Add Another Provider**.
      3. For example, for ABC gateway, provide the values for **Route** as 20 and **payment via** as `ABC`.
   3. You can choose to add another provider as Priority 2. To do this, click **Add Priority** and enter the following details:
      1. For example, for XYZ gateway, provide the values for **Route** as 100 and **payment via** as `XYZ`.
   4. Click **Next**.

![Add Target Provider](https://razorpay.com/docs/build/browser/assets/images/optimizer-target-provider.jpg)

6. Click **Publish Rule** to publish immediately. Alternatively, you can save the rule in draft state and publish later.

![Publish Rule](https://razorpay.com/docs/build/browser/assets/images/optimizer-publish-rule.jpg)

## Custom Identifiers

Custom identifiers are texts (strings) that can be used to construct routing rules. For instance, you can use custom identifiers to route transactions through Razorpay when you pass a custom text `xyz` and to PayU when you pass the text `abc`.

> [!WARNING]
>
> **Watch Out!**
>
> Custom identifiers are case-sensitive. Ensure that the values you pass in the `notes` object match exactly with the values configured in your routing rules. For example, `xyz` and `XYZ` are treated as different identifiers.

**How to send the values for custom identifier?** \

There are three field defined for custom identifiers:

1. optimizer\_identifier\_1
2. optimizer\_identifier\_2
3. optimizer\_identifier\_3

These fields can be sent within the notes object of the payment or order request. If this field is sent into the order request, it will be copied in the payment requests corresponding to the order id. This is done to ensure that you have both the options available. We recommend adding these fields in the order request since its more secure.

### Sample Code

Given below are sample codes which show how the `notes` parameter should be passed in the Orders API and the Standard Checkout code:

#### Orders API

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/orders \
-H "content-type: application/json" \
-d '{
  "amount": 50000,
  "currency": "INR",
  "receipt": "receipt#1",
  "notes": {
    "optimizer_identifier_1": "rzp",
    "optimizer_identifier_2": "payu",
    "optimizer_identifier_3": "atom"
  }
}'
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject orderRequest = new JSONObject();
orderRequest.put("amount", 50000); // amount in the smallest currency unit
orderRequest.put("currency", "INR");
orderRequest.put("receipt", "receipt#1");

JSONObject notes = new JSONObject();
notes.put("optimizer_identifier_1", "rzp");
notes.put("optimizer_identifier_2", "payu");
notes.put("optimizer_identifier_3, atom);
request.put("notes", notes);

Order order = razorpay.orders.create(orderRequest);
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.order.create({
"amount": 50000,
  "currency": "INR",
  "receipt": "receipt#1",
  "notes": {
    "optimizer_identifier_1": "rzp",
    "optimizer_identifier_2": "payu",
    "optimizer_identifier_3": "atom"
  }

 })
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->order->create(array('receipt' => 'receipt#1', 'amount' => 50000, 'currency' => 'INR', 
 'notes' => array( 'optimizer_identifier_1'=> 'rzp', 'optimizer_identifier_2'=> 'payu', 'optimizer_identifier_3'=> 'atom')));
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary<string, object> options = new Dictionary<string,object>();
options.Add("amount", 50000); // amount in the smallest currency unit
options.Add("receipt", "receipt#1");
options.Add("currency", "INR");
notes.optimizer_identifier_1="rzp";
notes.optimizer_identifier_2="payu";
notes.optimizer_identifier_3="atom";
options.Add("notes", notes);
Order order = client.Order.Create(options);
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

order = Razorpay::Order.create amount: 50000, currency: 'INR', receipt: 'receipt#1', "notes": {
    "optimizer_identifier_1": "rzp",
    "optimizer_identifier_2": "payu",
    "optimizer_identifier_3": "atom"
  }
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.orders.create({
  amount: 50000,
  currency: "INR",
  receipt: "receipt#1",
   notes: {
    optimizer_identifier_1: "rzp",
    optimizer_identifier_2: "payu",
    optimizer_identifier_3: "atom"
  }
})
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
	"amount": 50000,
	"currency": "INR",
	"receipt": "receipt#1",
	"notes": map[string]interface{}{
		"optimizer_identifier_1": "rzp",
		"optimizer_identifier_2": "payu",
		"optimizer_identifier_3": "atom",
	},
}
body, err := client.Order.Create(data, nil)
```

#### Standard Checkout

```javascript Standard Checkout Code theme={null}
<button id="rzp-button1">Pay</button>
<script src="https://checkout.razorpay.com/v1/checkout.js"></script>
<script>
var options = {
    "key": "YOUR_KEY_ID", // Enter the Key ID generated from the Dashboard
    "amount": "50000", // Amount is in currency subunits. Default currency is INR. Hence, 50000 refers to 50000 paise
    "currency": "INR",
    "name": "Acme Corp",
    "description": "Test Transaction",
    "image": "https://example.com/your_logo",
    "order_id": "order_9A33XWu170gUtm", //This is a sample Order ID. Pass the `id` obtained in the response of Step 1
    "handler": function (response){
        alert(response.razorpay_payment_id);
        alert(response.razorpay_order_id);
        alert(response.razorpay_signature)
    },
    "prefill": {
        "name": "Gaurav Kumar",
        "email": "gaurav.kumar@example.com",
        "contact": "9000090000"
    },
    "notes": {
        "optimizer_identifier_1": "rzp",
        "optimizer_identifier_2": "payu",
        "optimizer_identifier_3": "atom"
    },
    "theme": {
        "color": "#3399cc"
    }
};
var rzp1 = new Razorpay(options);
rzp1.on('payment.failed', function (response){
        alert(response.error.code);
        alert(response.error.description);
        alert(response.error.source);
        alert(response.error.step);
        alert(response.error.reason);
        alert(response.error.metadata.order_id);
        alert(response.error.metadata.payment_id);
});
document.getElementById('rzp-button1').onclick = function(e){
    rzp1.open();
    e.preventDefault();
}
</script>
```

## Turbo UPI on Optimizer

Watch this short video of how you to route your transactions for [Turbo UPI](https://razorpay.com/docs/payments/payment-gateway/android-integration/custom/payment-methods/turbo-upi) using Optimizer.

![Turbo UPI on optimizer gif](https://razorpay.com/docs/build/browser/assets/images/upi-turbo-optimizer.gif)

> [!NOTE]
>
> **Handy Tips**
>
> Make sure that you have enabled Turbo UPI as a payment method. If it is not yet enabled, please get in touch with your sales POC to activate this feature for your account.

Below is an example of how you can route your transactions for [Turbo UPI](https://razorpay.com/docs/payments/payment-gateway/android-integration/custom/payment-methods/turbo-upi) using Optimizer:

1. Log in to your Dashboard.
2. Go to the **PAYMENT PRODUCTS** section and click **Optimizer**.

   ![optimizer login](https://razorpay.com/docs/build/browser/assets/images/optimizer-login.jpg)
3. Click **Add New Rule**.

   ![Add new rule](https://razorpay.com/docs/build/browser/assets/images/add-new-rule-upi-turbo.jpg)
4. Enter the **Rule Name** and **Rule Description** and click **Next**.

   ![Add rule name & description](https://razorpay.com/docs/build/browser/assets/images/rule-name-description-upi-turbo.jpg)
5. Enter the following values:
   * **When** - Select `Payment Method`.
   * **is** - Select `Equal to`.
   * **Select Comparing Value** - Select `upi_in_app` and click **Next**.

![Add values](https://razorpay.com/docs/build/browser/assets/images/enter-values-upi-turbo.jpg)

> [!WARNING]
>
> **Watch Out!**
>
> The comparing value `upi_in_app` will be enabled only when you have the payment method Turbo UPI enabled for you.

6. Enter the target payment provider details and click **Next**.

   ![Add target provider](https://razorpay.com/docs/build/browser/assets/images/provider-details-upi-turbo.jpg)

> [!WARNING]
>
> **Watch Out!**
>
> * Razorpay is the only supported payment provider for Turbo UPI on Optimizer.
> * If you do not set any routing rules, then by default, all transactions will be routed via Razorpay.

7. Click **Publish Rule**.

   ![publish rule turbo upi](https://razorpay.com/docs/build/browser/assets/images/publish-rule-upi-turbo.jpg)
8. Click **Publish Now**.

   ![publish now turbo upi](https://razorpay.com/docs/build/browser/assets/images/publish-now-upi-turbo.jpg)

### Related Information

* [Add Payment Providers](https://razorpay.com/docs/payments/optimizer/add-payment-providers.md)
* [Manage Rules](https://razorpay.com/docs/payments/optimizer/manage-rules.md)
