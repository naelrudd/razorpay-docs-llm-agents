> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# API Sandbox Setup

> Sandbox setup for testing Razorpay Curlec APIs.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

The Razorpay Curlec Sandbox environment allows you to test your integration without using real money. It is a crucial step before going live with your Razorpay Curlec integration.

## Steps

Follow these steps to set up the sandbox environment.

> [accordion] Generate API Keys
>
> Follow these [steps to generate API keys](https://razorpay.com/docs/my/api/authentication.md#generate-api-keys).

> [accordion] Use Sandbox URL & Client Libraries
>
> The base URL for the Razorpay Curlec Sandbox and production API is the same - `https://api.razorpay.com/v1/`. In case of certain APIs, it is `https://api.razorpay.com/v2`.
>
> For testing APIs in the sandbox environment, use the test API keys.
>
> How you use them depends on the programming language and the Razorpay SDK you are using. Refer to the relevant SDK documentation for specific instructions. The SDK documentation will have clear examples of how to initialise the Razorpay Curlec client with your Key ID and Key Secret.
>
> **Client Libraries** \\
>
> For Razorpay Curlec Payments, the client SDK libraries are available on GitHub. You can use the API keys generated above to try out the API sample codes:
>
> > [card] .Net
> >
> > * [Integrate](https://razorpay.com/docs/my/payments/server-integration/dot-net.md)
> > * [GitHub Repo](https://github.com/razorpay/razorpay-dot-net)
>
> > [card] Java
> >
> > * [Integrate](https://razorpay.com/docs/my/payments/server-integration/java.md)
> > * [GitHub Repo](https://github.com/razorpay/razorpay-java)
>
> > [card] Node.JS
> >
> > * [Integrate](https://razorpay.com/docs/my/payments/server-integration/nodejs.md)
> > * [GitHub Repo](https://github.com/razorpay/razorpay-node)
>
> > [card] PHP
> >
> > * [Integrate](https://razorpay.com/docs/my/payments/server-integration/php.md)
> > * [GitHub Repo](https://github.com/razorpay/razorpay-php)
>
> > [card] Python
> >
> > * [Integrate](https://razorpay.com/docs/my/payments/server-integration/python.md)
> > * [GitHub Repo](https://github.com/razorpay/razorpay-python)
>
> > [card] Ruby
> >
> > * [Integrate](https://razorpay.com/docs/my/payments/server-integration/ruby.md)
> > * [GitHub Repo](https://github.com/razorpay/razorpay-ruby)
>
> > [card] Go
> >
> > * [Integrate](https://razorpay.com/docs/my/payments/server-integration/go.md)
> > * [GitHub Repo](https://github.com/razorpay/razorpay-go)

> [accordion] Go live
>
> After testing is complete, generate [Live API keys](https://razorpay.com/docs/my/payments/dashboard/account-settings/api-keys.md#generate-api-keys) from the dashboard. Ensure to replace the Test API keys in your integration with the Live API keys before going live. You can accept real money payments using the Live API Keys.

### Related Information

* [Understand Razorpay Curlec APIs](https://razorpay.com/docs/my/api/understand.md)
* [Errors](https://razorpay.com/docs/my/errors)
* [Best Practices](https://razorpay.com/docs/my/api/best-practices.md)
* [Glossary](https://razorpay.com/docs/my/api/glossary.md)
