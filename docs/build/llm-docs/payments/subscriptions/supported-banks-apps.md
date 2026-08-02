# Supported Banks and Apps

Razorpay Subscriptions supports recurring payments via Emandate, Cards and UPI Autopay. Use this page to check supported banks, apps and platform compatibility for each payment method.

**INFO**

**Dynamic Bank Lists**

The list of supported banks changes periodically. Use the [Methods API](#methods-api) to fetch the current list programmatically.

## Emandate

Emandate supports recurring payments via netbanking, debit card or Aadhaar authentication. To fetch the current list of supported banks and their authentication types, call the [Methods API](#methods-api). Supported banks appear under `recurring.emandate` in the response.

## Cards

We support Visa, Mastercard and RuPay cards from all major banks for recurring payments. To fetch the current list of supported card networks, call the [Methods API](#methods-api). Supported networks appear under `recurring.card` in the response.

**INFO**

**Handy Tips**

Contact our [Support team](https://razorpay.com/support/#request) if you face difficulties with card payments from any major bank.

## UPI Autopay

We support all apps and banks listed on the [NPCI Autopay members page](https://www.npci.org.in/product/autopay/all-members).

### Supported Apps and Handles

The table below shows frequently used UPI apps, their handles and whether they support mandate amounts above ₹15,000.

Application | Handles | Supports > ₹15,000
---
Google Pay | @okhdfcbank, @okicici, @okaxis, @oksbi | Yes
---
Paytm | @paytm | Yes
---
Amazon Pay | @apl, @yapl | Yes
---
PhonePe | @ybl, @ibl, @axl | No
---
BHIM | @upi | No

  
### Other UPI Apps and Handles

      
      Application | Handle
      ---
      BHIM Axis Pay | @axisbank, @sliceaxis
      ---
      BHIM Baroda Pay | @barodampay
      ---
      BHIM BOI UPI | @boi
      ---
      BHIM DLB UPI | @dlb
      ---
      BHIM IndusPay | @indus
      ---
      Canara Bank | @cnrb
      ---
      iMobile Pay | @icici
      ---
      NSDL Payments Bank | @nsdl
      ---
      DakPay | @postbank
      ---
      MobiKwik | @ikwik
      ---
      Digibank | @dbs
      ---
      PayZapp | @pz
      
    

### Amount Limits

The default maximum mandate amount for UPI Autopay is ₹15,000 per transaction. For certain MCCs, the limit increases to ₹1,00,000.

  
### MCCs with ₹1,00,000 Limit

      
      MCC | Description
      ---
      5413 | Credit Card Bill Payments
      ---
      5960 | Direct Marketing Insurance Services
      ---
      6012 | Financial Institutions Merchandise and Services
      ---
      6211 | Securities Brokers and Dealers
      ---
      6300 | Insurance Sales, Underwriting and Premiums
      ---
      6381 | Insurance Premiums
      ---
      6399 | Insurance
      ---
      6529 | LIC
      
    

Learn more about limits applicable to each merchant category by referring to [limits by MCC.](https://razorpay.com/docs/build/llm-docs/payments/recurring-payments/overview/integrate.md)

## UPI Intent Support

UPI Intent allows customers to complete mandate registration directly in their preferred UPI app. Support varies by checkout integration and platform.

  
    
    PSP App | mWeb | Android SDK | iOS SDK
    ---
    Google Pay | ✗ | ✓ | ✓
    ---
    PhonePe | ✓ | ✓ | ✓
    ---
    Paytm | ✓ | ✓ | ✓
    ---
    Amazon Pay | ✗ | ✗ | ✗
    ---
    BHIM | ✗ | ✓ | ✗
    
  
  
    
    PSP App | mWeb | Android SDK | iOS SDK
    ---
    Google Pay | ✓ | ✓ | ✗
    ---
    PhonePe | ✓ | ✓ | ✗
    ---
    Paytm | ✓ | ✓ | ✗
    ---
    Amazon Pay | ✗ | ✓ | ✗
    ---
    BHIM | ✗ | ✓ | ✗
    
  
  
    
    PSP App | mWeb | Android SDK | iOS SDK
    ---
    Google Pay | ✓ | ✓ | ✗
    ---
    PhonePe | ✓ | ✓ | ✗
    ---
    Paytm | ✓ | ✓ | ✗
    ---
    Amazon Pay | ✓ | ✓ | ✗
    ---
    BHIM | ✓ | ✓ | ✗
    
  

### UPI Intent for TPV

Third-Party Validation (TPV) ensures payments are made only from pre-registered bank accounts. The table below shows intent support for TPV.

  
    
    PSP App | mWeb | Android SDK | iOS SDK
    ---
    Google Pay | ✓ | ✓ | ✓
    ---
    PhonePe | ✓ | ✓ | ✗
    ---
    Paytm | ✓ | ✓ | ✓
    ---
    Amazon Pay | ✗ | ✓ | ✗
    ---
    BHIM | ✗ | ✓ | ✗
    
  
  
    
    PSP App | mWeb | Android SDK | iOS SDK
    ---
    Google Pay | ✓ | ✓ | ✓
    ---
    PhonePe | ✓ | ✓ | ✗
    ---
    Paytm | ✓ | ✓ | ✓
    ---
    Amazon Pay | ✗ | ✓ | ✗
    ---
    BHIM | ✗ | ✓ | ✗
    
  
  
    
    PSP App | mWeb | Android SDK | iOS SDK
    ---
    Google Pay | ✓ | ✓ | ✗
    ---
    PhonePe | ✓ | ✓ | ✗
    ---
    Paytm | ✓ | ✓ | ✗
    ---
    Amazon Pay | ✓ | ✓ | ✗
    ---
    BHIM | ✓ | ✓ | ✗
    
  

**WARN**

**Watch Out!**

- Contact [Support](https://razorpay.com/support/#request) to enable PSP apps other than PhonePe and Paytm on Standard Checkout for UPI TPV.
- UPI Intent TPV is not supported for @okaxis handle.

### UPI Intent for OC125

OC125 restricts customers from pausing or cancelling mandates. This feature is available only for lending businesses.

  
    
    PSP App | mWeb | Android SDK | iOS SDK
    ---
    Google Pay | ✓ | ✓ | ✓
    ---
    PhonePe | ✓ | ✓ | ✗
    ---
    Paytm | ✓ | ✓ | ✓
    
  
  
    
    PSP App | mWeb | Android SDK | iOS SDK
    ---
    Google Pay | ✓ | ✓ | ✓
    ---
    PhonePe | ✓ | ✓ | ✗
    ---
    Paytm | ✓ | ✓ | ✓
    
  
  
    
    PSP App | mWeb | Android SDK | iOS SDK
    ---
    Google Pay | ✓ | ✓ | ✗
    ---
    PhonePe | ✓ | ✓ | ✗
    ---
    Paytm | ✓ | ✓ | ✗
    
  

**WARN**

**Watch Out!**

- Contact [Support](https://razorpay.com/support/#request) to enable UPI Intent on Standard Checkout.
- UPI Intent is not supported for @okaxis handle.

## Methods API

Use the Methods API to fetch the current list of supported card networks and banks for subscriptions.

/methods

**INFO**

**[YOUR_KEY_ID] Required**

To fire this API, you need to provide your [KEY_ID] for authorization. Your [KEY_SECRET] is not required and should not be passed.

```curl: Request
curl -u [YOUR_KEY_ID] \
    -X GET https://api.razorpay.com/v1/methods
```json: Response
{
  "entity": "methods",
  ...
  ...
  ...
  "nach": true,
  ...
  ...
  ...
  "recurring": {
    "card": {
      "credit": [
        "MasterCard",
        "Visa"
      ]
    },
    "emandate": {
      "ANDB": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "Andhra Bank"
      },
      "UTIB": {
        "auth_types": [
          "netbanking"
        ],
        "name": "Axis Bank"
      },
      "BARB_R": {
        "auth_types": [
          "netbanking"
        ],
        "name": "Bank of Baroda - Retail Banking"
      },
      "MAHB": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "Bank of Maharashtra"
      },
      "CNRB": {
        "auth_types": [
          "netbanking"
        ],
        "name": "Canara Bank"
      },
      "CBIN": {
        "auth_types": [
          "netbanking"
        ],
        "name": "Central Bank of India"
      },
      "CIUB": {
        "auth_types": [
          "netbanking"
        ],
        "name": "City Union Bank"
      },
      "COSB": {
        "auth_types": [
          "netbanking"
        ],
        "name": "Cosmos Co-operative Bank"
      },
      "DEUT": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "Deutsche Bank"
      },
      "DLXB": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "Dhanlaxmi Bank"
      },
      "ESFB": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "Equitas Small Finance Bank"
      },
      "FDRL": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "Federal Bank"
      },
      "HDFC": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "HDFC Bank"
      },
      "HSBC": {
        "auth_types": [
          "netbanking"
        ],
        "name": "Hongkong & Shanghai Banking Corporation"
      },
      "ICIC": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "ICICI Bank"
      },
      "IBKL": {
        "auth_types": [
          "netbanking"
        ],
        "name": "IDBI"
      },
      "IDFB": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "IDFC FIRST Bank"
      },
      "IOBA": {
        "auth_types": [
          "netbanking"
        ],
        "name": "Indian Overseas Bank"
      },
      "INDB": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "Indusind Bank"
      },
      "KARB": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "Karnataka Bank"
      },
      "KKBK": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "Kotak Mahindra Bank"
      },
      "ORBC": {
        "auth_types": [
          "netbanking"
        ],
        "name": "PNB (Erstwhile-Oriental Bank of Commerce)"
      },
      "PYTM": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "Paytm Payments Bank"
      },
      "PUNB_R": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "Punjab National Bank - Retail Banking"
      },
      "RATN": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "RBL Bank"
      },
      "SIBL": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "South Indian Bank"
      },
      "SCBL": {
        "auth_types": [
          "netbanking"
        ],
        "name": "Standard Chartered Bank"
      },
      "SBIN": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "State Bank of India"
      },
      "TMBL": {
        "auth_types": [
          "netbanking"
        ],
        "name": "Tamilnadu Mercantile Bank"
      },
      "USFB": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "Ujjivan Small Finance Bank"
      },
      "UBIN": {
        "auth_types": [
          "netbanking"
        ],
        "name": "Union Bank of India"
      },
      "YESB": {
        "auth_types": [
          "netbanking",
          "debitcard"
        ],
        "name": "Yes Bank"
      },
      "AUBL": {
        "auth_types": [
          "debitcard"
        ],
        "name": "AU Small Finance Bank"
      },
      "CITI": {
        "auth_types": [
          "debitcard"
        ],
        "name": "CITI Bank"
      },
      "DCBL": {
        "auth_types": [
          "debitcard"
        ],
        "name": "DCB Bank"
      }
    },
    "nach": true
  },
  ...
  ...
  ...
}
```

### Related Information

- [About Subscriptions](https://razorpay.com/docs/build/llm-docs/payments/subscriptions.md)
- [Subscription Workflow](https://razorpay.com/docs/build/llm-docs/payments/subscriptions/workflow.md)
- [Subscription States](https://razorpay.com/docs/build/llm-docs/payments/subscriptions/states.md)
- [Create Subscriptions](https://razorpay.com/docs/build/llm-docs/payments/subscriptions/create.md)
- [Test Subscriptions](https://razorpay.com/docs/build/llm-docs/payments/subscriptions/test.md)
- [Subscriptions APIs](https://razorpay.com/docs/build/llm-docs/payments/subscriptions/apis.md)
