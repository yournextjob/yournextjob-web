# UI/UX Pro Max Validation Report

**Site:** https://yournextjobtalent.com (redirects to `www.yournextjobtalent.com`)
**Audited:** 2026-10-02, desktop viewport 1536px, one pass, live DOM and computed styles via Claude in Chrome
**Page height:** 16,562px (the first audit measured about 16,140px)

## Verdict

| Check | Target | Result | Status |
|---|---|---|---|
| Font weights | Only 300 and 500 | 20 of 246 text elements (8%) | **FAIL** |
| Primary colour | Strictly indigo `#533afd` | Every CTA fill is indigo; a few off-brand accents remain | **PARTIAL** |
| Button overload | About one filled button per section | 14 filled CTAs, 7 button heights, 6+ labels for 3 actions; re-checked after the fix prompts and unchanged | **FAIL** |
| Contrast | 4.5:1 for text | Nav links fixed (1.21:1 to 15.23:1, see re-check). Muted text 3.96:1 and indigo text on navy 3.04:1 not yet re-measured | **PARTIAL** |
| Legal and support pages | Exist and are linked | `/about`, `/privacy`, `/terms`, `/website-terms`, `/cookies`, `/resources` all return 404 | **FAIL** |
| Placeholders | None visible | 3 `[ ]` placeholders still live after the re-check | **FAIL** |

The site is part-way through the restructure. New sections and styling have been added, but most of the old sections have not been deleted, so the page is longer than before.

---

## Re-check after the nav contrast and placeholder fixes

Re-measured on the live site after the Landingsite prompts for the nav contrast and the placeholders were prepared. Only those two items were re-checked; everything else in this report is from the first pass.

| Item | First pass | Re-check | Status |
|---|---|---|---|
| Header nav link colour | `#0d253d` on `#0a1120`, **1.21:1** | `#e5e7eb` on `rgba(10,17,32,0.92)`, weight 500, **15.23:1** | **Fixed** |
| "Browse roles" button text | White on `#533afd`, 6.19:1 | Unchanged, 6.19:1 | Pass |
| Hero eyebrow pill | Looked empty | Now reads "Engineering recruitment, Australia" | **Fixed** |
| Hero trust line (y≈907) | `[ N placements ] \| [ N roles filled in sectors ] · As seen on LinkedIn` | Same text | **Not fixed** |
| Why us card (y≈10,394) | `...knowledge in [ sectors ].` | Same text | **Not fixed** |
| Employer checklist (y≈14,750) | `Shortlist in [ N ] days` | Same text | **Not fixed** |

**What this means**

- The nav link fix is live and passes by a wide margin. Hover, active and focus states and the mobile menu were not tested in this re-check.
- The three placeholders are unchanged, so the public page still shows unfinished text. The remove-the-wording prompt (or the fill-in prompt, if real figures are available) has not been applied.
- Page title and meta description were checked and contain no placeholder text. The meta description still reads generically ("Explore Your Next Job AU, your ultimate source for career advice...") and the old hero headline is unchanged.
- Not re-measured: muted text (`#64748b`, 3.96:1), indigo text on navy (`#533afd`, 3.04:1), button counts, font weights and section structure. These keep their first-pass results below.

---

## Re-check after the button overload fixes

Buttons were re-counted on the live site with the same definition as the first pass (a visible button or link with a filled background, at least 36px tall and 80px wide). Page height is now 16,563px (16,562px before).

**Result: no change.** The button fix prompts have not taken effect on the live page.

| Measure | First pass | Re-check | Target |
|---|---|---|---|
| Filled button-like elements | 17 | 17 | |
| Of which indigo CTAs | 14 | 14 | 8 to 9 |
| Button heights in use | 48, 53, 54, 56, 60, 62, 64 (7) | 48, 53, 54, 56, 60, 62, 64 (7) | 48 and 56 only |
| Corner radius | all pill (9999px) | all pill (9999px) | pill |

**Filled buttons found (y position, label, size)**

| y | Label | Size |
|---|---|---|
| 24 | Browse roles | 141x48 |
| 813 | I'm hiring | 267x62 |
| 2,153 | View all roles | 186x56 |
| 2,286 | Search | 140x53 |
| 3,004 | Upload PD (navy) | 536x48 |
| 3,004 | Upload CV (navy) | 536x48 |
| 3,121 | Send for personal review | 337x60 |
| 4,596 | Download the AI Agent Handbook | 400x60 |
| 5,763 | **Get in Touch Today** | 267x60 |
| 6,374 | Request a Consultation | 282x60 |
| 6,626 | As seen on LinkedIn (tag) | 203x48 |
| 8,621 | **Get in Touch** | 190x60 |
| 12,371 | **Get in Touch** | 190x60 |
| 12,799 | Subscribe | 162x54 |
| 13,209 | Request a consultation | 326x64 |
| 14,882 | Request a consultation | 263x56 |
| 16,206 | **Subscribe for Updates** | 373x48 |

**Still present (the three leftover "Get in Touch" calls to action, in bold above):** "Get in Touch Today" (y≈5,763) and two "Get in Touch" buttons (y≈8,621 and y≈12,371). "Subscribe for Updates" (y≈16,206) also remains as a second subscribe button. The case mismatch "Request a Consultation" / "Request a consultation" is unchanged.

**Engineers section (y≈3,004 to 3,121):** still three filled buttons together: two navy upload controls ("Upload PD", "Upload CV") and the indigo "Send for personal review".

**Other get-in-touch controls (outline, not filled):** three outline "Get in Touch" links at y≈9,660 (99x48 each), a wide "Subscribe & Get in Touch" control at y≈13,798 (1052x68), and an "Or request a consultation" link at y≈15,399. I did not check what these are, so they are not counted above, but they add to the repeated get-in-touch wording: "Get in Touch" appears in seven controls in total (three filled buttons, three outline links and the wide "Subscribe & Get in Touch" control).

**Still true from the first pass:** the primary action colour is `#533afd` on all 14 CTA fills, the radius is a pill everywhere, and the header's "Browse roles" is correctly a primary at 48px.

---

## 1. Font weights (target 300 / 500)

Counted over all 246 visible text elements. Font family is Karla on every element, which is consistent.

| Weight | Elements | Share |
|---|---|---|
| 300 | 4 | 2% |
| 400 | 92 | 37% |
| 500 | 16 | 7% |
| 600 | 101 | 41% |
| 700 | 33 | 13% |

**Result: fail.** 226 of 246 elements use a weight outside 300/500. The main offenders:

- Body paragraphs at 400: 72 `<p>` elements.
- H3 and card titles at 600: 27 elements.
- Spans and links at 600: 43 elements.
- H2s still at 700: 13 elements. The H1 is also 700.

**Note on the target.** The Landingsite prompts I wrote specified headings at 600, body at 400 and buttons at 500, not 300/500. The site follows those prompts partly (H3 at 600). If 300/500 is the intended rule, the prompts need to change, and I'd suggest testing it first: Karla at 300 is light, and on a dark background it may read thin. Karla does include 300 and 500.

**To reach 300/500:** headings and buttons at 500, body at 300, and nothing at 400, 600 or 700. A single global weight rule in Landingsite's theme settings is simpler than editing each element.

---

## 2. Primary colour (target strictly `#533afd`)

`rgb(83, 58, 253)` is the dominant accent:

- 60 elements use it as a background, 24 as a border and 21 as text colour.
- **Filled CTA buttons:** 14 of 14 use it. The yellow `#ffd400`, teal `#006699` and orange accents from the first audit are gone.

Other saturated colours still present (nothing else of note was found in the scan):

| Colour | Where | Elements | Note |
|---|---|---|---|
| `rgb(0,119,181)` (LinkedIn blue) | "As seen on LinkedIn" badge | 2 | Brand colour of a third party; decide whether to keep. |
| `rgb(255,0,0)` and its 20% tint | Border and backgrounds | 4 | Likely a status or live indicator; not verified. |
| `rgb(52,211,153)` and `rgb(110,231,183)` (green) | Status tag | 4 | Likely a "live"/"new" tag. |
| `rgb(157,141,255)`, `rgb(124,108,255)` | Lighter indigo tints | 5 | Same hue; acceptable tints. |

**Other colour issues**

- **The page is still dark.** The background is `rgb(10,17,32)` navy, not the white Stripe canvas. The Stripe ink `#0d253d` appears as a background (7 elements) and as the **colour of the header nav links**.
- **Muted text** is `rgb(100,116,139)` on 86 elements; it is a blue-grey, not part of the Stripe token set.

**Result: partial pass.** The primary action colour is strictly indigo. The site as a whole is not strictly indigo-only, because of the LinkedIn blue, the red and green status colours, and the dark theme.

---

## 3. Button count (layout overload)

Definition: a visible `<button>` or link with a filled background, at least 36px tall and 80px wide. There are 48 interactive text elements in total and 17 `<button>` tags.

**17 filled button-like elements:**

- 14 indigo CTAs.
- 2 navy upload controls ("Upload PD" and "Upload CV", 536x48). These are form controls, not calls to action.
- 1 LinkedIn badge ("As seen on LinkedIn"), which is a tag styled like a pill.

**Pills:** all 17 use a fully rounded radius (`9999px`). The earlier mix of 8px and 12px radii has gone.

**Heights:** 48, 53, 54, 56, 60, 62 and 64px, which is **seven** heights. The target is two (48 and 56).

**Labels for the same actions are not unified:**

| Action | Labels found |
|---|---|
| Employer enquiry | "I'm hiring", "Get in Touch Today", "Request a Consultation", "Request a consultation" (two different sizes: 326x64 and 263x56), "Get in Touch" (twice) |
| Newsletter | "Subscribe" and "Subscribe for Updates" (373x48) |
| Roles | "Browse roles", "View all roles", "Search" |
| Engineer | "Send for personal review", "Download the AI Agent Handbook" |

**Filled buttons by section (13 sections found):** hero 1, live roles 2, engineers 3 (two are upload controls), AI agents 1, employers 1, risk toolkit 1, founder 1, resources 0, why us 0, stay-ahead 1, newsletter 1, final CTA 1, second employer block 1.

**Result: fail.** 14 real CTAs across 13 sections is about one per section on average, but the labels and heights are inconsistent and three old calls to action remain ("Get in Touch Today", "Get in Touch" ×2). A single "Request a consultation" and a single "Subscribe" per page would cut the count to about 9.

---

## 4. Typography scale

| Element | Measured | Target | Status |
|---|---|---|---|
| H1 | 56px / 60.5px (1.08), weight 700, tracking -1.12px | 56px, line-height about 1.1, tracking -0.02em | Size, line-height and tracking pass; weight fails |
| H2 | 40px / 46px (1.15), weight 700, tracking -0.8px | 40px, line-height 1.15, tracking -0.02em | Size, line-height and tracking pass; weight fails |
| H3 | 24px / 30px, weight 600 | 24px | Pass on size |
| Font sizes in use | 12, 14, 16, 18, 20, 24, 30, 40, 56 (nine) | A short scale | Improved from eleven |
| Text under 14px | 20 elements | None | Fail |

Heading tracking and line-height are fixed. Only the weights and the small text remain.

---

## 5. Contrast (computed against actual backgrounds)

| Text | Colour on background | Ratio | Result |
|---|---|---|---|
| Header nav links (Jobs, Employers, Engineers, Resources, About) | `#0d253d` on `#0a1120` | **1.21:1** | Fail. Effectively invisible. |
| Muted text (86 elements) | `#64748b` on `#0a1120` | 3.96:1 | Fail for small text |
| Indigo text (21 elements) | `#533afd` on `#0a1120` | 3.04:1 | Fail for normal-size text |
| Button label | White on `#533afd` | 6.19:1 | Pass |

The nav links are the most urgent fix: the Stripe ink colour has been applied to a dark header. On a dark page, use white or a light grey for nav text and a lighter indigo (such as `#9d8dff`, already present on the page) for indigo text and links.

---

## 6. Structure: what has and hasn't changed

Sections found (order, y position):

1. Hero (97), still the old headline "Connecting Australia's Premier Engineering Talent with Leading Companies".
2. Open engineering roles in Australia (1,167), the new Live roles heading.
3. Check your position description against the market (2,487), the new For engineers heading.
4. Career Cheat Code #42 (3,617), still on the homepage.
5. Need Specialized Engineering Staff (5,919), the first employer section, still present.
6. The Risk Assurance Toolkit (6,530), still on the homepage.
7. An Industry Insider, Not a Salesperson (7,813), still present.
8. Guides for engineers and hiring managers (8,777), the new Resources heading.
9. Recruitment from someone who has run... (9,925), the new Why us heading.
10. Stay Ahead in Your Engineering Career (10,718), the old newsletter section.
11. Get the monthly engineering market note (12,527), the new Newsletter heading.
12. Hiring or job hunting? Start here. (12,981), the new final CTA.
13. Hire technically vetted infrastructure talent (14,148), the second employer block, restyled but **not merged** with section 5.

**Result:** new sections were added, but the old ones they replace are still there (AI agents, Risk Assurance, Industry Insider, the old newsletter, and both employer sections). That is why the page grew by about 400px. The target was about 9 sections and 9,000 to 10,000px.

---

## 7. Visible placeholders on the public page

Three unfilled placeholders are live:

- Hero trust line (y≈906): `[ N placements ] | [ N roles filled in sectors ] · As seen on LinkedIn`
- Why us card (y≈10,379): `Local market, awards and compliance knowledge in [ sectors ].`
- Employer checklist (y≈14,723): `Shortlist in [ N ] days`

Replace these with real facts or delete the lines. In the hero screenshot the eyebrow pill above the headline appears empty; I didn't verify what text it contains.

---

## 8. Pages and links

All of these return the site's 404 page:

`/about`, `/privacy`, `/terms`, `/website-terms`, `/cookies`, `/resources`

- The header already shows "Resources" and "About" links, so they likely lead to dead pages. I didn't check each link's destination.
- The footer shows Home, Jobs, Engineers, Employers, Why Us and Resources. It has **no Privacy, Terms or Cookies links**, even though the site collects emails, CVs and runs Google Analytics.

---

## 9. Recommended next steps (in priority order)

1. ~~Fix the nav link colour (contrast 1.21:1).~~ Done: 15.23:1 on the re-check.
2. Remove the three live placeholders. **Still open** (hero trust line, Why us card, employer checklist).
3. Delete the old sections that the new ones replaced, and merge the two employer sections.
4. Unify buttons: two heights (48 and 56), one label per action, remove "Get in Touch" variants and the second "Subscribe". **Still open**: re-checked and unchanged (17 filled, 14 indigo, 7 heights).
5. Decide the weight rule. If 300/500, apply it globally and review the result on the dark background.
6. Create `/privacy`, `/terms`, `/website-terms` and `/cookies` and link them in the footer.
7. Decide whether the page stays dark. If it does, define dark-theme tokens instead of mixing the light Stripe ones.
8. Re-run this audit after the changes.

## Method and limits

- One pass at 1536px. Mobile widths were not tested.
- Weights, colours and sizes are computed styles over visible elements. Counts are of elements, not of unique components.
- A "button" is defined as above. A different definition will change the counts.
- Colour contrast was computed from the element's own colour and the nearest non-transparent background. Text over images was not measured.
- Only the hero was screenshotted. Mid-page screenshots timed out in the earlier audit and were not retried.
- The 300/500 and "strictly indigo" targets are as stated in the request.
- Cookie and storage observations from the Cookie Policy check are not repeated here.
