> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Document APIs

> Use the Document APIs to upload files and complete the mandatory KYC requirements.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Use the Document APIs to upload and fetch documents for the KYC verification process. Check the [product activation status and updates permitted](https://razorpay.com/docs/partners/aggregators/onboarding-api#product-activation-status-and-updates-permitted) for Document APIs.

The maximum supported file size for a JPG/PNG is 4MB. The maximum supported file size for a PDF is 2MB. Do not pass file URLs instead of uploading documents. If you have uploaded the document but mandatory field-level parameters are not passed in the API, you need to re-execute the Documents API with the same document and pass the fields.

Fork the Razorpay Postman Public Workspace and try the Document APIs using your [Test API Keys](https://razorpay.com/docs/partners/aggregators/onboarding-api#api-authentication).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-91288595-d910-4f84-822d-808de103aeba)

> [card] [Upload Account Documents](https://razorpay.com/docs/api/partners/upload-document/upload-account-documents.md)
>
> `POST` `/v2/accounts/:account_id/documents`
>
> Uploads business documents for a sub-merchant's account.

> [card] [Upload Stakeholder Documents](https://razorpay.com/docs/api/partners/upload-document/upload-stakeholder-documents.md)
>
> `POST` `/v2/accounts/:account_id/stakeholders/:stakeholder_id/documents`
>
> Uploads signatory documents for a stakeholder.

> [card] [Fetch Account Documents](https://razorpay.com/docs/api/partners/upload-document/fetch-account-documents.md)
>
> `GET` `/v2/accounts/:account_id/documents`
>
> Retrieves the documents uploaded for an account.

> [card] [Fetch Stakeholder Documents](https://razorpay.com/docs/api/partners/upload-document/fetch-stakeholder-documents.md)
>
> `GET` `/v2/accounts/:account_id/stakeholders/:stakeholder_id/documents`
>
> Retrieves the documents uploaded for a stakeholder.

## Related Guides

* [Sub-merchant Onboarding APIs](https://razorpay.com/docs/partners/aggregators/onboarding-api)
* [Set Up Webhooks](https://razorpay.com/docs/partners/aggregators/onboarding-api/webhooks.md)
* [Webhook Payloads](https://razorpay.com/docs/webhooks/partners.md)
