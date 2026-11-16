> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Flash Links (ACH Debit)

> Accept payments from your US customers directly from their US bank account using ACH Debit (ACH Pull). US payers pay Indian exporters via a familiar pay-by-bank experience, and you receive settlements in INR in your Indian bank account.

Available in
🇮🇳 India

**ACH Debit** (also known as **ACH Pull**) lets your US customers pay you directly from their US bank account using a familiar "pay by bank" method. Instead of relying on expensive traditional wire transfers, your US buyers authorise a bank debit, and you receive settlements in INR in your Indian bank account.

ACH Debit is available two ways: as a **Flash Link (ACH Debit)** that you generate and share, and automatically as an option at **Razorpay Checkout** for eligible US payments. See [Accept Payments via ACH Debit](#accept-payments-via-ach-debit) for both flows.

ACH Debit is an addition to [International Bank Transfer (MoneySaver Export Account)](https://razorpay.com/docs/payments/international-payments/international-bank-transfer.md). It is available only for merchants who have International Bank Transfer activated and Flash Links (ACH Debit) enabled on their account.

> [accordion] Advantages
>
> > [tab] For Your Business
> >
> > * **Lower cost than wire transfers** \\
> >
> >   ACH Debit is significantly cheaper than traditional SWIFT wire transfers, letting your US customers pay you without the high per-transfer fees and FX markups of wires.
> >
> > * **Fewer card-related failures at submission** \\
> >
> >   Bank-based ACH payments avoid the common card failure reasons, such as expiry, limits or card network blocks. Note that ACH debits can still be reversed after payment through a chargeback. See [Chargebacks and reversals](#chargebacks-and-reversals).
> >
> > * **Familiar experience for US payers** \\
> >
> >   US customers pay from their bank account using a method they already use for domestic payments, reducing friction and abandoned payments.
> >
> > * **Suited to high-value B2B payments** \\
> >
> >   ACH Debit works well for large invoices where cards are expensive and wires are slow, making it ideal for services and B2B exports.
> >
> > * **Settlement in INR with compliance built in** \\
> >
> >   You receive settlements in INR in your Indian bank account, with FIRS and invoice management handled as part of International Bank Transfer.
>
> > [tab] For Your Customers
> >
> > * **Pay directly from a bank account** \\
> >
> >   Customers pay from their existing US bank account without needing an international card or visiting a bank branch.
> >
> > * **1-click bank connection** \\
> >
> >   Customers can securely connect most US banks through Plaid, so they do not have to enter bank details manually.
> >
> > * **Lower fees than cards or wires** \\
> >
> >   ACH Debit typically costs the payer less than international card payments or wire transfers.
> >
> > * **Clear, familiar authorisation** \\
> >
> >   Customers review and accept a standard bank authorisation before the payment is submitted, so they always know what they are approving.

## How It Works

1. Activate [International Bank Transfer](https://razorpay.com/docs/payments/international-payments/international-bank-transfer.md#activate-international-bank-transfer) and get Flash Links (ACH Debit) enabled on your account (see [Enable Flash Links (ACH Debit)](#enable-flash-links-ach-debit)).
2. Share a Flash Link (ACH Debit) with your US customer, or let ACH Debit appear automatically at Checkout for eligible US payments.
3. Your customer opens the link, connects their US bank account (via Plaid) or enters their bank details, and authorises the ACH debit.
4. The payment is submitted to the ACH network for processing.
5. Track the payment status and timeline on your dashboard.
6. Receive settlement in INR in your Indian bank account.

## Eligibility

The ACH Debit option is shown to a payer only when all of the following are true:

* The payer is located in the **United States** (based on the payer's IP/location).
* The payment currency is **USD**.
* **International Bank Transfer (MoneySaver)** is activated for your account.
* **Flash Links (ACH Debit)** is enabled for your account.

Because eligibility is based on the payer's IP/location, a US payer who is travelling abroad, or connecting through a VPN outside the US, may not see the ACH Debit option.

You must also meet the standard [International Bank Transfer prerequisites](https://razorpay.com/docs/payments/international-payments/international-bank-transfer.md#prerequisites), including a valid export purpose code.

## Enable Flash Links (ACH Debit)

Flash Links (ACH Debit) is enabled on top of International Bank Transfer and is not a self-serve dashboard toggle. To get it enabled on your account:

1. Ensure [International Bank Transfer](https://razorpay.com/docs/payments/international-payments/international-bank-transfer.md#activate-international-bank-transfer) is already activated.
2. Contact your Razorpay account manager or [Razorpay Support](https://razorpay.com/support/) to request Flash Links (ACH Debit).

Once enabled, ACH Debit becomes available through Flash Links and at Checkout for eligible US payments.

## Accept Payments via ACH Debit

There are two ways your US customers can pay you using ACH Debit.

> [tab] Invoices
>
> Generate a Flash Link (ACH Debit) by creating an invoice from your International Bank Transfer dashboard and sharing it with your US customer:
>
> 1. Log in to the Dashboard and navigate to **Intl Bank Transfer**.
> 2. Create a new invoice and add the **Customer details** and **Items**.
> 3. In the **Payment collection** step, select **Flash Links (ACH Debit)** ("Collect via ACH debit"). You can also enable **Bank Transfer** (where your customer pushes the payment from their bank) on the same invoice.
> 4. Finalise the invoice, then copy the generated link or send it to your customer directly over email from the dashboard.
>
> Because you provide the invoice and customer details while creating the invoice, your customer is not asked to enter their billing address again when they pay.

> [tab] Checkout
>
> If you use Razorpay Checkout, ACH Debit appears automatically as a payment option, with **no API or integration changes required**, when:
>
> * Your account is activated for International Bank Transfer and Flash Links (ACH Debit) is enabled.
> * The payer's location is the United States.
> * The transaction currency is USD.
>
> Your customer selects **ACH Debit** at Checkout to pay from their US bank account.

## Payer Experience

When your US customer pays through a Flash Link (ACH Debit) or at Checkout:

1. The customer selects **ACH Debit** ("Pay directly from bank account").
2. **Connect a bank account:** The customer connects their US bank account through **Plaid**. If they prefer, or if the bank connection is unavailable, they can enter their bank details manually.
   * When entering details manually, the customer provides their **routing number** and **account number**.
3. **Provide name and address (if required):** Whether the customer is asked for their name and billing address depends on how the payment was initiated. When you generate a Flash Link (ACH Debit) by creating an invoice from the International Bank Transfer dashboard, these details are captured during invoice creation and are not requested again. When the payment is initiated another way, such as at Checkout, the customer provides their full name and billing address at this step.
4. **Authorise the payment:** The customer reviews and accepts a standard ACH debit authorisation before submitting. The authorisation states that they permit the debit from their bank account and notes the expected processing time. The exact wording is shown on the payment page.
5. **Confirmation:** After submitting, the customer sees a success screen confirming the payment has been submitted to the ACH network for processing. They receive a payment confirmation email once the payment succeeds.

## Track ACH Debit Transactions

You can monitor your ACH Debit payments from the **Transactions** section of your International Bank Transfer dashboard.

* ACH Debit transactions are labelled as **ACH Debit** payments, and you can filter transactions by this method.
* Transaction details include the payment ID, amount, created date, customer details, bank name, account type and the masked bank account number (last 4 digits visible).
* A timeline view shows each status change for the payment.

ACH Debit transactions move through the following statuses:

| Status | Description |
| - | - |
| Authorised | The bank account is verified and the payment has been submitted to the ACH network. This is a transitionary state. |
| Captured | The payment has been processed successfully. |
| Failed | The payment could not be processed and was rejected before capture, for example because of invalid account details or insufficient funds. The failure reason is shown. |
| Refunded | The payment was refunded to the customer by you. See [Refunds](#refunds). |

A captured payment can still be reversed later if the payer raises a chargeback. See [Chargebacks and reversals](#chargebacks-and-reversals).

> [!NOTE]
>
> **Handy Tips**
>
> Because ACH is a bank-based rail with a chargeback window, settlement takes longer than card payments. Settlement is around **T+5 business days from the time the payment is captured, or from when a valid invoice is provided, whichever is later**. As with all International Bank Transfer payments, settlement is not initiated until a valid invoice is available for the transaction.

## Chargebacks and Reversals

ACH Debit is a pull-based payment, so a debit can be reversed by the payer *after* it has been captured through a chargeback. This is different from push-based International Bank Transfer payments, which cannot be reversed.

How a chargeback is handled depends on whether the payment has been settled to you:

* **Chargeback within 3 days of payment:** Razorpay returns the amount directly to the payer, and no settlement occurs to your account.
* **Chargeback after the payment has been settled to you:**
  * You are fully liable to return the payment amount, plus any additional processing fees required to send the funds back to the payer.
  * Razorpay reserves the right to withdraw the chargeback amount and fees directly from your Razorpay account or linked settlement account.
  * For details, refer to the [Razorpay chargeback policy](https://razorpay.com/terms/).

> [!NOTE]
>
> **Handy Tips**
>
> Because of the chargeback window, we recommend confirming that a payment has settled before treating it as final, especially for high-value orders or before shipping goods or delivering services.

## Refunds

Unlike push-based International Bank Transfer payments, ACH Debit transactions **support refunds**.

* Refunds are available for ACH Debit transactions that have been captured.
* Both **full** and **partial** refunds are supported.
* Refunds typically take **5–10 business days** to appear in your customer's bank account.
* Refund status follows Razorpay's standard refund states (`pending`, `processed`, `failed`), and refund history is visible in the transaction details.

> [!NOTE]
>
> A refund is a return of funds that you initiate. It is different from a [chargeback](#chargebacks-and-reversals), where the payer reverses a captured debit.

## Reports

ACH Debit transactions appear in your payment reports with the following differences:

* The payment **method** column value is `intl_bank_transfer`, and the bank-transfer sub-type is `ach_pull`. Merchants can filter on these column values to isolate ACH Debit transactions.
* The **Card Type** and **Card Network** columns are blank.
* The **Bank Name** and **Account Type** columns are populated for ACH transactions.
* The **failure reason** column is populated for failed transactions.
* The masked bank account number (last 4 digits) is included.

## Pricing

For ACH Debit pricing, refer to the pricing details mentioned [here](https://razorpay.com/accept-international-payments/bank-transfers/).

## Frequently Asked Questions (FAQs)

> [accordion] What is ACH Debit (ACH Pull)?
>
> ACH (Automated Clearing House) is the US electronic bank transfer network. ACH Debit, also called ACH Pull, is a method where the payment is "pulled" from the customer's US bank account after they authorise it. This lets your US customers pay you directly from their bank account instead of using a card or a wire transfer.

> [accordion] Which US banks are supported?
>
> Customers can connect most US banks through Plaid, including major banks. If a customer's bank cannot be connected, they can enter their bank details manually.

> [accordion] Who can pay using ACH Debit?
>
> ACH Debit is available for payers located in the United States paying in USD, when your account has International Bank Transfer activated and Flash Links (ACH Debit) enabled.

> [accordion] What is the settlement timeline?
>
> Settlement for ACH Debit is around T+5 business days from the time the payment is captured, or from when a valid invoice is provided, whichever is later. As with all International Bank Transfer payments, settlement is not initiated without a valid invoice. This is longer than card payments because ACH is a bank-based rail with a chargeback window.

> [accordion] Are refunds supported?
>
> Yes. Full and partial refunds are supported for captured ACH Debit transactions. Refunds typically take 5–10 business days to reach your customer's bank account. A refund is a return of funds that you initiate, and is different from a chargeback; see the question below.

> [accordion] How are chargebacks handled?
>
> ACH Debit is a pull-based payment, so the payer can reverse a captured debit through a chargeback.
>
> * If the payer issues a chargeback within 3 days of payment, Razorpay returns the amount directly to the payer, and no settlement occurs to your account.
> * If the payer issues a chargeback after the payment has been settled to you, you are fully liable to return the payment amount plus any additional processing fees required to send the funds back to the payer. Razorpay reserves the right to withdraw the chargeback amount and fees directly from your Razorpay account or linked settlement account.
>
> For details, refer to the [Razorpay chargeback policy](https://razorpay.com/terms/). See also [Chargebacks and reversals](#chargebacks-and-reversals).

> [accordion] Do I need to make any changes to my Checkout integration?
>
> No. If you use Razorpay Checkout, ACH Debit appears automatically for eligible US payments (payer located in the US, currency USD) once International Bank Transfer and Flash Links (ACH Debit) are enabled on your account. No API or integration changes are required.

> [accordion] Do I need to upload invoices for ACH Debit transactions?
>
> Yes. As with other International Bank Transfer payments, invoices and buyer details are required for compliance. When you generate a Flash Link (ACH Debit) from the dashboard, you create the invoice as part of the flow. Learn more about [managing invoices and transactions](https://razorpay.com/docs/payments/international-payments/international-bank-transfer/transactions-invoices.md).

> [accordion] Will I receive FIRS for these transactions?
>
> Yes. FIRS is provided for International Bank Transfer settlements, including ACH Debit, for your tax and compliance needs. FIRS is sent to your contact email within 24 hours after settlement.

### Related Information

* [International Bank Transfer](https://razorpay.com/docs/payments/international-payments/international-bank-transfer.md)
* [Transactions and Invoices](https://razorpay.com/docs/payments/international-payments/international-bank-transfer/transactions-invoices.md)
* [Connect Platforms](https://razorpay.com/docs/payments/international-payments/international-bank-transfer/connect-platforms.md)
