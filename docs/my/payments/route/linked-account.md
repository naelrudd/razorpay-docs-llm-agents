> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Linked Accounts

> Use Linked Accounts to split payments between multiple third-parties, bank accounts and vendors. Add Linked Accounts and provide them access to issue refunds, view reversals and settlements and manage their profile.

Available in
🇮🇳 India
🇲🇾 Malaysia

Businesses need to distribute payments across multiple recipients - marketplaces paying sellers, platforms sharing revenue with partners or companies managing vendor payments. Manual fund transfers and reconciliation create operational complexity.

Razorpay Curlec Route automates this through **Linked Accounts**, splitting payments between multiple recipients while giving you central control and each recipient self-service capabilities.

## What are Linked Accounts

Linked Accounts are dedicated entities within your Route setup that receive a portion of incoming funds. Each Linked Account:

* Receives funds based on your split payment configuration.
* Has a unique `account_id` for API integration and tracking.
* Can access a dedicated dashboard for self-service operations.
* Processes refunds using available balance.

### Features

> [tab] For You (Primary Account)
>
> * **Split Payments**: Automatically divide incoming funds between multiple recipients.
> * **Central Management**: Handle settlements, refunds and reconciliations for all Linked Accounts.
> * **Access Control**: Grant or revoke dashboard permissions for each Linked Account.
> * **Complete Visibility**: Track all fund movements, transfers and operations.

> [tab] For Linked Account Users
>
> * [Process individual and bulk refunds](https://razorpay.com/docs/my/payments/route/linked-account/initiate-refund.md).
> * [View reversals and settlements](https://razorpay.com/docs/my/payments/route/linked-account/reversals-settlements.md).
> * [Manage profile and team members](https://razorpay.com/docs/my/payments/route/linked-account/manage-profile.md).

## Add Linked Accounts

Contact our [Support team](https://curlec.com/support/) to create Linked Accounts for your business.

**Settlement Timing**: Linked Account settlements take 2 working days, regardless of your primary settlement schedule.

### Required Information

Provide these details when creating a Linked Account:

> [tab] Primary Details
>
> * Linked Account name
> * Contact number
> * Email address (required for dashboard access)

> [tab] Bank Details
>
> <ul>
>   <li>Account number</li>
>   <li>Account type</li>
>
>   <li>Bank name</li>
>   <li>Beneficiary name</li>
> </ul>

## Manage Linked Account Access

> [accordion] Dashboard Access
>
> Grant dashboard access to allow Linked Account users to manage their own operations:
>
> 1. Log in to the Dashboard.
> 2. Select **Route** and navigate to the **Accounts**.
> 3. Find the relevant Linked Account and enable **Dashboard Access**.
>
>    ![Grant Dashboard access to linked accounts](https://razorpay.com/docs/build/browser/assets/images/allow-dashboard-access-la.jpg)
>
> The Linked Account user receives login credentials via email and can access their dedicated dashboard.
>
> > [!WARNING]
> >
> > **Access Requirements**
> >
> > * While you can create a Linked Account without adding their email, you cannot grant them Dashboard access. The access can be granted or provided only after you add the email address of the Linked Account.
> >
> >   ![Grant Dashboard access to linked accounts](https://razorpay.com/docs/build/browser/assets/images/route-la-email.jpg)
> > * As a Linked Account user, you cannot access the Linked Account Dashboard unless the primary account owner adds you as a team member from their Linked Account Dashboard.

> [accordion] Refund Capabilities
>
> Due to government regulations, in certain cases, the Linked Accounts need to directly process refunds to customers. You can enable refunds capability while adding a new account.
>
> To enable refunds capability for an existing account:
>
> 1. Navigate to the **Accounts** tab.
> 2. Turn on the **Allow Refunds** toggle against the relevant account.
>
>    ![Grant refund access to linked accounts](https://razorpay.com/docs/build/browser/assets/images/permit-refund-la.jpg)

## Export Account Data

Download complete account information in CSV format:

* Click **Export All (CSV)** from the Accounts tab
* Includes all account details, settlement history, and configuration

## Related Information

* [Route Overview](https://razorpay.com/docs/my/payments/route)
* [Processing Refunds](https://razorpay.com/docs/my/payments/route/linked-account/initiate-refund.md)
* [Settlements and Reversals](https://razorpay.com/docs/my/payments/route/linked-account/reversals-settlements.md)
* [Profile Management](https://razorpay.com/docs/my/payments/route/linked-account/manage-profile.md)
* [Route APIs](https://razorpay.com/docs/my/api/payments/route.md)
