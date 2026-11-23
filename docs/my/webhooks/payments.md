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

You can accept customer payments using Razorpay Curlec products. By subscribing to payments webhook events you can get notified about payment state changes.

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

```json FPX theme={null}
{
  "entity": "event",
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "event": "payment.authorized",
  "contains": [
    "payment"
  ],
  "payload": {
    "payment": {
      "entity": {
        "id": "pay_DESlfW9H8K9uqM",
        "entity": "payment",
        "amount": 100,
        "currency": "MYR",
        "status": "authorized",
        "order_id": "order_DESlLckIVRkHWj",
        "invoice_id": null,
        "international": false,
        "method": "fpx",
        "amount_refunded": 0,
        "refund_status": null,
        "captured": false,
        "description": null,
        "card_id": null,
        "bank": "PHBM",
        "wallet": null,
        "email": "<email>",
        "contact": "<phone>",
        "notes": [],
        "fee": null,
        "tax": null,
        "error_code": null,
        "error_description": null,
        "error_source": null,
        "error_step": null,
        "error_reason": null,
        "acquirer_data": {
          "bank_transaction_id": "0125836177"
        },
        "created_at": 1567674599
      }
    }
  },
  "created_at": 1567674606
}
```

```json Card theme={null}
{
  "entity": "event",
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "event": "payment.authorized",
  "contains": [
    "payment"
  ],
  "payload": {
    "payment": {
      "entity": {
        "id": "pay_DESp9bgForNoUd",
        "entity": "payment",
        "amount": 100,
        "currency": "MYR",
        "status": "authorized",
        "order_id": "order_DESoU0U4ikYA19",
        "invoice_id": null,
        "international": false,
        "method": "card",
        "amount_refunded": 0,
        "refund_status": null,
        "captured": false,
        "description": null,
        "card_id": "card_DESp9fNnu0RoNc",
        "card": {
          "id": "card_DESp9fNnu0RoNc",
          "entity": "card",
          "name": "<name>",
          "last4": "0153",
          "network": "Visa",
          "type": "debit",
          "issuer": null,
          "international": false,
          "sub_type": "business"
        },
        "bank": null,
        "wallet": null,
        "email": "<email>",
        "contact": "<phone>",
        "notes": [],
        "fee": null,
        "tax": null,
        "error_code": null,
        "error_description": null,
        "error_source": null,
        "error_step": null,
        "error_reason": null,
        "acquirer_data": {
          "auth_code": "828553"
        },
        "created_at": 1567674797
      }
    }
  },
  "created_at": 1567674804
}
```

```json Wallets theme={null}
{
  "entity": "event",
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "event": "payment.authorized",
  "contains": [
    "payment"
  ],
  "payload": {
    "payment": {
      "entity": {
        "id": "pay_DEStK8twGApHtW",
        "entity": "payment",
        "amount": 100,
        "currency": "MYR",
        "status": "authorized",
        "order_id": "order_DESso0U9bpuzQc",
        "invoice_id": null,
        "international": false,
        "method": "wallet",
        "amount_refunded": 0,
        "refund_status": null,
        "captured": false,
        "description": null,
        "card_id": null,
        "bank": null,
        "wallet": "touchngo",
        "email": "<email>",
        "contact": "<phone>",
        "notes": [],
        "fee": null,
        "tax": null,
        "error_code": null,
        "error_description": null,
        "error_source": null,
        "error_step": null,
        "error_reason": null,
        "acquirer_data": {
          "transaction_id": null
        },
        "created_at": 1567675034
      }
    }
  },
  "created_at": 1567675037
}
```

### Payment Captured

```json FPX theme={null}
{
  "entity": "event",
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "event": "payment.captured",
  "contains": [
    "payment"
  ],
  "payload": {
    "payment": {
      "entity": {
        "id": "pay_DESlfW9H8K9uqM",
        "entity": "payment",
        "amount": 100,
        "currency": "MYR",
        "base_amount": 100,
        "status": "captured",
        "order_id": "order_DESlLckIVRkHWj",
        "invoice_id": null,
        "international": false,
        "method": "fpx",
        "amount_refunded": 0,
        "amount_transferred": 0,
        "refund_status": null,
        "captured": true,
        "description": null,
        "card_id": null,
        "bank": "PHBM",
        "wallet": null,
        "email": "gaurav.kumar@example.com",
        "contact": "+919876543210",
        "notes": [],
        "fee": 2,
        "tax": 0,
        "error_code": null,
        "error_description": null,
        "error_source": null,
        "error_step": null,
        "error_reason": null,
        "acquirer_data": {
          "bank_transaction_id": "0125836177"
        },
        "created_at": 1567674599
      }
    }
  },
  "created_at": 1567674606
}
```

```json Card theme={null}
{
  "entity": "event",
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "event": "payment.captured",
  "contains": [
    "payment"
  ],
  "payload": {
    "payment": {
      "entity": {
        "id": "pay_DESp9bgForNoUd",
        "entity": "payment",
        "amount": 100,
        "currency": "MYR",
        "base_amount": 100,
        "status": "captured",
        "order_id": "order_DESoU0U4ikYA19",
        "invoice_id": null,
        "international": false,
        "method": "card",
        "amount_refunded": 0,
        "amount_transferred": 0,
        "refund_status": null,
        "captured": true,
        "description": null,
        "card_id": "card_DESp9fNnu0RoNc",
        "card": {
          "id": "card_DESp9fNnu0RoNc",
          "entity": "card",
          "name": "Gaurav Kumar",
          "last4": "0153",
          "network": "Visa",
          "type": "debit",
          "issuer": null,
          "international": false,
          "sub_type": "business"
        },
        "bank": null,
        "wallet": null,
        "email": "gaurav.kumar@example.com",
        "contact": "+919876543210",
        "notes": [],
        "fee": 2,
        "tax": 0,
        "error_code": null,
        "error_description": null,
        "error_source": null,
        "error_step": null,
        "error_reason": null,
        "acquirer_data": {
          "auth_code": "828553"
        },
        "created_at": 1567674797
      }
    }
  },
  "created_at": 1567674804
}
```

```json Wallets theme={null}
{
  "entity": "event",
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "event": "payment.captured",
  "contains": [
    "payment"
  ],
  "payload": {
    "payment": {
      "entity": {
        "id": "pay_DEStK8twGApHtW",
        "entity": "payment",
        "amount": 100,
        "currency": "MYR",
        "base_amount": 100,
        "status": "captured",
        "order_id": "order_DESso0U9bpuzQc",
        "invoice_id": null,
        "international": false,
        "method": "wallet",
        "amount_refunded": 0,
        "amount_transferred": 0,
        "refund_status": null,
        "captured": true,
        "description": null,
        "card_id": null,
        "bank": null,
        "wallet": "touchngo",
        "email": "gaurav.kumar@example.com",
        "contact": "+919876543210",
        "notes": [],
        "fee": 2,
        "tax": 0,
        "error_code": null,
        "error_description": null,
        "error_source": null,
        "error_step": null,
        "error_reason": null,
        "acquirer_data": {
          "transaction_id": null
        },
        "created_at": 1567675034
      }
    }
  },
  "created_at": 1567675037
}
```

```json DuitNow QR theme={null}
{
  "entity": "event",
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "event": "payment.captured",
  "contains": [
    "payment"
  ],
  "payload": {
    "payment": {
      "entity": {
        "id": "pay_LUtJxInEqa0oAA",
        "entity": "payment",
        "amount": 10000,
        "currency": "MYR",
        "status": "captured",
        "order_id": "order_LSA6ny1sGKAp0C",
        "method": "duitnow",
        "duitnow": {
          "flow": "qr"
        },
        "amount_refunded": 0,
        "captured": true,
        "bank": null,
        "wallet": null,
        "email": "nur.aisyah@example.com",
        "contact": "+60123456789",
        "fee": 100,
        "tax": 0,
        "error_code": null,
        "acquirer_data": {},
        "created_at": 1793078185
      }
    }
  },
  "created_at": 1793078206
}
```

```json DuitNow Pay theme={null}
{
  "entity": "event",
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "event": "payment.captured",
  "contains": [
    "payment"
  ],
  "payload": {
    "payment": {
      "entity": {
        "id": "pay_TrGnjadtYa5w0A",
        "entity": "payment",
        "amount": 10000,
        "currency": "MYR",
        "status": "captured",
        "order_id": "order_TrGnI0fFdayPhx",
        "method": "duitnow",
        "duitnow": {
          "flow": "online_banking"
        },
        "amount_refunded": 0,
        "captured": true,
        "bank": "HSBC",
        "wallet": null,
        "email": "nur.aisyah@example.com",
        "contact": "+60123456789",
        "fee": 0,
        "tax": 0,
        "error_code": null,
        "acquirer_data": {},
        "created_at": 1792741106
      }
    }
  },
  "created_at": 1792741154
}
```

### Payment Failed

```json FPX theme={null}
{
  "entity": "event",
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "event": "payment.failed",
  "contains": [
    "payment"
  ],
  "payload": {
    "payment": {
      "entity": {
        "id": "pay_DEAU825sJlCbGa",
        "entity": "payment",
        "amount": 50000,
        "currency": "MYR",
        "status": "failed",
        "order_id": "order_DEATVTRRctwEGb",
        "invoice_id": null,
        "international": false,
        "method": "fpx",
        "amount_refunded": 0,
        "refund_status": null,
        "captured": false,
        "description": null,
        "card_id": null,
        "bank": "PHBM",
        "wallet": null,
        "email": "<email>",
        "contact": "<phone>",
        "notes": [],
        "fee": null,
        "tax": null,
        "error_code": "BAD_REQUEST_ERROR",
        "error_description": "Payment failed",
        "error_source": "bank",
        "error_step": "payment_authorization",
        "error_reason": "payment_failed",
        "acquirer_data": {
          "bank_transaction_id": null
        },
        "created_at": 1567610214
      }
    }
  },
  "created_at": 1567610215
}
```

```json Card theme={null}
{
  "entity": "event",
  "account_id": "acc_E6ztBHzyaVFgBV",
  "event": "payment.failed",
  "contains": [
    "payment"
  ],
  "payload": {
    "payment": {
      "entity": {
        "id": "pay_Epiw458kREjwE8",
        "entity": "payment",
        "amount": 10000,
        "currency": "MYR",
        "status": "failed",
        "order_id": "order_EpivkSy5UXJCdW",
        "invoice_id": "inv_EpivkS3Vb7AnUD",
        "international": false,
        "method": "card",
        "amount_refunded": 0,
        "refund_status": null,
        "captured": false,
        "description": null,
        "card_id": "card_EpihqypuNkmSJX",
        "card": {
          "id": "card_DESp9fNnu0RoNc",
          "entity": "card",
          "name": "<name>",
          "last4": "0153",
          "network": "Visa",
          "type": "debit",
          "issuer": null,
          "international": false,
          "sub_type": "business"
        },
        "bank": null,
        "wallet": null,
        "email": "<email>",
        "contact": "<phone>",
        "notes": [],
        "fee": null,
        "tax": null,
        "error_code": "BAD_REQUEST_ERROR",
        "error_description": "Payment failed",
        "error_source": "gateway",
        "error_step": "payment_authorization",
        "error_reason": "payment_failed",
        "acquirer_data": {
          "auth_code": null
        },
        "created_at": 1589347206
      }
    }
  },
  "created_at": 1589347208
}
```

```json Wallets theme={null}
{
  "entity": "event",
  "account_id": "acc_E6ztBHzyaVFgBV",
  "event": "payment.failed",
  "contains": [
    "payment"
  ],
  "payload": {
    "payment": {
      "entity": {
        "id": "pay_Epiu9wz2hXBGsJ",
        "entity": "payment",
        "amount": 10000,
        "currency": "MYR",
        "status": "failed",
        "order_id": "order_Epitst92Bya4gC",
        "invoice_id": "inv_EpitssSmeINDJU",
        "international": false,
        "method": "wallet",
        "amount_refunded": 0,
        "refund_status": null,
        "captured": false,
        "description": "#inv_EpitssSmeINDJU",
        "card_id": null,
        "bank": null,
        "wallet": "touchngo",
        "email": "<email>",
        "contact": "<phone>",
        "notes": [],
        "fee": null,
        "tax": null,
        "error_code": "BAD_REQUEST_ERROR",
        "error_description": "Payment failed",
        "error_source": "issuer",
        "error_step": "payment_authorization",
        "error_reason": "payment_failed",
        "acquirer_data": {
          "transaction_id": null
        },
        "created_at": 1589347098
      }
    }
  },
  "created_at": 1589347099
}
```

> [!WARNING]
>
> **Watch Out!**
>
> The webhook sequence is not fixed in the **JSON** payload for payment events.

## Payments Downtime

Downtime is a period during which one or more payment options underperform, leading to considerable delays in payment processing. These downtimes are due to technical issues or outages at Razorpay Curlec's partner or issuing banks side. Razorpay Curlec informs you about the downtime to communicate it to your customers.

### List of Payments Downtime Webhook Events

The table below lists the webhook events available for payments downtime.

| Webhook Event | Description |
| - | - |
| `payment.downtime.started` | Triggered at the beginning of the downtime. |
| `payment.downtime.resolved` | Triggered when a downtime is resolved. |
| `payment.downtime.updated` | Triggered when a downtime is updated. |

### Payment Downtime Started

```json FPX theme={null}
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
        "method": "fpx",
        "begin": 1591935238,
        "end": null,
        "status": "started",
        "scheduled": false,
        "severity": "high",
        "instrument": {
          "bank": "PHBM"
        },
        "instrument_schema": ["bank"],
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
          "issuer": "HSBC",
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

```json FPX theme={null}
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
        "method": "fpx",
        "begin": 1583119550,
        "end": 1583119551,
        "status": "resolved",
        "scheduled": false,
        "severity": "medium",
        "instrument": {
          "bank": "PHBM"
        },
        "instrument_schema": ["bank"],
        "created_at": 1583119551,
        "updated_at": 1591948663
      }
    }
  },
  "created_at": 1591948663
}
```

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
          "issuer": "HSBC",
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

```json FPX theme={null}
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
        "method": "fpx",
        "begin": 1591935238,
        "end": null,
        "status": "updated",
        "scheduled": false,
        "severity": "high",
        "instrument": {
          "bank": "PHBM"
        },
        "instrument_schema": ["bank"],
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
          "issuer": "HSBC",
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
