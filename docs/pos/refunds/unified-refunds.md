> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Unified Refunds for POS

> Issue full and partial refunds on POS payments from a single experience across API, Dashboard and device. Check supported banks, refund speed, status and webhooks.

Available in
🇮🇳 India

A refund returns the transaction amount to your customer. You issue refunds when a customer returns a product, cancels an order or is unhappy with a service.

With Unified Refunds, you initiate a refund from a single experience point and Razorpay routes it to the right method and gateway based on the original transaction. You do not need to handle the underlying technicalities.

> [!NOTE]
>
> **Customer Looking for Refund**
>
> If you are a customer looking for a refund, know about [customer refunds](https://razorpay.com/docs/payments/customers/customer-refunds.md).

## Supported Banks and Methods

Unified Refunds currently support the following acquiring banks and payment methods:

| Bank | Cards | UPI |
| - | - | - |
| SBI | Supported | Supported |
| HDFC | Supported | Supported |

> [!NOTE]
>
> **Handy Tips**
>
> Support for more banks and methods is being added. Refunds are possible only for payments in the `captured` state.

## Refund Surfaces

You can initiate a refund from any of the following surfaces:

* **API**: Initiate a refund from your CRM or backend using the [Refunds API](https://razorpay.com/docs/api/refunds.md).
* **Dashboard**: Initiate a refund from the Razorpay Dashboard. See [Issue Refunds](https://razorpay.com/docs/pos/refunds/issue.md).
* **Device**: Initiate a refund directly on the POS device.

> [!NOTE]
>
> **Handy Tips**
>
> A refund initiated from one surface appears in the others as an entry along with its status.

## Refund Types

| Type | Description |
| - | - |
| Full refund | The entire transaction amount is refunded to the customer. |
| Partial refund (once) | A part of the transaction amount is refunded one time. |
| Partial refund (multiple) | A part of the transaction amount is refunded across multiple refunds. The total refunded amount cannot exceed the original transaction amount. |

> [!WARNING]
>
> **Watch Out!**
>
> For HDFC card payments, only a single partial refund is supported. SBI card and UPI payments and HDFC UPI payments support multiple partial refunds.

## Refund Speed

POS refunds are processed as **Normal refunds**. The refund is credited to the original payment method, and the time taken depends on the method used for the original payment.

| Payment Method | Refund Time |
| - | - |
| Cards (credit, debit) | 5-10 days |
| Netbanking | 2-10 days |
| UPI | 2-7 days |
| Wallet | 0-3 days |

> [!NOTE]
>
> **Handy Tips**
>
> Instant refunds are not currently available for POS payments.

## Refund Fees

Razorpay does not charge a processing fee for Normal refunds. However, the transaction fee, GST and MDR levied at the time of payment capture are not reversed to your account. The customer receives the entire transaction amount.

## Refund Status

A refund can be in one of the following states:

| Status | Description |
| - | - |
| `PENDING` | The refund has been initiated by Razorpay and is awaiting processing at the gateway. |
| `REFUNDED` | The final state of a successful refund. |
| `FAILED` | The refund request was rejected. |

> [!NOTE]
>
> **Handy Tips**
>
> * You can initiate a refund up to 120 days for RuPay and 180 days for other networks from the transaction date.
> * Once a refund is `REFUNDED`, if the customer does not see the credit, they should contact their issuing bank.

## Reference Numbers

Each transaction and its refund carry a unique reference number you can use for reconciliation:

| Payment Method | Transaction Identifier | Refund Identifier |
| - | - | - |
| Cards (credit, debit) | RRN (Retrieval Reference Number) | ARN (Acquirer Reference Number) |
| UPI | ARN (Acquirer Reference Number) | RRN (Retrieval Reference Number) |
| Netbanking (NEFT, RTGS, IMPS) | UTR (Unique Transaction Reference) | UTR (Unique Transaction Reference) |

> [!NOTE]
>
> **Handy Tips**
>
> For multiple partial refunds, a separate refund identifier is generated for each refund.

## Webhooks

To receive refund notifications, subscribe to webhook events on the Razorpay Dashboard under **Account & Settings → Webhooks**. The following events are available:

| Event | Triggered when |
| - | - |
| `refund.created` | A refund is created. |
| `refund.processed` | A refund is successfully processed. |
| `refund.failed` | Razorpay is unable to process a refund. |

Know more about [subscribing to webhooks](https://razorpay.com/docs/payments/refunds/subscribe-to-webhooks.md).

### Related Information

* [About Refunds](https://razorpay.com/docs/pos/refunds)
* [Issue Refunds](https://razorpay.com/docs/pos/refunds/issue.md)
* [View Refunds](https://razorpay.com/docs/pos/refunds/view.md)
* [Handle Refund Errors](https://razorpay.com/docs/pos/refunds/errors.md)
* [Refunds API](https://razorpay.com/docs/api/refunds.md)
* [Refunds FAQs](https://razorpay.com/docs/pos/refunds/faqs.md)
