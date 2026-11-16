> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# About Razorpay Security

> Know about Razorpay's compliance certifications, firewalls, and authentication methods.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

As a financial service provider, we take utmost care of your data. We are continuously working to keep our environment safe and secure for everyone to use.

## Compliance

We follow the most stringent data security practices in the payment industry. As a payment service provider dealing with card data, we have the following certifications:

| Certifications | Seal |
| - | - |
| PCI-DSS Level 1 | [View Certificate](https://razorpay.com/docs/build/browser/assets/images/pci-dss-in.pdf) |
| ISO 27001:2022 IEC | ![ISO Seal](https://razorpay.com/docs/build/browser/assets/images/iso-seal.jpg) |
| System and Organization Controls (SOC) 2 Type 2 | ![SOC Seal](https://razorpay.com/docs/build/browser/assets/images/soc-seal.jpg) |

We can provide you with copies of our certifications. Please reach out to us via your Key Account Manager.

### TLS Encryption

At Razorpay, we employ the best encryption practices on our website and possess the highest assurance SSL certificate, the EV SSL (Extended Validity SSL) certificate.

<ul>
  <li>All Razorpay services are served over HTTPS using TLS and configured with industry-standard cyphers.</li>
  <li>You can download a copy of our [TLS certificate](https://razorpay.com/docs/security/whitelists.md#ssl-certificates).</li>
  <li>We follow industry-standard AES-128-bit encryption for all user data.</li>
  <li>Sensitive data, such as PII (Personal Identifiable Information) utilises field-level encryption.</li>
</ul>

## Authentication

Requests to Razorpay APIs are authenticated using Basic Authentication.
Know more about [API authentication](https://razorpay.com/docs/api/authentication.md).

Please ensure the security of your Dashboard credentials and API keys.

## Fraud and Risk

We are constantly building new processes to minimise the risk of online payment fraud. We actively monitor payment patterns and behaviour.

* Our robust fraud detection process identifies and flags fraudulent chargebacks for review.
* We check and flag hotlisted cards for every payment. (Hotlisting means that the card has been blocked temporarily or permanently for use.)
* We also use geographical and pattern-based transaction monitoring to identify fraudulent transactions.

Know more about [fraud protection for customers](https://razorpay.com/docs/security/customers.md#fraud-and-risk).

## Firewall

If you want to limit or authenticate ingress/egress to Razorpay, we provide a list of IP addresses for APIs and Webhooks.

* Razorpay API requests are resolved to these [IP addresses](https://razorpay.com/docs/security/whitelists.md#api-ips).
* Razorpay webhooks use these [IP addresses](https://razorpay.com/docs/security/whitelists.md#webhook-ips).

## Vulnerability Disclosure Policy

Razorpay looks forward to working with the security community to find vulnerabilities and protect our businesses and customers. We are dedicated to responsibly resolving any security concerns.

If you have discovered any security vulnerabilities associated with our services, we appreciate your help in disclosing them to us responsibly. We encourage you to report any bugs on our [HackerOne page](https://hackerone.com/razorpay). Please provide a detailed description of the vulnerability found and the steps to replicate it.

For more details on our bug bounty programme and to submit reports, visit our [HackerOne page](https://hackerone.com/razorpay).

### Related Information

* [Business Security Checklist](https://razorpay.com/docs/security/checklist.md)
* [Shared Responsibility Model](https://razorpay.com/docs/security/shared-responsibility-model.md)
* [Security For Customers](https://razorpay.com/docs/security/customers.md)
