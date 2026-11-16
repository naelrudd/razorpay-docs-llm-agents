> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Enable Store Credit Scopes - Shopify Magic Checkout

> Add the Shopify store credit scopes to your Magic Checkout app from the Shopify Dev Dashboard so that customers can redeem their store credit at checkout.

Available in
🇮🇳 India

Magic Checkout supports the redemption of Shopify store credit. To let customers use their store credit at checkout, the Magic Checkout app on your Shopify store needs access to store credit data. You give it this access by adding three store credit scopes (permissions) to the app and approving them on your store.

You complete these steps in the Shopify Admin and the Shopify Dev Dashboard. No code changes are needed.

> [!WARNING]
>
> **Watch Out!**
>
> Customers can redeem store credit on Magic Checkout only after you add these scopes and approve them on your store.

## Prerequisites

* Magic Checkout is installed on your Shopify store. Know more about [integrating Magic Checkout with Shopify](https://razorpay.com/docs/payments/magic-checkout/shopify.md).
* You can log in to the Shopify Admin of the store and to the Shopify Dev Dashboard of the organisation that owns the app.

## Scopes to Add

| Scope | What It Allows |
| - | - |
| `read_store_credit_accounts` | View store credit accounts. |
| `read_store_credit_account_transactions` | View store credit account transactions. |
| `write_store_credit_account_transactions` | Create store credit account transactions. |

The steps are in three parts:

1. [Find your Magic Checkout app](#1-find-your-magic-checkout-app).
2. [Release a new version with the store credit scopes](#2-release-a-new-version-with-the-store-credit-scopes).
3. [Approve the new permissions on your store](#3-approve-the-new-permissions-on-your-store).

The numbers on the screenshots match the step numbers.

## 1. Find Your Magic Checkout App

1. Log in to your Shopify Admin. At the bottom-left of the screen, click **Settings**.

   ![settings option at the bottom-left of the shopify admin](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-01-settings.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=d97106b4aae4ac484230ef173e9c2e53)

2. In the **Settings** sidebar, click **Apps**.

   ![apps option in the shopify settings sidebar](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-02-apps.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=cad3bfef42510c0e58fbdf2650bd8fa3)

3. The **Apps** page lists the apps installed on your store. Find the Magic Checkout app, listed as `<App ID> - MagicCheckout`, and copy its App ID. Then click **Develop apps** at the top-right.

   ![magic checkout app listed with its app id and the develop apps button](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-03-app-id.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=f8383487cc811c4289acc9d85cb95f1d)

4. The **App development** page opens. Click **Build apps in Dev Dashboard**.

   ![build apps in dev dashboard button on the app development page](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-04-dev-dashboard.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=ddfa789061a620bc8fa23ce49e3f1d2e)

5. You are redirected to the Shopify Dev Dashboard. In the left sidebar, click **Apps**.

   ![apps option in the shopify dev dashboard sidebar](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-05-dev-apps.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=73bdef46219829b1bfb6177c074ca3de)

6. Paste the App ID you copied in step 3 into the search bar. Two entries named MagicCheckout may appear. Click the one with the most recent **Updated** date.

   ![search results for the app id with the most recently updated app highlighted](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-06-search-app.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=ecfd48dc323d6cdf632e49a106d519d4)

## 2. Release a New Version with the Store Credit Scopes

7. The app overview page opens. In the left sidebar, click **Versions**.

   ![versions option in the app sidebar on the dev dashboard](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-07-versions.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=f2eab75587f6539ebaf3f339456e8f86)

8. At the top-right of the **Versions** page, click **Create version**.

   ![create version button on the versions page](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-08-create-version.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=cfbc3f53676cb37fcd84c402632b261a)

9. The **Create version** page opens, pre-filled from your current version. Enter a name in **App name**, for example, Magic checkout store credit. Then, under **API access**, click **Select from list** next to **Scopes**.

   ![app name field and select from list option for scopes on the create version page](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-09-app-name.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=f6c6e95ba8ce1892d54ed15cb30c016f)

10. In the **Select scopes** window, enter `store_credit` in the search box and select all three scopes listed below. Then click **Done**.

    * `read_store_credit_accounts`
    * `read_store_credit_account_transactions`
    * `write_store_credit_account_transactions`

    ![select scopes window with the search box and done button](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-10-select-scopes.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=14a5167215a373ffdbb381f59aff26b3)

11. Scroll to the bottom of the **Create version** page and click **Release**. Click **Release** again in the confirmation pop-up. Releasing makes the new version the **Active** version. Your earlier versions stay listed on the **Versions** page.

12. The **Versions** page now lists your new version at the top with an **Active** label.

    ![new version listed at the top of the versions page with the active label](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-12-active-version.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=ebf85d8830f78e251d04dc9dde1e0efd)

## 3. Approve the New Permissions on Your Store

13. In the left sidebar, click **Overview**. Then, at the top-right, click **Install app**.

    ![overview option and install app button on the dev dashboard](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-13-install-app.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=0c49876541331ae1e9ccaf5447c54375)

14. You are asked to choose a store. Click the store where Magic Checkout is installed.

    ![choose a store page on shopify](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-14-choose-store.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=a68fcfee1f7079599d54931a46db7c2c)

15. Shopify opens the **Update data access** page in your store's admin and lists the permissions the app needs, including store credit. Click **Update**.

    ![update data access page listing the store credit permissions](https://mintcdn.com/razorpay-881012b3/XfWMJP6jTxZKgxQL/static/docs-home/assets/magic-store-credit-scopes-15-update-access.png?fit=max\&auto=format\&n=XfWMJP6jTxZKgxQL\&q=85\&s=42c0161daf5fd5a3c9280b5ed99727e1)

Your Magic Checkout app now has the store credit scopes. No further action is needed in Shopify.

> [!NOTE]
>
> **Need Help?**
>
> If you cannot find the app, or a step looks different on your store, contact your Razorpay Magic Checkout point of contact or write to us at [magic-checkout-support@razorpay.com](mailto:magic-checkout-support@razorpay.com). Share a screenshot of the page you are on.

### Related Information

* [Magic Checkout Shopify Integration](https://razorpay.com/docs/payments/magic-checkout/shopify.md)
* [Magic Checkout Shopify Features](https://razorpay.com/docs/payments/magic-checkout/shopify/features)
