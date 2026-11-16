> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# SKU and Brand Offers on Standard Checkout

> Apply offers to specific products (SKUs) in a customer's cart on Razorpay Standard Checkout.

Available in
🇮🇳 India

SKU and Brand Offers let you attach offers to individual products (SKUs) in an order instead of the whole cart. For example, a customer buying a laptop and a mouse can get ₹3,000 off the laptop and ₹2,000 off the mouse in a single checkout session. Both merchant-funded offers and brand-funded offers, such as a brand's bank discount on a specific phone model, are supported.

You send the cart's SKUs in the order. Razorpay Standard Checkout finds the offers that match those SKUs, shows them to the customer and applies the best offers automatically.

To show these offers on your own website or app before checkout, for example on product pages, use the [Fetch and Match Offers APIs](https://razorpay.com/docs/payments/offers/fetch-match-offers.md).

> [!NOTE]
>
> **Feature Request**
>
> This is an on-demand feature. Contact your Razorpay account manager to enable SKU and Brand Offers on your account. Razorpay configures the offers and the SKUs they apply to for you. SKU and Brand Offers on Standard Checkout work in both test mode and live mode, so you can test your integration before you go live.

## Availability

| | Supported |
| - | - |
| **Platforms** | Standard Checkout on web, Android and iOS. Shopify and Magento plugins. [Payment Links](https://razorpay.com/docs/payments/payment-links/offers.md#sku-and-brand-offers-on-payment-links). |
| **Payment methods** | Cards and EMI. |

## Customer Experience

| Checkout stage | What the customer sees |
| - | - |
| Checkout opens | Cart items with SKU names and quantities. Offers that apply to those SKUs are highlighted. |
| Selects a payment method | The best offers for that payment method are applied automatically. |
| Completes the payment | The discount is deducted from the amount payable. The success screen shows the savings for each item. |

Watch this video to see SKU and Brand Offers on Standard Checkout. The customer sees the offers for each product in the cart, the best offers are applied automatically and the order summary shows the discount on each item.

<video controls muted playsInline preload="metadata" aria-label="Standard Checkout with two items in the cart: the Save more sheet lists a 5,000 rupee HDFC card discount on iPhone 16 and a 3,000 rupee discount on Apple Watch Series 10, both offers are applied for 8,000 rupees off, and the order summary shows each product's discount and a grand total of 1,01,800 rupees.">
  <source src="https://mintcdn.com/razorpay-881012b3/1HTwZNb6MPt43Eps/static/docs-home/assets/sku-offers-standard-checkout-demo.mp4?fit=max&auto=format&n=1HTwZNb6MPt43Eps&q=85&s=d48948411b54795084481be7c9acf018" type="video/mp4" />
</video>

## How It Works

Your backend makes the API calls. Standard Checkout handles everything in between.

| # | Actor | Action | API or mechanism |
| - | - | - | - |
| 1 | Customer | Adds products to the cart and clicks **Pay**. | — |
| 2 | Your backend | Creates an order with `line_items`. | [Create an Order](#step-1-create-an-order-with-line-items) |
| 3 | Your frontend | Opens Standard Checkout with the `order_id`. | [Standard Checkout](#step-2-open-standard-checkout) |
| 4 | Razorpay | Loads the offers that apply to the SKUs in the order. | Automatic |
| 5 | Customer | Selects a payment method and enters the payment details. | — |
| 6 | Razorpay | Applies the best offers. | Automatic |
| 7 | Customer | Clicks **Pay Now**. | — |
| 8 | Razorpay | Processes the payment and sends the `payment.authorized` webhook. | [Webhook](#step-3-handle-the-payment-authorized-webhook) |
| 9 | Your backend | Fetches the order to confirm which offers were applied. | [Fetch Order](#step-4-fetch-the-order-to-confirm-applied-offers) |

## Integration Steps

### Step 1: Create an Order With Line Items

When the customer clicks **Pay**, create an order using the [Orders API](https://razorpay.com/docs/api/orders/create.md) and pass every SKU in the cart in the `line_items` array. Razorpay matches offers using these line items, so include all SKUs with accurate prices and quantities.

> [!WARNING]
>
> **Watch Out!**
>
> The order `amount` must equal the total of `price` × `quantity` across all `line_items`. For example, a smartphone at ₹40,000 and earbuds at ₹15,000 make an order `amount` of `5500000` (₹55,000).

`POST /v1/orders`

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/orders \
-H "content-type: application/json" \
-d '{
  "amount": 5500000,
  "currency": "INR",
  "receipt": "receipt_order_001",
  "line_items": [
    {
      "sku": "SKU001",
      "brand": "acme",
      "name": "Smartphone 128 GB",
      "price": 4000000,
      "quantity": 1,
      "image_url": "https://example.com/images/smartphone.jpg"
    },
    {
      "sku": "SKU002",
      "brand": "acme",
      "name": "Wireless earbuds",
      "price": 1500000,
      "quantity": 1,
      "image_url": "https://example.com/images/earbuds.jpg"
    }
  ]
}'
```

#### Request Parameters

**amount** `integer` *required*

Total order amount in paise. It must equal the total of `price` × `quantity` across all `line_items`. For example, pass `5500000` for ₹55,000.

**currency** `string` *required*

Currency of the order. Possible value is `INR`.

**receipt** `string`

Your internal order reference for reconciliation. Maximum length is 40 characters and it must be unique.

**line\_items** `array` *required*

The products in the customer's cart.

**line\_items\[].sku** `string` *required*

SKU identifier of the product. It must match the SKU configured in the offer.

**line\_items\[].brand** `string` *required*

Brand of the product. For example, `apple`. Not case-sensitive. Brand offers are evaluated correctly only when you pass it.

**line\_items\[].price** `integer` *required*

Unit price of the product in paise.

**line\_items\[].quantity** `integer` *required*

Number of units of the product.

**line\_items\[].name** `string`

Name of the product. Shown to the customer on Checkout.

**line\_items\[].image\_url** `string`

Public URL of the product image.

#### Response

```json theme={null}
{
  "id": "order_DtEkng132N71M8",
  "entity": "order",
  "amount": 5500000,
  "amount_paid": 0,
  "amount_due": 5500000,
  "currency": "INR",
  "receipt": "receipt_order_001",
  "offers": ["offer_DtEhEm3XslgfXE"],
  "status": "created",
  "attempts": 0,
  "created_at": 1748750400
}
```

#### Response Parameters

**id** `string`

Unique identifier of the order. Pass this to Standard Checkout.

**status** `string`

Status of the order. It is `created` when the order is created successfully.

**offers** `array`

Identifiers of the offers that apply to the SKUs in this order.

**receipt** `string`

Your internal order reference, returned as sent.

### Step 2: Open Standard Checkout

Open [Standard Checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard.md) with the `order_id` from Step 1. You do not need to pass offer IDs. Checkout reads the `line_items` on the order and fetches and displays the offers that apply.

```js Checkout Options theme={null}
var options = {
  key: "YOUR_KEY_ID",
  order_id: "order_DtEkng132N71M8", // id from the Create Order API response
  name: "Acme Corp",
  // prefill, theme and handler as per your integration
};
var rzp = new Razorpay(options);
rzp.open();
```

> [!WARNING]
>
> **Watch Out!**
>
> The discount breakdown for each SKU is shown only inside Standard Checkout. The Create Order API response returns only the offers that apply to the order. To confirm which offers were applied after the payment, [fetch the order](#step-4-fetch-the-order-to-confirm-applied-offers).

### Step 3: Handle the payment.authorized Webhook

Razorpay sends the [`payment.authorized`](https://razorpay.com/docs/webhooks/payments#payment-authorised) webhook to your endpoint after the payment is processed. [Set up your webhook endpoint](https://razorpay.com/docs/webhooks/setup-edit-payments.md) on the Dashboard. Your endpoint must return HTTP `200`. Otherwise, Razorpay retries the delivery. Know more about [webhook delivery and retries](https://razorpay.com/docs/webhooks/best-practices.md#delivery-attempts-and-retries).

```json Sample Payload theme={null}
{
  "entity": "event",
  "account_id": "acc_BFQ7uQEaa6Kdt8",
  "event": "payment.authorized",
  "contains": ["payment"],
  "payload": {
    "payment": {
      "entity": {
        "id": "pay_A1B2C3D4E5F6G7",
        "entity": "payment",
        "amount": 5000000,
        "currency": "INR",
        "status": "authorized",
        "order_id": "order_DtEkng132N71M8",
        "method": "card",
        "captured": false,
        "created_at": 1748750600
      }
    }
  }
}
```

| Field | Description |
| - | - |
| `payload.payment.entity.id` | Payment ID. Use it to capture or refund the payment. |
| `payload.payment.entity.order_id` | The order this payment belongs to. |
| `payload.payment.entity.amount` | Amount charged in paise, after the discount. |
| `payload.payment.entity.status` | `authorized` means the payment succeeded. [Capture the payment](https://razorpay.com/docs/payments/payments/capture-settings.md) if it is not captured automatically. |

### Step 4: Fetch the Order to Confirm Applied Offers

After you receive the `payment.authorized` webhook, fetch the order with `expand[]=offers`. The response shows the final order state, the offers applied and the discount on each SKU. Use it for fulfilment, CRM and reconciliation.

> [!NOTE]
>
> **Handy Tips**
>
> Call this API only after you receive the `payment.authorized` webhook. The order status and applied offers are final only once the payment is authorised.

`GET /v1/orders/:id?expand[]=offers`

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET 'https://api.razorpay.com/v1/orders/order_DtEkng132N71M8?expand[]=offers'
```

```json Response theme={null}
{
  "id": "order_DtEkng132N71M8",
  "entity": "order",
  "amount": 5500000,
  "amount_paid": 5000000,
  "amount_due": 0,
  "currency": "INR",
  "receipt": "receipt_order_001",
  "status": "paid",
  "attempts": 1,
  "notes": {},
  "offers": ["offer_DtEhEm3XslgfXE"],
  "offers_applied": {
    "entity": "collection",
    "count": 1,
    "items": [
      {
        "id": "offer_DtEhEm3XslgfXE",
        "status": "redeemed",
        "benefits": [
          {
            "type": "instant_discount",
            "applicable_on": "line_item",
            "calculated_benefit_value": 500000,
            "benefit_breakup": [
              {
                "sku": "SKU001",
                "brand": "acme",
                "applied_quantity": 1,
                "calculated_benefit_value": 500000
              }
            ]
          }
        ]
      }
    ]
  },
  "created_at": 1748750400
}
```

#### Response Parameters

**id** `string`

Unique identifier of the order.

**amount** `integer`

Original order amount in paise, before discounts.

**amount\_paid** `integer`

Amount charged to the customer in paise, after discounts.

**amount\_due** `integer`

Amount still due in paise. It is `0` for a fully paid order.

**status** `string`

Status of the order. Possible values are `created`, `attempted` and `paid`.

**notes** `object`

Key-value pairs of notes for the order.

**offers** `array`

IDs of the offers on the order, including the ones in `offers_applied`.

**offers\_applied** `object`

Applied offers: `entity` (always `collection`), `count` and `items`. Returned when you pass `expand[]=offers`.

**offers\_applied.items\[].id** `string`

Identifier of the applied offer.

**offers\_applied.items\[].status** `string`

`redeemed` means the offer was applied successfully.

**offers\_applied.items\[].benefits** `array`

Benefits applied by this offer.

* `type`: Benefit type. Possible values are `instant_discount`, `cashback`, `no_cost_emi`, `low_cost_emi` and `already_discounted`.
* `applicable_on`: `line_item` for an SKU-level offer or `cart` for a cart-level offer.
* `calculated_benefit_value`: Total benefit amount from this benefit in paise.
* `benefit_breakup`: Benefit on each SKU, with `sku`, `brand`, `applied_quantity` and `calculated_benefit_value`. Present only for `line_item` benefits.

The API returns these responses without an error:

| Scenario | Behaviour |
| - | - |
| `expand[]=offers` is not passed | `offers_applied` is not included. |
| No offers were applied to the order | `offers_applied.count` is `0`. |
| The order is in `created` state and the payment is not complete | Order details are returned and `offers_applied` is empty. |

## Block and Unblock IMEIs for Brand Offers

For Brand Offers, you may need to block the IMEI or serial number of each device you sell against the order. Blocking records the sale of that device with the brand. Unblocking reverses it, for example when the order is refunded or cancelled.

> [!WARNING]
>
> **Watch Out!**
>
> For certain brands, the brand-funded offer amount is not settled to you unless you block the IMEI of each device sold. Check with your account manager whether this applies to the brands you sell.

To block or unblock an IMEI from the Dashboard:

1. Log in to the Dashboard and click **Offers**.
2. Click the **IMEI Block / Unblock** tab.
3. Select **Block** or **Unblock**.
4. Enter the details of the device:
   * **Razorpay Order ID** (Mandatory): The order the device was sold against. For example, `order_DtEkng132N71M8`.
   * **SKU** (Mandatory): The SKU of the device. It must match a line item on the order.
   * **Brand** (Mandatory): The brand of the device. For example, `Apple`.
   * **IMEI / Serial No.** (Mandatory): The 15-digit IMEI for phones. For other devices, the serial number.
   * **Dealer Code** (Optional): The identifier issued to you by the brand, if you have one.
5. Click **Block device** or **Unblock device**.

![IMEI Block / Unblock tab under Offers on the Dashboard, with the Block form showing Razorpay Order ID, SKU, Brand, IMEI / Serial No. and Dealer Code fields and a Block device button](https://mintcdn.com/razorpay-881012b3/lDyj6k-g77xZS0F7/static/docs-home/assets/offers-imei-block-unblock.png?fit=max\&auto=format\&n=lDyj6k-g77xZS0F7\&q=85\&s=9cf4bdb86272f12125b434b930c12a62)

Submit the form once for each device. For orders with more than one SKU or unit, repeat it for each device.

> [!NOTE]
>
> **Handy Tips**
>
> * Block the IMEI after the payment is complete.
> * If you refund or cancel the order, unblock the IMEI. Refunding the payment does not unblock it.
> * The **IMEI Block / Unblock** tab is available on request. Contact your account manager to enable it.

## SKU and Brand Offers on Payment Links

You can also apply SKU and Brand Offers to Payment Links by adding product details when you create the link from the Dashboard. Know more about [SKU and Brand Offers on Payment Links](https://razorpay.com/docs/payments/payment-links/offers.md#sku-and-brand-offers-on-payment-links).

### Related Information

* [About Offers](https://razorpay.com/docs/payments/offers)
* [Integrate Offers with Standard Checkout](https://razorpay.com/docs/payments/offers/standard-integration)
* [Fetch and Match Offers APIs](https://razorpay.com/docs/payments/offers/fetch-match-offers.md)
* [Standard Checkout Integration](https://razorpay.com/docs/payments/payment-gateway/web-integration/standard.md)
* [Orders API](https://razorpay.com/docs/api/orders.md)
* [Payment Webhooks](https://razorpay.com/docs/webhooks/payments.md)
