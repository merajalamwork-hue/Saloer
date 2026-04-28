# Bug Report — Saleor Storefront

---

## BUG-001: "Select Options" Button Does Not Add Product to Cart & Provides No User Feedback

---

### 📋 Bug Details

| Field              | Details                                      |
|--------------------|----------------------------------------------|
| **Bug ID**         | BUG-001                                      |
| **Reported By**    | Meraj Alam                                   |
| **Date Reported**  | April 28, 2026                               |
| **Severity**       | High                                         |
| **Priority**       | High                                         |
| **Status**         | Open                                         |
| **Related TC**     | TC-012 — Add to Cart With Variant Selected   |

---

### 🌐 Environment

| Field            | Details                                                                 |
|------------------|-------------------------------------------------------------------------|
| **URL**          | https://storefront.saleor.io/default-channel/products/blue-polygon-shirt?size=xl |
| **Browser**      | Chrome (latest)                                                         |
| **OS**           | macOS                                                                   |
| **Device**       | Desktop                                                                 |
| **Test Account** | Guest (not logged in)                                                   |

---

### 🐛 Bug Summary

After selecting a color and size variant on the **Blue Polygon Shirt** product detail page, the **"Select options"** button does not add the product to the cart. No error message, warning, or feedback of any kind is displayed to the user, leaving them with no indication of what went wrong or what action to take next.

---

### 🔁 Steps to Reproduce

1. Navigate to: `https://storefront.saleor.io/default-channel/products/blue-polygon-shirt`
2. On the Product Detail Page, select **Color: Blue**
3. Select **Size: XL**
4. Click the **"Select options"** button
5. Observe the page behavior

---

### ✅ Expected Result

- Product should be added to the cart
- Cart icon in the header should update with item count (e.g., "1")
- A success notification/toast should appear (e.g., "Item added to cart")
- **OR** if the item cannot be added, a clear error message should explain why (e.g., "This variant is out of stock")

---

### ❌ Actual Result

- Clicking **"Select options"** does nothing
- The cart count does **not** update
- **No error message** is displayed
- **No toast or notification** appears
- The button label remains **"Select options"** instead of changing to **"Add to Cart"**
- The user has **no indication** of what went wrong

---

### 📸 Screenshot

![Bug Screenshot](<img width="1680" height="1050" alt="Screenshot 2026-04-28 at 12 52 30 PM" src="https://github.com/user-attachments/assets/0b4b82f4-2e74-45ca-8d1f-f9201976885e" />
)

---

### 💥 Impact Analysis

| Impact Area         | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| **User Experience** | User is completely blocked with zero feedback — highly confusing            |
| **Business Impact** | User cannot complete a purchase → direct loss of sale / cart abandonment    |
| **Accessibility**   | Screen readers receive no context or error — fails accessibility standards  |
| **Trust**           | User assumes the website is broken and may leave permanently                |

---

### 🔍 Root Cause Hypothesis

The button label **"Select options"** typically appears when **not all required variants are selected**. However, in this case both Color and Size are already selected (Blue + XL), yet the button still shows "Select options" instead of "Add to Cart." This suggests one of the following:

- The selected variant (Blue / XL) may be **out of stock** but the system does not communicate this
- A **frontend state management bug** where the selected variant is not being registered properly
- The button label logic is **not updating** after variant selection

---

### 💡 Suggested Fix

1. Change button label to **"Add to Cart"** once all required variants are selected
2. If the variant is out of stock — **disable the button** and display a clear message: *"This size is currently out of stock"*
3. Add a **toast notification or inline error** when the action cannot be completed
4. Ensure the **out-of-stock state is visually indicated** on the size/color selector itself (e.g., strikethrough or greyed out)

---

### 🔗 Related Test Case

See `manual_test_cases_saleor.md`:
- **TC-010** — Select Product Variant
- **TC-011** — Add to Cart Without Selecting Variant
- **TC-012** — Add to Cart With Variant Selected
- **TC-032** — Add Out-of-Stock Product to Cart

---

*Reported as part of Manual QA Testing — Saleor Storefront Portfolio*
