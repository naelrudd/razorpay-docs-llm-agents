> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integrate With Subscriptions

> Step-by-step guide on how to integrate Razorpay Subscriptions.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Check the prerequisites and steps to integrate Razorpay Subscriptions:

## Prerequisites

* Create a Razorpay account.
* Log in to the Dashboard and [generate the API keys](https://razorpay.com/docs/us/api/authentication.md#generate-api-keys). You need to use these keys while using our APIs and Checkout.

## Integration Steps

Follow these steps to integrate Razorpay Subscriptions:

> [card] [1. Build Integration](https://razorpay.com/docs/us/payments/subscriptions/integration-guide.md#1-build-integration)
>
> Create Plan, Subscription and integrate with Standard Checkout.

> [card] [2. Test Integration](https://razorpay.com/docs/us/payments/subscriptions/integration-guide.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-live Checklist](https://razorpay.com/docs/us/payments/subscriptions/integration-guide.md#3-follow-go-live-checklist)
>
> Check the go-live checklist.

### 1. Build Integration

Follow these steps to create plans, subscriptions and accept payments from customers.

> [accordion] Step 1.1 Create a Plan
>
> A Plan is a foundation on which a Subscription is built. It acts as a reusable template and contains details of the goods or services offered with the amount to be charged and the frequency at which the customer should be charged (billing cycle). Depending on your business, you can create multiple Plans with different billing cycles and pricing.
>
> * Create a Plan before creating a Subscription using your checkout.
> * Create Plans from the [Dashboard](https://razorpay.com/docs/us/payments/subscriptions/create-plans.md#create-a-plan) or using [APIs](https://razorpay.com/docs/us/api/payments/subscriptions/create-plan.md).

> [accordion] Step 1.2 Create a Subscription
>
> A Subscription contains details like the Plan, the start date, total number of billing cycles, free [trial period](https://razorpay.com/docs/us/payments/subscriptions/create.md#trial-period) (if any) and [upfront amount](https://razorpay.com/docs/us/payments/subscriptions/create.md#upfront-amount) to be collected.
>
> Subscriptions can be created from the [Dashboard](https://razorpay.com/docs/us/payments/subscriptions/create-subscription-links.md#create-a-subscription-link-from-dashboard) or using [APIs](https://razorpay.com/docs/us/api/payments/subscriptions/create-subscription.md).

> [accordion] Step 1.3 Integrate With Standard Checkout
>
> After you create a Subscription, you need the customer's permission to charge their card at periodic intervals. For this, the customer has to complete an authentication/authorisation transaction.
>
> #### Authentication Transaction
>
> You can collect the authorisation transaction by passing the subscription\_id along with the other options to the Razorpay Standard Checkout.
>
> Once the authorisation transaction is successful, Razorpay returns the `razorpay_payment_id`, `razorpay_subscription_id` and the `razorpay_signature`.
>
> > [accordion] Code to Add Pay Button
> >
> > Use the sample code to initiate Razorpay Standard Checkout. Check the [list of checkout parameters](https://razorpay.com/docs/us/payments/payment-gateway/web-integration/standard/integration-steps.md#2-3-checkout-options).
> >
> > ```javascript Checkout with Callback URL theme={null}
> > 					<button id = "rzp-button1">Pay</button>
> > 							<script src = "https://checkout.razorpay.com/v1/checkout.js"></script>
> > 							<script>
> > 								var options = {
> > 									"key": "key_id",
> > 									"subscription_id": "sub_00000000000001",
> > 									"name": "Acme Corp.",
> > 									"description": "Monthly Test Plan",
> > 									"image": "/your_logo.jpg",
> > 									"callback_url": "https://eneqd3r9zrjok.x.pipedream.net/",
> > 									"prefill": {
> > 										"name": "<name>",
> > 										"email": "<email>",
> > 										"contact": "<phone>"
> > 									},
> > 									"notes": {
> > 										"note_key_1": "Tea. Earl Grey. Hot",
> > 										"note_key_2": "Make it so."
> > 									},
> > 									"theme": {
> > 										"color": "#F37254"
> > 									}
> > 								};
> > 								var rzp1 = new Razorpay(options);
> > 								document.getElementById('rzp-button1').onclick = function(e) {
> > 									rzp1.open();
> > 									e.preventDefault();
> > 								}
> > 								</script>		
> > ```
> >
> > ```javascript Checkout with Handler function theme={null}
> > 					<button id = "rzp-button1">Pay</button>
> > 							<script src = "https://checkout.razorpay.com/v1/checkout.js"></script>
> > 							<script>
> > 								var options = {
> > 									"key": "key_id",
> > 									"subscription_id": "sub_00000000000001",
> > 									"name": "Acme Corp.",
> > 									"description": "Monthly Test Plan",
> > 									"image": "/your_logo.jpg",
> > 									"handler": function(response) {
> > 										alert(response.razorpay_payment_id),
> > 										alert(response.razorpay_subscription_id),
> > 										alert(response.razorpay_signature);
> > 									},
> > 									"prefill": {
> > 										"name": "<name>",
> > 										"email": "<email>",
> > 										"contact": "<phone>"
> > 									},
> > 									"notes": {
> > 										"note_key_1": "Tea. Earl Grey. Hot",
> > 										"note_key_2": "Make it so."
> > 									},
> > 									"theme": {
> > 										"color": "#F37254"
> > 									}
> > 								};
> > 							var rzp1 = new Razorpay(options);
> > 							document.getElementById('rzp-button1').onclick = function(e) {
> > 								rzp1.open();
> > 								e.preventDefault();
> > 							}
> > 							</script>	
> > ```
> >
> > ```json Failure response theme={null}
> > 							{
> > 							"code": "BAD_REQUEST_ERROR",
> > 							"description": "Payment failed. Please contact the site admin",
> > 							"source": "business",
> > 							"step": "payment_initiation",
> > 							"reason": "amount_less_than_minimum_amount",
> > 							"metadata":{
> > 									},
> > 							"field": "amount"
> > 								}
> > ```
>
> > [accordion] Failure Reasons and Next Steps
> >
> > | Error | Cause | Solution |
> > | - | - | - |
> > | Customer payment is not allowed for the Subscription at this stage. | This error occurs when you are trying to make a payment for the next billing cycle during the current cycle. | Users cannot pay for the next billing cycle during the current cycle. |
> > | `end_time` must be between `946684800` and `4765046400`. | This error occurs when the end date of the Subscription is beyond the acceptable limits or if the current start and end are null. | Currently, you can only charge a Subscription for up to 10 years. |
>
> > [accordion] Payment Verification
> >
> > This is a mandatory step that allows you to confirm the authenticity of the card details returned to the Checkout form for successful payments.
> >
> > To verify the `razorpay_signature` returned to you by the Checkout form:
> >
> > 1. Create a signature in your server using the following attributes:
> >
> > | Parameter | Description |
> > | - | - |
> > | `subscription_id` | Retrieve the subscription\_id from your server. Do not use the razorpay\_subscription\_id returned by Checkout. |
> > | `razorpay_payment_id` | Returned by Checkout. |
> > | `key_secret` | Available in your server. The key\_secret that was generated from the Dashboard. |
> >
> > 2. Use the SHA256 algorithm, the `razorpay_payment_id` and the `subscription_id` to construct an HMAC hex digest as shown below:
> >
> > ```html Code theme={null}
> > 										generated_signature = hmac_sha256(razorpay_payment_id + "|" + subscription_id, secret);
> >
> > 										if (generated_signature == razorpay_signature) {
> > 										payment is successful
> > 										}
> > ```
> >
> > 3. If the signature you generate on your server matches the `razorpay_signature` returned to you by the Checkout form, the payment received is from an authentic source.

### 2. Test Integration

You can test the integration by making a test payment using our cards:

| Card Network | Card Number | CVV & Expiry Date |
| - | - | - |
| Visa | 4384 7968 2770 3274 | Use a random CVV and any future date ^^^^ |
| Mastercard | 5312 6865 5677 9641 | |
| Amex | 3782 8224 6310 005 | |
| Diners | 6594 7300 0000 0001 | |

### 3. Follow Go-live Checklist

Consider the following steps before taking your integration live.

> [accordion] Switch Test API Keys With Live API Keys
>
> After confirming if your integration is working successfully, you can take the integration live by switching the Test Mode API Keys with the Live Mode Keys.

> [accordion] Subscribe to Webhooks
>
> [Set up Razorpay Webhooks](https://razorpay.com/docs/us/webhooks/setup-edit-payments.md) to configure and receive notifications when a specific event occurs. When one of these events is triggered, we send an HTTP POST payload in JSON to the webhook's configured URL. Subscribe to these [Subscriptions webhook events](https://razorpay.com/docs/us/payments/subscriptions/subscribe-to-webhooks.md#webhook-events-and-descriptions).

## Best Practices

Follow the best practices for a smooth Subscriptions integration.

* [Verify Payments](https://razorpay.com/docs/us/payments/subscriptions/integration-guide.md#payment-verification): Verify the received payments to confirm the authenticity of the mandate details returned to the Checkout form for successful payments.
* [Implement Webhooks](https://razorpay.com/docs/us/payments/subscriptions/integration-guide.md#subscribe-to-webhooks): Implement Razorpay Webhooks to receive notifications on various events of Subscriptions.

### Related Information

* [Subscriptions API](https://razorpay.com/docs/us/api/payments/subscriptions)
* [Razorpay Standard Checkout](https://razorpay.com/docs/us/payments/payment-gateway/web-integration/standard.md)
