# SYLBET Test Cases

- **Business:** SYLBET (handcrafted cane furniture and decor)
- **Website:** https://sylbet.onrender.com
- **Tester:** Pritom Majumdar
- **Date:** 20-Dec-2025
- **Browser:** Chrome on Windows 11 and Mobile

---

## TC_REG_001: Register with valid details

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/register |
| **Priority / Severity** | High / Major |
| **Precondition** | User is not logged in; email is not already registered |
| **Test Data** | Name: Pritom Majumdar, Email: pritommajumdar@gmail.com, Phone: 01712345678, Password: pritom123@Pass |
| **Steps** | 1. Open the register page<br>2. Enter name, email, phone and password<br>3. Click Register |
| **Expected Result** | Account is created and the user is logged in or redirected to the login page with a success message. |
| **Actual Result** | Account was created and the user was redirected to the login page with the message "Registration successful". |
| **Status** | ✅ Pass |
| **Bug ID** | N/A |

## TC_REG_002: Register with an already registered email

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/register |
| **Priority / Severity** | Medium / Minor |
| **Precondition** | pritommajumdar@gmail.com was registered in TC_REG_001 |
| **Test Data** | Email: pritommajumdar@gmail.com, Password: pritom123@Pass |
| **Steps** | 1. Open the register page<br>2. Enter the existing email and other valid details<br>3. Click Register |
| **Expected Result** | An error such as "Email already exists" is shown. No duplicate account is created. |
| **Actual Result** | Error "Email already exists" was shown. No duplicate account was created. |
| **Status** | ✅ Pass |
| **Bug ID** | N/A |

## TC_REG_003: Register with empty required fields

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/register |
| **Priority / Severity** | Medium / Minor |
| **Precondition** | User is on the register page |
| **Test Data** | All fields left blank |
| **Steps** | 1. Open the register page<br>2. Leave all fields empty<br>3. Click Register |
| **Expected Result** | Validation messages appear for the required fields. The form is not submitted. |
| **Actual Result** | Browser validation "Please fill out this field" appeared on the first field. The form was not submitted. |
| **Status** | ✅ Pass |
| **Bug ID** | N/A |

## TC_REG_004: Register with a weak password

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/register |
| **Priority / Severity** | High / Major |
| **Precondition** | User is not logged in; email is not registered |
| **Test Data** | Name: Pritom Majumdar, Email: pritom.test02@gmail.com, Phone: 01712345678, Password: 123 |
| **Steps** | 1. Open the register page<br>2. Enter valid details with the password 123<br>3. Click Register |
| **Expected Result** | An error is shown that the password must be at least 8 characters with letters, numbers and a symbol. The account is not created. |
| **Actual Result** | The account was created successfully with the password "123". No password rule was enforced. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-105 |
| **Remarks** | Weak passwords are accepted, which makes accounts easy to hack. |

## TC_REG_005: Register with an invalid email format

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/register |
| **Priority / Severity** | Medium / Minor |
| **Precondition** | User is on the register page |
| **Test Data** | Email: pritom@gmail (no .com), Password: pritom123@Pass |
| **Steps** | 1. Open the register page<br>2. Enter the email pritom@gmail and other valid details<br>3. Click Register |
| **Expected Result** | An error "Enter a valid email address" is shown. The account is not created. |
| **Actual Result** | The account was created with the email "pritom@gmail". No error was shown. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-106 |
| **Remarks** | Email format is validated only partly. The user will never get the verification or order emails. |

## TC_LOG_001: Login with valid credentials

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/login |
| **Priority / Severity** | High / Major |
| **Precondition** | A registered account exists |
| **Test Data** | Email: pritommajumdar@gmail.com, Password: pritom123@Pass |
| **Steps** | 1. Open the login page<br>2. Enter the valid email and password<br>3. Click Login |
| **Expected Result** | User is logged in and redirected to the home page. The user name or account option is visible. |
| **Actual Result** | User was logged in and redirected to the home page. The account option was visible in the header. |
| **Status** | ✅ Pass |
| **Bug ID** | N/A |

## TC_LOG_002: Login with a wrong password

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/login |
| **Priority / Severity** | High / Major |
| **Precondition** | A registered account exists |
| **Test Data** | Email: pritommajumdar@gmail.com, Password: WrongPass@99 |
| **Steps** | 1. Open the login page<br>2. Enter the valid email and a wrong password<br>3. Click Login |
| **Expected Result** | A general error like "Invalid email or password" is shown. The user stays on the login page. |
| **Actual Result** | The error said "Incorrect password", which shows that the email exists in the system. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-101 |
| **Remarks** | Security issue (user enumeration). The message should not reveal which field is wrong. |

## TC_LOG_003: Login with empty fields

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/login |
| **Priority / Severity** | Medium / Minor |
| **Precondition** | User is on the login page |
| **Test Data** | Email and password left blank |
| **Steps** | 1. Open the login page<br>2. Leave both fields empty<br>3. Click Login |
| **Expected Result** | Validation messages appear for both fields. The form is not submitted. |
| **Actual Result** | No message was shown. The Login button showed a loading state for about 10 seconds and then returned to normal. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-107 |
| **Remarks** | The empty form is sent to the server and no feedback is given to the user. |

## TC_LOG_004: Account lock after repeated wrong passwords

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/login |
| **Priority / Severity** | High / Major |
| **Precondition** | A registered account exists |
| **Test Data** | Email: pritommajumdar@gmail.com, Password: WrongPass@99 (entered 6 times) |
| **Steps** | 1. Open the login page<br>2. Enter the valid email and a wrong password<br>3. Click Login<br>4. Repeat steps 2 and 3 five more times |
| **Expected Result** | After 5 failed attempts the account is locked for some time or a CAPTCHA is shown. |
| **Actual Result** | No lock and no CAPTCHA. The login form accepted 6 wrong attempts and kept allowing more. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-108 |
| **Remarks** | Security issue. The site is open to brute force password attacks. |

## TC_CAT_001: View the product category page

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/shop?subcategory=6a1ae06fea8cdd33b8096d61 |
| **Priority / Severity** | High / Major |
| **Precondition** | None |
| **Test Data** | Subcategory ID: 6a1ae06fea8cdd33b8096d61 |
| **Steps** | 1. Open the category page link<br>2. Wait for the products to load |
| **Expected Result** | Products of the selected subcategory (for example cane sofa, cane chair, bookshelf, mirror) are listed with image, name and price. No broken images. |
| **Actual Result** | Products were listed with image, name and price. All images loaded correctly. |
| **Status** | ✅ Pass |
| **Bug ID** | N/A |

## TC_PRD_001: Open a product detail page

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/shop?subcategory=6a1ae06fea8cdd33b8096d61 |
| **Priority / Severity** | High / Major |
| **Precondition** | Category page shows products |
| **Test Data** | Product: Cane Sofa |
| **Steps** | 1. Open the category page<br>2. Click the Cane Sofa product |
| **Expected Result** | The product page opens with the correct name, image, price, description and an Add to Cart button. |
| **Actual Result** | The Cane Sofa page opened with the correct name, image, price, description and the Add to Cart button. |
| **Status** | ✅ Pass |
| **Bug ID** | N/A |

## TC_PRD_002: Add an out-of-stock product to the cart

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/shop?subcategory=6a1ae06fea8cdd33b8096d61 |
| **Priority / Severity** | High / Major |
| **Precondition** | A product is marked Out of Stock |
| **Test Data** | Product: Cane Bookshelf (Out of Stock) |
| **Steps** | 1. Open the category page<br>2. Click the out-of-stock product<br>3. Click Add to Cart |
| **Expected Result** | The Add to Cart button is disabled or a message "Out of stock" is shown. The item is not added. |
| **Actual Result** | The product was added to the cart and the user could continue to checkout. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-109 |
| **Remarks** | Stock status is not checked at add to cart or at checkout. |

## TC_SRC_001: Search for a product by name

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/shop?subcategory=6a1ae06fea8cdd33b8096d61 |
| **Priority / Severity** | High / Major |
| **Precondition** | Products named "mirror" exist in the catalog |
| **Test Data** | Search keyword: mirror |
| **Steps** | 1. Open the shop page<br>2. Type "mirror" in the search box<br>3. Press Enter |
| **Expected Result** | Only mirror products are listed and the result count is shown. |
| **Actual Result** | The result showed cane chairs and sofas along with the mirrors. The search matched words in the descriptions of unrelated products. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-110 |
| **Remarks** | Search results are not relevant to the keyword. |

## TC_CRT_001: Add a product to the cart

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/shop?subcategory=6a1ae06fea8cdd33b8096d61 |
| **Priority / Severity** | High / Major |
| **Precondition** | Products are available |
| **Test Data** | Product: Cane Chair, Quantity: 1 |
| **Steps** | 1. Open the Cane Chair product page<br>2. Click Add to Cart<br>3. Open the cart |
| **Expected Result** | Cane Chair is in the cart with the correct name, price and quantity. The cart count increases. |
| **Actual Result** | Cane Chair was added with the correct name, price and quantity 1. The cart count changed to 1. |
| **Status** | ✅ Pass |
| **Bug ID** | N/A |

## TC_CRT_002: Update product quantity in the cart

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com |
| **Priority / Severity** | High / Minor |
| **Precondition** | Cane Chair (1 item) is in the cart |
| **Test Data** | New quantity: 3 |
| **Steps** | 1. Open the cart<br>2. Change the quantity from 1 to 3 |
| **Expected Result** | Subtotal and total update to price x 3. The cart count shows the correct number. |
| **Actual Result** | Subtotal and total updated correctly, but the cart count in the header still showed 1 until the page was refreshed. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-102 |
| **Remarks** | The header cart count does not refresh dynamically. |

## TC_CRT_003: Remove a product from the cart

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com |
| **Priority / Severity** | Medium / Minor |
| **Precondition** | At least one item is in the cart |
| **Test Data** | Product: Cane Chair |
| **Steps** | 1. Open the cart<br>2. Click Remove on the item |
| **Expected Result** | The item is removed and the total is recalculated. An empty cart message is shown if no items remain. |
| **Actual Result** | The item was removed and the message "Your cart is empty" was shown. |
| **Status** | ✅ Pass |
| **Bug ID** | N/A |

## TC_CRT_004: Enter a negative quantity in the cart

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com |
| **Priority / Severity** | High / Major |
| **Precondition** | Cane Chair (1 item) is in the cart |
| **Test Data** | Quantity: -2 |
| **Steps** | 1. Open the cart<br>2. Type -2 in the quantity field<br>3. Press Enter |
| **Expected Result** | The negative value is rejected and the quantity stays at 1 or the minimum allowed. |
| **Actual Result** | The quantity accepted -2 and the cart total became a negative amount. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-111 |
| **Remarks** | No minimum quantity check. Negative totals could cause wrong order amounts. |

## TC_CRT_005: Cart items stay after logout and login

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com |
| **Priority / Severity** | Medium / Minor |
| **Precondition** | User is logged in |
| **Test Data** | Product: Cane Sofa, Quantity: 1 |
| **Steps** | 1. Add Cane Sofa to the cart<br>2. Logout<br>3. Login again with the same account<br>4. Open the cart |
| **Expected Result** | The Cane Sofa is still in the cart. |
| **Actual Result** | The cart was empty after login. The Cane Sofa was lost. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-112 |
| **Remarks** | The cart is not saved to the user account. |

## TC_CHK_001: Place an order with valid details

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/checkout |
| **Priority / Severity** | Critical / Blocker |
| **Precondition** | User is logged in; cart has a Bookshelf |
| **Test Data** | Name: Pritom Majumdar, Phone: 01712345678, Address: House 10, Zindabazar, Sylhet, Payment: Cash on Delivery |
| **Steps** | 1. Add Bookshelf to the cart<br>2. Go to the checkout page<br>3. Enter shipping details<br>4. Select a payment method<br>5. Click Place Order |
| **Expected Result** | Order is placed, an order confirmation or order ID is shown, and the cart becomes empty. |
| **Actual Result** | Order was placed, a confirmation message with an order ID was shown, and the cart became empty. |
| **Status** | ✅ Pass |
| **Bug ID** | N/A |

## TC_CHK_002: Checkout with missing required fields

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/checkout |
| **Priority / Severity** | High / Major |
| **Precondition** | User is logged in; cart has a Mirror |
| **Test Data** | Address and phone number left blank |
| **Steps** | 1. Add Mirror to the cart<br>2. Go to the checkout page<br>3. Leave address and phone empty<br>4. Click Place Order |
| **Expected Result** | Validation messages are shown for the missing fields. The order is not placed. |
| **Actual Result** | Validation messages were shown for address and phone. The order was not placed. |
| **Status** | ✅ Pass |
| **Bug ID** | N/A |

## TC_CHK_003: Checkout with an invalid phone number

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/checkout |
| **Priority / Severity** | Medium / Major |
| **Precondition** | User is logged in; cart has an item |
| **Test Data** | Phone: abc123 |
| **Steps** | 1. Go to the checkout page<br>2. Enter an invalid phone number and other valid details<br>3. Click Place Order |
| **Expected Result** | An error about the invalid phone number is shown. The order is not placed. |
| **Actual Result** | The order was placed successfully with the phone number "abc123". No validation error was shown. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-103 |
| **Remarks** | Phone number format is not validated. Delivery staff cannot contact the customer. |

## TC_CHK_004: Open checkout with an empty cart

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/checkout |
| **Priority / Severity** | Medium / Minor |
| **Precondition** | Cart is empty |
| **Test Data** | None |
| **Steps** | 1. Make sure the cart is empty<br>2. Open the checkout page directly |
| **Expected Result** | The user is redirected to the shop or cart, or sees a message that the cart is empty. No order can be placed. |
| **Actual Result** | The user was redirected to the cart page with the message "Your cart is empty". |
| **Status** | ✅ Pass |
| **Bug ID** | N/A |

## TC_CHK_005: Click Place Order twice quickly

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/checkout |
| **Priority / Severity** | Critical / Blocker |
| **Precondition** | User is logged in; cart has a Cane Chair |
| **Test Data** | Payment: Cash on Delivery, valid shipping details |
| **Steps** | 1. Go to the checkout page<br>2. Enter valid shipping details<br>3. Double-click the Place Order button quickly |
| **Expected Result** | Only one order is created. The button is disabled after the first click. |
| **Actual Result** | Two orders with different order IDs were created for the same cart. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-113 |
| **Remarks** | Duplicate orders. The Place Order button is not disabled while the request is processing. |

## TC_CHK_006: Check the order total on the checkout page

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com/checkout |
| **Priority / Severity** | High / Major |
| **Precondition** | User is logged in; 2 Cane Chairs are in the cart |
| **Test Data** | Price per chair: as shown on the product page, Delivery charge: as shown at checkout |
| **Steps** | 1. Go to the checkout page<br>2. Check the item subtotal, delivery charge and total |
| **Expected Result** | Total = item subtotal + delivery charge. The same amount appears on the order confirmation. |
| **Actual Result** | The checkout page showed the delivery charge but the total did not include it. The confirmation page showed a different total. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-114 |
| **Remarks** | The amounts on the checkout and confirmation pages do not match. |

## TC_SEC_001: Browser back button after logout

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com |
| **Priority / Severity** | High / Major |
| **Precondition** | User is logged in |
| **Test Data** | Account: pritommajumdar@gmail.com |
| **Steps** | 1. Login and open the My Account or Orders page<br>2. Click Logout<br>3. Click the browser Back button |
| **Expected Result** | The user is redirected to the login page. Account details are not shown. |
| **Actual Result** | The previous account page with the user's name and order details was shown from the browser cache. |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-115 |
| **Remarks** | Private data is visible after logout, which is a risk on shared computers. |

## TC_UI_001: Check the site on a mobile screen

| Field | Details |
|---|---|
| **Page URL** | https://sylbet.onrender.com |
| **Priority / Severity** | Medium / Minor |
| **Precondition** | None |
| **Test Data** | Device: Android phone (360 x 800), Browser: Chrome |
| **Steps** | 1. Open the home page on a mobile<br>2. Open the category page<br>3. Open a product and add it to the cart |
| **Expected Result** | Layout fits the screen, images load, buttons are tappable, and nothing overlaps. |
| **Actual Result** | On the category page, the product price overlapped the product name for items with long names (for example "Handcrafted Cane Lounge Chair"). |
| **Status** | ❌ Fail |
| **Bug ID** | BUG-104 |
| **Remarks** | Text overlap on small screens. Other pages looked fine. |

---

## Summary

| Total | Passed | Failed | Pass Rate |
|---|---|---|---|
| 26 | 11 | 15 | 42% |

## Defect List

| Bug ID | Test Case | Summary | Severity | Status |
|---|---|---|---|---|
| BUG-101 | TC_LOG_002 | Login error message reveals that the email is registered | Major | Open |
| BUG-102 | TC_CRT_002 | Header cart count does not update after changing quantity | Minor | Open |
| BUG-103 | TC_CHK_003 | Order is accepted with an invalid phone number | Major | Open |
| BUG-104 | TC_UI_001 | Price overlaps product name on mobile category page | Minor | Open |
| BUG-105 | TC_REG_004 | Weak password (123) is accepted during registration | Major | Open |
| BUG-106 | TC_REG_005 | Invalid email format is accepted during registration | Minor | Open |
| BUG-107 | TC_LOG_003 | No validation message when login form is empty | Minor | Open |
| BUG-108 | TC_LOG_004 | No account lock or CAPTCHA after repeated wrong passwords | Major | Open |
| BUG-109 | TC_PRD_002 | Out-of-stock product can be added to the cart | Major | Open |
| BUG-110 | TC_SRC_001 | Search returns unrelated products | Major | Open |
| BUG-111 | TC_CRT_004 | Negative quantity is accepted and gives a negative total | Major | Open |
| BUG-112 | TC_CRT_005 | Cart items are lost after logout and login | Minor | Open |
| BUG-113 | TC_CHK_005 | Double click on Place Order creates duplicate orders | Blocker | Open |
| BUG-114 | TC_CHK_006 | Order total does not include the delivery charge | Major | Open |
| BUG-115 | TC_SEC_001 | Account page is visible after logout using the Back button | Major | Open |
