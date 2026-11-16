> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payments Webhook Events

> List of Payments webhook events along with sample payloads.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can accept customer payments using Razorpay products. By subscribing to payments webhook events you can get notified about payment state changes.

## List of Payments Webhook Events

The table below lists the webhook events available for payments.

| Webhook Event | Description |
| - | - |
| `payment.authorized` | Triggered when a payment is authorised. |
| `payment.captured` | Triggered when a payment is successfully captured. |
| `payment.failed` | Triggered when a payment fails. |

> [!NOTE]
>
> **Handy Tips**
>
> <ul>
>   <li>The payload for a Webhook is a snapshot of the entity when the event occurred.
>   For example, when a customer makes a payment, its status changes to `authorized`. It can then immediately move to the `captured` state.</li>
>   <li>The payment can be in the `captured` state when the `payment.authorized` Webhook is fired. However, the payload for the `payment.authorized` event contains details of the events when the payment was authorised, not when it was captured.</li>
> </ul>

### Comparison: payment.captured vs order.paid

Orders and payments go hand-in-hand. Once a payment is captured, the order is marked paid.  This is reflected in the `order.paid` and `payment.captured` webhook events as well. These events are triggered when the payment associated with the order is captured.

| `payment.captured` Webhook Event | `order.paid` Webhook Event |
| - | - |
| This event is triggered when the payment is successfully captured. | This event is triggered when a customer completes the checkout process and the order's status changes to `paid`. |
| This payload only contains the payment entity, providing details specific to the transaction, such as the amount, currency, and payment method. | This payload includes both order and payment entities, making all relevant information available in a single payload. |

## Sample Payloads

Given below are the sample payloads for payments webhook events.

### Payment Authorised

```json Card theme={null}
{
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "contains": [
    "payment"
  ],
  "created_at": 1691735748,
  "entity": "event",
  "event": "payment.authorized",
  "payload": {
    "payment": {
      "entity": {
        "acquirer_data": {
          "auth_code": "828553",
          "rrn": "322206890934"
        },
        "amount": 100,
        "amount_refunded": 0,
        "amount_transferred": 0,
        "bank": null,
        "captured": true,
        "card": {
          "emi": false,
          "entity": "card",
          "id": "card_DESp9fNnu0RoNc",
          "iin": "999999",
          "international": false,
          "issuer": null,
          "last4": "0153",
          "name": "<name>",
          "network": "Visa",
          "sub_type": "business",
          "type": "debit"
        },
        "card_id": "card_DESp9fNnu0RoNc",
        "contact": "<phone>",
        "created_at": 1567674797,
        "currency": "SGD",
        "description": null,
        "email": "<email>",
        "entity": "payment",
        "error_code": "",
        "error_description": "",
        "error_reason": null,
        "error_source": null,
        "error_step": null,
        "fee": null,
        "id": "pay_DESp9bgForNoUd",
        "international": false,
        "invoice_id": null,
        "method": "card",
        "notes": [],
        "order_id": "order_DESoU0U4ikYA19",
        "refund_status": null,
        "status": "authorized",
        "tax": null,
        "token_id": "token_MOfFlFTC1CBDOi",
        "vpa": null,
        "wallet": null
      }
    }
  }
}
```

### Payment Captured

```json Card theme={null}
{
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "contains": [
    "payment"
  ],
  "created_at": 1691735748,
  "entity": "event",
  "event": "payment.captured",
  "payload": {
    "payment": {
      "entity": {
        "acquirer_data": {
          "auth_code": "828553",
          "rrn": "322206890934"
        },
        "amount": 100,
        "amount_refunded": 0,
        "amount_transferred": 0,
        "bank": null,
        "captured": true,
        "card": {
          "emi": false,
          "entity": "card",
          "id": "card_DESp9fNnu0RoNc",
          "iin": "999999",
          "international": false,
          "issuer": null,
          "last4": "0153",
          "name": "<name>",
          "network": "Visa",
          "sub_type": "business",
          "type": "debit"
        },
        "card_id": "card_DESp9fNnu0RoNc",
        "contact": "<phone>",
        "created_at": 1567674797,
        "currency": "SGD",
        "description": null,
        "email": "<email>",
        "entity": "payment",
        "error_code": "",
        "error_description": "",
        "error_reason": null,
        "error_source": null,
        "error_step": null,
        "fee": null,
        "id": "pay_DESp9bgForNoUd",
        "international": false,
        "invoice_id": null,
        "method": "card",
        "notes": [],
        "order_id": "order_DESoU0U4ikYA19",
        "refund_status": null,
        "status": "captured",
        "tax": null,
        "token_id": "token_MOfFlFTC1CBDOi",
        "vpa": null,
        "wallet": null
      }
    }
  }
}
```

### Payment Failed

```json Card theme={null}
{
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "contains": [
    "payment"
  ],
  "created_at": 1691735748,
  "entity": "event",
  "event": "payment.failed",
  "payload": {
    "payment": {
      "entity": {
        "acquirer_data": {
          "auth_code": "828553",
          "rrn": "322206890934"
        },
        "amount": 100,
        "amount_refunded": 0,
        "amount_transferred": 0,
        "bank": null,
        "captured": true,
        "card": {
          "emi": false,
          "entity": "card",
          "id": "card_DESp9fNnu0RoNc",
          "iin": "999999",
          "international": false,
          "issuer": null,
          "last4": "0153",
          "name": "<name>",
          "network": "Visa",
          "sub_type": "business",
          "type": "debit"
        },
        "card_id": "card_DESp9fNnu0RoNc",
        "contact": "<phone>",
        "created_at": 1567674797,
        "currency": "SGD",
        "description": null,
        "email": "<email>",
        "entity": "payment",
        "error_code": "",
        "error_description": "",
        "error_reason": null,
        "error_source": null,
        "error_step": null,
        "fee": null,
        "id": "pay_DESp9bgForNoUd",
        "international": false,
        "invoice_id": null,
        "method": "card",
        "notes": [],
        "order_id": "order_DESoU0U4ikYA19",
        "refund_status": null,
        "status": "failed",
        "tax": null,
        "token_id": null,
        "vpa": null,
        "wallet": null
      }
    }
  }
}
```

## Payments Downtime

Downtime is a period during which one or more payment options underperform, leading to considerable delays in payment processing. These downtimes are due to technical issues or outages at Razorpay's partner or issuing banks side. Razorpay informs you about the downtime to communicate it to your customers.

### List of Payments Downtime Webhook Events

The table below lists the webhook events available for payments downtime.

| Webhook Event | Description |
| - | - |
| `payment.downtime.started` | Triggered at the beginning of the downtime. |
| `payment.downtime.resolved` | Triggered when a downtime is resolved. |
| `payment.downtime.updated` | Triggered when a downtime is updated. |

### Payment Downtime Started

```json Card - Issuer theme={null}
{
  "entity": "event",
  "account_id": "acc_CWX291oykl9aZA",
  "event": "payment.downtime.started",
  "contains": [
    "payment.downtime"
  ],
  "payload": {
    "payment.downtime": {
      "entity": {
        "id": "down_F1Zppa6lcVheSE",
        "entity": "payment.downtime",
        "method": "card",
        "begin": 1591935238,
        "end": null,
        "status": "started",
        "scheduled": false,
        "severity": "high",
        "instrument": {
          "issuer": "SBIN",
          "type": "credit"          
        },
        "instrument_schema": ["issuer", "type"],
        "created_at": 1591935238,
        "updated_at": 1591935238
      }
    }
  },
  "created_at": 1591935238
}
```

```json Card - Network theme={null}
{
  "entity": "event",
  "account_id": "acc_CWX291oykl9aZA",
  "event": "payment.downtime.started",
  "contains": [
    "payment.downtime"
  ],
  "payload": {
    "payment.downtime": {
      "entity": {
        "id": "down_F1Zppa6lcVheSE",
        "entity": "payment.downtime",
        "method": "card",
        "begin": 1591935238,
        "end": null,
        "status": "started",
        "scheduled": false,
        "severity": "high",
        "instrument": {
          "network": "MC",
          "type": "credit"
        },
        "instrument_schema": ["network", "type"],
        "created_at": 1591935238,
        "updated_at": 1591935238
      }
    }
  },
  "created_at": 1591935238
}
```

### Payment Downtime Resolved

```json Card - Issuer theme={null}
{
  "entity": "event",
  "account_id": "acc_DjF2cSbjtnqhJ5",
  "event": "payment.downtime.resolved",
  "contains": [
    "payment.downtime"
  ],
  "payload": {
    "payment.downtime": {
      "entity": {
        "id": "down_ENCWhh1lon7Hpp",
        "entity": "payment.downtime",
        "method": "card",
        "begin": 1583119550,
        "end": 1583119551,
        "status": "resolved",
        "scheduled": false,
        "severity": "medium",
        "instrument": {
          "issuer": "SBIN",
          "type": "credit"
        },
        "instrument_schema": ["issuer", "type"],
        "created_at": 1583119551,
        "updated_at": 1591948663
      }
    }
  },
  "created_at": 1591948663
}
```

```json Card - Network theme={null}
{
  "entity": "event",
  "account_id": "acc_DjF2cSbjtnqhJ5",
  "event": "payment.downtime.resolved",
  "contains": [
    "payment.downtime"
  ],
  "payload": {
    "payment.downtime": {
      "entity": {
        "id": "down_ENCWhh1lon7Hpp",
        "entity": "payment.downtime",
        "method": "card",
        "begin": 1583119550,
        "end": 1583119551,
        "status": "resolved",
        "scheduled": false,
        "severity": "medium",
        "instrument": {
          "network": "MC",
          "type": "credit"
        },
        "instrument_schema": ["network", "type"],
        "created_at": 1583119551,
        "updated_at": 1591948663
      }
    }
  },
  "created_at": 1591948663
}
```

### Payment Downtime Updated

```json Card - Network theme={null}
{
  "entity": "event",
  "account_id": "acc_CWX291oykl9aZA",
  "event": "payment.downtime.updated",
  "contains": [
    "payment.downtime"
  ],
  "payload": {
    "payment.downtime": {
      "entity": {
        "id": "down_F1Zppa6lcVheSE",
        "entity": "payment.downtime",
        "method": "card",
        "begin": 1591935238,
        "end": null,
        "status": "updated",
        "scheduled": false,
        "severity": "high",
        "instrument": {
          "network": "MC",
          "type": "credit"
        },
        "instrument_schema": ["network", "type"],
        "created_at": 1591935238,
        "updated_at": 1591935238
      }
    }
  },
  "created_at": 1591935238
}
```

```json Card - Issuer theme={null}
{
  "entity": "event",
  "account_id": "acc_CWX291oykl9aZA",
  "event": "payment.downtime.updated",
  "contains": [
    "payment.downtime"
  ],
  "payload": {
    "payment.downtime": {
      "entity": {
        "id": "down_F1Zppa6lcVheSE",
        "entity": "payment.downtime",
        "method": "card",
        "begin": 1591935238,
        "end": null,
        "status": "updated",
        "scheduled": false,
        "severity": "high",
        "instrument": {
          "issuer": "SBIN",
          "type": "credit"
        },
        "instrument_schema": ["issuer", "type"],
        "created_at": 1591935238,
        "updated_at": 1591935238
      }
    }
  },
  "created_at": 1591935238
}
```

> [!WARNING]
>
> **Watch Out!**
>
> * If you have changed your webhook secret, remember to use the old secret for webhook signature validation while retrying older requests. Using the new secret will lead to a signature mismatch.
>
> * While generating a signature at your end, ensure that the webhook body is passed as an argument in the **raw webhook request body**. **Do not parse or cast the webhook request body**.
