> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Security & Sign-in

> Verify your Razorpay Dashboard sign-ins with a 6-digit code from an authenticator app instead of waiting for an SMS OTP.

Available in
🇮🇳 India
🇸🇬 Singapore
🇺🇸 United States

You can sign in to the Razorpay Dashboard with a 6-digit code from an authenticator app on your phone instead of waiting for an SMS OTP. Setup takes about a minute. After that, the Dashboard asks for the code from your app at sign-in and no SMS is sent. SMS OTP stays on as your backup.

> [!WARNING]
>
> Authenticator app sign-in works on the web Dashboard only. The Razorpay mobile app does not support it yet, so after you set it up, the mobile app cannot complete your sign-in. If you sign in using the mobile app, wait before you set this up.

## Before You Start

* Use the web Dashboard at [dashboard.razorpay.com](https://dashboard.razorpay.com) in a browser, on your computer or your phone.
* Install an authenticator app on your phone. Google Authenticator, Microsoft Authenticator, Authy, 1Password, Duo and any other app that generates time-based 6-digit codes work.
* Keep a verified phone number on your profile. It is your backup if your phone is not with you, and some sensitive actions still start with an SMS OTP.
* Each team member sets up the authenticator app for their own login. Setting it up for yourself does not change anything for other users on your account.

## Set Up an Authenticator App

1. Log in to the Dashboard and click **Account & Settings**. Under **Your profile**, click **Manage** next to **Security & sign-in**.

   ![Your profile section with the Manage link next to Security and sign-in highlighted](https://mintcdn.com/razorpay-881012b3/BlHJjVbCB8-c6vlX/static/docs-home/assets/security-sign-in-manage-link.jpg?fit=max\&auto=format\&n=BlHJjVbCB8-c6vlX\&q=85\&s=46f916ea19de22da92c47af10ee0a46e)

2. You see two cards: **SMS OTP** and **Authenticator app**. On the **Authenticator app** card, click **Set up authenticator app**.

   ![Security and sign-in page with the Set up authenticator app button highlighted on the Authenticator app card](https://mintcdn.com/razorpay-881012b3/BlHJjVbCB8-c6vlX/static/docs-home/assets/security-sign-in-set-up-button.jpg?fit=max\&auto=format\&n=BlHJjVbCB8-c6vlX\&q=85\&s=36634d21155733557d5bed58b3b31655)

3. Open your authenticator app, choose to add an account and scan the QR code. If scanning does not work, click **Copy** next to the setup key and enter the key in your app instead. Do not share the QR code or setup key with anyone.

   ![Set up authenticator app dialog showing a blurred QR code and setup key](https://mintcdn.com/razorpay-881012b3/BlHJjVbCB8-c6vlX/static/docs-home/assets/security-sign-in-qr-code.jpg?fit=max\&auto=format\&n=BlHJjVbCB8-c6vlX\&q=85\&s=9feb9b1f5b066bb37f7edb0a2ca6a251)

4. Your app shows a 6-digit code for Razorpay that changes every 30 seconds. Enter the current code and click **Verify and finish**. If the code changes while you type, enter the new one. The setup window lasts 10 minutes. If it expires, close the dialog and start again.

   ![Set up authenticator app dialog with a 6-digit code entered and the Verify and finish button highlighted](https://mintcdn.com/razorpay-881012b3/BlHJjVbCB8-c6vlX/static/docs-home/assets/security-sign-in-verify-and-finish.jpg?fit=max\&auto=format\&n=BlHJjVbCB8-c6vlX\&q=85\&s=5b9c24550ecd69a3121767141348d7ae)

5. The **Authenticator app** card now shows the date you set it up. The authenticator app is now your first sign-in step and **SMS OTP** stays on as your backup.

   ![Security and sign-in page showing the authenticator app as the first verification step and SMS OTP as the backup](https://mintcdn.com/razorpay-881012b3/BlHJjVbCB8-c6vlX/static/docs-home/assets/security-sign-in-authenticator-on.jpg?fit=max\&auto=format\&n=BlHJjVbCB8-c6vlX\&q=85\&s=507bd8b6f266e98611241b5428626c16)

## Sign In With Your Authenticator App

1. Sign in with your email and password, or with Google, as usual. The **Two Step Verification** screen asks for the code from your authenticator app.
2. Open your app, enter the current 6-digit code and click **Verify**.

   ![Two Step Verification screen asking for the authenticator app code with the Verify button highlighted](https://mintcdn.com/razorpay-881012b3/BlHJjVbCB8-c6vlX/static/docs-home/assets/security-sign-in-sign-in-code.jpg?fit=max\&auto=format\&n=BlHJjVbCB8-c6vlX\&q=85\&s=69ab32699fad8c6f2eb469c8516009c5)

On your own computer, keep **Skip OTP on this browser for 30 days** selected and the Dashboard does not ask for a code on that browser for 30 days. Clear the checkbox on shared or public computers.

> [!NOTE]
>
> If a code does not work, wait for the next code in your app instead of entering the same digits again. After 9 incorrect codes, your account is locked for security reasons.

### Use SMS OTP Instead

If your phone is not with you, you can sign in with an SMS OTP. This option appears only if your profile has a verified phone number with SMS OTP on.

1. On the **Two Step Verification** screen, click **Use SMS OTP**.

   ![Two Step Verification screen with the Use SMS OTP link highlighted](https://mintcdn.com/razorpay-881012b3/BlHJjVbCB8-c6vlX/static/docs-home/assets/security-sign-in-use-sms-otp.jpg?fit=max\&auto=format\&n=BlHJjVbCB8-c6vlX\&q=85\&s=bc2e66c06a92bc2ab939454ee2832ffe)

2. Enter the OTP sent to your verified phone number to complete the sign-in. To go back to the code from your app, click **Use authenticator code**.

   ![SMS OTP screen with the Use authenticator code link highlighted](https://mintcdn.com/razorpay-881012b3/BlHJjVbCB8-c6vlX/static/docs-home/assets/security-sign-in-use-authenticator-code.jpg?fit=max\&auto=format\&n=BlHJjVbCB8-c6vlX\&q=85\&s=aec332809904f73be39674c065d5372b)

## Verify Sensitive Actions

Sensitive actions on the Dashboard, such as generating or regenerating [API keys](https://razorpay.com/docs/us/payments/dashboard/account-settings/api-keys.md) and inviting [team members](https://razorpay.com/docs/us/payments/dashboard/account-settings/manage-team.md), ask you to verify again in a **2-Step Verification** window. The window sends an SMS OTP first. To use your authenticator app instead, click **Use authenticator code** in the window. If the SMS cannot be delivered, the window switches to your authenticator app automatically.

After you verify, either at sign-in or in the Dashboard, you are not asked again for 30 minutes.

> [!NOTE]
>
> These sensitive actions still need a verified phone number on your profile. [Add and verify a phone number](https://razorpay.com/docs/us/payments/dashboard/account-settings/account-details.md#update-phone-number) before you need it.

## Turn Off the Authenticator App

1. Go to **Account & Settings** → **Security & sign-in** and click **Turn off authenticator app** on the **Authenticator app** card. This option works only when SMS OTP is on and your phone number is verified, so you always have one way to sign in.

   ![Authenticator app card with the Turn off authenticator app button highlighted](https://mintcdn.com/razorpay-881012b3/BlHJjVbCB8-c6vlX/static/docs-home/assets/security-sign-in-turn-off.jpg?fit=max\&auto=format\&n=BlHJjVbCB8-c6vlX\&q=85\&s=0579d2ad3ec1a341da540d69c0276613)

2. Enter the OTP sent to your phone and click **Continue**. Turning off always asks for an SMS OTP, even if you verified a few minutes ago.

   ![2-Step Verification window with the SMS OTP entered and the Continue button highlighted](https://mintcdn.com/razorpay-881012b3/BlHJjVbCB8-c6vlX/static/docs-home/assets/security-sign-in-turn-off-sms-confirm.jpg?fit=max\&auto=format\&n=BlHJjVbCB8-c6vlX\&q=85\&s=d904af6a92d252661de3cf046402809a)

Your next sign-in uses SMS OTP. You can set up the authenticator app again at any time.

## New Phone or Lost Phone

| Situation | What to do |
| - | - |
| Moving to a new phone | Before you reset the old phone, move your accounts within the authenticator app. Google Authenticator and Authy both support this. Alternatively, [turn off the authenticator app](#turn-off-the-authenticator-app) and [set it up again](#set-up-an-authenticator-app) on the new phone. |
| Lost your phone, but you still receive SMS on your verified number | Sign in using [Use SMS OTP](#use-sms-otp-instead), turn off the authenticator app and set it up again on your new phone. |
| No access to your authenticator app or your verified phone number | Raise a request with our [Support team](https://razorpay.com/us/support/). This applies to team members too, as the account owner cannot reset the authenticator app for you. |

## FAQs

> [accordion] Why don't I see the Authenticator app card?
>
> Your organisation may manage 2-step verification centrally, in which case the **Security & sign-in** page is not available. Reload the Dashboard and check again. If you still do not see the card, raise a request with our [Support team](https://razorpay.com/us/support/) and share the email address you sign in with.

> [accordion] Which authenticator apps can I use?
>
> Any app that generates time-based 6-digit codes, such as Google Authenticator, Microsoft Authenticator, Authy, 1Password and Duo.

> [accordion] Does the authenticator app replace SMS OTP?
>
> At sign-in, yes. The Dashboard asks for the code from your authenticator app first. SMS OTP stays on as your backup if you have a verified phone number.

> [accordion] Can I turn on the authenticator app for my whole team?
>
> No. Each team member sets up the authenticator app for their own login. There is no account-wide setting.

> [accordion] Is it safe to skip OTP on this browser for 30 days?
>
> **Skip OTP on this browser for 30 days** trusts one browser on one device. Use it only on your own computer.

> [accordion] Can I use the authenticator app on the Razorpay mobile app?
>
> Not yet. Authenticator app sign-in works on the web Dashboard only.
