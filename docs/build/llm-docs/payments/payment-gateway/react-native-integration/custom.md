# Integrate With React Native Custom SDK

The React Native SDK acts as a wrapper around the Razorpay Custom UI SDK to build a dynamic and responsive Checkout interface for your iOS or Android application.

**WARN**

**Watch Out!**

- Minimum software requirement: React version 16.5.0
- React Native version 0.57.1: This version of the Razorpay-React Native SDK supports Xcode 10. The  [known issues of React Native on Xcode 10](https://github.com/facebook/react-native/issues/19573) are fixed in the current version of our SDK.

**INFO**

**Handy Tips**

[Razorpay React Native Standard SDK](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/react-native-integration/standard.md) supports all payment methods by default. We recommend you integrate with the Razorpay React Native Standard SDK. If you integrate with Custom Checkout SDK, you will need to integrate these manually.

## List of Razorpay React Native Custom SDK Versions (Last 5 versions)

Version No. | Release Date | Changes
---
2.2.8 | 07 Jan 2026 | **Bug Fix**: A `RuntimeException` caused by `apiKey` not being found during activity recreation.
---
2.2.7 | 23 Nov 2025 | **Bug Fix**: Activity recreation crash.
---
2.2.6 | 08 Nov 2025 | **Feature**: Added support for unified Checkout experience.
---
2.2.5 | 24 Jun 2025 | **Bug Fix**: `getAppsWhichSupportUPI` NPE.
---
2.2.4 | 22 Feb 2024 | **Feature**: Calculate EMI function available on Android and iOS platforms.

**SUCCESS**

**Update SDK**

Check your current SDK version. If it is outdated, please [update the SDK](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/react-native-integration/custom/troubleshooting-faqs.md#3-how-can-i-update-the-razorpay-react) to ensure uninterrupted settlements of your funds.

**WARN**

**UPI Collect Flow Deprecated**

According to NPCI guidelines, the UPI Collect flow is being deprecated effective 28 February 2026. Customers can no longer make payments or register UPI mandates by manually entering VPA/UPI id/mobile numbers.

**Exemptions:** UPI Collect will continue to be supported for:
- MCC 6012 & 6211 (IPO and secondary market transactions).
- iOS mobile app and mobile web transactions.
- UPI Mandates (execute/modify/revoke operations only)
- eRupi vouchers.
- PACB businesses (cross-border/international payments).

**Action Required:**
- If you are a new Razorpay user, use [UPI Intent](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/web-integration/custom/payment-methods.md#intent-flow). 
- If you are an existing Razorpay user not covered by exemptions, you must migrate to UPI Intent or UPI QR code to continue accepting UPI payments. For detailed migration steps, refer to the [migration documentation](https://razorpay.com/docs/build/llm-docs/announcements/upi-collect-migration/custom-integration.md).

## Prerequisites

- Create a [Razorpay Account](https://dashboard.razorpay.com/signup).

- [Generate API Keys in Test Mode](https://razorpay.com/docs/build/llm-docs/api/authentication.md#generate-api-keys). To go live with the integration and start accepting real payments, generate Live Mode API Keys and replace them in the integration.
- Know about the [Razorpay Payment Flow](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/how-it-works.md).

## Integration Steps

Follow these integration steps:

1. [Build Integration](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/react-native-integration/custom/build-integration.md)
2. [Test Integration](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/react-native-integration/custom/test-integration.md)
3. [Go-Live Checklist](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/react-native-integration/custom/go-live-checklist.md)

### Related Information

- [Troubleshooting and FAQs](https://razorpay.com/docs/build/llm-docs/payments/payment-gateway/react-native-integration/standard/troubleshooting-faqs.md)
- [Address Verification System](https://razorpay.com/docs/build/llm-docs/payments/international-payments/address-verification-system.md)
