> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Currency Conversion

> Know how currency conversion works in the APIs, Razorpay Dashboard and Settlements.

Available in
🇮🇳 India
🇸🇬 Singapore

Razorpay Settlements occur in SGD based on the conversion rate at the time of payment.

## Checkout Form and APIs

On the checkout form or when using APIs for Razorpay products , you need to specify the desired currency and pass the amount in the currency subunit.

> [accordion] Sample Code
>
> The following is a sample API request and response to create an order for \$20:
>
> ```bash Request theme={null}
> curl -u <YOUR_KEY>:<YOUR_SECRET> \
> -X POST https://api.razorpay.com/v1/orders \
> -H "content-type: application/json"
> -d '{
>   "amount": 2000,
>   "currency": "USD",
>   "receipt": "rcptid #11"
>   }'
> ```
>
> ```java Java theme={null}
> try {
>   JSONObject orderRequest = new JSONObject();
>   orderRequest.put("amount", 2000); // amount in the smallest currency unit
>   orderRequest.put("currency", "USD");
>   orderRequest.put("receipt", "order_rcptid_11");
>
>   Order order = razorpay.Orders.create(orderRequest);
> } catch (RazorpayException e) {
>   // Handle Exception
>   System.out.println(e.getMessage());
> }
> ```
>
> ```python Python theme={null}
> order_amount = 2000
> order_currency = 'USD'
> order_receipt = 'order_rcptid_11'
> notes = {'Shipping address': 'Bommanahalli, Bangalore'}   # OPTIONAL
>
> client.order.create(amount=order_amount, currency=order_currency, receipt=order_receipt, notes=notes)
> ```
>
> ```php PHP theme={null}
> $order  = $client->order->create([
>   'receipt'         => 'order_rcptid_11',
>   'amount'          => 2000, // amount in the smallest currency unit
>   'currency'        => 'USD',//
>   )
> ]);
> ```
>
> ```csharp .NET theme={null}
> Dictionary<string, object> options = new Dictionary<string,object>();
> options.Add("amount", 2000); // amount in the smallest currency unit
> options.add("receipt", "order_rcptid_11");
> options.add("currency", "USD");
> Order order = client.Order.Create(options);
> ```
>
> ```ruby Ruby theme={null}
> options = amount: 2000, currency: 'USD', receipt: '<order_rcptid_11>'
> order = Razorpay::Order.create
> ```
>
> ```javascript Node.js theme={null}
> var options = {
>   amount: 2000,  // amount in the smallest currency unit
>   currency: "USD",
>   receipt: "order_rcptid_11"
> };
> instance.orders.create(options, function(err, order) {
>   console.log(order);
> });
> ```
>
> ```json Response theme={null}
> {
>   "id": "order_00000000000001",
>   "entity": "order",
>   "amount": 2000,
>   "currency": "USD",
>   "receipt": "order_rcptid_11",
>   "status": "created",
>   "attempts": 0,
>   "created_at": 1596208654,
>   "notes": []
> }
> ```
>
> `currency` *mandatory*
> : `string` Currency in which you want to accept the payment. For example, `GBP`. Check the [supported international currencies.](https://razorpay.com/docs/sg/payments/international-payments#supported-products)
>
> `amount` *mandatory*
> : `integer` The amount to be charged in the specified currency subunit.
>
> `receipt` *optional*
> : `string` Your receipt id for this order should be passed here. Maximum length is 40 characters.
>
> For example, when selling a product for ₹1000 in the domestic market, you pass SGD in the `currency` parameter and `100000` in the `amount` parameter (since the amount should be in sub units).
>
> When selling in the international market, you might want to charge \$20 for the same product. In this case, you must pass `USD` in the `currency` parameter and `2000` in the `amount` parameter (since the amount should be in sub units).

> [accordion] Payment Entity
>
> The [Payment entity](https://razorpay.com/docs/sg/api/payments/entity.md) will contain additional fields when the currency is not SGD to provide visibility into the conversion rate.
>
> **Example**
>
> The following is a sample payment entity for a \$1 payment:
>
> ```json Payment Entity theme={null}
> {
>   "id": "pay_Donb2t6WkJYhfU",
>   "entity": "payment",
>   "amount": 100,
>   "currency": "USD",
>   "base_amount": 7129,
>   "base_currency": "SGD",
>   "status": "captured",
>   "order_id": "order_CjCr5oKh4AVC51",
>   "international": true,
>   "method": "card",
>   "amount_refunded": 0,
>   "refund_status": null,
>   "description": "Payment at the Dollar Store",
>   "card_id": "card_Donb2wk8eC8EDN",
>   "email": "<email>",
>   "contact": "<phone>",
>   "notes": [],
>   "fee": 207,
>   "tax": 0,
>   "error_code": null,
>   "error_description": null,
>   "created_at": 1400826750
> }
> ```
>
> `base_currency`
> : `string` The conversion currency that will be used to calculate fees and settlements. This currently defaults to SGD and is present only if the `currency` is not SGD.
>
> `base_amount`
> : `integer` The converted payment amount that will be used to calculate fees and settlements. Represented in the smallest unit of the `base_currency`. This attribute is currently only present if the `currency` is not SGD.

## Select International Currency

When using products such as Payment Links or Subscription Links, ensure you select the desired currency from the currency drop-down list and add the amount in the selected currency. For example, if you want to charge \$20 when selling in the international market, select `USD` in the **Currency** drop-down list and enter 20 in the **Amount** field.

## Settlements

After your customers have made the payment, the payment amount is converted to SGD and settled to your Razorpay Payment Gateway (PG) account as per your settlement schedule. The exchange rate (according to the processing bank) on the date the payment was made is used to make the conversion.

#### Example

A customer made a payment of \$10 on February 02, 2019.

* **Settlement Schedule**: T+7 business days for domestic transactions, where T is the date of capture of payment.
* **Date of payment capture**: February 02, 2019
* **Conversion Rate**:  \$1 = ₹70 as on February 02, 2019
* **Settlement Amount**: For $10 payment, $10 \* ₹70= 700 (minus taxes and fees) is settled to your account on February 09, 2019.
