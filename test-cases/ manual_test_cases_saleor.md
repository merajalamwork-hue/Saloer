# Manual Test Cases — Saleor Storefront
**URL:** https://storefront.saleor.io/default-channel  
**Type:** Manual E2E Testing  
**Flow:** Browse → Cart → Checkout  

---

## TEST SUITE 1: Homepage & Navigation

### TC-001: Homepage Loads Successfully
- **Precondition:** Browser is open, internet connected
- **Steps:**
  1. Open https://storefront.saleor.io/default-channel
  2. Observe the page load
- **Expected Result:** Homepage loads with header, navigation, product listings, and footer visible
- **Status:**  Pass 

---

### TC-002: Navigate to a Product Category
- **Precondition:** Homepage is loaded
- **Steps:**
  1. Click on any category link in the navigation menu (e.g., "Clothing", "Accessories")
  2. Observe the category page
- **Expected Result:** Category page loads with relevant products displayed
- **Status:**  Pass 

---

### TC-003: Search for a Product
- **Precondition:** Homepage is loaded
- **Steps:**
  1. Click on the search icon
  2. Type a product name (e.g., "Apple Juice")
  3. Press Enter or click the search button
- **Expected Result:** Search results page displays matching products with names and prices
- **Status:**  Pass 

---

### TC-004: Search with No Results
- **Precondition:** Homepage is loaded
- **Steps:**
  1. Click the search icon
  2. Type a random string (e.g., "xyzabc123")
  3. Press Enter
- **Expected Result:** A "no results found" message is displayed gracefully
- **Status:**  Pass

---

## TEST SUITE 2: Product Listing Page (PLP)

### TC-005: Product Cards Display Correctly
- **Precondition:** A category page is open
- **Steps:**
  1. Navigate to any category
  2. Observe the product cards
- **Expected Result:** Each card shows product image, name, and price
- **Status:**   Pass

---

### TC-006: Sort Products
- **Precondition:** A category page with multiple products is open
- **Steps:**
  1. Locate the sort/filter dropdown
  2. Select "Price: Low to High"
  3. Observe the product order
- **Expected Result:** Products are reordered from lowest to highest price
- **Status:**   Pass 

---

### TC-007: Filter Products
- **Precondition:** A category page is open with filter options available
- **Steps:**
  1. Apply a filter (e.g., by color or size)
  2. Observe the updated product list
- **Expected Result:** Only products matching the selected filter are displayed
- **Status:**   Pass 

---

## TEST SUITE 3: Product Detail Page (PDP)

### TC-008: Open a Product Detail Page
- **Precondition:** A category or search results page is open
- **Steps:**
  1. Click on any product card
  2. Observe the product detail page
- **Expected Result:** PDP loads with product name, images, description, price, and "Add to Cart" button
- **Status:**   Pass  

---

### TC-009: Product Image Gallery
- **Precondition:** A PDP with multiple images is open
- **Steps:**
  1. Click on the thumbnail images below the main image
  2. Observe the main image area
- **Expected Result:** Main image updates to reflect the selected thumbnail
- **Status:**   Pass 

---

### TC-010: Select Product Variant (Size/Color)
- **Precondition:** PDP of a product with variants is open
- **Steps:**
  1. Select a size (e.g., "M")
  2. Select a color if available
  3. Observe any price or availability changes
- **Expected Result:** Selected variant is highlighted; price/stock updates if applicable
- **Status:**   Pass  

---

### TC-011: Add to Cart — Without Selecting Variant
- **Precondition:** PDP of a product with required variants (size/color) is open
- **Steps:**
  1. Do NOT select any variant
  2. Click "Add to Cart"
- **Expected Result:** An error or prompt appears asking the user to select a variant before adding
- **Status:**  Fail

---

### TC-012: Add to Cart — With Variant Selected
- **Precondition:** PDP is open; a variant is selected
- **Steps:**
  1. Select a valid variant (e.g., size "M")
  2. Click "Add to Cart"
  3. Observe the cart icon or confirmation
- **Expected Result:** Product is added to cart; cart count updates (e.g., shows "1"); success notification appears
- **Status:**  Fail

---

### TC-013: Change Quantity Before Adding to Cart
- **Precondition:** PDP is open with a quantity selector
- **Steps:**
  1. Change quantity to 3
  2. Click "Add to Cart"
- **Expected Result:** Cart shows the item with quantity 3
- **Status:**  Pass  

---

## TEST SUITE 4: Shopping Cart

### TC-014: View Cart
- **Precondition:** At least one product has been added to the cart
- **Steps:**
  1. Click the cart icon in the header
- **Expected Result:** Cart opens showing all added items with name, variant, quantity, and price
- **Status:**   Pass 

---

### TC-015: Update Item Quantity in Cart
- **Precondition:** Cart is open with at least one item
- **Steps:**
  1. Increase the quantity of a cart item to 2
  2. Observe the total price
- **Expected Result:** Quantity updates to 2; subtotal recalculates correctly
- **Status:**  Pass 

---

### TC-016: Remove Item from Cart
- **Precondition:** Cart has at least one item
- **Steps:**
  1. Click the remove/delete icon next to a cart item
- **Expected Result:** Item is removed from cart; cart total updates; if cart is empty, an empty cart message is shown
- **Status:**   Pass 

---

### TC-017: Cart Persists After Page Refresh
- **Precondition:** Cart has at least one item added
- **Steps:**
  1. Add a product to cart
  2. Refresh the browser (F5)
  3. Open the cart again
- **Expected Result:** Cart still contains the previously added item
- **Status:**  Pass  

---

### TC-018: Proceed to Checkout Button
- **Precondition:** Cart has at least one item
- **Steps:**
  1. Open the cart
  2. Click "Proceed to Checkout" or equivalent CTA
- **Expected Result:** User is navigated to the checkout page
- **Status:**  Pass  

---

## TEST SUITE 5: Checkout — Contact Information

### TC-019: Checkout Page Loads
- **Precondition:** User clicked "Proceed to Checkout" from cart
- **Steps:**
  1. Observe the checkout page
- **Expected Result:** Checkout page loads with an email/contact information field as the first step
- **Status:**  Pass 

---

### TC-020: Enter Guest Email
- **Precondition:** Checkout page is open (not logged in)
- **Steps:**
  1. Enter a valid email address (e.g., testuser@example.com)
  2. Click Continue / Next
- **Expected Result:** User proceeds to the shipping address step
- **Status:**  Pass  

---

### TC-021: Enter Invalid Email Format
- **Precondition:** Checkout page is open
- **Steps:**
  1. Enter an invalid email (e.g., "notanemail")
  2. Click Continue
- **Expected Result:** Validation error shown: "Please enter a valid email address"
- **Status:**  Pass  

---

## TEST SUITE 6: Checkout — Shipping Address

### TC-022: Fill Valid Shipping Address
- **Precondition:** Contact info step is complete; shipping form is visible
- **Steps:**
  1. Enter First Name: Test
  2. Enter Last Name: User
  3. Enter Address Line 1: 123 Main St
  4. Enter City: New York
  5. Select Country: United States
  6. Enter ZIP: 10001
  7. Enter Phone: +1 212 555 0100
  8. Click Continue
- **Expected Result:** Shipping address is accepted; user moves to shipping method step
- **Status:**  Pass  

---

### TC-023: Submit Shipping Form with Missing Required Fields
- **Precondition:** Shipping address form is open
- **Steps:**
  1. Leave the "Address Line 1" field empty
  2. Fill all other fields
  3. Click Continue
- **Expected Result:** Validation error highlights the missing required field
- **Status:**  Pass 

---

## TEST SUITE 7: Checkout — Shipping Method

### TC-024: Verify Shipping Cost in Order Summary
- **Precondition:** A shipping method is selected
- **Steps:**
  1. Observe the order summary panel on the right
- **Expected Result:** Shipping cost from the selected method is reflected in the total
- **Status:**  Pass 

---

## TEST SUITE 8: Checkout — Payment

### TC-025: Payment Section Loads
- **Precondition:** Shipping method step is complete
- **Steps:**
  1. Proceed to the payment step
  2. Observe available payment options
- **Expected Result:** Payment section loads with at least one payment method 
- **Status:**  Pass  

---


## TEST SUITE 9: Edge Cases & Negative Tests

### TC-026: Add Out-of-Stock Product to Cart
- **Precondition:** An out-of-stock product is visible
- **Steps:**
  1. Navigate to an out-of-stock product
  2. Attempt to add it to cart
- **Expected Result:** "Add to Cart" button is disabled or an "Out of Stock" message is shown
- **Status:**  Pass  

---

### TC-027: Navigate Back During Checkout
- **Precondition:** User is on the shipping method step
- **Steps:**
  1. Click the browser back button
  2. Observe the state
- **Expected Result:** User goes back to the previous checkout step with previously entered data intact
- **Status:**  Pass  

---

### TC-028: Checkout with Empty Cart
- **Precondition:** Cart is empty
- **Steps:**
  1. Manually navigate to /checkout
- **Expected Result:** User is redirected to the cart page or homepage with a message that the cart is empty
- **Status:**  Pass  

---

### TC-029: Responsiveness on Mobile View
- **Precondition:** Desktop browser available
- **Steps:**
  1. Open DevTools (F12)
  2. Switch to mobile view (e.g., iPhone 12 — 390px width)
  3. Repeat TC-001, TC-012, TC-018, TC-027
- **Expected Result:** All pages and flows are usable on mobile; no elements are cut off or broken
- **Status:**  Pass  

---

## Summary Table

| TC ID  | Title                                     | Priority | Status |
|--------|-------------------------------------------|----------|--------|
| TC-001 | Homepage Loads Successfully               | High     |        |
| TC-002 | Navigate to a Product Category            | High     |        |
| TC-003 | Search for a Product                      | High     |        |
| TC-004 | Search with No Results                    | Medium   |        |
| TC-005 | Product Cards Display Correctly           | Medium   |        |
| TC-006 | Sort Products                             | Low      |        |
| TC-007 | Filter Products                           | Low      |        |
| TC-008 | Open a Product Detail Page                | High     |        |
| TC-009 | Product Image Gallery                     | Low      |        |
| TC-010 | Select Product Variant                    | High     |        |
| TC-011 | Add to Cart Without Variant               | High     |        |
| TC-012 | Add to Cart With Variant                  | High     |        |
| TC-013 | Change Quantity Before Adding to Cart     | Medium   |        |
| TC-014 | View Cart                                 | High     |        |
| TC-015 | Update Item Quantity in Cart              | High     |        |
| TC-016 | Remove Item from Cart                     | High     |        |
| TC-017 | Cart Persists After Page Refresh          | Medium   |        |
| TC-018 | Proceed to Checkout Button                | High     |        |
| TC-019 | Checkout Page Loads                       | High     |        |
| TC-020 | Enter Guest Email                         | High     |        |
| TC-021 | Enter Invalid Email Format                | High     |        |
| TC-022 | Fill Valid Shipping Address               | High     |        |
| TC-023 | Submit Shipping Form with Missing Fields  | High     |        |
| TC-024 | Select a Shipping Method                  | High     |        |
| TC-025 | Payment Section Loads                     | High     |        |
| TC-026 | Add Out-of-Stock Product to Cart          | Medium   |        |
| TC-027 | Navigate Back During Checkout             | Medium   |        |
| TC-028 | Checkout with Empty Cart                  | Medium   |        |
| TC-029 | Responsiveness on Mobile View             | High     |        |

---

*Generated for: https://storefront.saleor.io/default-channel*  
*Last Updated: April 2026*
