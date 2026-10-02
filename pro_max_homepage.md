# UI/UX Pro Max Audit and Homepage Restructuring Plan

**Site:** https://www.yournextjobtalent.com (the apex domain redirects to `www`)
**Audited:** 2026-10-02, desktop viewport 1536px wide, page height about 16,140px
**Compared against:** Stripe tokens in `DESIGN.md`

## Method and limits

- I read the live DOM and computed styles in Chrome: headings, buttons, font sizes, radii and colours. I also took one hero screenshot.
- Two later screenshots (mid-page and the 5,150px scroll position) timed out, so the **alignment findings below come from measured geometry, not visual inspection**. Check them by eye before acting.
- I did not audit mobile widths. At 1536px there is no horizontal scroll.
- I only extracted headings and CTAs, not every paragraph. Section copy below is a restructuring plan, with new wording written where the current text is unknown. Replace the placeholders marked `[ ]` with real proof points.
- The `ui-ux-pro-max` search script was not run. The audit rests on the skill's rule categories (accessibility, touch, layout, typography and colour) and on `DESIGN.md`, not on its database.

---

## 1. Typography scale

| Property | Live site | Stripe token | Verdict |
|---|---|---|---|
| Font family | Karla (the only text face) | sohne-var, SF Pro Display fallback | Different brand voice. Karla is fine if kept deliberately. |
| Display weight | 700 on h1 to h4 | 300 | **Largest gap.** Everything is bold, so nothing stands out. |
| h1 | 60px / 60px (1.00) | 56px / 1.03, -1.4px | Line-height is tight and tracking is `normal`. |
| h2 | 48px / 48px (1.00), used 11 times | 48px / 1.15, -0.96px | Line-height 1.0 clips two-line h2s. Several wrap to 96px tall, so lines touch. |
| h3 | 24px and 18px | 32px / 26px / 22px | Two different h3 sizes. |
| h4 | 18px, same as the small h3 | n/a | **Hierarchy leak:** h3 and h4 look identical. |
| Card titles | 20px (blog and "why us" cards) | 20px heading-md | Matches. |
| Letter-spacing | `normal` everywhere | -0.2px to -1.4px on display | Large headings look loose. |
| Distinct font sizes | 11, 12, 14, 16, 18, 20, 24, 30, 36, 48, 60 | 10 to 56 across about 14 roles | Eleven sizes with no clear ratio. |
| Smallest text | 18 text elements under 13px; upload chip is 11px | micro 11px, only for tags | Hero trust line and meta text are too small. |

**Findings**

1. **Heading rhythm is flat.** Eleven h2s are all 48px bold, so the page reads as repeated shouting. The "PD Match Check" h2 is the only one at 30px, so it looks like a demoted section. Use one h2 size and one weight.
2. **Line-height 1.0 on display type.** Stripe uses 1.03 to 1.15. At 1.0 the descenders of one line touch the ascenders of the next in the 96px (two-line) h2s.
3. **No tracking on large type.** Add roughly -0.02em on h1 and -0.02em on h2.
4. **h3 and h4 collapse.** `Industry-Vetted Candidates` (h3, 18px) and `The Audio Agent` (h4, 18px) look the same. Pick one level per card style.
5. **Body copy is grey on near-black.** Paragraphs use `#777`, `#9ca3af` and `#c9cecd`. Three greys in one role is a token leak, and `#777` is borderline against the dark background. Use one body colour.
6. **Small text.** The 11px upload label and the hero trust line (about 12px) fail the skill's 12px minimum for body text.

**Fix (tokens)**

```css
--font-sans: Karla, system-ui, sans-serif;
--h1: 56px/1.08 700 -0.02em;
--h2: 40px/1.15 700 -0.02em;
--h3: 24px/1.25 600 -0.01em;
--h4: 18px/1.4  600;
--body-lg: 18px/1.5 400;
--body: 16px/1.5 400;
--caption: 14px/1.4 400;
--text-muted: one grey only, 4.5:1 or better on the surface
```

If you want a closer Stripe feel, keep Karla but drop headings to weight 500 to 600. Stripe's 300 weight depends on Sohne's drawing, and Karla at 300 would be thin.

---

## 2. Layout hierarchy leaks

1. **Six different primary CTAs on one page.** "Employers: Get Started", "Send for Personal Review", "Download the AI Agent Handbook", "Get in Touch Today", "Request a Consultation", "Get Started Today", plus "Get in Touch" three times and "Try the Free PD Match Check". Stripe uses one filled pill per band. Here there are nine or more filled buttons, so none is the main action.
2. **Two accent colours fight.** Primary buttons are teal-blue `rgb(0,102,153)` and secondary ones are yellow `rgb(255,212,0)`. The hero headline also colours "Engineering" blue and "Talent" orange. The Stripe system uses indigo `#533afd` as the one signature colour.
3. **Audience split is unclear above the fold.** The hero offers "Employers: Get Started" and "Engineers: Get Started" as equal buttons. The rest of the page then mixes both audiences section by section (jobs, AI agents, CV tips, hiring, toolkit, blog).
4. **Job search sits 1,167px down.** For a recruitment site the live-listings section is the first thing candidates want, but it is below the hero and has no preview of results.
5. **Content-marketing sections break the sales flow.** "Career Cheat Code #42" (AI agents), "Latest Insight: The CV Mistake...", "The Risk Assurance Toolkit" and the blog sit between the two conversion paths. This pushes the "Need Specialized Engineering Staff?" employer pitch to y=5,201.
6. **Repeated heading patterns.** Three sections use a 2-column `h2 + text` format at the same weight, and the "why us" copy appears at least three times ("An Industry Insider, Not a Salesperson", "Engineering Recruitment Done Right", the h3 cards at y=10,219).
7. **Long page.** About 16,140px, roughly 20 screens at this viewport, with 11 h2s.
8. **Nav is thin.** The header holds a logo, a text brand and a single "Subscribe for Updates" button. There are no anchor links to Jobs, Employers, Resources or Contact.

---

## 3. Alignment issues (from measured geometry)

Verify these visually, since screenshots timed out.

| Item | Measurement | Issue |
|---|---|---|
| h1 | x=153, width 584 | Left edge sits at 153px. |
| Section h2s | x=345 to 1165 depending on section | Left edges vary (`345`, `533`, `597`, `661`, `676`, `725`, `757`, `1165`), which suggests centred headings of different widths mixed with left-aligned ones. Pick one alignment per section type. |
| "An Industry Insider..." h2 | x=1165, width 584 | Sits in the right column while the others are centred, so the eye path zig-zags. |
| Hero CTAs | 281x63 and 284x63 | Close but not equal. Make them identical in width. |
| Button heights | 48px (nav), 52px (search), 60px, 63px | Four heights. Use two: 48px default, 56px hero. |
| Border radii | 8px, 12px, 16px, 24px, pill, `0 12px 12px 0` | Buttons are 12px. Stripe buttons are pills. Choose one family. |
| Header | logo, avatar and text brand overlap in a 662px wide link | The avatar, logo image and "YOUR NEXT JOB AU" text compete as three marks. |
| Hero image | Right column, rounded rectangle on a busy photo | Low-contrast overlay text and a hard-edged card on a dark photo make the hero heavy. |

---

## 4. Stripe token alignment, shortlist

| Token | Stripe | Live | Action |
|---|---|---|---|
| Primary | `#533afd` | `#006699` | Adopt one primary. Retain `#006699` only if it is the brand colour. |
| Ink / body | `#0d253d` on white | white on black | Dark mode throughout. Either keep dark and define dark tokens, or switch to light. |
| Canvas | `#fff`, `#f6f9fc` | black and near-black | Same as above. |
| Button radius | pill | 12px | Use pill (`9999px`) for buttons, 12px for cards. |
| Card padding | 32px | not measured | Standardise at 32px. |
| Spacing scale | 2, 4, 8, 12, 16, 24, 32, 64 | section gaps vary | Use 64px section padding, or 96px on desktop. |
| Accent yellow | none | `#ffd400` | Keep for one role only (job search), or remove. |

---

## 5. Homepage copy restructuring plan

**Goal:** one primary action per band, two clear audience paths, proof before the pitch, and fewer sections. Target: about 9 sections and 9,000 to 10,000px at desktop.

### New section order

| # | Section | Job | Replaces |
|---|---|---|---|
| 1 | Header | Navigation and one CTA | Subscribe-only header |
| 2 | Hero | State the value and split audiences | Current hero |
| 3 | Live roles | Show real listings | "Search Live For Your Next Job In AU" |
| 4 | Why us | Credibility, once | "Industry Insider", "Done Right" and h3 cards, merged |
| 5 | For employers | Hiring pitch | "Need Specialized Engineering Staff?" |
| 6 | For engineers | PD Match Check | "PD Match Check" and the CV mistake |
| 7 | Resources | Three best articles | Blog, Career Cheat Code, Risk Assurance Toolkit |
| 8 | Newsletter | Low-commitment capture | "Stay Ahead in Your Engineering Career" |
| 9 | Final CTA | Two buttons | "Ready for Your Next Engineering Challenge or Hire?" and "Let's Connect" |

### 1. Header

- Left: logo only. Drop the avatar and the duplicate text brand.
- Links: `Jobs` · `Employers` · `Engineers` · `Resources` · `About`.
- Right: **one** button, `Browse roles`. Move "Subscribe for Updates" into the footer and section 8.

### 2. Hero

- **Eyebrow:** `Engineering recruitment, Australia`
- **H1:** `Engineering talent, matched by people who've worked in engineering.`
  *(Current H1: "Connecting Australia's Premier Engineering Talent with Leading Companies". The new line says who is behind it and drops "premier" and "leading", which every agency claims.)*
- **Sub (18px, one grey):** `Led by a Senior Project Manager with industry-vetted candidates and an Australian engineering focus.`
- **Buttons:** primary `I'm hiring` · secondary `I'm an engineer`. Equal width, same height.
- **Trust line (14px minimum):** `[ N placements ] · [ N roles filled in sectors ] · As seen on LinkedIn`
- Remove the second accent colour from the headline. Use one highlight colour or none.

### 3. Live roles

- **H2:** `Open engineering roles in Australia`
- **Sub:** `Updated live. Filter by discipline, state or seniority.`
- Show 4 to 6 real listings above the search box, with the search box below them as `View all roles`.
- One button: `Search roles` (yellow or primary, not both).

### 4. Why us (merge three sections into one)

- **H2:** `Recruitment from someone who has run engineering projects`
- Three cards, 20px titles, 32px padding:
  1. **Industry-vetted candidates:** `Every candidate is assessed on technical fit and delivery record, not keywords.`
  2. **Technical understanding:** `We read a scope, a P&L and a programme, so briefs don't get lost in translation.`
  3. **Australian focus:** `Local market, awards and compliance knowledge in [ sectors ].`
- Keep "Rigorous candidate vetting", "Dual-sided support" and "Results-driven approach" as a short list inside these cards instead of a second block.

### 5. For employers

- **H2:** `Need specialised engineering staff?`
- **Body (2 lines):** `Tell us the role. You get a shortlist of vetted candidates in [ N days ].`
- Bullets: `Shortlist in [ N ] days` · `Vetted for technical fit` · `No fee until you hire` *(only if true)*.
- **Button:** `Request a consultation` (the single employer CTA on the page; drop "Get in Touch Today" and "Get Started Today").

### 6. For engineers

- **H2:** `Check your position description against the market`
- **Body:** `Upload your CV or PD and get a personal review of how it reads to a hiring manager.`
- Show the upload control (`.txt`, `.docx`, `.pdf`) at 12px minimum, with a visible label and a file-size note.
- **Button:** `Send for personal review`
- Add one short block from "The CV mistake most senior engineers make": a 2-sentence teaser with a `Read the full article` text link, not a button.

### 7. Resources

- **H2:** `Guides for engineers and hiring managers`
- Three cards only, 20px titles, with category, read time and author: *Top Engineering Skills in Demand for 2025*, *Resume Mistakes That Cost Engineers Interviews*, *3 Civil Engineering Skills That Pay Higher Rates in 2026*.
- Mark the "How to Leverage Technology in Engineering Recruitment" card, which still reads "Coming Soon", as hidden until it is published.
- Move "Career Cheat Code #42" (AI agents) and "The Risk Assurance Toolkit" to a `/resources` page. Add a text link `See all resources`.
- Update the stale year in "Top Engineering Skills in Demand for 2025" now that it is 2026.

### 8. Newsletter

- **H2:** `Get the monthly engineering market note`
- **Sub:** `Salary trends, in-demand skills and new roles. One email a month.` *(adjust to the real cadence)*
- Email field and a `Subscribe` button. Add helper text: `No spam. Unsubscribe any time.`

### 9. Final CTA

- **H2:** `Hiring or job hunting? Start here.`
- Two buttons: `Request a consultation` (employers) and `Browse roles` (engineers).
- Remove the extra "Let's Connect and Start..." section and the repeated "Get in Touch" buttons.

---

## 6. CTA rules to apply across the page

- One filled primary button per section. Secondary actions are outline or text links.
- Same label for the same action everywhere: `Request a consultation`, `Browse roles`, `Send for personal review`.
- Maximum two button heights and one radius family.
- Contact is reachable from the header and the final section, not repeated every screen.

## 7. Accessibility and quality checks

- Contrast: confirm body grey is at least 4.5:1 and the yellow button text is at least 4.5:1.
- Tap targets: all buttons are above 44px, but the 11px upload chip (180x30) is below it.
- Alt text: all 18 images have alt attributes. Confirm they are descriptive, not filename-like.
- Heading order: one h1, correct h2 to h3 nesting. Do not use h4 for same-level cards.
- Remove the "Coming Soon" article from the public listing, or label it clearly.
- Text-in-hero over a photo: add a solid or gradient scrim so the sub-text meets contrast on the bright shirt area.

## 8. Suggested implementation order

1. Define tokens (type scale, one primary, radii, spacing) in `:root`.
2. Fix heading line-height and tracking, and unify h2 to a single size.
3. Collapse CTAs to the rules in section 6.
4. Rebuild sections in the order in section 5 (merge, then delete).
5. Re-run this audit, including mobile widths and screenshots, once the changes are live.
