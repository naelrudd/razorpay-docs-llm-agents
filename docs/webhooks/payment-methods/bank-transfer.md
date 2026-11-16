> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Bank Transfer or ECMS Webhook Events

> List of Bank Transfer (ECMS) webhook events for HDFC Collect Now along with the sample payload.

**Bank Transfer or ECMS** lets your customers pay into a virtual account through their Netbanking/Mobile Banking portal or by visiting a bank branch and paying against an ECMS challan. Each successful credit triggers the `virtual_account.credited` webhook event.

## List of Webhook Events

The table below lists the webhook event available for Bank Transfer or ECMS.

| Webhook Event | Description |
| - | - |
| `virtual_account.credited` | Triggered when a payment is made to a virtual account using Bank Transfer or ECMS. |

## Sample Payload

### Virtual Account Credited

Given below is the sample payload for the `virtual_account.credited` event when the payment is received using Bank Transfer or ECMS.

```json virtual_account.credited theme={null}
{
  "entity": "event",
  "account_id": "acc_BFQ7uQEaa7j2z7",
  "event": "virtual_account.credited",
  "contains": [
    "payment",
    "virtual_account",
    "bank_transfer"
  ],
  "payload": {
    "payment": {
      "entity": {
        "id": "pay_ECMS2KrOlhqQzF",
        "entity": "payment",
        "amount": 50000,
        "currency": "INR",
        "status": "captured",
        "order_id": null,
        "invoice_id": null,
        "international": false,
        "method": "bank_transfer",
        "amount_refunded": 0,
        "amount_transferred": 0,
        "refund_status": null,
        "captured": true,
        "description": "NA",
        "card_id": null,
        "bank": null,
        "wallet": null,
        "vpa": null,
        "email": "gaurav.kumar@example.com",
        "contact": "+919000090000",
        "customer_id": "cust_BtQNqzmBlAXyTY",
        "notes": [],
        "fee": 590,
        "tax": 90,
        "error_code": null,
        "error_description": null,
        "created_at": 1567675983
      }
    },
    "virtual_account": {
      "entity": {
        "id": "va_DET8z3wBxfPB5L",
        "name": "Acme Corp",
        "entity": "virtual_account",
        "status": "active",
        "description": "Virtual Account to test webhook",
        "amount_expected": null,
        "notes": {
          "Important": "Notes for Internal Reference"
        },
        "amount_paid": 50000,
        "customer_id": "cust_BtQNqzmBlAXyTY",
        "close_by": null,
        "closed_at": null,
        "created_at": 1567675923,
        "receivers": [
          {
            "id": "ba_DET8z5Z5ghv4hW",
            "entity": "bank_account",
            "ifsc": "RATN0VAAPIS",
            "bank_name": "RBL Bank",
            "name": "Acme Corp",
            "account_number": "1112220006712324"
          }
        ]
      }
    },
    "bank_transfer": {
      "entity": {
        "id": "bt_ECMS2KSUJ3uCM9",
        "entity": "bank_transfer",
        "payment_id": "pay_ECMS2KrOlhqQzF",
        "mode": "ECMS",
        "bank_reference": "156767598341",
        "amount": 50000,
        "payer_bank_account": {
          "id": "ba_ECMS2UuuKtKLR1",
          "entity": "bank_account",
          "ifsc": "KKBK0000007",
          "bank_name": "Kotak Mahindra Bank",
          "name": "Gaurav Kumar",
          "account_number": "765432123456789"
        },
        "virtual_account_id": "va_DET8z3wBxfPB5L"
      }
    }
  },
  "created_at": 1567675983
}
```
