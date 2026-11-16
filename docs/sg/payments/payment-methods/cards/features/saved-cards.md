> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Save Customer Card Details at Standard Checkout

> Store customer's card details securely as tokens to repeat transactions made by the customer. Manage saved cards.

Available in
🇮🇳 India
🇸🇬 Singapore

Save your customers' card details with Razorpay using tokens. The next time the customer makes any transaction, they only need to enter the CVV of the previously saved card. This saves the customer the hassle of entering the card details multiple times for each transaction.

Know [how to integrate saved cards at Standard Checkout.](https://razorpay.com/docs/sg/payments/payment-methods/cards/features/integrate-saved-cards.md)

> [!WARNING]
>
> **Watch Out!**
>
> For a safer and secure payment experience, please advise your customers to log out of the Saved Cards feature after completing the payment. Doing so avoids any misuse of the card information.

## Save Card Details

To save card details, the customer:

1. Opens Razorpay Checkout and selects **Card** as the payment method.
2. Provides the card details.
3. While making a card payment, the customer can choose to:
   * Save their card details.
   * Not save their card details.

## Make Payments Using Saved Cards

To make payment using saved cards:

1. The customers log in to the Razorpay Checkout.
2. They select **Card** as the payment method.
3. They enter the OTP sent to their phone , then click **Verify**.
4. They select the saved card, enter the CVV and click **Pay**.
5. We recommend that customers log out of Checkout after they complete the transaction. To do this, they must:
   1. Open Razorpay Checkout.
   2. Select **Card** as the payment method.
   3. Click the drop-down list and select **Log out from all devices**.

## Frequently Asked Questions (FAQs)

> [accordion] Why are my customers unable to access the saved cards?
>
> If your customers are using Google Chrome and not able to access saved cards, it may be due to their browser configurations. Go to Chrome **Settings**, select **Privacy and security** → **Cookies and other site data** → **Allow all cookies** and restart the browser. If they still cannot access them, contact our [Support team](https://razorpay.com/sg/support/).
>
> ![Allow Cookies](https://razorpay.com/docs/build/browser/assets/images/saved-cards-chrome-settings-3.jpg)

> [accordion] My customers have accessed their saved cards on the  Checkout by providing OTP. How do they now log out?
>
> For a safer and secured payment experience, your customer must log out from the Razorpay Checkout by following these steps:\\
>
> 1. Open Razorpay Checkout.
> 2. Select **Card** as the payment method.
> 3. Click the drop-down and select **Log out from all devices**.
>
> This logs the customers out from the saved card feature on Checkout.
