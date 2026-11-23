> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Customise Payment Pages

> Customise Payment Pages and send different versions of the same Payment Page to different customers.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can customise Payment Pages for customers and send them custom links with the amount, email, phone and custom fields (such as First Name and Last Name) pre-populated. This serves as a personalisation value-add for customers. You can do this by making changes to the Payment Pages URL before sending it to customers. You can pre-populate [Input Fields](#pre-populate-input-fields) and [Amount Fields](#pre-populate-amount-fields)

## Pre-populate Input Fields

You can pre-populate the input fields on your Payment Page, such as name, email and contact and send customised Payment Pages to customers.

| Name | Email | Phone Number |
| - | - | - |
| Nur Aisyah | [nur.aisyah@example.com](mailto:nur.aisyah@example.com) | 899999999 |
| Siti Aisyah | [siti.aisyah@example.com](mailto:siti.aisyah@example.com) | 999988889 |

> [accordion] To pre-populate input fields:
>
> 1. Log in to the Dashboard and create a Payment Page titled **Registration**.
> 2. Fill in the details of the event such as description, venue, time and more.
> 3. Create a price field of any type in the Payment Details Section.
> 4. Create an input field with type as `Single Line` to capture the customer's **Full Name**.
> 5. **Save and Publish** the Payment Page.
> 6. Copy and paste the Payment Page short URL on the browser.
>
> When you open the Payment Page short URL on the browser, it expands to a longer format.
>
> **Example**
>
> * Payment Page Title - `Registrations`
> * Short URL - `https://curl.io/l/pcsLir1`
> * Long URL - `https://pages.curlec.com/pl_CjbpJ6gnwk6Ehy/view`
>
> Here, add suffixes to the field names and values as shown:
>
> | Field Name | Mandatory to create Payment Page | Value |
> | - | - | - |
> | `email` | Yes | [nur.aisyah@example.com](mailto:nur.aisyah@example.com) |
> | `phone` | Yes | 8999999999 |
> | `full_name`(`_` denotes the space between the field name words) | No | Nur%20Aisyah (%20 denotes the space between the field value words) |
>
> The long URL appears as shown:
>
> `https://pages.curlec.com/pl_DOiqlZTGqnH9F8/view?amount=199&email=nur.aisyah@example.com.com&phone=8999999999&full_name=Nur%20Aisyah`
>
> This is a unique URL that can be shared with the customer named Siti Aisyah to accept payments from her.
>
> Similarly, you can add suffixes to these field names and values and create different versions of the same Payment Page for different customers.

> [!NOTE]
>
> **Handy Tips**
>
> * Use only `lower case` when suffixing field names and values in the long URL. You can use `upper case` in values of custom fields, such as Full Name.
> * The field-level validations are in place. Hence, if you enter a character in `amount` value, say `amount=100a` or `amount=RM.Hundred%20only`, the field will not get populated.
> * If the custom field consists of two words, include an underscore as a separator of two words. For example, the two words in the Last Name field should be separated by an underscore, that is, `Last_Name`.

## Pre-populate Amount Fields

You can pre-populate amount fields on your Payment Page. That is, in case of amount field with type:

> [accordion] Case 1: Pre-populate Item Quantity
>
> Pre-populate the quantity of item to be purchased by customer.
>
> **Example** \\
>
> You want to sell iPhone 11 Pro smartphone cases for . You are creating a Payment Page titled `Limited Edition iPhone 11 Phone Case` to sell the product. You can ensure that when the customer opens the Payment Page, the quantity to be purchased appears pre-selected as `1`. However, this will work only when the field has been marked optional.
>
> > [accordion] To pre-populate item quantity:
> >
> > Add an optional amount field selected by default.
> >
> > 1. On the Dashboard, create a Payment Page titled **Limited Edition iPhone 11 Phone Case**.
> >
> > 2. Fill in the details of the product.
> >
> > 3. In the Payment Details Section, create a price field called `Marble Pink Case` using `Item with Quantity` as the amount field type.
> >
> > 4. Create any additional fields required such as Name, Address and so on.
> >
> > 5. **Save and Publish** the Payment Page.
> >
> > 6. Copy and paste the Payment Page short URL on the browser.
> >
> > When you open the Payment Page short URL on the browser, it expands to a longer format. For example:
> >
> > * Payment Page Title - `Limited Edition iPhone 11 Phone Case`
> > * Short URL - `https://curl.io/l/nfR16LE`
> > * Long URL - `https://pages.curlec.com/pl_EZvXqNgFYRNZtS/view`
> >
> > Here, add suffixes to the field names and values as shown:
> >
> > | Field Name | Value |
> > | - | - |
> > | `marble_pink_case` | 1 |
> >
> > The Long URL now appears as shown:
> >
> > `https://pages.curlec.com/pl_EZvXqNgFYRNZtS/view?marble_pink_case=1`
> >
> > This is now a unique URL wherein the item quantity will always appear selected as `1`:

> [accordion] Case 2: Pre-populate Fixed Amount Field
>
> Add an optional amount field that appears selected by default.
>
> **Example** \\
>
> You run a Creative Writing Academy that uses Payment Pages to collect online course registration fees from students. You offer two courses:
>
> * Creative Writing (main course)
> * Book Promotion Techniques (optional course)
>
> You can create a Payment Page titled `Creative Writing Course Registration` to collect registration fees. Also, you can ensure that when the student opens the Payment Page, the optional field, that is, the book promotion technique course appears pre-selected.
>
> > [accordion] To pre-populate fixed amount field:
> >
> > 1. On the Dashboard, create a Payment Page titled **Creative Writing Course Registration**.
> >
> > 2. Fill in the details of the product.
> >
> > 3. In the Payment Details Section, create a price field called `Creative Writing Course Registration` using `Fixed Amount` as the amount field type.
> >
> > 4) Create the additional fields:
> >    * `How To Promote Your Book` - Create this price field with `fixed amount` type and mark it `optional`.
> >    * Create other fields for collecting student details such as name.
> > 5) **Save and Publish** the Payment Page.
> > 6) Copy and paste the Payment Page short URL on the browser.
> >
> > When you open the Payment Page short URL on the browser, it expands to a longer format. For example:
> >
> > * Payment Page Title: `Creative Writing Course Registration`
> > * Short URL: `https://curl.io/l/lz3xNr6`
> > * Long URL: `https://pages.curlec.com/pl_EZxm4DFp4W0KPP/view`
> >
> > Here, add suffixes to the field names and values as shown:
> >
> > | Field Name | Value |
> > | - | - |
> > | `how_to_promote_your_book` | 1 |
> >
> > The Long URL now appears as shown:
> > `https://pages.razorpay.com/pl_EZxm4DFp4W0KPP/view?how_to_promote_your_book=1`
> >
> > This is now a unique URL wherein the amount field will always be appear selected:

> [accordion] Case 3: Display Different Amounts for Different Customers
>
> Add a field to display different amounts for different customers.
>
> **Example** \\
>
> You want to get registrations for an event. You are creating a Payment Page titled `Registrations` to accept the registration fee payments. You would like to set it up in such a way, wherein:
>
> * Early bird, Nur Aisyah pays RM199
> * Siti Aisyah pays RM299
> * Last minute registrant, Nur Siti pays RM399
>
> In this case, you do not have to create multiple Payment Pages. You can fix and pre-populate the amount you want each customer to pay.
>
> > [accordion] To display different amounts for different customers:
> >
> > 1. On the Dashboard, create a Payment Page titled **Registration**.
> > 2. Fill in the details of the event such as description, venue, time and more.
> > 3. In the Payment Details Section, create a price field. - `Customer Decides Amount`.
> > 4. Create an input field with type as `Single Line` to capture the customer's **Full Name**.
> > 5. **Save and Publish** the Payment Page.
> > 6. Copy and paste the Payment Page short URL on the browser.
> >
> > When you open the Payment Page short URL on the browser, it expands to a longer format. For example:
> >
> > * Payment Page Title - `Registrations`
> > * Short URL - `https://curl.io/l/pcsLir1`
> > * Long URL - `https://pages.curlec.com/pl_CjbpJ6gnwk6Ehy/view`
> >
> > Here, add suffixes to the field names and values as shown:
> >
> > | Field Name | Mandatory to create Payment Page | Value |
> > | - | - | - |
> > | `amount` | Yes | 199 |
> > | `email` | Yes | [nur.aisyah@example.com](mailto:nur.aisyah@example.com) |
> > | `phone` | Yes | 9000090000 |
> > | `full_name`(`_` denotes the space between the field name words) | No | Nur%20Aisyah (%20 denotes the space between the field value words) |
> >
> > The long URL now appears as shown:
> >
> > `https://pages.curlec.com/pl_CjbpJ6gnwk6Ehy/view/?amount=199&email=nur.aisyah@example.com&phone=9000090000&full_name=Nur%20Aisyah`
> >
> > This is a unique URL that can be shared with the customer named Nur Aisyah to accept payments from her.

> [!NOTE]
>
> **Points to Remember**
>
> * If using a custom field name for amount, ensure that the field name is entered in lowercase and is separated by an underscore. For example, if the amount field name is Registration Amount, enter the suffix as `registration_amount`.
> * If the amount field item is out of stock or has less quantity available, though the field will appear prefilled, the customer will not be able to make a purchase.
> * Pre-population of the amount field is subject to the Minimum and Maximum Input Price set for the amount field. For example, if Maximum Input Price has been set as , then the Registration Amount field cannot be prefilled with a value higher than .

### Related Information

* [Create a Payment Page](https://razorpay.com/docs/my/payments/payment-pages/create.md)
* [Add Images, Videos and More](https://razorpay.com/docs/my/payments/payment-pages/add-images-videos.md)
