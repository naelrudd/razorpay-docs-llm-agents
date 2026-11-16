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

| Functionality / Roles | Owner | Admin | Manager | Operations | Finance | Support |
| - | - | - | - | - | - | - |
| Generate API Keys | ✓ | ✓ | ✗ | ✗ | ✗ | ✗ |
| Create and manage webhooks | ✓ | ✓ | ✓ | ✗ | ✗ | ✗ |
| Manage Teams | ✓ | ✗ | ✗ | ✗ | ✗ | ✗ |
| Update brand name | ✓ | ✓ | ✗ | ✗ | ✗ | ✗ |
| Edit activation form details (including bank details) | ✓ | ✓ | ✓ | ✗ | ✓ | ✗ |
| View all transactions and settlements | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Configure payment capture settings | ✓ | ✗ | ✓ | ✗ | ✗ | ✗ |
| Configure payment methods | ✓ | ✓ | ✓ | ✗ | ✗ | ✗ |
| Capture transactions | ✓ | ✓ | ✓ | ✓ | ✗ | ✗ |
| Create refunds | ✓ | ✓ | ✓ | ✓ | ✗ | ✗ |
| Create and manage Payment Links and Customers | ✓ | ✓ | ✓ | ✓\* | ✗ | ✗ |
| Create and upload batch files | ✓ | ✓ | ✓ | ✓ | ✓ | ✗ |
| Download and email reports | ✓ | ✓ | ✓ | ✓ | ✓ | ✓\*\* |
| Install OAuth Apps | ✓ | ✗ | ✗ | ✗ | ✗ | ✗ |

> [!WARNING]
>
> **Watch Out!**
>
> * `*` - This role is limited to creating Payment Links only and does not have the authority to manage existing links or customers.
> * `**` - Monthly invoice reports excluded.

> [accordion] Owner
>
> **Actions Allowed**
>
> * Generate API Keys
> * Create and manage webhooks
> * Manage Teams
> * Update brand name
> * Edit activation form details, including bank account details, before submission
> * View all transactions and settlements
> * Configure payment capture settings
> * Configure payment methods
> * Capture transactions
> * Create refunds
> * Create and manage Payment Links and Customers
> * Create and upload batch files
> * Download and email reports
> * Install OAuth Apps

> [accordion] Admin
>
> **Actions Allowed**
>
> * Generate API Keys
> * Create and manage webhooks
> * Update brand name
> * Edit activation form details, including bank account details, before submission
> * Configure payment methods
> * View all transactions and settlements
> * Capture transactions
> * Create refunds
> * Create and manage Payment Links and Customers
> * Create and upload batch files
> * Download and email reports
>
> **Actions Not Allowed**
>
> * Manage Teams

> [accordion] Manager
>
> **Actions Allowed**
>
> * Create and manage webhooks
> * Edit activation form details, before submission
> * Configure payment capture settings
> * Configure payment methods
> * View all transactions and settlements
> * Capture transactions
> * Create refunds
> * Create and manage Payment Links and Customers
> * Create and upload batch files
> * Download and email reports
>
> **Actions Not Allowed**
>
> * Generate API Keys
> * Manage Teams

> [accordion] Operations
>
> **Actions Allowed**
>
> * View all transactions and settlements
> * Capture transactions
> * Create refunds
> * Create Payment Links
> * Create and upload batch files
> * Download and email reports
>
> **Actions Not Allowed**
>
> * Generate API Keys
> * Manage Teams
> * Edit activation form details, including bank account details, before submission

> [accordion] Finance
>
> **Actions Allowed**
>
> * Edit activation form details, before submission
> * View all transactions and settlements
> * Create and upload batch files
> * Download and email reports
>
> **Actions Not Allowed**
>
> * Generate API Keys
> * Create and manage webhooks
> * Manage Teams
> * Capture transactions
> * Create refunds
> * Create and manage Payment Links and Customers

> [accordion] Support
>
> **Actions Allowed**
>
> * View all transactions and settlements
> * Download and email reports other than the monthly invoice report
>
> **Actions Not Allowed**
>
> * Generate API Keys
> * Create and manage webhooks
> * Manage Teams
> * Edit activation form details, including bank account details, before submission
> * Capture transactions
> * Create refunds
> * Create and manage Payment Links and Customers
> * Create and upload batch files
> * Access monthly invoice report

> [!NOTE]
>
> **Handy Tips**
>
> A team member can be assigned only one role, as each role is tied to a specific email address. A user can have multiple roles if they have different email addresses.

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
>
> 2. Navigate to the **Account & Settings** → **Business settings** and click **Invitations**.
>
> 3. Click **Accept** next to the invite.
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
> * **If they use an authenticator app and still receive SMS on their verified phone number**, for example on a new phone with the same number, they can click **Use SMS OTP** on the **Two Step Verification** screen to sign in. They can then turn off the authenticator app and set it up again on the new phone. Know more about [what to do with a new or lost phone](https://razorpay.com/docs/sg/payments/dashboard/account-settings/security-sign-in.md#new-phone-or-lost-phone).
> * **If they use an authenticator app and cannot sign in**, they should raise a request with our [Support Team](https://razorpay.com/sg/support/). The account owner's **Invalidate 2FA** option does not remove the authenticator app.
> * **If they do not use an authenticator app**, they should reach out to their respective account owner. The account owner can **Invalidate 2FA** for the user, that is reset 2FA for the user. The user will be asked to enter their mobile number the next time they log in to the Dashboard.

> [accordion] What to do if the account owner is locked?
>
> If you are the account owner and have entered the wrong OTP 9 times, your account will be locked for security reasons. In such scenarios, contact our [Support Team](https://razorpay.com/sg/support/) to **Reset 2FA** for your account.

> [accordion] What to do if the account owner loses their mobile device?
>
> If you are the account owner and have lost your mobile device:
>
> * **If you use an authenticator app and still receive SMS on your verified phone number**, click **Use SMS OTP** on the **Two Step Verification** screen to sign in. Then turn off the authenticator app and set it up again on your new phone. Know more about [what to do with a new or lost phone](https://razorpay.com/docs/sg/payments/dashboard/account-settings/security-sign-in.md#new-phone-or-lost-phone).
> * **If you use an authenticator app and cannot sign in**, contact our [Support Team](https://razorpay.com/sg/support/) for help signing in.
> * **If you do not use an authenticator app**, contact our [Support Team](https://razorpay.com/sg/support/) to **Reset 2FA** for your account.
