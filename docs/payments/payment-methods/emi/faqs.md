> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Frequently Asked Questions (FAQs)

> Find answers to frequently asked questions about EMI as a payment method supported at Razorpay Checkout.

Available in
🇮🇳 India

## Common

> [accordion] If a customer chooses EMI as the payment method, do I get the full amount upfront?
>
> Yes, you receive the full amount at once and the provider/bank converts it into EMI for the customer.

> [accordion] What happens when the customer fails to pay the EMI?
>
> The loss is borne by the provider/bank. You receive the full payment upfront.

> [accordion] Can my customers avail Offers for EMI payments at Checkout?
>
> Yes, they can avail offer on debit and credit card EMIs. Know more about [creating EMI Offers](https://razorpay.com/docs/payments/offers).

## Debit Card EMI

> [accordion] How do banks perform the EMI eligibility check during the transaction flow?
>
> Eligibility is checked using the card number and registered phone number. Therefore, customers should always use the phone number registered with the bank while making a payment.

> [accordion] What is the minimum balance required in the customer's account to avail Debit Card EMI?
>
> None. Customers need not have any minimum balance in their accounts while placing the order. However, they need to ensure that their accounts have sufficient funds to pay the EMI due every month.

> [accordion] How will the customers know that they are eligible for Debit Card EMI?
>
> Customers can check their eligibility by sending the SMS
>
> `DCEMI last 4 digits of Debit Card number` to `56767`, from their registered mobile number.

> [accordion] What is the criteria to avail Debit Card EMI?
>
> To avail [Debit Card EMI](https://razorpay.com/docs/payments/payment-methods/emi/debit-card-emi.md), your customers should pass the eligibility criteria set by their banks. The minimum order amount on the Checkout should be ₹5000 (for HDFC and IndusInd debit cards).

> [accordion] Can you provide a list of the EMI plans and interest rates of different banks that support Debit card EMI?
>
> The interest rates applied by each bank for Debit Card EMIs is provided below.
>
> * The minimum transaction amount for which EMIs can be availed on debit cards can vary for each bank.
>
> * The maximum transaction amount depends upon the available pre-approved limit for the customer.
>
> > [accordion] For **HDFC Bank (HDFC)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Interest rates | Maximum Amount |
> > | - | - | - | - |
> > | 3 months | 3000 | 16% | NA |
> > | 6 months | 5000 | 16% | NA |
> > | 9 months | 5000 | 16% | NA |
> > | 12 months | 5000 | 16% | NA |
> > | 18 months | 5000 | 16% | NA |
> > | 24 months | NA | NA | NA |

> [accordion] Can the customers change the EMI plan after placing the order?
>
> No, EMI plans cannot be changed after an order is placed.

> [accordion] Do customers need to pay any down-payment to avail Debit Card EMI?
>
> No, the customers need not pay any down-payment amount to avail the Debit Card EMI option.

> [accordion] Is there a possibility to foreclose EMIs availed on Debit Cards?
>
> Yes, Debit Card EMIs can be foreclosed after clearing the first three EMIs.

> [accordion] Which are the business categories for which Debit Card EMI is not allowed?
>
> The Debit Card EMI payment method is not allowed for certain business categories. Check the relevant Category section below for the list of sub-categories and support status. Debit Card EMI is not allowed for categories with **N** as the status.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Due to our partner bank restrictions, the Debit Card EMI payment methods may not be available to all the Merchant Categories and Subcategories.
>
> > [accordion] Financial Services
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | mutual\_fund | Mutual Fund | N |
> > | lending | Lending | N |
> > | cryptocurrency | Cryptocurrency | N |
> > | insurance | Insurance | Y |
> > | nbfc | NBFC | N |
> > | cooperatives | Cooperatives | Y |
> > | pension\_fund | Pension Fund | Y |
> > | forex | Forex | N |
> > | securities | Securities | N |
> > | commodities | Commodities | N |
> > | accounting | Accounting and Taxes | Y |
> > | financial\_advisor | Financial and Investment Advisors/Financial Advisor | Y |
> > | crowdfunding | Crowdfunding Platform | N |
> > | trading | Stock Brokerage and Trading | N |
> > | betting | Betting | N |
> > | get\_rich\_schemes | Get Rich Schemes | N |
> > | moneysend\_funding | MoneySend Funding | Y |
> > | wire\_transfers\_and\_money\_orders | WIRE TRANSFER MONEY ORDER | N |
> > | tax\_preparation\_services | Tax Preparation Service | Y |
> > | tax\_payments | Tax Payments | Y |
> > | digital\_goods | Digital Goods-Multi-Category | Y |
> > | atms | Financial Institutions-Automated Cash Disbursements | N |
>
> > [accordion] Education
> >
> > | college | College |
> > | - | - |
> > | schools | Schools |
> > | university | University |
> > | professional\_courses | Professional Courses |
> > | distance\_learning | Distance Learning |
> > | day\_care | Pre-School/Day Care |
> > | coaching | Coaching Institute |
> > | elearning | E-Learning |
> > | vocational\_and\_trade\_schools | SCHOOLS, TRADE AND VOCATIONAL |
> > | sporting\_clubs | ATHLETIC FEES |
> > | dance\_halls\_studios\_and\_schools | Dance Halls, Studios and Schools |
> > | correspondence\_schools | Schools, Correspondence |
>
> > [accordion] Healthcare
> >
> > | Category Code | Category Name | Status |
> > | - | - | - |
> > | pharmacy | Pharmacy | N |
> > | clinic | Clinic | Y |
> > | hospital | Hospital | Y |
> > | lab | Lab | Y |
> > | dietician | Dietician/Diet Services | Y |
> > | fitness | Gym and Fitness | Y |
> > | health\_coaching | Health and Lifestyle Coaching | Y |
> > | health\_products | Health Products | Y |
> > | healthcare\_marketplace | Marketplace/Aggregator | N |
> > | osteopaths | Osteopaths | Y |
> > | medical\_equipment\_and\_supply\_stores | Dental/Laboratory/Medical/Ophthalmic Hospital Equipment and Supplies | Y |
> > | drug\_stores | DRUGS, DRUG PROPRIETARIES | N |
> > | podiatrists\_and\_chiropodists | Podiatrists and Chiropodists | Y |
> > | dentists\_and\_orthodontists | Dentists, Orthodontists | Y |
> > | hardware\_stores | Hardware Stores | Y |
> > | ophthalmologists | Optometrists, Ophthalmologists | Y |
> > | orthopedic\_goods\_stores | Orthopedic Goods-Artificial Limb Stores | Y |
> > | health\_practitioners\_medical\_services | Health Practitioners, Medical Services-not elsewhere classified | Y |
> > | testing\_laboratories | Testing Laboratories-Non medical | Y |
> > | doctors | Doctors-not elsewhere classified | Y |
>
> > [accordion] Utilities
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | electricity | Electricity | Y |
> > | gas | Gas | Y |
> > | telecom | Telecom Service Provider | Y |
> > | water | Water | Y |
> > | cable | Cable operator | Y |
> > | broadband | Broadband | Y |
> > | dth | DTH | Y |
> > | internet\_provider | Internet service provider | Y |
> > | bill\_and\_recharge\_aggregators | Bill Payment and Recharge Aggregators | Y |
> > | central | Central Department | Y |
>
> > [accordion] Government
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | central | Central Department | Y |
> > | state | State Department | Y |
> > | intra\_government\_purchases | Intra-Government Purchases -Government Only | Y |
> > | goverment\_postal\_services | Postal Services -Government Only | Y |
>
> > [accordion] Logistics
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | freight | Freight Consolidation/Management | Y |
> > | courier | Courier Shipping | Y |
> > | warehousing | Public/Contract Warehousing | Y |
> > | distribution | Distribution Management | Y |
> > | end\_to\_end\_logistics | End-to-end logistics | Y |
> > | courier\_services | Courier Services-Air \&amp, Ground, Freight Forwarders | Y |
>
> > [accordion] Tours and Travel
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | aviation | Aviation | Y |
> > | accommodation | Lodging and Accommodation | Y |
> > | ota | OTA | Y |
> > | travel\_agency | Tours and Travel Agency | Y |
> > | tourist\_attractions\_and\_exhibits | Tourist Attractions and Exhibits | Y |
> > | aquariums\_dolphinariums\_and\_seaquariums | Aquariums, Dolphinariums, and Seaquariums | Y |
> > | timeshares | Timeshares | Y |
>
> > [accordion] Transport
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | cab\_hailing | Cab/auto hailing | Y |
> > | bus | Bus ticketing | Y |
> > | train\_and\_metro | Train and metro ticketing | Y |
> > | automobile\_rentals | National Car Rental | Y |
> > | cruise\_lines | CRUISE LINES | Y |
> > | parking\_lots\_and\_garages | Automobile Parking Lots and Garages | Y |
> > | bridge\_and\_road\_tolls | BRIDGE & ROAD FEES, TOLLS | Y |
> > | freight\_transport | Railroads and Freight | Y |
> > | truck\_and\_utility\_trailer\_rentals | Truck and Utility Trailer Rentals | Y |
> > | transportation | Transportation—Suburban and Local Commuter Passenger, including Ferries | Y |
>
> > [accordion] Ecommerce
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | ecommerce\_marketplace | Horizontal Commerce/Marketplace | N |
> > | agriculture | Agricultural products | Y |
> > | books | Books and Publications | Y |
> > | electronics\_and\_furniture | Electronics and Furniture | Y |
> > | coupons | Coupons and deals | Y |
> > | rental | Product Rental | Y |
> > | fashion\_and\_lifestyle | Fashion and Lifestyle | Y |
> > | gifting | Flowers and Gifts | Y |
> > | grocery | Grocery | Y |
> > | baby\_products | Baby Care and Toys | Y |
> > | office\_supplies | Office Supplies | Y |
> > | wholesale | Wholesale/Bulk trade | Y |
> > | religious\_products | Religious products | Y |
> > | pet\_products | Pet Care and Supplies | Y |
> > | sports\_products | Sports goods | Y |
> > | arts\_and\_collectibles | Arts, crafts and collectibles | Y |
> > | sexual\_wellness\_products | Sexual Wellness Products | Y |
> > | drop\_shipping | Dropshipping | N |
> > | crypto\_machinery | Crypto Machinery | Y |
> > | tobacco | Tobacco | Y |
> > | weapons\_and\_ammunitions | Weapons and Ammunitions | Y |
> > | stamps\_and\_coins\_stores | Stamps & Coins Stores | Y |
> > | automobile\_parts\_and\_equipements | MOTOR VEHICLE SUPPLIES | Y |
> > | office\_equipment | Office, Photographic, Photocopy, and Microfilm Equipment | Y |
> > | garden\_supply\_stores | Lawn and Garden Supply Stores | Y |
> > | household\_appliance\_stores | Household Appliance Stores | Y |
> > | non\_durable\_goods | NONDURABLE GOODS | Y |
> > | electrical\_parts\_and\_equipment | Electrical Parts and Equipment | Y |
> > | wig\_and\_toupee\_shops | Wig and Toupee Shops | Y |
> > | gift\_novelty\_and\_souvenir\_shops | Card, Gift, Novelty, and Souvenir Shops | Y |
> > | duty\_free\_stores | Duty Free Stores | Y |
> > | office\_and\_commercial\_furniture | Office and Commercial Furniture | Y |
> > | dry\_goods | Piece Goods, Notions, and Other Dry Goods | Y |
> > | books\_and\_publications | Book Stores | Y |
> > | camera\_and\_photographic\_stores | Camera and Photographic Supply Stores | Y |
> > | meat\_supply\_stores | Freezer, Locker Meat Provisioners | Y |
> > | leather\_goods\_and\_luggage | Leather Goods and Luggage Stores | Y |
> > | snowmobile\_dealers | Snowmobile Dealers | Y |
> > | men\_and\_boys\_clothing\_stores | Men’s and Boy’s Clothing and Furnishings Store | Y |
> > | paint\_supply\_stores | Varnishes, Paints, Supplies | Y |
> > | automotive\_parts | Automotive Parts, Accessories Stores | Y |
> > | jewellery\_and\_watch\_stores | Precious Stones and Metals, Watches and Jewelry | Y |
> > | auto\_store\_home\_supply\_stores | Auto Store, Home Supply Stores | Y |
> > | tent\_stores | Tent and Awning Shops | Y |
> > | petroleum\_and\_petroleum\_products | Petroleum and Petroleum Products | N |
> > | department\_stores | Department Stores | Y |
> > | shoe\_stores\_retail | Shoe Stores | Y |
> > | automotive\_tire\_stores | Automotive Tire Stores | Y |
> > | sport\_apparel\_stores | Sports Apparel, Riding Apparel Stores | Y |
> > | chemicals\_and\_allied\_products | Chemicals and Allied Products | Y |
> > | fireplace\_parts\_and\_accessories | FIREPLACE FIREPLACE SCREENS AND ACCESSORIES STORES | Y |
> > | commercial\_equipments | COMMERCIAL EQUIPMENTS | Y |
> > | family\_clothing\_stores | Family Clothing Stores | Y |
> > | fabric\_and\_sewing\_stores | Fabric, Needlework, Piece Goods, and Sewing Stores | Y |
> > | camper\_recreational\_and\_utility\_trailer\_dealers | Camper, Recreational and utility trailer dealers | Y |
> > | record\_shops | Record Shops | Y |
> > | home\_supply\_warehouse | Home Supply Warehouse | Y |
> > | clocks\_and\_silverware\_stores | Clock, Jewelry, Watch, and Silverware Store | N |
> > | art\_supply\_stores | Artist Supply Stores, Craft Shops | Y |
> > | pawn\_shops | Pawn Shops | Y |
> > | school\_supplies\_and\_stationery | Office, School Supply, and Stationery Stores | Y |
> > | opticians\_optical\_goods\_and\_eyeglasse\_stores | Opticians, Optical Goods, and Eyeglasses | Y |
> > | watch\_and\_jewellery\_repair\_stores | Clock, Jewelry, and Watch Repair Shops | N |
> > | wholesale\_footwear\_stores | Commercial Footwear | Y |
> > | antique\_stores | Antique Reproduction Stores | Y |
> > | plumbing\_and\_heating\_equipment | Plumbing and Heating Equipment | Y |
> > | variety\_stores | Variety Stores | Y |
> > | liquor\_stores | Package Stores, Beer, Wine, Liquor | N |
> > | boat\_dealers | Boat Dealers | Y |
> > | cosmetic\_stores | Cosmetic Stores | Y |
> > | home\_furnishing\_stores | Miscellaneous House Furnishing Specialty Shops | Y |
> > | telecommunication\_equipment\_stores | Telecommunication Equipment Including Telephone Sales | Y |
> > | women\_clothing | Womens Ready to Wear Stores | Y |
> > | florists | Florists | Y |
> > | commercial\_photography\_and\_graphic\_design\_services | Commercial Art, Graphics, Photography | Y |
> > | building\_matrial\_stores | Building Materials, Lumber Stores | Y |
> > | candy\_nut\_confectionery\_shops | Candy, Nut, Confectionery Stores | Y |
> > | glass\_and\_wallpaper\_stores | Glass, Paint, Wallpaper Stores | Y |
> > | video\_game\_supply\_stores | Video Amusement Game Supplies | Y |
> > | drapery\_and\_window\_coverings\_stores | Drapery, Upholstery, and Window Coverings Stores | Y |
> > | uniforms\_and\_commercial\_clothing\_stores | Men’s, Women’s, and Children’s Uniforms and Commercial Clothing | Y |
> > | automotive\_paint\_shops | Automotive Paint Shops | Y |
> > | durable\_goods\_stores | Durable Goods not elsewhere classified | Y |
> > | fur\_shops | Furriers and Fur Shops | Y |
> > | industrial\_supplies | Industrial Supplies | Y |
> > | motorcycle\_shops\_and\_dealers | Motorcycle Shops and Dealers | Y |
> > | children\_and\_infants\_wear\_stores | Children’s and Infants’ Wear Stores | Y |
> > | computer\_software\_stores | Computer Software Stores | Y |
> > | women\_accessory\_stores | Women Accessory and Specialty Stores | Y |
> > | books\_periodicals\_and\_newspaper | Books, Periodicals and Newspapers | Y |
> > | floor\_covering\_stores | Floor Covering Stores | Y |
> > | crystal\_and\_glassware\_stores | Crystal and Glassware Stores | Y |
> > | hardware\_equipment\_and\_supply\_stores | Hardware Equipment and Supplies | Y |
> > | discount\_stores | Discount stores | Y |
> > | computers\_peripheral\_equipment\_software | Computers, Computer Peripheral Equipment, Software | Y |
> > | automobile\_and\_truck\_dealers | Automobile and Truck Dealers-Used Only-Sales | Y |
> > | aircraft\_and\_farm\_equipment\_dealers | Miscellaneous Automotive, Aircraft, and Farm Equipment Dealers-not elsewhere classified | Y |
> > | antique\_shops\_sales\_and\_repairs | Antique Shops-Sales, Repairs, and Restoration Services | Y |
> > | bicycle\_stores | Bicycle Shops-Sales and Service | Y |
> > | hearing\_aids\_stores | Hearing Aids-Sales, Service, Supply Stores | Y |
> > | music\_stores | Music Stores-Musical Instruments, Pianos, Sheet Music | Y |
> > | construction\_materials | Construction Materials-not elsewhere classified | Y |
> > | accessory\_and\_apparel\_stores | Accessory and Apparel Stores-Miscellaneous | Y |
> > | second\_hand\_stores | SECOND HAND STORES-USED MERCHANDISE STORES | Y |
> > | fuel\_dealers | Fuel Dealers-Coal, Fuel Oil, Liquefied Petroleum, Wood | N |
> > | furniture\_and\_home\_furnishing\_store | Furniture and Home Furnishing store | Y |
>
> > [accordion] Food and Beverages
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | online\_food\_ordering | Online Food Ordering | Y |
> > | restaurant | Restaurants | Y |
> > | food\_court | Food Courts/Corporate Cafeteria | Y |
> > | catering | Catering Services | Y |
> > | alcohol | Alcoholic Beverages | Y |
> > | restaurant\_search\_and\_booking | Restaurant search and reservations | Y |
> > | dairy\_products | Dairy Products Stores | Y |
> > | bakeries | Bakeries | Y |
>
> > [accordion] IT and Software
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | saas | SaaS (Software as a service) | N |
> > | paas | Platform as a service | N |
> > | iaas | Infrastructure as a service | N |
> > | consulting\_and\_outsourcing | Consulting and Outsourcing | N |
> > | web\_development | Web designing, development and hosting | Y |
> > | technical\_support | Technical Support | Y |
> > | data\_processing | Data processing | Y |
>
> > [accordion] Gaming
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | game\_developer | Game developer and publisher | N |
> > | esports | E-sports | N |
> > | online\_casino | Online Casino | N |
> > | fantasy\_sports | Fantasy Sports | N |
> > | gaming\_marketplace | Game distributor/Marketplace | N |
>
> > [accordion] Media and Entertainment
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | video\_on\_demand | Video on demand | Y |
> > | music\_streaming | Music streaming services | Y |
> > | multiplex | Multiplexes | Y |
> > | content\_and\_publishing | Content and Publishing | Y |
> > | ticketing | Events and movie ticketing | Y |
> > | news | News | Y |
> > | video\_game\_arcades | Video Game Arcades/Establishments | N |
> > | video\_tape\_production\_and\_distribution | Motion Pictures and Video Tape Production and Distribution | Y |
> > | bowling\_alleys | Bowling Alleys | Y |
> > | billiard\_and\_pool\_establishments | Billiard and Pool Establishments | Y |
> > | amusement\_parks\_and\_circuses | Amusement Parks, Carnivals, Circuses, Fortune Tellers | Y |
> > | ticket\_agencies | Theatrical Producers-except Motion Pictures, Ticket Agencies | Y |
>
> > [accordion] Services
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | repair\_and\_cleaning | Repair and cleaning services | Y |
> > | interior\_design\_and\_architect | Interior Designing and Architect | Y |
> > | movers\_and\_packers | Movers and Packers | Y |
> > | legal | Legal Services | Y |
> > | event\_planning | Event planning services | Y |
> > | service\_centre | Service Centre | Y |
> > | consulting | Consulting Services | N |
> > | ad\_and\_marketing | Ad and marketing agencies | Y |
> > | services\_classifieds | Services Classifieds | Y |
> > | multi\_level\_marketing | Multi-level Marketing | Y |
> > | construction\_services | GENERAL CONTRACTORS | Y |
> > | architectural\_services | Horticultural and Landscaping Services | Y |
> > | car\_washes | CAR WASHES | Y |
> > | motor\_home\_rentals | A MOTOR HOME AND RECREATIONAL | Y |
> > | stenographic\_and\_secretarial\_support\_services | Stenographic and Secretarial Support Services | Y |
> > | chiropractors | Chiropractors | Y |
> > | automotive\_service\_shops | Automotive Service Shops | Y |
> > | shoe\_repair\_shops | Hat Cleaning Shops, Shoe Repair Shops, Shoe Shine Parlors | Y |
> > | telecommunication\_service | Telecom Servc including but not ltd to prepaid phone serv | Y |
> > | fines | FINES | N |
> > | security\_agencies | Agencies – Security Services | Y |
> > | type\_setting\_and\_engraving\_services | Typesetting, Plate Making, Related Services | Y |
> > | small\_appliance\_repair\_shops | Appliance Repair Shops, Electrical and Small | Y |
> > | photography\_labs | Photo Developing, Photofinishing Laboratories | Y |
> > | dry\_cleaners | Dry Cleaners | Y |
> > | electronic\_repair\_shops | Electronic Repair Shops | Y |
> > | cleaning\_and\_sanitation\_services | Specialty Cleaning, Polishing, and Sanitation Preparations | Y |
> > | nursing\_care\_facilities | Nursing and Personal Care Facilities | Y |
> > | direct\_marketing | Direct Marketing Other Direct Marketers not elsewhere classified | Y |
> > | veterinary\_services | Veterinary Services | Y |
> > | affliated\_auto\_rental | AFFILIATED AUTO RENTAL | Y |
> > | alimony\_and\_child\_support | COURT COST INCLUDING ALIMONY AND CHILD SUPPORT | Y |
> > | airport\_flying\_fields | AIRPORT FLYING FIELDS | Y |
> > | tire\_retreading\_and\_repair\_shops | Tire Retreading and Repair Shops | Y |
> > | television\_cable\_services | Cable and other Pay Television Services | Y |
> > | recreational\_and\_sporting\_camps | Recreational and Sporting Camps | Y |
> > | agricultural\_cooperatives | AGRICULTURAL COOPERATIVES | Y |
> > | carpentry\_contractors | Carpentry Contractors | Y |
> > | wrecking\_and\_salvaging\_services | Wrecking and Salvage Yards | Y |
> > | automobile\_towing\_services | Towing Services | Y |
> > | barber\_and\_beauty\_shops | Barber and Beauty Shops | Y |
> > | video\_tape\_rental\_stores | Video Tape Rental Stores | Y |
> > | golf\_courses | Golf Courses, Public | Y |
> > | miscellaneous\_repair\_shops | Miscellaneous Repair Shops and Related Services | Y |
> > | motor\_homes\_and\_parts | MOTOR HOME DEALERS | Y |
> > | debt\_marriage\_personal\_counseling\_service | Debt, Marriage, Personal Counseling Service | Y |
> > | air\_conditioning\_and\_refrigeration\_repair\_shops | Air Conditioning and Refrigeration Repair Shops | Y |
> > | tailors | Alterations, Mending, Seamstresses, Tailors | Y |
> > | massage\_parlors | Massage Parlors | Y |
> > | horse\_or\_dog\_racing | Government Licensed Horse/Dog Racing | N |
> > | credit\_reporting\_agencies | Consumer Credit Reporting Agencies | Y |
> > | heating\_and\_plumbing\_contractors | Air Conditioning, Heating, and Plumbing Contractors | Y |
> > | electrical\_contractors | ELECTRICAL CONTRACTORS | Y |
> > | carpet\_and\_upholstery\_cleaning\_services | Carpet and Upholstery Cleaning | Y |
> > | roofing\_and\_metal\_work\_contractors | Roofing and Siding, Sheet Metal Work Contractors | Y |
> > | internet\_service\_providers | Computer Network/Information Services | Y |
> > | laundry\_services | Cleaning, Garment, and Laundry Services | Y |
> > | recreational\_camps | Trailer Parks and Campgrounds | Y |
> > | masonry\_contractors | Insulation, Masonry, Plastering, Stonework, and Tile Setting Contractors | Y |
> > | exterminating\_and\_disinfecting\_services | Exterminating and Disinfecting Services | Y |
> > | ambulance\_services | Ambulance Services | Y |
> > | funeral\_services\_and\_crematories | Funeral Services and Crematories | Y |
> > | metal\_service\_centres | Metal Service Centers and Offices | Y |
> > | copying\_and\_blueprinting\_services | Quick Copy, Reproduction, and Blueprinting Services | Y |
> > | fuel\_dispensers | Fuel Dispenser, Automated | N |
> > | lottery | Government Owned Lottery,Government Owned Lottery | N |
> > | welding\_repair | WELDING REPAIR | Y |
> > | mobile\_home\_dealers | Mobile Home Dealers | Y |
> > | concrete\_work\_contractors | CONCRETE WORK CONTRACTORS | Y |
> > | boat\_rentals | Boat Leases and Boat Rentals | Y |
> > | personal\_shoppers\_and\_shopping\_clubs | Buying/Shopping Clubs, Services | Y |
> > | door\_to\_door\_sales | DOOR-TO-DOOR SALES | Y |
> > | travel\_related\_direct\_marketing | Direct Marketing-Travel-Related Arrangement Services | Y |
> > | lottery\_and\_betting | Betting -including Lottery Tickets, Chips at Gaming Casinos, Off-Track Betting and Wagers at Race Tracks | N |
> > | bands\_orchestras\_and\_miscellaneous\_entertainers | Bands, Orchestras, and Miscellaneous Entertainers-not elsewhere classified | Y |
> > | furniture\_repair\_and\_refinishing | Furniture-Reupholstery and Repair, Refinishing | Y |
> > | direct\_marketing\_and\_subscription\_merchants | Direct Marketing-Continuity/Subscription Merchants | N |
> > | typewriter\_stores\_sales\_service\_and\_rentals | Typewriter Stores-Sales, Service, and Rentals | Y |
> > | direct\_marketing\_insurance\_services | Direct Marketing-Insurance Services | Y |
> > | business\_services | Business Services-not elsewhere classified | Y |
> > | inbound\_telemarketing\_merchants | Direct Marketing-Inbound Telemarketing Merchants | N |
> > | recreation\_services | Recreation Services-not elsewhere classified | Y |
> > | swimming\_pools | Swimming Pools-Sales and Supplies | Y |
> > | outbound\_telemarketing\_merchants | Direct Marketing-Outbound Telemarketing Merchants | N |
> > | public\_warehousing | Public Warehousing-Farm Products, Refrigerated Goods, | Y |
> > | clothing\_rental\_stores | Clothing Rental-Costumes, Uniforms, and Formal Wear | Y |
> > | contractors | Contractors, Special Trade-not elsewhere classified | Y |
> > | transportation\_services | Transportation Services-not elsewhere classified | Y |
> > | electric\_razor\_stores | Electric Razor Stores-Sales and Service | Y |
> > | service\_stations | Service Stations with or without Ancillary Services | N |
> > | photographic\_studio | Photographic studios | Y |
> > | professional\_services | Professional services | Y |
>
> > [accordion] Housing and Real Estate
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | developer | Developer | N |
> > | facility\_management | Facility Management Company | Y |
> > | rwa | RWA | Y |
> > | coworking | Co-working spaces | N |
> > | realestate\_classifieds | Real estate classifieds | N |
> > | space\_rental | Home or office rentals | N |
>
> > [accordion] Not-for-Profit
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | charity | Charity | Y |
> > | educational | Educational | Y |
> > | religious | Religious | Y |
> > | personal | Personal | Y |
>
> > [accordion] Social
> >
> > | Sub Category | Description | Status |
> > | - | - | - |
> > | matchmaking | Dating and Matrimony platforms | N |
> > | social\_network | Social Network | Y |
> > | messaging | Messaging and Communication | Y |
> > | professional\_network | Professional Network | Y |
> > | neighbourhood\_network | Local/Neighbourhood network | Y |
> > | automobile\_associations\_and\_clubs | Automobile Associations | Y |
> > | political\_organizations | Political Organizations | N |
> > | country\_and\_athletic\_clubs | Clubs-Country Clubs, Membership-Athletic, Recreation, Sports, Private Golf Courses | Y |
> > | associations\_and\_membership | Associations and membership | Y |

## Credit Card EMI

> [accordion] What are the standard credit card interest rates charged by the banks for EMI?
>
> The interest rates charged by various banks for each of the tenures are provided for your reference. The minimum transaction amount for which EMIs are applicable can vary for each bank. The maximum amount is dependent on the card limit set by the issuing bank.
>
> > [accordion] **American Express (AMEX)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 5000 ^^^^^^^ | 199 ^^^^^^^ | 14% | October 12, 2023 ^^^^^^^ |
> > | 6 months | | | 14% | |
> > | 9 months | | | 14% | |
> > | 12 months | | | 14% | |
> > | 18 months | | | 15% | |
> > | 24 months | | | 15% | |
> > | 36 months | | | NA | |
>
> > [accordion] **Bank of Baroda (BARB)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 2500 ^^^^^^^ | NA ^^^^^^^ | 16% | July 26, 2024 ^^^^^^^ |
> > | 6 months | | | 16% | |
> > | 9 months | | | 16% | |
> > | 12 months | | | 16% | |
> > | 18 months | | | 16% | |
> > | 24 months | | | 16% | |
> > | 36 months | | | NA | |
>
> > [accordion] **Citibank (CITI)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 2500 ^^^^^^^ | A one-time processing fee of 1% or ₹100, whichever is higher, will be charged by the bank. ^^^^^^^ | 16% | April 08, 2024 ^^^^^^^ |
> > | 6 months | | | 16% | |
> > | 9 months | | | 16% | |
> > | 12 months | | | 16% | |
> > | 18 months | | | 16% | |
> > | 24 months | | | 16% | |
> > | 36 months | | | NA | |
>
> > [accordion] **Federal Bank (FDRL)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 2500 ^^^^^^^ | NA ^^^^^^^ | 15.99% | July 26, 2024 ^^^^^^^ |
> > | 6 months | | | 15.99% | |
> > | 9 months | | | 15.99% | |
> > | 12 months | | | 15.99% | |
> > | 18 months | | | 15.99% | |
> > | 24 months | | | 15.99% | |
> > | 36 months | | | NA | |
>
> > [accordion] **HDFC Bank (HDFC)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 1000 | 299 ^^^^^^^ | 16% | July 23, 2025 ^^^^^^^ |
> > | 6 months | 1000 | | 16% | |
> > | 9 months | 1000 | | 16% | |
> > | 12 months | 1000 | | 16% | |
> > | 18 months | 3000 | | 16% | |
> > | 24 months | 3000 | | 16% | |
> > | 36 months | NA | | NA | |
>
> > [accordion] **HSBC Bank (HSBC)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 2000 ^^^^^^^ | 99 ^^^^^^^ | 15% | 21 February 2024 ^^^^^^^ |
> > | 6 months | | | 15% | |
> > | 9 months | | | 15% | |
> > | 12 months | | | 15% | |
> > | 18 months | | | 15% | |
> > | 24 months | | | 15% | |
> > | 36 months | | | NA | |
>
> > [accordion] **ICICI Bank (ICIC)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 1500 ^^^^^^^ | 199 ^^^^^^^ | 15.99% | November 29, 2023 ^^^^^^^ |
> > | 6 months | | | 15.99% | |
> > | 9 months | | | 15.99% | |
> > | 12 months | | | 15.99% | |
> > | 18 months | | | 15.99% | |
> > | 24 months | | | 15.99% | |
> > | 36 months | | | NA | |
>
> > [accordion] **IDFB Bank (IDFB)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 2500 ^^^^^^^ | A one-time processing fee of 1% or ₹99, whichever is higher, will be charged by the bank. ^^^^^^^ | 16% | September 17, 2025 ^^^^^^^ |
> > | 6 months | | | 16% | |
> > | 9 months | | | 16% | |
> > | 12 months | | | 16% | |
> > | 18 months | | | 16% | |
> > | 24 months | | | 16% | |
> > | 36 months | | | 16% | |
>
> > [accordion] **IndusInd Bank (INDB)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 2000 ^^^^^^^ | 249 ^^^^^^^ | 16% | September 12, 2024 ^^^^^^^ |
> > | 6 months | | | 16% | |
> > | 9 months | | | 16% | |
> > | 12 months | | | 16% | |
> > | 18 months | | | 16% | |
> > | 24 months | | | 16% | |
> > | 36 months | | | 16% | |
>
> > [accordion] **Kotak Mahindra Bank (KKBK)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 2500 ^^^^^^^ | 249 ^^^^^^^ | 16% | February 21, 2024 ^^^^^^^ |
> > | 6 months | | | 16% | |
> > | 9 months | | | 16% | |
> > | 12 months | | | 16% | |
> > | 18 months | | | 16% | |
> > | 24 months | | | 16% | |
> > | 36 months | | | NA | |
>
> > [accordion] **RBL Bank (RATN)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 2000 ^^^^^^^ | 199 ^^^^^^^ | 13% | April 05, 2023 ^^^^^^^ |
> > | 6 months | | | 14% | |
> > | 9 months | | | 15% | |
> > | 12 months | | | 15% | |
> > | 18 months | | | 15% | |
> > | 24 months | | | 15% | |
> > | 36 months | | | NA | |
>
> > [accordion] **State Bank of India (SBIN)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 2500 ^^^^^^^ | NA | 16.75% | January 7, 2026 ^^^^^^^ |
> > | 6 months | | A one-time processing fee of ₹40 will be charged if the transaction amount exceeds ₹20,000. | 16.50% | |
> > | 9 months | | A one-time processing fee of ₹79 will be charged if the transaction amount exceeds ₹20,000. | 16.50% | |
> > | 12 months | | A one-time processing fee of ₹159 will be charged if the transaction amount exceeds ₹20,000. | 16% | |
> > | 18 months | | A one-time processing fee of ₹199 will be charged if the transaction amount exceeds ₹20,000. | 16.25% | |
> > | 24 months | | A one-time processing fee of ₹299 will be charged if the transaction amount exceeds ₹20,000. | 16.25% | |
> > | 36 months | | NA | NA | |
>
> > [accordion] **Standard Chartered (SCBL)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 2500 ^^^^^^^ | A one-time processing fee of 1% will be charged by the bank. ^^^^^^^ | 11.88% | July 26, 2024 ^^^^^^^ |
> > | 6 months | | | 13% | |
> > | 9 months | | | 14% | |
> > | 12 months | | | 14% | |
> > | 18 months | | | NA | |
> > | 24 months | | | NA | |
> > | 36 months | | | NA | |
>
> > [accordion] **Axis Bank (UTIB)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 3000 ^^^^^^^ | A one-time processingfee of 1% or ₹100, whichever is higher, will be charged by the bank. ^^^^^^^ | 16% | December 12, 2023 ^^^^^^^ |
> > | 6 months | | | 16% | |
> > | 9 months | | | 16% | |
> > | 12 months | | | 16% | |
> > | 18 months | | | 16% | |
> > | 24 months | | | 16% | |
> > | 36 months | | | NA | |
>
> > [accordion] **Yes Bank (YESB)**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Processing Fee (in INR) | Interest rates | Last Updated |
> > | - | - | - | - | - |
> > | 3 months | 1500 ^^^^^^^ | 299 ^^^^^^^ | 16% | December 12, 2023 ^^^^^^^ |
> > | 6 months | | | 16% | |
> > | 9 months | | | 16% | |
> > | 12 months | | | 16% | |
> > | 18 months | | | 16% | |
> > | 24 months | | | 16% | |
> > | 36 months | | | NA | |

> [accordion] What are the interest rates charged by other credit cards for EMI?
>
> The interest rates charged by other cards for EMI is given below.
>
> > [accordion] **OneCard**:
> >
> > | Tenures in Months | Minimum Amount (in INR) | Interest rates |
> > | - | - | - |
> > | 3 months | 2500 ^^^^^^ | 16% |
> > | 6 months | | 16% |
> > | 9 months | | 16% |
> > | 12 months | | 16% |
> > | 18 months | | 16% |
> > | 24 months | | 16% |

## Cardless EMI

> [accordion] What are the standard interest rates charged by the banks for cardless EMI?
>
> The standard interest rates charged by various banks for cardless EMI are provided for your reference.
>
> | Cardless EMI | Issuer Bank | Provider Code | Minimum Amount (in INR) | 3 months | 6 months | 9 months | 12 months | 18 months |
> | - | - | - | - | - | - | - | - | - |
> | InstaCred | HDFC Bank | `hdfc` | 5000 | 16% | 16% | 16% | 16% | 16% |
> | InstaCred | ICICI Bank | `icic` | 7000 | 16% | 16% | 16% | 16% | NA |
> | InstaCred | IDFC First | `idfb` | 5000 | 24% | 24% | 24% | 24% | NA |
> | InstaCred | Kotak Mahindra Bank | `kkbk` | 3000 | 20% | 20% | 20% | 20% | NA |
> | axio | NA | `walnut369` | 900 | 24% | 24% | 24% | NA | NA |
> | Fibe | NA | `earlysalary` | 3000 | 30% | 30% | 30% | NA | NA |
> | ZestMoney | NA | `zestmoney` | 3000 | 22% | 24% | 24% | NA | NA |

> [accordion] What are the standard interest rates charged by Pay Later providers for cardless EMI?
>
> The standard interest rates charged by the providers for Pay Later providers are given below:
>
> | Pay Later | 15 days | 30 days | 45 days | 60 days | 90 days |
> | - | - | - | - | - | - |
> | LazyPay | Interest free | NA | NA | NA | NA |
> | PayPal | Interest free | NA | NA | NA | NA |
>
> <sup>\*</sup> Interest rates are determined on a case-to-case basis. [Contact support](https://razorpay.com/support/#request) for more information.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > All interest rates mentioned above are per annum.

## No Cost EMI

> [accordion] Who bears the cost for the discount given in No Cost EMI?
>
> You, as a merchant, would bear the cost of No Cost EMI. It will be given as an upfront discount on the product cost to the end consumer. The discount percentage will vary by the bank and period of EMI.

> [accordion] Which payment methods can be used for No Cost EMI?
>
> No Cost EMI is available on all credit card and debit card EMI banks.

> [accordion] Will the customers' banks continue to charge them interest?
>
> Yes, the customers' banks will continue to charge them interest. However, this interest charge has been provided to the customer as an upfront discount at the time of purchase, effectively giving them the benefit of a No Cost EMI.

> [accordion] Can I enable No Cost EMIs at the Checkout?
>
> Yes. Razorpay enables you to display No Cost EMIs at the Checkout. Know more about [No Cost EMIs](https://razorpay.com/docs/payments/offers/no-cost-emi.md).

> [accordion] How can I know about the percentage discount of the No Cost EMI that I bear?
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > The banks charge GST to end consumers on the interest paid over and above the following amount.
>
> Calculations on the cost incurred by the merchant at all standard plan and tenures are listed below:
>
> | Amount (in INR) | Interest (in %) | Tenure (in Months) | Amount Paid by Customer | Monthly EMI | No Cost EMI Discount | Discount | Pricing | Total Cost (in %) |
> | - | - | - | - | - | - | - | - | - |
> | 10000 | 11% | 3 | 9,819.43 | 3333.33 | 180.57 | 1.81% | 3% | 4.81% |
> | 10000 | 12% | 3 | 9,803.28 | 3333.33 | 196.72 | 1.97% | 3% | 4.97% |
> | 10000 | 13% | 3 | 9,787.18 | 3333.33 | 212.82 | 2.13% | 3% | 5.13% |
> | 10000 | 14% | 3 | 9,771.13 | 3333.33 | 228.87 | 2.29% | 3% | 5.29% |
> | 10000 | 15% | 3 | 9,755.11 | 3333.33 | 244.89 | 2.45% | 3% | 5.45% |
> | 10000 | 11% | 6 | 9686.85 | 1666.67 | 313.15 | 3.13% | 3% | 6.13% |
> | 10000 | 12% | 6 | 9659.13 | 1666.67 | 340.87 | 3.41% | 3% | 6.41% |
> | 10000 | 13% | 6 | 9631.53 | 1666.67 | 368.47 | 3.68% | 3% | 6.68% |
> | 10000 | 14% | 6 | 9604.04 | 1666.67 | 395.96 | 3.96% | 3% | 6.96% |
> | 10000 | 15% | 6 | 9576.68 | 1666.67 | 423.32 | 4.23% | 3% | 7.23% |
> | 10000 | 11% | 9 | 9556.66 | 1111.11 | 443.34 | 4.43% | 3% | 7.43% |
> | 10000 | 12% | 9 | 9517.80 | 1111.11 | 482.20 | 4.82% | 3% | 7.82% |
> | 10000 | 13% | 9 | 9479.17 | 1111.11 | 520.83 | 5.21% | 3% | 8.21% |
> | 10000 | 14% | 9 | 9440.77 | 1111.11 | 559.23 | 5.59% | 3% | 8.59% |
> | 10000 | 15% | 9 | 9402.61 | 1111.11 | 597.39 | 5.97% | 3% | 8.97% |
> | 10000 | 11% | 12 | 9428.80 | 833.33 | 571.20 | 5.71% | 3% | 8.71% |
> | 10000 | 12% | 12 | 9379.23 | 833.33 | 620.77 | 6.21% | 3% | 9.21% |
> | 10000 | 13% | 12 | 9330.04 | 833.33 | 669.96 | 6.70% | 3% | 9.70% |
> | 10000 | 14% | 12 | 9281.21 | 833.33 | 718.79 | 7.19% | 3% | 10.19% |
> | 10000 | 15% | 12 | 9232.76 | 833.33 | 767.24 | 7.67% | 3% | 10.67% |
> | 10000 | 11% | 18 | 9179.92 | 555.56 | 820.08 | 8.20% | 3% | 11.20% |
> | 10000 | 12% | 18 | 9110.15 | 555.56 | 889.85 | 8.90% | 3% | 11.90% |
> | 10000 | 13% | 18 | 9041.13 | 555.56 | 958.87 | 9.59% | 3% | 12.59% |
> | 10000 | 14% | 18 | 8972.85 | 555.56 | 1027.15 | 10.27% | 3% | 13.27% |
> | 10000 | 15% | 18 | 8905.30 | 555.56 | 1094.70 | 10.95% | 3% | 13.95% |
> | 10000 | 11% | 24 | 8939.84 | 416.67 | 1060.16 | 10.60% | 3% | 13.60% |
> | 10000 | 12% | 24 | 8851.41 | 416.67 | 1148.59 | 11.49% | 3% | 14.49% |
> | 10000 | 13% | 24 | 8764.21 | 416.67 | 1235.79 | 12.36% | 3% | 15.36% |
> | 10000 | 14% | 24 | 8678.23 | 416.67 | 1321.77 | 13.22% | 3% | 16.22% |
> | 10000 | 15% | 24 | 8593.43 | 416.67 | 1406.57 | 14.07% | 3% | 17.07% |

> [accordion] How does the No Cost EMI settlement work?
>
> The order amount minus the entire interest subvented by you as a discount is settled in your bank account as per your [settlement cycle](https://razorpay.com/docs/payments/settlements#settlement-cycle).
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > However, Razorpay pricing is not included in this settlement, it will be applied in addition to the above amount.

> [accordion] Can I create No Cost EMI offers on Cardless EMI?
>
> No, we do not support No Cost EMI offers on Cardless EMI.

## Low Cost EMI

> [accordion] Why should I run Low Cost EMI Offers?
>
> Running Low Cost EMI Offers helps you attract a wider customer base by reducing the upfront cost barrier. This leads to increased sales and higher average order values.
>
> Additionally, offering discount on interest for longer tenures sets you apart in a competitive market and opens opportunities for upselling, contributing to overall business growth and financial stability.

> [accordion] Who bears the cost for the discount given in Low Cost EMI?
>
> As a business, you would bear the partial cost of Low Cost EMI, which appears as an upfront discount on the product cost to the end consumer.
>
> You can decide the cost to subvent for each tenure and the customer bears the remaining cost. The interest percentage will vary by the bank and the EMI tenure. Know more about the [EMI Calculation](https://razorpay.com/docs/payments/offers/low-cost-emi.md#calculation-of-emi).

> [accordion] Which payment methods can be used for Low Cost EMI?
>
> Low Cost EMI is available on all credit and debit card EMIs.

> [accordion] Will the customers' banks continue to charge them interest?
>
> Yes, the customers' banks will continue to charge them interest. However, partial interest subvented by you appears as an upfront discount to the customers at the time of purchase.

> [accordion] Can I enable Low Cost EMIs at the Checkout?
>
> Yes. Razorpay enables you to display Low Cost EMIs at the Checkout. Know more about [Low Cost EMIs](https://razorpay.com/docs/payments/offers/low-cost-emi.md).

> [accordion] How can I know about the percentage discount of the Low Cost EMI that I bear?
>
> You can decide how much percentage of the total interest you want to subvent during offer creation. This appears as an upfront discount on the product cost and the customer bears the remaining cost.

> [accordion] How does the Low Cost EMI settlement work?
>
> The order amount minus the discount subvented by you is settled in your bank account as per your [settlement cycle](https://razorpay.com/docs/payments/settlements#settlement-cycle).
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Razorpay pricing is not included in this settlement, it will be applied in addition to the above amount.

> [accordion] Can I create Low Cost EMI offers on Cardless EMI?
>
> No, we do not support Low Cost EMI offers on Cardless EMI.
