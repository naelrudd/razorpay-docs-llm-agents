> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Disputes

> List of Dispute APIs available to perform various actions.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

A [dispute](https://razorpay.com/docs/payments/disputes) arises when your customer or the issuing bank questions the validity of a payment. You can manage disputes using APIs or from the [Dashboard](https://razorpay.com/docs/payments/disputes#dashboard-actions) to ensure a seamless dispute management experience.\
\


Fork the Razorpay Postman Public Workspace and try the Disputes APIs using your [Test API Keys](https://razorpay.com/docs/api/authentication.md#generate-api-keys).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-0803d1d0-dbdf-4312-bd7b-b4817cea2840)

> [card] [Fetch All Disputes](https://razorpay.com/docs/api/disputes/fetch-all.md)
>
> `GET` `/v1/disputes`
>
> Retrieves information about all disputes.

> [card] [Fetch a Dispute With ID](https://razorpay.com/docs/api/disputes/fetch.md)
>
> `GET` `/v1/disputes/:id`
>
> Retrieves details for a specific dispute using the unique identifier linked to the dispute.

> [card] [Fetch a Dispute With ID (Example 1)](https://razorpay.com/docs/api/disputes/fetch-dispute-expanded-payment.md)
>
> `GET` `/v1/disputes/:id?expand[]=payment`
>
> Retrieves details for a specific dispute with expanded payment details.

> [card] [Fetch a Dispute With ID (Example 2)](https://razorpay.com/docs/api/disputes/fetch-dispute-expanded-transaction.md)
>
> `GET` `/v1/disputes/:id?expand[]=transaction.settlement`
>
> Retrieves details for a specific dispute with expanded `transaction.settlement` details.

> [card] [Accept a Dispute](https://razorpay.com/docs/api/disputes/accept.md)
>
> `POST` `/v1/disputes/:id/accept`
>
> Accepts a dispute against the payment.

> [card] [Contest a Dispute](https://razorpay.com/docs/api/disputes/contest.md)
>
> `PATCH` `/v1/disputes/:id/contest`
>
> Contests a dispute with explanations and supporting documents to submit evidences.

## Related Guides

* [About Disputes](https://razorpay.com/docs/payments/disputes)
* [Set Up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payments.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/disputes.md)
