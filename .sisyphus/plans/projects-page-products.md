# Projects Page Real Product Integration Plan

## TL;DR

> **Quick Summary**: Replace the generic product showcase in `projects_stitch.html` with four real student products, lightly polish the English copy from `内容.txt`, wire in the local product images, and adapt the towel product to a 1-main-image + 4-thumbnail layout.
>
> **Deliverables**:
> - Update `projects_stitch.html` so the four visible product sections are: Humidifier, Smart Control Center, Desk Lamp, and Cotton Antibacterial Towel
> - Remove the duplicate standalone humidifier section after the real 4-product showcase is in place
> - Keep the existing overall page style, hero / nav / footer structure, and engineering section continuity
>
> **Estimated Effort**: Medium
> **Parallel Execution**: YES - 3 waves
> **Critical Path**: Task 1 → Task 2 → Task 7 → Task 8 → Task 9 → Task 10

---

## Context

### Original Request
The user is building a company-style website page for a workplace English assignment. The target file is `projects_stitch.html`. The page already has a basic framework. Product-writing requirements are in `projects.txt`, the four members' product copy is in `内容.txt`, and the page must be updated so it shows four real products with matching local images. The towel product has five images and needs more space than the single-image products.

### Interview Summary
**Key Discussions**:
- Communication should be in Chinese.
- This session should produce a work plan, not direct implementation.
- Product copy should stay close to the original wording, with only light grammar / webpage-tone polishing.
- Approved product order: 1) Smart Desktop Humidifier 2) OmniHub Smart Control Center 3) Wireless Charging Desk Lamp 4) Cotton Antibacterial Towel.
- Approved towel layout: 1 main image + 4 smaller thumbnails below.
- Scope choice: replace the current generic showcase with the 4 real products while keeping the overall page style.
- Verification choice: page/browser validation only; no automated test setup.

**Research Findings**:
- `projects_stitch.html:154-214` contains four generic showcase cards that are the main replacement target.
- `projects_stitch.html:216-251` contains an additional standalone humidifier section that would duplicate product #1 if left in place.
- `projects_stitch.html:252-287` contains an engineering section that can remain after the product showcase.
- `projects.txt:1-8` defines the preferred copy structure: appearance / function / price, with flexibility to omit some appearance subpoints.
- `内容.txt:1-10` contains the humidifier copy.
- `内容.txt:13-57` contains the smart control center copy.
- `内容.txt:59-80` contains the towel copy.
- `内容.txt:81-103` contains the desk lamp copy.
- Local confirmed images exist in the workspace: `humidifier.png`, `智能中控台.png`, `台灯.jpg`, `毛巾材料1.jpg`, `毛巾材料2.jpg`, `毛巾产品图.jpg`, `毛巾产品图2.jpg`, `毛巾总图.jpg`.
- The repository is a static HTML site with no automated test infrastructure.

### Metis Review
**Identified Gaps** (addressed):
- Duplicate-product risk resolved by planning explicit removal of the old standalone humidifier section after the 4-card showcase is populated.
- Verification ambiguity resolved by planning stable section hooks (`id` / `data-*`) for browser assertions.
- Scope-creep risk resolved by explicitly freezing nav, footer, engineering section purpose, and overall visual style.
- Towel gallery risk resolved by adding a dedicated CSS/layout task before content population.

---

## Work Objectives

### Core Objective
Turn `projects_stitch.html` from a generic product-demo page into a finished four-product assignment page that reflects the real team products, uses the local images correctly, and keeps the existing premium layout style intact.

### Concrete Deliverables
- `projects_stitch.html` shows exactly 4 real products in the approved order.
- Each product uses the correct local image file(s).
- The towel product uses one large image plus four thumbnails below it.
- The previous extra humidifier block is removed to avoid duplication.
- The engineering section remains after the product showcase without broken spacing.

### Definition of Done
- [ ] `projects_stitch.html` contains the four approved product names and none of the generic placeholder product names.
- [ ] All product image `src` values point to existing local files in the workspace.
- [ ] Browser validation confirms the four product sections render in order and the towel section shows 5 images in the approved layout.
- [ ] The page still retains working hero, nav, footer, and engineering section structure.

### Must Have
- Real product headings and copy derived from `内容.txt`
- Content structure guided by `projects.txt`
- Light copy polishing only
- Stable selectors/hooks for page validation
- Local image integration only

### Must NOT Have (Guardrails)
- No new frameworks, build tools, or JavaScript widgets
- No unrelated redesign of nav, footer, or other pages
- No extra fifth product section
- No carousel/lightbox for the towel gallery
- No heavy rewriting of the student copy into entirely new marketing copy

---

## Verification Strategy (MANDATORY)

> **ZERO HUMAN INTERVENTION** - ALL verification is agent-executed. No exceptions.

### Test Decision
- **Infrastructure exists**: NO
- **Automated tests**: None
- **Framework**: none
- **Primary verification mode**: browser/page validation only

### QA Policy
Every task includes agent-executed QA scenarios. Evidence is saved under `.sisyphus/evidence/`.

- **Frontend/UI**: Use Playwright against `file:///E:/github/my-work/projects_stitch.html`
- **Static file checks**: Use Bash / PowerShell commands to confirm file existence, selector presence, and duplicate-removal conditions
- **Image validation**: Verify both file existence and in-browser image rendering (`naturalWidth > 0`)

---

## Execution Strategy

### Parallel Execution Waves

> Maximize throughput while respecting the fact that all final output lands in one HTML file. Parallel tasks should work on non-overlapping concerns and merge carefully.

```text
Wave 1 (Foundation - start immediately)
├── Task 1: Update page metadata + hero/product intro copy [quick]
├── Task 2: Convert generic showcase into four stable real-product shells [quick]
└── Task 3: Add towel-gallery/stable-hook support styles [quick]

Wave 2 (Populate the four real product cards)
├── Task 4: Fill humidifier product card [writing]
├── Task 5: Fill smart control center product card [writing]
├── Task 6: Fill desk lamp product card [writing]
└── Task 7: Fill towel product card with 5-image gallery [writing]

Wave 3 (Cleanup + polish)
├── Task 8: Remove duplicate standalone humidifier section and preserve engineering transition [quick]
├── Task 9: Sweep alt text, image paths, labels, and content-length polish [quick]
└── Task 10: Final in-file consistency and browser-layout pass [unspecified-high]

Wave FINAL (After ALL tasks — 4 parallel reviews)
├── Task F1: Plan compliance audit (oracle)
├── Task F2: Code quality review (unspecified-high)
├── Task F3: Real manual QA (unspecified-high)
└── Task F4: Scope fidelity check (deep)

Critical Path: 1 → 2 → 7 → 8 → 9 → 10 → F1-F4
Parallel Speedup: ~55% faster than single-threaded editing
Max Concurrent: 4
```

### Dependency Matrix

- **1**: Blocked By none → Blocks 10
- **2**: Blocked By none → Blocks 4, 5, 6, 7, 8, 9, 10
- **3**: Blocked By none → Blocks 7, 9, 10
- **4**: Blocked By 2 → Blocks 8, 9, 10
- **5**: Blocked By 2 → Blocks 9, 10
- **6**: Blocked By 2 → Blocks 9, 10
- **7**: Blocked By 2, 3 → Blocks 9, 10
- **8**: Blocked By 4 → Blocks 9, 10
- **9**: Blocked By 4, 5, 6, 7, 8 → Blocks 10
- **10**: Blocked By 1, 2, 3, 4, 5, 6, 7, 8, 9 → Blocks F1, F2, F3, F4
- **F1**: Blocked By 10 → Final approval gate
- **F2**: Blocked By 10 → Final approval gate
- **F3**: Blocked By 10 → Final approval gate
- **F4**: Blocked By 10 → Final approval gate

### Agent Dispatch Summary

- **Wave 1**: **3 agents** — T1 → `quick`, T2 → `quick`, T3 → `quick`
- **Wave 2**: **4 agents** — T4-T7 → `writing`
- **Wave 3**: **3 agents** — T8 → `quick`, T9 → `quick`, T10 → `unspecified-high`
- **FINAL**: **4 agents** — F1 → `oracle`, F2 → `unspecified-high`, F3 → `unspecified-high`, F4 → `deep`

---

## TODOs

- [x] 1. Update page metadata and top-level introduction for the real product page

  **What to do**:
  - Review the current `<title>`, hero heading, and hero intro paragraph in `projects_stitch.html`.
  - Keep the overall premium style, but adjust the wording so the page clearly presents real team products rather than abstract futuristic placeholder products.
  - Ensure the hero still supports the approved four-product showcase and does not mention placeholder-only concepts.

  **Must NOT do**:
  - Do not redesign nav, footer, or hero layout.
  - Do not turn the hero into a long text block.

  **Recommended Agent Profile**:
  - **Category**: `quick`
    - Reason: This is a tightly scoped wording update inside an existing HTML structure.
  - **Skills**: [`brainstorming`]
    - `brainstorming`: Helps preserve the approved tone and scope decisions from the design discussion.
  - **Skills Evaluated but Omitted**:
    - `frontend-design`: Omitted because the task is wording alignment, not a visual redesign.

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1 (with Tasks 2, 3)
  - **Blocks**: 10
  - **Blocked By**: None

  **References**:

  **Pattern References**:
  - `projects_stitch.html:150-153` - Existing hero structure to preserve while updating wording.

  **API/Type References**:
  - `projects.txt:1-8` - Indicates the product-info structure expected across the page.

  **Test References**:
  - `projects_stitch.html:145-155` - Page entry area that should still flow naturally into the product showcase after edits.

  **External References**:
  - None required.

  **WHY Each Reference Matters**:
  - `projects_stitch.html:150-153` shows the exact text nodes to adjust without changing the hero layout.
  - `projects.txt:1-8` anchors the page toward practical product presentation rather than abstract marketing.

  **Acceptance Criteria**:
  - [ ] Hero heading and intro still exist and are readable in English.
  - [ ] Hero copy no longer conflicts with the four real products.
  - [ ] The section spacing/layout is unchanged.

  **QA Scenarios**:
  ```
  Scenario: Hero wording renders correctly
    Tool: Playwright
    Preconditions: Open local file `file:///E:/github/my-work/projects_stitch.html`
    Steps:
      1. Load the page at 1440x900.
      2. Locate `main section h1` within the first hero section.
      3. Assert the heading is non-empty and the paragraph below it is non-empty.
      4. Capture a screenshot of the hero area.
    Expected Result: Updated hero text is visible and layout matches the original hero block structure.
    Failure Indicators: Empty heading, overlapping text, unexpected line wrapping that breaks layout.
    Evidence: .sisyphus/evidence/task-1-hero-render.png

  Scenario: Hero still flows into showcase section
    Tool: Playwright
    Preconditions: Same local page open
    Steps:
      1. Scroll from the hero to the first product card.
      2. Assert there is a visible transition with no blank oversized gap and no duplicate introductory copy.
    Expected Result: Hero leads directly into the real product showcase naturally.
    Failure Indicators: Huge whitespace gap, repeated intro text, broken stacking.
    Evidence: .sisyphus/evidence/task-1-hero-to-showcase.png
  ```

  **Evidence to Capture:**
  - [ ] `task-1-hero-render.png`
  - [ ] `task-1-hero-to-showcase.png`

  **Commit**: NO

- [x] 2. Convert the four generic showcase cards into four stable real-product shells

  **What to do**:
  - Replace the four placeholder product names/categories/descriptions in `projects_stitch.html:157-214` with the four approved real products in this exact order: Humidifier, Smart Control Center, Desk Lamp, Cotton Antibacterial Towel.
  - Keep the alternating Z-pattern card layout already used by the page.
  - Add stable section identifiers such as `id="product-humidifier"`, `id="product-control-center"`, `id="product-desk-lamp"`, `id="product-towel"` or equivalent `data-product` hooks for validation.
  - Leave detailed long-form copy population for Tasks 4-7.

  **Must NOT do**:
  - Do not add a fifth product.
  - Do not collapse the 4 cards into a different page architecture.

  **Recommended Agent Profile**:
  - **Category**: `quick`
    - Reason: This is structural relabeling and hook setup inside a single HTML file.
  - **Skills**: [`smart-explore`]
    - `smart-explore`: Useful for locating and mapping the repeated product-card structure efficiently.
  - **Skills Evaluated but Omitted**:
    - `frontend-design`: Omitted because the layout pattern is already chosen and should stay intact.

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1 (with Tasks 1, 3)
  - **Blocks**: 4, 5, 6, 7, 8, 9, 10
  - **Blocked By**: None

  **References**:

  **Pattern References**:
  - `projects_stitch.html:157-214` - Existing four-card showcase to reuse structurally.
  - `projects_stitch.html:158`, `172`, `186`, `200` - Existing alternating card wrappers showing the left/right rhythm to preserve.

  **API/Type References**:
  - `内容.txt:1-103` - Source of the four real products and their names.

  **Test References**:
  - `projects_stitch.html:155-214` - Validation target for counting the final 4 product cards.

  **External References**:
  - None required.

  **WHY Each Reference Matters**:
  - `projects_stitch.html:157-214` is the exact replacement zone.
  - `内容.txt:1-103` confirms the four real products that should occupy those slots.

  **Acceptance Criteria**:
  - [ ] There are exactly four visible real-product showcase cards in the main showcase block.
  - [ ] Generic product titles like `FrontierWatch Series 2`, `LinkView AR Glasses`, `Guardian Smart Lock`, and `Aura Smart Hub` are removed from the file.
  - [ ] Each card has a stable unique hook for browser validation.

  **QA Scenarios**:
  ```
  Scenario: Four real product shells exist in correct order
    Tool: Playwright
    Preconditions: Open `file:///E:/github/my-work/projects_stitch.html`
    Steps:
      1. Query the showcase cards using their new `id` or `data-product` hooks.
      2. Assert exactly 4 products are found.
      3. Assert visible heading order is: Smart Desktop Humidifier → OmniHub Smart Control Center → Wireless Charging Desk Lamp → Cotton Antibacterial Towel.
    Expected Result: Four product shells render in the approved order.
    Failure Indicators: Missing card, wrong order, duplicate headings.
    Evidence: .sisyphus/evidence/task-2-product-order.png

  Scenario: Generic placeholder names are absent
    Tool: Bash (PowerShell)
    Preconditions: `projects_stitch.html` saved locally
    Steps:
      1. Run a text search for `FrontierWatch`, `LinkView`, `Guardian`, and `Aura` in `projects_stitch.html`.
      2. Assert zero matches for all four names.
    Expected Result: No generic placeholder product names remain.
    Failure Indicators: Any placeholder name still exists in the file.
    Evidence: .sisyphus/evidence/task-2-placeholder-check.txt
  ```

  **Evidence to Capture:**
  - [ ] `task-2-product-order.png`
  - [ ] `task-2-placeholder-check.txt`

  **Commit**: NO

- [x] 3. Add towel-gallery support styles and stable gallery hooks

  **What to do**:
  - Add only the minimal HTML/CSS support needed so the towel card can display one large main image with four smaller thumbnails below.
  - Reuse the existing aesthetic language (rounded corners, soft glass card feel, generous spacing).
  - Ensure the gallery can collapse responsively on narrow screens without overflowing horizontally.
  - Add stable selectors such as `.towel-main-image`, `.towel-thumb-grid`, and `.towel-thumb` for validation.

  **Must NOT do**:
  - Do not implement a carousel or thumbnail-click switching behavior.
  - Do not add JavaScript.

  **Recommended Agent Profile**:
  - **Category**: `quick`
    - Reason: Small contained style/layout support inside existing HTML/CSS.
  - **Skills**: [`frontend-design`]
    - `frontend-design`: Helps maintain visual consistency for the gallery treatment without redesigning the whole page.
  - **Skills Evaluated but Omitted**:
    - `playwright`: Omitted for implementation itself; it is only needed for verification.

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1 (with Tasks 1, 2)
  - **Blocks**: 7, 9, 10
  - **Blocked By**: None

  **References**:

  **Pattern References**:
  - `projects_stitch.html:94-115` - Existing custom style block where minimal support styles should be added.
  - `projects_stitch.html:217-248` - Existing single-product image/text section that shows the current visual language.

  **API/Type References**:
  - None required.

  **Test References**:
  - `毛巾总图.jpg`, `毛巾材料1.jpg`, `毛巾材料2.jpg`, `毛巾产品图.jpg`, `毛巾产品图2.jpg` - Assets the gallery must support.

  **External References**:
  - None required.

  **WHY Each Reference Matters**:
  - `projects_stitch.html:94-115` is the safe place to add minimal custom CSS.
  - `projects_stitch.html:217-248` helps mirror the current image-container polish.

  **Acceptance Criteria**:
  - [ ] The file contains a clear main-image region and a thumbnail-grid region for the towel product.
  - [ ] The gallery remains within the card width at desktop and mobile widths.
  - [ ] No JavaScript is introduced.

  **QA Scenarios**:
  ```
  Scenario: Towel gallery containers render with correct structure
    Tool: Playwright
    Preconditions: Open local projects page
    Steps:
      1. Scroll to the towel section.
      2. Assert one element matching `.towel-main-image img` exists.
      3. Assert four elements matching `.towel-thumb-grid .towel-thumb img` exist.
    Expected Result: Gallery structure exists with 1 main image and 4 thumbnails.
    Failure Indicators: Missing main image region, wrong thumbnail count, broken DOM nesting.
    Evidence: .sisyphus/evidence/task-3-gallery-structure.png

  Scenario: Towel gallery does not overflow on mobile width
    Tool: Playwright
    Preconditions: Page open
    Steps:
      1. Set viewport to 390x844.
      2. Scroll to the towel section.
      3. Assert `document.documentElement.scrollWidth === document.documentElement.clientWidth`.
    Expected Result: No horizontal overflow introduced by the towel gallery.
    Failure Indicators: Horizontal scroll appears or thumbnails overflow card width.
    Evidence: .sisyphus/evidence/task-3-gallery-mobile.png
  ```

  **Evidence to Capture:**
  - [ ] `task-3-gallery-structure.png`
  - [ ] `task-3-gallery-mobile.png`

  **Commit**: NO

- [x] 4. Fill the humidifier product card with polished copy and the confirmed local image

  **What to do**:
  - Use `内容.txt:1-10` as the source.
  - Keep the approved structure of appearance / features / price.
  - Use `humidifier.png` as the product image.
  - Lightly polish the wording for grammar and consistent website tone, but keep the meaning and examples from the student copy.
  - Ensure the byline / attribution is either retained neatly or absorbed into the section naturally without sounding repetitive.

  **Must NOT do**:
  - Do not rewrite the product into a totally different marketing voice.
  - Do not use any image other than `humidifier.png`.

  **Recommended Agent Profile**:
  - **Category**: `writing`
    - Reason: The core challenge is polishing and structuring content while respecting the original wording.
  - **Skills**: [`brainstorming`]
    - `brainstorming`: Keeps the content aligned with the agreed design constraints and tone.
  - **Skills Evaluated but Omitted**:
    - `frontend-design`: Omitted because the card layout already exists.

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 2 (with Tasks 5, 6, 7)
  - **Blocks**: 8, 9, 10
  - **Blocked By**: 2

  **References**:

  **Pattern References**:
  - `projects_stitch.html:216-248` - Existing humidifier section content that can guide the final wording density and block structure.
  - `projects_stitch.html:157-170` - Card structure that the humidifier card should occupy in the main 4-product showcase.

  **API/Type References**:
  - `内容.txt:1-10` - Source humidifier copy.
  - `projects.txt:1-8` - Preferred information grouping.

  **Test References**:
  - `humidifier.png` - Confirmed local image asset for this card.

  **External References**:
  - None required.

  **WHY Each Reference Matters**:
  - `内容.txt:1-10` provides the actual content to preserve.
  - `projects_stitch.html:157-170` shows the exact target card shape for the first product.

  **Acceptance Criteria**:
  - [ ] Humidifier card heading reads `Smart Desktop Humidifier`.
  - [ ] The card includes appearance, features, and price content in readable English.
  - [ ] The card image source is `humidifier.png`.

  **QA Scenarios**:
  ```
  Scenario: Humidifier section shows correct title, image, and price content
    Tool: Playwright
    Preconditions: Open local projects page
    Steps:
      1. Scroll to `#product-humidifier` or equivalent hook.
      2. Assert heading text contains `Smart Desktop Humidifier`.
      3. Assert the image `src` ends with `humidifier.png`.
      4. Assert visible text contains `under £20` or equivalent polished price wording.
    Expected Result: Humidifier card is fully populated with the correct image and core content.
    Failure Indicators: Missing image, missing price, wrong title.
    Evidence: .sisyphus/evidence/task-4-humidifier-card.png

  Scenario: Humidifier image loads successfully
    Tool: Playwright
    Preconditions: Same page open
    Steps:
      1. Select the humidifier image element.
      2. Evaluate `img.complete && img.naturalWidth > 0`.
    Expected Result: The humidifier image has loaded successfully.
    Failure Indicators: Broken image icon or `naturalWidth === 0`.
    Evidence: .sisyphus/evidence/task-4-humidifier-image.txt
  ```

  **Evidence to Capture:**
  - [ ] `task-4-humidifier-card.png`
  - [ ] `task-4-humidifier-image.txt`

  **Commit**: NO

- [x] 5. Fill the smart control center card with structured copy and local image

  **What to do**:
  - Use `内容.txt:13-57` as the source.
  - Condense the product into a webpage-friendly card without losing the key areas: appearance/materials, integration/control/security/energy functions, and price tiers.
  - Use `智能中控台.png` as the product image.
  - Keep product naming consistent as `OmniHub Smart Control Center`.

  **Must NOT do**:
  - Do not dump the raw long proposal text without editing for webpage readability.
  - Do not add features not mentioned in the source text.

  **Recommended Agent Profile**:
  - **Category**: `writing`
    - Reason: This is content condensation and polishing work.
  - **Skills**: [`brainstorming`]
    - `brainstorming`: Preserves the approved content-treatment boundaries.
  - **Skills Evaluated but Omitted**:
    - `doc-coauthoring`: Omitted because the deliverable is webpage copy, not a long-form document.

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 2 (with Tasks 4, 6, 7)
  - **Blocks**: 9, 10
  - **Blocked By**: 2

  **References**:

  **Pattern References**:
  - `projects_stitch.html:172-184` - The second product card shell target.
  - `projects_stitch.html:231-244` - Existing sub-block pattern for sectioned product information.

  **API/Type References**:
  - `内容.txt:13-57` - Source control-center copy.
  - `projects.txt:1-8` - Required information categories.

  **Test References**:
  - `智能中控台.png` - Confirmed image asset for this card.

  **External References**:
  - None required.

  **WHY Each Reference Matters**:
  - `内容.txt:13-57` contains the densest source copy and defines what needs condensing.
  - `projects_stitch.html:172-184` is the correct target shell and preserves the alternating layout.

  **Acceptance Criteria**:
  - [ ] Heading reads `OmniHub Smart Control Center`.
  - [ ] Core copy mentions whole-home integration, dual control modes, and security/energy value.
  - [ ] Price information includes Basic and Pro editions or a compact equivalent.
  - [ ] Image source is `智能中控台.png`.

  **QA Scenarios**:
  ```
  Scenario: Control center card includes key selling points
    Tool: Playwright
    Preconditions: Open local page
    Steps:
      1. Scroll to `#product-control-center`.
      2. Assert heading contains `OmniHub Smart Control Center`.
      3. Assert visible text contains references to integration / voice or touch control / security.
      4. Assert the image `src` ends with `智能中控台.png`.
    Expected Result: Card displays the product identity and core value points clearly.
    Failure Indicators: Wrong title, missing major features, wrong image.
    Evidence: .sisyphus/evidence/task-5-control-center-card.png

  Scenario: Price tier wording is preserved in compact form
    Tool: Playwright
    Preconditions: Same page open
    Steps:
      1. In the control center section, locate the price block.
      2. Assert the text contains `Basic` and `Pro` (or a clearly equivalent tier label pair).
    Expected Result: The tiered pricing survives the webpage condensation.
    Failure Indicators: Price section missing or both tiers omitted.
    Evidence: .sisyphus/evidence/task-5-control-center-price.txt
  ```

  **Evidence to Capture:**
  - [ ] `task-5-control-center-card.png`
  - [ ] `task-5-control-center-price.txt`

  **Commit**: NO

- [x] 6. Fill the desk lamp card with concise feature-led copy and the local lamp image

  **What to do**:
  - Use `内容.txt:81-103` as the source.
  - Present the desk lamp as a modern home-office / study product.
  - Retain the important features: adjustable brightness, warm/cool modes, 15W wireless charging, eye-friendly LED, 360-degree arm, touch controls, and unit price.
  - Use `台灯.jpg` as the product image.

  **Must NOT do**:
  - Do not omit the wireless charging feature.
  - Do not replace the confirmed image with any unrelated file.

  **Recommended Agent Profile**:
  - **Category**: `writing`
    - Reason: Copy shaping is the main concern.
  - **Skills**: [`brainstorming`]
    - `brainstorming`: Keeps the copy within the agreed tone and scope.
  - **Skills Evaluated but Omitted**:
    - `frontend-design`: Omitted because no layout change beyond content fill is needed.

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 2 (with Tasks 4, 5, 7)
  - **Blocks**: 9, 10
  - **Blocked By**: 2

  **References**:

  **Pattern References**:
  - `projects_stitch.html:186-198` - The third product card shell target.

  **API/Type References**:
  - `内容.txt:81-103` - Source desk-lamp copy.
  - `projects.txt:1-8` - Product-info grouping guidance.

  **Test References**:
  - `台灯.jpg` - Confirmed local image asset.

  **External References**:
  - None required.

  **WHY Each Reference Matters**:
  - `内容.txt:81-103` has the final source content and feature list that must remain recognizable.
  - `projects_stitch.html:186-198` gives the target slot in the alternating sequence.

  **Acceptance Criteria**:
  - [ ] Heading reads `Wireless Charging Desk Lamp`.
  - [ ] Copy includes lighting adjustment plus wireless charging.
  - [ ] Price `$25.99` (or equivalent polished unit-price wording) is present.
  - [ ] Image source is `台灯.jpg`.

  **QA Scenarios**:
  ```
  Scenario: Desk lamp card includes charging and lighting features
    Tool: Playwright
    Preconditions: Open local page
    Steps:
      1. Scroll to `#product-desk-lamp`.
      2. Assert heading contains `Wireless Charging Desk Lamp`.
      3. Assert visible text mentions `15W` or `wireless charging` and mentions adjustable brightness/light modes.
      4. Assert image `src` ends with `台灯.jpg`.
    Expected Result: The card clearly communicates both lamp and charging functions.
    Failure Indicators: Missing charging feature, wrong image, empty content.
    Evidence: .sisyphus/evidence/task-6-desk-lamp-card.png

  Scenario: Desk lamp price is visible
    Tool: Playwright
    Preconditions: Same page open
    Steps:
      1. Locate the price area inside the desk lamp card.
      2. Assert the text contains `$25.99`.
    Expected Result: Unit price is displayed clearly.
    Failure Indicators: Price omitted or incorrect.
    Evidence: .sisyphus/evidence/task-6-desk-lamp-price.txt
  ```

  **Evidence to Capture:**
  - [ ] `task-6-desk-lamp-card.png`
  - [ ] `task-6-desk-lamp-price.txt`

  **Commit**: NO

- [x] 7. Fill the towel card with 5-image gallery and structured product copy

  **What to do**:
  - Use `内容.txt:59-80` as the source.
  - Present the towel with the approved main image + 4-thumbnail layout.
  - Use all 5 towel images: `毛巾总图.jpg` as the recommended main image, plus `毛巾材料1.jpg`, `毛巾材料2.jpg`, `毛巾产品图.jpg`, `毛巾产品图2.jpg` as thumbnails unless implementation review shows a better mapping while keeping 1+4 structure.
  - Preserve the key points: Xinjiang long-staple cotton raw material, antibacterial safety, softness, absorbency, durability, quick-drying, and the multiple price options.

  **Must NOT do**:
  - Do not reduce the towel section to a single image.
  - Do not turn the section into an interactive gallery beyond static display.

  **Recommended Agent Profile**:
  - **Category**: `writing`
    - Reason: This combines content shaping with a fixed image-usage plan.
  - **Skills**: [`frontend-design`]
    - `frontend-design`: Ensures the 5-image presentation feels cohesive inside the existing premium card style.
  - **Skills Evaluated but Omitted**:
    - `playwright`: Omitted from implementation; used only for QA.

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 2 (with Tasks 4, 5, 6)
  - **Blocks**: 9, 10
  - **Blocked By**: 2, 3

  **References**:

  **Pattern References**:
  - `projects_stitch.html:200-214` - Fourth product card shell target.
  - `projects_stitch.html:94-115` - Custom style region where the supporting gallery styles live.

  **API/Type References**:
  - `内容.txt:59-80` - Source towel copy.
  - `projects.txt:1-8` - Product-info grouping guidance.

  **Test References**:
  - `毛巾总图.jpg`
  - `毛巾材料1.jpg`
  - `毛巾材料2.jpg`
  - `毛巾产品图.jpg`
  - `毛巾产品图2.jpg`

  **External References**:
  - None required.

  **WHY Each Reference Matters**:
  - `内容.txt:59-80` contains the only source for the towel's raw-material and antibacterial claims.
  - The 5 image files must all be wired correctly and validated explicitly.

  **Acceptance Criteria**:
  - [ ] Heading reads `Cotton Antibacterial Towel` or a very close polished equivalent.
  - [ ] One main towel image and four thumbnail images are present in the card.
  - [ ] Copy mentions raw material, antibacterial property, and multiple price options.
  - [ ] All 5 towel image paths point to existing local files.

  **QA Scenarios**:
  ```
  Scenario: Towel card shows all 5 approved images
    Tool: Playwright
    Preconditions: Open local page
    Steps:
      1. Scroll to `#product-towel`.
      2. Assert one `.towel-main-image img` exists.
      3. Assert four `.towel-thumb img` elements exist.
      4. Evaluate every towel image for `naturalWidth > 0`.
    Expected Result: Main image and all four thumbnails render correctly.
    Failure Indicators: Missing thumbnail, broken image, wrong count.
    Evidence: .sisyphus/evidence/task-7-towel-gallery.png

  Scenario: Towel copy preserves key feature and pricing information
    Tool: Playwright
    Preconditions: Same page open
    Steps:
      1. In the towel section, assert visible text mentions `Xinjiang` or `long-staple cotton`.
      2. Assert visible text mentions `99% antibacterial` or equivalent polished wording.
      3. Assert visible text includes at least two distinct towel prices.
    Expected Result: Source product identity and pricing survive the webpage version.
    Failure Indicators: Raw material missing, antibacterial claim missing, price block incomplete.
    Evidence: .sisyphus/evidence/task-7-towel-copy.txt
  ```

  **Evidence to Capture:**
  - [ ] `task-7-towel-gallery.png`
  - [ ] `task-7-towel-copy.txt`

  **Commit**: NO

- [x] 8. Remove the duplicate standalone humidifier section and preserve the post-showcase flow

  **What to do**:
  - Delete or fully repurpose the old standalone humidifier section at `projects_stitch.html:216-251` so the page does not show the humidifier twice.
  - Preserve a clean transition from the final towel product card into the engineering section.
  - Ensure spacing and decorative background continuity remain visually consistent after removal.

  **Must NOT do**:
  - Do not accidentally remove the engineering section.
  - Do not leave an empty container or large blank gap where the old humidifier section used to be.

  **Recommended Agent Profile**:
  - **Category**: `quick`
    - Reason: Focused cleanup inside one file.
  - **Skills**: [`smart-explore`]
    - `smart-explore`: Helps confirm the exact duplicate section boundaries before removal.
  - **Skills Evaluated but Omitted**:
    - `frontend-design`: Omitted because this is a cleanup task, not a new layout design.

  **Parallelization**:
  - **Can Run In Parallel**: NO
  - **Parallel Group**: Sequential after Task 4
  - **Blocks**: 9, 10
  - **Blocked By**: 4

  **References**:

  **Pattern References**:
  - `projects_stitch.html:216-251` - Duplicate humidifier block to remove.
  - `projects_stitch.html:252-287` - Engineering section that must remain immediately after cleanup.

  **API/Type References**:
  - None required.

  **Test References**:
  - `projects_stitch.html:214-253` - Transition region to validate after cleanup.

  **External References**:
  - None required.

  **WHY Each Reference Matters**:
  - `projects_stitch.html:216-251` is the exact duplicate-content risk flagged during planning.
  - `projects_stitch.html:252-287` defines the section that must survive untouched.

  **Acceptance Criteria**:
  - [ ] Only one humidifier product remains on the page.
  - [ ] No empty duplicate section remains between the showcase and engineering section.
  - [ ] The engineering section still renders directly after the product showcase area.

  **QA Scenarios**:
  ```
  Scenario: Duplicate humidifier block is removed
    Tool: Playwright
    Preconditions: Open local page
    Steps:
      1. Search the rendered page for `Smart Desktop Humidifier` headings.
      2. Assert exactly one visible match exists.
    Expected Result: Only the first showcase humidifier card remains.
    Failure Indicators: Two humidifier sections still visible.
    Evidence: .sisyphus/evidence/task-8-single-humidifier.txt

  Scenario: Engineering section follows showcase cleanly
    Tool: Playwright
    Preconditions: Same page open
    Steps:
      1. Scroll from the towel section into the next section.
      2. Assert the next major heading is `The Engineering Edge`.
      3. Capture a screenshot of the transition.
    Expected Result: The page flows directly from product showcase to engineering section without an empty card gap.
    Failure Indicators: Blank vertical hole, missing engineering heading, duplicate humidifier card.
    Evidence: .sisyphus/evidence/task-8-showcase-to-engineering.png
  ```

  **Evidence to Capture:**
  - [ ] `task-8-single-humidifier.txt`
  - [ ] `task-8-showcase-to-engineering.png`

  **Commit**: NO

- [x] 9. Sweep alt text, labels, image paths, and copy consistency across all four cards

  **What to do**:
  - Review all four product cards and ensure every image has meaningful alt text.
  - Confirm every image path matches the exact local filename, including Chinese filenames and extensions.
  - Normalize section labels / subheadings so the four cards feel coherent as one page.
  - Tighten any copy that is too long for the layout while staying within the “light polishing only” rule.

  **Must NOT do**:
  - Do not silently replace local filenames with guessed English aliases.
  - Do not introduce inconsistent heading hierarchies.

  **Recommended Agent Profile**:
  - **Category**: `quick`
    - Reason: Cross-card cleanup and consistency pass.
  - **Skills**: [`brainstorming`]
    - `brainstorming`: Keeps the polish bounded to the approved tone and no-rewrite rule.
  - **Skills Evaluated but Omitted**:
    - `code-reviewer`: Omitted because this is a content and asset consistency sweep, not a deep audit.

  **Parallelization**:
  - **Can Run In Parallel**: NO
  - **Parallel Group**: Wave 3 (with Tasks 8, 10 staged around dependencies)
  - **Blocks**: 10
  - **Blocked By**: 4, 5, 6, 7, 8

  **References**:

  **Pattern References**:
  - `projects_stitch.html:157-287` - Final product and engineering region to normalize.

  **API/Type References**:
  - `内容.txt:1-103` - Source wording to stay faithful to.

  **Test References**:
  - `humidifier.png`
  - `智能中控台.png`
  - `台灯.jpg`
  - `毛巾总图.jpg`
  - `毛巾材料1.jpg`
  - `毛巾材料2.jpg`
  - `毛巾产品图.jpg`
  - `毛巾产品图2.jpg`

  **External References**:
  - None required.

  **WHY Each Reference Matters**:
  - `projects_stitch.html:157-287` is the full scope area that must end in a coherent polished state.
  - The asset list defines the exact filenames that must resolve correctly.

  **Acceptance Criteria**:
  - [ ] Every product image has non-empty alt text.
  - [ ] All image paths reference existing files exactly.
  - [ ] Card headings / subheadings feel consistent in tone and formatting.

  **QA Scenarios**:
  ```
  Scenario: All product images have valid src and alt text
    Tool: Playwright
    Preconditions: Open local page
    Steps:
      1. Query all product-card `img` elements.
      2. Assert each has a non-empty `alt` attribute.
      3. Assert each image has `naturalWidth > 0`.
    Expected Result: No product image is broken or missing alt text.
    Failure Indicators: Empty alt, broken image, missing src.
    Evidence: .sisyphus/evidence/task-9-image-audit.txt

  Scenario: Local asset filenames all exist exactly as referenced
    Tool: Bash (PowerShell)
    Preconditions: Final HTML saved
    Steps:
      1. Extract or manually verify all product image filenames referenced in the HTML.
      2. Run `Test-Path -LiteralPath` on each exact path.
      3. Save the results.
    Expected Result: Every referenced local asset returns `True`.
    Failure Indicators: Any `False` result.
    Evidence: .sisyphus/evidence/task-9-asset-paths.txt
  ```

  **Evidence to Capture:**
  - [ ] `task-9-image-audit.txt`
  - [ ] `task-9-asset-paths.txt`

  **Commit**: NO

- [x] 10. Run the final in-file consistency and browser layout pass

  **What to do**:
  - Inspect the final HTML for malformed nesting, duplicate IDs, broken class attributes, and leftover placeholder wording.
  - Open the page in a browser at both desktop and mobile widths.
  - Confirm the four-product sequence, image rendering, towel gallery layout, and spacing around the engineering section.
  - Capture final screenshots that prove the page is ready for assignment submission.

  **Must NOT do**:
  - Do not claim the page is complete without actual browser validation.
  - Do not skip mobile-width verification.

  **Recommended Agent Profile**:
  - **Category**: `unspecified-high`
    - Reason: This is a cross-cutting final validation task combining markup review and rendered QA.
  - **Skills**: [`verification-before-completion`, `playwright`]
    - `verification-before-completion`: Forces evidence-based completion.
    - `playwright`: Required for final browser assertions and screenshots.
  - **Skills Evaluated but Omitted**:
    - `requesting-code-review`: Omitted because this is pre-review internal verification.

  **Parallelization**:
  - **Can Run In Parallel**: NO
  - **Parallel Group**: Wave 3 final task
  - **Blocks**: F1, F2, F3, F4
  - **Blocked By**: 1, 2, 3, 4, 5, 6, 7, 8, 9

  **References**:

  **Pattern References**:
  - `projects_stitch.html:1-332` - Final page file requiring whole-file consistency review.

  **API/Type References**:
  - None required.

  **Test References**:
  - Product hooks added in Task 2
  - Towel gallery selectors added in Task 3

  **External References**:
  - None required.

  **WHY Each Reference Matters**:
  - `projects_stitch.html:1-332` must be treated as the final delivery artifact.
  - The stable hooks/selectors from earlier tasks are what make reliable final QA possible.

  **Acceptance Criteria**:
  - [ ] No leftover placeholder product names remain.
  - [ ] All 4 product sections render correctly at desktop width.
  - [ ] All 4 product sections render acceptably at mobile width.
  - [ ] Final evidence screenshots exist for the page.

  **QA Scenarios**:
  ```
  Scenario: Final desktop page render passes
    Tool: Playwright
    Preconditions: Open `file:///E:/github/my-work/projects_stitch.html`
    Steps:
      1. Set viewport to 1440x1600.
      2. Verify all 4 product hooks are present in order.
      3. Verify all product images load successfully.
      4. Capture a full-page screenshot.
    Expected Result: The completed page renders cleanly on desktop with all sections intact.
    Failure Indicators: Missing section, broken image, collapsed layout, placeholder text.
    Evidence: .sisyphus/evidence/task-10-final-desktop.png

  Scenario: Final mobile page render passes
    Tool: Playwright
    Preconditions: Same local page open
    Steps:
      1. Set viewport to 390x1600.
      2. Scroll through all 4 products.
      3. Assert no horizontal overflow and towel gallery remains readable.
      4. Capture a full-page screenshot.
    Expected Result: Mobile layout stays readable and contained.
    Failure Indicators: Horizontal scroll, overlapping text, broken gallery stacking.
    Evidence: .sisyphus/evidence/task-10-final-mobile.png
  ```

  **Evidence to Capture:**
  - [ ] `task-10-final-desktop.png`
  - [ ] `task-10-final-mobile.png`

  **Commit**: NO

---

## Final Verification Wave (MANDATORY — after ALL implementation tasks)

> 4 review agents run in PARALLEL. ALL must approve. Present consolidated results to the user and get explicit okay before completing.

- [x] F1. **Plan Compliance Audit** — `oracle`
  Verify the final page contains exactly 4 real product sections in the approved order, that the old generic product names are absent, and that the old standalone humidifier block is gone.
  Output: `Must Have [N/N] | Must NOT Have [N/N] | Tasks [N/N] | VERDICT`

- [x] F2. **Code Quality Review** — `unspecified-high`
  Review `projects_stitch.html` for malformed markup, duplicated IDs, broken class attributes, missing closing tags, empty `src`, and missing / weak alt text.
  Output: `Markup [PASS/FAIL] | Image refs [PASS/FAIL] | Issues [N] | VERDICT`

- [x] F3. **Real Manual QA** — `unspecified-high` (+ `playwright` skill)
  Open `file:///E:/github/my-work/projects_stitch.html`, verify rendering at desktop and mobile widths, confirm towel gallery count/layout, and capture screenshots of each product section plus a full-page summary.
  Output: `Scenarios [N/N pass] | Responsive [PASS/FAIL] | Image load [PASS/FAIL] | VERDICT`

- [x] F4. **Scope Fidelity Check** — `deep`
  Confirm the implementation only changed the projects page content/layout needed for the 4 real products and did not drift into nav/footer/other-page redesign.
  Output: `Tasks [N/N compliant] | Scope Creep [CLEAN/N issues] | Unaccounted [CLEAN/N changes] | VERDICT`

---

## Commit Strategy

- **Default**: No commit unless the user explicitly asks for one during execution.
- **If user later requests a commit**: create one final commit after F1-F4 pass, e.g. `feat(projects): replace placeholder showcase with real products`

---

## Success Criteria

### Verification Commands
```powershell
Test-Path -LiteralPath "humidifier.png"; Test-Path -LiteralPath "智能中控台.png"; Test-Path -LiteralPath "台灯.jpg"; Test-Path -LiteralPath "毛巾总图.jpg"
# Expected: True for each required product image path
```

### Final Checklist
- [x] All 4 real products are present in the approved order
- [x] All generic placeholder product names are removed
- [x] The duplicate standalone humidifier section is removed
- [x] The towel gallery shows 1 main image + 4 thumbnails
- [x] Browser validation passes at desktop and mobile widths
- [x] Nav, footer, hero, and engineering section remain structurally intact
