# Implementation Plan: Knee Massager Page Visual Updates

This document outlines the detailed plan to update the Knee Massager page into a high-converting, distraction-free sales funnel page, replicating a proven "Russell Brunson-style" layout and premium visual theme.

## Progress Checklist

### Phase 0: The "Bulldoze" Prep (Schema & Control Mapping)
- [ ] **Standardized IDs (SSD):** Define consistent setting IDs (e.g., `ag_hero_title`, `ag_cta_link`) for all new sections to ensure "Bulldoze" compatibility.
- [ ] **Block-First Architecture:** Re-plan the 3-Step Process, Trust Badges, and FAQ as dynamic **Blocks** for reordering in the Theme Editor.
- [ ] **Visibility Toggles:** Add `show_on_mobile` and `show_on_desktop` checkboxes to every section schema for responsive control.
- [ ] **Checkout Bypass Toggle:** Add an `enable_direct_checkout` setting to the Hero and Main Offer sections.
- [ ] **Typography Sliders:** Map `font_size_mobile` and `font_size_desktop` settings to all headlines to allow for manual sizing adjustments.

### Phase 1: Design System & Visual Theme Setup
- [x] **Colors:** Configure backgrounds, premium accents (`#F4D03F`), Trust Green (`#3CB371`), Amber (`#F59E0B`), Red (`#EF4444` to `#CF3F5C`), and Brand Black (`#1F1F1F`).
- [x] **Typography:** Set base font to 'Outfit'/'Inter'. Implement `.heading-premium` utility class.
- [x] **Textures & Effects:** 
  - [x] Implement `.glass` and `.glass-dark` classes for glassmorphism.
  - [x] Implement `.bg-dot-grid` utility.
  - [x] Implement `.bg-glow-blob` for atmospheric lighting.
- [x] **Animations & Motion:**
  - [x] Implement `.animate-on-scroll` with organic bezier curve.
  - [x] Implement staggered delays (`stagger-1` to `stagger-5`).
  - [x] Implement CTA slow premium glow pulse animation.

### Phase 2: Page Structure & Layout Implementation (Top-to-Bottom Flow)
- [x] **1. Global Navigation:** Remove all headers, nav bars, and external links at the top.
- [ ] **2. Combined "Hero" Experience:**
  - [ ] Build top section (full-width, landscape text layout, no button initially).
  - [ ] Build "Cost of Waiting" visual section underneath.
  - [ ] Add the Hook CTA immediately following the problem visualization.
- [ ] **3. Trust & Process:**
  - [ ] Add Trust Badges strip.
  - [x] Add 3-Step Process (horizontal layout with icons).
- [ ] **4. Main Offer Section:** 
  - [ ] Build a massive, highly-styled "Irresistible Offer" box wrapping the core deliverable.
- [ ] **5. Comparison / Why We Are Better:** 
  - [ ] Implement "Us vs. Them" table or checklist.
- [ ] **6. FAQ & Hidden Exits:** 
  - [ ] Create an accordion-style FAQ component with a subtle bottom hidden exit link.
- [ ] **7. Minimal Footer:** 
  - [ ] Add ultra-thin footer with copyright and legal info.

### Phase 3: Advanced CRO & Performance Injection
- [ ] **1. Frictionless Checkout Bypassing:** Recode primary CTA buttons (Green `#3CB371`) to skip the cart drawer and jump straight to checkout.
- [ ] **2. Sticky Mobile CTA:** Implement a `.sticky-cta-bar` at the bottom of the screen that triggers after the Hero section.
- [x] **3. Performance Load:** Strip heavy inactive native Shopify javascript assets from the funnel layout for instant load speeds.

---

## Detailed Guidelines

### 1. DESIGN SYSTEM & VISUAL THEME
**Colors & Palette:**
*   **Backgrounds:** Clean white/slate backgrounds with high contrast.
*   **Premium Accents:** Use a bright energetic yellow for primary accents (`#F4D03F`) with a subtle glow effect (`rgba(244, 208, 63, 0.4)`).
*   **Trust & Warning:** Use Trust Green (`#3CB371`) for guarantees, Amber (`#F59E0B`) for stage 1 warnings, and bold Red (`#EF4444` to `#CF3F5C`) for critical pain points/warnings.
*   **Dark Elements:** Brand Black (`#1F1F1F`).

**Typography:**
*   **Base Font:** 'Outfit', 'Inter', or similar modern sans-serif.
*   **Headings:** Implement a custom `.heading-premium` utility class. All major section headers should be **Bold/Black weight, tracking-tighter (letter-spacing), uppercase, and italicized**. 
*   *Example:* `<h2 className="text-4xl md:text-6xl font-black leading-tight tracking-tighter uppercase italic text-center">Your <span className="text-red-600">Pain Point</span> Here</h2>`

**Textures & Effects:**
*   **Glassmorphism:** Use a `.glass` class for cards (`bg-white/70 backdrop-blur-[12px] border border-black/10 shadow-sm`) and a `.glass-dark` class for dark sections.
*   **Dot Grids:** Implement a `.bg-dot-grid` utility using a radial gradient (light border color dots on transparent background, size 24px).
*   **Atmospheric Lighting:** Use `.bg-glow-blob` (absolute rounded-full, heavy blur `blur-[120px]`) behind key offers to create a premium radiant effect.

**Animations & Motion:**
*   **Scroll Reveals:** Use a `.animate-on-scroll` class (`opacity-0 translate-y-[15px] transition-all duration-700`) using an organic bezier curve: `cubic-bezier(0.21, 0.45, 0.32, 0.9)`. Use staggered delays (`stagger-1` to `stagger-5`).
*   **CTA Pulsing:** Buttons and main offers should have a slow, premium glow pulse animation that scales slightly (1.02) and drops a shadow of the accent color.

### 2. PAGE STRUCTURE & LAYOUT (Russell Brunson Funnel Style)
**1. Global Navigation (None)**
*   Remove all headers, navigation bars, and external links at the top of the page.

**2. The Combined "Hero" Experience**
*   **Top Section:** Full-width, landscaped text layout. Do NOT include a button here. Focus purely on the hook and the problem.
*   **"Cost of Waiting" Section:** Directly beneath the text, insert a highly visual, data-driven section (like a decay chart or staged problem timeline: Stage 1 [Stable], Stage 2 [Accelerating], Stage 3 [Detrimental]).
*   **The Hook CTA:** Immediately following the problem visualization, drop the first Call To Action.

**3. Trust & Process**
*   **Trust Badges:** A strip of high-contrast client logos or trust badges (e.g., "5-Star Rated", "Licensed & Insured").
*   **3-Step Process:** A simplified, icon-driven horizontal layout: 1. Identify Problem -> 2. Schedule Consult -> 3. We Fix It.

**4. The Main Offer Section**
*   Create a massive, highly-styled "Irresistible Offer" box completely wrapping the core deliverable. 
*   *Format Example:* "The Ultimate [Service] Audit ($297 Value - Yours FREE)".
*   Use the dark glassmorphism (`.glass-dark`) or a heavy border with the atmospheric glow behind it to make it pop off the screen.

**5. Comparison / Why We Are Better**
*   Include a "Us vs. Them" comparison table or checklist utilizing the Trust Green for green checkmarks and muted grays for the competitors' red X's.

**6. FAQ & Hidden Exits**
*   A clean accordion-style FAQ section handling the top 4-5 objections. 
*   Include legal/license text subtly at the bottom of the FAQs, embedding a discreet/hidden link back to the main website if they absolutely need to leave the funnel.

**7. Minimal Footer**
*   Extremely thin, bottom-pinned line.
*   Format: `© [Year] [COMPANY NAME] • [LICENSE/LEGAL INFO]`. No other links.
