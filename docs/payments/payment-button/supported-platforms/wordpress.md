> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Embed Payment Button on WordPress Website

> Embed a Razorpay Payment Button on your WordPress website and accept payments from customers.

Available in
🇮🇳 India

> [card] [Payment Button - Wordpress Changelog](https://razorpay.com/docs/payments/changelog.md#products)
>
> Version 2.4.6 released for Payment Button Wordpress. This version fixes naming conflict in Razorpay section.

WordPress is one of the most popular Content Management Systems out there. You can quickly build a website using WordPress and embed the our Payment Button to accept payments from customers.

![WordPress Homepage](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-wordpress-homepage.jpg)

## WordPress Plan

> [tab] For Websites Hosted on Domain
>
> If you have built your website using `www.wordpress.com`, and are on a paid plan, you can directly install the Razorpay Payment Button Plugin from the WordPress Plugins store.
>
> 1. [Install the Razorpay Payment Button Plugin on your WordPress site](https://wordpress.org/plugins/razorpay-payment-button/).
> 2. [Create a Payment Button on Dashboard](#2-create-a-payment-button-on-razorpay-dashboard).
> 3. [Embed the Payment Button on your WordPress site](#3-embed-the-payment-button-on-wordpress-site).

> [tab] For Websites Hosted on Localhost
>
> If you are using WordPress with the free plan, you need to use MAMP to set up a local WordPress site and continue with the Payment Button
> implementation.
>
> 1. [Set up WordPress site locally on your system](#1-set-up-wordpress-site-locally-on-your-system).
> 2. [Create a Payment Button on Dashboard](#2-create-a-payment-button-on-razorpay-dashboard).
> 3. [Embed the Payment Button on your WordPress site](#3-embed-the-payment-button-on-wordpress-site).

## Prerequisites

1. Download the [Razorpay Payment Button WordPress Plugin](https://wordpress.org/plugins/razorpay-payment-button/).
2. Create a Razorpay account.
3. Navigate to **Settings** → **API Keys** and [generate API keys](https://razorpay.com/docs/api/authentication.md#generate-api-keys) in the test mode.

[YouTube video player](https://www.youtube.com/embed/6mJnOWZDhDo)

Add the API key details in the Razorpay Payment Button plugin settings.

> [!NOTE]
>
> **Handy Tips**
>
> * When testing: Generate the keys in Test mode. \\
>
> * To accept live payments: Generate the keys in Live mode and replace them in the Payment Button plugin settings.

## Set Up a Payment Button Using Wordpress Plugin

Watch this video to see how to set up a Payment Button using Wordpress Plugin.

[YouTube video player](https://www.youtube.com/embed/xyk5FXSDdK4)

### 1. Set Up WordPress Site Locally on Your System

> [tab] For Windows Users
>
> See: [Installation Steps for Windows](https://documentation.mamp.info/en/MAMP-Windows/Installation/)

> [tab] For Mac Users
>
> To install WordPress on your Mac system:
>
> 1. [Download the latest version of MAMP](https://www.mamp.info/en/downloads/) and install it on your Mac system. This software enables you to manage your websites locally.
> 2. Install the downloaded file using the wizard and save MAMP in your **Applications** folder.
>
>    ![Install MAMP](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-install-mamp.jpg)
> 3. Navigate to the **MAMP** folder.
>
>    ![Navigate to MAMP](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-mamp-folder.jpg)
>
>    In the folder, click the **MAMP** icon:
>
>    ![Click MAMP](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-mamp-icon.jpg)
> 4. Click **Start Server** to run the server on your system.
>
>    ![Start Server](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-start-server.jpg)
>
>    The server status appears green once they are ready.
>
>    ![Server in Ready State](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-server-running.jpg)
> 5. Click **Open WebStart Page**. The server starts running on your browser as shown:
>
>    ![Open WebStart Page](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-phpmyadmin.jpg)
> 6. We must set up a MySQL database for the WordPress website. This is done using **phpMyAdmin**.
>
>    ![Setup phpMyAdmin](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-setup-database.jpg)
>
>    a. Select the required database and click **Privileges**.\\
>
>    ![Add user account: phpMyAdmin](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-priviledges.jpg)
>
>    b. Click **Add user account**.
>
>    ![Add user account: phpMyAdmin](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-add-user-account.jpg)
>
>    c. Enter the username and password, same as the WordPress account login credentials.\\
>
>    ![Add user account: phpMyAdmin](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-username-password-priviledges.jpg)
>
>    d. Click **Go**.
>
>    ![user account added: phpMyAdmin](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-user-account-added.jpg)
> 7. Navigate to the WordPress application you had downloaded.
> 8. Rename the `WordPress` folder. Provide a name relevant to the site you will be building/testing locally. For example, `teafactory`. Add the `teafactory` folder in `htdocs` of your MAMP directory.
>
>    ![Rename WordPress folder](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-htdocs.jpg)
> 9. Open the browser and type in the URL pointing to your site folder. For example, `localhost:8888/teafactory`. Select the language of your choice and click **Continue** → **Let's Go**.
>
>    ![Select Language](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-select-language.jpg)
> 10. Enter your database details. Provide a name for the database, and enter `root` for both the database username and password. Click **Submit**.
>
>     ![Log in](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-wp-login.jpg)
> 11. Provide the required general site information (which you can change later), as well as your login information in WordPress.
>
>     ![Setup Login Information](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-setup-login.jpg)
> 12. Click the **Install WordPress** button. With this, your website is ready.
>
>     ![Install WordPress](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-login.jpg)

## 2. Create a Payment Button on Razorpay Dashboard

To accept payments on your WordPress site, you must create a Payment Button.

* [Quick Pay Button](https://razorpay.com/docs/payments/payment-button/quick-pay.md)
* [Buy Now Button](https://razorpay.com/docs/payments/payment-button/buy-now.md)
* [Donations Button](https://razorpay.com/docs/payments/payment-button/donations.md)
* [Custom Button](https://razorpay.com/docs/payments/payment-button/custom.md)

## 3. Embed the Payment Button on WordPress Site

To embed the Payment Button:

3.1 Download and install the Razorpay Payment Button Plugin. You can do this using either of these methods:

* [Download the plugin from the WordPress Plugin Directory](https://wordpress.org/plugins/razorpay-payment-button/) and add the zip file to your WordPress website's **Plugins** folder.
* Add the plugin directly onto your WordPress website from the **Plugin** page.

3.2 In your WordPress site, activate the plugin in the **WordPress Plugin Manager**.

![Activate Plugin](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-activate-plugin.jpg)

3.3 Navigate to **Razorpay Buttons** → **Settings** to add your Razorpay API key details and connect your Razorpay account to the plugin.

![Add Razorpay API Key](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-settings.jpg)

3.4 Navigate to **Razorpay Buttons**. A list of buttons you created on Razorpay are available here. Select the required button.

![List of Payment Buttons](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-view-buttons.jpg)

3.5 Click **Pages** and navigate to the page where you want to embed the Payment button.

![Select Page](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-shop-page.jpg)

3.6 Select **Add Block** → **Widgets** → **Razorpay: Payment Button** to embed the Payment button onto the page.

![Embed Button](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-add-pb-widget.jpg)

3.7 Choose the Payment Button using the drop-down and publish or update the page.

![Choose Payment Button](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-select-button.jpg)

The Payment Button appears on the page.

![Payment Button Appears](https://razorpay.com/docs/build/browser/assets/images/payment-button-wordpress-pb.gif)

You can now start accepting payments on your WordPress website using the Payment Button.

## FAQs

> [accordion] I have created a Payment Button on the Dashboard. When I try to embed this code on my `www.wordpress.com` website, I am facing errors. How do I resolve this?
>
> You cannot directly use the Payment Button code generated from the Dashboard if you are using `www.wordpress.com`. You must upgrade to the WordPress paid plan and use the Razorpay Payment Button plugin.

> [accordion] I am using Thrive Editor to add the button code for Razorpay. What should I be aware of, and how should I add payment buttons?
>
> If you are using Thrive Editor to add the button code for Razorpay, it is essential to note that Thrive Editor does not support the direct inclusion of scripts in HTML pages or posts. It automatically places a code tag on top of the script and adds a `<code class="tve_js_placeholder">` above the payment button script. Unfortunately, there is no workaround for this behaviour. We recommend using the WordPress default editor, Gutenberg, or any other compatible editor to add payment buttons effectively. These editors allow you to add payment button scripts without the interference caused by Thrive Editor's script handling. This will ensure a smooth integration of Razorpay payment buttons into your website.

> [accordion] I am getting following error message `Razorpay error: Payment button fetch failed with the following message: The API key provided by you has expired and cannot be used. Please use the correct key and secret.` How do I resolve this?
>
> This error indicates that your API Key and Secret for Razorpay have expired. Follow the steps given below to resolve the issue:
>
> 1. Log in to Dashboard.
> 2. Generate new [API Keys](https://razorpay.com/docs/api/authentication.md#generate-api-keys).
> 3. Replace the old API Key and Secret in your integration code with the newly generated API keys.

### Related Information

* [Payment Button](https://razorpay.com/docs/payments/payment-button)
* [Create a WordPress Website](https://razorpay.com/docs/payments/payment-button/supported-platforms/wordpress/create-website.md)
* [Payment Button Elementor Plugin for WordPress](https://razorpay.com/docs/payments/payment-button/supported-platforms/wordpress/elementor.md)
* [Payment Button SiteOrigin Plugin for WordPress](https://razorpay.com/docs/payments/payment-button/supported-platforms/wordpress/site-origin.md)
* [Payment Button Visual Composer Plugin for WordPress](https://razorpay.com/docs/payments/payment-button/supported-platforms/wordpress/visual-composer.md)
