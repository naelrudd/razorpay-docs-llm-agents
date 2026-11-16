> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Java Server SDK Prerequisites

> Check the prerequisites before you integrate with Razorpay Java server-side SDK.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Install the Razorpay Java SDK and integrate it with your Java-based website to accept payments, initiate refunds and much more.

## Dependencies

* You must use Java v15 or higher. Know more about the [latest java versions](https://www.java.com/releases/).

* Import the following packages before your get started:

```json Import Package theme={null}
import org.json.JSONObject;
import com.razorpay.*;
```

## Installation

You can install Razorpay using Maven or Gradle.

> [tab] Maven
>
> 1. Download  and install [Maven](https://maven.apache.org/download.cgi)  on your system.
> 2. Download the [latest Source code](https://github.com/razorpay/razorpay-java/releases) zip file from the Releases section of GitHub.
> 3. Unzip the file and add this dependency to the project object model (POM) of your project.
>
> ```java Java theme={null}
> <dependency>
> <groupId>com.razorpay</groupId>
> <artifactId>razorpay-java</artifactId>
> <version>x.y.z</version> //x.y.z = the version you want to install
> </dependency>
> ```

> [tab] Gradle
>
> 1. [Download](https://gradle.org/releases) and [install](https://docs.gradle.org/current/userguide/installation.html) Gradle on your system.
> 2. Download the [latest Source code](https://github.com/razorpay/razorpay-java/releases) zip file from the Releases section of GitHub.
> 3. Unzip the file and add this dependency to the build file of the project:
>
> ```java Java theme={null}
> implementation 'com.razorpay:razorpay-java:x.y.z" //x.y.z = the version you want to install
> ```

> [card] [Payment Gateway](https://razorpay.com/docs/sg/payments/server-integration/java/integration-steps.md)
>
> Integrate with Razorpay Payment Gateway.

> [card] [API Sample Codes](https://github.com/razorpay/razorpay-java/tree/master/documents)
>
> Integrate using API sample codes.

> [card] [Other Razorpay Products](https://razorpay.com/docs/sg/payments/server-integration/java/integration-steps.md#integrate-with-other-razorpay-products)
>
> Integrate with other Razorpay products.

## Support

* **Queries**: If you have queries, [contact support](https://razorpay.com/sg/support/).

* **Feature Request:** If you have a feature request, raise an issue on [GitHub](https://github.com/razorpay/razorpay-java/issues/new).

### Related Information

[Address Verification System](https://razorpay.com/docs/sg/payments/international-payments/address-verification-system.md)
