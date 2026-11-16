> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# How QR Codes Work

> Create and share QR Codes to receive payments. Track payments and generate reports.

Available in
🇮🇳 India

Given below is a complete end-to-end flow about how you can use QR Codes to accept payments.

![QR Codes Flow](https://razorpay.com/docs/build/browser/assets/images/qr-codes-flow.jpg)

## QR Codes Workflow

To accept payments using Razorpay QR Codes:

> [card] [1. Create a QR Code](https://razorpay.com/docs/payments/qr-codes/how-it-works.md#1-create-a-qr-code)
>
> Create a QR Code that you can share with your customers to accept payments.

> [card] [2. Share the QR Code](https://razorpay.com/docs/payments/qr-codes/how-it-works.md#2-share-the-qr-code)
>
> Print or download the QR Code to share with your customers to accept payments.

> [card] [3. Receive Payments](https://razorpay.com/docs/payments/qr-codes/how-it-works.md#3-receive-payments)
>
> Receive payments after your customer scans the QR Codes and makes payments.

> [card] [4. Track QR Code Payments and Reports](https://razorpay.com/docs/payments/qr-codes/how-it-works.md#4-track-qr-code-payments-and-reports)
>
> Receive notifications, check payments and view reports for QR Code payments.

### 1. Create a QR Code

[Create a QR Code](https://razorpay.com/docs/payments/qr-codes/create.md) by providing all the required details. You can set a close by date and enable multiple payments.

The QR Code is in `active` status. Know more about [QR Code states](https://razorpay.com/docs/payments/qr-codes/states.md).

> [!NOTE]
>
> **Handy Tips**
>
> You can close a QR Code from the [Dashboard](https://razorpay.com/docs/payments/qr-codes/close.md) or with the [Close a QR Code API](https://razorpay.com/docs/api/qr-codes/close.md).

### 2. Share the QR Code

Print and download the QR Code to share it with the customers. Customers can scan the code and complete the payment using their preferred UPI PSP apps. Check the [supported UPI apps](https://razorpay.com/docs/payments/payment-methods#supported-upi-apps).

### 3. Receive Payments

Customer scans the QR Code with their UPI PSP app and completes the payment. They can make multiple payments if the option was enabled at the time of QR creation. You receive a notification about the payment.

> [!NOTE]
>
> **Handy Tips**
>
> After the payment is captured, the amount is settled to your account as per the settlement schedule. Know more about [payments](https://razorpay.com/docs/payments/payments), [settlements](https://razorpay.com/docs/payments/settlements), [refunds](https://razorpay.com/docs/payments/refunds) and [disputes](https://razorpay.com/docs/payments/disputes).

### 4. Track QR Code Payments and Reports

* Notifications: Receive notifications regarding activity on QR Code via email and webhooks. Know more about [subscribing to QR Code webhooks](https://razorpay.com/docs/payments/qr-codes/subscribe-to-webhooks.md).
* Track Payments: Track payments made using the QR Code on the Dashboard. Click **QR Codes** from the left menu and select **Payments**. All the payments received on your QR Codes are listed with their status.
* Reports: Gain detailed insights using reports and real-time data on the Dashboard. These reports can then be used for accounting and reconciliation purposes. Know more about [reports](https://razorpay.com/docs/payments/dashboard/reports.md).

### Related Information

* [QR Codes](https://razorpay.com/docs/payments/qr-codes)
* [QR Codes States](https://razorpay.com/docs/payments/qr-codes/states.md)
* [Create a QR Code](https://razorpay.com/docs/payments/qr-codes/create.md)
* [Subscribe to QR Code Webhooks](https://razorpay.com/docs/payments/qr-codes/subscribe-to-webhooks.md)
* [QR Codes APIs](https://razorpay.com/docs/payments/qr-codes/apis.md)
