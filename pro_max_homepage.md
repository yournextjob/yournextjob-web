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
8. **The employer pitch appears twice.** A second dark "FOR EMPLOYERS" block ("Hire Technically Vetted Infrastructure Talent", y≈14,694, about 1,014px tall) repeats the first employer section near y≈5,201 and ends in a `mailto:` button that exposes the contact email. The plan merges the two.
9. **Nav is thin.** The header holds a logo, a text brand and a single "Subscribe for Updates" button. There are no anchor links to Jobs, Employers, Resources or Contact, and the planned `About` link has no page behind it yet (`/about` is a 404; see section 8).

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
| 5 | For employers (merged) | Hiring pitch, proof and terms | "Need Specialized Engineering Staff?" (y≈5,201) and the second "FOR EMPLOYERS" block, "Hire Technically Vetted Infrastructure Talent" (y≈14,694) |
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

### 5. For employers (merged from two sections)

The live page pitches employers twice: "Need Specialized Engineering Staff?" near y≈5,201, and a second block tagged "FOR EMPLOYERS" near y≈14,694 ("Hire Technically Vetted Infrastructure Talent", three cards, a `mailto:` "Contact Us for Terms of Business" button). They are merged into one section at the first position, and the second block is deleted.

**Top row (two columns: text left, "Your shortlist" card right)**

- **Eyebrow:** `For employers`
- **H2:** `Hire technically vetted infrastructure talent` (the second block's wording, which is more specific than the question form)
- **Intro:** `Skip automated ATS filters and generalist recruiters. We deliver engineering and project management professionals who understand the ground reality of major Victorian infrastructure packages, and we judge candidates on technical capability, not document formatting.`
- **Credibility line:** `Led by an active Interface Manager on complex packages such as SRL East, and involved with Civil College Victoria and Engineers Australia.`
- **Bullets:** `Shortlist in [ N ] days` · `Every candidate vetted by a senior civil engineer` · `No fee until you hire`
- **Button:** `Request a consultation` (the single filled button in the section and the single employer CTA on the page; drop "Get in Touch Today", "Get Started Today" and the `mailto:` button). Reply line: `Reply within [ 1 business day ]`.

**Cards row ("How we work", three cards, wording kept from the live site)**

1. `Peer-to-peer screening`: every candidate pre-vetted by a senior civil engineer; Tier 1 and Tier 2 package experience.
2. `Passive talent network`: mapping and engaging professionals in the Victorian market who are not applying on job boards.
3. `Zero-risk contingency` (the featured card, dark navy): standard contingency model, blind technically screened profiles at no upfront cost, fee only if you hire. Link `Ask about our terms of business →` goes to `/terms#key-terms` (section 10), with a second link `Or request a consultation` to the contact form; no `mailto:` with a visible email address.

**Optional strip ("How it works", three steps):** `Brief us` · `We search and vet` · `You meet a shortlist`. The earlier stats row (placements, days to shortlist) is dropped unless real numbers are supplied.

**Claims to confirm before publishing:** the SRL East reference, the Civil College Victoria and Engineers Australia involvement, and the fee promise are all public statements about the business and are kept as written on the live site. The merged copy says "Victorian" while the hero and page title say "Australian"; choose one scope or state both.

**Anchors:** the merged section is `#employers`; the cards row is `#employer-terms` (linked from the Why us card and the footer).

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

## 8. About page (new page, `/about`)

`https://www.yournextjobtalent.com/about` returns a 404, so the header, footer and Why us credibility-strip links to "About" currently point nowhere. The homepage already holds the raw material in its "About the Founder" section ("An Industry Insider, Not a Salesperson"), which the homepage plan merges into Why us. The full story moves to a dedicated page. No new facts are added to the live wording.

| # | Block | Job | Content |
|---|---|---|---|
| 1 | Hero | Identify the founder and the offer | Eyebrow `About the founder`. H1 `An industry insider, not a salesperson.` Intro: a Senior Project Manager who has delivered major infrastructure projects across Australia and started the business to close the gap between engineers and the companies that hire them. Meta line `[ Name ] · Senior Project Manager · [ City, State ]`. Buttons `Request a consultation` and `I'm an engineer`. Founder photo (real photo, not stock) with a `Senior Project Manager` badge. |
| 2 | Story | Tell the origin in the founder's voice | H2 `Why I started this`. Four paragraphs taken from the live copy: not a traditional recruiter; frustration with good engineers overlooked for poor resumes and hiring managers buried in irrelevant CVs; `I bridge that gap.` as a pull-quote; "someone who speaks your language". |
| 3 | How I vet | Explain the method | H2 `I assess candidates through the lens of a Project Manager`. Three cards from the live copy: `Technical competence`, `Communication skills`, `Delivery focus`. |
| 4 | Background | Credentials | A strip with `[ Active Interface Manager on complex packages such as SRL East ]`, `[ Civil College Victoria ]`, `[ Engineers Australia ]` as editable text, no logos unless supplied. |
| 5 | Who I work with | Route each audience | Two cards, `Engineers` (links to the PD Match Check) and `Employers` (links to `#employer-terms`), text links only. |
| 6 | Final CTA | Close | The navy band from the homepage: `Let's talk about your next hire or your next role.` with `Request a consultation` and `Browse roles`. |

**Rules**

- First-person voice ("I") throughout, matching the live copy. Change it everywhere (including the Why us strip) if the brand should say "we".
- One filled primary button per band; the hero and final CTA use the same labels as the rest of the site.
- Use the real founder photo; do not use stock or generated people.
- Structured data (Person, Organization) only for fields that are filled in; omit anything still a placeholder.
- Page title `About - Your Next Job AU | Engineering recruitment, Australia`, meta description under 155 characters, one H1, add the page to the sitemap.

**Links to wire:** header and footer `About` → `/about`; Why us credibility strip `About me →` → `/about`; the page's own buttons go to `/#contact`, `/#engineers`, `/#roles` and `/#employer-terms`.

**Claims to confirm:** the SRL East reference and the Civil College Victoria and Engineers Australia involvement are public statements. They are kept as written on the live site, but should be checked before publishing. Also decide whether the founder's surname is shown.

---

## 9. Privacy Policy page (new page, `/privacy`)

The site collects personal information in several places, and the footer plan links to a Privacy Policy. I have not confirmed that `/privacy` exists, so the plan is to create it only if missing and otherwise edit the existing page.

**What the site collects (from the live page and the plan)**

- Contact form: name, email, company, message.
- Newsletter: email address and, optionally, whether the person is an engineer or an employer.
- PD Match Check: email, an uploaded CV or position description (`.txt`, `.docx`, `.pdf`), and the targeted role.
- Candidate sourcing: the live copy says the business maps and engages professionals who have not applied ("Passive Talent Network"), and presents "blind" profiles to employers.
- Website analytics and cookies: not yet identified.

| # | Section | Anchor | Content |
|---|---|---|---|
| 1 | What we collect | `#collect` | The five sources above. |
| 2 | How we use it | `#use` | Replying, CV and PD reviews, matching, the newsletter, running the site, legal obligations. |
| 3 | Who we share it with | `#sharing` | Employers only with the person's agreement; service providers `[ list ]`; legal requirements; overseas storage `[ confirm ]`. |
| 4 | CVs, position descriptions and candidate files | `#cvs` | Used to prepare the review; retention `[ period ]`; who can access them. |
| 5 | Finding people who have not applied | `#sourcing` | Public sources, what is recorded, how people are told, how they opt out. All details `[ to confirm ]`. |
| 6 | Storage and security | `#storage` | Reasonable steps `[ actual measures ]`. |
| 7 | How long we keep it | `#retention` | Per data type `[ periods ]`. |
| 8 | Cookies and analytics | `#cookies` | Tools used `[ names ]`; browser controls. |
| 9 | Your choices and rights | `#rights` | Access, correction, deletion, newsletter unsubscribe, OAIC complaint route. |
| 10 | Contact us | `#contact-us` | `[ business name / ABN ]`, `[ privacy contact email ]`, `[ reply time ]`. |
| 11 | Changes to this policy | `#changes` | Date at the top shows the last update. |

**Layout:** header block (eyebrow `Legal`, H1 `Privacy Policy`, last-updated date, short intro), then a sticky "On this page" contents list on the left (a dropdown on mobile) and a 720px reading column. Body 17px at line-height 1.7, one H1, H2 per section, links in the indigo primary, no buttons in the body.

**Links to wire**

- Footer bottom bar: `Privacy Policy` → `/privacy` (a Terms link only if a Terms page exists).
- Newsletter helper text → `/privacy#collect`; PD Match Check note → `/privacy#cvs`; contact form note → `/privacy`.
- Page title `Privacy Policy | Your Next Job AU`, meta description under 155 characters, add to the sitemap.

**Rules**

- The text must match what the forms and the business actually do. The form microcopy in this plan ("We only use your details to reply to you", "Your file is used only to prepare your review") must be changed if the real practice is wider.
- No invented facts: every provider, retention period, storage country and security measure stays a visible `[ ]` placeholder until supplied, and the page is not published while any remain.
- No email address, phone number or ABN appears unless the owner supplies it.
- This is a draft structure, not legal advice. Have the final text reviewed, in particular section 5, since collecting details from public sources has its own requirements under the Australian Privacy Principles, and whether the Privacy Act applies depends on the business's circumstances. The newsletter also needs Spam Act compliance (consent, sender identification, working unsubscribe link), which is separate from this policy.

**Related page:** the contingency card refers to "terms of business". That is a separate document, covered in section 10.

---

## 10. Terms of Business page (new page, `/terms`)

The live contingency card ends in a `mailto:` button, "Contact Us for Terms of Business", so the terms are only available on request and no `/terms` page exists. This page publishes the client terms for employers, in the same long-form layout as the Privacy Policy. I have not confirmed whether `/terms` already exists, so the plan is to create it only if missing.

**What the site already commits to (and the terms must match):** contingency basis, zero upfront cost, blind technically screened profiles, and a placement fee only if the employer hires a candidate introduced by the business.

**Page structure**

- **Header block:** eyebrow `Legal`, H1 `Terms of Business`, last-updated date, a short intro that repeats the contingency promise.
- **"Key terms at a glance" card** directly under the header (anchor `#key-terms`): `Upfront cost: None` · `When a fee applies: only if you hire a candidate we introduce` · `Fee: [ N ]% of [ remuneration basis ] or fixed fee` · `Payment terms: [ N ] days, plus GST`. The card must agree with the full terms below; any placeholder value is highlighted.

| # | Section | Anchor | Content |
|---|---|---|---|
| 1 | Definitions | `#definitions` | `[ legal entity, ABN ]`, You, Candidate, Introduction, Placement. |
| 2 | Introductions and blind profiles | `#introductions` | Screened candidates; blind profiles hide identity until the candidate agrees; no guarantee of suitability. |
| 3 | Fees | `#fees` | No upfront fee; fee only on a Placement; `[ percentage and basis ]`; contract and temporary engagements `[ describe ]`; GST exclusive. |
| 4 | Invoicing and payment | `#invoicing` | `[ invoice trigger ]`, `[ N ]` days, `[ late terms ]`. |
| 5 | Introduction protection | `#protection` | Fee applies to engagement within `[ N ]` months of introduction, including via related parties; no passing details on without asking. |
| 6 | Replacement or refund | `#guarantee` | `[ exact terms, or state that there is no guarantee ]`. |
| 7 | Candidates | `#candidates` | `[ confirm candidates are not charged ]`; accuracy of information; client responsible for its own checks. |
| 8 | Confidentiality and privacy | `#confidentiality` | Mutual confidentiality; links to `/privacy`. |
| 9 | Liability | `#liability` | `[ lawyer-approved limits only ]`. |
| 10 | Governing law | `#law` | `[ state or territory ]`, Australia. |
| 11 | Changes to these terms | `#changes` | Date at the top; which version applies to existing introductions `[ confirm ]`. |
| 12 | Contact us | `#contact-us` | `[ business name / ABN ]`, `[ terms contact email ]`, `[ reply time ]`. |

**Links to wire**

- Footer bottom bar: `Terms` → `/terms` beside `Privacy Policy`; footer Employers column: `Terms of business` → `/terms`.
- Featured Zero-risk contingency card: `Ask about our terms of business →` → `/terms#key-terms`, plus `Or request a consultation` → `#contact`. Remove every remaining `mailto:` terms button.
- Contact form, when the visitor selects Employer: a note under the button that the Terms of Business apply to introductions, with no required checkbox.
- Page title `Terms of Business | Your Next Job AU`, meta description under 155 characters, add to the sitemap.

**Rules**

- No fee, percentage, period, jurisdiction or guarantee is written in unless the owner supplies it; every one stays a visible `[ ]` placeholder, and the page is not published while any remain.
- The terms, the key-terms card, the "No fee until you hire" checklist line and the contingency card wording must say exactly the same thing.
- This is a draft structure, not legal advice. Have a lawyer review the final text. Standard-form contracts with small businesses can fall under the unfair contract terms rules, so clauses such as long introduction-protection periods, broad liability exclusions and automatic fee triggers need particular care.
- If there is no replacement or refund, say so plainly rather than omitting the section.

**Not covered:** terms of use for the website itself are a separate document and are not in this plan.

---

## 11. Suggested implementation order

1. Define tokens (type scale, one primary, radii, spacing) in `:root`.
2. Fix heading line-height and tracking, and unify h2 to a single size.
3. Collapse CTAs to the rules in section 6.
4. Rebuild sections in the order in section 5 (merge, then delete).
5. Create the About page (section 8) so the nav, footer and Why us links resolve.
6. Create the Privacy Policy page (section 9), fill every `[ ]` placeholder, and have it reviewed before publishing, so the footer and form links resolve.
7. Create the Terms of Business page (section 10), fill every `[ ]` placeholder, have it reviewed, and then repoint the contingency card and footer links to it.
8. Re-run this audit, including mobile widths and screenshots, once the changes are live.
