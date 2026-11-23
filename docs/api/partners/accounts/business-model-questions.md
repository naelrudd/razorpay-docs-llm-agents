> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Business Model Questions

> Know about the business model questions for each subcategory and their answer options.

Available in
🇮🇳 India

Razorpay asks business model questions for some business subcategories. They help Razorpay understand how the business sells and delivers. The account lists them as inputs of the `business_model_clarifications` requirement. Each input's `requirement_code` is the question ID. Know more about [requirements](https://razorpay.com/docs/api/partners/accounts/requirement-entity.md).

Use this page to ask the questions in your own onboarding flow. To answer them before Razorpay lists them, send the answers in [Create an Account](https://razorpay.com/docs/api/partners/accounts/create.md).

## How Razorpay Picks the Questions

The business subcategory decides the first questions. Know more about [business categories and subcategories](https://razorpay.com/docs/api/partners/accounts/business-categories.md). A subcategory not listed in [Questions by Subcategory](#questions-by-subcategory) has no questions.

Two things can change the first questions:

* **Business type:** Some subcategories ask an `individual` different questions from other business types.
* **Payment channels:** Some subcategories ask different questions when the account has only a website. An account with an Android or iOS app gets the other set. So does an account with no website.

Some answers lead to a follow-up question. Each question below lists its follow-ups under the option that leads to them. Answer every follow-up the requirements list. In total, 25 first questions lead to 14 follow-up questions.

## How to Answer

Send each answer at `business_profile.business_category.business_model_clarifications.<question_id>`, with the `question_id` and the `answer`. `answer` is an array:

* **`single_select`:** One option `value`.
* **`multi_select`:** One or more option `value`s.
* **`free_text`:** One string.

Send the option `value`, not its `label`. Show the `label` to the sub-merchant. In the requirement, a `single_select` question has the `value_type` `enum`. A `free_text` question has the `value_type` `text`.

```bash Update an Account theme={null}
curl -X PATCH https://api.razorpay.com/v1/accounts/acc_TcdGEzmfKQzEl1 \
-u rzp_test_partner_[CLIENT_ID]:[CLIENT_SECRET] \
-H "Content-Type: application/json" \
-d '{
  "business_profile": {
    "business_category": {
      "business_model_clarifications": {
        "bmc_question_9": {
          "question_id": "bmc_question_9",
          "answer": ["bmc_question_9_option_1"]
        }
      }
    }
  }
}'
```

Razorpay merges the answers by question ID, so send them in one update or several. Some answers ask for a supporting document, such as a Food Safety and Standards Authority of India (FSSAI) certificate. The account then lists it in the `business_documents` requirement.

## Questions by Subcategory

The table below lists the first questions for each subcategory:

| Subcategory | Questions |
| - | - |
| `accessory_and_apparel_stores` | [`bmc_question_2`](#question-2) |
| `agriculture` | [`bmc_question_19`](#question-19), [`bmc_question_2`](#question-2) |
| `aircraft_and_farm_equipment_dealers` | [`bmc_question_22`](#question-22), [`bmc_question_2`](#question-2) |
| `alcohol` | [`bmc_question_12`](#question-12) |
| `automobile_parts_and_equipements` | [`bmc_question_2`](#question-2) |
| `automotive_parts` | [`bmc_question_2`](#question-2) |
| `automotive_tire_stores` | [`bmc_question_2`](#question-2) |
| `aviation` | [`bmc_question_13`](#question-13) |
| `baby_products` | [`bmc_question_2`](#question-2) |
| `bicycle_stores` | [`bmc_question_2`](#question-2) |
| `books_periodicals_and_newspaper` | [`bmc_question_2`](#question-2) |
| `building_matrial_stores` | [`bmc_question_2`](#question-2) |
| `camera_and_photographic_stores` | [`bmc_question_2`](#question-2) |
| `children_and_infants_wear_stores` | [`bmc_question_2`](#question-2) |
| `clocks_and_silverware_stores` | [`bmc_question_2`](#question-2) |
| `clothing_rental_stores` | [`bmc_question_2`](#question-2) |
| `coaching` | [`bmc_question_6`](#question-6) |
| `commercial_equipments` | [`bmc_question_2`](#question-2) |
| `commercial_photography_and_graphic_design_services` | [`bmc_question_3`](#question-3) |
| `construction_materials` | [`bmc_question_2`](#question-2) |
| `consulting_and_outsourcing` | Only a website: None An app or no website: [`bmc_question_15`](#question-15) |
| `cosmetic_stores` | [`bmc_question_2`](#question-2) |
| `cryptocurrency` | [`bmc_question_24`](#question-24) |
| `data_processing` | [`bmc_question_33`](#question-33) |
| `department_stores` | [`bmc_question_2`](#question-2) |
| `dietician` | [`bmc_question_31`](#question-31) |
| `discount_stores` | [`bmc_question_2`](#question-2) |
| `distance_learning` | [`bmc_question_6`](#question-6) |
| `drop_shipping` | [`bmc_question_2`](#question-2) |
| `dry_goods` | [`bmc_question_2`](#question-2) |
| `durable_goods_stores` | [`bmc_question_2`](#question-2) |
| `duty_free_stores` | [`bmc_question_2`](#question-2) |
| `ecommerce_marketplace` | [`bmc_question_2`](#question-2) |
| `elearning` | [`bmc_question_6`](#question-6) |
| `electric_razor_stores` | [`bmc_question_2`](#question-2) |
| `electrical_parts_and_equipment` | [`bmc_question_2`](#question-2) |
| `event_planning` | Only a website: None An app or no website: [`bmc_question_14`](#question-14) |
| `family_clothing_stores` | [`bmc_question_2`](#question-2) |
| `fashion_and_lifestyle` | [`bmc_question_2`](#question-2) |
| `fireplace_parts_and_accessories` | [`bmc_question_2`](#question-2) |
| `fitness` | [`bmc_question_31`](#question-31) |
| `furniture_and_home_furnishing_store` | [`bmc_question_2`](#question-2) |
| `garden_supply_stores` | [`bmc_question_2`](#question-2) |
| `glass_and_wallpaper_stores` | [`bmc_question_2`](#question-2) |
| `hardware_equipment_and_supply_stores` | [`bmc_question_2`](#question-2) |
| `hardware_stores` | [`bmc_question_21`](#question-21), [`bmc_question_2`](#question-2) |
| `health_products` | [`bmc_question_32`](#question-32) |
| `healthcare_marketplace` | [`bmc_question_2`](#question-2) |
| `home_furnishing_stores` | [`bmc_question_2`](#question-2) |
| `home_supply_warehouse` | [`bmc_question_2`](#question-2) |
| `hospital` | [`bmc_question_37`](#question-37) |
| `industrial_supplies` | [`bmc_question_2`](#question-2) |
| `jewellery_and_watch_stores` | [`bmc_question_10`](#question-10) |
| `medical_equipment_and_supply_stores` | [`bmc_question_21`](#question-21), [`bmc_question_2`](#question-2) |
| `men_and_boys_clothing_stores` | [`bmc_question_2`](#question-2) |
| `metal_service_centres` | [`bmc_question_2`](#question-2) |
| `miscellaneous_repair_shops` | Only a website: [`bmc_question_26`](#question-26) An app or no website: None |
| `mobile_home_dealers` | [`bmc_question_2`](#question-2) |
| `moneysend_funding` | [`bmc_question_2`](#question-2) |
| `music_streaming` | `individual`: [`bmc_question_30`](#question-30) Other business types: [`bmc_question_20`](#question-20) |
| `office_supplies` | [`bmc_question_2`](#question-2) |
| `opticians_optical_goods_and_eyeglasse_stores` | [`bmc_question_2`](#question-2) |
| `orthopedic_goods_stores` | [`bmc_question_21`](#question-21), [`bmc_question_2`](#question-2) |
| `ota` | [`bmc_question_9`](#question-9) |
| `plumbing_and_heating_equipment` | [`bmc_question_2`](#question-2) |
| `professional_courses` | [`bmc_question_6`](#question-6) |
| `professional_services` | [`bmc_question_17`](#question-17) |
| `record_shops` | [`bmc_question_35`](#question-35) |
| `repair_and_cleaning` | Only a website: None An app or no website: [`bmc_question_16`](#question-16), [`bmc_question_25`](#question-25) |
| `school_supplies_and_stationery` | [`bmc_question_2`](#question-2) |
| `second_hand_stores` | [`bmc_question_18`](#question-18), [`bmc_question_2`](#question-2) |
| `shoe_stores_retail` | [`bmc_question_2`](#question-2) |
| `snowmobile_dealers` | [`bmc_question_2`](#question-2) |
| `stationery_supplies` | [`bmc_question_2`](#question-2) |
| `swimming_pools` | [`bmc_question_2`](#question-2) |
| `tech_consulting_and_outsourcing` | Only a website: None An app or no website: [`bmc_question_15`](#question-15) |
| `telecommunication_equipment_stores` | [`bmc_question_2`](#question-2) |
| `tent_stores` | [`bmc_question_2`](#question-2) |
| `tourist_attractions_and_exhibits` | [`bmc_question_9`](#question-9) |
| `train_and_metro` | [`bmc_question_9`](#question-9) |
| `transportation` | [`bmc_question_9`](#question-9) |
| `travel_agency` | [`bmc_question_9`](#question-9) |
| `typewriter_stores_sales_service_and_rentals` | [`bmc_question_2`](#question-2) |
| `used_automobile_and_truck_dealers` | [`bmc_question_18`](#question-18), [`bmc_question_2`](#question-2) |
| `variety_stores` | [`bmc_question_2`](#question-2) |
| `video_game_supply_stores` | [`bmc_question_2`](#question-2) |
| `video_on_demand` | `individual`: [`bmc_question_30`](#question-30) Other business types: [`bmc_question_20`](#question-20) |
| `video_tape_production_and_distribution` | `individual`: [`bmc_question_30`](#question-30) Other business types: [`bmc_question_20`](#question-20) |
| `wholesale` | [`bmc_question_2`](#question-2) |
| `wholesale_footwear_stores` | [`bmc_question_2`](#question-2) |
| `women_accessory_stores` | [`bmc_question_2`](#question-2) |
| `women_clothing` | [`bmc_question_2`](#question-2) |

## Questions

Each question lists its ID and text, its input type and its options. The `label` and the question text are shown as Razorpay returns them.

### Question 2

`bmc_question_2`: What is your average delivery time after receiving an order?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_2_option_1` | 0-7 days |
| `bmc_question_2_option_2` | 8-14 days |
| `bmc_question_2_option_3` | 15-21 days |
| `bmc_question_2_option_4` | 22-35 days |
| `bmc_question_2_option_5` | 35+ days |
| `bmc_question_2_option_6` | No shipping required |

### Question 3

`bmc_question_3`: What is your business model like?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_3_option_1` | We sell physical art pieces |
| `bmc_question_3_option_2` | We sell digital art |
| `bmc_question_3_option_3` | We sell both digital and physical art pieces |
| `bmc_question_3_option_4` | My business model is not specified here |

#### Follow-up to `bmc_question_3_option_1`

When the answer includes `bmc_question_3_option_1`, also answer:

`bmc_question_3_1_1`: Do you procure any art or collectibles from third-party vendors?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_3_1_1_option_1` | We procure from third-party vendors |
| `bmc_question_3_1_1_option_2` | No, we don't procure from third-party vendors |

#### Follow-up to `bmc_question_3_option_2`

When the answer includes `bmc_question_3_option_2`, also answer:

`bmc_question_3_2_1`: Do you procure any art or collectibles from third-party vendors?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_3_2_1_option_1` | We procure from third-party vendors |
| `bmc_question_3_2_1_option_2` | No, we don't procure from third-party vendors |

#### Follow-up to `bmc_question_3_option_3`

When the answer includes `bmc_question_3_option_3`, also answer:

`bmc_question_3_3_1`: Do you procure any art or collectibles from third-party vendors?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_3_3_1_option_1` | We procure from third-party vendors |
| `bmc_question_3_3_1_option_2` | No, we don't procure from third-party vendors |

#### Follow-up to `bmc_question_3_option_4`

When the answer includes `bmc_question_3_option_4`, also answer:

`bmc_question_3_4_1`: Add a brief description of your business model

Input type: `free_text`.

Send one non-empty string in `answer`.

### Question 6

`bmc_question_6`: What is your business model like?

Input type: `multi_select`.

| `value` | `label` |
| - | - |
| `bmc_question_6_option_1` | We provide education services on a third-party Edtech platform |
| `bmc_question_6_option_2` | We provide recorded sessions that students can access anytime |
| `bmc_question_6_option_3` | We sell physical course material |
| `bmc_question_6_option_4` | We provide offline coaching classes in physical settings |
| `bmc_question_6_option_5` | My business model is not specified here |

#### Follow-up to `bmc_question_6_option_5`

When the answer includes `bmc_question_6_option_5`, also answer:

`bmc_question_6_5_1`: Add a brief description of your business model

Input type: `free_text`.

Send one non-empty string in `answer`.

### Question 9

`bmc_question_9`: What type of ticket booking services does your business provide?

Input type: `multi_select`.

| `value` | `label` |
| - | - |
| `bmc_question_9_option_1` | International flight tickets |
| `bmc_question_9_option_2` | Domestic flight tickets |
| `bmc_question_9_option_3` | Train tickets |
| `bmc_question_9_option_4` | Bus tickets |
| `bmc_question_9_option_5` | None of the above |

### Question 10

`bmc_question_10`: Select all products that you sell.

Input type: `multi_select`.

| `value` | `label` |
| - | - |
| `bmc_question_10_option_1` | Silver |
| `bmc_question_10_option_2` | Gold |
| `bmc_question_10_option_3` | Diamond |
| `bmc_question_10_option_4` | Platinum |
| `bmc_question_10_option_5` | Gemstones |
| `bmc_question_10_option_6` | I am not selling any of these |

#### Follow-up to `bmc_question_10_option_1`

When the answer includes `bmc_question_10_option_1`, also answer:

`bmc_question_10_1_1`: Is the price of any silver products you sell more than ₹10,000?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_10_1_1_option_1` | Yes, I sell some products worth more than ₹10,000 |
| `bmc_question_10_1_1_option_2` | No, I don't sell any products worth more than ₹10,000 |

#### Follow-up to `bmc_question_10_option_6`

When the answer includes `bmc_question_10_option_6`, also answer:

`bmc_question_10_6_1`: What type of products do you sell? List a few examples below.

Input type: `free_text`.

Send one non-empty string in `answer`.

### Question 12

`bmc_question_12`: What is your business model like?

Input type: `multi_select`.

| `value` | `label` |
| - | - |
| `bmc_question_12_option_1` | We sell alcoholic beverages from our authorised premises |
| `bmc_question_12_option_2` | We do home-delivery of alcoholic beverages |

### Question 13

`bmc_question_13`: Is your business into ticket booking services?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_13_option_1` | Yes, we provide ticket booking |
| `bmc_question_13_option_2` | No, we don't provide ticket booking |

#### Follow-up to `bmc_question_13_option_1`

When the answer includes `bmc_question_13_option_1`, also answer:

`bmc_question_13_1_1`: What type of ticket booking services does your business provide?

Input type: `multi_select`.

| `value` | `label` |
| - | - |
| `bmc_question_13_1_1_option_1` | International flight tickets |
| `bmc_question_13_1_1_option_2` | Domestic flight tickets |
| `bmc_question_13_1_1_option_3` | Train tickets |
| `bmc_question_13_1_1_option_4` | Bus tickets |
| `bmc_question_13_1_1_option_5` | None of the above |

### Question 14

`bmc_question_14`: What type of event services do you offer? List a few examples

Input type: `free_text`.

Send one non-empty string in `answer`.

### Question 15

`bmc_question_15`: What type of consultation services do you offer? List a few examples

Input type: `free_text`.

Send one non-empty string in `answer`.

### Question 16

`bmc_question_16`: Add name of the few services you offer along with the prices

Input type: `free_text`.

Send one non-empty string in `answer`.

### Question 17

`bmc_question_17`: What type of professional services do you offer?

Input type: `free_text`.

Send one non-empty string in `answer`.

### Question 18

`bmc_question_18`: Tell us name(s) of few used or second-hand products that you sell

Input type: `free_text`.

Send one non-empty string in `answer`.

### Question 19

`bmc_question_19`: What is your business model like?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_19_option_1` | We manufacture products |
| `bmc_question_19_option_2` | We buy and maintain inventory from suppliers and resell them to customers |
| `bmc_question_19_option_3` | We don’t maintain inventory, but purchase them from suppliers only when we receive an order from a customer |
| `bmc_question_19_option_4` | My business model is not specified here |

#### Follow-up to `bmc_question_19_option_1`

When the answer includes `bmc_question_19_option_1`, also answer:

`bmc_question_19_1_1`: Do you manufacture any fertilisers?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_19_1_1_option_1` | We manufacture fertilisers |
| `bmc_question_19_1_1_option_2` | No, we don’t manufacture fertilisers |

#### Follow-up to `bmc_question_19_option_4`

When the answer includes `bmc_question_19_option_4`, also answer:

`bmc_question_19_4_1`: Explain your business in detail

Input type: `free_text`.

Send one non-empty string in `answer`.

### Question 20

`bmc_question_20`: Is your business into streaming or distribution of copyrighted movies/ music?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_20_option_1` | Yes, my business is into streaming or distribution of copyrighted movies/ music |
| `bmc_question_20_option_2` | No, my business is not into streaming or distribution of copyrighted movies/ music |

#### Follow-up to `bmc_question_20_option_1`

When the answer includes `bmc_question_20_option_1`, also answer:

`bmc_question_20_1_1`: Do you produce and own the content you stream/distribute?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_20_1_1_option_1` | Yes, we produce and own the content |
| `bmc_question_20_1_1_option_2` | No, we've tied up with third-party producers |

### Question 21

`bmc_question_21`: What is your business model like?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_21_option_1` | We manufacture products |
| `bmc_question_21_option_2` | We resell the products after procuring from our suppliers |
| `bmc_question_21_option_3` | My business model is not specified here |

#### Follow-up to `bmc_question_21_option_3`

When the answer includes `bmc_question_21_option_3`, also answer:

`bmc_question_21_3_1`: Explain your business in detail

Input type: `free_text`.

Send one non-empty string in `answer`.

### Question 22

`bmc_question_22`: Do you sell any used/second-hand products?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_22_option_1` | Yes, we sell used products |
| `bmc_question_22_option_2` | No, we don't sell used products |

#### Follow-up to `bmc_question_22_option_1`

When the answer includes `bmc_question_22_option_1`, also answer:

`bmc_question_22_1_1`: Explain your business in detail

Input type: `free_text`.

Send one non-empty string in `answer`.

### Question 24

`bmc_question_24`: Is your business involved in the trading or mining of cryptocurrency?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_24_option_1` | Yes, we are involved in the trading or mining of cryptocurrency |
| `bmc_question_24_option_2` | No, we don't provide trading or mining of cryptocurrency |

#### Follow-up to `bmc_question_24_option_2`

When the answer includes `bmc_question_24_option_2`, also answer:

`bmc_question_24_2_1`: Explain your business in detail

Input type: `free_text`.

Send one non-empty string in `answer`.

### Question 25

`bmc_question_25`: Is your business tied up with any third-party provider to offer any service?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_25_option_1` | We’ve tied up with a third-party provider to offer services |
| `bmc_question_25_option_2` | No, we’ve not tied up with a third-party provider to offer services |

### Question 26

`bmc_question_26`: Is your business tied up with any third-party provider to offer any service?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_26_option_1` | We’ve tied up with a third-party provider to offer services |
| `bmc_question_26_option_2` | No, we’ve not tied up with a third-party provider to offer services |

### Question 30

`bmc_question_30`: Is your business into streaming or distribution of copyrighted movies/ music?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_30_option_1` | Yes, my business is into streaming or distribution of copyrighted movies/ music |
| `bmc_question_30_option_2` | No, my business is not into streaming or distribution of copyrighted movies/ music |

### Question 31

`bmc_question_31`: Do you sell any nutraceutical supplements?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_31_option_1` | Yes, we sell nutraceutical supplements |
| `bmc_question_31_option_2` | No, we do not sell nutraceutical supplements |

### Question 32

`bmc_question_32`: Do you sell any supplements or medicines?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_32_option_1` | Yes, we sell nutritional supplements or medicines |
| `bmc_question_32_option_2` | No, we don't sell nutritional supplements or medicines |

### Question 33

`bmc_question_33`: Is your business involved in data entry services?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_33_option_1` | Yes, we provide data-entry services |
| `bmc_question_33_option_2` | No, we don't provide data-entry services |

### Question 35

`bmc_question_35`: Do you sell/rent out any content that is suitable only for adults (18+)?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_35_option_1` | Yes, I sell/rent out content that is suitable only for adults (18+) |
| `bmc_question_35_option_2` | No, I don't sell/rent out any such content |

### Question 37

`bmc_question_37`: What type of setup do you have?

Input type: `single_select`.

| `value` | `label` |
| - | - |
| `bmc_question_37_option_1` | It's a clinic for consulting patients without any facilities for hospitalisation or surgery |
| `bmc_question_37_option_2` | It's a hospital where consulting is provided along with facilities for hospitalisation or surgery |

## Related Information

* [Requirement Entity](https://razorpay.com/docs/api/partners/accounts/requirement-entity.md)
* [Account Entity](https://razorpay.com/docs/api/partners/accounts/entity.md)
* [Collect Requirements](https://razorpay.com/docs/partners/aggregators/onboarding-api/collect-requirements.md)
