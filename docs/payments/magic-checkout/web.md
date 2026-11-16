> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integrate Magic Checkout on Website

> Steps to integrate Magic Checkout on your Website.

Available in
🇮🇳 India

Follow these steps to integrate the Razorpay Magic Checkout on your website.

#### Prerequisites

* [Create a Razorpay account](https://dashboard.razorpay.com/).
* Generate [API Keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys) from the Dashboard. To go live with the integration and start accepting real payments, generate Live Mode API Keys and replace them in the integration.

## Integration Steps

Follow the steps given below:

> [accordion] 1 Enable/Disable Magic Checkout and Cash on Delivery
>
> > [tab] Enable Magic Checkout
> >
> > Raise a request with your Razorpay SPOC to get this feature enabled on your account.
> > Once this feature is enabled, the customer address saving and coupon features are enabled.
>
> > [tab] Enable Cash on Delivery Payment Method
> >
> > Raise a request with our [Support team](https://razorpay.com/support/) to enable this feature for your account.

> [accordion] 2 Create Promotions and Shipping Info API Endpoints
>
> Follow the steps given below to create promotions and shipping info API endpoints:
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Ensure that the URLs are publicly accessible, require no authentication and are hosted on your server.
>
> 1. Log in to the Dashboard and navigate to **Magic Checkout**.
> 2. In the **Platform Setup**, select **Custom E-Commerce Platform** from the drop-down list and click **Next**.
>
>    ![Choose custom platform](https://razorpay.com/docs/build/browser/assets/images/magic-custom-platform.jpg)
> 3. In the **Setup & Settings** section, click **Checkout Settings**.
> 4. In the **Coupon Settings** section, enter the following:
>    1. **URL for get promotions**: The API URL should return a list of promotions applicable to the specified order\_id and customer. Magic Checkout uses this endpoint to fetch these promotions from your server and display them to your customers in the checkout modal.
>    2. **URL for apply promotions**: The API URL validates the promotion code applied by the customer and should return the discount amount. Magic Checkout uses this endpoint to apply promotions via your server.
> 5. Click **Save settings**.
>
>    ![Add promotion URLs](https://razorpay.com/docs/build/browser/assets/images/magic-web-promo-url.jpg)
> 6. Navigate to **Shipping Setup**.
> 7. Select **API** as the Shipping Service type from the drop-down list.
> 8. Enter the **URL for shipping info**. The API URL should return shipping serviceability, COD serviceability, shipping fees and COD fees for a given list of customer addresses. Magic Checkout uses this endpoint to retrieve shipping information from your server.
> 9. Click **Save Settings**.
>
>    ![Add shipping URL](https://razorpay.com/docs/build/browser/assets/images/magic-web-shipping-url.jpg)

> [accordion] 3 Create an Order
>
> You can create an order using the following API and send the additional information required for Magic Checkout. Pass the `order_id` received in response to the checkout code.
>
> ```bash Curl theme={null}
> curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
> -X POST https://api.razorpay.com/v1/orders \
> -H "content-type: application/json" \
> -d '{
>   "amount": 50000,
>   "currency": "INR",
>   "receipt": "receipt#1",
>   "line_items_total": 50000,  // Mandatory for Magic Checkout
>   "line_items": [
>     {
>       "sku": "1g234",
>       "variant_id": "12r34",
>       "price": 50000,
>       "offer_price": 50000,
>       "quantity": 1,
>       "name": "Product Name"
>       // ... other line item details
>     }
>   ]
> }'
> ```
>
> ```java Java theme={null}
> RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> JSONObject orderRequest = new JSONObject();
> orderRequest.put("amount", 50000);
> orderRequest.put("currency", "INR");
> orderRequest.put("receipt", "receipt#1");
> orderRequest.put("line_items_total", 50000); // Mandatory for Magic Checkout
>
> JSONArray lineItems = new JSONArray();
> JSONObject item = new JSONObject();
> item.put("sku", "1g234");
> item.put("variant_id", "12r34");
> item.put("price", 50000);
> item.put("offer_price", 50000);
> item.put("quantity", 1);
> item.put("name", "Product Name");
> // ... other line item details
> lineItems.put(item);
> orderRequest.put("line_items", lineItems);
>
> Order order = razorpay.orders.create(orderRequest);
> ```
>
> ```python Python theme={null}
> import razorpay
> client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
> data = {
>   "amount": 50000,
>   "currency": "INR",
>   "receipt": "receipt#1",
>   "line_items_total": 50000,  # Mandatory for Magic Checkout
>   "line_items": [
>     {
>       "sku": "1g234",
>       "variant_id": "12r34",
>       "price": 50000,
>       "offer_price": 50000,
>       "quantity": 1,
>       "name": "Product Name"
>       # ... other line item details
>     }
>   ]
> }
>
> client.order.create(data)
> ```
>
> ```go Go theme={null}
> import (
>   razorpay "github.com/razorpay/razorpay-go"
> )
>
> client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
>
> para_attr := map[string]interface{}{
>   "amount": 50000,
>   "currency": "INR",
>   "receipt": "receipt#1",
>   "line_items_total": 50000, // Mandatory for Magic Checkout
>   "line_items": []interface{}{
>     map[string]interface{}{
>       "sku": "1g234",
>       "variant_id": "12r34",
>       "price": 50000,
>       "offer_price": 50000,
>       "quantity": 1,
>       "name": "Product Name",
>       // ... other line item details
>     },
>   },
> }
>
> body, err := client.Order.Create(para_attr, nil)
> ```
>
> ```php PHP theme={null}
> $api = new Api($key_id, $secret);
>
> $api->order->create(array(
>   'amount' => 50000,
>   'currency' => 'INR',
>   'receipt' => 'receipt#1',
>   'line_items_total' => 50000, // Mandatory for Magic Checkout
>   'line_items' => array(
>     0 => array(
>       'sku' => '1g234',
>       'variant_id' => '12r34',
>       'price' => 50000,
>       'offer_price' => 50000,
>       'quantity' => 1,
>       'name' => 'Product Name',
>       // ... other line item details
>     ),
>   ),
> ));
> ```
>
> ```ruby Ruby theme={null}
> require "razorpay"
> Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
>
> para_attr = {
>   "amount": 50000,
>   "currency": "INR",
>   "receipt": "receipt#1",
>   "line_items_total": 50000, # Mandatory for Magic Checkout
>   "line_items": [
>     {
>       "sku": "1g234",
>       "variant_id": "12r34",
>       "price": 50000,
>       "offer_price": 50000,
>       "quantity": 1,
>       "name": "Product Name"
>       # ... other line item details
>     }
>   ]
> }
>
> Razorpay::Order.create(para_attr)
> ```
>
> ```javascript Node.js theme={null}
> var instance = new Razorpay({
>   key_id: 'YOUR_KEY_ID',
>   key_secret: 'YOUR_SECRET'
> })
>
> var data = {
>   "amount": 50000,
>   "currency": "INR",
>   "receipt": "receipt#1",
>   "line_items_total": 50000, // Mandatory for Magic Checkout
>   "line_items": [
>     {
>       "sku": "1g234",
>       "variant_id": "12r34",
>       "price": 50000,
>       "offer_price": 50000,
>       "quantity": 1,
>       "name": "Product Name"
>       // ... other line item details
>     }
>   ]
> }
>
> instance.orders.create(data);
> ```
>
> ```csharp .Net theme={null}
> RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
>
> Dictionary<string, object> orderRequest = new Dictionary<string, object>();
> orderRequest.Add("amount", 50000);
> orderRequest.Add("currency", "INR");
> orderRequest.Add("receipt", "receipt#1");
> orderRequest.Add("line_items_total", 50000); // Mandatory for Magic Checkout
>
> List<object> lineItem = new List<object>();
> Dictionary<string, object> lineItems = new Dictionary<string, object>();
> lineItems.Add("sku", "1g234");
> lineItems.Add("variant_id", "12r34");
> lineItems.Add("price", 50000);
> lineItems.Add("offer_price", 50000);
> lineItems.Add("quantity", 1);
> lineItems.Add("name", "Product Name");
> // ... other line item details
> lineItem.Add(lineItems);
> orderRequest.Add("line_items", lineItem);
>
> Order order = client.Order.Create(orderRequest);
> ```
>
> ```json Response theme={null}
> {
>   "id": "order_EKwxwAgItmmXdp",
>   "entity": "order",
>   "amount": 50000,
>   "amount_paid": 0,
>   "amount_due": 50000,
>   "currency": "INR",
>   "receipt": "receipt#1",
>   "offer_id": null,
>   "status": "created",
>   "attempts": 0,
>   "notes": [],
>   "created_at": 1582628071,
>   "line_items_total": 50000
> }
> ```
>
> > [accordion] Request Parameters
> >
> > `amount` *mandatory*
> > : `integer` The transaction amount, expressed in the currency subunit, such as paise (in case of INR). For example, for an actual amount of ₹299.35, the value of this field should be `29935`.
> >
> > `currency` *mandatory*
> > : `string` The currency in which the transaction should be made. See the [list of supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies). Default is `INR`. Length must be of 3 characters.
> >
> > `receipt` *mandatory*
> > : `string` Your receipt id for this order should be passed here. Maximum length of 40 characters.
> >
> > `notes` *optional*
> > : `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty"`.
> >
> > `line_items_total` *mandatory*
> > : `integer` Total of `offer_price` for all line items added to the cart, in paise. For example, if a shoe worth ₹8,000 and a shirt worth ₹10,000 are added, the `line_item_total` will be `1800000`. This amount is post-tax.
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > To ensure the order is considered as a Magic Checkout order, you must pass this parameter. Otherwise, it will default to Standard Checkout order and customers will view the Standard Checkout UI instead of Magic Checkout. Know more about [Razorpay Standard Checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard.md).
> >
> > `line_items` *mandatory*
> > : `array` This will have the details about the specific items added to the cart.
> >
> > `sku` *mandatory*
> > : `string` Unique product id defined by you. It can be alphanumeric.
> >
> > `variant_id` *mandatory*
> > : `string` Unique variant id defined by you. It can be alphanumeric.
> >
> > `price` *mandatory*
> > : `integer` Price of the product in paise.
> >
> > `offer_price` *mandatory*
> > : `integer` Final price charged to the customer in paise, after applying any adjustments, such as product discounts.
> >
> > > [!NOTE]
> > >
> > > **Handy Tips**
> > >
> > > If no discount is applied, `price` and `offer_price` will be the same.
> >
> > `quantity` *mandatory*
> > : `integer` Number of units added in the cart.
> >
> > `name` *mandatory*
> > : `string` Name of the product.
> >
> > `description` *mandatory*
> > : `string` Description of the product.
> >
> > `weight` *optional*
> > : `integer` Weight of the product in grams.
> >
> > `dimensions` *optional*
> > : `object` The dimensions of the product.
> >
> > `length` *optional*
> > : `string` The length of the product in centimeters.
> >
> > `width` *optional*
> > : `string` The width of the product in centimeters.
> >
> > `height` *optional*
> > : `string` The height of the product in centimeters.
> >
> > `image_url` *mandatory*
> > : `string` The URL of the product image. This parameter is mandatory if you want to display product images on our iframe.
> >
> > `product_url` *optional*
> > : `string` URL of the product's listing page.
> >
> > `notes` *optional*
> > : `object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty"`.
>
> > [accordion] Response Parameters
> >
> > `id`
> > : `string` The unique identifier of the order.
> >
> > `amount`
> > : `integer` Payment amount in the smallest currency sub-unit. For example, if the amount to be charged is ₹299, then pass `29900` in this field.
> >
> > `partial_payment`
> > : `boolean` Indicates whether the customer can make a partial payment. Possible values:
> >
> > * `true`: The customer can make partial payments.
> > * `false` (default): The customer cannot make partial payments.
> >
> > `amount_paid`
> > : `integer` The amount paid against the order.
> >
> > `amount_due`
> > : `integer` The amount pending against the order.
> >
> > `currency`
> > : `string` ISO code for the currency in which you want to accept the payment. The default length is 3 characters.
> >
> > `receipt`
> > : `string` Receipt number that corresponds to this order. Can have a maximum length of 40 characters and has to be unique.
> >
> > `status`
> > : `string` The status of the order. Possible values:
> >
> > * `created`: When you create an order it is in the `created` state. It stays in this state till a payment is attempted on it.
> > * `attempted`: An order moves from `created` to `attempted` state when a payment is first attempted on it. It remains in the `attempted` state till one payment associated with that order is captured.
> > * `paid`: After the successful capture of the payment, the order moves to the `paid` state. No further payment requests are permitted once the order moves to the `paid` state. The order stays in the `paid` state even if the payment associated with the order is refunded.
> >
> > `attempts`
> > : `integer` The number of payment attempts, successful and failed, that have been made against this order.
> >
> > `notes`
> > : `json object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty"`.
> >
> > `created_at`
> > : `integer` Indicates the Unix timestamp when this order was created.
> >
> > `line_items_total`
> > : `integer` Total of `offer_price` for all line items added to the cart, in paise.
>
> > [accordion] Error Response Parameters
> >
> > The error response parameters are available in the [API Reference Guide](https://razorpay.com/docs/api/orders/create.md).
>
> > [accordion] Pre-discount Handling
> >
> > Line items total should equal the sum of individual item prices after your discounts are applied. When applying discounts, reduce both `amount` and `line_items_total` by the same amount:
> >
> > ```json Example theme={null}
> > {
> >   "amount": 45000,           // ₹500 - ₹50 discount = ₹450
> >   "line_items_total": 45000, // Must match the discounted amount
> >   "currency": "INR",
> >   "receipt": "receipt#1",
> >   "notes": {
> >     "prediscount_applied": "5000"  // Track discount in paise
> >   },
> >   "line_items": [
> >     // ... your line items with original prices
> >   ]
> > }
> > ```
> >
> > > [!NOTE]
> > >
> > > **Handy Tips**
> > >
> > > Magic Checkout automatically handles all discount calculations on the UI. The system detects differences in checkout amounts and adjusts accordingly.

> [accordion] 4 Interact with Shipping Info API
>
> This API should return shipping serviceability, COD serviceability, shipping fees and COD fees for a given list of customer addresses.
>
> `GET /your-server-url/shipping-info-api-path`
>
> ```bash Request theme={null}
> {
>  "order_id": "SomeReceiptValue", // This is the receipt field set in the Razorpay order
>  "razorpay_order_id": "EKwxwAgItmXXXX", // This is the RZP order created without the `order_` prefix
>  "email": "<email>", // Email field will be set if the customer enters an email
>  "contact": "+919000090000", // Customer phone number with country code
>  "addresses": [{
>    "id": "0", 
>    "zipcode": "560060",
>    "state_code": "KA",
>    "country": "IN"
>  }]
> }
> ```
>
> ```json Response theme={null}
> {
>   "addresses": [
>     {
>       "id": "0",
>       "zipcode": "560000",
>       "state_code": "KA",
>       "country": "IN",
>       "shipping_methods": [
>         {
>           "id": "1",
>           "description": "Free shipping",
>           "name": "Delivery within 5 days",
>           "serviceable": true,
>           "shipping_fee": 1000, // in paise. Here 1000 = 1000 paise, which equals to ₹10
>           "cod": true,
>           "cod_fee": 1000 // in paise. Here 1000 = 1000 paise, which equals to ₹10
>         },
>         {
>           "id": "2",
>           "description": "Standard Delivery",
>           "name": "Delivered on the same day",
>           "serviceable": true,
>           "shipping_fee": 1000, // in paise. Here 1000 = 1000 paise, which equals to ₹10
>           "cod": false,
>           "cod_fee": 0 // in paise. Here 1000 = 1000 paise, which equals to ₹10
>         }
>       ]
>     }
>   ]
> }
> ```
>
> > [accordion] Request Parameters
> >
> > `order_id` *mandatory*
> > : `string` Unique identifier of the order created [previously](#3-create-an-order).
> >
> > `razorpay_order_id` *mandatory*
> > : `string` Unique identifier for the order returned by Checkout.
> >
> > `email` *optional*
> > : `string` Customer's email address.
> >
> > `contact` *mandatory*
> > : `string` Customer's phone number.
> >
> > `addresses` *mandatory*
> > : `array` Customer's address details.
> >
> > `id` *mandatory*
> > : `string` Unique identifier of the customer's address.
> >
> > `zipcode` *mandatory*
> > : `string` Customer's zipcode.
> >
> > `state_code` *optional*
> > : `string` The code of the state where the customer resides.
> >
> > `country` *mandatory*
> > : `string` Country where the customer resides. The length cannot exceed 2 characters.
>
> > [accordion] Response Parameters
> >
> > `addresses` *mandatory*
> > : `array` Customer's address details.
> >
> > `id` *mandatory*
> > : `string` Unique identifier of the customer's address.
> >
> > `zipcode` *mandatory*
> > : `string` Customer's zipcode.
> >
> > `country` *mandatory*
> > : `string` Country where the customer resides. The length cannot exceed 2 characters.
> >
> > `shipping_methods` *mandatory*
> > : `array` Details regarding the shipping methods.
> >
> > `id` *mandatory*
> > : `string` Unique identifier of the shipping method.
> >
> > `description`
> > : `integer` Brief description of the shipping method.
> >
> > `name` *mandatory*
> > : `string` Name of the shipping method.
> >
> > `serviceable` *mandatory*
> > : `boolean` Indicates whether you deliver orders to the  zipcode entered by the customer. This is based on the zipcodes you have added in the serviceability setting on the Razorpay Dashboard. Possible values:
> >
> > * `true`: Orders can be delivered to the added zipcodes.
> > * `false`: Orders cannot be delivered to the added zipcodes.
> >
> > `shipping_fee` *mandatory*
> > : `integer` Shipping charge in paise applicable to be paid by the customer.
> >
> > `cod` *mandatory*
> > : `boolean` Indicates whether you support cash on delivery on this order.
> >
> > * `true`: COD payment method is supported.
> > * `false`: COD payment method is not supported.
> >
> > `cod_fee` *mandatory* : `integer` Cash on Delivery fee charged in paise. This amount is based on the COD settings configured in your Razorpay Dashboard.
> >
> > > [!NOTE]
> > >
> > > **Handy Tips**
> > >
> > > If the `cod` field is false, set the `cod_fee` field to 0.

> [accordion] 5 Interact with Get Promotions API
>
> This API should return the list of promotions applicable for the given `order_id` and customer.
>
> `GET /your-server-url/create-promotions-api-path`
>
> ```bash Request theme={null}
> {
>   "order_id": "SomeReceiptValue", // this is the receipt field set in Razorpay order
>   "contact": "+919000090000", 
>   "email": "<email>"
> }
> ```
>
> ```json Response theme={null}
> {
>    "promotions": [
>      {
>        "code": "10%OFF",
>        "summary": "10% off on total cart value",
>        "description": "10% on total cart value upto ₹300"
>      },
>      {
>        "code": "500OFF",
>        "summary": "₹500 off on total cart value",
>        "description": "₹500 off on a minimum cart value of ₹1500"
>      }
>    ]
>  }
> ```
>
> > [accordion] Request Parameters
> >
> > `order_id` *mandatory*
> > : `string` Unique identifier of the order created [previously](#3-create-an-order).
> >
> > `contact` *optional*
> > : `string` Customer's phone number.
> >
> > `email` *optional*
> > : `string` Customer's email address.
>
> > [accordion] Response Parameters
> >
> > `promotions` *mandatory*
> > : `array` Details of the promotions created.
> >
> > `code` *mandatory*
> > : `string` Unique identifier of the promotion.
> >
> > `summary` *mandatory*
> > : `string` Summary about the promotion. For example, 10% off on total cart value.
> >
> > `description` *optional*
> > : `string` Brief description of the promotion. For example, 10% on total cart value upto ₹300.
>
> > [accordion] 5.1 Interact with Apply Promotions API
> >
> > This API should validate the promotion code applied by the customer and return the discount amount.
> >
> > `GET /your-server-url/create-promotions-api-path`
> >
> > ```bash Request theme={null}
> > {
> >   "order_id": "SomeReceiptValue", // this is the receipt field set in Razorpay order
> >   "contact": "+919000090000",
> >   "email": "<email>",
> >   "code": "500OFF"
> > }
> > ```
> >
> > ```json Success Response theme={null}
> > {
> >   "promotion": {
> >   "reference_id": "3rvff", 
> >   "type": "offer",
> >   "code": "500OFF", 
> >   "value": 50000, 
> >   "value_type": "fixed_amount", 
> >   "description": "New Year Sale Offer"
> >   } 
> > }
> > ```
> >
> > ```json Failure Response theme={null}
> > {
> >  "failure_code": "LOGIN_REQUIRED",
> >  "failure_reason": “promotion Code has expired" 
> > }
> > ```
> >
> > > [accordion] Request Parameters
> > >
> > > `order_id` *mandatory*
> > > : `string` Unique identifier of the order created [previously](#3-create-an-order).
> > >
> > > `contact` *optional*
> > > : `string` Customer's phone number.
> > >
> > > `email` *optional*
> > > : `string` Customer's email address.
> > >
> > > `code` *mandatory*
> > > : `string` Promotion code used to avail discount on checkout.
> >
> > > [accordion] Response Parameters
> > >
> > > `promotion` *mandatory*
> > > : `object` Used to pass all offer or discount-related information, including promotion code discount, method discount and so on.
> > >
> > > `reference_id` *mandatory*
> > > : `string` Identifier of the offer you create.
> > >
> > > `code` *optional*
> > > : `string` Promotion code used to avail discount on checkout.
> > >
> > > `type` *optional*
> > > : `string` Type of offer. Possible values:
> > >
> > > * `coupon`: A discount applied by customers during checkout. For example, customers can use a coupon like `Diwali Sale 500 Off` to get ₹500 off the total cart value.
> > > * `offer`: A promotion you create for your customers. For example, you create an offer `Buy 4 t-shirts and get 2 free`. In this case, when customers add 4 t-shirts to their cart, the 2 additional t-shirts will be automatically added for free.
> > >
> > > `value` *optional*
> > > : `integer` The offer value that needs to be applied in paise. For example, if you want to offer a discount of ₹500, enter 50000.
> > >
> > > `value_type` *optional*
> > > : `string` The type of value like:
> > >
> > > * `fixed_amount`: A fixed amount discount value in the currency of the order. For example, ₹500.
> > >
> > > * `percentage`: A percentage discount value. For example, 10%.
> > >
> > > * `BXGY`: Buy X and Get Y. For example, if you buy 2 t-shirts, you a get a cap for free or at a discounted value.
> > >
> > > > [!NOTE]
> > > >
> > > > **Handy Tips**
> > > >
> > > > Regardless of the `value_type`, the amount specified in the `value` parameter is applied as-is. For example, if `value_type` is percentage and the `value` is 5000, 5000 is considered in currency subunits (paise).
> > >
> > > `description` *optional*
> > > : `string` Description of the promotion applied. For example, `New Year Sale Offer`.
> >
> > > [accordion] Error Code, Description and Next Steps
> > >
> > > | Code | Description | Next Steps |
> > > | - | - | - |
> > > | INVALID\_PROMOTION | The specified promotion code is not recognised or does not exist in the system. | Please verify the code and try again. |
> > > | LOGIN\_REQUIRED | This coupon is specifically assigned to a registered customer. | To redeem it, the customer must log in to their account and authenticate their identity. |
> > > | REQUIREMENT\_NOT\_MET | The current cart conditions do not meet the requirements for this promotion to be valid. For example, the promotion may require a minimum cart value of ₹1,000, but the cart total is ₹800. | Review the promotion's terms and adjust the cart contents accordingly. |

> [accordion] 6 Integrate with Magic Checkout on Client-Side
>
> Add the Pay button on your web page using the handler function or callback URL.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > If your website is running on WooCommerce or Shopify, please integrate with the Razorpay [WooCommerce](https://razorpay.com/docs/payments/magic-checkout/woocommerce.md) or [Shopify](https://razorpay.com/docs/payments/magic-checkout/shopify.md) plugin based on your requirement.
>
> > [accordion] Advanced Checkout Features
> >
> > Before implementing the basic integration, understand these advanced features available in Magic Checkout:
> >
> > > [accordion] Pre-discount Implementation
> > >
> > > Display custom discounts (coupons, gift cards, loyalty points) in the checkout order summary before customers enter the checkout flow:
> > >
> > > For example, customer adds items to cart:
> > >
> > > * T-shirt: ₹499
> > > * Applies gift card (discount): ₹49
> > > * Final amount: ₹450
> > >
> > > You can follow the steps given below:
> > >
> > > 1. Create an order with amount 45000 (₹450 in paise).
> > > 2. Add pre-discount in checkout with the following
> > >    * `label`: Gift Card (5AA3Y-E9TZE-82EGJ)
> > >    * `value`: ₹49.
> > > 3. Customer views the discount applied in the checkout and pays ₹450.
> > >
> > > ![View pre-discount on checkout](https://razorpay.com/docs/build/browser/assets/images/magic-web-pre-discount-checkout.jpg)
> > >
> > > ```javascript theme={null}
> > > "prefill": {
> > >   "prediscount": [
> > >     {
> > >       "label": "Gift Card (5AA3Y-E9TZE-82EGJ)", 
> > >       "value": "₹49",
> > >       "gift_card_applied": true  // Required for gift cards
> > >     }
> > >   ]
> > > }
> > > ```
> > >
> > > > [!WARNING]
> > > >
> > > > **Watch Out!**
> > > >
> > > > Pre-discounts are for display only and do not affect the payment amount.
> > > >
> > > > * No calculations are required. Magic Checkout handles everything automatically.
> > > > * Payment amount is determined by your Razorpay order, not these display values.
> > > > * Pre-discounts show existing discounts only and do not apply new ones.
> > >
> > > #### Discount Types
> > >
> > > > [tab] Regular Discounts
> > > >
> > > > Use for coupons, promotional codes, loyalty points:
> > > >
> > > > ```javascript theme={null}
> > > > {
> > > >   "label": "WELCOME20",
> > > >   "value": "₹ 200"
> > > > }
> > > > ```
> > >
> > > > [tab] Gift Cards
> > > >
> > > > You must include `gift_card_applied: true` for proper tracking and UI display:
> > > >
> > > > ```javascript theme={null}
> > > > {
> > > >   "label": "Gift Card (5AA3Y-E9TZE-82EGJ)",
> > > >   "value": "₹ 49",
> > > >   "gift_card_applied": true  // Critical for gift cards
> > > > }
> > > > ```
> >
> > > [accordion] Promotional Tags
> > >
> > > Add promotional badges to specific products:
> > >
> > > ```javascript theme={null}
> > > "prefill": {
> > >   "promotional_tag": [
> > >     {
> > >       "tag": "free gift item",
> > >       "variant_id": "1234"
> > >     }
> > >   ]
> > > }
> > > ```
> > >
> > > Below is an example of a promotional tag:
> > >
> > > ![Checkout promotion tag](https://razorpay.com/docs/build/browser/assets/images/magic-web-promotion-tag1.jpg)
>
> > [accordion] 6.1 Handler Function and Callback URL
> >
> > | **Callback URL** | **Handler Function** |
> > | - | - |
> > | When you use this: <ul><li>On successful payment, the customer is redirected to the specified URL, for example, a payment success page.</li><li>On failure, the customer is asked to retry the payment.</li></ul> | When you use this: <ul><li>On successful payment, the customer is shown your web page.</li><li>On failure, the customer is notified of the failure and asked to retry the payment.</li></ul> |
>
> > [accordion] 6.2 Code to Add Pay Button
> >
> > Copy-paste the parameters as `options` in your code:
> >
> > ```html Callback URL (JS) Checkout Code theme={null}
> > <button id="rzp-button1">Pay</button>
> > <script src="https://checkout.razorpay.com/v1/magic-checkout.js"></script>
> > <script>
> > var options = {
> >     "key": "YOUR_KEY_ID", // Enter the Key ID generated from the Dashboard
> >     "one_click_checkout": true,
> >     "name": "Acme Corp", // your business name
> >     "order_id": "order_EKwxwAgItmXXXX", // This is a sample Order ID. Pass the `id` obtained in the response of Step 1; mandatory
> >     "show_coupons": true, // default true; false if coupon widget should be hidden
> >     "callback_url": "https://eneqd3r9zrjok.x.pipedream.net/",
> >     "redirect": "true",
> >     "prefill": { // We recommend using the prefill parameter to auto-fill customer's contact information especially their phone number
> >         "name": "<name>", // your customer's name
> >         "email": "<email>",
> >         "contact": "9000090000", // Provide the customer's phone number for better conversion rates
> >         "coupon_code": "500OFF" // any valid coupon code that gets auto-applied once magic opens
> >     },
> >     "notes": {
> >         "address": "ABC Office"
> >     }
> > };
> > var rzp1 = new Razorpay(options);
> > document.getElementById('rzp-button1').onclick = function(e){
> >     rzp1.open();
> >     e.preventDefault();
> > }
> > </script>
> > ```
> >
> > ```html Handler Functions (JS) Checkout Code theme={null}
> > <button id="rzp-button1">Pay</button>
> > <script src="https://checkout.razorpay.com/v1/magic-checkout.js"></script>
> > <script>
> > var options = {
> >     "key": "YOUR_KEY_ID", // Enter the Key ID generated from the Dashboard
> >     "one_click_checkout": true,
> >     "name": "Acme Corp", // your business name
> >     "order_id": "order_EKwxwAgItmXXXX", // This is a sample Order ID. Pass the `id` obtained in the response of Step 1
> >     "show_coupons": true, // default true; false if coupon widget should be hidden
> >     "handler": function (response){
> >         alert(response.razorpay_payment_id);
> >         alert(response.razorpay_order_id);
> >         alert(response.razorpay_signature)
> >     },
> >     "prefill": { // We recommend using the prefill parameter to auto-fill customer's contact information, especially their phone number
> >         "name": "<name>", // your customer's name
> >         "email": "<email>", 
> >         "contact": "9000090000"  // Provide the customer's phone number for better conversion rates 
> >     },
> >     "notes": {
> >         "address": "ABC Office"
> >     }
> > };
> > var rzp1 = new Razorpay(options);
> > rzp1.on('payment.failed', function (response){
> >         alert(response.error.code);
> >         alert(response.error.description);
> >         alert(response.error.source);
> >         alert(response.error.step);
> >         alert(response.error.reason);
> >         alert(response.error.metadata.order_id);
> >         alert(response.error.metadata.payment_id);
> > });
> > document.getElementById('rzp-button1').onclick = function(e){
> >     rzp1.open();
> >     e.preventDefault();
> > }
> > </script>
> > ```
>
> > [accordion] Checkout Options
> >
> > `key` *mandatory*
> > : `string` API Key id generated from the Razorpay Dashboard.
> >
> > `one_click_checkout` *mandatory*
> > : `boolean` Specifies whether to initiate Magic Checkout or Standard Checkout. Possible values:
> >
> > * `true`: Initiates Magic Checkout.
> > * `false` (default): Initiates Standard Checkout.
> >
> > `name` *mandatory*
> > : `string` Your Business/Enterprise name shown on the Checkout form. For example, **Acme Corp**.
> >
> > `order_id` *mandatory*
> > : `string` Order id generated via [Orders API](https://razorpay.com/docs/api/orders.md).
> >
> > `show_coupons` *optional*
> > : `boolean` Determines whether to show the coupons to customer on the checkout. Possible values:
> >
> > * `true` (default): Enables the Coupon feature.
> > * `false`: Disables the Coupon feature.
> >
> > `prefill` *optional*
> > : `object` You can prefill the following details at Checkout.
> >
> > > [!NOTE]
> > >
> > > **Boost Conversions and Minimise Drop-offs**
> > >
> > > * Autofill customer contact details, especially phone number to ease form completion. Include customer's phone number in the `contact` parameter of the JSON request's `prefill` object. (Format: +(country code)(phone number). Example: "contact": "+919000090000").
> > > * This is not applicable if you do not collect customer contact details on your website before checkout, have Shopify stores or use any of the no-code apps.
> >
> > `name` *optional*
> > : `string` Cardholder's name to be pre-filled if customer is to make card payments on Checkout. For example, **Gaurav Kumar**.
> >
> > `email` *optional*
> > : `string` Email address of the customer.
> >
> > `contact` *optional*
> > : `string` Phone number of the customer. The expected format of the phone number is `+ {country code}{phone number}`. If the country code is not specified, `91` will be used as the default value. This is particularly important while prefilling `contact` of customers with phone numbers issued outside India. **Examples**:
> >
> > * +14155552671 (a valid non-Indian number)
> > * +919977665544 (a valid Indian number). \
> >   If 9977665544 is entered, `+91` is added to it as +919977665544.
> >
> > `coupon_code` *optional*
> > : `string` Automatically applies relevant coupon as soon as the checkout modal opens.
> >
> > `prediscount` *optional*
> > : `array` Custom discounts to display in the checkout order summary. Use this to show applied coupons, gift cards or loyalty points before the customer completes payment.
> >
> > `label` *mandatory*
> > : `string` Display name for the discount (for example: `WELCOME20`, `Gift Card (ABC123-XYZ789)`). Labels exceeding character limits will be trimmed with `...`.
> >
> > `value` *mandatory*
> > : `string` Discount amount with currency symbol in rupees format (for example: `₹200`). Must include currency symbol and be in rupees, not paise.
> >
> > `gift_card_applied` *optional*
> > : `boolean` Set to `true` when the discount represents a gift card. This ensures proper UI display and tracking. Possible values:
> >
> > * `true`: Discount is treated as a gift card with specialised UI display.
> > * `false` (default): Discount is treated as a regular coupon or promotional discount.
> >
> > `promotional_tag` *optional*
> > : `array` Promotional badges to display on specific products in the checkout.
> >
> > `tag` *mandatory*
> > : `string` Promotional text to display (maximum 15 characters). For examples: `free`, `bestseller`, `limited`.
> >
> > `variant_id` *mandatory*
> > : `string` Product variant id where the promotional tag should be displayed. Must match the variant\_id from your order line items.
> >
> > `notes` *optional*
> > : `object` Set of key-value pairs that can be used to store additional information about the payment. It can hold a maximum of 15 key-value pairs, each 256 characters long (maximum).
> >
> > `theme` *optional*
> > : `object` Thematic options to modify the appearance of Checkout.
> >
> > `color` *optional*
> > : `string` Enter your brand colour's HEX code to alter the text, payment method icons and CTA (call-to-action) button colour of the Checkout form.
> >
> > > [!NOTE]
> > >
> > > **Handy Tips**
> > >
> > > This is an on-demand feature. Please raise a request with your SPOC or our [Support team](https://razorpay.com/support/#request) to get it activated on your Razorpay account.
> >
> > `backdrop_color` *optional*
> > : `string` Enter a HEX code to change the Checkout's backdrop colour.
> >
> > `modal` *optional*
> > : `object` Options to handle the Checkout modal.
> >
> > `backdropclose` *optional*
> > : `boolean` Indicates whether clicking the translucent blank space outside the Checkout form should close the form. Possible values:
> >
> > * `true`: Closes the form when your customer clicks outside the checkout form.
> > * `false` (default): Does not close the form when customer clicks outside the checkout form.
> >
> > `escape` *optional*
> > : `boolean` Indicates whether pressing the **escape** key should close the Checkout form. Possible values:
> >
> > * `true` (default): Closes the form when the customer presses the **escape** key.
> > * `false`: Does not close the form when the customer presses the **escape** key.
> >
> > `handleback` *optional*
> > : `boolean` Determines whether Checkout must behave similar to the browser when back button is pressed. Possible values:
> >
> > * `true` (default): Checkout behaves similarly to the browser. That is, when the browser's back button is pressed, the Checkout also simulates a back press. This happens as long as the Checkout modal is open.
> > * `false`: Checkout does not simulate a back press when browser's back button is pressed.
> >
> > `confirm_close` *optional*
> > : `boolean` Determines whether a confirmation dialog box should be shown if customers attempts to close Checkout. Possible values:
> >
> > * `true`: Confirmation dialog box is shown.
> > * `false` (default): Confirmation dialog box is not shown.
> >
> > `ondismiss` *optional*
> > : `function` Used to track the status of Checkout and abandonment analytics. You can pass a modal object with `ondismiss: function()\{\}` as options. This function is called when the modal is closed by the user without completing payment.
> >
> > `animation` *optional*
> > : `boolean` Shows an animation before loading of Checkout. Possible values:
> >
> > * `true`(default): Animation appears.
> > * `false`: Animation does not appear.
> >
> > `callback_url` *optional*
> > : `string` Customers will be redirected to this URL on successful payment. Ensure that the domain of the Callback URL is allowlisted (also known as whitelisted).
> >
> > `redirect` *optional*
> > : `boolean` Determines whether to post a response to the event handler post payment completion or redirect to Callback URL. `callback_url` must be passed while using this parameter. Possible values:
> >
> > * `true`: Customer is redirected to the specified callback URL in case of payment failure.
> > * `false` (default): Customer is shown the Checkout popup to retry the payment.
> >
> > `timeout` *optional*
> > : `integer` Sets a timeout on Checkout, in seconds. After the specified time limit, the customer will not be able to use Checkout.
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > Some browsers may pause `JavaScript` timers when the user switches tabs, especially in power saver mode. This can cause the checkout session to stay active beyond the set timeout duration.
> >
> > `readonly` *optional*
> > : `object` Marks fields as read-only.
> >
> > `contact` *optional*
> > : `boolean` Used to set the `contact` field as readonly. Possible values:
> >
> > * `true`: Customer will not be able to edit this field.
> > * `false` (default): Customer will be able to edit this field.
> >
> > `email` *optional*
> > : `boolean` Used to set the `email` field as readonly. Possible values:
> >
> > * `true`: Customer will not be able to edit this field.
> > * `false` (default): Customer will be able to edit this field.
> >
> > `name` *optional*
> > : `boolean` Used to set the `name` field as readonly. Possible values:
> >
> > * `true`: Customer will not be able to edit this field.
> > * `false` (default): Customer will be able to edit this field.
> >
> > `send_sms_hash` *optional*
> > : `boolean` Used to auto-read Razorpay OTPs for login. Applicable from Android SDK version 1.6.34 and above. Possible values:
> >
> > * `true` (default): OTP is auto-read.
> > * `false`: OTP is not auto-read.
> >
> > `retry` *optional*
> > : `object` Parameters that enable retry of payment on the checkout.
> >
> > `enabled` *optional*
> > : `boolean` Determines whether the customers can retry payments on the checkout. Possible values:
> >
> > * `true` (default): Enables customers to retry payments.
> > * `false`: Disables customers from retrying the payment.
> >
> > `max_count` *optional*
> > : `integer` The number of times the customer can retry the payment. We recommend you to set this to 4. Having a larger number here can cause loops to occur.
> >
> > > [!WARNING]
> > >
> > > **Watch Out!**
> > >
> > > Web Integration does not support the `max_count` parameter. It is applicable only in Android and iOS SDKs.
> >
> > `config` *optional*
> > : `object` Parameters that enable checkout configuration.
> >
> > `display` *optional*
> > : `object` Child parameter that enables configuration of checkout display language.
> >
> > `language` *optional*
> > : `string` The language in which checkout should be displayed. Possible values:
> >
> > * `en`: English
> > * `ben`: Bengali
> > * `hi`: Hindi
> > * `mar`: Marathi
> > * `guj`: Gujarati
> > * `tam`: Tamil
> > * `tel`: Telugu

> [accordion] 7 Verify Payment Signature
>
> This is a mandatory step to confirm the authenticity of the details returned to the Checkout form for successful payments.
>
> > [accordion] To verify the `razorpay_signature` returned to you by the Checkout form:
> >
> > 1. Create a signature in your server using the following attributes:
> >    * `order_id`: Retrieve the `order_id` from your server. Do not use the `razorpay_order_id` returned by Checkout.
> >    * `razorpay_payment_id`: Returned by Checkout.
> >    * `key_secret`: Available in your server. The `key_secret` that was generated from the [Dashboard](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys).
> > 2. Use the SHA256 algorithm, the `razorpay_payment_id` and the `order_id` to construct a HMAC hex digest as shown below:
> >
> > ```html HMAC Hex Digest theme={null}
> > generated_signature = hmac_sha256(order_id + "|" + razorpay_payment_id, secret);
> >
> >   if (generated_signature == razorpay_signature) {
> >     payment is successful
> >   }
> > ```
> >
> > 3. If the signature you generate on your server matches the `razorpay_signature` returned to you by the Checkout form, the payment received is from an authentic source.
>
> > [accordion] Generate Signature on Your Server
> >
> > Given below is the sample code for payment signature verification:
> >
> > ```java Java theme={null}
> > RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
> >
> > String secret = "EnLs21M47BllR3X8PSFtjtbd";
> >
> > JSONObject options = new JSONObject();
> > options.put("razorpay_order_id", "order_IEIaMR65cu6nz3");
> > options.put("razorpay_payment_id", "pay_IH4NVgf4Dreq1l");
> > options.put("razorpay_signature", "0d4e745a1838664ad6c9c9902212a32d627d68e917290b0ad5f08ff4561bc50f");
> >
> > boolean status =  Utils.verifyPaymentSignature(options, secret);
> > ```
> >
> > ```php PHP theme={null}
> > $api = new Api($key_id, $secret);
> >
> > $api->utility->verifyPaymentSignature(array('razorpay_order_id' => $razorpayOrderId, 'razorpay_payment_id' => $razorpayPaymentId, 'razorpay_signature' => $razorpaySignature));
> > ```
> >
> > ```ruby Ruby theme={null}
> > require "razorpay"
> > Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
> >
> > payment_response = {
> >        razorpay_order_id: 'order_IEIaMR65cu6nz3',
> >        razorpay_payment_id: 'pay_IH4NVgf4Dreq1l',
> >        razorpay_signature: '0d4e745a1838664ad6c9c9902212a32d627d68e917290b0ad5f08ff4561bc50f'
> >      }
> > Razorpay::Utility.verify_payment_signature(payment_response)
> > ```
> >
> > ```python Python theme={null}
> > import razorpay
> > client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
> >
> > client.utility.verify_payment_signature({
> >   'razorpay_order_id': razorpay_order_id,
> >   'razorpay_payment_id': razorpay_payment_id,
> >   'razorpay_signature': razorpay_signature
> >   })
> > ```
> >
> > ```c .NET theme={null}
> > RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
> >
> > Dictionary<string, string> options = new Dictionary<string, string>();
> > options.Add("razorpay_order_id", "order_IEIaMR65cu6nz3");
> > options.Add("razorpay_payment_id", "pay_IH4NVgf4Dreq1l");
> > options.Add("razorpay_signature", "0d4e745a1838664ad6c9c9902212a32d627d68e917290b0ad5f08ff4561bc50f");
> >
> > Utils.verifyPaymentSignature(options);
> > ```
> >
> > ```javascript Node.js theme={null}
> > var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
> >
> > var { validatePaymentVerification, validateWebhookSignature } = require('./dist/utils/razorpay-utils');
> > validatePaymentVerification({"order_id": razorpayOrderId, "payment_id": razorpayPaymentId }, signature, secret);
> > ```
> >
> > ```go Go theme={null}
> > import ( razorpay "github.com/razorpay/razorpay-go" )
> > client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
> >
> > params := map[string]interface{}{
> >  "razorpay_order_id": "order_IEIaMR65cu6nz3",
> >  "razorpay_payment_id": "pay_IH4NVgf4Dreq1l",
> > }
> >
> > signature := "0d4e745a1838664ad6c9c9902212a32d627d68e917290b0ad5f08ff4561bc50f";
> > secret := "EnLs21M47BllR3X8PSFtjtbd";
> > utils.VerifyPaymentSignature(params, signature, secret)
> > ```
>
> > [accordion] Post Signature Verification
> >
> > After you have completed the integration, you can [set up webhooks](https://razorpay.com/docs/webhooks/setup-edit-payments.md), make test payments, replace the test key with the live key and integrate with other [APIs](https://razorpay.com/docs/api).
>
> Here are the links to our [SDKs](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard.md#client-libraries) for the supported platforms.

> [accordion] 8 Verify Payment Status
>
> Verify the payment status using the APIs and webhooks.
>
> > [tab] Fetch Payment API
> >
> > You can fetch the payment details using the [Fetch Payments API](https://razorpay.com/docs/api/payments/fetch-with-id.md).
> >
> > The different payment states are given below:
> >
> > | Payment State | Description |
> > | - | - |
> > | `created` | When the customer starts the payment. |
> > | `pending` | When the customer finally places the order. |
> > | `authorized` | The payment moves to the failed state if money is not captured within 45 days. It moves to the captured state when you confirm that the money is received. |
> > | `captured` | When you receive the money. |
> > | `refunded` | When the refund request is initiated. |
> > | `failed` | When the payment is failed. |
>
> > [tab] Webhooks
> >
> > You should [set up webhooks](https://razorpay.com/docs/webhooks/setup-edit-payments.md) on the Razorpay Dashboard to receive notifications when certain events occur.
> >
> > #### Orders Events
> >
> > We recommend you to subscribe to these orders events:
> >
> > | Webhook Event | Description |
> > | - | - |
> > | **order.created** | Triggered when an order is successfully created. |
> > | **order.placed** | Triggered when a COD order is successfully placed. |
> > | **order.paid** | Triggered when a prepaid order has been successfully completed. |
> > | **order.expired** | Triggered when an order has expired. |
> >
> > #### Payments Events
> >
> > We recommend you to subscribe to these payments events:
> >
> > | Webhook Event | Description |
> > | - | - |
> > | **payment.pending** | Triggered when a COD payment is moved to pending state. |
> > | **payment.captured** | Triggered when a payment is successfully captured. |
> > | **payment.failed** | Triggered when a payment fails. |
> >
> > #### Fulfillment Events
> >
> > We recommend you to subscribe to these fulfillment events:
> >
> > | Webhook Event | Description |
> > | - | - |
> > | **fulfillment.to\_be\_shipped** | Triggered when the business needs to act on the order |
> > | **fulfillment.ready\_to\_ship** | Triggered when the order needs to be picked by the logistics partner. |
> > | **fulfillment.in\_transit** | Triggered when the order is picked by the logistics partner. |
> > | **fulfillment.rto** | Triggered when the order is returned to origin because of customer unavailability or decline. |
> > | **fulfillment.delivered** | Triggered when the order is delivered. |
> > | **fulfillment.customer\_refunded** | Triggered when the order is picked for return as part of the refund. |

> [accordion] 9 Perform Post Payment Processing
>
> Based on the response, you can handle post-payment processing on your end.
>
> > [!WARNING]
> >
> > **Timeout Handling**
> >
> > If no API call is made within 45 seconds, our background job will assume there is a network drop off and will proceed to place the order on Shopify automatically.
>
> > [accordion] Fetch an Order
> >
> > Use the Fetch Orders API to retrieve order details, including customer information, address, shipping method and promotions of a particular order:
> >
> > `GET v1/orders/:id`
> >
> > ```bash Curl theme={null}
> > curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]\
> > -X GET https://api.razorpay.com/v1/orders/order_R1yDkxyIuKXXXX \
> > ```
> >
> > ```java Java theme={null}
> > RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
> > import com.razorpay.Order;
> > import com.razorpay.RazorpayClient;
> > import com.razorpay.RazorpayException;
> > try {
> >   Order order = razorpay.Orders.fetch("<order_id>");
> > } catch (RazorpayException e) {
> >   // Handle Exception
> >   System.out.println(e.getMessage());
> > }
> > ```
> >
> > ```python Python theme={null}
> > # do easy_install razorpay or
> > #    pip install razorpay
> >
> > import razorpay
> > razorpay.Client(auth=("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]"))
> >
> > order_id = <ORDER_ID>
> > resp = client.order.fetch(order_id)
> > ```
> >
> > ```php PHP theme={null}
> > $api = new Api($key_id, $secret);
> >
> > $api->order->fetch($orderId);
> > ```
> >
> > ```ruby Ruby theme={null}
> > require "razorpay"
> > Razorpay.setup('key_id', 'key_secret')
> >
> > order = Razorpay::Order.fetch('order_R1yDkxyIuKXXXX')
> > ```
> >
> > ```javascript Node.js theme={null}
> > var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
> >
> > instance.orders.fetch(orderId)
> > ```
> >
> > ```go Go theme={null}
> > import ( razorpay "github.com/razorpay/razorpay-go" )
> > client := razorpay.NewClient("<YOUR_API_KEY>", "<YOUR_API_SECRET>")
> >
> > body, err := client.Order.Fetch("<order_id>", nil, nil)
> > ```
> >
> > ```json Response: COD Orders theme={null}
> > {
> >   "id": "order_R1yDkxyIuKXXXX",
> >   "entity": "order",
> >   "amount": 507000,
> >   "amount_paid": 0,
> >   "amount_due": 507000,
> >   "currency": "INR",
> >   "receipt": "#30567",
> >   "offers": [
> >       "offer_QXwkRH1bOvXXXX",
> >       "offer_QXwoP07qnHXXXX",
> >       "offer_QYrcJ29gBCXXXX",
> >       "offer_QZDsVyMNzDXXXX",
> >       "offer_QtfwFTZYkGXXXX",
> >       "offer_Qtg3UsQyZaXXXX"
> >   ],
> >   "status": "placed",
> >   "attempts": 0,
> >   "notes": {
> >       "cart_id": "hWN2Am4BGnQrizKE3hzeQaXc?key=2b3cad31",
> >       "storefront_id": "gid://shopify/Cart/hf5Q?key=14bbbce35b8",
> >       "shopify_order_id": "6302119854247"
> >   },
> >   "created_at": 1756045901,
> >   "description": null,
> >   "checkout": null,
> >   "promotions": [
> >       {
> >           "code": "orderOff",
> >           "type": "cart_value",
> >           "value": 10000,
> >           "description": "order off",
> >           "reference_id": "offer_ORnSr9d2eAXXXX"
> >       }
> >   ],
> >   "cod_fee": 5000,
> >   "shipping_fee": 7000,
> >   "customer_details": {
> >       "contact": "+919100000000",
> >       "email": "gaurav.kumar@example.com",
> >       "shipping_address": {
> >           "city": "Bengaluru",
> >           "contact": "+919100000000",
> >           "country": "in",
> >           "line1": "Houseno:24",
> >           "line2": "Andree Road, Bheemanna Garden, Shanti Nagar",
> >           "name": "Gaurav Kumar",
> >           "state": "KARNATAKA",
> >           "tag": "Home",
> >           "type": "shipping_address",
> >           "zipcode": "560001"
> >       },
> >       "billing_address": {
> >           "city": "Bengaluru",
> >           "contact": "+919100000000",
> >           "country": "in",
> >           "line1": "Houseno:24",
> >           "line2": "Andree Road, Bheemanna Garden, Shanti Nagar",
> >           "name": "Gaurav Kumar",
> >           "state": "KARNATAKA",
> >           "tag": "Home",
> >           "type": "shipping_address",
> >           "zipcode": "560001"
> >       }
> >   },
> >   "line_items_total": 600000,
> >   "tax_details": {
> >       "total_tax": 4128,
> >       "taxes_included": true
> >   }
> > }
> > ```
> >
> > ```json Response: Prepaid Orders theme={null}
> > {
> >   "id": "order_R1yDkxyIuKXXXX",
> >   "entity": "order",
> >   "amount": 100700,
> >   "amount_paid": 100700,
> >   "amount_due": 0,
> >   "currency": "INR",
> >   "receipt": "#30414",
> >   "offers": [
> >       "offer_QXwkRH1bOvXXXX",
> >       "offer_QXwoP07qnHXXXX",
> >       "offer_QYrcJ29gBCXXXX",
> >       "offer_QZDsVyMNzDXXXX",
> >       "offer_QtfwFTZYkGXXXX",
> >       "offer_Qtg3UsQyZaXXXX"
> >   ],
> >   "status": "paid",
> >   "attempts": 1,
> >   "notes": {
> >       "cart_id": "hWN1TcwL?key=1a3a5a7c",
> >       "storefront_id": "gid://shopify/Cart/hIkey=af7c7800",
> >       "flits_cart_token": "hWcwL?key=1a3741dc_8740f5_175447",
> >       "shopify_order_id": "6266036191399"
> >   },
> >   "created_at": 1754466155,
> >   "description": null,
> >   "checkout": null,
> >   "promotions": [
> >       {
> >       "code": "orderOff",
> >       "type": "cart_value",
> >       "value": 10000,
> >       "description": "order off",
> >       "reference_id": "offer_ORnSr9d2eAXXXX"
> >       }
> >   ],
> >   "cod_fee": 0,
> >   "shipping_fee": 700,
> >   "customer_details": {
> >       "billing_address": {
> >       "city": "South West Delhi",
> >       "contact": "+919000090000",
> >       "country": "in",
> >       "id": "Qb3BljuFFoXXXX",
> >       "line1": "12",
> >       "line2": "Qutab Garh, Rama Krishna Puram",
> >       "name": "Gaurav Kumar",
> >       "state": "Delhi",
> >       "tag": "Home",
> >       "type": "billing_address",
> >       "zipcode": "110057"
> >       },
> >       "contact": "+919000090000",
> >       "email": "gaurav.kumar@example.com",
> >       "shipping_address": {
> >       "city": "South West Delhi",
> >       "contact": "+919000090000",
> >       "country": "in",
> >       "id": "Qb3BljuFFoXXXX",
> >       "line1": "12",
> >       "line2": "Qutab Garh, Rama Krishna Puram",
> >       "name": "Gaurav Kumar",
> >       "state": "Delhi",
> >       "tag": "Home",
> >       "type": "shipping_address",
> >       "zipcode": "110057"
> >       }
> >   },
> >   "line_items_total": 110000,
> >   "tax_details": {
> >       "total_tax": 0,
> >       "taxes_included": true
> >   }
> > }
> > ```
> >
> > Know more about the [Orders API.](https://razorpay.com/docs/api/orders.md)
> >
> > > [!NOTE]
> > >
> > > **Order Status**
> > >
> > > Check the order status for the following:
> > >
> > > * Prepaid orders: `paid`.
> > > * COD orders: `placed`.
> >
> > > [accordion] Path Parameter
> > >
> > > `id` *mandatory*
> > > : `string` Unique identifier of the order to be retrieved.
> >
> > > [accordion] Response Parameters
> > >
> > > `id`
> > > : `string` Unique identifier of the order. For example, `order_R1yDkxyIuKXXXX`.
> > >
> > > `entity`
> > > : `string` Type of entity. Value is `order`.
> > >
> > > `amount`
> > > : `integer` Total order amount in the smallest currency unit (paise).
> > >
> > > `amount_paid`
> > > : `integer` Amount paid towards the order in paise. For prepaid orders, this shows the actual amount paid. For COD orders, this is `0` until payment is collected.
> > >
> > > `amount_due`
> > > : `integer` Outstanding amount due in paise. For prepaid orders, this shows any remaining balance. For COD orders, this equals the `amount` field until payment is collected.
> > >
> > > `currency`
> > > : `string` The 3-letter ISO currency code. For example, `INR`.
> > >
> > > `receipt`
> > > : `string` Receipt identifier for internal reference. For example, `#30567`.
> > >
> > > `offers`
> > > : `array` Array of offer IDs applied to the order.
> > >
> > > `status`
> > > : `string` Current status of the order. Possible values:
> > >
> > > * `placed`: Order placed but payment pending (COD orders).
> > > * `paid`: Order placed and payment completed (prepaid orders).
> > > * `cancelled`: Order cancelled.
> > > * `refunded`: Order refunded.
> > >
> > > `attempts`
> > > : `integer` Number of payment attempts made for this order. For example, `1`.
> > >
> > > `notes`
> > > : `object` Custom notes added to the order containing integration-specific data.
> > >
> > > `cart_id`
> > > : `string` Shopping cart identifier.
> > >
> > > `storefront_id`
> > > : `string` Storefront system identifier.
> > >
> > > `shopify_order_id`
> > > : `string` Shopify order reference.
> > >
> > > `flits_cart_token`
> > > : `string` Flits integration token (optional).
> > >
> > > `created_at`
> > > : `integer` Unix timestamp indicating when the order was created. For example, `1756045901`.
> > >
> > > `description`
> > > : `string|null` Order description. Returns `null` if no description is provided.
> > >
> > > `checkout`
> > > : `string|null` Checkout identifier. Returns `null` if not applicable.
> > >
> > > `promotions`
> > > : `array` Array of promotion objects applied to the order.
> > >
> > > `code`
> > > : `string` Promotion code used. For example, `orderOff`.
> > >
> > > `type`
> > > : `string` Type of promotion. For example, `cart_value`.
> > >
> > > `value`
> > > : `integer` Discount value in paise. For example, `10000` for ₹100.
> > >
> > > `description`
> > > : `string` Human-readable promotion description.
> > >
> > > `reference_id`
> > > : `string` Internal reference for the promotion.
> > >
> > > `cod_fee`
> > > : `integer` Cash on Delivery charges in paise. For COD orders, this contains the fee amount (for example, `5000` for ₹50). For prepaid orders, this is `0`.
> > >
> > > `shipping_fee`
> > > : `integer` Shipping charges in paise. For example, `700` for ₹7.
> > >
> > > `customer_details`
> > > : `object` Customer information.
> > >
> > > `contact`
> > > : `string` Customer's phone number.
> > >
> > > `email`
> > > : `string` Customer's email address.
> > >
> > > `shipping_address`
> > > : `object` Complete shipping address information.
> > >
> > > `city`
> > > : `string` City name.
> > >
> > > `contact`
> > > : `string` Contact number for delivery.
> > >
> > > `country`
> > > : `string` Country code. For example, `in`.
> > >
> > > `id`
> > > : `string` Address identifier (optional).
> > >
> > > `line1`
> > > : `string` Address line 1.
> > >
> > > `line2`
> > > : `string` Address line 2.
> > >
> > > `name`
> > > : `string` Recipient name.
> > >
> > > `state`
> > > : `string` State name.
> > >
> > > `tag`
> > > : `string` Address tag. For example, `Home`.
> > >
> > > `type`
> > > : `string` Address type. Value is `shipping_address`.
> > >
> > > `zipcode`
> > > : `string` Postal code.
> > >
> > > `billing_address`
> > > : `object` Complete billing address information.
> > >
> > > `city`
> > > : `string` City name.
> > >
> > > `contact`
> > > : `string` Contact number for billing.
> > >
> > > `country`
> > > : `string` Country code. For example, `in`.
> > >
> > > `id`
> > > : `string` Address identifier (optional).
> > >
> > > `line1`
> > > : `string` Address line 1.
> > >
> > > `line2`
> > > : `string` Address line 2.
> > >
> > > `name`
> > > : `string` Account holder name.
> > >
> > > `state`
> > > : `string` State name.
> > >
> > > `tag`
> > > : `string` Address tag. For example, `Home`.
> > >
> > > `type`
> > > : `string` Address type. Value is `billing_address`.
> > >
> > > `zipcode`
> > > : `string` Postal code.
> > >
> > > `line_items_total`
> > > : `integer` Total value of line items in paise before adding shipping fees and COD fees, after applying promotions. For example, `60000` for ₹600.
> > >
> > > `tax_details`
> > > : `object` Tax information.
> > >
> > > `total_tax`
> > > : `integer` Total tax amount in paise. For example, `4128`.
> > >
> > > `taxes_included`
> > > : `boolean` Indicates whether taxes are included in the item prices. Possible values:
> > >
> > > * `true`: Taxes are included in item prices.
> > > * `false`: Taxes are separate from item prices.
>
> > [accordion] Fetch a Payment
> >
> > Use the Fetch Payments API to retrieve comprehensive payment details, including transaction status, payment method, customer information, settlement details, and the associated order information for a specific payment:
> >
> > `GET v1/payments/:id`
> >
> > ```bash Curl theme={null}
> > curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
> > -X GET https://api.razorpay.com/v1/payments/pay_R1yFlWQar3XXXX
> > ```
> >
> > ```java Java theme={null}
> > RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
> >
> > String paymentId = "pay_R1yFlWQar3XXXX";
> >
> > Payment payment = razorpay.payments.fetch(paymentId);
> > ```
> >
> > ```python Python theme={null}
> > import razorpay
> > client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
> >
> > client.payment.fetch(paymentId)
> > ```
> >
> > ```go Go theme={null}
> > import ( razorpay "github.com/razorpay/razorpay-go" )
> > client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")
> >
> > paymentId := "pay_R1yFlWQar3XXXX"
> >
> > body, err := client.Payment.Fetch(paymentId, nil, nil)
> > ```
> >
> > ```php PHP theme={null}
> > $api = new Api($key_id, $secret);
> >
> > $api->payment->fetch($paymentId);
> > ```
> >
> > ```ruby Ruby theme={null}
> > require "razorpay"
> > Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')
> >
> > paymentId = "pay_R1yFlWQar3XXXX"
> >
> > Razorpay::Payment.fetch(paymentId)
> > ```
> >
> > ```javascript Node.js theme={null}
> > var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })
> >
> > instance.payments.fetch(paymentId)
> > ```
> >
> > ```csharp .NET theme={null}
> > RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
> > Payment payment = client.Payment.Fetch(paymentId);
> > ```
> >
> > ```json Response: COD Orders theme={null}
> > {
> >   "id": "pay_R1yFlWQar3XXXX",
> >   "entity": "payment",
> >   "amount": 55700,
> >   "currency": "INR",
> >   "status": "pending",
> >   "order_id": "order_R1yDkxyIuKXXXX",
> >   "invoice_id": null,
> >   "international": false,
> >   "method": "cod",
> >   "amount_refunded": 0,
> >   "refund_status": null,
> >   "captured": false,
> >   "description": null,
> >   "card_id": null,
> >   "bank": null,
> >   "wallet": null,
> >   "vpa": null,
> >   "email": "gaurav.kumar@example.com",
> >   "contact": "+919100000000",
> >   "notes": {
> >     "cart_id": "hWN2QaXc?key=2b3cad31",
> >     "storefront_id": "gid://shopify/Cart/h?key=14bbf59ce35b8"
> >   },
> >   "fee": null,
> >   "tax": null,
> >   "error_code": null,
> >   "error_description": null,
> >   "error_source": null,
> >   "error_step": null,
> >   "error_reason": null,
> >   "acquirer_data": {},
> >   "created_at": 1756046099,
> >   "receiver_type": null
> > }
> > ```
> >
> > ```json Response: Prepaid Orders theme={null}
> > {
> >   "id": "pay_R1yFlWQar3XXXX",
> >   "entity": "payment",
> >   "amount": 90630,
> >   "currency": "INR",
> >   "status": "captured",
> >   "order_id": "order_R1yDkxyIuKXXXX",
> >   "invoice_id": null,
> >   "international": false,
> >   "method": "upi",
> >   "amount_refunded": 0,
> >   "refund_status": null,
> >   "captured": true,
> >   "description": null,
> >   "card_id": null,
> >   "bank": null,
> >   "wallet": null,
> >   "vpa": "gaurav.kumar@exampleupi",
> >   "email": "gaurav.kumar@example.com",
> >   "contact": "+919000090000",
> >   "notes": {
> >     "cart_id": "hWNsVrcwL?key=1a3a457ddc",
> >     "storefront_id": "gid://shopify/Cart/hWv3e8?key=af707",
> >     "flits_cart_token": "hWrcwL?key=1a3a5a70f5_17547",
> >     "optimizer_provider_name": "razorpay"
> >   },
> >   "fee": 0,
> >   "tax": 0,
> >   "error_code": null,
> >   "error_description": null,
> >   "error_source": null,
> >   "error_step": null,
> >   "error_reason": null,
> >   "acquirer_data": {
> >     "rrn": "727947422583",
> >     "upi_transaction_id": "1F723677C679EF578A95"
> >   },
> >   "created_at": 1754466271,
> >   "receiver_type": null,
> >   "upi": {
> >     "vpa": "gaurav.kumar@exampleupi"
> >   }
> > }
> > ```
> >
> > Know more about the [Payments API](https://razorpay.com/docs/api/payments).
> >
> > > [accordion] Path Parameter
> > >
> > > `id` *mandatory*
> > > : `string` Unique identifier of the payment to be retrieved.
> >
> > > [accordion] Response Parameters
> > >
> > > `id`
> > > : `string` Unique identifier of the payment. For example, `pay_R1yFlWQar3XXXX`.
> > >
> > > `entity`
> > > : `string` Type of entity. Value is `payment`.
> > >
> > > `amount`
> > > : `integer` Payment amount in the smallest currency unit (paise). For COD payments, this includes the COD fee (for example, `55700` for ₹557). For prepaid payments, this equals the captured amount (for example, `90630` for ₹906.30).
> > >
> > > `currency`
> > > : `string` The 3-letter ISO currency code. For example, `INR`.
> > >
> > > `status`
> > > : `string` Current status of the payment. Possible values:
> > >
> > > * `pending`: Payment pending collection (COD orders).
> > > * `captured`: Payment successfully captured (prepaid orders).
> > > * `authorized`: Payment authorized but not captured.
> > > * `failed`: Payment attempt failed.
> > >
> > > `order_id`
> > > : `string` Unique identifier of the associated order. For example, `order_R1yDkxyIuKXXXX`.
> > >
> > > `invoice_id`
> > > : `string|null` Unique identifier of the associated invoice. Returns `null` if no invoice is linked.
> > >
> > > `international`
> > > : `boolean` Indicates whether this is an international payment. Possible values:
> > >
> > > * `true`: International payment.
> > > * `false`: Domestic payment.
> > >
> > > `method`
> > > : `string` Payment method used. Possible values include:
> > >
> > > * `cod`
> > > * `upi`
> > > * `card`
> > > * `netbanking`
> > > * `wallet`
> > >
> > > `amount_refunded`
> > > : `integer` Amount refunded in paise. For example, `0` indicates no refund has been processed.
> > >
> > > `refund_status`
> > > : `string|null` Current refund status. Returns `null` if no refund is applicable. Possible values:
> > >
> > > * `partial`: Partial refund processed.
> > > * `full`: Full refund processed.
> > >
> > > `captured`
> > > : `boolean` Indicates whether the payment has been captured. Possible values:
> > >
> > > * `true`: Payment has been captured.
> > > * `false`: Payment has not been captured.
> > >
> > > `description`
> > > : `string|null` Payment description. Returns `null` if no description is provided.
> > >
> > > `card_id`
> > > : `string|null` Unique identifier of the card used for payment. Returns `null` for non-card payments.
> > >
> > > `bank`
> > > : `string|null` Bank identifier for netbanking payments. Returns `null` for other payment methods.
> > >
> > > `wallet`
> > > : `string|null` Wallet provider identifier. Returns `null` for non-wallet payments.
> > >
> > > `vpa`
> > > : `string|null` Virtual Payment Address for UPI payments. For example, `gaurav.kumar@exampleupi`. Returns `null` for non-UPI payments.
> > >
> > > `email`
> > > : `string` Customer's email address.
> > >
> > > `contact`
> > > : `string` Customer's phone number.
> > >
> > > `notes`
> > > : `object` Custom notes added to the payment containing integration-specific data.
> > >
> > > `cart_id`
> > > : `string` Shopping cart identifier.
> > >
> > > `storefront_id`
> > > : `string` Storefront system identifier.
> > >
> > > `flits_cart_token`
> > > : `string` Flits integration token (optional).
> > >
> > > `optimizer_provider_name`
> > > : `string` Payment optimizer provider name (optional).
> > >
> > > `fee`
> > > : `integer|null` Processing fee charged in paise. For example, `0` indicates no fee. Returns `null` for COD payments.
> > >
> > > `tax`
> > > : `integer|null` Tax amount on processing fee in paise. For example, `0` indicates no tax. Returns `null` for COD payments.
> > >
> > > `error_code`
> > > : `string|null` Error code if payment failed. Returns `null` for successful payments.
> > >
> > > `error_description`
> > > : `string|null` Human-readable error description. Returns `null` for successful payments.
> > >
> > > `error_source`
> > > : `string|null` Source of the error. Returns `null` for successful payments.
> > >
> > > `error_step`
> > > : `string|null` Step at which error occurred. Returns `null` for successful payments.
> > >
> > > `error_reason`
> > > : `string|null` Reason for the error. Returns `null` for successful payments.
> > >
> > > `acquirer_data`
> > > : `object` Data from the payment acquirer.
> > >
> > > `rrn`
> > > : `string` Retrieval Reference Number from the acquirer (optional).
> > >
> > > `upi_transaction_id`
> > > : `string` UPI transaction identifier from the acquirer (optional).
> > >
> > > `created_at`
> > > : `integer` Unix timestamp indicating when the payment was created. For example, `1756046099`.
> > >
> > > `receiver_type`
> > > : `string|null` Type of receiver for the payment. Returns `null` if not applicable.
> > >
> > > `upi`
> > > : `object` UPI-specific payment details (only present for UPI payments).
> > >
> > > `vpa`
> > > : `string` Virtual Payment Address used for the UPI payment.

> [accordion] 10 Analytics Integration (Advanced Feature)
>
> Track customer journey events to understand customer behavior and optimise conversion rates.
>
> Magic Checkout provides detailed analytics events that help you analyse the checkout funnel and identify optimisation opportunities.
>
> ```javascript theme={null}
> // Use the same Razorpay instance for analytics
> var rzp1 = new Razorpay(options);
>
> // Register analytics event listener
> rzp1.on('mx-analytics', function(data) {
>   if (data && data.event) {
>     console.log('Analytics Event:', data.event, data);
>
>     // Send to your analytics platform
>     sendToAnalytics(data);
>   }
> });
>
> function sendToAnalytics(eventData) {
>   // Example: Send to Google Analytics
>   if (typeof gtag !== 'undefined') {
>     gtag('event', eventData.event, {
>       'event_category': 'Magic Checkout',
>       'event_label': eventData.paymentMode,
>       'value': eventData.latestTotal
>     });
>   }
>
>   // Example: Send to your custom analytics
>   fetch('/analytics-endpoint', {
>     method: 'POST',
>     headers: { 'Content-Type': 'application/json' },
>     body: JSON.stringify(eventData)
>   });
> }
> ```
>
> #### Events
>
> | Event | Description | Triggered |
> | - | - | - |
> | `initiate` | Checkout started | Customer opens checkout modal |
> | `otp_initiated` | Phone verification | Customer enters phone number |
> | `payment_initiated` | Payment attempt | Customer clicks pay button |
> | `checkout_abandoned` | Checkout closed | Customer exits without paying |
> | `coupon_applied` | Discount applied | Valid coupon code used |
> | `payment_failed` | Payment unsuccessful | Payment attempt fails |
>
> Use these examples to implement event tracking and purchase analytics:
>
> > [tab] Event Handling
> >
> > Track checkout journey events as they occur:
> >
> > ```javascript theme={null}
> > rzp1.on('mx-analytics', function(data) {
> >   switch(data.event) {
> >     case 'initiate':
> >       console.log('Checkout opened for amount:', data.totalAmount);
> >       break;
> >
> >     case 'payment_initiated':
> >       console.log('Payment started via:', data.paymentMethod);
> >       break;
> >
> >     case 'payment_failed':
> >       console.log('Payment failed for order:', data.totalAmount);
> >       // Show retry message or track failure reasons
> >       break;
> >
> >     case 'checkout_abandoned':
> >       console.log('Customer left after:', data.time_since_open, 'milliseconds');
> >       // Track abandonment funnel for optimisation
> >       break;
> >
> >     case 'coupon_applied':
> >       console.log('Coupon applied:', data.couponCode, 'Discount:', data.couponDiscountValue);
> >       break;
> >   }
> > });
> > ```
>
> > [tab] Purchase Tracking
> >
> > Track successful payment completion in your handler function:
> >
> > ```javascript theme={null}
> > "handler": function(response) {
> >   // Payment successful
> >   console.log('Purchase completed:', response);
> >
> >   // Track purchase event
> >   sendToAnalytics({
> >     event: 'purchase',
> >     payment_id: response.razorpay_payment_id,
> >     order_id: response.razorpay_order_id,
> >     amount: /* your order amount */,
> >     currency: 'INR'
> >   });
> >
> >   // Redirect to success page
> >   window.location.href = '/payment-success?payment_id=' + response.razorpay_payment_id;
> > }
> > ```

## Go-Live Best Practices

Before going live, make sure to check the following:

* If you configured the above settings in Test Mode, ensure you replicate them in Live Mode.
* Ensure you use API keys generated in Live Mode.
* If you have multiple Razorpay accounts, ensure you use the Live key from the correct account you intend to go live with.

### Related Information

[Troubleshoot and FAQs](https://razorpay.com/docs/payments/magic-checkout/troubleshooting-faqs.md#web)
