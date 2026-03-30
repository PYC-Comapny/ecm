# Implementation Plan: Custom Bundle Deal Section (Main Offer)
**File Name:** IMPLIMETANTIONBUNDLEDEAL.md
**Status:** Implemented (Custom Optimized Offer Section)

This document outlines the execution strategy for creating a high-converting, custom bundle selection section (Main Offer) for the Knee Massager landing page, following the "The Precision Protocol" (CEG).

---

## 🎯 1. Core Objective
Replace the generic product selection with a custom "Tiered Bundle Selection" grid that allows customers to choose between three specific offers:
1. **Single Device Bundle** (1 Device + Upsells)
2. **Pair Only** (2 Devices - Discounted)
3. **Pair Devices Bundle** (2 Devices + Upsells - Best Value)

**CRITICAL:** We will NOT use a 3rd party "Bundle App" to create "Bundle Products." Instead, we will use a **Multi-Cart AJAX Injector** to add discrete items to the cart simultaneously.

---

## 🏗️ 2. Architectural Design

### A. The "Virtual Bundle" Logic
Each bundle option will be defined as a **Block** in the Shopify Section schema.
- **Block Settings:** 
    - `bundle_title` (e.g., "Pair Devices Bundle")
    - `bundle_subtitle` (e.g., "LEVIDE Knee 2.0")
    - `main_product_variant_id` (The ID for the massager)
    - `main_product_quantity` (1 or 2)
    - `upsell_1_variant_id` (The ID for the Gel)
    - `upsell_1_quantity` (0, 1, or 2)
    - `upsell_2_variant_id` (The ID for the Brace)
    - `upsell_2_quantity` (0, 1, or 2)
    - `display_price` (The front-end price shown to the user)
    - `compare_at_price` (The slashed price)

### B. Multi-Add-To-Cart Execution
When the "Add Bundle to Cart" button is clicked, a custom JS function will:
1. Scrape the variant IDs and quantities from the block's data-attributes.
2. Build an `items` array:
   ```json
   {
     "items": [
       { "id": 123456789, "quantity": 2 },
       { "id": 987654321, "quantity": 2 },
       { "id": 112233445, "quantity": 1 }
     ]
   }
   ```
3. POST to `/cart/add.js`.
4. Redirect the user directly to `/checkout` (bypassing the cart drawer as per Phase 3 of the Visuals Plan).

---

## 🎨 3. Visual Execution (The "High-Conversion" Look)
Following the provided images and the **Clean Execution Guidelines**:

1. **Card Layout:** Vertical stack of cards with premium rounded corners.
2. **Border Pulsing:** The "Best Value" (Popular) bundle will use a **Trust Green** or **Bright Red** border with a subtle glow pulse effect (`ag-glow-pulse`).
3. **Highlighting:** The "Pair Devices Bundle" will be the largest card with a "Most Popular" badge in the top-right corner.
4. **Icons:** Use the custom product images provided in the screenshots (Gel, Brace, etc.) as block image settings.
5. **Price Design:** Massive, bold pricing with the slashed "Compare At" price next to it, using the `heading-premium` utility class.

---

## 📝 4. Detailed Implementation Checklist

### Phase 1: Logic & Schema (The Foundation)
- [x] **Section Creation:** Create `sections/ag-bundle-offer.liquid`. (Renamed to `ag-bundle-deals.liquid`)
- [x] **Schema Definition:**
    - [x] Create `bundle_option` block type.
    - [x] Add `product` and `variant` selectors to the schema.
    - [x] Add `text` settings for titles, subtitles, and price overrides.
- [x] **Data-Attribute Mapping:** Ensure each "Add to Cart" button includes `data-bundle-items='[{"id": 123, "qty": 1}, ...]'`.

### Phase 2: CSS & Visuals (The Premium Layer)
- [x] **Responsive Grid:** Flexbox/CSS Grid to handle 1-column mobile and 3-column desktop (or stacked if preferred).
- [x] **Animations:** Implement `.animate-on-scroll` for the cards. (Available via `ag-custom.css`)
- [x] **Borders & Badges:** Use `.ag-card-popular` with the Red gradient border shown in the image.

### Phase 3: JS Interaction (The Checkout Bridge)
- [x] **AJAX Handler:** Write the `ag-multicart.js` logic (integrated into the section).
- [x] **Direct Checkout:** Ensure the `window.location.href = '/checkout'` redirect is triggered only on success.
- [x] **Error Handling:** Add a simple loading state to the button while the AJAX request is pending. (Loading spinner added)
- [x] **Integrated Layout:** Created `sections/ag-optimized-offer.liquid` with the 2-column image/content split and stacked bundles.


---

## 🛡️ 5. Safety & Verification (CEG Protocol)
1. **Isolation Test:** This section must ONLY load on the `knee-massager` page.
2. **Commerce Guard:** Verify that adding a bundle does not "empty" existing items in the cart (Standard `/cart/add.js` behavior).
3. **Checkout Verification:** Test the "Pair Devices Bundle" through to the Shopify Payment page to ensure all items are correctly calculated.

---

**Next Step:** Once this plan is approved, I will begin building the Liquid structure for `ag-bundle-offer.liquid`.
