# Manage Mandates and Tokens

Once your UPI Reserve Pay integration is live, you can use the following APIs to monitor and manage active mandates.

## Track Mandate Funds

Use the `recurring_details` object to monitor the utilisation of funds within an active mandate. This object is available in the response of the [Fetch Token by Customer id](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/s2s-integration/recurring-payments/upi-reserve-pay/integration-steps.md#21-fetch-token-by-customer-id) and [Fetch Token by Token id and Customer id](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/s2s-integration/recurring-payments/upi-reserve-pay/integration-steps.md#23-fetch-token-by-token-id-and-customer) APIs. This object contains the following parameters:

Parameter | Description
---
`amount_blocked` | The total amount the customer authorised at the start.
---
`amount_debited` | The cumulative sum of all successful debits made against this token to date.

**INFO**

**Handy Tips**

To find the remaining amount available for future debits, subtract the `amount_debited` from the `amount_blocked`. This allows you to manage customer expectations and ensure you do not initiate a debit that exceeds the remaining authorised limit.

## Cancel Tokens

The blocked amount under a UPI Reserve Pay token can be released in two ways:

  
    Use the [Cancel Token API](#cancel-token-api) below to release the blocked funds. When this API is called, all remaining funds under the token are unblocked and credited to the customer's bank account instantly.
  
  
    If you do not cancel the token and the token balance is not fully utilised before expiry, Razorpay automatically triggers a reversal of the remaining funds 10 minutes before the token expires.
  

Released funds reflect in the customer's account instantly. The bank statement may not display this as a separate credit entry, but the account balance is updated immediately.

**INFO**

**Handy Tips**

Ensure customers are informed that their funds remain blocked until you explicitly release them or the token expires.

## Cancel Token API

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

  
### Path Parameters

    
`customer_id` _mandatory_
: `string` The unique identifier of the customer with whom the token is linked. For example, `cust_1Aa00000000002`.

`token_id` _mandatory_
: `string` The unique identifier of the token that is to be cancelled. For example, `token_1Aa00000000001`.
    

### Error Response Parameters

Given below is a list of possible errors you may face while cancelling a token.

    
### token_not_recurring

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
        

    
### invalid_request_timing

         - **Description**: The cancellation request was received outside the allowed cancellation window or for an unsupported mandate type.
         - **Next Steps**: Please ensure the cancel request is sent within the valid cancellation window and that the mandate type supports this operation. Retry after verifying mandate details.
        

## Delete Tokens API

Deleting a token removes it from Razorpay's database. The deleted token will not appear on the Dashboard or when all tokens are fetched. However, it does not cancel the mandate. If you wish to delete the mandate with Razorpay, you must first cancel it using the [Cancel Token API](#cancel-token-api).

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

```ruby: Ruby
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

customerId = "cust_1Aa00000000004"

tokenId = "token_Hxe0skTXLeg9pF"

Razorpay::fetch(customerId).deleteToken(tokenId)

```java: Java
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String customerId = "cust_DtHaBuooGHTuyZ";

String tokenId = "token_HouA2OQR5Z2jTL";

Customer customer = instance.customers.deleteToken(customerId, tokenId);

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
