> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Subscribe to Webhooks

> Subscribe to various Webhook events related to RazorpayX to receive instant notifications.

Available in
🇮🇳 India

Webhooks (Web Callback, HTTP Push API or Reverse API) are one of the ways in which one web application can send information to another application in real-time when a specific event happens. Know more about [Webhooks](https://razorpay.com/docs/webhooks).

## Set Up and Edit Payout Webhooks

You must first [set up and edit Payout Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payouts.md) as per your requirement.

## Validate and Test Webhooks

Then you must [validate and test webhooks](https://razorpay.com/docs/webhooks/validate-test.md) as a best practice.

## Webhook Events and Descriptions

Listed below are the various webhook events available in RazorpayX. The payload remains the same irrespective of the `fund_account_type`, that is, a bank account, VPA or card, to which the payout is made.

The table below lists the webhook events available for RazorpayX Payouts.

> [!WARNING]
>
> **Watch Out!**
>
> RazorpayX Lite is currently not available for new merchants. To set up a new RazorpayX account, refer to [Current Account](https://razorpay.com/docs/x/account-types/current-account.md).

| Webhook Event | Applicable For | Description |
| - | - | - |
| `payout.pending` | *all payouts* | Triggered whenever a payout moves to the `pending` state. The payout remains in this state till you approve or reject it. |
| `payout.rejected` | *all payouts* | Triggered whenever a payout moves to the `rejected` state. The payout was rejected by someone from your team. |
| `payout.queued` | *all payouts* | <ul><li> Triggered whenever a payout moves to the queued state. Payout goes to queued state when you do not have sufficient funds to process it or when the beneficiary bank/NPCI/partner bank is down. This event is applicable only for RazorpayX Lite.</li><li>You will receive the reason for the payout to be in the queued state as part of the status\_details object.</li></ul> |
| `payout.initiated` | *all payouts* | Triggered when the payout moves to the `processing` state when the payout is created or from the `queued` state when sufficient funds are available to process the payout. |
| `payout.processed` | *all payouts* | Triggered when a payout moves to the `processed` state. This happens when the payout is processed by the contact's bank. |
| `payout.updated` | *all payouts* | Triggered whenever there is a change in the payout entity. For example, when we receive the UTR for the payout from the bank. <ul><li>For NEFT transactions, this webhook is fired within 90 seconds.</li><li>For IMPS and UPI transactions, this webhook is generally fired immediately.</li></ul> |
| `payout.reversed` | *all payouts* | Triggered whenever a payout fails and the amount is returned to your business account. |
| `payout.failed` | *all payouts* | Triggered when a payout is failed because the beneficiary bank OR NPCI OR processing partner bank is down. If the beneficiary bank/partner bank/NPCI does not recover within the stipulated SLA, a FAILED event will be sent with the respective reason. |

> [!NOTE]
>
> **Handy Tips** It is mandatory to subscribe to the `payout.failed` event if you are using Payout APIs.

|
\| `payout.downtime.started` | *all payouts* | Triggered when a payout downtime starts. Do not initiate a payout if this is triggered since the beneficiary bank is down and the payout will fail.

> [!WARNING]
>
> **Watch Out!** UPI mode is not supported by `payout.downtime` webhooks.

|
\| `payout.downtime.resolved` | *all payouts* | Triggered when a payout downtime is resolved. Make payouts once this webhook is triggered as it indicates that the beneficiary bank downtime is resolved. |

The table below lists the webhook events available for RazorpayX transactions.

> [!WARNING]
>
> **Watch Out!**
>
> RazorpayX Lite is currently not available for new merchants. To set up a new RazorpayX account, refer to [Current Account](https://razorpay.com/docs/x/account-types/current-account.md).

| Webhook Events | Description |
| - | - |
| `transaction.created` | Triggered whenever you: <ul><li> Make a Payout (RazorpayX Lite). </li><li> Add funds to your RazorpayX account (RazorpayX Lite). </li></ul> |

When your webhook `secret` is set, Razorpay uses it to create a hash signature with each payload. This hash signature is passed with each request under the `X-Razorpay-Signature` header that you need to validate at your end. Support for validating the signature is provided in all our  [language SDKs](https://razorpay.com/docs/payments/server-integration.md).

> [!WARNING]
>
> **Do Not Parse or Cast the Webhook Request Body**
>
> While generating the signature at your end, ensure that the webhook body passed as an argument is the **raw webhook request body**. **Do not parse or cast the webhook request body**.

```php PHP theme={null}
// PHP SDK: https://github.com/razorpay/razorpay-php
use Razorpay\Api\Api;
$api = new Api("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");

$api->utility->verifyWebhookSignature($webhookBody, $webhookSignature, $webhookSecret);
// $webhookBody should be raw webhook request body
```

```python Python theme={null}
# Python SDK: https://github.com/razorpay/razorpay-python
import razorpay
client = razorpay.Client(auth=("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]"))

client.utility.verify_webhook_signature(webhook_body, webhook_signature, webhook_secret)
# webhook_body should be raw webhook request body
```

```ruby Ruby theme={null}
# Ruby SDK: https://github.com/razorpay/razorpay-ruby
require razorpay

Razorpay::Utility.verify_webhook_signature(webhook_body, webhook_signature, webhook_secret)
# webhook_body should be raw webhook request body
```

```c C# theme={null}
// C# SDK: https://github.com/razorpay/razorpay-dot-net

Utils.verifyWebhookSignature(webhookBody, webhookSignature, webhookSecret);
// webhookBody should be raw webhook request body
```

```java Java theme={null}
// Java SDK: https://github.com/razorpay/razorpay-java

Utils.verifyWebhookSignature(webhookBody, webhookSignature, webhookSecret);
// webhookBody should be raw webhook request body
```

`X-Razorpay-Signature`
: The hash signature is calculated using HMAC with SHA256 algorithm, your webhook secret set as the key and the webhook request body as the message.

You can also validate the webhook signature yourself using an [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code) as shown below:

```
key                = webhook_secret
message            = webhook_body // raw webhook request body
received_signature = webhook_signature

expected_signature = hmac('sha256', message, key)

if expected_signature != received_signature
    throw SecurityError
end
```

## Sample Payloads and Events

See [Payout Sample Payloads](https://razorpay.com/docs/webhooks/payouts.md).

For transaction webhook events, check the [Transaction Sample Payloads](https://razorpay.com/docs/webhooks/transactions.md).

### Related Information

* [Set Up Webhooks for Payouts](https://razorpay.com/docs/webhooks/setup-edit-payouts.md)
* [Payout APIs](https://razorpay.com/docs/api/x/payouts.md)
