> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Supported Banks and Apps

> List of banks and apps that support Subscription using Emandate (Netbanking, Debit Card, Aadhaar), card and UPI.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Razorpay Subscriptions in Singapore supports recurring card payments from the following banks.

## Supported Banks

| S. No. | Bank Name |
| - | - |
| 1 | Bank of America, National Association |
| 2 | Bank of China |
| 3 | CIMB Bank |
| 4 | Citibank Singapore |
| 5 | DBS Bank |
| 6 | GXS Bank |
| 7 | HSBC Bank Singapore |
| 8 | Industrial and Commercial Bank of China |
| 9 | MariBank |
| 10 | MayBank Singapore |
| 11 | CBC Bank |
| 12 | Standard Chartered Bank |
| 13 | Hongkong and Shanghai Banking Corporation |
| 14 | Trust Bank Singapore |
| 15 | UOB Bank |

## Methods API

Use the Methods API to fetch the current list of supported card networks and banks for subscriptions.

`GET /methods`

> [!NOTE]
>
> **\[YOUR\_KEY\_ID] Required**
>
> To fire this API, you need to provide your \[KEY\_ID] for authorization. Your \[KEY\_SECRET] is not required and should not be passed.

```bash Request theme={null}
curl -u [YOUR_KEY_ID] \
    -X GET https://api.razorpay.com/v1/methods
```

```json Response theme={null}
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

* [About Subscriptions](https://razorpay.com/docs/sg/payments/subscriptions)
* [Subscription Workflow](https://razorpay.com/docs/sg/payments/subscriptions/workflow.md)
* [Subscription States](https://razorpay.com/docs/sg/payments/subscriptions/states.md)
* [Create Subscriptions](https://razorpay.com/docs/sg/payments/subscriptions/create.md)
* [Test Subscriptions](https://razorpay.com/docs/sg/payments/subscriptions/test.md)
* [Subscriptions APIs](https://razorpay.com/docs/sg/payments/subscriptions/apis.md)
