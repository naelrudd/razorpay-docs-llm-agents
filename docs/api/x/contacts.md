> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Contacts

> List of Contacts APIs to create, retrieve, update and delete RazorpayX Contacts.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

A contact is an entity to whom payouts can be made through various supported modes like UPI, IMPS, NEFT and RTGS, Cards and more. Know more about [Contacts and Fund Accounts](https://razorpay.com/docs/x/contacts). \
&#x20;\


It is mandatory to [allowlist the IPs](https://razorpay.com/docs/x/dashboard/allowlist-ip.md) that you use while making payouts via APIs, else the request will fail. In case of errors, you can refer to the error codes in the respective API endpoint pages.

Fork the Razorpay Postman Public Workspace and try the Contacts APIs using your [Test API Keys](https://razorpay.com/docs/x/dashboard/api-keys.md).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-46855750-fa22-46cd-9fa2-2f294507ec22)

> [card] [Create a Contact](https://razorpay.com/docs/api/x/contacts/create.md)
>
> `POST` `/v1/contacts`
>
> Creates a new Contact with phone number/email id.

> [card] [Update a Contact](https://razorpay.com/docs/api/x/contacts/update.md)
>
> `PATCH` `/v1/contacts/:id`
>
> Updates a particular Contact's details.

> [card] [Retrieve All Contacts](https://razorpay.com/docs/api/x/contacts/fetch-all.md)
>
> `GET` `/v1/contacts`
>
> Retrieves all Contacts created in your RazorpayX account.

> [card] [Retrieve Contact With ID](https://razorpay.com/docs/api/x/contacts/fetch-with-id.md)
>
> `GET` `/v1/contacts/:id`
>
> Retrieves a single Contact with ID.

> [card] [Activate or Deactivate a Contact](https://razorpay.com/docs/api/x/contacts/update.md)
>
> `PATCH` `/v1/contacts/:id`
>
> Activates or deactivates an existing contact.

## Related Guides

* [About Contacts](https://razorpay.com/docs/x/contacts)
* [Set Up Webhooks](https://razorpay.com/docs/webhooks/setup-edit-payouts.md)
