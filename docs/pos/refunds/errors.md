> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Handle Refund Errors

> Check the errors that may occur while processing Refunds and how to handle these errors.

Available in
🇮🇳 India

Sometimes when you try to process a refund request, it fails to get processed and you may encounter `BAD_REQUEST_ERROR` messages stating refunds are not supported. This happens because most of the banks do not support refunds for payments that are more than 6 months old.

## List of Possible Refund Errors

```json Error Response theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "Refund is not supported by the bank because the payment is more than 6 months old",
    "source": null,
    "step": null,
    "reason": null,
    "metadata": {}
  }
}
```

```json Error Response theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "Payment is more than 6 months old, only instant refund is supported",
    "source": null,
    "step": null,
    "reason": null,
    "metadata": {}
  }
}
```

You may also encounter the following refund errors:

```json Error Response theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "The refund amount provided is greater than amount captured",
    "source": null,
    "step": null,
    "reason": null,
    "metadata": {}
  }
}
```

```json Error Response theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "The payment has been fully refunded already",
    "source": null,
    "step": null,
    "reason": null,
    "metadata": {}
  }
}
```

```json Error Response theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "The total refund amount is greater than the refund payment amount",
    "source": null,
    "step": null,
    "reason": null,
    "metadata": {}
  }
}
```

To check the refund status, navigate to the **Refund Details** pop-up by clicking on the specific **Refund Id** under the **Transactions** → **Refunds** tab.

You can get the ARN/RRN for successfully processed refunds under the [Dashboard Refunds tab](https://razorpay.com/docs/payments/refunds/view.md) or using the [Fetch Refund API](https://razorpay.com/docs/api/refunds/fetch-with-id.md). This is a unique reference number that can be used by customers to track refunds.

## Void Errors

A [void](https://razorpay.com/docs/pos/refunds#void) request can also fail. The most common void error is:

```json Error Response theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "Void is not supported for partial refunds",
    "source": null,
    "step": null,
    "reason": null,
    "metadata": {}
  }
}
```

This error occurs because a void can only be issued for the full transaction amount, before the payment is settled to your account. Issue a [refund](https://razorpay.com/docs/pos/refunds) instead if you need to return only part of the amount, or if the payment is already settled.

### Related Information

* [About Refunds](https://razorpay.com/docs/pos/refunds)
* [Normal Refunds](https://razorpay.com/docs/pos/refunds/normal.md)
* [Refunds FAQs](https://razorpay.com/docs/pos/refunds/faqs.md)
