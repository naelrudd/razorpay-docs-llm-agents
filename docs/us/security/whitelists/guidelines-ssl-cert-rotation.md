> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Guidelines for SSL Certificate Rotation

> How Razorpay's SSL certificates are managed, what your integration must support, and what to do if your systems pin or whitelist certificates.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Your integration connects to Razorpay over HTTPS. Razorpay's SSL certificate proves that you are connected to Razorpay's services and keeps the traffic private. This page explains what your integration must support, why you should not pin our certificate, and what to do if your security policy requires pinning.

> [!NOTE]
>
> **Upcoming SSL certificate renewal: October 05, 2026, 10:00 PM IST**
>
> If your integration pins or whitelists Razorpay's certificate, review the guidance on this page and complete the required changes before this date.

## Prerequisites

Before proceeding, determine if your application uses:

* SSL certificate pinning
* Certificate whitelisting
* Custom certificate trust stores

No action is required if your systems have never been configured to use, trust, or manually install a specific Razorpay SSL certificate, including through SSL pinning or certificate whitelisting. This includes any configurations previously made by your team. Your systems will automatically trust the renewed certificate.

> [!NOTE]
>
> **No Action Needed for Third-Party Platform Users**
>
> If you use a third-party platform such as WooCommerce, Magento, CS Cart, OpenCart, Shopify, WHMCS, Arastta, Prestashop, WordPress, Easy Digital Downloads, WIX, BigCommerce or Drupal Commerce, you are not required to take any action. The platform handles SSL management. Read [FAQ #3](#faqs) and [FAQ #4](#faqs) for more details.
>
> The same applies if you use Razorpay-hosted products such as Payment Links, Payment Pages, Payment Buttons or Invoices.

## Requirements

Your systems must support TLS 1.2 or higher. TLS 1.3 is preferred.

## TLS certificates

When you connect, our server presents a chain of certificates. Your client checks that the chain ends at a root it already trusts.

* **Leaf certificate:** Razorpay's own certificate for `*.razorpay.com`. It is renewed every few months.
* **Intermediate certificate:** issued by the certificate authority; it signs the leaf and can change without notice.
* **Root certificate:** the long-lived trust anchor built into operating systems and browsers. Roots stay valid for many years.

For a fuller explanation, see [DigiCert: how certificate chains work](https://knowledge.digicert.com/solution/how-certificate-chains-work) and [Let's Encrypt: chain of trust](https://letsencrypt.org/certificates/).

## Certificate pinning

Razorpay does not recommend [certificate pinning](https://www.ssl.com/blogs/what-is-certificate-pinning).

If you use certificate pinning, your system only accepts the certificate that you pinned for Razorpay. When we renew our SSL certificate and present a different one during the TLS handshake, your application refuses to connect to Razorpay, even though the new certificate is issued by a trusted certificate authority (CA).

Why Razorpay does not support certificate pinning of any kind:

* **Outside of Razorpay's control:** your system handles certificate pinning. We do not know whether you pin, or which certificates you pin.
* **Risk of failing connections:** when we renew our certificate and your system still expects the previous one, your connection to Razorpay breaks. Our certificate is now renewed every few months.

> [!WARNING]
>
> **Watch Out!**
>
> If you have pinned or whitelisted a Razorpay certificate, remove it and rely on standard SSL validation. Pinning adds no practical protection for your integration and can stop your payments at every renewal.

## Certificate changes

If your security policy requires certificate pinning, do the following to reduce the risk of broken connections.

**Only pin the root certificates:** instead of pinning the leaf certificate or the entire certificate chain, you must pin all of the following root certificates. Razorpay no longer publishes per-certificate files (X\*.pem):

| Root certificate | Key type | Valid until | Download |
| - | - | - | - |
| DigiCert Global Root G2 | RSA | Jan 2038 | [.pem](https://cacerts.digicert.com/DigiCertGlobalRootG2.crt.pem) |
| DigiCert Global Root CA | RSA | Nov 2031 | [.pem](https://cacerts.digicert.com/DigiCertGlobalRootCA.crt.pem) |
| DigiCert Global Root G3 | ECDSA | Jan 2038 | [.pem](https://cacerts.digicert.com/DigiCertGlobalRootG3.crt.pem) |
| DigiCert TLS RSA4096 Root G5 | RSA | Jan 2046 | [.pem](https://cacerts.digicert.com/DigiCertTLSRSA4096RootG5.crt.pem) |
| DigiCert TLS ECC P384 Root G5 | ECDSA | Jan 2046 | [.pem](https://cacerts.digicert.com/DigiCertTLSECCP384RootG5.crt.pem) |
| Amazon Root CA 1 | RSA | Jan 2038 | [.pem](https://www.amazontrust.com/repository/AmazonRootCA1.pem) |
| Amazon Root CA 2 | RSA | May 2040 | [.pem](https://www.amazontrust.com/repository/AmazonRootCA2.pem) |
| Amazon Root CA 3 | ECDSA | May 2040 | [.pem](https://www.amazontrust.com/repository/AmazonRootCA3.pem) |
| Amazon Root CA 4 | ECDSA | May 2040 | [.pem](https://www.amazontrust.com/repository/AmazonRootCA4.pem) |
| Starfield Services Root CA - G2 | RSA | Dec 2037 | [.pem](https://www.amazontrust.com/repository/SFSRootCAG2.pem) |

> [accordion] Fingerprints and serial numbers (for verification)
>
> | Root certificate | Details |
> | - | - |
> | DigiCert Global Root G2 | Valid until: 15/Jan/2038 Serial #: 03:3A:F1:E6:A7:11:A9:A0:BB:28:64:B1:1D:09:FA:E5 SHA-1: DF:3C:24:F9:BF:D6:66:76:1B:26:80:73:FE:06:D1:CC:8D:4F:82:A4 SHA-256: CB:3C:CB:B7:60:31:E5:E0:13:8F:8D:D3:9A:23:F9:DE:47:FF:C3:5E:43:C1:14:4C:EA:27:D4:6A:5A:B1:CB:5F |
> | DigiCert Global Root CA | Valid until: 10/Nov/2031 Serial #: 08:3B:E0:56:90:42:46:B1:A1:75:6A:C9:59:91:C7:4A SHA-1: A8:98:5D:3A:65:E5:E5:C4:B2:D7:D6:6D:40:C6:DD:2F:B1:9C:54:36 SHA-256: 43:48:A0:E9:44:4C:78:CB:26:5E:05:8D:5E:89:44:B4:D8:4F:96:62:BD:26:DB:25:7F:89:34:A4:43:C7:01:61 |
> | DigiCert Global Root G3 | Valid until: 15/Jan/2038 Serial #: 05:55:56:BC:F2:5E:A4:35:35:C3:A4:0F:D5:AB:45:72 SHA-1: 7E:04:DE:89:6A:3E:66:6D:00:E6:87:D3:3F:FA:D9:3B:E8:3D:34:9E SHA-256: 31:AD:66:48:F8:10:41:38:C7:38:F3:9E:A4:32:01:33:39:3E:3A:18:CC:02:29:6E:F9:7C:2A:C9:EF:67:31:D0 |
> | DigiCert TLS RSA4096 Root G5 | Valid until: 14/Jan/2046 Serial #: 08:F9:B4:78:A8:FA:7E:DA:6A:33:37:89:DE:7C:CF:8A SHA-1: A7:88:49:DC:5D:7C:75:8C:8C:DE:39:98:56:B3:AA:D0:B2:A5:71:35 SHA-256: 37:1A:00:DC:05:33:B3:72:1A:7E:EB:40:E8:41:9E:70:79:9D:2B:0A:0F:2C:1D:80:69:31:65:F7:CE:C4:AD:75 |
> | DigiCert TLS ECC P384 Root G5 | Valid until: 14/Jan/2046 Serial #: 09:E0:93:65:AC:F7:D9:C8:B9:3E:1C:0B:04:2A:2E:F3 SHA-1: 17:F3:DE:5E:9F:0F:19:E9:8E:F6:1F:32:26:6E:20:C4:07:AE:30:EE SHA-256: 01:8E:13:F0:77:25:32:CF:80:9B:D1:B1:72:81:86:72:83:FC:48:C6:E1:3B:E9:C6:98:12:85:4A:49:0C:1B:05 |
> | Amazon Root CA 1 | Valid until: 17/Jan/2038 Serial #: 06:6C:9F:CF:99:BF:8C:0A:39:E2:F0:78:8A:43:E6:96:36:5B:CA SHA-1: 8D:A7:F9:65:EC:5E:FC:37:91:0F:1C:6E:59:FD:C1:CC:6A:6E:DE:16 SHA-256: 8E:CD:E6:88:4F:3D:87:B1:12:5B:A3:1A:C3:FC:B1:3D:70:16:DE:7F:57:CC:90:4F:E1:CB:97:C6:AE:98:19:6E |
> | Amazon Root CA 2 | Valid until: 26/May/2040 Serial #: 06:6C:9F:D2:96:35:86:9F:0A:0F:E5:86:78:F8:5B:26:BB:8A:37 SHA-1: 5A:8C:EF:45:D7:A6:98:59:76:7A:8C:8B:44:96:B5:78:CF:47:4B:1A SHA-256: 1B:A5:B2:AA:8C:65:40:1A:82:96:01:18:F8:0B:EC:4F:62:30:4D:83:CE:C4:71:3A:19:C3:9C:01:1E:A4:6D:B4 |
> | Amazon Root CA 3 | Valid until: 26/May/2040 Serial #: 06:6C:9F:D5:74:97:36:66:3F:3B:0B:9A:D9:E8:9E:76:03:F2:4A SHA-1: 0D:44:DD:8C:3C:8C:1A:1A:58:75:64:81:E9:0F:2E:2A:FF:B3:D2:6E SHA-256: 18:CE:6C:FE:7B:F1:4E:60:B2:E3:47:B8:DF:E8:68:CB:31:D0:2E:BB:3A:DA:27:15:69:F5:03:43:B4:6D:B3:A4 |
> | Amazon Root CA 4 | Valid until: 26/May/2040 Serial #: 06:6C:9F:D7:C1:BB:10:4C:29:43:E5:71:7B:7B:2C:C8:1A:C1:0E SHA-1: F6:10:84:07:D6:F8:BB:67:98:0C:C2:E2:44:C2:EB:AE:1C:EF:63:BE SHA-256: E3:5D:28:41:9E:D0:20:25:CF:A6:90:38:CD:62:39:62:45:8D:A5:C6:95:FB:DE:A3:C2:2B:0B:FB:25:89:70:92 |
> | Starfield Services Root CA - G2 | Valid until: 31/Dec/2037 Serial #: 00 SHA-1: 92:5A:8F:8D:2C:6D:04:E0:66:5F:59:6A:FF:22:D8:63:E8:25:6F:3F SHA-256: 56:8D:69:05:A2:C8:87:08:A4:B3:02:51:90:ED:CF:ED:B1:97:4A:60:6A:13:C6:E5:29:0F:CB:2A:E6:3E:DA:B5 |

> [!NOTE]
>
> Download the root certificates only from the CAs' official repositories: [DigiCert](https://knowledge.digicert.com/general-information/digicert-trusted-root-authority-certificates) · [Amazon Trust Services](https://www.amazontrust.com/repository/). Verify each download against the fingerprints above:
>
> ```bash theme={null}
> openssl x509 -in <root.pem> -noout -subject -fingerprint -sha256
> ```

**Keep track of root certificate updates:** even if you pin all the root certificates, Razorpay may add a new root certificate to this list in future.

* **Regular business practice:** we publish the new root on this page at least 30 days before our servers start using it.
* **Emergency cases:** the notice period can be shorter before we make the change.

It is your responsibility to ensure your applications (for example, web or mobile) can handle any certificate changes.

> [!WARNING]
>
> **Never pin the leaf certificate, the intermediate certificate, or the certificate chain**
>
> Razorpay updates these certificates routinely and without notice. Any integration that pins them will break at the next rotation.

### Certificate trust store updates

If you have a certificate trust store in your server environment that is not configured to update automatically, you must ensure that it contains all the root certificates listed above. Refer to this [manual](https://manuals.gfi.com/en/kerio/connect/content/server-configuration/ssl-certificates/adding-trusted-root-certificates-to-the-server-1605.html) to learn how to update trust stores in different environments.

## Verify your setup

Before each announced change, the upcoming certificate is served on a test endpoint ahead of production. Connect to it to confirm your setup:

```bash theme={null}
curl -v https://api-ssl-test.razorpay.com

# or inspect the certificate directly:
openssl s_client -connect api-ssl-test.razorpay.com:443 \
  -servername api-ssl-test.razorpay.com </dev/null
```

If the connection succeeds without an SSL or certificate error, your system is ready for the renewal.

> [!WARNING]
>
> **Watch Out!**
>
> This is only a test domain (`api-ssl-test.razorpay.com`) and should not be used in production environments.

## Additional Support

If you encounter any difficulties during the process, our support team is here to help:

1. Log in to the Dashboard.
2. Navigate to the **Help & Support** section at the bottom right.
3. Raise a ticket under the **Technical Assistance** category to contact our tech support team.

## FAQs

> [accordion] I have received an email about a certificate change, or I am a new Razorpay user. Do I need to take action?
>
> Not unless you have manually pinned or installed a Razorpay certificate in your applications or servers. Otherwise your systems validate our certificate through the standard trust store of your operating system or platform, and the change is invisible to you. If you have pinned one, remove it or pin all the root certificates listed on this page.

> [accordion] I previously downloaded the X9 or X10 certificate files. What should I do now?
>
> Remove the pinned or installed Razorpay certificate and let your system use standard SSL validation. If your security policy requires pinning, replace the old files with all the root certificates listed on this page. Per-certificate files (X\*.pem and chain files) are no longer published.

> [accordion] How do I check whether I am using a third-party platform?
>
> Third-party platforms are services such as WooCommerce, Magento, CS Cart, OpenCart, Shopify, WHMCS, Arastta, Prestashop, WordPress, Easy Digital Downloads, WIX, BigCommerce and Drupal Commerce. If you are unsure, check whether you use an admin panel provided by one of these platforms to add stock, offers or perform other tasks. If yes, you are using a third-party platform.

> [accordion] If I am using a third-party platform, do I need to take action?
>
> No. The platform manages the connection to Razorpay and handles SSL validation for you. See the list of platforms in the box near the top of this page.

> [accordion] What are leaf, intermediate and root certificates?
>
> When you connect to Razorpay, our server sends three certificates in a chain. The leaf is our own certificate, and it changes every few months. The intermediate belongs to the certificate authority, and it can change at any time. The root is built into your operating system or browser and stays the same for many years. That is why only root certificates are safe to pin. See [TLS certificates](#tls-certificates) for more.

> [accordion] Why can I no longer pin Razorpay's certificate?
>
> Industry rules now limit how long any SSL certificate may be valid, so Razorpay's certificate will be renewed every few months instead of once a year. A pin on the certificate or its intermediate breaks at every renewal. Root certificates stay valid for many years, which is why only root pinning is supported.

> [accordion] What do I gain by removing certificate pinning instead of pinning the root certificates?
>
> **Nothing to maintain, ever.** With pinning removed, your system trusts Razorpay the same way it trusts every other website: through the certificate authorities built into your operating system or platform. Certificate renewals, a change of certificate authority, even a change to the root list need no action from you.
>
> **No risk of an outage from a stale pin.** Every pinned integration is one missed update away from failed payments. Root pinning reduces that risk but does not remove it: the root list can still change, and someone has to act within the notice period.
>
> **No loss of security.** Standard validation already checks that the certificate is issued for razorpay.com by a trusted authority and has not expired or been revoked. Pinning adds protection only against a certificate wrongly issued by a trusted authority, a risk the industry now covers through Certificate Transparency logs and CAA records rather than client-side pins. This is why Razorpay, like other major payment providers and certificate authorities, advises against pinning.

> [accordion] Which root certificate should I pin? Only the one used today?
>
> We strongly recommend that you do not pin at all; standard certificate validation is enough and needs no maintenance.
>
> If your security policy requires pinning, pin all the root certificates listed on this page, not only the one in today's chain. Razorpay may issue certificates under any of them, and any change to this list will be announced on this page at least 30 days in advance.

> [accordion] My server keeps its own certificate trust store. What do I need to do?
>
> Make sure your trust store has all the root certificates listed on this page. This matters most on servers that do not update automatically, such as locked-down Windows servers. If you maintain your own bundle manually, start from the [Mozilla CA bundle published by curl](https://curl.se/docs/caextract.html) and add any of the roots above that it does not include. See [Certificate trust store updates](#certificate-trust-store-updates) for how to update it.

> [accordion] Do I need to update my Razorpay SDK?
>
> We recommend that everyone uses the latest version of the Razorpay SDK for their platform. Current SDKs use an up-to-date trusted certificate list, either from your operating system or language runtime or bundled with the SDK, that already contains the root certificates on this page, so certificate renewals need no change on your side.
>
> You can find the latest versions of our SDKs and plugins at [razorpay.com/integrations](https://razorpay.com/integrations/).

> [accordion] How can I make sure my services remain uninterrupted after a renewal?
>
> Test before the renewal date. Connect to `https://api-ssl-test.razorpay.com` from your system. If it connects without an SSL or certificate error, you are ready. See [Verify your setup](#verify-your-setup) for the exact commands.
