> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Orders

> Create, view and update an Order using Razorpay APIs.

Available in
🇮🇳 India

You can create [Orders](https://razorpay.com/docs/payments/orders) and link them to payments. Orders APIs are used to create, update and retrieve details of Orders. Also, you can retrieve details of payments made towards these Orders.

Fork the Razorpay Postman Public Workspace and try the Orders APIs using your [Test API Keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-91450029-1c52-4375-8033-39ca4c2d0a8c)

> [card] [Create an Order](https://razorpay.com/docs/api/orders/create.md)
>
> `POST` `/v1/orders`
>
> Creates an order by providing basic details such as amount and currency.

> [card] [Fetch All Orders](https://razorpay.com/docs/api/orders/fetch-all.md)
>
> `GET` `/v1/orders`
>
> Retrieves details of all the orders.

> [card] [Fetch All Orders (Example 1)](https://razorpay.com/docs/api/orders/fetch-all-expanded-payments.md)
>
> `GET` `/v1/orders?expand[]=payments`
>
> Retrieves details of all the orders and expands the payments object.

> [card] [Fetch All Orders (Example 2)](https://razorpay.com/docs/api/orders/fetch-all-expanded-card-payments.md)
>
> `GET` `/v1/orders?expand[]=payments.card`
>
> Retrieves details of all the orders and expands cards parameter in the payments object.

> [card] [Fetch Order With ID](https://razorpay.com/docs/api/orders/fetch-with-id.md)
>
> `GET` `/v1/orders/:id`
>
> Retrieves details of a particular order.

> [card] [Fetch All Payments for an Order](https://razorpay.com/docs/api/orders/fetch-payments.md)
>
> `GET` `/v1/orders/:id/payments`
>
> Retrieves all the payments made for an order.

> [card] [Update an Order](https://razorpay.com/docs/api/orders/update.md)
>
> `PATCH` `/v1/orders/:id`
>
> Modifies an existing order.

## Related Guides

* [About Orders](https://razorpay.com/docs/payments/orders)
* [Set Up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payments.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/orders.md)
