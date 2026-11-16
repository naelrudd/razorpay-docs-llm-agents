> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Delete an Offer Linked to a Subscription

> Remove an Offer from a Subscrition using Dashboard or APIs.

Available in
🇮🇳 India

You can delete an Offer linked to a Subscription from the [Dashboard](https://razorpay.com/docs/payments/subscriptions/offers/delete.md#delete-an-offer-linked-to-a-subscription-from-dashboard) or using [APIs](https://razorpay.com/docs/payments/subscriptions/offers/delete.md#delete-an-offer-linked-to-a-subscription-using-apis). The invoices generated after the offer is deleted will be charged in full.

## Delete an Offer Linked to a Subscription From Dashboard

Watch this video to see how to delete an offer linked to a Subscription from the Dashboard.

[https://www.youtube-nocookie.com/embed/xdPZ3xpVDRQ](https://www.youtube-nocookie.com/embed/xdPZ3xpVDRQ)

To delete an Offer linked to a Subscription:

1. Log in to the Dashboard and click **Subscriptions** under **PAYMENT PRODUCTS** in the left menu.
2. Click on the **Subscription Id** for which you want to update the offer.
3. Click **Remove** against Offer.

> [!WARNING]
>
> **Watch Out!**
>
> The offer will be removed from the Subscription only at the end of the cycle. It is not possible to remove an offer linked to a Subscription immediately.

1. Click **Yes, Remove**.

## Delete an Offer Linked to a Subscription Using APIs

Use the [Delete an offer Linked to a Subscription API](https://razorpay.com/docs/api/payments/subscriptions/delete-offer.md).

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:YOUR_KEY_SECRET] \
-X DELETE https://api.razorpay.com/v1/subscriptions/sub_00000000000001/offer_JHD834hjbxzhd38d \
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String subscriptionId = "sub_00000000000001";

String offerId = "offer_JHD834hjbxzhd38d";

Subscription subscription = razorpay.subscription.deleteSubscriptionOffer(subscriptionId, offerId);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->subscription->fetch($subscriptionId)->deleteOffer($offerId)
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.subscriptions.deleteOffer(subscriptionId, offerId)
```

```python Python theme={null}
import razorpay
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.subscription.delete_offer(subscriptionId, offerId)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

subscriptionId = "sub_00000000000001"

offerId = "offer_JHD834hjbxzhd38d"
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Subscription.DeleteOffer("<subscriptionId>", "<offerId>", nil, nil)
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string subscriptionId = "sub_I3GGEs7Xgmnozy";

string offerId = "offer_JCTD1XMlUmzF6Z";

Subscription subscription = client.Subscription.Fetch(subscriptionId).DeleteOffer(offerId);
```

```bash CLI theme={null}
razorpay subscriptions delete-offer sub_ABC123 offer_ABC123
```

### Related Information

* [About Offers](https://razorpay.com/docs/payments/subscriptions/offers.md)
* [Create Subscription Offers](https://razorpay.com/docs/payments/subscriptions/offers/create.md)
* [Link an Offer to a Subscription](https://razorpay.com/docs/payments/subscriptions/offers/link.md)
* [Update an Offer Linked to a Subscription](https://razorpay.com/docs/payments/subscriptions/offers/update.md)
