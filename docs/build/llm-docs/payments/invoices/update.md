# Update an Invoice

You can only update a `draft` invoice. Know more about [invoice states](https://razorpay.com/docs/build/llm-docs/payments/invoices/states.md).

## Update an Invoice From Dashboard

Watch this video to see how to update an invoice.

To update an invoice:
1. Log in to the Dashboard.
1. Click on **Invoices**.
1. Search for the **Draft** invoice that you want to update using the [search criteria](https://razorpay.com/docs/build/llm-docs/payments/invoices/search.md).
1. Select the **Invoice Id**.
1. The following information can be edited:
    - Customer details
    - Description
    - Expiry date of the invoice
    - Notes
    - Billing Address
    - Shipping Address
    - Partial payments
    - Label
1. Click **Save Invoice**.

**WARN**

**Watch Out!**

When an item's attributes are modified at the time of invoice creation, the modified item cannot be reused. The item will then be referred as a **Line item**. In other words, a **Line Item** is created when an **Item** is used as a template, in order to customise its attributes.

The invoice now displays the updated details.

## Update an Invoice Using API
You can update a `draft` invoice using [this](https://razorpay.com/docs/build/llm-docs/api/payments/invoices.md#update-an-invoice) API.

### Related Information
- [Invoices](https://razorpay.com/docs/build/llm-docs/payments/invoices.md)
- [Invoices States](https://razorpay.com/docs/build/llm-docs/payments/invoices/states.md)
- [How Invoices Work](https://razorpay.com/docs/build/llm-docs/payments/invoices/how-it-works.md)
- [Create an Invoice](https://razorpay.com/docs/build/llm-docs/payments/invoices/create.md)
- [Issue an Invoice](https://razorpay.com/docs/build/llm-docs/payments/invoices/issue.md)
- [Search an Invoice](https://razorpay.com/docs/build/llm-docs/payments/invoices/search.md)
- [Duplicate an Invoice](https://razorpay.com/docs/build/llm-docs/payments/invoices/duplicate.md)
- [Delete an Invoice](https://razorpay.com/docs/build/llm-docs/payments/invoices/delete.md)
- [Cancel an Invoice](https://razorpay.com/docs/build/llm-docs/payments/invoices/cancel.md)
- [Invoice APIs](https://razorpay.com/docs/build/llm-docs/payments/invoices/apis.md)
- [Download and Print an Invoice](https://razorpay.com/docs/build/llm-docs/payments/invoices/download-print.md)
