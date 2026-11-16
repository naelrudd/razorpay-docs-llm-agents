> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Manage Team

> Manage your team, add or remove users and provide appropriate roles to control access on the Razorpay Dashboard.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Manage your team of users who can access the Dashboard. You can provide specific access to a user or a set of users.

**Example**

You need someone in your organisation to perform day-to-day operations such as handling refunds and settlements. In this case, you can give Dashboard access to a person and assign the **Operations** role. This limits their access to actions related to refunds and settlements only.

## Standard User Roles

There are some predefined user roles that you can assign to your team members. You can use these roles to limit a user's access to the Dashboard. Check each role and the permissions associated with it.

> [accordion] Owner
>
> **Actions Allowed**
>
> <ul>
>   <li>Generate API keys</li>
>   <li>Create and manage webhooks</li>
>   <li>Manage teams</li>
>   <li>Update brand name</li>
>   <li>Edit activation form details, including bank account details and GST number, before submission</li>
>   <li>View all transactions and settlements</li>
>   <li>View all disputes</li>
>   <li>Accept all disputes</li>
>   <li>Contest all disputes and submit evidence</li>
>   <li>Configure payment capture settings</li>
>   <li>Configure payment methods</li>
>   <li>Capture transactions</li>
>   <li>Create refunds</li>
>   <li>Create and manage Invoices, Plans and Subscription Links, Customer Identifiers, Customers, Payment Pages and Payment Links.</li>
>   <li>Edit Razorpay Linked Account details</li>
>   <li>Create and upload batch files</li>
>   <li>Download and email reports</li>
>   <li>Use Payments Mobile App</li>
>   <li>Create Offers.</li>
>   <li>Install OAuth Apps</li>
>   <li>View and download API/webhooks logs (Developers > APIs/Webhooks)</li>
> </ul>

> [accordion] Pseudo Owner
>
> The Pseudo Owner role provides full owner-level access to trusted team members for business continuity when the primary owner is unavailable (on leave, travel or emergencies). This role has identical permissions to the Owner role with enhanced audit tracking.
>
> **Actions Allowed**
>
> <ul>
>   <li>All permissions identical to Owner role</li>
>   <li>Generate API keys</li>
>   <li>Create and manage webhooks</li>
>   <li>Manage teams (invite, modify, deactivate users)</li>
>   <li>Update brand name</li>
>   <li>Edit activation form details, including bank account details and GST number</li>
>   <li>View and modify settlement bank account details</li>
>   <li>View all transactions and settlements</li>
>   <li>View all disputes</li>
>   <li>Accept all disputes</li>
>   <li>Contest all disputes and submit evidence</li>
>   <li>Configure payment capture settings</li>
>   <li>Configure payment methods</li>
>   <li>Capture transactions</li>
>   <li>Create refunds (any amount)</li>
>   <li>Create and manage Invoices, Plans and Subscription Links, Customer Identifiers, Customers, Payment Pages and Payment Links.</li>
>   <li>Edit Razorpay Linked Account details</li>
>   <li>Create and upload batch files</li>
>   <li>Download and email reports</li>
>   <li>Use Payments Mobile App</li>
>   <li>Create Offers</li>
>   <li>Install OAuth Apps</li>
>   <li>View and download API/Webhooks logs</li>
> </ul>
>
> **Actions Not Allowed**
>
> * Delete the primary owner account
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > * Maximum of 2 Pseudo Owners allowed per Razorpay account.
> > * Assignment requires additional authentication (OTP/2FA).
> > * Owner receives email confirmation when a Pseudo Owner is assigned.
> > * All actions are logged with "Pseudo Owner" designation for audit purposes.

> [accordion] View-Only (Auditor)
>
> The View-Only role provides complete visibility into all Dashboard data without any ability to perform actions or make changes. This role is designed for stakeholders who need to monitor, review or audit your payment operations.
>
> **Actions Allowed**
>
> <ul>
>   <li>View all transactions and settlements</li>
>   <li>View all disputes</li>
>   <li>View analytics and insights</li>
>   <li>View configuration and settings pages (read-only)</li>
>   <li>Navigate all Dashboard sections</li>
> </ul>
>
> **Actions Not Allowed**
>
> <ul>
>   <li>Generate API keys</li>
>   <li>Create and manage webhooks</li>
>   <li>Manage teams</li>
>   <li>Capture transactions</li>
>   <li>Create refunds</li>
>   <li>Accept or contest disputes</li>
>   <li>Create and manage Razorpay Invoices, Payment Pages, Payment Links</li>
>   <li>Edit activation form details, including bank account details</li>
>   <li>Create and upload batch files</li>
>   <li>Download or export files</li>
>   <li>Edit any settings or configurations</li>
>   <li>Edit Razorpay Linked Account details</li>
>   <li>Modify API keys or webhook URLs</li>
>   <li>Change account settings, bank details or KYC information</li>
> </ul>
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > * All operational buttons (Refund, Create Payout, Edit Settings, Save) are hidden or disabled.
> > * Form fields on configuration pages are displayed in read-only mode.
> > * Attempting any restricted action displays: "Permission Denied. Please contact the owner."
> > * All page views are logged for audit and compliance purposes.
>
> > [!NOTE]
> >
> > **View-Only (Auditor) Role is Best For**
> >
> > * Internal and external auditors
> > * Compliance officers
> > * Senior management and executives
> > * Business analysts
> > * Regulatory reviewers

> [accordion] Admin
>
> **Actions Allowed**
>
> <ul>
>   <li>Generate API Keys</li>
>   <li>Create and manage webhooks</li>
>   <li>Update brand name</li>
>   <li>Edit activation form details, including bank account details and GST number, before submission.</li>
>   <li>Configure payment methods</li>
>   <li>View all transactions and settlements</li>
>   <li>View all disputes</li>
>   <li>Accept all disputes</li>
>   <li>Contest all disputes and submit evidence</li>
>   <li>Capture transactions</li>
>   <li>Create refunds</li>
>   <li>Create and manage Invoices, Plans and Subscription Links, Customers, Customer Identifiers, Payment Pages and Payment Links.</li>
>   <li>Create and upload batch files</li>
>   <li>Download and email reports</li>
>   <li>Use Payments Mobile App</li>
>   <li>Create Offers</li>
>   <li>Edit Razorpay Linked Account details</li>
> </ul>
>
> **Actions Not Allowed**
>
> * Manage Teams

> [accordion] Manager
>
> **Actions Allowed**
>
> <ul>
>   <li>Create and manage webhooks</li>
>   <li>Edit activation form details, including GST number, before submission</li>
>   <li>Configure payment capture settings</li>
>   <li>Configure payment methods</li>
>   <li>View all transactions and settlements</li>
>   <li>View all disputes</li>
>   <li>Accept all disputes</li>
>   <li>Contest all disputes and submit evidence</li>
>   <li>Capture transactions</li>
>   <li>Create refunds</li>
>   <li>Create and manage Invoices, Plans and Subscription Links, Customers, Customer Identifiers, Payment Pages and Payment Links. </li>
>   <li>Create and upload batch files</li>
>   <li>Download and email reports</li>
>   <li>Use Payments Mobile App</li>
>   <li>Edit Razorpay Linked Account details</li>
> </ul>
>
> **Actions Not Allowed**
>
> <ul>
>   <li>Generate API Keys</li>
>   <li>Manage Teams</li>
>   <li>Resend Subscription Registration link</li>
> </ul>

> [accordion] Operations
>
> **Actions Allowed**
>
> <ul>
>   <li>View all transactions and settlements</li>
>   <li>View all disputes</li>
>   <li>Accept all disputes</li>
>   <li>Contest all disputes and submit evidence</li>
>   <li>Capture transactions</li>
>   <li>Create refunds</li>
>   <li>Create Invoices, Payment Buttons, Customer Identifiers, Payment Links and Payment Pages.</li>
>   <li>Create and upload batch files</li>
>   <li>Download and email reports</li>
>   <li>Use Payments Mobile App</li>
> </ul>
>
> **Actions Not Allowed**
>
> <ul>
>   <li>Generate API Keys</li>
>   <li>Manage Teams</li>
>   <li>Edit activation form details, including bank account details and GST number, before submission</li>
>   <li>Edit Razorpay Linked Account details</li>
> </ul>

> [accordion] Finance
>
> **Actions Allowed**
>
> <ul>
>   <li>Edit activation form details including GST number, before submission</li>
>   <li>View all transactions and settlements</li>
>   <li>View all disputes</li>
>   <li>Accept all disputes</li>
>   <li>Contest all disputes and submit evidence</li>
>   <li>Create and upload batch files</li>
>   <li>Download and email reports</li>
> </ul>
>
> **Actions Not Allowed**
>
> <ul>
>   <li>Generate API Keys</li>
>   <li>Create and manage webhooks</li>
>   <li>Manage Teams</li>
>   <li>Capture transactions</li>
>   <li>Create refunds</li>
>   <li>Create and manage Invoices, Plans and Subscription Links, Customers, Customer Identifiers Payment Pages and Payment Links.</li>
>   <li>Edit Razorpay Linked Account details</li>
> </ul>

> [accordion] ePos
>
> **Actions Allowed**
>
> <ul>
>   <li>Create Invoices and Payment Links in INR only</li>
>   <li>Create, view and edit Offers</li>
>   <li>Create, view and edit Payment Page</li>
>   <li>Create, view and edit Payment Button</li>
>   <li>Create, view and edit Payment Handle</li>
> </ul>
>
> **Actions Not Allowed**
>
> <ul>
>   <li>Generate API Keys</li>
>   <li>Edit activation form details including GST number, before submission</li>
>   <li>Create and manage webhooks</li>
>   <li>Manage Teams</li>
>   <li>View all transactions and settlements</li>
>   <li>View all disputes</li>
>   <li>Accept all disputes</li>
>   <li>Contest all disputes and submit evidence</li>
>   <li>Capture transactions</li>
>   <li>Create refunds</li>
>   <li>Edit Razorpay Linked Account details</li>
>   <li>Create and upload batch files</li>
>   <li>Download and email reports</li>
>   <li>Create Items</li>
>   <li>View Invoices, Payment Pages, Payment Links created by other users</li>
> </ul>

> [accordion] Dispute Manager
>
> The Dispute Manager role is designed for team members who handle chargebacks and payment disputes. This role provides focused access to dispute management functions while restricting access to sensitive financial operations.
>
> **Actions Allowed**
>
> * View all disputes and dispute details
> * Accept disputes
> * Contest disputes and submit evidence
> * Download dispute reports
> * Search and filter disputes
> * View dispute summary metrics (pending, accepted, contested)
>
> **Actions Not Allowed**
>
> <ul>
>   <li>Generate API keys</li>
>   <li>Create and manage webhooks</li>
>   <li>Manage teams</li>
>   <li>View transactions (except dispute-related context)</li>
>   <li>View settlements</li>
>   <li>View or edit bank account details</li>
>   <li>Create refunds</li>
>   <li>Capture transactions</li>
>   <li>Edit activation form details</li>
>   <li>Edit Razorpay account or business settings</li>
>   <li>Create and manage Razorpay Invoices, Payment Pages, Payment Links</li>
>   <li>Create and upload batch files (non-dispute)</li>
>   <li>Download reports (except dispute reports)</li>
>   <li>Edit Razorpay Linked Account details</li>
>   <li>Use Payments Mobile App</li>
> </ul>
>
> > [!NOTE]
> >
> > **Dispute Manager Role is Best For**
> >
> > * Dedicated chargeback teams.
> > * Customer support specialists handling dispute cases.
> > * Third-party dispute management agencies.

> [accordion] Marketing (Offers Manager)
>
> **Actions Allowed**
>
> <ul>
>   <li>Create offers</li>
> </ul>
>
> **Actions Not Allowed**
>
> <ul>
>   <li>View or manage payments</li>
>   <li>View settlements</li>
>   <li>View or manage disputes</li>
>   <li>Create refunds</li>
>   <li>Generate API keys</li>
>   <li>Download or email general reports</li>
> </ul>

> [accordion] Finance Manager
>
> **Actions Allowed**
>
> <ul>
>   <li>View Payments, Payment Links, Payment Pages and the Settlements tab</li>
>   <li>View all transactions and settlements</li>
>   <li>Capture payments</li>
>   <li>Capture transactions</li>
>   <li>View all disputes</li>
>   <li>Create refunds</li>
>   <li>Create and manage Invoices, Plans and Subscription Links, Customer Identifiers, Customers, Payment Pages and Payment Links</li>
>   <li>Create and upload batch files</li>
>   <li>Download and email reports</li>
> </ul>
>
> **Actions Not Allowed**
>
> <ul>
>   <li>Generate API keys</li>
>   <li>Create and manage webhooks</li>
>   <li>Accept, defend or contest disputes (view only)</li>
>   <li>Edit activation form details</li>
>   <li>Edit Razorpay Linked Account details</li>
>   <li>Create Offers</li>
> </ul>

> [accordion] Fraud Operations
>
> **Actions Allowed**
>
> <ul>
>   <li>View Payments, Payment Links, Payment Pages and the Settlements tab</li>
>   <li>View all transactions and settlements</li>
>   <li>View all disputes</li>
>   <li>Accept/defend all disputes (chargebacks)</li>
>   <li>Contest all disputes and submit evidence</li>
> </ul>
>
> **Actions Not Allowed**
>
> <ul>
>   <li>Create refunds</li>
>   <li>Edit settlement or bank account details</li>
>   <li>Generate API keys</li>
>   <li>Create Offers</li>
>   <li>Manage billing entities</li>
> </ul>

> [accordion] Fraud Analyst
>
> **Actions Allowed**
>
> <ul>
>   <li>View Payments, Payment Links, Payment Pages and the Settlements tab</li>
>   <li>View all transactions and settlements</li>
>   <li>View all disputes</li>
> </ul>
>
> **Actions Not Allowed**
>
> <ul>
>   <li>Accept, defend or contest disputes</li>
>   <li>Create refunds</li>
>   <li>Edit any settings or configurations</li>
>   <li>Generate API keys</li>
> </ul>

> [accordion] R\&D
>
> The R\&D role is designed for developers and engineering teams who need to configure and troubleshoot webhooks without access to payments, settlements or other financial operations.
>
> **Actions Allowed**
>
> <ul>
>   <li>Create, view, edit and delete webhooks</li>
>   <li>View webhook logs, including the event logs and request/response headers for each delivery attempt (last 3 hours)</li>
> </ul>
>
> **Actions Not Allowed**
>
> <ul>
>   <li>Generate API keys</li>
>   <li>View or manage payments</li>
>   <li>View or manage disputes</li>
>   <li>Create refunds</li>
>   <li>View settlements</li>
>   <li>Create Offers</li>
>   <li>Download and email reports</li>
>   <li>Manage Teams</li>
> </ul>

> [accordion] Support
>
> **Actions Allowed**
>
> <ul>
>   <li>View all transactions and settlements</li>
>   <li>View all disputes</li>
>   <li>Accept all disputes</li>
>   <li>Download and email reports other than the monthly invoice report</li>
> </ul>
>
> **Actions Not Allowed**
>
> <ul>
>   <li>Generate API Keys</li>
>   <li>Create and manage webhooks</li>
>   <li>Manage Teams</li>
>   <li>Edit activation form details, including bank account details and GST number, before submission</li>
>   <li>Capture transactions</li>
>   <li>Create refunds</li>
>   <li>Create and manage Invoices, Plans and Subscription Links, Customers, Customer Identifiers, Payment Pages and Payment Links.</li>
>   <li>Edit Razorpay Linked Account details</li>
>   <li>Create and upload batch files</li>
>   <li>Access monthly invoice report</li>
> </ul>

> [!NOTE]
>
> **Handy Tips**
>
> A team member can be assigned only one role, as each role is tied to a specific email address. A user can have multiple roles if they have different email addresses.

> [!NOTE]
>
> **Handy Tips**
>
> * A team member should be assigned a role as the role is tied to an email address. A user can have multiple roles if they have different email ids.
> * Use the [Dispute Manager](https://razorpay.com/docs/payments/dashboard/account-settings/manage-team.md#dispute-manager) role for team members who only need to handle chargebacks without access to refunds or bank details.
> * Use the [Pseudo Owner](https://razorpay.com/docs/payments/dashboard/account-settings/manage-team.md#pseudo-owner) role sparingly for trusted individuals who need to manage the account when the Owner is unavailable.
> * Use the [View-Only](https://razorpay.com/docs/payments/dashboard/account-settings/manage-team.md#view-only-auditor) role for auditors and stakeholders who need visibility without operational access.

> [accordion] Invite a Registered User
>
> 1. Log in to the Dashboard.
> 2. Navigate to the **Account & Settings** → **Business settings** and click **Manage Team**.
> 3. Click **Invite New Member**.
> 4. Type in the email address of the user whom you want to invite. Select a role from the drop-down list.
> 5. Click **Send Invitation** to invite the user. A list of accepted and pending invitations is displayed on the same page.
> 6. Click **Resend** to re-invite the user or **Cancel** to cancel the invitation.

> [accordion] Accept Invite - Existing User
>
> To accept an invitation:
>
> 1. Log in to the Dashboard.
> 2. Navigate to the **Account & Settings** → **Business settings** and click **Invitations**.
> 3. Click **Accept** next to the invite.
>
> ![Accept invite to be team member (for an existing Razorpay user)](https://razorpay.com/docs/build/browser/assets/images/dashboard-guide-accept-invitation.jpg)
>
> > [!NOTE]
> >
> > **Switching Accounts**
> >
> > After accepting the invite, the invited user can switch between their and your account using the **Switch Merchant** option available on the Dashboard header.
> > You cannot access their account unless they invite you to join their team.

> [accordion] Invite a New User
>
> You can invite a user who is not registered with Razorpay to join your team. Such users are sent an invitation link via email.
>
> To invite a new user:
>
> 1. Log in to the Dashboard.
> 2. Navigate to the **Account & Settings** → **Business settings** and click **Manage Team**.
> 3. Click **Invite New Member**.
> 4. Enter the member's email id and select the user role to be assigned.
> 5. Click **Send Invitation**.
>
> ![Send invite to new member (for a new Razorpay user)](https://razorpay.com/docs/build/browser/assets/images/dashboard-guide-invite-new-user.jpg)

> [accordion] Update Role of a User
>
> You can change the user's role after the invitation is sent to the user or after the invitation is accepted by the user.
>
> To update a user's role:
>
> 1. Log in to the Dashboard.
> 2. Navigate to the **Account & Settings** → **Business settings** and click **Manage Team**.
> 3. Select the new role for the user from the drop-down.
> 4. Click **Update**.

> [accordion] Remove a User
>
> You can remove a user from your team to remove their complete access from your Dashboard.
>
> To remove a user from your team:
>
> 1. Log in to the Dashboard.
> 2. Navigate to the **Account & Settings** → **Business settings** and click **Manage Team**.
> 3. Click **Remove** to remove a user from the **Team Member** list. Once removed, the user can no longer access your Dashboard.
> 4. Click **Cancel** to remove a user from the **Pending Invitations** list.

> [accordion] Enable 2-Step Verification (2FA at Team Level)
>
> You can set 2-step verification for your entire team for enhanced security and protection of your Dashboard data thus preventing malicious attacks or misuse of your sensitive business data.
>
> To enable 2-step verification for your team:
>
> 1. Log in to the Dashboard.
> 2. Navigate to the **Account & Settings** → **Business settings** and click **Manage Team**.
> 3. Enable the **2-Step Verification to the team** option.
> 4. Enter the OTP sent to your registered mobile device. (This step is not required if you had already performed OTP verification during login.)
> 5. Enter your account password and confirm.
>
> You have now set up 2FA for your entire team.

## Frequently Asked Questions (FAQs)

> [accordion] What to do if a user account is locked?
>
> If a user enters the wrong OTP 9 times, their account will be locked for security reasons. In such scenarios, the user should contact their respective account owner. The account owner can unlock the users' accounts.

> [accordion] What to do if a user loses their mobile device?
>
> If a user loses their mobile device:
>
> * **If they use an authenticator app and still receive SMS on their verified phone number**, for example on a new phone with the same number, they can click **Use SMS OTP** on the **Two Step Verification** screen to sign in. They can then turn off the authenticator app and set it up again on the new phone. Know more about [what to do with a new or lost phone](https://razorpay.com/docs/payments/dashboard/account-settings/security-sign-in.md#new-phone-or-lost-phone).
> * **If they use an authenticator app and cannot sign in**, they should raise a request with our [Support Team](https://razorpay.com/support/#request). The account owner's **Invalidate 2FA** option does not remove the authenticator app.
> * **If they do not use an authenticator app**, they should reach out to their respective account owner. The account owner can **Invalidate 2FA** for the user, that is reset 2FA for the user. The user will be asked to enter their mobile number the next time they log in to the Dashboard.

> [accordion] What to do if the account owner is locked?
>
> If you are the account owner and have entered the wrong OTP 9 times, your account will be locked for security reasons. In such scenarios, contact our [Support Team](https://razorpay.com/support/#request) to **Reset 2FA** for your account.

> [accordion] What to do if the account owner loses their mobile device?
>
> If you are the account owner and have lost your mobile device:
>
> * **If you use an authenticator app and still receive SMS on your verified phone number**, click **Use SMS OTP** on the **Two Step Verification** screen to sign in. Then turn off the authenticator app and set it up again on your new phone. Know more about [what to do with a new or lost phone](https://razorpay.com/docs/payments/dashboard/account-settings/security-sign-in.md#new-phone-or-lost-phone).
> * **If you use an authenticator app and cannot sign in**, contact our [Support Team](https://razorpay.com/support/#request) for help signing in.
> * **If you do not use an authenticator app**, contact our [Support Team](https://razorpay.com/support/#request) to **Reset 2FA** for your account.

> [accordion] What is the Dispute Manager role?
>
> The Dispute Manager role is designed for team members who handle chargebacks and payment disputes. Users with this role can view, accept and contest disputes and download dispute reports. They cannot create refunds or access settlement/bank details. This role is ideal for dedicated chargeback teams or third-party dispute management agencies.

> [accordion] What is the Pseudo Owner role?
>
> The Pseudo Owner role provides full owner-level access to trusted team members for business continuity. It is useful when the primary owner is unavailable (on leave, travel or emergencies). Pseudo Owner role has the same permissions as the Owner role except they cannot delete the primary owner account. A maximum of 2 Pseudo Owners can be assigned per account and assignment requires additional authentication.

> [accordion] What is the View-Only (Auditor) role?
>
> The View-Only role provides read-only access to all Dashboard data. Users with this role can view transactions, settlements, disputes and settings but cannot perform any actions or make changes. This role is ideal for auditors, compliance officers and senior management who need visibility without operational access. All page views are logged for audit purposes.

> [accordion] How many Pseudo Owners can I have?
>
> You can provide Pseudo Owner access to a maximum of 2 users for each Razorpay account. If you need more, contact [Razorpay support](https://razorpay.com/support/#request) to discuss your requirements.

> [accordion] Can a Dispute Manager issue refunds?
>
> No, Dispute Managers cannot create refunds. If a refund is needed to resolve a dispute, the Dispute Manager must coordinate with a team member who has refund permissions (Owner, Pseudo Owner, Admin, Manager or Operations roles).

> [accordion] Can a View-Only user download reports?
>
> No, users with view-only access can only view reports and data on the Dashboard. They cannot download or export files. This restriction helps maintain data security for audit and compliance purposes.

> [accordion] What is the R\&D role?
>
> The R\&D role is designed for developers and engineering teams who manage webhooks. Users with this role can create, view, edit and delete webhooks and view webhook logs (event logs and request/response headers from the last 3 hours). They cannot generate API keys, view payments, settlements or disputes, create refunds or manage teams. This role is ideal for engineering teams that need to configure and troubleshoot webhook deliveries without access to financial operations.
