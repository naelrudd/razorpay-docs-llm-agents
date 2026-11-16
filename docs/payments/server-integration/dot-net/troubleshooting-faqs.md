> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Troubleshooting & FAQs

> Troubleshoot common error scenarios and find answers to frequently asked questions about Razorpay .NET SDK.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

> [accordion] How to resolve the following error displayed during Orders API integration?
>
> Following are the solutions for two possible errors:
>
> ### Server Response: Array
>
> | Error | Cause |
> | - | - |
> | The server did not send back a well-formed response. Server Response: Array. | This error appears if you are using TLS v1 on your client-side. |
>
> **Resolution**
>
> * **Fix 1**: Verify if client supports TLS v1.1 using this website: [How's My SSL?](https://www.howsmyssl.com/s/api.html). If yes, upgrade the client to `TLS v1.1+`.
> * **Fix 2**: Use the code given below to force TLS v1.2:
>
> ```c Force TLS v1.2 theme={null}
> System.Net.ServicePointManager.SecurityProtocol = SecurityProtocolType.Tls12;
> ```
>
> ### Exception User-Unhandled
>
> | Error | Cause |
> | - | - |
> | Exception User-Unhandled | This error appears if you are using TLS v1 on your client-side |
>
> **Resolution**
>
> Use the code given below to force TLS v1.2.
>
> ```c Force TLS v1.2 theme={null}
> System.Net.ServicePointManager.SecurityProtocol = SecurityProtocolType.Tls12;
> ```

> [accordion] Does Razorpay support ASP.NET?
>
> We only have the .NET framework on which ASP.NET works; we do not support it for .NET core.
