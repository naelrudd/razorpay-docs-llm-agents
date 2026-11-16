> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# About OAuth

> Use OAuth to integrate your applications and securely access Razorpay and RazorpayX client resources via token-based authentication.

Available in
🇮🇳 India

**OAuth** or **Open Authorisation** is an authorisation standard that allows you to access resources hosted by other web apps on behalf of a user.

Razorpay OAuth is a token-based authentication method where you can obtain an access token with the consent of the user, without them having to compromise their API key secret. OAuth lets the user decide who can access what level of resources within their Razorpay account.

As Razorpay Technology Partners, you must use OAuth to securely access and manage the Razorpay accounts of businesses on your platform, without them having to share sensitive credentials. This contributes to better user experience.

#### Example

Assume you are a marketplace that signs up as Razorpay's Technology Partner -  ***Corpfy***.\

You onboard a sub-merchant that wants to sell clothes on your platform - ***Acme***.

* You integrate with Razorpay OAuth after signing up.
* You create an application via Razorpay Partner Dashboard, to onboard *Acme* as a sub-merchant.
  * During onboarding, you request *Acme* to give you their account access.
  * On authorising, you can access the payments, refunds, disputes etcetra on *Acme*'s Razorpay account, but the security information however, remains safe with Razorpay.

After *Acme* authorises you to access their account, a `code` is generated. You must use this code to generate `access_token` which you can use to trigger APIs on *Acme*'s behalf.

![oauth token process](https://razorpay.com/docs/build/browser/assets/images/oauth-process.jpg)

## Prerequisites

Sign up with Razorpay as a Technology Partner by reaching out to our [support team](https://razorpay.com/support/). You require this to register your application on the Dashboard.

## Video Tutorial

Watch this video to know how to integrate Razorpay OAuth as a Technology Partner.

[YouTube video player](https://www.youtube.com/embed/_qWjer8Rw8Q?si=L4XN-lPME7cGGgcF)

## Next Steps

1. [Build Integration](https://razorpay.com/docs/partners/technology-partners/onboard-businesses/integrate-oauth/integration-steps.md)
2. [Test Integration](https://razorpay.com/docs/partners/technology-partners/onboard-businesses/integrate-oauth/test-integration.md)
3. [Go-live Checklist](https://razorpay.com/docs/partners/technology-partners/onboard-businesses/integrate-oauth/go-live-checklist.md)

### Related Information

* [Revoke Access to Application](https://razorpay.com/docs/partners/technology-partners/onboard-businesses/integrate-oauth/revoke-access.md)
* [Track Onboarding Status](https://razorpay.com/docs/partners/technology-partners/onboard-businesses/status.md)
