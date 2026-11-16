> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Chargeback Fees & Penalties

> Understand the turnaround time for each chargeback phase, the fees and penalties charged by card networks, and how Deduct at Onset (DAO) works.

Available in
🇮🇳 India

Understand the turnaround time for each chargeback phase, the fees and penalties levied by card networks at each stage, and how Razorpay handles the disputed amount while a case is being resolved.

## Chargeback Phases and Turnaround Time (TAT)

Each chargeback phase has a fixed window within which you must respond with your evidence. Missing this window results in an automatic loss of the chargeback, regardless of the merits of your case.

| Phase | Turnaround Time |
| - | - |
| **Chargeback** | T+3 business days |
| **Pre-Arbitration** | T+2 business days |
| **Arbitration** | T+1 business day |

> [!NOTE]
>
> **Handy Tips**
>
> Pre-arbitration and arbitration are long-drawn, complex, and costly stages. Responding with complete evidence at the first chargeback stage is the most effective way to avoid escalation.

## Fees and Penalties by Network

If a chargeback escalates beyond the first stage, the card network levies additional fees, which are passed on to you. These fees apply regardless of the final outcome of the case.

| Dispute Stage | Mastercard | Visa | RuPay | UPI |
| - | - | - | - | - |
| **Chargeback** | Nil | Nil | Nil | Nil |
| **Pre-Arbitration** | USD 15.00 | USD 0.75 | Nil | Nil |
| **Arbitration** | USD 675.00 | USD 600.00 | INR 3,000.00 | Arbitration acceptance/NRP fee of INR 500 + GST, and PRD fee of INR 3,000 + GST per arbitration |

**Note:** Visa's arbitration penalty fee was revised from USD 500 to USD 600, effective October 1, 2024.

If the arbitration is ruled in the cardholder's favour, the arbitration fee — in addition to the disputed transaction amount — is borne by you.

## Deduct at Onset (DAO)

When a dispute is raised, Razorpay deducts the disputed amount, along with any applicable fees, from your account balance at the outset — before the case is resolved. This is standard practice across payment gateways and ensures sufficient funds are available to cover the liability if the dispute is decided against you, in line with network and regulatory requirements.

If the dispute is resolved in your favour, the withheld amount is credited back to your account.

## What Happens After a Decision

### If you win the dispute

Once you submit your evidence, Razorpay forwards it to the acquiring bank, which passes it on to the issuing bank and card network for review. If the case is decided in your favour, the amount debited earlier is credited back to your account. Since this involves multiple stakeholders, the reversal can take **up to 30 days** from the date your evidence was submitted.

### If you accept or lose the dispute

If you accept a dispute — or lose it after contesting — Razorpay notifies the issuing bank of the outcome via the acquiring bank. The issuing bank and card network then determine the refund amount and timeline for the customer. Razorpay does not have visibility or control over the exact timing of the refund reaching the customer's payment instrument; customers should be directed to their bank for refund status.

### Related Information

* [About Disputes](https://razorpay.com/docs/payments/disputes)
* [Chargeback Types & Prevention](https://razorpay.com/docs/payments/disputes/chargeback-types-and-prevention.md)
* [Submit Evidence](https://razorpay.com/docs/payments/disputes/submit-evidence.md)
* [Disputes - Dashboard Actions](https://razorpay.com/docs/payments/disputes/dashboard.md)
* [International Chargebacks](https://razorpay.com/docs/payments/disputes/international-chargebacks.md)
* [Dispute FAQs](https://razorpay.com/docs/payments/disputes/faqs.md)
* [Dispute APIs](https://razorpay.com/docs/payments/disputes/apis.md)
