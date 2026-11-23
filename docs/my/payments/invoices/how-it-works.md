> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# How Invoices Work

> Create Invoices, send them to customers to receive payments and perform other actions.

Available in
🇮🇳 India
🇲🇾 Malaysia

The following steps indicate the workflow of an Invoice:

1. [Create an Invoice](#step-1-create-an-invoice)
2. [Issue an Invoice](#step-2-issue-an-invoice)
3. [Receive Payments](#step-3-receive-payments)
4. [Track Invoices and Reports](#step-4-track-invoices-and-reports)

### Step 1: Create an Invoice

[Create an invoice](https://razorpay.com/docs/my/payments/invoices/create.md) by providing all the required details. You can set an expiry date and enable partial payments.

Save the invoice. The invoice is in `draft` status. Know more about [invoice states](https://razorpay.com/docs/my/payments/invoices/states.md).

> [!NOTE]
>
> **Handy Tips**
>
> * You can [update](https://razorpay.com/docs/my/payments/invoices/update.md), [delete](https://razorpay.com/docs/my/payments/invoices/delete.md), or [create a duplicate](https://razorpay.com/docs/my/payments/invoices/duplicate.md) of an invoice in `draft` status.
> * **Invoice APIs**:
>   * [Create an invoice](https://razorpay.com/docs/my/api/payments/invoices/create-with-customer-id.md)
>   * [Update an invoice](https://razorpay.com/docs/my/api/payments/invoices/update.md)
>   * [Delete an invoice](https://razorpay.com/docs/my/api/payments/invoices/delete.md)

### Step 2: Issue an Invoice

[Issue an invoice](https://razorpay.com/docs/my/payments/invoices/issue.md) to a customer via email and/or sms. The customer receives a notification by email or sms with a payment link using which the customer can pay using one of the available payment methods.

> [!NOTE]
>
> **Handy Tips**
>
> Use the [Issue an Invoice API](https://razorpay.com/docs/my/api/payments/invoices/issue.md).

### Step 3: Receive Payments

Customer clicks the payment link and tries to make the payment.

* The customer chooses the mode of payment: Pay Online or Pay via Bank Transfer

Customer makes a successful payment. The invoice is marked as `paid`. You receive a notification about the payment.

> [!NOTE]
>
> **Handy Tips**
>
> After the payment is captured, the amount is settled to your account as per the settlement schedule. Know more about [payments](https://razorpay.com/docs/my/payments/payments).

### Step 4: Track Invoices and Reports

* Notifications
  \
  You receive notifications regarding activity on invoices via SMS, emails and webhook. Know more about [subscribing to Webhooks](https://razorpay.com/docs/my/payments/invoices/subscribe-to-webhooks.md).
* Track Payments
  \
  Track payments made against the issued invoices on Dashboard. Click **Invoices** from the left menu. All the invoices are listed with their status under **Invoices**.
* Reports
  \
  Detailed insights can be gained using reports and real-time data on the Dashboard. These reports can then be used for accounting and reconciliation purposes. Know more about [reports](https://razorpay.com/docs/my/payments/dashboard/reports.md).

### Related Information

* [Invoices](https://razorpay.com/docs/my/payments/invoices)
* [Invoices States](https://razorpay.com/docs/my/payments/invoices/states.md)
* [Create an Invoice](https://razorpay.com/docs/my/payments/invoices/create.md)
* [Issue an Invoice](https://razorpay.com/docs/my/payments/invoices/issue.md)
* [Search an Invoice](https://razorpay.com/docs/my/payments/invoices/search.md)
* [Update an Invoice](https://razorpay.com/docs/my/payments/invoices/update.md)
* [Duplicate an Invoice](https://razorpay.com/docs/my/payments/invoices/duplicate.md)
* [Delete an Invoice](https://razorpay.com/docs/my/payments/invoices/delete.md)
* [Cancel an Invoice](https://razorpay.com/docs/my/payments/invoices/cancel.md)
* [Download and Print an Invoice](https://razorpay.com/docs/my/payments/invoices/download-print.md)
* [Subscribe to Webhooks](https://razorpay.com/docs/my/payments/invoices/subscribe-to-webhooks.md)
* [Invoice APIs](https://razorpay.com/docs/my/payments/invoices/apis.md)
