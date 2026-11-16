> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payment Downtime

> Check the Payment Downtime API to view a list of affected payment methods during downtime.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Downtime is when one or more payment options underperform, leading to considerable delays in payment processing. These downtimes are due to technical issues or outages at Razorpay's partner or issuing banks.\
\


Razorpay informs you about the downtime to communicate it to your customers and display only the unaffected payment methods while accepting payments from them. You can poll the API or configure Webhooks to be notified of the downtimes and plan the remediation steps accordingly. Downtime communication for the payment methods such as cards and paynow is available.\
\


> [card] [Fetch Payment Downtime Details](https://razorpay.com/docs/sg/api/payments/downtime/fetch-all.md)
>
> `GET` `/v1/payments/downtimes`
>
> Retrieves details of Payment Downtime.

> [card] [Fetch Payment Downtime Details With ID](https://razorpay.com/docs/sg/api/payments/downtime/fetch-with-id.md)
>
> `GET` `/v1/payments/downtimes/:id`
>
> Retrieves details of a Payment Downtime with id.

## Related Guides

* [About Downtime](https://razorpay.com/docs/payments/payments/downtime-updates.md)
* [Set Up Webhooks](https://razorpay.com/docs/sg/webhooks/setup-edit-payments.md)
* [Webhook Payloads](https://razorpay.com/docs/sg/webhooks/payments.md#payments-downtime)
