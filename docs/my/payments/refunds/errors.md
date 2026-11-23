> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Handle Refund Errors

> Check the errors that may occur while processing Refunds and how to handle these errors.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Sometimes when you try to process a refund request, it fails to get processed and you may encounter `BAD_REQUEST_ERROR` messages stating refunds are not supported. This happens because most of the banks do not support refunds for payments that are more than 6 months old.

## List of Possible Refund Errors

Given below is a refund error example.

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

To check the refund status, navigate to the **Refund Details** pop-up by clicking on the specific **Refund Id** under the **Transactions** → **Refunds** tab.

You can get the  successfully processed refunds under the [Dashboard Refunds tab](https://razorpay.com/docs/my/payments/refunds/view.md) or using the [Fetch Refund API](https://razorpay.com/docs/my/api/refunds/fetch-with-id.md). This is a unique reference number which can be used by the customers to track refunds.

### Related Information

<ul>
  <li>[About Refunds](https://razorpay.com/docs/my/payments/refunds)</li>
  <li>[Normal Refunds](https://razorpay.com/docs/my/payments/refunds/normal.md)</li>

  <li>Batch Refund</li>
  <li>[Refunds FAQs](https://razorpay.com/docs/my/payments/refunds/faqs.md)</li>
</ul>
