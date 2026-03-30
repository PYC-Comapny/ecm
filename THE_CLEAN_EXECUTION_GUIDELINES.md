# 🧹 The Clean Execution Guidelines (CEG)
## Version 1.0 | "The Precision Protocol"

This document defines the strict boundaries and execution standards for all Shopify theme modifications. Its purpose is to ensure that performance optimizations and visual updates never compromise core commerce functionality (Checkout, Payments, or Product Logic).

---

## 🛡️ 1. The Golden Rule: Scope Isolation
**Every edit must be page-specific.** 
- **NO GLOBAL LEAKS:** Custom CSS or JS intended for a specific landing page must never load or execute on irrelevant pages (e.g., Checkout, Cart, or other Product pages).
- **PREFIXING MANDATE:** Every custom file, snippet, and CSS class MUST start with the `ag-` prefix. Global theme classes (e.g., `.button`) should ONLY be extended using `ag-` wrappers.
- **CONDITIONAL LOADING:** Use Liquid logic to wrap custom assets:
  ```liquid
  {% if request.page_type == 'product' and product.handle == 'knee-massager' %}
    {{ 'ag-knee-massager.css' | asset_url | stylesheet_tag }}
  {% endif %}
  ```
- **VERIFICATION:** Before saving any change, the agent MUST confirm: *"Which specific page (handle/template) am I targeting?"*

---

## 🚫 2. The "No-Touch" Commerce Zone
The following areas are strictly off-limits for aesthetic or layout modifications unless explicitly requested for a deep-dive fix:
- **Payment Processing:** Any scripts or forms involving `stripe`, `paypal`, `klarna`, or Shopify Pay.
- **Checkout Bot-Protection:** Do not modify fields or hidden inputs in checkout-related forms.
- **Cart Logic:** Standard Shopify AJAX cart hooks must remain untouched to ensure the "Add to Cart" flow works globally.
- **Shopify Guidelines:** Code must remain compliant with Shopify's "Online Store 2.0" standards.

---

## 🎯 3. Element Integrity Check
When working with buttons, CTAs, or products, follow this precision checklist:
1.  **Unique Selectors:** Use `id` or specific classes (prefixed with `ag-`) to target elements. Never use generic selectors like `button` or `.btn` globally.
2.  **CTA Routing:** Ensure that funnel-specific CTA redirects (e.g., bypassing cart to checkout) ONLY affect the targeted funnel page.
3.  **Variant Selection:** Do not break the connection between variant selectors and the "Add to Cart" button.
4.  **Checkout Barriers:** Ensure no custom overlays or "glassmorphism" effects block the actual checkout or payment buttons on mobile devices.

---

## 🧪 4. Pre-Deployment Audit (Every Time)
Before declaring a task complete, every AI agent must verify:
- [ ] **Mobile Touch-Targets:** Are buttons large enough and unblocked?
- [ ] **The "Back-Door" Test:** Does the normal site (non-funnel pages) still work perfectly?
- [ ] **Checkout Bridge:** Does clicking the CTA result in a successful redirect to `/checkout`?
- [ ] **Console Hygiene:** No "ReferenceError" or "Undefined" errors in the browser console.

---

## 📝 5. Communication Protocol
- **AGENT:** "I am preparing to edit `sections/ag-hero.liquid`. This will only affect the `knee-massager` product page. Is this correct?"
- **USER:** "Yes."
- **AGENT:** *Proceeds with scoped execution.*

---

## 🏗️ 6. Asset & File Hygiene
To maintain a high-performance, premium store:
- **Don't use Inline Styles:** Avoid `<style>` tags inside Liquid sections. Move all custom CSS to `assets/ag-custom.css`.
- **Naming Convention (CSS):** Use BEM-lite with the prefix: `.ag-hero`, `.ag-hero__title`, `.ag-hero--large`.
- **File Metadata:** Every `ag-` file must start with a comment header:
  ```liquid
  {% comment %}
    @author Antigravity
    @description [What this section does]
    @isolated [Page/Template this belongs to]
  {% endcomment %}
  ```
- **Custom Presets:** Section presets in the `{% schema %}` must be labeled `AG - [Name]` for easy filtering in the Shopify Theme Editor.

---

## 🤝 7. The Handover Protocol
When working with other AI developers or continuing a chat:
1. **Declare Scope:** Start by saying: *"I am working within the AG boundary of [Page Name]. I will not touch core checkout or global logic."*
2. **Double Check:** Always run a `grep` search for `anti-gravity` to ensure no legacy, non-standard names still exist.
3. **Log Progress:** Update the checklist in `IMPLEMENTATION_PLACINGECMBOUNDAIRIES.md` after every major task.

---

## 🏗️ 8. Theme Editor Empowerment (The "Slider" Rule)
To ensure the USER has full control without needing an AI for every adjustment:
- **ZERO HARD-CODED CONTENT:** No text strings, image URLs, or button links should be hard-coded in Liquid. Everything MUST be exposed via the `{% schema %}`.
- **PRECISION CONTROLS:** Every `ag-` section must include schema settings for:
    - **Typography:** Desktop & Mobile font size sliders (e.g., `font_size_h1`, `font_size_mobile`).
    - **Mapping:** Button links must use the `url` setting type (never hardcoded strings like `/checkout`).
    - **Visibility:** Toggle switches for optional sub-elements (e.g., `show_icon_bar`).
- **LOGICAL NAMING:** Use intuitive setting IDs (e.g., `hero_title` instead of `text_1`) to ensure the Theme Editor sidebar is easy to navigate.
- **STYLE PROTECTION (The "Premium Lock"):** While text and links are editable, the core visual aesthetics (glassmorphism, glow effects, and custom animations) must be strictly bound to the `ag-` CSS system. Schema settings should control *content* and *proportions* (font size, margin), while the *styling* itself remains a protected premium asset to ensure the high-converting "look" is never accidentally removed.

---

## ⚡ 9. The Bulldoze Protocol (Scaling & Speed)
The goal is to launch new product funnels with maximum velocity and zero technical debt:
- **MODULAR REUSE:** Build sections to be generic enough for reuse across products. Use the "AG - [Section Name]" prefix for easy identification.
- **IMPLEMENTATION LEDGERS:** Every new product launch must start with a dedicated `IMPLEMENTATION_PRODUCT_[NAME].md`. Refer back to previous implementation plans to clone successful layout logic.
- **SECTION HISTORY:** Before creating a new section, check if an existing `ag-` section can be adapted with a new schema setting.
- **SPEED THROUGH STRUCTURE:** Strictly follow BEM-lite and scoped CSS so that "bulldozing" a section into a new template never breaks existing layouts.

---

---

## 🏗️ 10. Advanced Scaling Techniques (The Funnel Library)
To achieve maximum "Bulldoze" speed with the consistency of a high-end agency:
- **STANDARDIZED SETTINGS DICTIONARY (SSD):** Reuse setting IDs across different sections (e.g., `ag_hero_title`, `ag_cta_link`, `ag_primary_color`). This ensures that swapping a section preserves existing configuration mapping.
- **BLOCK-FIRST ARCHITECTURE:** Prioritize using `blocks` within sections for sub-elements (e.g., trust badges, feature lists). This allows for dynamic reordering and addition of elements directly in the Theme Editor sidebar.
- **GITHUB "COMMIT" TEMPLATES:** Treat the Git history as a template library. Use descriptive commit messages (e.g., `Template: High-Converting Sales Page V1`) to allow for quick roll-backs or cloning of successful funnel layouts to new branches/products.
- **DEVICE VISIBILITY TOGGLES:** Every major element or block must include a "Show on Mobile" and "Show on Desktop" checkbox in the schema to give the USER full control over responsive layout overrides.

---

## 🛡️ 11. Visual Regression & Content Continuity (The "Solid State" Rule)
To prevent accidental layout shifts or disappearing content during "Full Control" upgrades:
- **NO VISUAL REGRESSIONS:** Updates must preserve the exact original layout, spacing, and design of existing sections unless a visual redesign is explicitly requested.
- **CSS MASTER-OVER-LOCAL:** Prioritize styling via the master `assets/ag-custom.css`. Avoid adding duplicate or overriding `<style>` tags within Liquid sections that clash with existing grid or flex layouts.
- **HTML STRUCTURE STABILITY:** When "Schema-fying" a section, the HTML template structure and CSS classes must remain identical to the original version to ensure compatibility with the existing CSS system.
- **BLOCK FALLBACK LOGIC:** When moving a section from hardcoded to block-based, the schema MUST include default values (text, SVGs, colors) that replicate the original content. This ensures the section never appears "empty" or "broken" to the USER upon deployment.
- **AUDIT BEFORE PUSH:** Before declaring a section "Upgraded," the agent must verify: *"Is every original icon and text still present and in its original position?"*

---

**Failure to follow these guidelines results in "Code Mess" (leaks, regressions, or broken checkouts). Stop and clarify if unsure.**
