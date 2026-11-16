> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Embedded Quick Buy: Mobile Web Integration

> Integrate Embedded Quick Buy on your mobile website with Razorpay Custom Checkout and show customers their recommended payment instrument.

Available in
🇮🇳 India

Follow these steps to add [Embedded Quick Buy](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded.md) to your mobile website. The integration builds on [Razorpay Custom Checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/build-integration.md) and shows a customer's recommended saved card or UPI app on your product or cart page, before the full checkout opens.

> [!NOTE]
>
> **Already on Custom Checkout?**
>
> If you have already integrated Razorpay Custom Checkout on your mobile website, the only new step is [1.5 Fetch Recommended Instruments](#1-5-fetch-recommended-instruments). Make sure you also create customers ([step 1.2](#1-2-create-a-customer)), as Quick Buy needs them. All other steps stay the same.

**1.1** [Include razorpay.js in Your Webpage](#1-1-include-razorpay-js-in-your-webpage).

**1.2** [Create a Customer](#1-2-create-a-customer). Required for Quick Buy.

**1.3** [Create an Order in Server](#1-3-create-an-order-in-server).

**1.4** [Instantiate Custom Checkout](#1-4-instantiate-custom-checkout).

**1.5** [Fetch Recommended Instruments](#1-5-fetch-recommended-instruments). New for Quick Buy.

**1.6** [Submit Payment](#1-6-submit-payment).

**1.7** [Store Fields in Your Server](#1-7-store-fields-in-your-server).

**1.8** [Verify Payment Signature](#1-8-verify-payment-signature).

**1.9** [Verify Payment Status](#1-9-verify-payment-status).

## 1.1 Include razorpay.js in Your Webpage

Add the `razorpay.js` script to the `<head>` section of every page where the Quick Buy button appears:

```html HTML theme={null}
<script type="text/javascript" src="https://checkout.razorpay.com/v1/razorpay.js"></script>
```

> [!NOTE]
>
> **Handy Tips**
>
> Always load the script directly from `https://checkout.razorpay.com/v1/razorpay.js`. Do not host it yourself. This way your integration automatically receives the latest updates and bug fixes.

## 1.2 Create a Customer

Create a customer on your server with the [Customers API](https://razorpay.com/docs/api/customers/create.md). You can do this asynchronously, for example when the customer registers or starts checkout. Use the `customer_id` returned in the response to fetch recommended instruments in [step 1.5](#1-5-fetch-recommended-instruments).

```bash Request theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/customers \
-H "Content-Type: application/json" \
-d '{
  "name": "Gaurav Kumar",
  "contact": "9123456780",
  "email": "gaurav.kumar@example.com",
  "fail_existing": "0"
}'
```

```json Response theme={null}
{
  "id": "cust_1Aa00000000004",
  "entity": "customer",
  "name": "Gaurav Kumar",
  "email": "gaurav.kumar@example.com",
  "contact": "9123456780",
  "created_at": 1234567890
}
```

## 1.3 Create an Order in Server

Create an order on your server using the [Orders API](https://razorpay.com/docs/api/orders/create.md). Create the order before you fetch recommended instruments, so that all instrument types are eligible.

> [!WARNING]
>
> **Watch Out!**
>
> Create an order for every payment, server-side, using your API Key ID and secret. Payments made without an `order_id` cannot be captured and are automatically refunded.

```bash Request theme={null}
curl -X POST https://api.razorpay.com/v1/orders \
-u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-H 'content-type:application/json' \
-d '{
  "amount": 50000,
  "currency": "INR",
  "customer_id": "cust_1Aa00000000004",
  "receipt": "rcptid_11"
}'
```

```json Response theme={null}
{
  "id": "order_IluGWxBm9U8zJ8",
  "entity": "order",
  "amount": 50000,
  "amount_paid": 0,
  "amount_due": 50000,
  "currency": "INR",
  "receipt": "rcptid_11",
  "status": "created",
  "created_at": 1642662092
}
```

#### Request Parameters

`amount` *mandatory*
: `integer` Payment amount in the smallest currency sub-unit. For example, pass `50000` for ₹500.

`currency` *mandatory*
: `string` The 3-letter ISO currency code. For example, `INR`.

`customer_id` *mandatory*
: `string` The customer ID returned in [step 1.2](#1-2-create-a-customer).

`receipt` *optional*
: `string` Your receipt number for the order. Maximum 40 characters.

`notes` *optional*
: `object` Key-value pairs for additional information. Maximum 15 pairs of 256 characters each.

## 1.4 Instantiate Custom Checkout

Create a Razorpay instance with your API Key ID. Know more about [instantiating Custom Checkout](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/build-integration.md#1-3-2-instantiate-custom-checkout).

```javascript JavaScript theme={null}
var razorpay = new Razorpay({
  key: '<YOUR_KEY_ID>',
  image: 'https://your-domain.com/logo.png' // optional
});
```

## 1.5 Fetch Recommended Instruments

Call `Razorpay.getRecommendedInstruments()` to get the customer's recommended payment instruments. On mobile web, this is a JavaScript function in `razorpay.js`.

* The response contains up to 3 instruments, ranked by how likely the customer is to complete the payment. `items[0]` is the strongest recommendation.
* The response includes the logos you need to render the Quick Buy button.
* Pass the `order_id` from [step 1.3](#1-3-create-an-order-in-server). If you do not, the response is limited to UPI intent apps and `amount` and `currency` become mandatory.
* Pass the `customer_id`. If you do not have one, pass the customer's contact number in `customer.contact`.

```javascript JavaScript theme={null}
const options = {
  order_id: 'order_IluGWxBm9U8zJ8',  // recommended
  customer_id: 'cust_1Aa00000000004', // from step 1.2
  amount: 50000,                      // mandatory if no order_id
  currency: 'INR',                    // mandatory if no order_id
  customer: {
    contact: '9123456780'             // pass if no customer_id
  }
};

Razorpay.getRecommendedInstruments(options).then(response => {
  const items = response.get_recommended_instruments.items;

  items.forEach(item => {
    if (item.method === 'card') {
      console.log(item.card.last4);
    }
    if (item.method === 'upi') {
      console.log(item.upi.app);
      console.log(item.upi.app_logo);
    }
  });
});
```

> [!WARNING]
>
> **Watch Out!**
>
> * Always show a **Change payment method** option next to the Quick Buy button. It should open the full Razorpay Checkout, as in your current integration.
> * If the response has no instruments, or the call fails, show your regular checkout button instead of the Quick Buy button.
> * The browser cannot check whether a UPI app is installed. Show every UPI app returned. If an app is not installed, the device handles the failed deep link.

#### Sample Response

```json Response theme={null}
{
  "actions": ["get_recommended_instruments"],
  "get_recommended_instruments": {
    "entity": "collection",
    "count": 3,
    "items": [
      {
        "method": "card",
        "token": "token_Hf7vKlM2NpQrSt",
        "card": {
          "last4": "4242",
          "network": "Visa",
          "issuer": "HDFC",
          "type": "debit",
          "sub_type": "consumer",
          "international": false,
          "network_logo_url": "https://cdn.razorpay.com/app/visa.svg",
          "issuer_logo_url": "https://cdn.razorpay.com/app/hdfc.svg"
        }
      },
      {
        "method": "upi",
        "upi": {
          "flow": "intent",
          "app": "gpay",
          "app_logo": "https://cdn.razorpay.com/app/gpay.svg"
        }
      },
      {
        "method": "upi",
        "upi": {
          "flow": "intent",
          "app": "phonepe",
          "app_logo": "https://cdn.razorpay.com/app/phonepe.svg"
        }
      }
    ]
  }
}
```

#### Response Parameters

| Parameter | Type | Description | How to use it |
| - | - | - | - |
| `actions` | array | Always `get_recommended_instruments`. | Check that the response matches the action you called. |
| `count` | integer | Number of instruments in `items`. Maximum 3. | If `0`, skip Quick Buy and show your regular checkout. |
| `items` | array | Recommended instruments in order. Index 0 is the strongest recommendation. | Render the Quick Buy button from `items[0]`. |
| `items.method` | string | `card` or `upi`. | Decides which UI to render and which payment fields to send. |
| `token` | string | Razorpay token ID of the saved card. | Pass as `token` when you submit the payment. |
| `card.last4` | string | Last 4 digits of the card. For display only. | Render a masked label, such as **HDFC Debit ••••4242**. Never pass it to payment APIs. |
| `card.network` | string | Card network. For example, `Visa`, `MasterCard`, `RuPay` or `Amex`. | Show the network name on the button. |
| `card.issuer` | string | 4-character issuer code. For example, `HDFC`, `ICIC` or `SBIN`. | Show the issuer name on the button. |
| `card.type` | string | `credit`, `debit` or `prepaid`. | Show the card type on the button. |
| `card.network_logo_url` | string | CDN-hosted card network logo. | Use directly in an `<img>` tag. |
| `card.issuer_logo_url` | string | CDN-hosted issuing bank logo. | Use directly in an `<img>` tag. |
| `upi.flow` | string | Always `intent`. | Confirms the UPI flow. |
| `upi.app` | string | Short name of the UPI app. For example, `gpay`, `phonepe` or `paytm`. Returned on mobile web. | Pass as `upi_app` when you submit the payment. |
| `upi.app_logo` | string | CDN-hosted UPI app logo. | Use directly in an `<img>` tag on the button. |

## 1.6 Submit Payment

When the customer taps the Quick Buy button, call `razorpay.createPayment()` inside the click event listener. Pass the fields for the recommended instrument's method, for example the saved card `token` or the UPI app. Use the same `createPayment()` payloads as your existing Custom Checkout integration. Know more about [submitting payment details](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/build-integration.md#1-3-3-submit-payment-details).

## 1.7 Store Fields in Your Server

A successful payment returns `razorpay_payment_id`, `razorpay_order_id` and `razorpay_signature`. Store these on your server. Know more about [storing fields in your server](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/build-integration.md#1-4-store-fields-in-your-server).

## 1.8 Verify Payment Signature

Verify the signature on your server to confirm the payment is authentic. This step is mandatory. Know more about [verifying the payment signature](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/build-integration.md#1-5-verify-payment-signature).

## 1.9 Verify Payment Status

Confirm that the payment status is `captured`. You can track it in 3 ways:

* **Dashboard**: Log in to the Dashboard and go to **Transactions** → **Payments**. A successful payment has a payment ID and the status **Captured**.
* **Webhooks**: Subscribe to [payment webhook events](https://razorpay.com/docs/webhooks/payments.md) for real-time updates.
* **API**: Poll the [Fetch a Payment API](https://razorpay.com/docs/api/payments/fetch-with-id.md) with the `razorpay_payment_id`.

Know more about [verifying the payment status](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/build-integration.md#1-6-verify-payment-status).

> [!NOTE]
>
> **Handy Tips**
>
> Use [Payment Capture Settings](https://razorpay.com/docs/payments/payments/capture-settings.md) to capture payments automatically.

## Next Steps

* [Test your integration](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/test-integration.md) in Test Mode.
* Set up the full checkout as the fallback for customers who tap **Change payment method**.
* Replace your test API keys with live keys when you are ready to go live.

## Related Information

* [Embedded Quick Buy](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded.md)
* [Embedded Quick Buy FAQs](https://razorpay.com/docs/payments/payment-gateway/features/quickbuy/embedded/faqs.md)
* [Custom Checkout Integration](https://razorpay.com/docs/payments/payment-gateway/web-integration/custom/build-integration.md)
