> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Pay Later

> Offer Pay Later (Buy Now, Pay Later) payment method at Razorpay Checkout. Check providers and payment flow.

Available in
🇮🇳 India
🇸🇬 Singapore

Accept payments from your customers in Singapore using **Atome**, a leading Buy Now, Pay Later (BNPL) provider across Southeast Asia. Atome allows shoppers to split purchases into 3 interest-free installments while you receive full settlement upfront.

> [!NOTE]
>
> **Handy Tips**
>
> * Atome in Singapore is processed via Airwallex as the payment aggregator.
> * Passing product details (`line_items`) and a shipping address in your Orders API request is strongly recommended for optimal success rates.
> * Maximum transaction limit: **SGD 3,000**.

## How it Works

Based on the concept [Buy Now, Pay Later](https://en.wikipedia.org/wiki/Buy_now,_pay_later):

1. The customers get a running line of credit by registering with any providers.
2. When customers buy goods or services on your website or apps, no money is debited from their accounts.
3. You receive the payments from their providers.
4. The customer pays back to the provider as per the fixed schedule defined by the provider.

**At Razorpay Checkout:**

1. At the Checkout, customers enter their contact details and select **Pay Later** as the payment method.
2. Customers select **Atome** from the list of providers.
3. Customers are redirected to the Atome authentication page, where they log in to their Atome account and approve the 3-installment plan.
4. Customers are redirected back to the business's website after successful authentication.
5. Payment is confirmed via a webhook notification from Razorpay.

## Supported Pay Later Providers

| **Provider name** | **Provider Code** |
| - | - |
| Atome | `atome` |

### Supported Region and Currency

| Region | Currency |
| - | - |
| Singapore | SGD |

### Transaction Limits

| Minimum Transaction Amount | Maximum Transaction Amount |
| - | - |
| SGD 0.01 | SGD 3,000 |

### Create an Order

No additional client-side integration is required to display Atome on your Standard Checkout. Before opening the Checkout, create an order using the [Orders API](https://razorpay.com/docs/sg/api/orders/create.md). For Atome in Singapore, pass `line_items` (product details) and `customer_details.shipping_address` in the order payload for optimal success rates.

> [!WARNING]
>
> **Watch Out!**
>
> Passing real product details (`line_items`) and a shipping address is strongly recommended for Atome transactions in Singapore. If `line_items` are not provided, a generic item will be used as a fallback. If a shipping address is not provided, a default address will be sent. Both fallbacks may reduce approval rates.

```bash Sample Request theme={null}
curl -X POST https://api.razorpay.com/v1/orders \
-U [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-H 'content-type:application/json' \
-d '{
  "amount": 50000,
  "currency": "SGD",
  "receipt": "receipt#1111",
  "customer_details": {
    "name": "John Doe",
    "contact": "+6580001500",
    "email": "john@example.com",
    "shipping_address": {
      "line1": "16 Sandilands Road",
      "line2": "#05-01",
      "city": "Singapore",
      "country": "SGP",
      "state": "Singapore",
      "zipcode": "546080"
    }
  },
  "line_items": [
    {
      "name": "iPhone 15 Pro",
      "quantity": 1,
      "price": 50000
    }
  ]
}'
```
