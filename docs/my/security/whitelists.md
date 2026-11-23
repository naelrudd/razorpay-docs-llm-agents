> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Razorpay Curlec IPs and Certificates

> Download Razorpay Curlec SSL certificates and whitelist our API and Webhooks IP addresses.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can whitelist Razorpay Curlec-issued SSL certificates and IP addresses to communicate with Razorpay Curlec APIs and Webhooks. By downloading Razorpay Curlec SSL certificates and whitelisting our IPs, you can verify that you are securely communicating with our servers.

## SSL Certificates

> [!NOTE]
>
> **Update (September 2026):** Razorpay Curlec no longer publishes new SSL certificate files. The table below is provided for historical reference only, with X10 being the last certificate published. Do not pin these certificates.
>
> For the current SSL certificate policy, including certificate pinning, root certificates, certificate changes, verification steps and FAQs, see the [Guidelines for SSL Certificate Rotation](https://razorpay.com/docs/my/security/whitelists/guidelines-ssl-cert-rotation.md).

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
> We highly discourage pinning our SSL certificate to your applications. If your internal policy mandates pinning, pin all the root CA certificates listed on the [Guidelines for SSL Certificate Rotation](https://razorpay.com/docs/my/security/whitelists/guidelines-ssl-cert-rotation.md) page, not the certificate files above. Otherwise, use the [latest CA Bundle](https://curl.haxx.se/docs/caextract.html) provided by your OS.

## API IPs

Requests to Razorpay Curlec APIs should be routed to `api.razorpay.com`. This will be resolved to various IPs controlled by our load balancers. However, if the IPs to which the requests should be sent are restricted, all your API requests can be routed to `prod-api-static.razorpay.com`. This will be resolved to any of the following IPs:

```javascript API Ingress IPs theme={null}
52.66.140.48
52.66.140.61
13.235.207.57
13.232.63.19
13.234.135.6
13.234.83.3 
13.235.208.84
13.235.96.132
15.206.46.184
18.99.160.48/29
```

> [!NOTE]
>
> **Handy Tips**
>
> * `18.99.160.0/29` is a CIDR range. All the IPs in the range `18.99.160.48 - 18.99.160.55` are utilised.
>
> * All our SDKs use proper DNS caching and honour the TTLs that we set. However, if you are not using our SDKs, ensure that DNS TTLs set by Razorpay Curlec are honoured and are not cached aggressively.

## Webhook IPs

Below is the list of IPs from which Webhooks are sent from our servers.

```javascript Egress IPs theme={null}
43.216.167.81
43.216.100.227
43.216.239.250
```

We highly recommend using [Webhook Signature](https://razorpay.com/docs/my/webhooks/validate-test.md#validate-webhooks) to validate the integrity of the webhooks, even if you have whitelisted our Webhook IPs.

## UAT Static IPs

Below is the list of UAT egress IPs.

```javascript UAT Egress IPs theme={null}
52.66.76.68
52.66.95.207
13.127.201.109
```

### Related Information

[Razorpay Curlec Security](https://razorpay.com/docs/my/security)
