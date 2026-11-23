> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# About Payment Methods Configuration

> Configure the payment methods of your choice at Razorpay Curlec Checkout.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

You can configure the payment methods of your choice on the Razorpay Curlec Checkout to provide a highly personalised experience for your customers. This provides a simple and accessible experience to your customers increasing your sales and your success rates.

## Use Cases

Depending on the use cases that you might have, Razorpay Curlec allows you to create any configuration of the payment methods, of your choice:

* **Highlighting certain payment instruments on the Checkout.**\
  For example, **Grab Pay** could be displayed outside the Wallet block as a separate payment method. **Maybank** could come out of the FPX/Online Banking container as a different payment method.

* **Restricting the kind of network, issuer, BIN and card type, different card properties, to accept payments.** \
  For example, you can choose to accept payments only from **Maybank Visa Debit cards** on the Checkout.

* **Removing a certain payment method or instrument.** \
  For example, **TouchnGo** can be removed as a payment method from wallets. The entire **FPX/Online Banking** block or a certain bank in FPX/Online Banking can be removed from the Checkout.

* **Reordering of payment methods on the Checkout.** \
  You can choose to arrange **Wallets** as the first section instead of **Cards** on the Checkout. You can again order the PSPs within the Wallet block according to your need.

* **Grouping of payment instruments.** \
  For example, you can choose to group **FPX/Online banking** and **Cards** payment methods of a bank as a block that will be labelled as **Pay via Bank** on the Checkout.

## Configuring Payment Methods

To control payment methods on the Checkout, there are different ways to pass the configuration to the Checkout:

* **Pass Configuration at Runtime**: Pass the configuration to the `options` parameter of the Checkout code at the run time.  This is useful when you want to modify the order of the payment methods for a particular set of payments while rendering the Checkout. See the [Sample Code](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods/sample-code.md) for details.

* **Use a Configuration ID**: Create a global setting of the payments as a **Configuration ID** and pass these values while creating the Order. This is useful when you want control the checkout configurations dynamically using different **Configuration IDs**. You can create a **Configuration ID** through the Dashboard. There are two ways to pass the Configuration ID:
  * While creating the order: Add the `checkout_config_id` field in the order creation request.
  * While opening the checkout: Include the `checkout_config_id` in the checkout options.

```json Pass config id theme={null}
"checkout_config_id": "YourConfigIDHere"
```

## Next Steps

[Understand the Configuration](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods/understand-configuration.md)

### Related Information

* [Supported Methods](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods/supported-methods.md)
* [Sample Codes](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods/sample-code.md)
