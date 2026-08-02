# Payment Link States

A Payment Link starts in the `issued` state and moves through several states in its life cycle. The life cycle differs for [Standard](#standard-payment-links) and [UPI](#upi-payment-links) Payment Links.

## Standard Payment Links

After a Standard Payment Link is created, you can track its status on your Dashboard on the Payment Link page. The diagram given below illustrates the life cycle of a Payment Link.

The table below lists the various states and their descriptions in the Payment Link life cycle:

Status | Description | Next Steps
---
Created | Indicates that the Payment Link has been created. Know more about [creating a Payment Link](https://razorpay.com/docs/build/llm-docs/payments/payment-links/create.md#create-a-standard-payment-link). | Start accepting payments by sending the Payment Link to the customers. 
---
Partially Paid | Indicates that the customer has made a partial payment against the Payment Link. Know more about [enabling partial payments for Payment Links.](https://razorpay.com/docs/build/llm-docs/payments/payment-links/partial-payments.md) | Send a reminder to the customer to pay the next instalment. Know more about [sending reminders.](https://razorpay.com/docs/build/llm-docs/payments/payment-links/reminders.md)
---
Paid | Indicates that the Payment Link has been paid in full. | NA
---
Cancelled | Indicates that you have cancelled the Payment Link. Know more about [cancelling Payment Links.](https://razorpay.com/docs/build/llm-docs/payments/payment-links/cancel.md)| Customers can no longer pay using this Payment Link. Create a new Payment Link to start accepting payments (if required).
---
Expired | Indicates that the Payment Link has expired. You can set the expiry date and time while creating the Payment Link. Know more about [creating a Payment Link.](https://razorpay.com/docs/build/llm-docs/payments/payment-links/create.md#create-a-standard-payment-link) | This link is no longer accessible to the customers. Create a new Payment Link to start accepting payments (If required).

**Handy Tips**

- You cannot delete a Payment Link. However, you can cancel it. Know more about [cancelling Payment Links](https://razorpay.com/docs/build/llm-docs/payments/payment-links/cancel.md).
- You can cancel a Payment Link only if it is in the `issued` state. You cannot cancel Payment Links in the `partially_paid` or `paid` state.

## UPI Payment Links

After you create a UPI Payment Link, you can track its status on your Dashboard on the **Payment Links** page. The diagram given below illustrates the life cycle of a UPI Payment Link.

The table below lists the various states and their descriptions in the UPI Payment Link life cycle:

Status | Description | Next Steps
---
Created | Indicates that the Payment Link has been created. Know more about [creating a UPI Payment Link](https://razorpay.com/docs/build/llm-docs/payments/payment-links/create.md#create-a-standard-payment-link-from-dashboard). | Start accepting payments by sending the Payment Link to the customers.
---
Paid | Indicates that the Payment Link has been paid in full. | NA
---
Cancelled | Indicates that you have cancelled the Payment Link. Know more about [cancelling Payment Links](https://razorpay.com/docs/build/llm-docs/payments/payment-links/cancel.md). | Customers can no longer pay using this Payment Link. Create a new Payment Link to start accepting payments (If required).
---
Expired | The payment link has expired. You can set the expiry date and time while creating the payment link. Know more about [creating a UPI Payment Link](https://razorpay.com/docs/build/llm-docs/payments/payment-links/create.md#create-a-upi-payment-link).| This link is no longer accessible to the customers. Create a new Payment Link to start accepting payments (if required).

**INFO**

**Partial Payments Not Supported**

UPI Payment Links do not support partial payments. Hence, the `partially_paid` state does not exist.

#### Related Information

- [How Payment Links Work](https://razorpay.com/docs/build/llm-docs/payments/payment-links/how-it-works.md)

- [Create a Payment Link](https://razorpay.com/docs/build/llm-docs/payments/payment-links/create.md)

- [FAQs](https://razorpay.com/docs/build/llm-docs/payments/payment-links/faqs.md)

- [Payment Links APIs](https://razorpay.com/docs/build/llm-docs/payments/payment-links/apis.md)
