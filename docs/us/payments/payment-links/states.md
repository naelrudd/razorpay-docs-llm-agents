> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payment Link States

> List of states of a Razorpay Payment Link and their significance.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

A Payment Link starts in the `issued` state and moves through several states in its life cycle.

## Standard Payment Links

After a Standard Payment Link is created, you can track its status on your Dashboard on the Payment Link page. The diagram given below illustrates the life cycle of a Payment Link.

![Standard Payment Link States](https://razorpay.com/docs/build/browser/assets/images/payment-links-standard-link-cycle.jpg)

The table below lists the various states and their descriptions in the Payment Link life cycle:

| Status | Description | Next Steps |
| - | - | - |
| Created | Indicates that the Payment Link has been created. Know more about [creating a Payment Link](https://razorpay.com/docs/us/payments/payment-links/create.md#create-a-standard-payment-link-from-dashboard). | Start accepting payments by sending the Payment Link to the customers. |
| Partially Paid | Indicates that the customer has made a partial payment against the Payment Link. Know more about [enabling partial payments for Payment Links.](https://razorpay.com/docs/us/payments/payment-links/partial-payments.md) | Send a reminder to the customer to pay the next instalment. Know more about [sending reminders.](https://razorpay.com/docs/us/payments/payment-links/reminders.md) |
| Paid | Indicates that the Payment Link has been paid in full. | NA |
| Cancelled | Indicates that you have cancelled the Payment Link. Know more about [cancelling Payment Links.](https://razorpay.com/docs/us/payments/payment-links/cancel.md) | Customers can no longer pay using this Payment Link. Create a new Payment Link to start accepting payments (if required). |
| Expired | Indicates that the Payment Link has expired. You can set the expiry date and time while creating the Payment Link. Know more about [creating a Payment Link.](https://razorpay.com/docs/us/payments/payment-links/create.md#create-a-standard-payment-link-from-dashboard) | This link is no longer accessible to the customers. Create a new Payment Link to start accepting payments (If required). |

> [!NOTE]
>
> **Handy Tips**
>
> * You cannot delete a Payment Link. However, you can cancel it. Know more about [cancelling Payment Links](https://razorpay.com/docs/us/payments/payment-links/cancel.md).
> * You can cancel a Payment Link only if it is in the `issued` state. You cannot cancel Payment Links in the `partially_paid` or `paid` state.

#### Related Information

<ul>
  <li>[How Payment Links Work](https://razorpay.com/docs/us/payments/payment-links/how-it-works.md)</li>
  <li>[Create a Payment Link](https://razorpay.com/docs/us/payments/payment-links/create.md)</li>
  <li>[FAQs](https://razorpay.com/docs/us/payments/payment-links/faqs.md)</li>
  <li>[Payment Links APIs](https://razorpay.com/docs/us/payments/payment-links/apis.md)</li>
</ul>
