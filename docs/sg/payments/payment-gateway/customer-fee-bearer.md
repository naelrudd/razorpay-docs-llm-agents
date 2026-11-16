> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Customer Fee Bearer

> Pass the Razorpay transaction fee on credit card payments to your customers as an Admin Fee at checkout.

Available in
🇸🇬 Singapore

Razorpay charges a transaction fee on every payment. By default, you bear this fee and it is deducted from your settlement. With Customer Fee Bearer (CFB), you can pass this fee to your customers when they pay with a credit card.

When CFB is enabled, your customer sees an **Admin Fee** at checkout after they enter their card details. They pay the order amount plus the Admin Fee, and you receive the full order amount.

> [!NOTE]
>
> **Feature Request**
>
> This is an on-demand feature. Contact your account manager or raise a request with our [Support team](https://razorpay.com/sg/support/) to enable CFB on your account. You cannot turn CFB on or off from the Dashboard.

## How It Works

1. Your customer selects a payment method at checkout and enters their card details.
2. If the card is eligible for CFB, checkout shows the Admin Fee and the new total. For other payment methods, such as PayNow or a debit card, no fee is shown.
3. Your customer pays the order amount plus the Admin Fee. The fee is fixed at this point and does not change later.
4. You are settled the full order amount in SGD.

The Admin Fee is the Razorpay transaction fee plus 9% GST, shown as a single amount.

### Example

The rate below is for illustration only. Your rate is as agreed with Razorpay.

| Line | Amount |
| - | - |
| Order amount | S\$100.00 |
| Transaction fee (2.50% + S\$0.50) | S\$3.00 |
| GST (9% on the transaction fee) | S\$0.27 |
| **Admin Fee shown to the customer** | **S\$3.27** |
| **Customer pays** | **S\$103.27** |
| **You receive** | **S\$100.00** |

## Supported Payment Methods

| Payment method | Who pays the fee |
| - | - |
| Domestic credit cards (Visa, Mastercard, American Express and UnionPay) | Customer |
| International cards | Customer, if enabled for your account |
| Domestic debit and prepaid cards | You |
| PayNow | You |
| Wallets, such as GrabPay | You |
| Pay Later, such as Atome | You |
| Apple Pay and Google Pay | Not available while CFB is enabled. See [Apple Pay and Google Pay](#apple-pay-and-google-pay). |

Card network rules do not allow surcharging debit and prepaid cards, and PayNow cannot be surcharged. Your customers do not see an Admin Fee when they pay with these methods.

> [!WARNING]
>
> **Watch Out!**
>
> International credit and debit cards cannot be told apart. If CFB is enabled for international cards on your account, the Admin Fee applies to all international cards, including debit cards.

## Supported Integrations

CFB is supported on:

* [Standard Checkout](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard.md) (web)
* [Payment Links](https://razorpay.com/docs/sg/payments/payment-links)
* [Payment Pages](https://razorpay.com/docs/sg/payments/payment-pages)

CFB is **not supported** on:

* [Server-to-server (S2S) integration](https://razorpay.com/docs/sg/payments/payment-gateway/s2s-integration/json/v2). See [Pass the Fee on S2S Payments](#pass-the-fee-on-s2s-payments).
* Subscriptions and recurring card payments.
* [Offers](https://razorpay.com/docs/sg/payments/offers).

If you use any other integration, such as the mobile SDKs or Custom Checkout, contact your account manager to confirm support before you enable CFB.

### Pass the Fee on S2S Payments

If you accept payments through a server-to-server (S2S) integration, you can still pass the fee to your customers. Keep CFB disabled on your account and add the fee to the amount you charge:

1. Calculate the fee for the payment method your customer selects, based on your agreed rate.
2. Show the fee on your checkout page as a separate line, such as **Admin Fee** or **Processing Fee**, below the order amount. Show the total your customer will pay before they confirm the payment.
3. Update the fee and the total when your customer changes the payment method. For example, remove the fee if they switch from a credit card to PayNow.
4. Pass the total, order amount plus fee, in the `amount` field when you create the order and the payment.

> [!NOTE]
>
> **Handy Tips**
>
> * Add the fee only to payment methods that allow it. Card network rules do not allow surcharging debit or prepaid cards, and PayNow cannot be surcharged.
> * Mention the fee in your payment confirmation and receipts so your customers can match it to their statement.
> * The total you pass is the payment amount. The Razorpay transaction fee is deducted from your settlement as usual, and a full refund returns the total, including the fee, to your customer.

## Apple Pay and Google Pay

Apple Pay and Google Pay are hidden at checkout while CFB is enabled on your account. If you use either of these methods, choose between them and CFB before you raise the request.

## Refunds

When you refund a CFB payment:

* Your customer receives everything they paid, including the Admin Fee.
* Your balance is debited the full amount the customer paid.
* You bear the refund fee.

This applies to full, partial and multiple refunds. Know more about [refunds](https://razorpay.com/docs/sg/payments/refunds).

## Receipts

The payment acknowledgement email shows the total amount the customer paid. You can request a breakdown that shows the **Base Amount** and the **Admin Fee** as separate lines on credit card CFB payments. GST is included in the Admin Fee and cannot be shown separately.

To request this breakdown, contact your account manager.

## Reports

Payments made with CFB appear on your Dashboard reports with the total amount the customer paid. Reports do not show who bore the fee.

## Inform Your Customers

Razorpay shows the Admin Fee to your customers only at checkout. Let your customers know about the fee before they reach checkout, for example on your pricing or payment page.

## Test Mode

In test mode, checkout shows the Admin Fee when you pay with a test credit card. Settlement amounts and email receipts are available only in live mode.

## FAQs

> [accordion] 1. Can I pass on only part of the fee to my customers?
>
> No. Your customer pays the full fee for an eligible card, or no fee at all.

> [accordion] 2. Is CFB available for non-SGD payments?
>
> Yes, if it is enabled for your account. Non-SGD payments are usually made with international cards, so the Admin Fee applies only if CFB is enabled for international cards on your account. The Admin Fee is shown and charged in the payment currency, and you are settled the order amount in SGD.

> [accordion] 3. Can I use CFB in Malaysia?
>
> No. CFB is available only for businesses in Singapore.

> [accordion] 4. Why are my customers seeing a fee on a debit card?
>
> Domestic debit cards should never carry an Admin Fee. If your customer sees one, raise a request with our [Support team](https://razorpay.com/sg/support/) with the payment ID.

### Related Information

* [List of Features](https://razorpay.com/docs/sg/payments/payment-gateway/features.md)
* [Refunds](https://razorpay.com/docs/sg/payments/refunds)
* [Offers](https://razorpay.com/docs/sg/payments/offers)
