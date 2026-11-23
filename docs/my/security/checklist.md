> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Business Security Checklist

> List of security measures and best practices to ensure secure transactions using Razorpay Curlec.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Information security is critical for businesses handling financial transactions online. Being a technology-first online finance company, we ensure that every transaction made using Razorpay Curlec products is secure.

The security of your business's online transactions and data is a shared responsibility between you and Razorpay Curlec. As a Razorpay Curlec user, ensure you use the security measures below to secure your online transactions.

## General

Following are the general security best practices:

* Implement [Two-Factor Authentication (2FA)](https://razorpay.com/docs/my/payments/dashboard/account-settings/manage-team.md#enable-2-step-verification-2fa-at-team-level) across your team for additional security.
* Use TLS and HTTPS, as they significantly decrease the risk of a man-in-the-middle attack on you or your customers.
* Use a password manager and set strong passwords.
* Maintain a checklist for timely onboarding and off-boarding of users.
* Do not share user accounts among employees.
* Back up your data regularly, and test the restoration periodically.

## APIs

It is essential to store your API keys safely. For the utmost security, follow the best practices listed below when integrating with Razorpay Curlec APIs.

### Applications

While integrating Razorpay Curlec APIs with your application, ensure that:

* The API key secret is not included in version control (GitHub, Gitlab).
* You only provide access to the API secret to employees on a need-to-know basis.
* You store all secrets, such as the API secret, customer ID, and card tokens in a secure vault.
* All websites and APIs are accessed only using HTTPS, and they follow basic security best practices.

### Payments API

While integrating with our [Payments API](https://razorpay.com/docs/my/api/payments), ensure that you:

* Use the [Capture a Payment API](https://razorpay.com/docs/my/api/payments/capture.md) to assert the payment status.
* Fetch the amounts of captured payments only from the backend or a trusted source.

### Orders API

While integrating with our [Orders API](https://razorpay.com/docs/my/api/orders/create.md), ensure that:

* [Payments are auto-captured](https://razorpay.com/docs/my/payments/payments/capture-settings.md#auto-capture-all-payments) from the Dashboard.
* Signatures are validated in the callback request when using the Orders API to confirm payment status.
* Order ids are retrieved only from a trusted source, such as your database for the HMAC generation.

## Webhooks

To use our webhooks securely, ensure that all webhook requests are validated using Hash-based Message Authentication Code (HMAC).

## Accounts and Dashboard

Following are the best practices for Dashboard usage:

* Grant access to the Dashboard only for necessary users.
* Define [user roles](https://razorpay.com/docs/my/payments/dashboard/account-settings/manage-team.md#standard-user-roles) for team members based on their usage of the Dashboard.
* Implement [Two-Factor Authentication (2FA)](https://razorpay.com/docs/my/payments/dashboard/account-settings/manage-team.md#enable-2-step-verification-2fa-at-team-level) on all your Razorpay Curlec accounts.
* Never share Razorpay Curlec Two-Factor Authentication OTPs among employees.

## Plugin Integration

Implement the below best practices while integrating with Razorpay Curlec using [third-party plugins](https://razorpay.com/docs/my/payments/payment-gateway/ecommerce-plugins).

* Use the latest version of all plugins.
* Vendors like WordPress, Drupal, and Magento send notifications on security issues and product updates. Ensure that you subscribe to these notifications.
* Wherever applicable, follow the official [Hardening WordPress Guide](https://wordpress.org/support/article/hardening-wordpress/Hardening).

### Related Information

* [Razorpay Curlec Security](https://razorpay.com/docs/my/security)
* [Shared Responsibility Model](https://razorpay.com/docs/my/security/shared-responsibility-model.md)
