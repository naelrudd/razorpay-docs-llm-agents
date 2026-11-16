> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Link an Offer to a Subscription

> Link an Offer to a Subscription on the Razorpay Dashboard.

Available in
🇮🇳 India

After creating an Offer and a Subscription Plan, you need to link the Offer to a Subscription.

* [Link an Offer while creating a Subscription](#link-an-offer-while-creating-a-subscription)
* [Link an Offer to an active Subscription](#link-an-offer-to-an-existing-subscription)

You can also [delete an Offer linked to a Subscription](https://razorpay.com/docs/payments/subscriptions/offers/delete.md).

## Link an Offer While Creating a Subscription

Watch this video to see how to link an Offer to a Subscription.

[https://www.youtube.com/embed/SoGr8jsfp24](https://www.youtube.com/embed/SoGr8jsfp24)

You can link an Offer while creating a Subscription from the [Dashboard](https://razorpay.com/docs/payments/subscriptions/offers/link.md#link-an-offer-while-creating-a-subscription-from-dashboard) or using [APIs](https://razorpay.com/docs/payments/subscriptions/offers/link.md#link-an-offer-while-creating-a-subscription-using-apis).

> [!WARNING]
>
> **Watch Out!**
>
> Offers for Subscriptions are only available when using Razorpay Standard Checkout.

### Link an Offer While Creating a Subscription From Dashboard

You can link an Offer to a Subscription by selecting the required Offer using the **Offer** drop-down list when creating the Subscription.

![link offer when creating a subscription](https://razorpay.com/docs/build/browser/assets/images/subscriptions-offers-link_offer_when_creating_subscription.jpg)

Know more about [Subscription Links](https://razorpay.com/docs/payments/subscriptions/create-subscription-links.md).

### Link an Offer While Creating a Subscription Using APIs

Use the [Link an Offer to a Subscription API](https://razorpay.com/docs/api/payments/subscriptions/link-offer.md).

## Link an Offer to an Existing Subscription

You can link an Offer to a Subscription or update the Offer linked to a Subscription from the [Dashboard](https://razorpay.com/docs/payments/subscriptions/offers/link.md#link-an-offer-to-an-existing-subscription-from-dashboard) or using [API](https://razorpay.com/docs/payments/subscriptions/offers/link.md#link-an-offer-to-an-existing-subscription-using-apis).

* This is possible only if the Subscription is in the `active` state and not in any other state.
* The Offer is applied to the Subscription at the end of the current billing cycle. It is not possible to update an Offer linked to a Subscription immediately.

### Link an Offer to an Existing Subscription From Dashboard

You can link an Offer to an existing active Subscription by selecting the required Offer using the **Offer** drop-down when updating the Subscription.

![link an offer to an existing active subscription](https://razorpay.com/docs/build/browser/assets/images/subscriptions-offers-link_offer_to_existing_subscription.jpg)

Know more about [updating a Subscription](https://razorpay.com/docs/payments/subscriptions/update.md).

### Link an Offer to an Existing Subscription Using APIs

Use the [Update a Subscription API](https://razorpay.com/docs/api/payments/subscriptions/update-subscription.md) to link an Offer to an existing active Subscription by passing the `offer_id: <offer_id>` in the request body.

### Related Information

* [About Offers](https://razorpay.com/docs/payments/subscriptions/offers.md)
* [Create Subscription Offers](https://razorpay.com/docs/payments/subscriptions/offers/create.md)
* [Update an Offer Linked to a Subscription](https://razorpay.com/docs/payments/subscriptions/offers/update.md)
* [Delete an Offer Linked to a Subscription](https://razorpay.com/docs/payments/subscriptions/offers/delete.md)
