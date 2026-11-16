> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Python Server SDK Prerequisites

> Check the prerequisites before you integrate with Razorpay Python server-side SDK.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

> [card] [Python Changelog](https://razorpay.com/docs/payments/changelog.md#server-sdks)
>
> Discover new features, updates and deprecations related to the Razorpay Python SDK (since Jan 2024).

Install the Razorpay Python SDK and integrate it with your Python-based website to accept payments, initiate refunds and do much more.

## Dependencies

You must use Python v3.12 or higher. Know more about the [latest Python versions](https://www.python.org/downloads/).

Download the latest source code zip file from [GitHub](https://github.com/razorpay/razorpay-python/releases). Unzip the file and add it to your project.

After setting up the client, set up your app details before making requests to Razorpay. Run the following command to set up your app details:

```python theme={null}
client.set_app_details({"title" : "<YOUR_APP_TITLE>", "version" : "<YOUR_APP_VERSION>"})
```

The app title and version is a `string`. For example, you can set the title to **Django** and version to **1.8.17**.

> [card] [Payment Gateway](https://razorpay.com/docs/payments/server-integration/python/integration-steps.md#integrate-with-razorpay-payment-gateway)
>
> Integrate with Razorpay Payment Gateway.

> [card] [API Sample Codes](https://github.com/razorpay/razorpay-python/tree/master/documents)
>
> Integrate using API sample codes.

> [card] [Other Razorpay Products](https://razorpay.com/docs/payments/server-integration/python/integration-steps.md#integrate-with-other-razorpay-products)
>
> Integrate with other Razorpay products.

## Support

* **Queries**: If you have queries, [contact support](https://razorpay.com/support/).

* **Feature Request**: If you have a feature request, raise an issue on [GitHub](https://github.com/razorpay/razorpay-python/issues/new).

### Related Information

[Address Verification System](https://razorpay.com/docs/payments/international-payments/address-verification-system.md)
