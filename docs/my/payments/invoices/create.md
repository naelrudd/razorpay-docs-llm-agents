> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create an Invoice

> Create and save an Invoice.

Available in
🇮🇳 India
🇲🇾 Malaysia

An Invoice is a digital document that summarises the details of an order or a transaction and allows customers to initiate payments. A typical invoice contains sale transaction information such as the name of the ordered products or services, quantities, price breakup, receipt number, customer information and so on.

## Create an Invoice From Dashboard

To create an invoice:

1. Log in to the Dashboard.
2. Click **Invoices** → **+Create Invoice**.
3. A new invoice draft is displayed with your company name and logo.
4. Enter a unique **Invoice #**. Provide a brief description or summary of the invoice.
5. Under the **BILLING TO** field, select a customer by searching from the list of existing customers. You can also [create a new customer while creating an invoice](#create-a-new-customer-while-creating-invoice)
6. Enter the **ISSUE DATE** of the invoice. By default, it takes today's date. Use the calendar icon if you want to select a different date as Issue Date.
7. Click the calendar icon to select the **EXPIRY DATE** of the invoice.
   The Expiry Date is the date after which the customer cannot pay for the invoice. You can keep this field blank, in such a case, there will not be any Expiry Date for the invoice. You cannot select an Expiry Date in past.
8. Under **BILLING ADDRESS**, the Billing Address as specified for the selected customer is displayed. You can change or remove this address and add a new address.
9. Under **SHIPPING ADDRESS**, click **Add Shipping Address**. The Shipping Address that was added while creating the customer is displayed. You can select the existing Shipping Address or click **Add new Address** to add a new Shipping Address. The newly added address is added to the list of saved Shipping Addresses for the customer.
10. Enter the **PLACE OF SUPPLY**. The place of supply is auto-populated based on the shipping address.
11. Under **DESCRIPTION**, select an item, add the rate/item and the quantity. Click **Add Line Item** to add multiple items to the invoice. You can also [create a new item while creating an invoice](#create-a-new-item-while-creating-invoice)
12. In the **Add Customer Notes (Optional)** field, you can enter additional details, if any. You can add a maximum of 2048 characters in this field.
13. In the **Add Terms and Conditions (Optional)** field, you can add terms, if any. You can add a maximum of 2048 characters in this field.
14. Select **Enable Partial Payments** to accept multiple payments for the invoice.
15. Click **Save Invoice** to save the invoice as `draft`. You can also click **Finalize and Issue** to save the invoice and `issue` it to the selected customer.

Click **All Invoices** on the top ribbon to view the newly created invoice in the list of all the invoices. Know more about [invoice states](https://razorpay.com/docs/my/payments/invoices/states.md).

### Create a New Customer While Creating Invoice

You can also create a customer while creating an invoice. Click **+Create New Customer** which opens up a pop-up page.

1. Specify details of the customer, such as **Company/Individual Name**, **Email** and **Contact No.**.
2. Select the **Billing Address** check box to specify the Billing Address.
3. Next, specify the Shipping Address. If the Shipping Address is the same as Billing Address, select the **Same as Billing Address** check box.
4. Click **Create Customer**.

The details of the newly created customer are auto-populated on the invoice draft. You can also click **Edit Customer** to make changes to the customer details. This customer will now be available to you for creating more invoices for this customer in future. This customer name is also displayed under the **Customers** menu.

Know more about [customers](https://razorpay.com/docs/my/payments/customers).

### Create a New Item While Creating Invoice

You can also create a new item while creating an invoice. Click **+Create new Item** on the draft invoice which opens up a pop-up page. Specify details of the item, such as **Name**, **Rate per unit** and **Description**.

> [!WARNING]
>
> **Watch Out!**
>
> When an item's attributes are modified while creating an invoice, the modified item cannot be reused. The item will then be referred as a **Line item**. In other words, a **Line Item** is created when an **Item** is used as a template, in order to customise its attributes.

## Create an Invoice Using API

You can create an invoice for the items ordered on your website or app by a customer using
[this](https://razorpay.com/docs/my/api/payments/invoices/create-with-customer-id.md) API.

## What Next

If you have saved the invoice as `draft`, you should next [issue it](https://razorpay.com/docs/my/payments/invoices/issue.md) to the selected customer to receive payments. You can also choose to do any one of the following actions:\


* [Update invoice](https://razorpay.com/docs/my/payments/invoices/update.md)
* [Duplicate invoice](https://razorpay.com/docs/my/payments/invoices/duplicate.md)
* [Delete invoice](https://razorpay.com/docs/my/payments/invoices/delete.md)

### Related information

* [Invoices](https://razorpay.com/docs/my/payments/invoices)
* [Invoice States](https://razorpay.com/docs/my/payments/invoices/states.md)
* [How Invoices Work](https://razorpay.com/docs/my/payments/invoices/how-it-works.md)
* [Download or Print an Invoice](https://razorpay.com/docs/my/payments/invoices/download-print.md)
* [Update an Invoice](https://razorpay.com/docs/my/payments/invoices/update.md)
* [Issue an Invoice](https://razorpay.com/docs/my/payments/invoices/issue.md)
* [Search an Invoice](https://razorpay.com/docs/my/payments/invoices/search.md)
* [Duplicate an Invoice](https://razorpay.com/docs/my/payments/invoices/duplicate.md)
* [Cancel an Invoice](https://razorpay.com/docs/my/payments/invoices/cancel.md)
* [Delete an Invoice](https://razorpay.com/docs/my/payments/invoices/delete.md)
