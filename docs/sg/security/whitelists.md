> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Razorpay IPs and Certificates

> Download Razorpay SSL certificates and whitelist our API and Webhooks IP addresses.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can whitelist Razorpay-issued SSL certificates and IP addresses to communicate with Razorpay APIs and Webhooks. By downloading Razorpay SSL certificates and whitelisting our IPs, you can verify that you are securely communicating with our servers.

## SSL Certificates

> [!NOTE]
>
> **Update (September 2026):** Razorpay no longer publishes new SSL certificate files. The table below is provided for historical reference only, with X10 being the last certificate published. Do not pin these certificates.
>
> For the current SSL certificate policy, including certificate pinning, root certificates, certificate changes, verification steps and FAQs, see the [Guidelines for SSL Certificate Rotation](https://razorpay.com/docs/sg/security/whitelists/guidelines-ssl-cert-rotation.md).

Past SSL certificates for `api.razorpay.com`, along with their validity periods, are listed below.

| Certificate File | Valid From | Expiry |
| - | - | - |
| [X10.pem](https://razorpay.com/docs/build/browser/assets/images/certs-x10.pem) & [Chain](https://razorpay.com/docs/build/browser/assets/images/certs-x10-chain.pem) | Oct 9th, 2025 | Nov 9th, 2026 |
| [X9.pem](https://razorpay.com/docs/build/browser/assets/images/certs-x9.pem) & [Chain](https://razorpay.com/docs/build/browser/assets/images/certs-x9-chain.pem) | Nov 11th, 2024 | Dec 12th, 2025 |
| [X8.pem](https://razorpay.com/docs/build/browser/assets/images/certs-x8.pem) & [Chain](https://razorpay.com/docs/build/browser/assets/images/certs-x8-chain.pem) | Jan 5th, 2024 | Jan 4th, 2025 |
| [X7.pem](https://razorpay.com/docs/build/browser/assets/images/certs-x7.pem) & [Chain](https://razorpay.com/docs/build/browser/assets/images/certs-x7-chain.pem) | Feb 3rd, 2023 | Feb 2nd, 2024 |
| [X6.pem](https://razorpay.com/docs/build/browser/assets/images/certs-x6.pem) & [Chain](https://razorpay.com/docs/build/browser/assets/images/certs-x6-chain.pem) | May 19th, 2022 | May 19th, 2023 |
| [X4.pem](https://razorpay.com/docs/build/browser/assets/images/certs-x4.pem) & [Chain](https://razorpay.com/docs/build/browser/assets/images/certs-x4-chain.pem) | July 7th, 2021 | June 7th, 2022 |
| [X3.pem](https://razorpay.com/docs/build/browser/assets/images/certs-x3.pem) & [Chain](https://razorpay.com/docs/build/browser/assets/images/certs-x3-chain.pem) | March 13th, 2020 | July 28th, 2021 |
| [X2.pem](https://razorpay.com/docs/build/browser/assets/images/certs-x2.pem) & [Chain](https://razorpay.com/docs/build/browser/assets/images/certs-x2-chain.pem) | April 10th, 2019 | April 15th, 2020 |
| [X1.pem](https://razorpay.com/docs/build/browser/assets/images/certs-x1.pem) & [Chain](https://razorpay.com/docs/build/browser/assets/images/certs-x1-chain.pem) | Feb 7th, 2016 | April 12th, 2019 |

These files applied to past rotations only. Do not pin or whitelist them for new integrations.

> [!WARNING]
>
> **Watch Out!**
>
> We highly discourage pinning our SSL certificate to your applications. If your internal policy mandates pinning, pin all the root CA certificates listed on the [Guidelines for SSL Certificate Rotation](https://razorpay.com/docs/sg/security/whitelists/guidelines-ssl-cert-rotation.md) page, not the certificate files above. Otherwise, use the [latest CA Bundle](https://curl.haxx.se/docs/caextract.html) provided by your OS.

## Webhook IPs

Below is the list of IPs from which Webhooks are sent from our servers.

```javascript Non-cde theme={null}
54.169.125.233
13.215.109.81
18.138.140.254
```

```javascript Cde theme={null}
18.139.8.177
13.213.198.156
13.250.66.198
```

We highly recommend using [Webhook Signature](https://razorpay.com/docs/sg/webhooks/validate-test.md#validate-webhooks) to validate the integrity of the webhooks, even if you have whitelisted our Webhook IPs.

### Related Information

[Razorpay Security](https://razorpay.com/docs/sg/security)
