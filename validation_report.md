# UI/UX Pro Max Validation Report

**Site:** https://yournextjobtalent.com (redirects to `www.yournextjobtalent.com`)
**First audit:** 2026-10-02, desktop viewport 1536px, one pass, live DOM and computed styles via Claude in Chrome
**Latest full re-run:** 2026-10-03, same method and viewport
**Page height:** 16,502px on the latest run (16,562px on the first audit)

## Verdict (latest full re-run, 2026-10-03)

| Check | Target | Result | Status |
|---|---|---|---|
| Font weights | Only 300 and 500 | 24 of 246 text elements (10%); H1 is now 300 | **FAIL** |
| Primary colour | Strictly indigo `#533afd` | All 14 CTA fills are indigo; red status accents, a LinkedIn blue badge and the navy page background remain | **PARTIAL** |
| Button overload | About one filled button per section | 17 filled, 14 indigo CTAs, 7 heights, same labels; unchanged | **FAIL** |
| Text contrast | 4.5:1 (3:1 for large text) | 4 of 246 elements fail (2%); nav 15.2:1; hero pill 12.7:1; "Why Us" pill 1.2:1 | **MOSTLY PASS** |
| Navigation anchors | Every link is an on-page anchor | 40 anchors, none broken; 6 planned anchors missing | **PARTIAL** |
| Placeholders | None visible | The same 3 `[ ]` placeholders still live | **FAIL** |
| Icons | Consistent line-art, readable | 117 of 124 solid, 27 low contrast, none empty | **FAIL** |
| Page structure | About 9 sections, 9,000 to 10,000px | 13 sections, 16,502px; no old section removed | **FAIL** |

The site is part-way through the restructure. Some styling has been applied (nav colour, hero pill, H1 weight), but most of the old sections have not been deleted and the legal and About sections have not been added.

---

## Full re-run, 2026-10-03

Every check was re-measured on the live site, using the same definitions as the first audit unless noted.

| Measure | First audit | Previous re-check | Latest | Change |
|---|---|---|---|---|
| Text on weight 300 or 500 | 20 of 246 | not re-measured | 24 of 246 | Slightly better |
| Weight split (300 / 400 / 500 / 600 / 700) | 4 / 92 / 16 / 101 / 33 | not re-measured | 6 / 91 / 18 / 100 / 31 | Almost unchanged |
| H1 | 56px, weight 700 | not re-measured | 56px, weight **300** | Changed |
| H2 | 40px, weight 700 | not re-measured | 40px; mostly 700, one style at 500 | Mostly unchanged |
| Filled button-like elements | 17 | 17 | 17 | None |
| Indigo CTAs | 14 | 14 | 14 | None |
| Button heights | 7 (48 to 64px) | 7 | 7 | None |
| Visible `[ ]` placeholders | 3 | 3 | 3 | None |
| Header nav link contrast | 1.21:1 | 15.23:1 | 15.2:1 | Fixed |
| Hero eyebrow pill contrast | looked empty | readable | 12.7:1 | Fixed |
| "Why Us" eyebrow pill contrast | not seen | not re-measured | **1.2:1** (dark ink on dark) | Still broken |
| Text elements below contrast thresholds | not totalled | not re-measured | 4 of 246 (2%) | Mostly fixed |
| Text under 14px (old definition) | 20 | not re-measured | 20 | None |
| Sections | 13 | not re-measured | 13 | None |
| Page height | 16,562px | 16,563px | 16,502px | About 60px shorter |

**Text contrast detail.** The grey text that failed in the first audit (about 4.0:1 on the navy) no longer appears in the failures. The four remaining failures are one dark-ink label (the "Why Us" pill, 1.21:1), one element with white text on `#7c6cff` (3.86:1) and two elements with a fully transparent text colour (1.11:1) that I did not identify. The check treats text of 24px and above, or 18.66px and above in bold, as large (3:1 threshold). It is not a like-for-like comparison with the first audit's per-colour contrast notes.

**Buttons, unchanged.** The list is the same as the previous re-check: "Browse roles", "I'm hiring", "View all roles", "Search", the two navy upload controls, "Send for personal review", "Download the AI Agent Handbook", "Get in Touch Today", "Request a Consultation", "Get in Touch" (twice), "Subscribe", "Request a consultation" (two sizes), "Subscribe for Updates", plus the LinkedIn badge.

**Icons.** 124 visible Font Awesome icons, none with an empty glyph. Styles: 117 solid, 5 brands, 1 light, 1 regular. 27 icons sit at under 3:1 contrast (light indigo on solid indigo tiles). The line-art restyle has not been applied.

**Links (single-page rule).** 40 in-page anchor links and none point at a missing id. Four links go to `/` (the logo twice, "yournextjobtalent.com" and "Home"). There are no `mailto:` links. External links go to `drive.google.com`, `www.linkedin.com` and `www.youtube.com`.

- Header targets: `Jobs` → `#jobs`, `Employers` → `#employers`, `Engineers` → `#engineers`, `Resources` → `#resources`, `About` → `#about`, `Browse roles` → `#live-listings`.
- Present among the planned ids: `why-us`, `about`, `employers`, `engineers`, `resources`, `contact`.
- **Missing among the planned ids:** `roles`, `employer-terms`, `newsletter`, `privacy`, `terms`, `web-terms`. The site uses `#jobs` and `#live-listings` where the plan says `#roles`; one of the two should change so they match.

**Sections found (y position, id, heading).** 97 hero; 1,107 `job-search-section` "Open engineering roles in Australia"; 2,427 "Check your position description against the market"; 3,556 "Career Cheat Code #42"; 5,859 "Need Specialized Engineering Staff?"; 6,470 "The Risk Assurance Toolkit"; 7,752 "An Industry Insider, Not a Salesperson"; 8,716 "Guides for engineers and hiring managers"; 9,865 "Recruitment from someone who has run engineering projects" (Why us); 10,658 "Stay Ahead in Your Engineering Career"; 12,466 "Get the monthly engineering market note"; 12,920 `contact-form` "Hiring or job hunting? Start here."; 14,087 "Hire technically vetted infrastructure talent". The hero headline is still the old "Connecting Australia's Premier Engineering Talent with Leading Companies".

**Not done yet on the live site:** the About section update, the Legal block (Privacy, Terms of Business, Website Terms), the merged employer section, removal of the old sections, the button cleanup, the placeholder removal, the weight rule and the icon restyle.

**Limits of this run.** Desktop only; hero screenshot only; weights, colours and contrast are computed over visible elements; counts of elements, not of components.

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

## 8. Navigation and links

The site is a single-page layout with no sub-pages, so `/about`, `/privacy`, `/terms`, `/website-terms`, `/cookies` and `/resources` returning the 404 page is expected. It is not a failure and has been removed from the verdict.

What is still open:

- **Checked on 2026-10-03:** the header links all jump to on-page anchors (`#jobs`, `#employers`, `#engineers`, `#resources`, `#about`, `#live-listings`) and none of the 40 anchor links point at a missing id. Six planned ids are still absent (`roles`, `employer-terms`, `newsletter`, `privacy`, `terms`, `web-terms`); see the full re-run section.
- **Footer legal links:** the footer shows Home, Jobs, Engineers, Employers, Why Us and Resources, with **no Privacy, Terms or Cookies links**, even though the site collects emails and CVs and runs Google Analytics. The legal text needs to live on the page and be reachable by anchor from the footer.

---

## 9. Recommended next steps (in priority order)

1. ~~Fix the nav link colour (contrast 1.21:1).~~ Done: 15.23:1 on the re-check.
2. Remove the three live placeholders. **Still open** on the 2026-10-03 re-run (hero trust line, Why us card, employer checklist).
3. Delete the old sections that the new ones replaced, and merge the two employer sections. **Still open**: all 13 sections remain.
3a. Fix the "Why Us" eyebrow pill (1.21:1, dark ink on dark), the last clear contrast failure. The hero pill is fixed.
3b. Restyle icons to one line-art style with white glyphs on indigo tiles (117 solid, 27 low contrast).
4. Unify buttons: two heights (48 and 56), one label per action, remove "Get in Touch" variants and the second "Subscribe". **Still open**: re-checked and unchanged (17 filled, 14 indigo, 7 heights).
5. Decide the weight rule. If 300/500, apply it globally and review the result on the dark background. **In progress**: the H1 is now 300, but H2s, card titles and body text are not.
6. Add the legal text (Privacy, Terms of Business, Website Terms) as on-page sections and link them from the footer with anchors (`#privacy`, `#terms`, `#web-terms`). The header and footer targets have now been read: they are anchors, but `#roles`, `#employer-terms`, `#newsletter`, `#privacy`, `#terms` and `#web-terms` do not exist yet, and the site uses `#jobs` and `#live-listings` where the plan says `#roles`.
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
- An earlier version of this report counted the 404s on sub-page routes as failures. That was removed once it was confirmed that the site is a single page with no sub-pages.
