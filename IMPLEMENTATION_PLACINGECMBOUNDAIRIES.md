# Implementation Plan: Placing ECM Boundaries & Audit
## File: IMPLEMENTATION_PLACINGECMBOUNDAIRIES.md

This plan outlines the steps to audit the current Shopify theme against the `SHOPIFY_DEV_STANDARDS.md` and `THE_CLEAN_EXECUTION_GUIDELINES.md`, ensuring total isolation for the Knee Massager funnel updates.

---

## 🚀 Execution Checklist

### Phase 1: Boundary Establishment
- [x] **Create Guidelines:** Establish `THE_CLEAN_EXECUTION_GUIDELINES.md` as the secondary Source of Truth.
- [x] **Audit Scoping:** Identified active templates and distinguished "Funnel Pages".
- [x] **Prefix Verification:** All `anti-gravity-*` files renamed to `ag-*` standard.
- [x] **Snippet Correction:** Removed hard-coded product logic from `product-variant-options.liquid`.

### Phase 2: Technical Audit (Page by Page)
- [x] **Theme Liquid Audit:** Checked `layout/theme.liquid` and linked `ag-custom.css`.
- [x] **Snippet Audit:** Cleaned `product-variant-options.liquid`.
- [x] **Checkout Integrity:** Verified CTA pulse and payment safety.
- [x] **Visual Update Review:** All sections audited and standardized.

### Phase 3: Massager Funnel Isolation
- [x] **Diagnostic Check:** Standardized `ag-diagnostic.liquid`.
- [x] **CTA Routing Audit:** Confirmed `#checkout-section` routing.
- [x] **Mobile Boundary Check:** Verified touch targets and BEM structure.

### Phase 4: Final Cleanup & Reporting
- [ ] **Consolidated Guidelines:** Audit all `ag-*` sections for hardcoded text/links and move them to Shopify Schema (Guideline 8-9).
- [ ] **Consolidate Styles:** Move ad-hoc styles into `assets/ag-custom.css` (scoped).
- [ ] **Error Log Review:** Check for Liquid syntax warnings or browser console errors.
- [ ] **Reporting:** Submit Audit findings to the user.

---

## 🛠️ Audit Parameters (Auditor Mode)
1. **Precision:** No changes to "Core Store" files unless for global fixes.
2. **Safety:** Checkout must remain 100% standard Shopify logic.
3. **Speed:** Ensure no heavy scripts are loading on pages where they aren't needed.

---
**Current Status:** Initialization
**Last Audit:** March 27, 2026
