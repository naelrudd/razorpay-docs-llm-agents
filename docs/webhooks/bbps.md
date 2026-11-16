> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Bill Payments (BBPS) Webhook Events

> List of Bill Payments (BBPS) webhook events along with sample payloads.

Available in
🇮🇳 India

Razorpay's [Bill Payments (BBPS)](https://razorpay.com/docs/api/bills/bill-payments.md) APIs are asynchronous. By subscribing to Bill Payments webhook events, you get notified when a bill request or a bill payment reaches a terminal state (`success` or `failed`), instead of continuously polling the corresponding Fetch API.

## List of Bill Payments Webhook Events

The table below lists the webhook events available for Bill Payments.

| Webhook Event | Description |
| - | - |
| `bill_payment.bill_request.success` | Triggered when a bill request is successfully completed and the bill amount is retrieved from the biller. |
| `bill_payment.bill_request.failed` | Triggered when a bill request fails. |
| `bill_payment.payment.success` | Triggered when a bill payment is successful. |
| `bill_payment.payment.failed` | Triggered when a bill payment fails. |

> [!NOTE]
>
> **Handy Tips**
>
> The payload for a webhook is a snapshot of the entity when the event occurred. The `contains` array names the entity present in the `payload` object (`bill_request` or `bill_payment`).

## Sample Payloads

Given below are the sample payloads for Bill Payments webhook events.

### Bill Request Success

Triggered when a bill request is successfully completed and the bill amount is retrieved from the biller.

```json bill_payment.bill_request.success theme={null}
{
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "entity": "event",
  "event": "bill_payment.bill_request.success",
  "contains": [
    "bill_request"
  ],
  "created_at": 1691735748,
  "payload": {
    "bill_request": {
      "entity": {
        "id": "billreq_ERNEungCtXpZqM",
        "entity": "bill_payment.bill_request",
        "status": "success",
        "biller_id": "rzp_blr_123",
        "gateway_biller_id": "VODA00000MUM03",
        "created_at": 1691735700,
        "updated_at": 1691735748,
        "expiry_at": 1691736300,
        "customer": {
          "id": "rzp_cust_123",
          "name": "Gaurav Kumar",
          "mobile": "919000090000",
          "email": "gaurav.kumar@example.com"
        },
        "account_holder": {
          "account_holder_name": "Gaurav Kumar",
          "account_number": "XXXXXXX"
        },
        "bills": [
          {
            "bill_number": "1232332",
            "amount": 120000,
            "currency": "INR",
            "bill_date": 1688169600,
            "due_date": 1690848000,
            "bill_period": "monthly",
            "amount_details": {
              "min_amount_due": 12000,
              "current_outstanding_amount": 120000
            }
          }
        ],
        "data": {
          "registered_email": "gaurav.kumar@example.com"
        }
      }
    }
  }
}
```

> [!NOTE]
>
> **Handy Tips**
>
> For validate-only billers, `bills` is returned as an empty array (`[]`).

### Bill Request Failed

Triggered when a bill request fails.

```json bill_payment.bill_request.failed theme={null}
{
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "entity": "event",
  "event": "bill_payment.bill_request.failed",
  "contains": [
    "bill_request"
  ],
  "created_at": 1691735800,
  "payload": {
    "bill_request": {
      "entity": {
        "id": "billreq_ERNEungCtXpZqM",
        "entity": "bill_payment.bill_request",
        "status": "failed",
        "biller_id": "rzp_blr_123",
        "gateway_biller_id": "VODA00000MUM03",
        "created_at": 1691735700,
        "updated_at": 1691735800,
        "customer": {
          "id": "rzp_cust_123",
          "name": "Gaurav Kumar",
          "mobile": "919000090000",
          "email": "gaurav.kumar@example.com"
        },
        "error": {
          "code": "GATEWAY_ERROR",
          "description": "Bill fetch failed. Customer account not found at biller.",
          "source": "biller",
          "step": "bill_request",
          "reason": "customer_not_found",
          "metadata": {
            "bill_request_id": "billreq_ERNEungCtXpZqM",
            "payment_id": "rzp_paymentid",
            "gateway_error_code": "BRR005",
            "gateway_error_description": "customer account not found at biller"
          }
        }
      }
    }
  }
}
```

> [!WARNING]
>
> **Watch Out!**
>
> `expiry_at` is not present on failed bill request events.

### Bill Payment Success

Triggered when a bill payment is successful.

```json bill_payment.payment.success theme={null}
{
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "entity": "event",
  "event": "bill_payment.payment.success",
  "contains": [
    "bill_payment"
  ],
  "created_at": 1691735900,
  "payload": {
    "bill_payment": {
      "entity": {
        "id": "bill_pay_ERNEungCtXpZqM",
        "entity": "bill_payment.payment",
        "status": "success",
        "biller_id": "rzp_blr_123",
        "gateway_biller_id": "VODA00000MUM03",
        "gateway": "bbps",
        "gateway_transaction_id": "BBPS0012345678901234",
        "biller_transaction_id": "AB123456",
        "created_at": 1691735820,
        "updated_at": 1691735900,
        "bill_pay_amount": 120000,
        "currency": "INR",
        "fees": {
          "app_convenience_fee": 1000,
          "biller_convenience_fee": 500
        },
        "customer": {
          "id": "rzp_cust_123",
          "name": "Gaurav Kumar",
          "mobile": "919000090000",
          "email": "gaurav.kumar@example.com"
        },
        "payment": [
          {
            "id": "rzp_pay_1234",
            "status": "authorized",
            "provider": "razorpay",
            "amount": 72000,
            "currency": "INR",
            "method": "card"
          },
          {
            "id": "rzp_pay_5678",
            "status": "authorized",
            "provider": "razorpay",
            "amount": 48000,
            "currency": "INR",
            "method": "upi"
          }
        ],
        "account_holder": {
          "account_number": "XXXXXXX"
        },
        "bills": [
          {
            "bill_number": "12345",
            "amount": 120000,
            "currency": "INR",
            "bill_date": 1688169600,
            "due_date": 1690848000,
            "bill_period": "monthly"
          }
        ],
        "data": {
          "mobile_number": "9999999999"
        }
      }
    }
  }
}
```

### Bill Payment Failed

Triggered when a bill payment fails.

```json bill_payment.payment.failed theme={null}
{
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "entity": "event",
  "event": "bill_payment.payment.failed",
  "contains": [
    "bill_payment"
  ],
  "created_at": 1691735900,
  "payload": {
    "bill_payment": {
      "entity": {
        "id": "bill_pay_ERNEungCtXpZqM",
        "entity": "bill_payment.payment",
        "status": "failed",
        "biller_id": "rzp_blr_123",
        "gateway_biller_id": "VODA00000MUM03",
        "gateway": "bbps",
        "gateway_transaction_id": "BBPS0012345678901234",
        "created_at": 1691735820,
        "updated_at": 1691735900,
        "bill_pay_amount": 120000,
        "currency": "INR",
        "fees": {
          "app_convenience_fee": 1000,
          "biller_convenience_fee": 500
        },
        "customer": {
          "id": "rzp_cust_123",
          "name": "Gaurav Kumar",
          "mobile": "919000090000",
          "email": "gaurav.kumar@example.com"
        },
        "payment": [
          {
            "id": "rzp_pay_1234",
            "status": "authorized",
            "provider": "razorpay",
            "amount": 72000,
            "currency": "INR",
            "method": "card"
          },
          {
            "id": "rzp_pay_5678",
            "status": "authorized",
            "provider": "razorpay",
            "amount": 48000,
            "currency": "INR",
            "method": "upi"
          }
        ],
        "account_holder": {
          "account_number": "XXXXXXX"
        },
        "bills": [
          {
            "bill_number": "12345",
            "amount": 120000,
            "currency": "INR",
            "bill_date": 1688169600,
            "due_date": 1690848000,
            "bill_period": "monthly"
          }
        ],
        "error": {
          "code": "GATEWAY_ERROR",
          "description": "Bill payment failed. Biller is not accepting payments at the moment.",
          "source": "biller",
          "step": "bill_payment",
          "reason": "biller_not_accepting_payments",
          "metadata": {
            "bill_payment_id": "bill_pay_ERNEungCtXpZqM",
            "payment_ids": [
              "rzp_pay_1234",
              "rzp_pay_5678"
            ],
            "gateway_error_code": "BRR005",
            "gateway_error_description": "biller is not accepting payments at the moment"
          }
        }
      }
    }
  }
}
```

> [!WARNING]
>
> **Watch Out!**
>
> On failed bill payment events:
>
> * `gateway_transaction_id` is present only if NPCI assigned a transaction id before the failure. It may be absent.
> * `biller_transaction_id` is never present.
> * `data` is not present, as no biller response metadata is available when the payment fails.

> [!WARNING]
>
> **Watch Out!**
>
> * If you have changed your webhook secret, remember to use the old secret for webhook signature validation while retrying older requests. Using the new secret will lead to a signature mismatch.
>
> * While generating a signature at your end, ensure that the webhook body is passed as an argument in the **raw webhook request body**. **Do not parse or cast the webhook request body**.
