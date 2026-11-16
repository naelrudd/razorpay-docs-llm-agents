> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Troubleshooting & FAQs

> Find answers to frequently asked questions about BigCommerce plugin.

Available in
🇮🇳 India

> [accordion] How can I verify if the plugin is installed successfully?
>
> On your BigCommerce Dashboard, navigate to **Channel Manager** → **Storefronts** section.
>
> ![specific and meaningful image title](https://razorpay.com/docs/build/browser/assets/images/bigcommerce-verify-installation.jpg)
>
> There are two ways to verify the installation:
>
> ### Web Pages
>
> 1. Click **Web pages**.
> 2. Ensure the **Razorpay Order Confirmation** page appears.
>
> ![Verify installation through web pages](https://razorpay.com/docs/build/browser/assets/images/bigcommerce-web-page.jpg)
>
> ### Scripts
>
> 1. Click **Scripts**.
> 2. Ensure the Razorpay **Header** and **Footer** scripts appear.
>
> ![Verify installation through scripts](https://razorpay.com/docs/build/browser/assets/images/bigcommerce-script.jpg)

> [accordion] How can I verify if webhooks are auto-configured?
>
> To verify if webhooks are enabled:
>
> 1. Log in to the Razorpay Dashboard and navigate to **Account & Settings**.
> 2. In the **Website and app settings** section, click **Webhooks**.
>
>    ![Navigate to Webhooks](https://razorpay.com/docs/build/browser/assets/images/account-settings-webhooks.jpg)
> 3. Select the relevant webhook **URL**.
> 4. On the right panel, check if the status for `order.paid` and `refund.processed` is enabled.

> [accordion] Why am I asked to approve a new Checkout Write permission for the Razorpay Payment App?
>
> Following a bug fix on BigCommerce's side, the Razorpay Payment App now requires an additional access permission: **Checkout Write**. If you currently use the Razorpay Payment App, you must approve this new permission to ensure the integration continues to function correctly.
>
> Follow these steps to reauthorise the app:
>
> 1. Log in to your **BigCommerce Store Control Panel**.
>
> 2. Navigate to **Apps** → **My Apps** (or the installed apps section).
>
> 3. Locate and open the **Razorpay Payment App**.
>
> 4. BigCommerce displays a prompt requesting approval for the updated app permissions.
>
> 5. Review the new **Checkout Write** permission and click **Update**, **Authorize** or **Accept**, as displayed.
>
> 6. Once authorisation is complete, reopen the Razorpay Payment App to confirm it loads successfully.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > * Complete this authorisation using the store owner account or an account with the required app permissions.
> > * You do not need to uninstall or reinstall the app as part of the standard reauthorisation process.
>
> If the permission prompt does not appear or the update fails, contact [Razorpay Support](https://razorpay.com/support).

> [accordion] Does the BigCommerce plugin support 3 or 0 decimal unit currencies?
>
> The BigCommerce plugin currently supports only currencies that use 2 decimal units. For example: USD, EUR, INR. It does not support currencies with 0 decimal (for example, JPY) or 3 decimal units (for example, BHD).
