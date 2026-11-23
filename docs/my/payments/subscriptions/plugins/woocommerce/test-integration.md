> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# 2. Test Integration

> Run test payments to make sure that your integration works.

Available in
🇮🇳 India
🇲🇾 Malaysia

After the integration is complete, Razorpay Curlec will appear as a payment option on your web page/app. You need to click the button and make a test transaction to ensure that the integration is working as expected. You can start accepting actual payments from your customers once the test is successful.

You can make test payments using one of the payment methods configured at the Checkout.

* No money is deducted from the customer's account as this is a simulated transaction.
* Ensure you have entered the API keys generated in the test mode in the Checkout code.

## Cards

You can use one of the test cards to make transactions in the test mode. Use any valid expiration date in the future and any random CVV to create a successful payment.

| Card Network | Card Number | CVV & Expiry Date |
| - | - | - |
| Mastercard | 5272 0088 0623 5704 | Use a random CVV and any future date ^^ |
| Visa | 4842 7930 0208 6571 | |

> [!WARNING]
>
> **Watch Out!**
>
> In test mode, you can perform a subsequent debit only within 3 days of token creation, as card tokens are valid for 3 days only.

### Next Steps

[Step 3: Go Live Checklist](https://razorpay.com/docs/my/payments/subscriptions/plugins/woocommerce/go-live-checklist.md)
