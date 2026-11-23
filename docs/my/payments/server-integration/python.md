> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Python Server SDK Prerequisites

> Check the prerequisites before you integrate with Razorpay Curlec Python server-side SDK.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Install the Razorpay Curlec Python SDK and integrate it with your Python-based website to accept payments, initiate refunds and do much more.

## Dependencies

You must use Python v3.12 or higher. Know more about the [latest Python versions](https://www.python.org/downloads/).

Download the latest source code zip file from [GitHub](https://github.com/razorpay/razorpay-python/releases). Unzip the file and add it to your project.

After setting up the client, set up your app details before making requests to Razorpay Curlec. Run the following command to set up your app details:

```python theme={null}
client.set_app_details({"title" : "<YOUR_APP_TITLE>", "version" : "<YOUR_APP_VERSION>"})
```

The app title and version is a `string`. For example, you can set the title to **Django** and version to **1.8.17**.

> [card] [Payment Gateway](https://razorpay.com/docs/my/payments/server-integration/python/integration-steps.md#integrate-with-razorpay-curlec-payment-gateway)
>
> Integrate with Razorpay Curlec Payment Gateway.

> [card] [API Sample Codes](https://github.com/razorpay/razorpay-python/tree/master/documents)
>
> Integrate using API sample codes.

> [card] [Other Razorpay Curlec Products](https://razorpay.com/docs/my/payments/server-integration/python/integration-steps.md#integrate-with-other-razorpay-curlec-products)
>
> Integrate with other Razorpay Curlec products.

## Support

* **Queries**: If you have queries, [contact support](https://curlec.com/support/).

* **Feature Request**: If you have a feature request, raise an issue on [GitHub](https://github.com/razorpay/razorpay-python/issues/new).
