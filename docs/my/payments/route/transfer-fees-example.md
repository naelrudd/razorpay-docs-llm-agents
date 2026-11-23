> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Transfers and Related Fees Example

> Transfers amount and related fee calculations for payments made to Linked Accounts using Route.

Available in
🇮🇳 India
🇲🇾 Malaysia

Following are examples of transfers to Linked Accounts and how Payment Gateway and transfer fees apply to the transactions.

> [accordion] Transfer to Single Linked Account
>
> In this example, you are making a transfer to a single Linked Account. Following are the details:
>
> * **Payment Amount** = RM100.00
> * **Payment Pricing Plan** = 2%
> * **Transfer Fees** = 0.25%
> * **Your Commission** = RM10.00
> * **Amount Transferred to Linked Account** = RM90.00
>
> | Transaction Details | Your Account Balance (RM) |
> | - | - |
> | **Payment received from Customer** | 100.00 |
> | **Gateway Fee Charged on Capture**   Payment Amount \* Pricing Plan   100 \* 2/100 | -2.00 |
> | **Account Balance after Deduction** | **98** |
> | **Transfer Fee Charged**  Transfer Amount \* Pricing Plan 90 \* 0.25/100 | -0.22 |
> | **Amount Transferred to Linked Account** | -90.00 |
> | **Final Account Balance** | **7.78** |

> [accordion] Transfer to Two Linked Accounts
>
> In this example, you are making transfers to two Linked Accounts. Following are the details:
>
> * **Payment Amount** = RM100.00
> * **Payment Pricing Plan** = 2%
> * **Transfer Fees** = 0.25%
> * **Your Commission** = RM10
> * **Amount Transferred to Linked Account 1** = RM30.00
> * **Amount Transferred to Linked Account 2** = RM70.00
>
> | Transaction Details | Your Account Balance (RM) |
> | - | - |
> | **Payment received from Customer** | 100.00 |
> | **Gateway Fee Charged on Capture**   Payment Amount \* Pricing Plan   100 \* 2/100 | -2.00 |
> | **Account Balance after Deduction** | **98.00** |
> | **Linked Account 1 Transfer Fee Charged**  Transfer Amount \* Pricing Plan  30 \* 0.25/100 | -0.075 |
> | **Amount Transferred to Linked Account 1** | -30.00 |
> | **Net Account Balance** | **67.92** |
> | **Linked Account 2 Transfer Fee Charged**  Transfer Amount \* Pricing Plan 70 \* 0.25/100 | -0.175 |
> | **Amount Transferred to Linked Account 2** | -70.00 |
> | **Final Account Balance** | **-2.25** |
>
> The transfer happens **only if** you have an account balance equal to or greater than RM2.25.

### Related Information

* [Transfer Funds to Linked Accounts](https://razorpay.com/docs/my/payments/route/transfer-funds-to-linked-accounts.md)
* [Schedule Settlements](https://razorpay.com/docs/my/payments/route/schedule-settlement.md)
* [Payment Reversals](https://razorpay.com/docs/my/payments/route/reversal.md)
* [Refund to Customers](https://razorpay.com/docs/my/payments/route/refund.md)
