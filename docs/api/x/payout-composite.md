> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Payout Composite

> Explore composite APIs to make a payout using a single API call.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Composite API allows you to make three requests in a single API call. No OTP authorization is required when creating a payout using APIs. Ensure you [allowlist IPs](https://razorpay.com/docs/x/dashboard/allowlist-ip.md) and pass the [idempotency key](https://razorpay.com/docs/api/x/payout-idempotency/make-request.md) to make a successful payout.

You can either create a new Contact and its Fund Account while making the payout, or use an existing Contact and Fund Account details to make the payout. Using the Contact and Fund Account details instead of IDs will not create duplicate Contacts or Fund Accounts in your system. However, we recommend that you create the Contact and Fund Account before making a payout to help **improve payout processing time**.

Fork the Razorpay Postman Public Workspace and try the Payout Composite APIs using your [Test API Keys](https://razorpay.com/docs/x/dashboard/api-keys.md).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-d81df592-f496-49f0-a3b1-e8cf62855d50)

> [card] [Create a Payout to a Bank Account](https://razorpay.com/docs/api/x/payout-composite/create/bank-account.md)
>
> `POST` `/v1/payouts`
>
> Creates a payout along with the Contact and Fund Account with of the type bank account.

> [card] [Create a Payout to a VPA](https://razorpay.com/docs/api/x/payout-composite/create/vpa.md)
>
> `POST` `/v1/payouts`
>
> Creates a payout along with the Contact and Fund Account of the type VPA.

> [card] [Create a Payout to a Card](https://razorpay.com/docs/api/x/payout-composite/create/card.md)
>
> `POST` `/v1/payouts`
>
> Creates a payout along with the Contact and Fund Account of the type card.

## Related Guides

* [About Payouts API](https://razorpay.com/docs/api/x/payouts.md)
* [Set Up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payouts.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks)
* [Payouts Best Practices](https://razorpay.com/docs/x/payouts/best-practices.md)
