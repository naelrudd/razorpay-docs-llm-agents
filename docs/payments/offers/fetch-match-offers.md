> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fetch and Match Offers Using APIs

> Fetch the offers on your account or find the offers that apply to a customer's order, so you can show them on your website or app.

Available in
🇮🇳 India

Use the Fetch Offers and Match Offers APIs to show offers on your own website or app. For example, show offer badges on product pages or list the offers a customer can get on your payment page. The APIs work for offers on the whole order (cart-level offers) and for offers on specific products in the cart (SKU-level offers).

## Prerequisites

* [Generate the API keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md) from the Dashboard. You need the `key_id` and `key_secret` to authenticate API requests.
* [Create the offers](https://razorpay.com/docs/payments/offers/create.md) you want to give from the Dashboard.

## Choose an API

| API | Use it to |
| - | - |
| [Fetch Offers](#fetch-offers) | Get the full catalogue of active offers on your account. Cache it on your server and match offers to orders yourself. |
| [Match Offers](#match-offers) | Get the offers that apply to a specific order and, optionally, a payment instrument. Razorpay does the matching and calculates the discount. |

## Key Concepts

### Offer Structure

Every offer has one or more rules. Each rule has eligibility criteria and the benefits the customer gets when the criteria are met.

```text theme={null}
Offer
├── display_name, description, currency, terms
├── schedules[], benefits_types[]
├── usage_limits[], display_config
└── rules
    └── Rule
        ├── criteria
        │   ├── includes   (conditions that must all be true)
        │   │   ├── payment_instrument
        │   │   └── order   (order amount and SKU conditions)
        │   └── excludes   (conditions that disqualify the transaction)
        └── benefits
            └── items[]
                ├── type, applicable_on, value, max_benefit_value
                ├── limit_type, unit, tenures[]
                ├── calculated_benefit_value   (Match Offers only)
                └── benefit_breakup[]          (Match Offers only)
```

* `criteria.includes` lists the conditions that must all be true for the offer to apply.
* `criteria.excludes` lists the conditions that disqualify a transaction. It is an empty object `{}` when no exclusions are set.
* Razorpay evaluates the rules in an offer independently. Each rule applies either to the whole cart or to line items, never both.

### Cart-Level and SKU-Level Offers

| Field | Cart-level offer | SKU-level offer |
| - | - | - |
| `criteria.includes.order.applies_to` | `cart` | `line_items` |
| `criteria.includes.order.line_item` | Absent | Present. Contains `skus`, `brands`, `min_quantity` and `min_price`. |
| `benefits.items[].applicable_on` | `cart` | `line_item` |
| `benefits.items[].calculated_benefit_value` | Flat reduction on the order total. | Sum of the discount on each eligible SKU. |
| `benefits.items[].benefit_breakup` | Absent | Present. Shows the discount on each SKU. |

All amounts in these APIs are in paise. For example, pass `150000` for ₹1,500.

## Fetch Offers

Use this API to fetch the complete catalogue of active offers on your account. Use the response to build a local cache and match eligibility on your server. For SKU-level offers, the eligible SKUs are returned inline.

`GET /v1/offers`

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X GET 'https://api.razorpay.com/v1/offers?status=active&count=10&skip=0'
```

### Query Parameters

**status** `string`

Filter offers by status. Possible values are `active` (default) and `inactive`.

**starts\_at** `integer`

Unix timestamp. Returns offers that start on or after this time.

**ends\_at** `integer`

Unix timestamp. Returns offers that end on or before this time.

**count** `integer`

Number of offers to return. Default is `10`. Maximum is `100`.

**skip** `integer`

Number of offers to skip. Use it with `count` to paginate. Default is `0`.

### Response

```json theme={null}
{
  "entity": "collection",
  "count": 2,
  "has_more": false,
  "items": [
    {
      "entity": "offer",
      "id": "offer_MULTISKU_001",
      "name": "10% off on Apple devices with HDFC Bank cards",
      "status": "ACTIVE",
      "starts_at": 1738368600,
      "ends_at": 1740960600,
      "display_name": "10% Off on Apple Devices",
      "description": "Get 10% off up to ₹1,500 on Apple iPhone and iPad purchases with HDFC Bank cards.",
      "currency": "INR",
      "terms": {
        "tnc": "Valid on Apple iPhone and iPad purchases only.",
        "url": "https://example.com/offers/apple-hdfc/tnc"
      },
      "benefits_types": ["instant_discount"],
      "usage_limits": [
        {
          "on": "CARD_NUMBER",
          "limit_type": "COUNT",
          "limit_value": 5,
          "frequency_type": "MONTHLY",
          "frequency_value": 2,
          "tracking_level": "TRACKING_LEVEL_OFFER"
        }
      ],
      "display_config": {
        "offer_display_priority": 1,
        "should_validate": true,
        "is_hidden": false,
        "auto_apply": false
      },
      "rules": {
        "entity": "collection",
        "count": 1,
        "items": [
          {
            "criteria": {
              "includes": {
                "payment_instrument": {
                  "methods": ["card"],
                  "card": {
                    "issuers": ["HDFC"],
                    "types": ["CREDIT", "DEBIT"],
                    "networks": ["Visa", "Mastercard"]
                  }
                },
                "order": {
                  "applies_to": "line_items",
                  "min_amount": 3000000,
                  "line_item": {
                    "skus": {
                      "type": "list",
                      "values": ["IPHONE16_128", "IPHONE16_256", "IPAD_AIR_M2"]
                    },
                    "brands": ["apple"],
                    "min_quantity": 1,
                    "min_price": 3000000
                  }
                }
              },
              "excludes": {}
            },
            "benefits": {
              "entity": "collection",
              "count": 1,
              "items": [
                {
                  "type": "instant_discount",
                  "applicable_on": "line_item",
                  "value": 10,
                  "max_benefit_value": 150000,
                  "calculated_benefit_value": 0,
                  "benefit_breakup": [],
                  "limit_type": "UPTO",
                  "unit": "PERCENTAGE",
                  "tenures": []
                }
              ]
            }
          }
        ]
      }
    },
    {
      "entity": "offer",
      "id": "offer_CART_002",
      "name": "Flat ₹2,000 off on orders above ₹1,00,000 with HDFC Bank credit cards",
      "status": "ACTIVE",
      "starts_at": 1738368600,
      "ends_at": 1740960600,
      "display_name": "₹2,000 Off with HDFC Bank Credit Cards",
      "description": "Flat ₹2,000 off on orders above ₹1,00,000 with HDFC Bank credit cards.",
      "currency": "INR",
      "terms": {
        "tnc": "Valid on HDFC Bank credit card transactions.",
        "url": "https://example.com/offers/hdfc-cart/tnc"
      },
      "benefits_types": ["instant_discount"],
      "display_config": {
        "offer_display_priority": 2,
        "should_validate": true,
        "is_hidden": false,
        "auto_apply": false
      },
      "rules": {
        "entity": "collection",
        "count": 1,
        "items": [
          {
            "criteria": {
              "includes": {
                "payment_instrument": {
                  "methods": ["card"],
                  "card": {
                    "issuers": ["HDFC"],
                    "types": ["CREDIT"]
                  }
                },
                "order": {
                  "applies_to": "cart",
                  "min_amount": 10000000
                }
              },
              "excludes": {}
            },
            "benefits": {
              "entity": "collection",
              "count": 1,
              "items": [
                {
                  "type": "instant_discount",
                  "applicable_on": "cart",
                  "value": 200000,
                  "max_benefit_value": 200000,
                  "calculated_benefit_value": 0,
                  "benefit_breakup": [],
                  "limit_type": "FLAT",
                  "unit": "FIXED",
                  "tenures": []
                }
              ]
            }
          }
        ]
      }
    }
  ]
}
```

### Response Parameters

**entity** `string`

Always `collection`.

**count** `integer`

Number of offers returned on this page.

**has\_more** `boolean`

`true` if more offers exist beyond this page.

**items** `array`

List of [offer objects](#offer-object).

### Offer Object

**entity** `string`

Always `offer`.

**id** `string`

Unique identifier of the offer. For example, `offer_MULTISKU_001`.

**name** `string`

Internal name of the offer.

**display\_name** `string`

Customer-facing name of the offer.

**description** `string`

Short explanation of the offer, usually shown alongside it.

**terms** `object`

Structured terms and conditions: `tnc`, the text, and `url`, a link to the full terms.

**status** `string`

Status of the offer. Possible values are `ACTIVE` and `INACTIVE`.

**inactivation\_reason** `string`

Why the offer was deactivated. Present only when the offer is inactive. Possible values are `INACTIVATION_REASON_UNSPECIFIED`, `EXPIRED`, `EXHAUSTED`, `ON_DEMAND`, `ADVERTISER_ON_DEMAND`, `ADVERTISER_EXPIRED` and `DISCONTINUED`.

**starts\_at** `integer`

Unix timestamp when the offer becomes active.

**ends\_at** `integer`

Unix timestamp when the offer expires.

**currency** `string`

Currency of the offer. For example, `INR`.

**schedules** `array`

Time windows in which the offer is available, for example the 1st of every month or weekdays only.

* `period`: How often the window recurs. Possible values are `DAILY`, `WEEKLY`, `FORTNIGHTLY`, `MONTHLY`, `MONTH_WEEKLY`, `YEARLY`, `CALENDAR_MONTHLY` and `CALENDAR_YEARLY`.
* `interval`: Interval values for the period. For example, `[1]` for the 1st of every month.
* `starts_at` and `ends_at`: Unix timestamps for the start and end of the schedule.
* `days_of_week`: Days of the week, from `SUNDAY` to `SATURDAY`.
* `dates_of_month`: Dates of the month, from `DATE_1` to `DATE_31`.
* `months_of_year`: Months, from `JANUARY` to `DECEMBER`.
* `weeks_of_month`: Weeks of the month, from `FIRST` to `SIXTH`.

**benefits\_types** `array`

Types of benefit the offer gives. Possible values are `instant_discount`, `cashback`, `already_discounted`, `no_cost_emi` and `low_cost_emi`.

**usage\_limits** `array`

Usage restrictions on the offer, for example a maximum of 5 redemptions per card in 2 months.

* `on`: What the limit is tracked on. Possible values are `OFFER`, `MOBILE`, `EMAIL`, `CARD_NUMBER` and `CUSTOMER_ID`.
* `limit_type`: `BUDGET` for an amount cap or `COUNT` for a redemption cap.
* `limit_value`: The limit. A count, or an amount in paise.
* `frequency_type`: The window the limit applies to. Possible values are `DAILY`, `WEEKLY`, `FORTNIGHTLY`, `MONTHLY`, `MONTH_WEEKLY`, `YEARLY`, `CALENDAR_MONTHLY` and `CALENDAR_YEARLY`.
* `frequency_value`: Multiplier for `frequency_type`. For example, `2` with `MONTHLY` means 2 months.
* `tracking_level`: `TRACKING_LEVEL_OFFER` or `TRACKING_LEVEL_PUBLISHER`.

**display\_config** `object`

How to present the offer.

* `offer_display_priority`: Display priority. A higher number means a higher priority.
* `should_validate`: Whether to validate the offer before you show it.
* `is_hidden`: Whether the offer is hidden.
* `auto_apply`: Whether to apply the offer automatically, without the customer selecting it.

**rules** `object`

Collection of [rule objects](#rule-object): `entity` (always `collection`), `count` and `items`.

Fetch Offers does not return `eligible`. [Match Offers](#match-offers) returns it.

### Rule Object

**criteria.includes** `object`

Conditions that must all be true for the offer to apply. Contains `payment_instrument` and `order`.

**criteria.excludes** `object`

Conditions that disqualify a transaction. Same structure as `criteria.includes`. It is `{}` when no exclusions are set.

**criteria.includes.payment\_instrument** `object`

Payment instrument conditions. See [payment instrument conditions](#payment-instrument-conditions).

**criteria.includes.order.applies\_to** `string`

Scope of the rule. `cart` for a cart-level offer or `line_items` for an SKU-level offer.

**criteria.includes.order.min\_amount** `integer`

Minimum order amount in paise.

**criteria.includes.order.max\_amount** `integer`

Maximum order amount in paise. Absent if there is no upper limit.

**criteria.includes.order.line\_item** `object`

SKU conditions. Present only when `applies_to` is `line_items`.

* `skus`: The eligible SKUs. `type` is `list` and `values` has the SKU identifiers.
* `brands`: Eligible brands. For example, `["apple"]`.
* `min_quantity`: Minimum quantity of each eligible SKU.
* `min_price`: Minimum price of the eligible line items, in paise.

**benefits** `object`

Collection of [benefit objects](#benefit-object): `entity` (always `collection`), `count` and `items`.

### Payment Instrument Conditions

The same structure appears in an offer's rules and in `criteria.payment_instrument` of the Match Offers request.

**methods** `array`

Payment methods. Possible values are `card`, `upi`, `netbanking`, `wallet` and `emi`. For example, `["card"]`.

**card** `object`

Card conditions. Present when `methods` is `["card"]`.

* `saved`: When `true`, only saved cards are eligible.
* `international`: Whether international cards are eligible.
* `issuers`: Issuing banks. For example, `["HDFC", "Axis"]`.
* `types`: Card types. Possible values are `CREDIT`, `DEBIT` and `PREPAID`.
* `networks`: Card networks. For example, `["Visa", "Mastercard"]`.
* `categories`: Card categories. For example, `["Platinum"]`.
* `iins`: Card IINs, the first 6 digits of the card number.
* `subtype`: Card subtypes. Possible values are `CONSUMER` and `BUSINESS`.
* `cobranding_partners`: Co-branding partners. For example, `["onecard"]`.
* `tokens`: Tokens associated with the card.
* `reference_number`: Reference number of the card.

**upi** `object`

UPI conditions. Present when `methods` is `["upi"]`.

* `psps`: Payment service providers. For example, `["PHONEPE", "GPAY"]`.
* `vpa_handle`: UPI ID handles.
* `payer_account_types`: Possible values are `BANK`, `WALLET` and `CREDIT_CARD`.
* `flow`: UPI flows. Possible values are `COLLECT`, `INTENT` and `IN_APP`.
* `payer_account_bins`: Payer account BINs.

**bank\_account** `object`

Bank account conditions: `account_numbers`, `ifscs` and `names` (account holder names). Present when `methods` is `["netbanking"]`.

**netbanking** `object`

Netbanking conditions: `banks`, the eligible banks. Present when `methods` is `["netbanking"]`.

**emi** `object`

EMI conditions: `durations`, the eligible tenures in months. Present when `methods` is `["emi"]`.

**wallet** `object`

Wallet conditions: `providers`, the eligible wallet providers. Present when `methods` is `["wallet"]`.

### Benefit Object

**type** `string`

Benefit type. Possible values are `instant_discount`, `cashback`, `low_cost_emi`, `no_cost_emi` and `already_discounted`.

**applicable\_on** `string`

Where the benefit applies: `cart` or `line_item`.

**value** `integer`

Size of the benefit. Percentage points when `unit` is `PERCENTAGE` (for example, `10` for 10%) or an amount in paise when it is `FIXED`.

**max\_benefit\_value** `integer`

Maximum benefit in paise.

**limit\_type** `string`

`FLAT` or `UPTO`.

**unit** `string`

`FIXED` or `PERCENTAGE`.

**tenures** `array`

EMI tenures in months that the benefit applies to, if any.

**calculated\_benefit\_value** `integer`

The calculated discount in paise. Empty in Fetch Offers. Populated by [Match Offers](#match-offers).

## Match Offers

Use this API during checkout to find the offers that apply to the customer's order and, optionally, their payment instrument. The response lists the matched offers with the calculated discount, including the discount on each SKU for SKU-level offers. It can also include the offers that did not match.

`POST /v1/offers/match`

### When to Call

| Checkout stage | What to pass | What you get |
| - | - | - |
| Before the customer selects a payment instrument, for example on the product or cart page | `criteria.order` only. Do not pass `criteria.payment_instrument`. | All offers that apply to the order across payment instruments. Use them to show offer badges. |
| Payment page | `criteria.order` and `criteria.payment_instrument` | Offers that apply to this order and the selected payment instrument. |
| Card number entry | `criteria.payment_instrument.card.iins` with the IIN the customer enters | Offers that apply to that specific card. |

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/offers/match \
-H "Content-Type: application/json" \
-d '{
  "criteria": {
    "offers": ["offer_MULTISKU_001", "offer_MULTISKU_002", "offer_CART_002"],
    "order": {
      "amount": 15489900,
      "currency": "INR",
      "line_items": [
        {
          "sku": "IPHONE16_128",
          "brand": "apple",
          "quantity": 1,
          "price": 7990000
        },
        {
          "sku": "SAMSUNG_S24",
          "brand": "samsung",
          "quantity": 1,
          "price": 7499900
        }
      ]
    },
    "customer": {
      "contact": "+919000090000",
      "email": "gaurav.kumar@example.com"
    },
    "payment_instrument": {
      "methods": ["card"],
      "card": {
        "issuers": ["HDFC"],
        "types": ["CREDIT"],
        "networks": ["Visa"]
      }
    }
  },
  "ineligible": {
    "include": true
  },
  "count": 10,
  "skip": 0
}'
```

### Request Parameters

**criteria** `object`

Inputs used to evaluate eligibility. If you do not pass it, Razorpay evaluates all active offers without filters.

**criteria.offers** `array`

IDs of specific offers to evaluate. Maximum 20. If you do not pass it, all active offers are evaluated.

**criteria.order\_id** `string`

Order ID for the request.

**criteria.order** `object`

Cart details used to evaluate eligibility.

**criteria.order.amount** `integer`

Total cart amount in paise.

**criteria.order.currency** `string`

Currency code. For example, `INR`.

**criteria.order.notes** `object`

Key-value pairs of notes for the order.

**criteria.order.line\_items** `array`

Products in the cart. Required to evaluate SKU-level offers.

**criteria.order.line\_items\[].sku** `string`

SKU identifier of the product. Required when you pass `line_items`.

**criteria.order.line\_items\[].brand** `string`

Brand of the product. Not case-sensitive. Required when you pass `line_items`. Brand offers are evaluated correctly only when you pass it.

**criteria.order.line\_items\[].quantity** `integer`

Quantity in the cart. Must be 1 or more. Required when you pass `line_items`.

**criteria.order.line\_items\[].price** `integer`

Unit price of the product in paise. Required when you pass `line_items`.

**criteria.order.line\_items\[].notes** `object`

Key-value pairs of notes for the line item.

**criteria.payment\_instrument** `object`

Payment instrument to filter offers by. If you do not pass it, offers are returned for all instruments. Pass `methods`, required when you pass an instrument, and the [conditions for that method](#payment-instrument-conditions).

**criteria.customer** `object`

Customer details used to check per-customer usage limits.

* `id`: Customer ID.
* `contact`: Customer's phone number. `mobile_number` is accepted as an alias.
* `email`: Customer's email address.
* `card_number`: Customer's card number.
* `upi_vpa`: Customer's UPI ID.

**ineligible** `object`

Pass `{"include": true}` to also return the offers that did not match.

**count** `integer`

Number of offers to return. Default is `10`. Maximum is `100`.

**skip** `integer`

Number of offers to skip. Default is `0`.

### Response

The sample shows only the key fields of each offer. The API returns every [offer field](#offer-object).

```json theme={null}
{
  "matched": {
    "entity": "collection",
    "count": 2,
    "items": [
      {
        "entity": "offer",
        "id": "offer_MULTISKU_001",
        "display_name": "10% Off on Apple Devices",
        "status": "ACTIVE",
        "benefits_types": ["instant_discount"],
        "eligible": true,
        "rules": {
          "entity": "collection",
          "count": 1,
          "items": [
            {
              "criteria": {
                "includes": {
                  "payment_instrument": {
                    "methods": ["card"],
                    "card": {
                      "issuers": ["HDFC"],
                      "types": ["CREDIT", "DEBIT"]
                    }
                  },
                  "order": {
                    "applies_to": "line_items",
                    "min_amount": 3000000,
                    "line_item": {
                      "skus": {
                        "type": "list",
                        "values": ["IPHONE16_128", "IPHONE16_256", "IPAD_AIR_M2"]
                      },
                      "brands": ["apple"],
                      "min_quantity": 1,
                      "min_price": 3000000
                    }
                  }
                },
                "excludes": {}
              },
              "benefits": {
                "entity": "collection",
                "count": 1,
                "items": [
                  {
                    "type": "instant_discount",
                    "applicable_on": "line_item",
                    "value": 10,
                    "max_benefit_value": 150000,
                    "limit_type": "UPTO",
                    "unit": "PERCENTAGE",
                    "calculated_benefit_value": 150000,
                    "benefit_breakup": [
                      {
                        "sku": "IPHONE16_128",
                        "brand": "apple",
                        "eligible_quantity": 1,
                        "calculated_benefit_value": 150000
                      }
                    ]
                  }
                ]
              }
            }
          ]
        }
      },
      {
        "entity": "offer",
        "id": "offer_CART_002",
        "display_name": "₹2,000 Off with HDFC Bank Credit Cards",
        "status": "ACTIVE",
        "benefits_types": ["instant_discount"],
        "eligible": true,
        "rules": {
          "entity": "collection",
          "count": 1,
          "items": [
            {
              "criteria": {
                "includes": {
                  "payment_instrument": {
                    "methods": ["card"],
                    "card": {
                      "issuers": ["HDFC"],
                      "types": ["CREDIT"]
                    }
                  },
                  "order": {
                    "applies_to": "cart",
                    "min_amount": 10000000
                  }
                },
                "excludes": {}
              },
              "benefits": {
                "entity": "collection",
                "count": 1,
                "items": [
                  {
                    "type": "instant_discount",
                    "applicable_on": "cart",
                    "value": 200000,
                    "max_benefit_value": 200000,
                    "limit_type": "FLAT",
                    "unit": "FIXED",
                    "calculated_benefit_value": 200000
                  }
                ]
              }
            }
          ]
        }
      }
    ]
  },
  "ineligible": {
    "entity": "collection",
    "count": 1,
    "items": [
      {
        "entity": "offer",
        "id": "offer_MULTISKU_002",
        "display_name": "5% Off on OnePlus Phones",
        "status": "ACTIVE",
        "benefits_types": ["instant_discount"],
        "eligible": false,
        "rules": {
          "entity": "collection",
          "count": 1,
          "items": [
            {
              "criteria": {
                "includes": {
                  "payment_instrument": {
                    "methods": ["card"],
                    "card": {
                      "issuers": ["HDFC"],
                      "types": ["CREDIT"]
                    }
                  },
                  "order": {
                    "applies_to": "line_items",
                    "min_amount": 2000000,
                    "line_item": {
                      "skus": {
                        "type": "list",
                        "values": ["ONEPLUS_13_256", "ONEPLUS_13_512"]
                      },
                      "brands": ["oneplus"],
                      "min_quantity": 1,
                      "min_price": 2000000
                    }
                  }
                },
                "excludes": {}
              },
              "benefits": {
                "entity": "collection",
                "count": 1,
                "items": [
                  {
                    "type": "instant_discount",
                    "applicable_on": "line_item",
                    "value": 5,
                    "max_benefit_value": 100000,
                    "limit_type": "UPTO",
                    "unit": "PERCENTAGE"
                  }
                ]
              }
            }
          ]
        }
      }
    ]
  }
}
```

### Response Parameters

**matched** `object`

Offers that match the cart and payment instrument: `entity` (always `collection`), `count` and `items`. Each item has every [offer field](#offer-object) and `eligible`, which is always `true`. The benefits in each item include the calculated fields below.

**matched.items\[].rules.items\[].benefits.items\[].calculated\_benefit\_value** `integer`

Total discount from this benefit in paise. Use this value. Do not add up `benefit_breakup` yourself.

**matched.items\[].rules.items\[].benefits.items\[].benefit\_breakup** `array`

Discount on each SKU. Present only for SKU-level offers when you pass `criteria.order.line_items`.

* `sku`: SKU identifier from the request.
* `brand`: Brand from the request.
* `eligible_quantity`: Units eligible for the offer. It can be lower than the cart quantity if a per-customer limit applies.
* `calculated_benefit_value`: Discount in paise for the eligible units of this SKU.

**ineligible** `object`

Offers that do not apply to this order: `entity` (always `collection`), `count` and `items`. An offer is ineligible when, for example, no SKU in the cart matches it, the payment instrument does not meet its conditions or the order amount is below its minimum. Present only when you pass `ineligible.include` as `true`. Each item has every [offer field](#offer-object) and `eligible` as `false`. `benefit_breakup` is empty for these offers.

## Errors

| API | HTTP status | Scenario | `reason` | `field` |
| - | - | - | - | - |
| Fetch Offers | 400 | `status` is not a supported value. | `input_validation_failed` | `status` |
| Fetch Offers | 400 | `ends_at` is before `starts_at`. | `input_validation_failed` | `ends_at` |
| Fetch Offers | 400 | `count` is more than 100. | `input_validation_failed` | `count` |
| Match Offers | 400 | `criteria.offers` has more than 20 entries. | `input_validation_failed` | `criteria.offers` |
| Match Offers | 400 | A line item `quantity` is less than 1. | `input_validation_failed` | `criteria.order.line_items[n].quantity` |
| Match Offers | 429 | Rate limit exceeded. | `rate_limit_exceeded` | — |
| Both | 401 | The API key is invalid or missing. | `authentication_failed` | — |

### Related Information

* [About Offers](https://razorpay.com/docs/payments/offers)
* [Create Offers](https://razorpay.com/docs/payments/offers/create.md)
* [Integrate Offers with Standard Checkout](https://razorpay.com/docs/payments/offers/standard-integration)
* [SKU and Brand Offers on Standard Checkout](https://razorpay.com/docs/payments/offers/sku-offers.md)
