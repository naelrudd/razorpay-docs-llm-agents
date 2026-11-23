> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# India Billing API - Integration Guide for Stripe Merchants

> Integrate Razorpay India Billing API with your existing Stripe billing to execute payments for Indian customers using UPI Autopay, card mandates and smart retries.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Keep Stripe as your billing system. Let Razorpay execute payments in India.

The India Billing API lets you continue using Stripe for billing, subscriptions and usage metering. For Indian customers, Razorpay handles payment execution, including UPI Autopay, card mandates, Pre-Debit Notifications (PDN) and RBI compliance, without changing your existing Stripe workflows.

This integration is proven with Replit, which uses Stripe for billing, subscriptions and usage metering. For Indian users, payment execution routes through Razorpay with zero changes to their Stripe workflows.

## How It Works

Stripe decides when and how much to charge. Razorpay executes those charges in India, compliantly, with UPI Autopay, smart retries and pre-debit notifications.

Your existing Stripe billing, invoicing and reconciliation workflows remain untouched. For Indian customers, Razorpay handles coupon validation (coupon creation remains at Stripe), mandate creation, PDN delivery, payment execution and status reporting back to Stripe. Razorpay also calculates and adds 18% GST on the amount debited from Indian customers. See [Charges, Taxes and Limits](#charges-taxes-and-limits).

## What Changes vs. What Stays the Same

| Stays the Same (Stripe) | New (Razorpay Handles) |
| - | - |
| Billing logic, pricing, plans | UPI Autopay and card mandate creation |
| Subscription lifecycle management | RBI-compliant Pre-Debit Notifications |
| Invoice creation and reconciliation | Payment execution and smart retries |
| Your billing/invoicing taxes | 18% India GST added on the debited amount |
| Usage metering (Orb/Metronome) | Mandate limit handling and FX conversion (USD → INR → USD) |
| Webhooks your app listens to | Payment status reporting back to Stripe |

## Prerequisites

* Share your Stripe API key with Razorpay.
* Create custom payment methods (`Razorpay_UPI` and `Razorpay_Card`) in Stripe.
* Create a plan mapping between your Stripe plans and Razorpay.
* For usage-based billing, configure your webhook endpoint to forward Stripe's `invoice.payment_attempt_required` events to Razorpay's `/v1/cb/stripe/webhook`. Your server is the intermediary: Stripe sends the event to your endpoint and you forward it to Razorpay. This is not required for scheduled subscription renewals.

## Integration Flows

The India Billing API supports three flows. No billing rebuild is required.

1. [Mandate Setup](#flow-1-mandate-setup)
2. [Subscription Payments](#flow-2-subscription-payments)
3. [Usage-Based Billing](#flow-3-usage-based-billing)

Additionally, you can accept [one-time credit pack payments](#one-time-credit-pack-payments) using the standard Razorpay Orders flow.

## Flow 1: Mandate Setup

This is a one-time flow for each customer. When a customer selects a plan on your pricing page, Razorpay opens its checkout, collects customer details and allows the customer to apply coupons.

1. Customer selects a plan on your pricing page.
2. Your server calls the [Create Checkout Session API](#create-checkout-session) to create a Razorpay checkout session.
3. Your frontend invokes Razorpay Custom JS with the `checkout_session_id`. The Custom JS renders the pricing breakdown (including GST), lets the customer validate coupons and creates the subscription on authorisation.
4. Customer authorises the payment. Razorpay creates the mandate and reports the payment outcome back to Stripe.
5. Stripe marks the invoice as paid and the subscription as active.
6. Your app provisions access via existing Stripe webhooks.

> [!NOTE]
>
> **Handy Tips**
>
> The checkout session is consumed by Razorpay Custom JS on your frontend. Custom JS exposes helpers to fetch the pricing and GST breakdown, validate coupons and create the subscription. Contact your Razorpay account manager for the Custom JS integration snippet.

### Create Checkout Session

Use this API to create a checkout session for mandate setup.

`POST /v1/cb-checkout/session>`

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/cb-checkout/session \
-H "Content-Type: application/json" \
-d '{
  "mode": "subscription",
  "purpose": "create",
  "customer_id": "<stripe_customer_id>",
  "amount": 50000,
  "currency": "USD",
  "items": [
    {
      "price_id": "<stripe_price_id>",
      "quantity": 1
    }
  ],
  "method_id": "<RAZORPAY_CPMT_ID>",
  "promocode_id": "<optional_promo_code>",
  "metadata": {
    "user_id": "<user_id_string>"
  }
}'

```

```json Response theme={null}
{
  "checkout_session_id": "rzp_ckout_...",
  "expiry": 1735689600,
  "expires_in": 1800
}
```

> [accordion] Request Parameters
>
> `mode` *mandatory*
> : `string` The checkout mode. Set this to `subscription` for mandate setup.
>
> `purpose` *mandatory*
> : `string` The purpose of the checkout session. Possible values:
>
> * `create`: Set up a new subscription and mandate.
> * `upgrade`: Change the plan for an existing subscription.
> * `migrate`: Move an existing Stripe-card customer to a Razorpay mandate.
>
> See [Checkout Purposes](#checkout-purposes).
>
> `customer_id` *mandatory*
> : `string` The Stripe customer ID. For example, `cus_abc123`.
>
> `amount` *mandatory*
> : `integer` The amount in the smallest currency unit. For example, for \$500.00, pass `50000`.
>
> `currency` *mandatory*
> : `string` The currency code. For example, `USD`.
>
> `items` *mandatory*
> : `array` An array of line items for the checkout session. Each item contains:
>
> `price_id` *mandatory*
> : `string` The Stripe price id.
>
> `quantity` *mandatory*
> : `integer` The quantity for the line item.
>
> `method_id` *mandatory*
> : `string` The Razorpay custom payment method ID (`RAZORPAY_CPMT_ID`). This identifies the payment method type (UPI or card) created in Stripe during one-time setup.
>
> `promocode_id` *optional*
> : `string` The promotional code to apply to the checkout session. Coupon creation happens at Stripe. Razorpay validates and applies the coupon at checkout.
>
> `metadata` *optional*
> : `object` Additional custom metadata for the session. For example:
>
> `user_id`
> : `string` Your internal user identifier.

> [accordion] Response Parameters
>
> `checkout_session_id`
> : `string` The unique identifier for the checkout session. Use this to invoke Razorpay Custom JS on your frontend.
>
> `expiry`
> : `integer` The Unix timestamp at which the checkout session expires.
>
> `expires_in`
> : `integer` The time in seconds until the checkout session expires. The session is valid for 30 minutes (`1800` seconds).

### Checkout Purposes

The `purpose` field in the [Create Checkout Session API](#create-checkout-session) determines the intent of the session.

| Purpose | Description |
| - | - |
| `create` | Sets up a new subscription and mandate for a customer who does not yet have one. |
| `upgrade` | Changes the plan for an existing subscription. Any difference in amount (delta) is handled as a credit or refund. |
| `migrate` | Moves an existing customer paying by Stripe card onto a Razorpay mandate, without interrupting their subscription. |

> [!NOTE]
>
> **Handy Tips**
>
> The full request payload for `upgrade` and `migrate` (including plan-change and migration parameters) is shared during onboarding. Contact your Razorpay account manager to enable these flows.

## Flow 2: Subscription Payments

Subscription payments are fully automated. After the mandate is set up, Razorpay handles scheduled renewals end-to-end with no frontend involvement and no webhook forwarding from you. The entire flow is driven by Razorpay.

1. A Razorpay cron job identifies subscriptions with an upcoming billing date.
2. Razorpay sends a Pre-Debit Notification (PDN) to the customer around 48 hours before the billing date.
3. On the billing date, Razorpay auto-debits the customer via the stored mandate. Razorpay automatically retries failed debits in line with RBI norms.
4. Razorpay reports the payment outcome to Stripe. Stripe updates the invoice (paid/failed).
5. Your app reacts via existing Stripe webhooks.

> [!NOTE]
>
> **Handy Tips**
>
> Scheduled renewals do **not** require you to forward any Stripe webhook to Razorpay. Razorpay's cron job initiates the PDN and the debit based on the upcoming billing date. Webhook forwarding is only needed for [usage-based billing](#flow-3-usage-based-billing).

## Flow 3: Usage-Based Billing

Usage-based billing is a coupled, single-step model. When your metering system (Orb, Metronome or custom) creates a usage-based invoice on Stripe, Stripe fires an `invoice.payment_attempt_required` event that you forward to Razorpay. Razorpay charges the customer immediately, with no pre-debit notification.

1. Your metering system monitors usage and creates an invoice in Stripe when the threshold is reached (recommended within \$150).
2. Stripe fires `invoice.payment_attempt_required` to your webhook endpoint.
3. Your server forwards the event to Razorpay using the [Stripe Webhook Forwarding API](#stripe-webhook-forwarding).
4. Razorpay immediately debits the customer using the existing mandate. There is no PDN — the Stripe invoice triggers an immediate charge.
5. Razorpay reports the outcome back to Stripe.
6. Your billing system sees the Stripe invoice as paid. No India-specific logic is needed on your end.

> [!NOTE]
>
> **Handy Tips**
>
> `invoice.payment_attempt_required` is a custom invoice event used to signal that an immediate charge is required. It is not part of the standard Stripe SDK event types, so your webhook handler must handle it explicitly before your exhaustive `switch` on `event.type` (for example, with a string comparison such as `(event.type as string) === "invoice.payment_attempt_required"` in TypeScript).

### Stripe Webhook Forwarding

Use this API to forward Stripe usage-based billing events to Razorpay.

`POST /v1/cb/stripe/webhook>`

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/cb/stripe/webhook \
-H "Content-Type: application/json" \
-d '{
  "provider": "stripe",
  "data": "<full_stripe_webhook_event_object>"
}'
```

> [accordion] Request Parameters
>
> `provider` *mandatory*
> : `string` The billing provider. Set this to `stripe`.
>
> `data` *mandatory*
> : `object` The full Stripe webhook event object, forwarded as-is.

> [!WARNING]
>
> **Watch Out!**
>
> Forward an event to Razorpay only if it relates to a Razorpay-managed subscription. Determine this from your own records (for example, whether you created the subscription through Razorpay) and fall back to the subscription metadata. Do not forward events for subscriptions billed entirely through Stripe.

## One-Time Credit Pack Payments

For one-time payments such as credit packs, use the standard Razorpay Orders flow instead of the checkout session flow. This involves creating a customer, creating an order, verifying the payment signature, fetching the payment and capturing it.

### Step 1: Create a Customer

Create a customer with basic details such as name.

`POST /v1/customers>`

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/customers \
-H "Content-Type: application/json" \
-d '{
  "name": "<name>"
}'

```

```json Response theme={null}
{
  "id": "cust_1Aa00000000004"
}
```

> [accordion] Request Parameters
>
> `name` *mandatory*
> : `string` The customer name.

> [accordion] Response Parameters
>
> `id`
> : `string` The unique identifier for the customer. For example, `cust_1Aa00000000004`. Use this as the `customer_id` when creating an order.

### Step 2: Create an Order

After a customer is created, an order needs to be generated using the Orders API. This order contains details such as the payment amount, currency, customer details. After the order is created, an `order_id` is generated, for example, `order_NGrgEcmYJsfUyl`. Learn more about [Order and Payment states](https://razorpay.com/docs/my/payments/orders#order-states).

`POST /v1/orders>`

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/orders \
-H "Content-Type: application/json" \
-d '{
  "amount": 10000,
  "currency": "USD",
  "customer_id": "cust_1Aa00000000004",
  "customer_details": {
    "name": "<name>",
    "email": "<email>",
    "contact": "<phone>",
    "shipping_address": {
      "line1": "Mantri apartment",
      "city": "Bengaluru",
      "country": "IND",
      "state": "Karnataka",
      "zipcode": "560032"
    }
  },
  "payment": {
    "capture": "manual",
    "capture_options": {
      "manual_expiry_period": 7200
    }
  }
}'
```

```json Response theme={null}
{
  "id": "order_RB58MiP5SPFYyM",
  "amount": 10000,
  "currency": "USD"
}
```

> [accordion] Request Parameters
>
> `amount` *mandatory*
> : `integer` The payment amount in the smallest currency unit. For example, for \$100.00, pass `10000`.
>
> `currency` *mandatory*
> : `string` The ISO currency code. For example, `USD`.
>
> `customer_details` *mandatory*
> : `object` This contains details about the customer details of the order.
>
> `name` *mandatory*
> : `string` Customer's name.
>
> * Character length: Between 5 and 50 characters.
> * Allowed characters: Uppercase letters (A-Z), lowercase letters (a-z), and spaces (not at the beginning).
> * Not allowed characters: Numbers, special characters (e.g., @, ", ,, ., etc.), Unicode characters, emojis, and non-Latin scripts or regional languages.
> * Prohibited names: Names must be meaningful and contextually appropriate.
>   * Avoid using repetitive patterns (e.g., aaa, xyz, kkk kk).
>   * Names like litri litri, Hfg Gh, or husi husi are not permitted.
>   * Curse words and offensive names are prohibited.
> * Example: `Gaurav Kumar`.
>
> `email` *optional*
> : `string` The customer's email address. A maximum length of 64 characters for the username. For example, in "[gaurav.kumar@example.com](mailto:gaurav.kumar@example.com)", "gaurav.kumar" must not exceed 64 characters.
>
> `contact` *optional*
> : `string` The customer's phone number. A maximum length of 15 characters including country code. For example, `+919123456780`.
>
> `shipping_address` *mandatory*
> : `object` This contains the shipping address of the order.
>
> `line1` *mandatory*
> : `string` Address Line 1 of the address.
>
> * Character length: Must be between 3 and 100 characters.
> * Allowed characters: Uppercase letters (A-Z), lowercase letters (a-z), numbers (0-9), spaces, and special characters (\*&/-()#\_+{}\[]:'".,.).
> * Not allowed characters: Regional languages.
>
> `city` *mandatory*
> : `string` Name of the city. Must be between 3 and 50 characters in length and can only include uppercase (A-Z) and lowercase (a-z) English letters, and spaces.
>
> `country` *mandatory*
> : `string` ISO3 country code of the billing address. Only `IND` is allowed.
>
> `state` *mandatory*
> : `string` Name of the state. It must be between 3 and 50 characters extended and can only include uppercase (A-Z) and lowercase (a-z) English letters and spaces. Please send the full name of the state, for example, Madhya Pradesh.
>
> `zipcode` *mandatory*
> : `string` The ZIP code must consist of 6-digit numeric characters. Only valid Indian ZIP codes will be accepted. Refer to the [list of supported ZIP codes](https://razorpay.com/docs/build/browser/assets/images/IN_zipcodes.xlsx).
>
> `payment` *mandatory*
> : `object` Payment capture configuration.
>
> `capture` *mandatory*
> : `string` Set to `manual` for manual capture.
>
> `capture_options` *mandatory*
> : `object` Contains `manual_expiry_period`.
>
> `manual_expiry_period` *mandatory*
> : `integer` the time in seconds before the authorisation expires. For example, `7200` for 2 hours.

> [accordion] Response Parameters
>
> `id`
> : `string` The unique identifier for the order. For example, `order_RB58MiP5SPFYyM`.
>
> `amount`
> : `integer` The order amount in the smallest currency unit.
>
> `currency`
> : `string` The ISO currency code.

### Step 3: Verify Payment Signature

Signature verification is a mandatory step to ensure that the callback is sent by Razorpay. The `razorpay_signature` contained in the callback can be regenerated by your system and verified as follows.

Create a string for hashing by combining the "razorpay\_payment\_id" from the callback and the Order ID generated in the initial step, separated by a `|`. Proceed to hash this string using SHA256 alongside your API Secret.

```
generated_signature = hmac_sha256(order_id + "|" + razorpay_payment_id, secret);

if (generated_signature == razorpay_signature) {
    payment is successful
}
```

#### Generate Signature on your Server

> [accordion] Sample code
>
> ```java Java theme={null}
> /**
> * This class defines common routines for generating
> * authentication signatures for Razorpay Webhook requests.
> */
> public class Signature
> {
>     private static final String HMAC_SHA256_ALGORITHM = "HmacSHA256";
>     /**
>     * Computes RFC 2104-compliant HMAC signature.
>     * * @param data
>     * The data to be signed.
>     * @param key
>     * The signing key.
>     * @return
>     * The Base64-encoded RFC 2104-compliant HMAC signature.
>     * @throws
>     * java.security.SignatureException when signature generation fails
>     */
>     public static String calculateRFC2104HMAC(String data, String secret)
>     throws java.security.SignatureException
>     {
>         String result;
>         try {
>
>             // get an hmac_sha256 key from the raw secret bytes
>             SecretKeySpec signingKey = new SecretKeySpec(secret.getBytes(), HMAC_SHA256_ALGORITHM);
>
>             // get an hmac_sha256 Mac instance and initialize with the signing key
>             Mac mac = Mac.getInstance(HMAC_SHA256_ALGORITHM);
>             mac.init(signingKey);
>
>             // compute the hmac on input data bytes
>             byte[] rawHmac = mac.doFinal(data.getBytes());
>
>             // base64-encode the hmac
>             result = DatatypeConverter.printHexBinary(rawHmac).toLowerCase();
>
>         } catch (Exception e) {
>             throw new SignatureException("Failed to generate HMAC : " + e.getMessage());
>         }
>         return result;
>     }
> }
>
> ```
>
> ```php PHP theme={null}
> use Razorpay\Api\Api;
> $api = new Api($key_id, $key_secret);
> $attributes  = array('razorpay_signature'  => '23233',  'razorpay_payment_id'  => '332' ,  'razorpay_order_id' => '12122');
> $order  = $api->utility->verifyPaymentSignature($attributes)
>
> ```
>
> ```ruby Ruby theme={null}
> require 'razorpay'
> Razorpay.setup('key_id', 'key_secret')
> payment_response = {
>   'razorpay_order_id': '12122',
>   'razorpay_payment_id': '332',
>   'razorpay_signature': '23233'
> }
>
> Razorpay::Utility.verify_payment_signature(payment_response)
>
> ```
>
> ```python Python theme={null}
> import razorpay
> client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))
>
> client.utility.verify_payment_signature({
>    'razorpay_order_id': razorpay_order_id,
>    'razorpay_payment_id': razorpay_payment_id,
>    'razorpay_signature': razorpay_signature
>    })
>
> ```
>
> ```c .NET theme={null}
>  Dictionary<string, string> attributes = new Dictionary<string, string>();
>
>             attributes.Add("razorpay_payment_id", paymentId);
>             attributes.Add("razorpay_order_id", Request.Form["razorpay_order_id"]);
>             attributes.Add("razorpay_signature", Request.Form["razorpay_signature"]);
>
>             Utils.verifyPaymentSignature(attributes);
> ```
>
> ```nodejs Node.js theme={null}
> var { validatePaymentVerification } = require('./dist/utils/razorpay-utils');
>
> validatePaymentVerification({"order_id": razorpayOrderId, "payment_id": razorpayPaymentId }, signature, secret);
> ```
>
> ```Go Go theme={null}
> import (
> 	"crypto/hmac"
> 	"crypto/sha256"
> 	"crypto/subtle"
> 	"encoding/hex"
> 	"fmt"
> )
>
> func main()  {
> 	signature := "477d1cdb3f8122a7b0963704b9bcbf294f65a03841a5f1d7a4f3ed8cd1810f9b"
> 	secret := "qp3zKxwLZxbMORJgEVWi3Gou"
> 	data := "order_J2AeF1ZpvfqRGH|pay_J2AfAxNHgqqBiI"
> 	//fmt.Printf("Secret: %s Data: %s\n", secret, data)
>
> 	// Create a new HMAC by defining the hash type and the key (as byte array)
> 	h := hmac.New(sha256.New, []byte(secret))
>
> 	// Write Data to it
> 	_, err := h.Write([]byte(data))
>
> 	if err != nil {
> 		panic(err)
> 	}
>
> 	// Get result and encode as hexadecimal string
> 	sha := hex.EncodeToString(h.Sum(nil))
>
> 	fmt.Printf("Result: %s\n", sha)
>
> 	if subtle.ConstantTimeCompare([]byte(sha), []byte(signature)) == 1 {
> 		fmt.Println("Works")
> 	}
> }
> ```

### Step 4: Fetch and Verify Payment

Fetch the payment details to confirm the payment status. See [Fetch a Payment With ID](https://razorpay.com/docs/my/api/payments/fetch-with-id.md).

### Step 5: Capture Payment

Capture the authorised payment. See [Capture a Payment](https://razorpay.com/docs/my/api/payments/capture.md)

## Coupons and Recurring Discounts

Recurring coupons work out of the box with Razorpay. No coupon sync or offer mapping is required.

1. Stripe creates the upcoming invoice with the coupon or discount already applied (reduced amount).
2. Razorpay's cron job scans for upcoming Stripe invoices around 48 hours before the billing date and reads the discounted amount.
3. Razorpay sends a PDN to the customer for the discounted invoice amount from Stripe.
4. On the billing date, Razorpay debits the same discounted amount via the stored mandate.

> [!NOTE]
>
> **Handy Tips**
>
> Any Stripe-level discount is automatically respected by Razorpay during renewal. No special handling is needed on the merchant's side. Stripe is the source of truth for the invoice amount.

## Charges, Taxes and Limits

Stripe remains the source of truth for your billing and invoice amounts. For Indian customers, Razorpay applies the following on the amount it debits.

### 18% GST

Razorpay calculates and adds 18% GST on the amount debited from Indian customers. The customer is charged the total amount, not just the plan amount.

`total_amount = plan_amount + tax_amount`

Where `tax_amount = 18% of plan_amount`. The pricing breakdown (plan amount, GST and total) is available on the frontend via Razorpay Custom JS so the customer sees the final amount before authorising.

### \$1 Minimum Charge

Every debit must be at least $1.00. If the payable amount is below $1.00 (for example, after a large coupon or discount), Razorpay charges \$1.00 and automatically refunds the difference to the customer.

### UPI Recurring Debit Cap

UPI recurring debits are capped at \$250 per transaction. If a debit exceeds this limit, it fails and the customer must switch to a card mandate to complete the payment.

## Pre-Debit Notification (PDN) Timelines

Razorpay sends Pre-Debit Notifications to customers before scheduled subscription debits. Usage-based billing charges immediately and has no PDN.

| Billing Type | PDN Sent Before Debit |
| - | - |
| Subscription renewals (UPI Autopay and card mandate) | Around 48 hours before the billing date |
| Usage-based billing | No PDN — the Stripe invoice triggers an immediate charge |

## Frequently Asked Questions

> [accordion] Do I need to change my Stripe billing logic?
>
> No. Your existing Stripe billing, invoicing and reconciliation workflows remain untouched, and Stripe stays the source of truth for your invoice amounts. Razorpay handles payment execution for Indian customers and adds 18% GST on the debited amount. See [Charges, Taxes and Limits](#charges-taxes-and-limits).

> [accordion] What payment methods does Razorpay support for Indian customers?
>
> Razorpay supports UPI Autopay and card mandates for recurring payments in India. Both methods are RBI-compliant with automatic pre-debit notifications for scheduled renewals.

> [accordion] What happens if a recurring payment fails?
>
> Razorpay automatically retries failed debits in line with RBI norms. The payment outcome (paid or failed) is reported back to Stripe, and your app reacts via existing Stripe webhooks.

> [accordion] Is usage-based billing a separate integration?
>
> Usage-based billing uses the [Stripe Webhook Forwarding](#stripe-webhook-forwarding) API to forward Stripe's `invoice.payment_attempt_required` events to Razorpay, which then charges immediately with no PDN. Scheduled subscription renewals do not use webhook forwarding — Razorpay's cron job drives them automatically.

> [accordion] How are coupons handled?
>
> Coupon creation and application happen at the Stripe level. Razorpay reads the discounted invoice amount from Stripe and charges accordingly. No coupon sync or offer mapping is required.

> [accordion] Does Razorpay add GST to the amount charged?
>
> Yes. Razorpay calculates and adds 18% GST on the amount debited from Indian customers. The customer is charged `plan_amount + tax_amount`, where `tax_amount` is 18% of the plan amount. See [Charges, Taxes and Limits](#charges-taxes-and-limits).

> [accordion] Is there a minimum charge amount?
>
> Yes. Every debit must be at least $1.00. If the payable amount is below $1.00 (for example, after a large coupon), Razorpay charges \$1.00 and automatically refunds the difference to the customer.

> [accordion] Is there a limit on UPI recurring debits?
>
> Yes. UPI recurring debits are capped at \$250 per transaction. If a debit exceeds this limit, the customer must switch to a card mandate to complete the payment.
