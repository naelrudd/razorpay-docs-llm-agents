# Integrate Offers with Standard Checkout

After creating [offers](https://razorpay.com/docs/build/llm-docs/payments/offers/create.md) from the Dashboard, you have to integrate them on Razorpay Standard Checkout so that your customers can avail them while making payments.

**WARN**

**Integrate Offers with Orders API**

If you use our JS, SDK files or other Ecommerce plugins, you **should** integrate offers with the Orders API.

## Exception

You need **not** integrate offers with Orders API if you use any of the following Razorpay products or plugins to accept payments:

  - Plugins: Magento, Shopify or WooCommerce.
  - Products: Payment Links, Payment Buttons, Payment Pages and Invoices.

This is because Razorpay automatically creates orders for these products or plugins when customers initiate payment at the Checkout.

**INFO**

**Handy Tips**

As per the RBI guidelines, the original card number is replaced with a surrogate value called a token. However, we will continue to support BIN-based offers post tokenisation. Note that BIN-based offers will not work on saved American Express (AMEX) cards.

## Validation Criteria

Only those offers that pass the following validations are be displayed at the Checkout:

Criteria | Description
---
**Amount Match** | Order amount should be more than or equal to the [Minimum Order Amount](https://razorpay.com/docs/build/llm-docs/payments/offers/create.md#instant) set in an offer.
---
**Validity** | Offer should be in the active or enabled state.
---
**Date Validation** | The current date lies within the range of the offer's `start` and `end` dates.
---
**Usage** | You can define the maximum number of times an offer can be availed. The offer will not be displayed at the Checkout if this limit is met.
---
**Show Offer on Checkout** | This option must be enabled while creating the offer. This determines whether the offer will be displayed at the Checkout.

## Display Offers at Checkout

There are three ways in which you can display offers at Razorpay Checkout:

- [Display Offers by Default](#method-1-display-offers-by-default)
- [Display Limited Offers](#method-2-display-limited-offers)
- [Force Offer](#method-3-force-offer)

### Method 1: Display Offers by Default

This is the easiest way to display offers at the Checkout. While creating the offer from the Dashboard, enable the **Show Offer on Checkout** option.  The offer automatically appears at the Checkout.

### Method 2: Display Limited Offers 

To display a specific set of offers at the Checkout, you should associate the offers with an order. You can pass the `offers` array as a request attribute in the Create Orders API.

Some use cases:
- If you have multiple product lines running on the same account and certain business logic on your side for displaying offers.
- The discount has already been applied, and you would like to restrict the payment method to avail the offer.

**WARN**

**Watch Out!**

To display an Offer for a particular customer:

- **Do not** select the Show Offer on the Checkout check box while creating an Offer.

- Specify the offer_id; for example, `offer_ANZoaxsOww2X53` in the `offers` array while creating an order.

### Method 3: Force Offer

Use this method when a customer has already selected an offer on your website or app before the payment process begins. By forcing an offer, you lock the checkout to that specific offer, ensuring the customer can only pay using the forced offer. If the customer does not accept the forced offer, the payment will not be processed.

**WARN**

**Watch Out!**

You must pass only one offer id in the `offers` array when using `force_offer`. Passing multiple offers with `force_offer` set to `true` is not supported.

## Integrate Offers with Orders API

To integrate offers, follow these steps:
1. [Create an Offer](#step-1-create-an-offer-from-the-dashboard).
2. [Pass the Offer in Orders API](#step-2-pass-the-offer-in-orders-api).
3. [Pass order_id and Trigger Checkout](#step-3-pass-order-id-and-trigger-the).

### Step 1: Create an Offer from the Dashboard

You can [create offers](https://razorpay.com/docs/build/llm-docs/payments/offers/create.md#create-offers) from the [Dashboard](https://razorpay.com/docs/build/llm-docs/payments/offers/create.md).

Let us say you have created an offer `offer_ANZoaxsOww2X53`, such that a discount of  is applicable on all transactions done through AXIS netbanking only.

### Step 2: Pass the Offer in Orders API

Create an order using the [Orders API](https://razorpay.com/docs/build/llm-docs/api/orders.md). Depending on the method, you can pass specific offers in the request or let Razorpay apply the default offers automatically.

**INFO**

**Handy Tips**

To display specific offers at checkout, pass them in the `offers` array (see the sample code below). If you don't include anything in the `offers` array, the default offers will automatically appear at checkout.

  
You do not have to pass any offer id in the request. Razorpay automatically applies the offers created and enabled from the Dashboard.

#### Sample Code

```curl: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/orders \
-H "content-type: application/json" \
-d '{
  "amount": 5000,
  "currency": "INR",
  "receipt": "receipt#1",
  "notes": {
    "key1": "value3",
    "key2": "value2"
  }
}'

```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

JSONObject orderRequest = new JSONObject();
orderRequest.put("amount",5000);
orderRequest.put("currency","INR");
orderRequest.put("receipt", "receipt#1");
JSONObject notes = new JSONObject();
notes.put("notes_key_1","Tea, Earl Grey, Hot");
notes.put("notes_key_1","Tea, Earl Grey, Hot");
orderRequest.put("notes",notes);

Order order = razorpay.orders.create(orderRequest);

```Python: Python
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.order.create({
  "amount": 5000,
  "currency": "INR",
  "receipt": "receipt#1",
  "notes": {
    "key1": "value3",
    "key2": "value2"
  }
})

```php: PHP
$api = new Api($key_id, $secret);

$$api->order->create(array('receipt' => '123', 'amount' => 100, 'currency' => 'INR', 'notes'=> array('key1'=> 'value3','key2'=> 'value2')));

```csharp: .NET
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

Dictionary options = new Dictionary();
options.Add("amount", 5000); // amount in the smallest currency unit
options.Add("receipt", "order_rcptid_11");
options.Add("currency", "INR");
Order order = client.Order.Create(options);

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

para_attr = {
  "amount": 5000,
  "currency": "INR",
  "receipt": "receipt#1",
  "notes": {
    "key1": "value3",
    "key2": "value2"
  }
}

Razorpay::Order.create(para_attr)

```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.orders.create({
  amount: 50000,
  currency: "INR",
  receipt: "receipt#1",
  notes: {
    key1: "value3",
    key2: "value2"
  }
})

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
  "amount": 5000,
  "currency": "INR",
  "receipt": "some_receipt_id",
  "partial_payment": false,
  "notes": map[string]interface{}{
      "key1": "value1",
      "key2": "value2",
    } 
}
body, err := client.Order.Create(data, nil)

```json: Response
{
  "amount": 5000,
  "amount_due": 5000,
  "amount_paid": 0,
  "attempts": 0,
  "created_at": 1756455561,
  "currency": "INR",
  "entity": "order",
  "id": "order_RB58MiP5SPFYyM",
  "notes": {
      "key1": "value3",
      "key2": "value2"
  },
  "offer_id": null,
  "receipt": "receipt#1",
  "status": "created"
}
```

  
### Request Parameters

`amount` _mandatory_
: `integer` Enter the amount for which the order is to be created in currency subunits. For example, for an amount of , enter `5000`.

`currency` _mandatory_
: `string` ISO code of the currency associated with the order amount. Here, it is `INR`.

`receipt` _optional_
: `string` Your receipt id for this order.

`notes` _optional_
: `object` Key-value pair that can be used to store additional information about the order.
    

  
### Response Parameters

For a complete list of response parameters, refer to the [Create an Order API](https://razorpay.com/docs/build/llm-docs/api/orders/create.md)
    

  
  
Pass one or more offer ids in the `offers` array to display only those offers at the Checkout.

#### Sample Code

```curl: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/orders \
-H "Content-Type: application/json" \
-d '{
  "amount": 1000000,
  "currency": "INR",
  "offers": [
    "offer_ANZoaxsOww2X53"
  ]
}'
```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

       ArrayList Offer = new ArrayList();
        Offer.add("offer_JTUADI4ZWBGWur");

        JSONObject orderRequest = new JSONObject();
        orderRequest.put("amount", 1000000); // amount in the smallest currency unit
        orderRequest.put("currency", "INR");
        orderRequest.put("offers", Offer);

        Order order = razorpayclient.orders.create(orderRequest);
        System.out.print(order);
```python: Python
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.order.create({
  "amount": 1000000,
  "currency": "INR",
  "receipt": "receipt#1",
  "offers": [
    "offer_ANZoaxsOww2X53"
  ]
})
```php: PHP
$api = new Api($key_id, $secret);

$api->order->create(array('amount' => 1000000, 'currency' => 'INR', 'offers'=> array('offer_JTUADI4ZWBGWur')));
```ruby: Ruby 
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

order = Razorpay::Order.create amount: 1000000, currency: 'INR', receipt: 'receipt#1',  offers: [
    'offer_ANZoaxsOww2X53"'
]
```js: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.orders.create({
  amount: 1000000,
  currency: "INR",
  receipt: "receipt#1",
  offers: [
    "offer_ANZoaxsOww2X53"
  ]
})
```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

data := map[string]interface{}{
 "amount": 1000000,
 "currency": "INR",
 "receipt": "receipt#1",
  "offers": []interface{}{
  "offer_JTUADI4ZWBGWur",
  },
}
body, err := client.Order.Create(data, nil)

```json: Response
{
  "id": "order_CjyoZFRpB8r0AH",
  "entity": "order",
  "amount": 1000000,
  "amount_paid": 0,
  "amount_due": 1000000,
  "currency": "INR",
  "receipt": null,
  "offer_id": "offer_ANZoaxsOww2X53",
  "offers": [
    "offer_ANZoaxsOww2X53"
  ],
  "status": "created",
  "attempts": 0,
  "notes": [],
  "created_at": 1561018912
}
```

  
### Request Parameters

`amount` _mandatory_
: `integer` Enter the amount for which the order is to be created in currency subunits. For example, for an amount of , enter `1000000`.

`currency` _mandatory_
: `string` ISO code of the currency associated with the order amount. Here, it is `INR`.

`offers` _mandatory_
: `array` Unique identifier of the offer. Pass the offer_id obtained from the response of the previous step.
    

  
### Response Parameters

For a complete list of response parameters, refer to the [Create an Order API](https://razorpay.com/docs/build/llm-docs/api/orders/create.md) 
    

  
  
Pass a single offer id in the `offers` array and set `force_offer` to `true` to lock the checkout to that offer.

#### Sample Code

```curl: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/orders \
-H "Content-Type: application/json" \
-d '{
  "amount": 5000000,
  "currency": "INR",
  "offers": [
    "offer_ANZoaxsOww2X53"
  ],
  "force_offer": "true"
}'
```json: Response
{
  "id": "order_SdHL46SFWnEPR7",
  "entity": "order",
  "amount": 5000000,
  "amount_paid": 0,
  "amount_due": 5000000,
  "currency": "INR",
  "receipt": null,
  "offer_id": "offer_ANZoaxsOww2X53",
  "offers": [
    "offer_ANZoaxsOww2X53"
  ],
  "status": "created",
  "attempts": 0,
  "notes": [],
  "created_at": 1776149151
}
```

  
### Request Parameters

`amount` _mandatory_
: `integer` Enter the amount for which the order is to be created in currency subunits. For example, for an amount of , enter `5000000`.

`currency` _mandatory_
: `string` ISO code of the currency associated with the order amount. Here, it is `INR`.

`offers` _mandatory_
: `array` Pass a single offer_id in the array. This is the offer that will be forced on the checkout.

`force_offer` _mandatory_
: `string` Set this to `true` to force the specified offer on the checkout. The customer will only be able to pay using this offer.
    

  
### Response Parameters

For a complete list of response parameters, refer to the [Create an Order API](https://razorpay.com/docs/build/llm-docs/api/orders/create.md) 
    

  

### Step 3: Pass Order_id and Trigger the Checkout

The `order_id` obtained in the previous step can be passed to the Checkout form as follows:

```js: Checkout
Pay

var options = {
    "key": "[YOUR_KEY_ID]",
    "amount": "1000000",
    "currency": "INR",
    "order_id":"order_FIL1vBOsWFllnO",
    "name": "Acme Corp",
    "description": "Test Transaction",
    "image": "https://cdn.razorpay.com/logos/F9Yhfb7ZXjXmIQ_medium.jpg",
    "handler": function (response){
        alert(response.razorpay_payment_id);
        alert(response.razorpay_order_id);
        alert(response.razorpay_signature)
    },
    "prefill": {
        "name": "Gaurav Kumar",
        "email": "gaurav.kumar@example.com",
        "contact": "+919876543210"
    },
    "notes": {
        "address": "Razorpay Corporate Office"
    },
    "theme": {
        "color": "#3399cc"
    }
};
var rzp1 = new Razorpay(options);
document.getElementById('rzp-button1').onclick = function(e){
    rzp1.open();
    e.preventDefault();
}

```

Know more about [Standard Checkout](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/web-integration/standard.md).

## Next Steps

After the customer has availed the offers and made the payment at the Checkout, you can  track the status of the payments:

- From the Dashboard.
- By [configuring webhooks](https://razorpay.com/docs/build/llm-docs/webhooks/setup-edit-payments.md).
- By polling our [payment APIs](https://razorpay.com/docs/build/llm-docs/api/payments/fetch-with-id.md).

### Related Information

- [About Offers](https://razorpay.com/docs/build/llm-docs/payments/offers.md)
- [Create Offers](https://razorpay.com/docs/build/llm-docs/payments/offers/create.md)
- [Tutorial - How to Create Offers](https://razorpay.com/docs/build/llm-docs/payments/offers/tutorial.md)
- [Disable Offers](https://razorpay.com/docs/build/llm-docs/payments/offers/create.md#disabling-offers)
- [Offers FAQs](https://razorpay.com/docs/build/llm-docs/payments/offers/faqs.md)
