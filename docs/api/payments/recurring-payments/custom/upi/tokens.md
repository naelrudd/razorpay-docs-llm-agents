> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# 2. Fetch and Manage Tokens

> Retrieve tokens using Razorpay APIs to create subsequent payments.

Available in
🇮🇳 India

Once you capture a payment, Razorpay Checkout returns a `razorpay_payment_id`. You can use this id to fetch the `token_id`, which is used to create and charge subsequent payments.

You can retrieve the `token_id` using the [Dashboard](https://razorpay.com/docs/payments/recurring-payments/create.md#3-search-for-the-token) or the APIs given below.

## Token States

A UPI Autopay token (mandate) transitions through the following states during its lifecycle. Ensure your integration handles all of these states to avoid unexpected failures.

| Token State | Description | Webhook generated |
| - | - | - |
| `initiated` | The mandate registration request has been sent to the customer's UPI app. The customer has not yet approved or rejected it. | No |
| `confirmed` | The customer has successfully approved the mandate, or has resumed a paused token. The token is active and can be used for subsequent debits. | Yes, `token.confirmed` |
| `rejected` | The customer rejected the mandate registration request from their UPI app. | Yes, `token.rejected` |
| `paused` | The mandate has been temporarily paused. No subsequent debits can be executed while the token is in this state. | Yes, `token.paused` |
| `cancellation_initiated` | The cancellation request has been submitted via the Cancel Token API. Razorpay is waiting for NPCI and the customer's bank to process and confirm the mandate closure. This is a temporary in-transit state. No subsequent debits can be executed while the token is in this state. | No |
| `cancelled` | The mandate has been permanently cancelled, either by the customer from their UPI app or by the merchant via the Cancel Token API. NPCI and the bank have confirmed the closure. No further debits are possible. The token also moves to the `cancelled` state if it has crossed its `expire_at` date and is no longer valid for debits. | Yes, `token.cancelled` |

> [!WARNING]
>
> **Watch Out!**
>
> * Only tokens in the `confirmed` state can be used to execute subsequent payments.
> * If a token transitions to `paused`, `cancellation_initiated` or `cancelled`, any subsequent payment attempt against that token will fail.
> * Tokens in the `cancellation_initiated` state will eventually transition to `cancelled` once NPCI confirms the closure. Do not treat `cancellation_initiated` as a final state.
> * Tokens in the `rejected` state indicate that the customer declined the mandate. You will need to initiate a new mandate registration for the customer.
> * Sometimes the customer cancels the token after the pre-debit notification (PDN) is sent. In such cases, you receive both the `token.cancelled` and the `payment.failed` webhooks.

## 2.1. Fetch Token by Payment ID

Use the below endpoint to fetch the `token_id` using a `payment_id`.

`GET /payments/:id`

```bash Curl theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-X GET https://api.razorpay.com/v1/payments/pay_1Aa00000000002
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->payment->fetch($paymentId);
```

```json Response theme={null}
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
```

> [!NOTE]
>
> **Note**
>
> You can also retrieve the `token_id` against the `payment_id` from the [payment.authorized webhook](https://razorpay.com/docs/api/payments/recurring-payments/webhooks.md#payment-authorized).

### Path Parameter

`id` *mandatory*
: `string` The unique identifier of the payment to be retrieved. For example, `pay_1Aa00000000002`.

## 2.2. Fetch Tokens by Customer ID

> [!WARNING]
>
> **Watch Out!**
>
> The UPI tokens are not populated in the API response if the `save_vpa` feature is not enabled in your account. Please raise a request with our [Support team](https://razorpay.com/support/#request) to get this activated.

```bash Curl theme={null}
curl -u <YOUR_KEY_ID>:<YOUR_KEY_SECRET> \
-X GET https://api.razorpay.com/v1/customers/cust_1Aa00000000002/tokens
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->customer->fetch($customerId)->tokens()->all();
```

```json Response theme={null}
{
  "entity": "collection",
  "count": 1,
  "items": [
    {
      "id": "token_FHfAzGzREc1ug6",
      "entity": "token",
      "token": "9KHtest0000001",
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

### Path Parameter

`id` *mandatory*
: `string` The unique identifier of the customer for whom tokens are to be retrieved. For example, `cust_1Aa00000000002`.

## 2.3. Cancel Token

You can cancel tokens that are in the `initiated`, `confirmed` or `paused` state. You can also retry a cancellation for a token that is in the `cancellation_initiated` state. Razorpay does not perform any additional validation checks before forwarding the cancellation request to NPCI.

The interim `cancellation_initiated` status is returned when the cancellation request is acknowledged but a successful callback from the downstream partners is not yet received. When the gateway returns a callback confirming the cancellation, the status updates to `cancelled` and the `token.cancelled` webhook is triggered. Wait for the `token.cancelled` webhook before suspending or terminating subscription services, or applying any late payment fees to customers. Use the following endpoint to cancel a token. This initiates the cancellation of the mandate from NPCI.

`PUT /customers/:customer_id/tokens/:token_id/cancel`

```bash Request theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X PUT https://api.razorpay.com/v1/customers/cust_1Aa00000000002/tokens/token_1Aa00000000001/cancel
```

```json Response theme={null}
{
      "status": "cancellation_initiated"
}
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.token.cancel(customerId, tokenId)
```

> [accordion] Path Parameters
>
> `customer_id` *mandatory*
> : `string` The unique identifier of the customer with whom the token is linked. For example, `cust_1Aa00000000002`.
>
> `token_id` *mandatory*
> : `string` The unique identifier of the token that is to be cancelled. For example, `token_1Aa00000000001`.

### Error Response Parameters

Given below is a list of possible errors you may face while cancelling a token.

> [accordion] token\_not\_recurring
>
> * **Description**: The token provided is not a recurring/autopay token and is not eligible for cancellation via this API.
> * **Next Steps**: Please ensure you are passing a valid UPI Autopay recurring token. Non-recurring tokens cannot be cancelled using this API.

> [accordion] invalid\_mandate\_state
>
> * **Description**: The UPI mandate linked to this token is not in a cancellable state. The mandate may already be revoked or failed.
> * **Next Steps**: Please check the current status of the mandate before attempting cancellation. Cancellation is only allowed when the mandate is in confirmed or active state.

> [accordion] token\_customer\_mismatch
>
> * **Description**: The token provided does not belong to the authenticated customer. Cross-customer token access is not permitted.
> * **Next Steps**: Please verify that the `token_id` belongs to the customer in context and retry with the correct token.

> [accordion] token\_merchant\_mismatch
>
> * **Description**: The token provided was not created under your merchant account. Cross-merchant token access is not permitted.
> * **Next Steps**: Please ensure you are using tokens created under your own merchant account and retry with the correct `token_id`.

> [accordion] concurrent\_request\_in\_progress
>
> * **Description**: A cancellation or update operation is already in progress for this token. Simultaneous requests on the same token are not allowed.
> * **Next Steps**: Please wait at least 60 seconds before retrying the cancellation request. Avoid sending duplicate or parallel cancel requests for the same token.

## 2.4. Delete Tokens

Deleting a token removes it from Razorpay's database. The deleted token will not appear on the Dashboard or when all tokens are fetched. However, it does not cancel the mandate. If you wish to delete the mandate with Razorpay, you must first cancel it using the [Cancel Token API](#2-3-cancel-token).

The following endpoint deletes a token.

`DELETE /customers/:customer_id/tokens/:token_id`

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X DELETE https://api.razorpay.com/v1/customers/cust_1Aa00000000002/tokens/token_1Aa00000000001
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String customerId = "cust_1Aa00000000002";

String tokenId = "token_1Aa00000000001";

Customer customer = razorpay.customers.deleteToken(customerId, tokenId);
```

```php PHP theme={null}
$api = new Api($key_id, $secret);

$api->customer->fetch($customerId)->tokens()->delete($tokenId);
```

```javascript Node.js theme={null}
var instance = new Razorpay({ key_id: 'YOUR_KEY_ID', key_secret: 'YOUR_SECRET' })

instance.customers.deleteToken(customerId, tokenId)
```

```python Python theme={null}
client = razorpay.Client(auth=("YOUR_ID", "YOUR_SECRET"))

client.token.delete(customerId, tokenId)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

customerId = "cust_1Aa00000000004"

tokenId = "token_Hxe0skTXLeg9pF"

Razorpay::Customer.fetch(customerId).deleteToken(tokenId)
```

```go Go theme={null}
import ( razorpay "github.com/razorpay/razorpay-go" )
client := razorpay.NewClient("YOUR_KEY_ID", "YOUR_SECRET")

body, err := client.Token.Delete("<customerId>", "<tokenId>", nil, nil)
```

```ruby Ruby theme={null}
require "razorpay"
Razorpay.setup('YOUR_KEY_ID', 'YOUR_SECRET')

customerId = "cust_1Aa00000000004"

tokenId = "token_Hxe0skTXLeg9pF"

Razorpay::fetch(customerId).deleteToken(tokenId)
```

```java Java theme={null}
RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

String customerId = "cust_DtHaBuooGHTuyZ";

String tokenId = "token_HouA2OQR5Z2jTL";

Customer customer = instance.customers.deleteToken(customerId, tokenId);
```

```csharp .NET theme={null}
RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

string customerId = "cust_Z6t7VFTb9xHeOs";

string tokenId = "token_1Aa00000000001";

Customer customer = client.Customer.Fetch(customerId).DeleteToken(tokenId);
```

```json Response theme={null}
{
    "deleted": true
}
```

> [accordion] Path Parameters
>
> `customer_id` *mandatory*
> : `string` The unique identifier of the customer with whom the token is linked. For example, `cust_1Aa00000000002`.
>
> `token_id` *mandatory*
> : `string` The unique identifier of the token that is to be deleted. For example, `token_1Aa00000000001`.

> [accordion] Response Parameters
>
> `deleted`
> : `boolean` Indicates whether the token is deleted. Possible values:
>
> * `true`: The token is deleted successfully.
> * `false`: The token was not deleted.
