> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Change Business Information

> Learn how to request a change to your registered business information such as name or business type on Razorpay.

Available in
🇮🇳 India

When you create a Razorpay account, it is tied to your **business entity type** and **PAN**. Here is what happens when one of these changes:

* **Entity type changes, but PAN stays the same**: You can request Razorpay to update your entity type on your current account, subject to eligibility conditions.
* **PAN changes**: (For example, Sole Proprietorship → Private Limited) You must create a new **Razorpay account** and complete a fresh KYC. Your existing account cannot be updated since Razorpay treats each PAN as a separate legal entity.

> [!WARNING]
>
> **Watch Out!**
>
> Your Razorpay Merchant id (MID) is permanently linked to the PAN registered during onboarding. PAN is used as the primary identifier for KYC, tax compliance and regulatory reporting. When a new PAN is involved, regardless of the reason, Razorpay treats it as a new legal entity. The existing MID cannot be reassigned to a different PAN.

## When your PAN Remains Same

You can request an entity type change if **all** of the following conditions are met:

* Your PAN remains the same before and after the change.
* You have [valid KYC documents](https://razorpay.com/docs/payments/business-types-kyc-documents.md#kyc-documents) for the new entity type.

### Supported Entity Transitions

The following entity transitions are currently supported since they do not require PAN to be updated.

| From | To | Allowed? | |
| - | - | - | - |
| Individual | Sole Proprietorship | ✓ | |
| Private Limited | Public Limited | ✓ | |
| Public Limited | Private Limited | ✓ | |
| Private Limited | Section 8 Company | ✓ | |
| Section 8 Company | Private Limited | ✓ | |

> [!NOTE]
>
> **Handy Tips**
>
> Business Entity transitions that involve a change in PAN (for example, moving from an Individual to a Private Limited company) cannot be done for the same MID.

## When your PAN Changes

There can be two scenarios where a PAN change applies:

### Scenario 1: New PAN (Different entity type)

Some entity transitions inherently require a different PAN. For example, moving from an Individual to a Private Limited company means the PAN shifts from a personal PAN to a company PAN. Since all compliance documents such as proof of identity, proof of address and business registration must align with the new PAN, Razorpay cannot process this as a modification to your existing account.

### Scenario 2: Different PAN (Same entity type)

Even if your entity type stays the same, a change in PAN requires fresh documentation. For example, if your account was originally registered under your PAN and you now want to re-register it under a spouse's or partner's PAN, the following must be re-validated against the new PAN:

* Bank Account used for settlements
* Proof of identity
* Proof of address

This is effectively a fresh KYC process and cannot be completed under your existing MID.

In both scenarios described above, you must create a new Razorpay account with the updated PAN and complete fresh onboarding. Your existing MID, transaction history and settlements remain unaffected.

## When your Entity Name Changes

In case of a change in the name of your registered business (for example, after rebranding or reincorporation), the action required depends on whether your PAN changed as a result:

* **PAN unchanged**: Raise a support ticket. The Razorpay team will get in touch with you and enable you to change your entity name on your Razorpay Dashboard.
* **PAN changed**: You must create a new Razorpay account. See [Scenario 1](#scenario-1-new-pan-different-entity-type) or [Scenario 2](#scenario-2-different-pan-same-entity-type) above for details.

> [!WARNING]
>
> **Watch Out**
>
> This is a manual, backend-assisted process. You must reach out to the Razorpay team if you want to change the business details.

## How to Request an Entity Change

To request an entity type change, raise a support ticket from your Razorpay Dashboard.

1. Log in to your [Razorpay Dashboard](https://dashboard.razorpay.com).
2. Navigate to **Help & Support** and raise a ticket.
3. A ticket creation window is displayed with your MID and current entity type automatically retrieved. Ensure to add the following info to the ticket:
   * Requested entity type
   * Reason for the change
   * Supporting KYC documents for the new entity type.
4. Razorpay's compliance team reviews your request. If approved, Razorpay team will get back to you with the next steps.
5. You will be notified once the change is complete.

Once a ticket is raised, our team will resolve the ticket within 2-3 working days.

## Frequently Asked Questions

> [accordion] Can I change my entity type from Individual to Private Limited?
>
> No. This transition requires a new PAN, which is not supported. Entity changes are only allowed when the PAN remains the same.

> [accordion] Can I change my PAN on an existing Razorpay account?
>
> No. A PAN change requires a fresh set of KYC documents, whether or not it involves an entity type change. Razorpay does not support PAN updates on an existing MID. You must create a new account and complete onboarding with the new PAN.

> [accordion] How long does the process take?
>
> Timelines depend on document completeness and compliance review. Razorpay support will keep you updated via the ticket.

> [accordion] Will my existing payment history and settlements be affected?
>
> Your transaction history remains intact. However, certain account settings tied to the previous entity type may need to be reconfigured. Razorpay support will guide you if this applies to your case.

> [accordion] Can I change my entity type without raising a ticket?
>
> Not currently. All requests must go through [Help & Support](https://razorpay.com/docs/payments/dashboard/support.md).

> [accordion] What if my new entity type requires a different PAN?
>
> Razorpay does not support entity changes that require a PAN change. In such cases, you would need to create a new Razorpay account for the new entity.

## Related Topics

* [Edit Business Information](https://razorpay.com/docs/payments/dashboard/faqs.md#edit-business-information)
* [KYC Documents for Companies and Businesses](https://razorpay.com/docs/payments/business-types-kyc-documents.md)
* [Contact Support](https://razorpay.com/docs/payments/dashboard/support.md)
