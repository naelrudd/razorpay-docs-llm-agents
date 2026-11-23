> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integrate With Route

> Step-by-step guide on how to integrate Razorpay Curlec Route.

Available in
🇮🇳 India
🇲🇾 Malaysia

Razorpay Curlec Route can split payments between third parties, sellers or bank accounts.

## Prerequisites

<ul>
  <li>Create a Razorpay Curlec account.</li>
  <li>Log in to the Dashboard and [generate the API keys](https://razorpay.com/docs/my/api/authentication.md#generate-api-keys). You need to use these keys while using our APIs and Checkout.</li>
  <li>Add Linked Accounts by contacting the [Support team](https://curlec.com/support/).</li>
</ul>

## Integration Steps

Follow these steps to integrate Razorpay Curlec Route:

> [card] [1. Build Integration](https://razorpay.com/docs/my/payments/route/integration-guide.md#1-build-integration)
>
> Integrate Route.

> [card] [2. Test Integration](https://razorpay.com/docs/my/payments/route/integration-guide.md#2-test-integration)
>
> Test the integration by making a test payment.

> [card] [3. Go-live Checklist](https://razorpay.com/docs/my/payments/subscriptions/integration-guide.md#3-follow-go-live-checklist)
>
> Check the go-live checklist.

## 1. Build Integration

Follow these steps to create Linked Accounts and transfer funds to them.

> [accordion] Step 1.1.1 Create Linked Accounts
>
> To transfer funds to various third parties, sellers, bank accounts or vendors, you should add them as Linked Accounts. When you add a Linked Account, you gain complete visibility and control of all the fund movements, such as transfers, reversals and refunds for each of your Linked Accounts.
>
> You should contact [Support team](https://curlec.com/support/) to create Linked Accounts.

> [accordion] Step 1.2 Transfer Funds to Linked Accounts
>
> After you create Linked Accounts, you can start transferring funds to them. You can transfer funds using the following methods:
>
> * [Orders](https://razorpay.com/docs/my/payments/route/transfer-funds-to-linked-accounts.md#transfer-funds-to-linked-account-via-orders): You can set up transfers at the time of order creation. The transfer is automatically created and settled to the respective Linked Accounts after the payment is captured and the order is paid.
>
> * [Payments](https://razorpay.com/docs/my/payments/route/transfer-funds-to-linked-accounts.md#transfers-funds-to-linked-accounts-via-payments): You can initiate a transfer from the received payments.
>
> * [Direct Transfer](https://razorpay.com/docs/my/payments/route/transfer-funds-to-linked-accounts.md#transfer-funds-to-linked-accounts-via-direct-transfers): You can transfer funds to Linked Accounts directly from your account balance using Direct Transfers.
>
> > [!NOTE]
> >
> > **Requirements to Initiate a Transfer**
> >
> > * Maintain sufficient funds to successfully process the transfer to the Linked Account.
> > * You can only transfer the `captured` payments.
> > * You can create more than one transfer on a `payment_id`. However, the total transfer amount (payment amount + fee) should not exceed the captured payment amount.
> > * You cannot request a transfer on payment once a refund has been initiated.

## 2. Test Integration

After completing the integration, you can simulate a test transfer in the test mode using the [Transfer via Payment](https://razorpay.com/docs/my/payments/route/transfer-funds-to-linked-accounts.md#transfers-funds-to-linked-accounts-via-payments) or [Direct Transfer](https://razorpay.com/docs/my/payments/route/transfer-funds-to-linked-accounts.md#transfer-funds-to-linked-accounts-via-direct-transfers) methods from the Dashboard.

> [!WARNING]
>
> **Watch Out!**
>
> Transfers via orders can only be done using [APIs](https://razorpay.com/docs/my/api/payments/route/create-transfers-orders.md).

## 3. Go-live Checklist

Consider the following steps before taking your integration live.

> [accordion] 1 Switch Test API Keys With Live API Keys
>
> * After confirming your integration is working successfully, you can take the integration live by switching the Test Mode API Keys with the Live Mode Keys.
>
> * You can create live Transfers to Linked Accounts created in the Test Mode.

> [accordion] 2 Subscribe to Webhooks
>
> [Set up Webhooks](https://razorpay.com/docs/my/webhooks/setup-edit-payments.md) to configure and receive notifications when a specific event occurs. When one of these events is triggered, we send an HTTP POST payload in JSON to the webhook's configured URL. You can subscribe to these [Route webhook events](https://razorpay.com/docs/my/webhooks/route.md).

## Appendix

This section provides information about business type, category, sub-category, KYC requirements and their possible values.

> [accordion] Business Type
>
> The following table lists the supported Business Types:
>
> | Values |
> | - |
> | <ul><li>`llp`</li> <li>`ngo`</li> <li>`other`</li> <li>`individual`</li> <li>`partnership`</li> <li>`proprietorship`</li> <li>`public_limited`</li> <li>`private_limited`</li> <li>`trust`, `society`</li> <li>`not_yet_registered`</li> <li>`educational_institutes`</li></ul> |

> [accordion] Business Category
>
> The following table lists the possible values for Business Category:
>
> | Values |
> | - |
> | `financial_services`; `education`; `healthcare`; `utilities`; `government`; `logistics`; `tours_and_travel`; `transport`; `ecommerce`; `food`; `it_and_software`; `gaming`; `media_and_entertainment`; `services`; `housing`; `not_for_profit`; `social`; `others` |

> [accordion] Business Sub-Category
>
> The following table lists the possible values for Business Sub-Category:
>
> | Attribute | Values |
> | - | - |
> | FINANCIAL\_SERVICES | mutual\_fund, lending, cryptocurrency, insurance, nbfc, cooperatives, pension\_fund, forex, securities, commodities, accounting, financial\_advisor, crowdfunding, trading, betting, get\_rich\_schemes, moneysend\_funding, wire\_transfers\_and\_money\_orders, tax\_preparation\_services, tax\_payments, digital\_goods, atms |
> | EDUCATION | college, schools, university, professional\_courses, distance\_learning, day\_care, coaching, elearning, vocational\_and\_trade\_schools, sporting\_clubs, dance\_halls\_studios\_and\_schools, correspondence\_schools |
> | HEALTHCARE | pharmacy, clinic, hospital, lab, dietician, fitness, health\_coaching, health\_products, drug\_stores, healthcare\_marketplace, osteopaths, medical\_equipment\_and\_supply\_stores, podiatrists\_and\_chiropodists, dentists\_and\_orthodontists, hardware\_stores, ophthalmologists, orthopedic\_goods\_stores, testing\_laboratories, doctors, health\_practitioners\_medical\_services, testing\_laboratories |
> | ECOMMERCE | ecommerce\_marketplace, agriculture, books, electronics\_and\_furniture, coupons, rental, fashion\_and\_lifestyle, gifting, grocery, baby\_products, office\_supplies, wholesale, religious\_products, pet\_products, sports\_products, arts\_and\_collectibles, sexual\_wellness\_products, drop\_shipping, crypto\_machinery, tobacco, weapons\_and\_ammunitions, stamps\_and\_coins\_stores, office\_equipment, automobile\_parts\_and\_equipements, garden\_supply\_stores, household\_appliance\_stores, non\_durable\_goods, pawn\_shops, electrical\_parts\_and\_equipment, wig\_and\_toupee\_shops, gift\_novelty\_and\_souvenir\_shops, duty\_free\_stores, office\_and\_commercial\_furniture, dry\_goods, books\_and\_publications, camera\_and\_photographic\_stores, record\_shops, meat\_supply\_stores, leather\_goods\_and\_luggage, snowmobile\_dealers, men\_and\_boys\_clothing\_stores, paint\_supply\_stores, automotive\_parts, jewellery\_and\_watch\_stores, auto\_store\_home\_supply\_stores, tent\_stores, shoe\_stores\_retail,petroleum\_and\_petroleum\_products, department\_stores, automotive\_tire\_stores, sport\_apparel\_stores, variety\_stores, chemicals\_and\_allied\_products, commercial\_equipments,fireplace\_parts\_and\_accessories, family\_clothing\_stores, fabric\_and\_sewing\_stores, home\_supply\_warehouse, art\_supply\_stores, camper\_recreational\_and\_utility\_trailer\_dealers, clocks\_and\_silverware\_stores, discount\_stores,school\_supplies\_and\_stationery, second\_hand\_stores, watch\_and\_jewellery\_repair\_stores, liquor\_stores, boat\_dealers, opticians\_optical\_goods\_and\_eyeglasse\_stores, wholesale\_footwear\_stores, cosmetic\_stores, home\_furnishing\_stores, antique\_stores, plumbing\_and\_heating\_equipment, telecommunication\_equipment\_stores, women\_clothing, florists, computer\_software\_stores, building\_matrial\_stores, candy\_nut\_confectionery\_shops, glass\_and\_wallpaper\_stores,commercial\_photography\_and\_graphic\_design\_services, video\_game\_supply\_stores, fuel\_dealers,drapery\_and\_window\_coverings\_stores, hearing\_aids\_stores, automotive\_paint\_shops, durable\_goods\_stores,uniforms\_and\_commercial\_clothing\_stores, fur\_shops, industrial\_supplies, bicycle\_stores, second\_hand\_stores, motorcycle\_shops\_and\_dealers, children\_and\_infants\_wear\_stores, women\_accessory\_stores, construction\_materials, books\_periodicals\_and\_newspaper, floor\_covering\_stores, crystal\_and\_glassware\_stores, accessory\_and\_apparel\_stores,hardware\_equipment\_and\_supply\_stores, computers\_peripheral\_equipment\_software, automobile\_and\_truck\_dealers, aircraft\_and\_farm\_equipment\_dealers, antique\_shops\_sales\_and\_repairs, hearing\_aids\_stores, music\_stores, furniture\_and\_home\_furnishing\_store |
> | SERVICES | repair\_and\_cleaning, interior\_design\_and\_architect, movers\_and\_packers, legal, event\_planning, service\_centre, consulting, ad\_and\_marketing, services\_classifieds, multi\_level\_marketing, construction\_services, architectural\_services, car\_washes, motor\_home\_rentals, stenographic\_and\_secretarial\_support\_services, chiropractors, automotive\_service\_shops, shoe\_repair\_shops, telecommunication\_service, fines, security\_agencies, tailors,type\_setting\_and\_engraving\_services, small\_appliance\_repair\_shops, photography\_labs, dry\_cleaners, massage\_parlors,electronic\_repair\_shops, cleaning\_and\_sanitation\_services, nursing\_care\_facilities, direct\_marketing, lottery,veterinary\_services, affliated\_auto\_rental, alimony\_and\_child\_support, airport\_flying\_fields, golf\_courses, tire\_retreading\_and\_repair\_shops, television\_cable\_services, recreational\_and\_sporting\_camps, barber\_and\_beauty\_shops, agricultural\_cooperatives, carpentry\_contractors, wrecking\_and\_salvaging\_services, automobile\_towing\_services, video\_tape\_rental\_stores, miscellaneous\_repair\_shops, motor\_homes\_and\_parts, horse\_or\_dog\_racing, laundry\_services,electrical\_contractors, debt\_marriage\_personal\_counseling\_service, air\_conditioning\_and\_refrigeration\_repair\_shops, credit\_reporting\_agencies, heating\_and\_plumbing\_contractors, carpet\_and\_upholstery\_cleaning\_services, swimming\_pools, roofing\_and\_metal\_work\_contractors, internet\_service\_providers, recreational\_camps, masonry\_contractors, exterminating\_and\_disinfecting\_services, ambulance\_services, funeral\_services\_and\_crematories, metal\_service\_centres, copying\_and\_blueprinting\_services, fuel\_dispensers, welding\_repair, mobile\_home\_dealers, concrete\_work\_contractors, boat\_rentals, personal\_shoppers\_and\_shopping\_clubs, door\_to\_door\_sales, travel\_related\_direct\_marketing, lottery\_and\_betting, bands\_orchestras\_and\_miscellaneous\_entertainers, furniture\_repair\_and\_refinishing, contractors, direct\_marketing\_and\_subscription\_merchants, typewriter\_stores\_sales\_service\_and\_rentals, recreation\_services, direct\_marketing\_insurance\_services, business\_services, inbound\_telemarketing\_merchants, public\_warehousing, outbound\_telemarketing\_merchants, clothing\_rental\_stores, transportation\_services, electric\_razor\_stores, service\_stations, photographic\_studio, professional\_services |
> | HOUSING | developer, facility\_management, rwa, coworking, realestate\_classifieds, space\_rental |
> | NOT\_FOR\_PROFIT | charity, educational, religious, personal |
> | SOCIAL | matchmaking, social\_network, messaging, professional\_network, neighbourhood\_network, political\_organizations, automobile\_associations\_and\_clubs, country\_and\_athletic\_clubs, associations\_and\_membership |
> | MEDIA\_AND\_ENTERTAINMENT | video\_on\_demand, music\_streaming, multiplex, content\_and\_publishing, ticketing, news, video\_game\_arcades, video\_tape\_production\_and\_distribution, bowling\_alleys, billiard\_and\_pool\_establishments, amusement\_parks\_and\_circuses, ticket\_agencies |
> | GAMING | game\_developer, esports, online\_casino, fantasy\_sports, gaming\_marketplace |
> | IT\_AND\_SOFTWARE | saas, paas, iaas, consulting\_and\_outsourcing, web\_development, technical\_support, data\_processing |
> | FOOD | online\_food\_ordering, restaurant, food\_court, catering, alcohol, restaurant\_search\_and\_booking, dairy\_products, bakeries |
> | UTILITIES | electricity, gas, telecom, water, cable, broadband, dth, internet\_provider, bill\_and\_recharge\_aggregators |
> | GOVERNMENT | central, state, intra\_government\_purchases, goverment\_postal\_services |
> | LOGISTICS | freight, courier, warehousing, distribution, end\_to\_end\_logistics, courier\_services |
> | TOURS\_AND\_TRAVEL | aviation, accommodation, ota, travel\_agency, tourist\_attractions\_and\_exhibits, timeshares, aquariums\_dolphinariums\_and\_seaquariums |
> | TRANSPORT | cab\_hailing, bus, train\_and\_metro, automobile\_rentals, cruise\_lines, parking\_lots\_and\_garages, transportation, bridge\_and\_road\_tolls, freight\_transport, truck\_and\_utility\_trailer\_rentals |

> [accordion] Supported Banks
>
> The following table lists the supported banks and their codes:
>
> | Bank Name | Bank Codes |
> | - | - |
> | Affin Bank | PHBMMYKL |
> | Affin Islamic Bank | AFFIN\_ISLAMIC\_BANK |
> | Agrobank | AGOBMYKL |
> | Alliance Bank | MFBBMYKL |
> | Alliance Islamic Bank | ALLIANCE\_ISLAMIC\_BANK |
> | Al-Rajhi Banking & Inv.Corp. (M) Bhd | RJHIMYKL |
> | AmBank Berhad | ARBKMYKL |
> | AmIslamic Bank | AMISLAMIC\_BANK |
> | Bangkok Bank Berhad | BKKBMYKL |
> | Bank Islam Malaysia Berhad | BIMBMYKL |
> | Bank Muamalat Malaysia Berhad | BMMBMYKL |
> | Bank of America | BOFAMY2X |
> | Bank of China | BKCHMYKL |
> | Bank Rakyat | BKRMMYKL |
> | Bank Simpanan Nasional | BSNAMYK1 |
> | BNP Paribas | BNPAMYKL |
> | China Construction Bank | PCBCMYKL |
> | CIMB Bank | CIBBMYKL |
> | CIMB Islamic Bank | CIMB\_ISLAMIC\_BANK |
> | Citibank | CITIMYKL |
> | Deutsche Bank | DEUTMYKL |
> | Hong Leong Bank | HLBBMYKL |
> | Hong Leong Islamic Bank | HONG\_LEONG\_ISLAMIC\_BANK |
> | HSBC Amanah | HBMBMYKL |
> | HSBC Bank | HSBC\_BANK |
> | Industrial & Commercial Bank of China | ICBKMYKL |
> | JP Morgan Chase Bank | CHASMYKX |
> | Kuwait Finance House | KFHOMYKL |
> | Malayan Banking Berhad | MBBEMYKL |
> | Maybank Islamic Bank | MAYBANK\_ISLAMIC |
> | MBSB Bank Malaysia Berhad | AFBQMYKL |
> | Mizuho Bank (M) Berhad | MHCBMYKA |
> | MUFG Bank (Malaysia) BHD | BOTKMYKX |
> | OCBC Al-Amin Bank Berhad | OCBCMYKL |
> | OCBC Bank | OCBC\_BANK |
> | Public Bank | PBBEMYKL |
> | Public Islamic Bank Berhad | PUBLIC\_ISLAMIC\_BANK |
> | RHB Bank | RHBBMYKL |
> | RHB Islamic Bank | RHB\_ISLAMIC\_BANK |
> | Standard Chartered Bank Berhad | SCBLMYKX |
> | Standard Chartered Saadiq Bank Berhad | STANDARD\_CHARTERED\_SAADIQ\_BANK |
> | Sumitomo Mitsui Bank | SMBCMYKL |
> | United Overseas Bank | UOVBMYKL |
> | TNG Digital | TNGDMYNB |

### Related Information

* [Route API](https://razorpay.com/docs/my/api/payments/route.md)
* [Route Webhooks](https://razorpay.com/docs/my/payments/route/subscribe-to-webhooks.md)
