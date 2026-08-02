# 2. Fetch and Manage Tokens

Once you capture a payment, Razorpay Checkout returns a `razorpay_payment_id`. You can use this id to fetch the `token_id`, which is used to create and charge subsequent payments.

You can retrieve the `token_id` using the [Dashboard](https://razorpay.com/docs/build/llm-docs/payments/recurring-payments/create.md#3-search-for-the-token) or the APIs given below.

## 2.1 What is a Token?

A token is a unique identifier that represents a registered UPI Autopay mandate between a customer and your business. When a customer approves a mandate through their UPI app during the [Initiate Mandate Registration](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/s2s-integration/recurring-payments/upi/authorization-transaction.md) step, Razorpay generates a `token_id` and associates it with the customer's `customer_id`.

The token stores the mandate's configuration, including the maximum debit amount, frequency and expiry date. You use this `token_id` every time you want to charge the customer a subsequent payment. A single customer can have multiple tokens for different mandates, for example, one for a monthly subscription and another for a quarterly insurance premium.

**INFO**

**Handy Tips**

- Each token is tied to a specific payment method and customer. A token created via UPI cannot be used for card-based recurring payments and vice versa.
- Tokens have a lifecycle with defined states. Always check the token state before attempting a subsequent debit. Know more in the [Token States](#22-token-states) section below.

## 2.2 Token States

A UPI Autopay token (mandate) transitions through the following states during its lifecycle. Ensure your integration handles all of these states to avoid unexpected failures.

Token State | Description
---
`initiated` | The mandate registration request has been sent to the customer's UPI app. The customer has not yet approved or rejected it.
---
`confirmed` | The customer has successfully approved the mandate. The token is active and can be used for subsequent debits.
---
`rejected` | The customer rejected the mandate registration request from their UPI app.
---
`paused` | The mandate has been temporarily paused. No subsequent debits can be executed while the token is in this state.
---
`cancellation_initiated` | The cancellation request has been submitted via the Cancel Token API. Razorpay is waiting for NPCI and the customer's bank to process and confirm the mandate closure. This is a temporary in-transit state. No subsequent debits can be executed while the token is in this state.
---
`cancelled` | The mandate has been permanently cancelled, either by the customer from their UPI app or by the merchant via the Cancel Token API. NPCI and the bank have confirmed the closure. No further debits are possible.
---
`expired` | The mandate has crossed its `expire_at` date and is no longer valid for debits.

**WARN**

**Watch Out!**

- Only tokens in the `confirmed` state can be used to execute subsequent payments.
- If a token transitions to `paused`, `cancellation_initiated`, `cancelled` or `expired`, any subsequent payment attempt against that token will fail.
- Tokens in the `cancellation_initiated` state will eventually transition to `cancelled` once NPCI confirms the closure. Do not treat `cancellation_initiated` as a final state.
- Tokens in the `rejected` state indicate that the customer declined the mandate. You will need to initiate a new mandate registration for the customer.

## 2.3. Fetch Token by Payment ID

The following endpoint fetches the `token_id` using a `payment_id`.

/payments/:id

```cURL: Curl
curl -u : \
-X GET https://api.razorpay.com/v1/payments/pay_1Aa00000000002

```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String paymentId = "pay_1Aa00000000002";

Payment payment = razorpay.payments.fetch(paymentId)

```php: PHP
$api = new Api($key_id, $secret);

$api->payment->fetch($paymentId);
```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.payments.fetch(paymentId)

```python: Python
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.payment.fetch(paymentId)

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

paymentId = "pay_FHfAzEJ51k8NLj"

Razorpay::Payment.fetch(paymentId)

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Payment.Fetch("", nil, nil)

```csharp: .NET
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string paymentid = "pay_FHfqtkRzWvxky4";

Payment payment = client.Payment.Fetch(paymentid);
```

```json: Debit Payment
{
  "id": "pay_FHfAzEJ51k8NLj",
  "entity": "payment",
  "amount": 100,
  "currency": "INR",
  "status": "captured",
  "order_id": "order_FHfANdTUYeP8lb",
  "invoice_id": null,
  "international": false,
  "method": "upi",
  "amount_refunded": 0,
  "refund_status": null,
  "captured": true,
  "description": null,
  "card_id": null,
  "bank": null,
  "wallet": null,
  "vpa": "gaurav.kumar@upi",
  "email": "gaurav.kumar@example.com",
  "contact": "+919876543210",
  "customer_id": "cust_DtHaBuooGHTuyZ",
  "token_id": "token_FHfAzGzREc1ug6",
  "notes": {
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot."
  },
  "fee": 0,
  "tax": 0,
  "error_code": null,
  "error_description": null,
  "error_source": null,
  "error_step": null,
  "error_reason": null,
  "acquirer_data": {
    "rrn": "854977234911",
    "upi_transaction_id": "D0BED5A062ECDB3E9B3A1071C96BB273"
  },
  "created_at": 1595447490
}
```json: Authorisation Payment
{
  "id": "pay_QDhVJ5M23wt4rh",
  "entity": "payment",
  "amount": 1000,
  "currency": "INR",
  "status": "failed",
  "order_id": "order_QDhT2PqFJvtg4y",
  "invoice_id": null,
  "international": false,
  "method": "upi",
  "amount_refunded": 0,
  "refund_status": null,
  "captured": false,
  "description": null,
  "card_id": null,
  "bank": null,
  "wallet": null,
  "vpa": "success@razorpay",
  "email": "gaurav.kumar@example.com",
  "contact": "+919123456780",
  "customer_id": "cust_Q0g6LTYw3obZEn",
  "token_id": "token_QDhVJHYr5m87fF",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf.",
    "note_key 1": "Beam me up Scotty",
    "note_key 2": "Tea. Earl Gray. Hot.",
    "optimizer_provider_name": "razorpay"
  },
  "fee": null,
  "tax": null,
  "error_code": "BAD_REQUEST_ERROR",
  "error_description": "Payment was a dummy payment for one time mandate registration.",
  "error_source": "business",
  "error_step": "payment_initiation",
  "error_reason": "upi_dummy_payment",
  "acquirer_data": {
    "rrn": null
  },
  "gateway_provider": "Razorpay",
  "created_at": 1743490280,
  "upi": {
    "vpa": "success@razorpay"
  }
}
```

**INFO**

**Handy Tips**

You can also retrieve the `token_id` via the [payment.authorized webhook](https://razorpay.com/docs/build/llm-docs/api/payments/recurring-payments/webhooks.md#payment-authorized).

### Path Parameter

`id` _mandatory_
: `string` The unique identifier of the payment to be retrieved. For example, `pay_1Aa00000000002`.

## 2.4. Fetch Tokens by Customer ID

A customer can have multiple tokens and these tokens can be used to create subsequent payments for multiple products or services. The following endpoint retrieves tokens linked to a customer.

**WARN**

**Watch Out!**

- This endpoint will not fetch the details of expired and unused tokens.
- The UPI tokens are not populated in the API response if the `save_vpa` feature is not enabled in your account. Please raise a request with our Support team to get this activated.

/customers/:id/tokens

```curl: Curl
curl -u : \
-X GET https://api.razorpay.com/v1/customers/cust_1Aa00000000002/tokens

```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String customerId = "cust_1Aa00000000002";

List tokens = razorpay.customers.fetchTokens(customerId);

```php: PHP
$api = new Api($key_id, $secret);

$api->customer->fetch($customerId)->tokens()->all();
```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.customers.fetchTokens(customerId)

```python: Python
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.token.all(customerId)

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

customerId = "cust_1Aa00000000004"

Razorpay::Customer.fetch(customerId).fetchTokens

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Token.All("", nil, nil)

```csharp: .NET
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string customerId = "cust_1Aa00000000001";

List token = client.Customer.Fetch(customerId).Tokens();
```

```json: Response
{
  "entity": "collection",
  "count": 1,
  "items": [
    {
      "id": "token_FHfAzGzREc1ug6",
      "entity": "token",
      "token": "9KHsdPaCELeQ0t",
      "bank": null,
      "wallet": null,
      "method": "upi",
      "vpa": {
        "username": "gaurav.kumar",
        "handle": "upi",
        "name": null
      },
      "recurring": true,
      "recurring_details": {
        "status": "confirmed",
        "failure_reason": null
      },
      "auth_type": null,
      "mrn": null,
      "used_at": 1595447490,
      "created_at": 1595447490,
      "start_time": 1595447455,
      "dcc_enabled": false
    }
  ]
}
```

**INFO**

**Handy Tips**

The `recurring_details.status` field in the response indicates the current token state. Use this to check if the token is `confirmed` (active), `paused`, `cancelled` or in any other state before attempting a subsequent debit.

### Path Parameter

`id` _mandatory_
: `string` The unique identifier of the customer for whom tokens are to be retrieved. For example, `cust_1Aa00000000002`.

## 2.5. Fetch Token by Token ID and Customer ID

Use this API to fetch token details using `token_id` and `customer_id` as path parameters.

/v1/customers/:customer_id/tokens/:token_id

```curl: Request
curl -u : \
-X GET https://api.razorpay.com/v1/customers/cust_1Aa00000000002/tokens/token_1Aa00000000001
```json: Response
{
  "id": "token_FHfAzGzREc1ug6",
  "entity": "token",
  "token": "9KHsdPaCELeQ0t",
  "bank": null,
  "wallet": null,
  "method": "upi",
  "vpa": {
    "username": "gaurav.kumar",
    "handle": "upi",
    "name": null
  },
  "recurring": true,
  "recurring_details": {
    "status": "confirmed",
    "failure_reason": null
  },
  "auth_type": null,
  "mrn": null,
  "used_at": 1595447490,
  "created_at": 1595447490,
  "start_time": 1595447455,
  "dcc_enabled": false,
  "max_amount": 500000,
  "expired_at": 1893456000
}
```

  
### Path Parameters

`customer_id` _mandatory_
: `string` The unique identifier of the customer with whom the token is linked. For example, `cust_1Aa00000000002`.

`token_id` _mandatory_
: `string` The unique identifier of the token to be fetched. For example, `token_1Aa00000000001`.
    

  
### Response Parameters

`id`
: `string` The unique identifier of the token. For example, `token_FHfAzGzREc1ug6`.

`entity`
: `string` The name of the entity. Here, it is `token`.

`token`
: `string` The token value used to identify the mandate.

`bank`
: `string` The bank associated with the token. Returns `null` for UPI tokens.

`wallet`
: `string` The wallet associated with the token. Returns `null` for UPI tokens.

`method`
: `string` The payment method associated with the token. Here, it is `upi`.

`vpa`
: `json object` Details of the customer's UPI VPA linked to the token.

  `username`
  : `string` The username part of the customer's UPI ID.

  `handle`
  : `string` The handle (bank or PSP) part of the customer's UPI ID. For example, `upi`.

  `name`
  : `string` The account holder's name as registered with the bank. Returns `null` if not available.

`recurring`
: `boolean` Indicates whether the token is enabled for recurring payments. Possible values: `true`, `false`.

`recurring_details`
: `json object` Details of the recurring mandate associated with the token.

  `status`
  : `string` The status of the recurring mandate. For example, `confirmed`.

  `failure_reason`
  : `string` The reason for mandate failure, if applicable. Returns `null` if there is no failure.

`auth_type`
: `string` The authentication type used. Returns `null` if not applicable.

`mrn`
: `string` The mandate reference number. Returns `null` if not yet assigned.

`used_at`
: `integer` Unix timestamp at which the token was last used. Returns `null` if unused.

`created_at`
: `integer` Unix timestamp at which the token was created.

`start_time`
: `integer` Unix timestamp at which the mandate validity begins.

`dcc_enabled`
: `boolean` Indicates whether Dynamic Currency Conversion (DCC) is enabled.

`max_amount`
: `integer` The maximum amount that can be debited per transaction, in currency subunits.

`expired_at`
: `integer` Unix timestamp at which the token expires.
    

## 2.6. Cancel Token

You can cancel tokens that are in the `initiated`, `confirmed` or `paused` state. Razorpay does not perform any additional validation checks before forwarding the cancellation request to NPCI. 

Cancellations can fail if NPCI returns a failure response. This typically happens due to an internal issue on the remitter's side. Use the following endpoint to cancel a token. This initiates the cancellation of the mandate from NPCI.

/customers/:customer_id/tokens/:token_id/cancel

```curl: Request
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X PUT https://api.razorpay.com/v1/customers/cust_1Aa00000000002/tokens/token_1Aa00000000001/cancel
```json: Response
{
      "status": "cancellation_initiated"
}
```

**INFO**

**Handy Tips**

- Use the Cancel Token API when you want to permanently revoke the mandate from NPCI. This ensures the customer cannot be charged further against this mandate.
- The response status `cancellation_initiated` indicates that the cancellation request has been sent to NPCI. The token enters the `cancellation_initiated` state while Razorpay waits for NPCI and the customer's bank to process the closure. Once confirmed, the token transitions to `cancelled`.
- Do not attempt subsequent debits while the token is in the `cancellation_initiated` state. The payment will fail.

  
### Path Parameters

    
`customer_id` _mandatory_
: `string` The unique identifier of the customer with whom the token is linked. For example, `cust_1Aa00000000002`.

`token_id` _mandatory_
: `string` The unique identifier of the token that is to be cancelled. For example, `token_1Aa00000000001`.
    

  
### Error Response Parameters

Given below is a list of possible errors you may face while cancelling a token.

    
        token_not_recurring
        
         - **Description**: The token provided is not a recurring/autopay token and is not eligible for cancellation via this API.
         - **Next Steps**: Please ensure you are passing a valid UPI Autopay recurring token. Non-recurring tokens cannot be cancelled using this API.
        

    
### invalid_mandate_state

         - **Description**: The UPI mandate linked to this token is not in a cancellable state. The mandate may already be revoked or failed.
         - **Next Steps**: Please check the current status of the mandate before attempting cancellation. Cancellation is only allowed when the mandate is in confirmed or active state.
        

    
### token_customer_mismatch

         - **Description**: The token provided does not belong to the authenticated customer. Cross-customer token access is not permitted.
         - **Next Steps**: Please verify that the `token_id` belongs to the customer in context and retry with the correct token.
        

    
### token_merchant_mismatch

         - **Description**: The token provided was not created under your merchant account. Cross-merchant token access is not permitted.
         - **Next Steps**: Please ensure you are using tokens created under your own merchant account and retry with the correct `token_id`.
        

    
### concurrent_request_in_progress

         - **Description**: A cancellation or update operation is already in progress for this token. Simultaneous requests on the same token are not allowed.
         - **Next Steps**: Please wait at least 60 seconds before retrying the cancellation request. Avoid sending duplicate or parallel cancel requests for the same token.
        

    
  

## 2.7. Delete Tokens

Deleting a token removes it from Razorpay's database. The deleted token will not appear on the Dashboard or when all tokens are fetched. However, it does not cancel the mandate. If you wish to delete the mandate with Razorpay, you must first cancel it using the [Cancel Token API](#25-cancel-token).

The following endpoint deletes a token.

/customers/:customer_id/tokens/:token_id

```curl: Curl
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X DELETE https://api.razorpay.com/v1/customers/cust_1Aa00000000002/tokens/token_1Aa00000000001

```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String customerId = "cust_1Aa00000000002";

String tokenId = "token_1Aa00000000001";

Customer customer = razorpay.customers.deleteToken(customerId, tokenId);

```php: PHP
$api = new Api($key_id, $secret);

$api->customer->fetch($customerId)->tokens()->delete($tokenId);
```javascript: Node.js
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.customers.deleteToken(customerId, tokenId)

```python: Python
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.token.delete(customerId, tokenId)

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

customerId = "cust_1Aa00000000004"

tokenId = "token_Hxe0skTXLeg9pF"

Razorpay::Customer.fetch(customerId).deleteToken(tokenId)

```go: Go
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Token.Delete("", "", nil, nil)

```csharp: .NET
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string customerId = "cust_Z6t7VFTb9xHeOs";

string tokenId = "token_1Aa00000000001";

Customer customer = client.Customer.Fetch(customerId).DeleteToken(tokenId);
```
```json: Response
{
    "deleted": true
}
```

  
### Path Parameters

`customer_id` _mandatory_
: `string` The unique identifier of the customer with whom the token is linked. For example, `cust_1Aa00000000002`.

`token_id` _mandatory_
: `string` The unique identifier of the token that is to be deleted. For example, `token_1Aa00000000001`.
    

  
### Response Parameters

`deleted`
: `boolean` Indicates whether the token is deleted. Possible values:
    - `true`: The token is deleted successfully.
    - `false`: The token was not deleted.
