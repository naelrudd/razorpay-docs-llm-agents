> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Manage API Key Secrets

> Generate, rotate and revoke multiple API key secrets using the Razorpay Dashboard.

Available in
🇮🇳 India

> [!NOTE]
>
> **Feature Availability**
>
> Multiple secrets are being rolled out to merchants in phases. If the **API Keys** page on your Dashboard shows separate **Public keys** and **Secrets** sections, this feature is enabled for your account. Otherwise, follow the steps to [regenerate API keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#regenerate-api-keys).

Your API key has two parts:

* **Public key** (`key_id`): Identifies your account. It is safe to use in your website or app code.
* **Secret** (`key_secret`): Authenticates your API requests. Never put a secret in your website or app code.

With multiple secrets, you can keep up to 10 secrets in each mode (**Test** and **Live**). Any active public key works with any active secret in the same mode. This lets you:

* Give each server or vendor its own secret, so you can revoke one without affecting the others.
* Rotate a secret without downtime. The old and new secrets both work for 24 hours while you update your servers.

![API Keys page on the Razorpay Dashboard with separate Public keys and Secrets sections](https://mintcdn.com/razorpay-881012b3/pXO9BYiUirLuZXk1/static/docs-home/assets/api-key-secrets-overview.jpg?fit=max\&auto=format\&n=pXO9BYiUirLuZXk1\&q=85\&s=4f8459989de8fc972543caabd0d6c48c)

> [!NOTE]
>
> **Two-Factor Authentication**
>
> In **Live Mode**, you must verify your identity with an OTP before you generate, rotate or revoke a secret. **Test Mode** does not require an OTP.

## Generate a Secret

To generate a new secret:

1. Log in to the Dashboard and select the mode (**Test** or **Live**).
2. Navigate to **Account & Settings** → **API Keys** (under **Website and app settings**).
3. In the **Secrets** section, click **Generate secret**. You can have up to 10 secrets in each mode.
4. Enter a **Name** for the secret. Name it after the server or vendor that will use it. The name must be unique within the selected mode.

   ![Generate secret dialog with the Name field](https://mintcdn.com/razorpay-881012b3/pXO9BYiUirLuZXk1/static/docs-home/assets/api-key-secrets-generate.jpg?fit=max\&auto=format\&n=pXO9BYiUirLuZXk1\&q=85\&s=e48d652e95d6b1f0bb86218420815323)
5. Click **Generate secret**.
6. In the **Save your new secret** dialog, copy the secret or click **Download .env** to save it as an environment file. The dialog also shows the public key to use with the secret.

   ![Save your new secret dialog showing the public key, the new secret and the Download .env option](https://mintcdn.com/razorpay-881012b3/pXO9BYiUirLuZXk1/static/docs-home/assets/api-key-secrets-save-secret.jpg?fit=max\&auto=format\&n=pXO9BYiUirLuZXk1\&q=85\&s=3c83e3d8a12a3e9f9cf50c669db8579d)
7. Select **I've saved this secret somewhere safe** and click **Done**.

> [!WARNING]
>
> **Watch Out!**
>
> * The secret is shown only once. Razorpay cannot show it again, not even through Support. If you lose a secret, generate a new one and revoke the lost one.
> * Store the secret in your server's environment variables. Never put it in your website or app code.

## Rotate a Secret

Rotate a secret to replace it with a new one. Your public keys stay the same.

To rotate a secret:

1. Log in to the Dashboard and select the mode (**Test** or **Live**).
2. Navigate to **Account & Settings** → **API Keys** (under **Website and app settings**).
3. In the **Secrets** section, click **Rotate secret** next to the secret. You can also click the **⋮** (more options) icon and select **Rotate secret**.

   ![Rotate secret button and the more options menu with Rotate secret and Revoke secret](https://mintcdn.com/razorpay-881012b3/pXO9BYiUirLuZXk1/static/docs-home/assets/api-key-secrets-more-options.jpg?fit=max\&auto=format\&n=pXO9BYiUirLuZXk1\&q=85\&s=11141a779bcafb73f86fd7e05ece24f5)
4. Under **When should the old secret stop working?**, select one of the following:

   * **In 24 hours**: Both secrets work until then, so you can switch your servers to the new secret without downtime. Use this for routine rotation.
   * **Immediately**: The old secret stops working right away. Use this if the secret has leaked.

   ![Rotate secret dialog with the In 24 hours and Immediately options](https://mintcdn.com/razorpay-881012b3/pXO9BYiUirLuZXk1/static/docs-home/assets/api-key-secrets-rotate.jpg?fit=max\&auto=format\&n=pXO9BYiUirLuZXk1\&q=85\&s=cf3dd8751e59b8ef9e42bd1a12078c98)
5. Click **Rotate secret**.
6. In the **Save your new secret** dialog, copy or download the new secret and save it securely.
7. Replace the old secret with the new one on every server, plugin or vendor system that uses it.

If you selected **In 24 hours**, the old secret stays in the **Secrets** table with **(old)** added to its name and the status **Expiring in N hours** until it stops working.

![Secrets table showing the old secret with the status Expiring in 24 hours](https://mintcdn.com/razorpay-881012b3/pXO9BYiUirLuZXk1/static/docs-home/assets/api-key-secrets-rotated-old-secret.jpg?fit=max\&auto=format\&n=pXO9BYiUirLuZXk1\&q=85\&s=d26cc487b704905845a9466ce971c67e)

> [!TIP]
>
> **Verify Payment Signatures During Rotation**
>
> During the 24 hours, verify payment signatures against both the old and the new secret.

## Revoke a Secret

Revoking a secret is permanent. To get a new secret without breaking your integration, [rotate the secret](#rotate-a-secret) instead.

To revoke a secret:

1. Log in to the Dashboard and select the mode (**Test** or **Live**).
2. Navigate to **Account & Settings** → **API Keys** (under **Website and app settings**).
3. In the **Secrets** section, click the **⋮** (more options) icon next to the secret and select **Revoke secret**.
4. Under **When should this secret stop working?**, select one of the following:
   * **In 24 hours**: Gives you time to move your servers to another secret.
   * **Immediately**: The secret stops working right away. Use this if the secret has leaked.
5. Select **I understand API calls still using this secret will fail**.

   ![Revoke secret dialog with the In 24 hours and Immediately options and the confirmation checkbox](https://mintcdn.com/razorpay-881012b3/pXO9BYiUirLuZXk1/static/docs-home/assets/api-key-secrets-revoke.jpg?fit=max\&auto=format\&n=pXO9BYiUirLuZXk1\&q=85\&s=eaeb046146171de4e88120000d22437c)
6. Click **Revoke secret**.

> [!WARNING]
>
> **Watch Out!**
>
> Once a revoked secret stops working, every API call that uses it fails. Before you revoke a secret, make sure none of your servers, plugins or vendors still use it.

Expired and revoked secrets are hidden from the **Secrets** table 7 days after they stop working.

## Frequently Asked Questions (FAQs)

> [accordion] How many secrets can I have?
>
> You can have up to 10 secrets in each mode (**Test** and **Live**) for your public key.

> [accordion] Will rotating my secret break my integration?
>
> No, if you select **In 24 hours** while rotating. The old and new secrets both work for 24 hours, so you can update your servers without downtime. If you select **Immediately**, every API call that still uses the old secret fails right away.

> [accordion] What should I do if I lose a secret?
>
> Razorpay cannot show a secret again after you close the **Save your new secret** dialog. [Generate a new secret](#generate-a-secret), update your servers and then [revoke the lost secret](#revoke-a-secret).

> [accordion] Who can manage secrets?
>
> Only users with the **Owner** or **Admin** role have access to API keys. Know more about [standard user roles & permissions](https://razorpay.com/docs/payments/dashboard/account-settings/manage-team.md#standard-user-roles).

### Related Information

* [API Keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md)
* [API Best Practices](https://razorpay.com/docs/api/best-practices.md)
