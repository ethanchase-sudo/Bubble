# Handoff: Magic Bubbles Detailing — Marketing Website

## Overview
A single-page, premium marketing site for **Magic Bubbles Detailing**, a mobile auto detailing business in Houston, TX (est. January 1999). The site lets Houston customers browse services, compare three detailing packages, learn about the business and fleet/commercial offer, read reviews, and **request a booking/quote** (call, text, or form).

## About the Design Files
The files in this bundle are **design references created in HTML**. They are prototypes that show the intended look and behavior. They are **not production code to copy directly**. Recreate the design in the target codebase's existing environment (React/Next.js, Astro, Vue, etc.) using its established patterns. If no environment exists, a static-friendly framework such as **Next.js or Astro + plain CSS/CSS modules** is recommended (SEO-friendly, fast, easy to deploy).

## Fidelity
**High-fidelity.** Colors, typography, spacing, copy and interactions are final. Recreate them pixel-accurately. Imagery is **licensed stock** used as a stand-in. It should be replaced 1:1 with the business's own photos when they're available (the Facebook page couldn't be accessed for imagery).

---

## Global Layout
- Single scrolling page, full-bleed sections, dark theme with one light section ("How it works").
- Horizontal page padding: `--pad: clamp(20px, 4vw, 64px)`.
- Section vertical padding: `clamp(90px, 12vw, 170px)`.
- **Section header pattern** (`.sec-head`): a 2-col grid `200px 1fr`, gap 40px, margin-bottom `clamp(50px,6vw,90px)`.
  - Left: mono label `"01 / Services"`. The number is in `--blue-hi` with a 1px top border `--line` and padding-top 12px.
  - Right: H2 plus an optional lede paragraph.
- Breakpoints: **≤1080px** (tablet) and **≤720px** (mobile). Details are in the Responsive section below.

## Screens / Sections (in order)

### 1. Nav (fixed header)
- Fixed top, z-index 50, flex space-between, padding `18px var(--pad)`.
- **Scrolled state** (scrollY > 40) adds class `.solid`:
  - background `rgba(11,13,16,.78)`, `backdrop-filter: blur(14px) saturate(1.3)`
  - padding-block 12px, bottom border 1px `--line`
  - transition .4s
- **Brand lockup:**
  - Oval mark: 58×34px with a 1.5px `--foam` border and border-radius 50%. Inside sits an inner oval (inset 4px, 1px `--blue` border) and the text "MB" (Archivo 800, width 125%, 11px). It nods to the business's original oval badge.
  - Wordmark "MAGIC BUBBLES": Archivo 800, font-stretch 125%, 15px, letter-spacing .04em.
  - Subline "DETAILING · HOUSTON": JetBrains Mono 10px, letter-spacing .24em, `--mute`.
- **Links** (Services, We Come To You, Packages, Fleet, Story):
  - Mono 12px, uppercase, letter-spacing .12em, `--mute`.
  - Hover: color `--foam`, and a 1px `--blue` underline grows left→right (.3s).
- **CTAs:**
  - Ghost pill "(281) 217-0461" → `tel:+12812170461`
  - Blue pill "Get a quote" with a pulsing dot → `#quote`
- ≤1080px: the links hide and a 46px round burger button opens a **full-screen drawer**. The drawer slides down from translateY(-100%) in .6s `cubic-bezier(.7,0,.2,1)`. Its links are Archivo 900 / 125% width at `clamp(40px,9vw,80px)`.

### 2. Hero (`#top`)
- min-height 100svh. Grid rows `1fr auto`, with the content anchored to the bottom.
- **Background image:**
  - Foam-covered black sedan (`img/c1.jpg`), cover, positioned center 60%.
  - Filter `saturate(.75) contrast(1.08) brightness(.72)`, scale 1.08.
  - Parallax: `translateY(scrollY*0.25)`.
- **Overlays:**
  - Vertical: dark 55% at top → transparent at 30–50% → solid `--ink` at the bottom.
  - Horizontal: `--ink` at 85% on the left → transparent by 60%.
- **Bubble canvas** (see Interactions) sits over the image.
- **Eyebrow:** "Mobile auto detailing · Houston, TX · Since 1999". Mono 12px, `--blue-hi`, preceded by a 40px 1px line.
- **H1** (2 lines): "SHOWROOM" / "AT YOUR DOOR."
  - Archivo 900, font-stretch 125%, `clamp(46px, 9vw, 176px)`, line-height .86, letter-spacing -.03em, uppercase, nowrap on desktop.
  - "at your" is outlined text: transparent fill, `-webkit-text-stroke: 1.5px --foam`.
  - Each line masks and rises from translateY(105%) (1.1s `cubic-bezier(.2,.8,.2,1)`). Line 2 is delayed .12s.
- **Side block** (right column, 260–340px):
  - Paragraph at 17px / 1.5: "Hand wash, wax, interior shampoo and full detailing — brought to your home, office or job site anywhere in the Houston area."
  - Buttons: blue "Request a booking →" and ghost "Services".
  - Fades in after .6s.
- **Spec strip:** 4 columns with a 1px top border and 1px dividers between cells, cell padding 22px. Each cell has a mono label plus Archivo 700 / 110% width / 18px:
  - Est. — January 1999
  - Service — 100% Mobile
  - Base — Galleria · 77056
  - Direct — (281) 217-0461 (tel link)
- **"Scroll" cue:** vertical text on the right with an animated dripping line (2.2s loop).

### 3. Vehicle marquee
- Bordered top and bottom, padding 22px 0. An infinite horizontal scroll moves left (40s linear; the content is duplicated).
- Words: Cars · Trucks · SUVs · Vans · Motorcycles · Boats · RVs · 18-Wheelers · Buses · Fleets.
  - Archivo 800, 125% width, `clamp(28px,4vw,56px)`, uppercase.
  - Even items are outline-only (1px stroke, white at 45%).
- Separator after each word: a 14px circle with a 1.5px `--blue` ring (a "bubble").

### 4. Services (`#services`, "01 / Services")
- H2: "Every surface. **Inside & out.**" (second phrase in `--blue-hi`).
- Lede: "From a maintenance hand wash to a full shampoo-and-wax detail, every service is tailored to your vehicle, your schedule and your location."
- **Layout:** 2-col grid `1.05fr 1fr`, gap `clamp(30px,5vw,80px)`.
- **Left: accordion list**, 5 rows. Each row is a grid `56px 1fr auto`, padding 24px 0, with a 1px bottom border.
  - Row number: mono.
  - Title: Archivo 700, 112% width, `clamp(22px,2.4vw,34px)`, uppercase.
  - Plus button: a 34px circle that turns into a minus when open.
  - **Open state:**
    - Title turns `--blue-hi` and shifts translateX(6px).
    - Plus circle fills `--blue`.
    - Body expands via `grid-template-rows 0fr→1fr` (.45s).
  - Body: paragraph (16px / 1.6, `--mute`, left indent 72px) plus mono pill tags.
- **Services and tags:**
  1. **Exterior Hand Wash** — Exterior detail, Clean windows, Clean rims, Dress tires.
  2. **Polish & Hand Wax** — Hand wax, Wax buff, Polish.
  3. **Interior Detailing** — Carpet shampoo, Leather conditioning, Vinyl / plastic treatment, Ozone odor removal.
  4. **Wheels & Engine Bay** — Rim detail, Engine cleaning.
  5. **Commercial & Fleet** — Fleet accounts, Heavy equipment, RV · Truck · Trailer, Boats.
- **Right: sticky media panel**
  - Sticky at top 110px, aspect-ratio 4/5, radius 6px.
  - Five stacked images crossfade (opacity .7s) and zoom from scale(1.08) to 1 over 1.4s.
  - Thin corner brackets top-left and top-right.
  - Caption: the service name in mono at the bottom-left, and a huge outlined number ("01"–"05", Archivo 900, 84px) at the bottom-right.
  - Images in order: c4, c9, d3, c5, c3.
- **Behavior:** hover (pointer devices) or click opens one item and closes the others, swaps the image and updates the caption and number.

### 5. How it works (`#mobile`, "02 / How it works") — LIGHT section
- Background `--foam` with `--ink` text. Accents use `--blue`, and muted text is `#575d64`-ish (`oklch(0.4 0.01 250)`).
- H2: "You keep working. **We bring the shine.**"
- Lede: "No waiting rooms, no drop-offs. Magic Bubbles comes to your driveway, office lot or job site — so your car gets detailed on your time, not in place of it."
- **4-step row:** 4 columns with dividers (1px black at 14%), min-height 260px. Each step has a big number (Archivo 900, 125% width, 64px, `--blue`), an H4 (Archivo 700, 22px, uppercase) and a paragraph.
  1. **Call or request** — "Tell us your vehicle, the service you want and where it's parked."
  2. **Get your quote** — "Affordable packages or a custom plan built around your vehicle and needs."
  3. **We roll up** — "Our crew arrives at your home, office or business location across Houston."
  4. **Drive away clean** — "We work with you until you are completely satisfied."
- **Two images** below in a 2-col grid, aspect 16/11, radius 6px. Each has a pill caption (mono, foam background):
  - c1 — "At your driveway"
  - c11 — "At your office"

### 6. Packages (`#packages`, "03 / Packages")
- H2: "Three levels **of clean.**"
- Lede: "Pricing depends on vehicle size and condition — cars, trucks and SUVs are quoted individually. Request a quote and we'll confirm your price before we start."
- **No prices are shown, on purpose.** The only prices found were roughly 10 years old.
- **Cards:** 3-col grid, gap 18px.
  - Card: 1px `--line` border, radius 8px, padding 30/28px, background gradient `--ink2 → --ink`.
  - **Hover:** border turns blue at 70%, the card lifts translateY(-6px), and a radial blue glow (400px, 16% alpha) follows the cursor via CSS vars `--mx/--my`.
  - Top row: mono "Package" / tier word.
  - Title: Archivo 900, 125% width, 48px, line-height .9. A mono "Level 0X" kicker sits above it in `--blue-hi`.
  - **Meter:** 3 bars, 4px tall, radius 2. Filled bars are `--blue`, empty ones `--ink3`.
  - Feature list: rows with dashed bottom borders. Each row has the feature on the left and a mono "IN" / "EX" / "+" on the right. New items are in `--blue-hi`.
  - CTA: a full-width pill "Quote this →". It scrolls to `#quote` and pre-selects that package.
- **Package contents:**
  - **Level 01 — Wash & Wipe** (Maintenance, 1 bar): Vacuum interior, Wipe interior, Exterior detail, Clean windows, Clean rims, Dress tires.
  - **Level 02 — Wash & Wax** (Gloss, 2 bars). Featured: blue border plus a "Hand wax" tab badge on the top-right edge, and the CTA is the blue button. Contents: Everything in Level 01 + **Hand wax**.
  - **Level 03 — Full Detail** (Complete, 3 bars): Everything in Level 01 + **Interior shampoo**, **Wax buff**.
- **Add-ons row:** Rim detail, Engine cleaning, Leather treatment, Ozone odor removal (pill tags).

### 7. Fleet / Commercial (`#fleet`, "04 / Commercial")
- Background: a tire-tread texture (`img/c6.jpg`) tiled at 420px, opacity .07, blend mode screen.
- H2: "From coupes **to cement trucks.**"
- Lede: "Houston businesses trust Magic Bubbles to keep their fleets presentable, right where the vehicles are parked."
- **Layout:** grid `1fr 1.15fr`.
- **Left column:**
  - 2-col vehicle list with letter codes A–J: Cars, Pickups, Vans & Step Vans, Tractor-Trailers, Bobtails, Tankers, Garbage Trucks, Cement Trucks, Flatbeds, Forklifts. Text is Archivo 600, 110% width, 20px, uppercase. Hover turns it `--blue-hi`.
  - "Commercial accounts have included": Alamo Stone, RV Masters, Brand Scaffold, GTS Ambulances, Vista Fibers, Amerigroup, Roy Moffitt, Enterprise, Loews, Shred-It. Archivo 700, 90% width, 18px.
  - Blue CTA "Set up a fleet account →" pre-selects vehicle = Fleet / Commercial.
- **Right column:** SUV headlights image (c7), min-height 520px, with mono labels at the top ("Fleet service" / "On-site · Houston").

### 8. Story (`#story`, "05 / Our story")
- 2-col grid `1.1fr 1fr`, min-height 90vh.
- **Left:** full-bleed image (d4, grayscale .2) with a giant outlined "1999" at the bottom-left. Archivo 900, 125% width, `clamp(90px,14vw,240px)`, 1.5px stroke.
- **Right:** `--ink2` background, vertically centered content.
  - Blockquote: "“Our main goal is to have satisfied customers. We are determined to treat our customers with *honesty and respect.*”". Archivo 500, `clamp(24px,2.4vw,36px)`, line-height 1.22. The highlighted phrase is in `--blue-hi`.
  - Paragraphs:
    - "Magic Bubbles was established in January 1999 in Houston, Texas as an automotive detailing company — built on top quality at a reasonable price."
    - "Our highly trained staff and customer service team work together with you until you are completely satisfied, whatever your schedule."
  - Signature row: a 52px initials circle "TB", **Tyrone Bush**, and mono "Owner · Magic Bubbles".

### 9. Reviews (`#reviews`, "06 / Reviews")
- H2: "Heard around **Houston.**"
- **Cards:** 3 columns. Each card has a 2px `--blue` top border and padding-top 28px. The quote is 20px / 1.45 with blue curly quote marks, and min-height 150px. The name is in mono below.
  - Mina A. — "Magic Bubbles came over to my company which was super awesome — having my car washed while working and not having to go on my own time."
  - Andy N. — "Wow. Just wow. My car looked like it came from the showroom. I work in the Galleria area and they service in this area. It's very convenient."
  - Steff G. — "I will recommend this detailing company to others — the convenience of being located in the Houston area was great!"
- Footer row: "Reviews excerpted from Yelp" and a ghost button "Follow on Facebook ↗" → https://www.facebook.com/magicbubblesdetailing/

### 10. Quote / Booking (`#quote`, "07 / Book")
- `--ink2` background with a top border. Grid `1fr 1.25fr`.
- **Left column:**
  - H2 "Request a **booking.**"
  - Lede: "Build your request in under a minute. We'll reach back to confirm price, date and location."
  - Contact list rows. Each row has a 1px bottom border, padding 20px 0, a mono label on the left and Archivo 700 / 115% width / 22px on the right. Link rows shift right 10px and turn blue on hover.
    - Call / text: (281) 217-0461
    - Facebook: @magicbubblesdetailing ↗
    - Service area: Houston, TX 77056
- **Right column: form** in 4 fieldsets. Each legend is mono with a blue step letter.
  - **A Vehicle** (radio chips): Car (default), Truck / SUV, Van, Motorcycle, Boat / RV, Fleet (value "Fleet / Commercial").
  - **B Package** (radio chips): 01 · Wash & Wipe, 02 · Wash & Wax (default), 03 · Full Detail, Not sure.
  - **C Add-ons** (checkbox chips): Rims, Engine, Leather, Odor.
  - **D Details:** floating-label underline inputs on a 2-col grid:
    - Your name* · Phone*
    - Location / zip (home, office, job site) — full width
    - Preferred day & notes (textarea, 2 rows) — full width
  - **Chip styling:**
    - 46px tall pill, 1px `--line` border, Archivo 600, 108% width, 15px, uppercase.
    - Hover: the border turns foam.
    - Checked: foam background with ink text.
    - Focus-visible: 2px blue outline.
  - **Input styling:**
    - Transparent background, 1px bottom border, 18px text, padding 26px 0 12px.
    - Focus: the border turns `--blue`.
    - The label floats up to mono 11px `--blue-hi` when focused or filled.
  - **Live summary** (mono) beside the submit button, e.g. "**Car** · **Level 02** · + Rim detail".
  - Submit: blue pill "Send request →".
- **Validation:** name and phone are required. Empty required fields get a red bottom border (`oklch(0.65 0.2 25)` ≈ `#e5484d`), which clears on input.
- **Success state:** the form is replaced with a card that has a 1px blue border at 50% and radius 8px:
  - Mono "Request ready"
  - H3 "Thanks, {FirstName}." (Archivo 900, 125% width, 44px)
  - Copy: "For the fastest booking, call or text us now with your request — we'll confirm your price, date and location."
  - Buttons: **Call (281) 217-0461**, **Text request** (an `sms:` link with the whole request pre-filled as the body), and **Edit** (returns to the form).
- **Production note:** wire the submit to a real endpoint (email/SMS/CRM, e.g. Formspree, Resend, Twilio, or a serverless function). Keep the SMS fallback.

### 11. Footer
- Giant wordmark "MAGIC BUBBLES": Archivo 900, 125% width, `clamp(30px, 8.4vw, 220px)`, nowrap. The text is filled with a vertical gradient from `--foam` (at 20%) to `#3a3f45`.
- Bottom row (mono, `--mute`): "© Magic Bubbles Detailing · Houston, Texas · Est. 1999" and phone · Facebook · Back to top ↑.

### Mobile sticky call bar (≤720px)
- Fixed at the bottom with a 12px inset. Two equal pills: ghost "Call" (tel link) and blue "Get a quote". The footer gets 100px of bottom padding so the bar doesn't cover it.

---

## Interactions & Behavior
- **Smooth anchor scrolling:** `scroll-behavior: smooth`.
- **Reveal on scroll:** `.rv-up` elements start at opacity 0 and translateY(40px), then animate to their resting state over 1s `cubic-bezier(.2,.8,.2,1)` when 15% visible (IntersectionObserver, fires once). The stagger delay is `(index % 4) * 80ms`.
- **Hero parallax:** background translateY = scrollY × 0.25. It's only computed while the hero is near the viewport.
- **Iridescent bubbles (hero canvas):**
  - 28 bubbles on desktop, 14 below 720px wide, radius 6–52px (biased small).
  - They rise 0.2–0.7px per frame with a sine drift and recycle from the bottom.
  - Rendering: a radial gradient whose rim colors cycle through hue (hsla), a 0.8px white stroke at 22%, and a small white specular ellipse at top-left.
  - **Pointer within radius + 30px pops the bubble:** it grows ×1.04 per frame while fading out, then respawns.
  - Paused when offscreen. Disabled under `prefers-reduced-motion`.
  - DPR is capped at 2.
- **Services accordion and image swap:** described in Section 4. Hover only applies on `(hover:hover)` devices.
- **Package card spotlight:** pointermove sets `--mx/--my` for the radial glow.
- **CTA pre-selection:** "Quote this" sets the package radio; "Set up a fleet account" sets the vehicle radio. The summary updates either way.
- **Buttons:**
  - Pill height 46px, mono 12px, uppercase, letter-spacing .12em, `.25s` transitions.
  - Blue button hover: lighter blue plus translateY(-2px).
  - Ghost button hover: the border turns foam.
- **Pulsing dot** on "Get a quote": a box-shadow ping, 2s infinite.
- **Reduced motion:** all animations and transitions are disabled, and all content shows statically.

## Responsive
- **≤1080px:**
  - Nav links hide and the burger and drawer appear.
  - Services, Fleet, Quote and Story go to 1 column. In Services, the media panel becomes non-sticky, 16/10, and moves above the list.
  - Packages and Reviews go to 1 column.
  - Steps go to 2×2.
  - Section headers stack.
- **≤720px:**
  - The hero H1 wraps normally.
  - The spec strip goes 2×2.
  - The ghost phone button in the nav hides.
  - The two images, form fields, steps and vehicle list each go to 1 column.
  - The accordion body indent is removed.
  - The sticky call bar appears.

## State Management
- `activeService` (0–4).
- Form state: `vehicle` (string), `package` (string), `addons` (string[]), `name`, `phone`, `location`, `notes`, and `status` ('editing' | 'submitted').
- `navSolid` (bool, from scroll), `drawerOpen` (bool).
- No data fetching. Reviews and copy are static. If a backend is added: a POST to submit the quote request, plus a loading state and error state on the submit button.

## Design Tokens
| Token | OKLCH (source) | ≈ Hex |
|---|---|---|
| `--ink` (page bg) | oklch(0.14 0.008 250) | #0B0D10 |
| `--ink2` (raised bg) | oklch(0.18 0.01 250) | #131619 |
| `--ink3` (empty meter) | oklch(0.23 0.012 250) | #1D2125 |
| `--line` | white @ 12% | rgba(255,255,255,.12) |
| `--foam` (text / light bg) | oklch(0.97 0.004 240) | #F3F5F7 |
| `--mute` | oklch(0.72 0.01 250) | #A3A8AE |
| `--blue` (primary accent) | oklch(0.64 0.17 252) | #2F86E6 (based on the original brand blue #1773DA) |
| `--blue-hi` (highlight / hover) | oklch(0.74 0.14 235) | #4FB1F0 |
| Error | oklch(0.65 0.2 25) | #E5484D |

Hex values are close approximations. Prefer the OKLCH values.

**Typography**
- Display / UI: **Archivo** (Google Fonts, variable: `wdth` 62–125, `wght` 300–900). The look depends on `font-stretch: 110–125%` for expanded headlines.
- Labels / specs: **JetBrains Mono** 400/500. Mono label: 12px, letter-spacing .08em, uppercase.

| Use | Size | Weight / width | Line-height | Tracking |
|---|---|---|---|---|
| H1 | clamp(46px, 9vw, 176px) | 900 / 125% | .86 | -.03em |
| H2 | clamp(38px, 5.6vw, 96px) | 800 / 118% | .92 | -.025em |
| Package title | 48px | 900 / 125% | .9 | -.02em |
| Service row title | clamp(22px, 2.4vw, 34px) | 700 / 112% | — | -.01em |
| Lede | 18px | 400 | 1.55 | — |
| Body | 15–17px | 400 | 1.5–1.65 | — |

**Radii:** 6px (media), 8px (cards), 999px (buttons, chips, tags), 50% (oval mark, bubbles).

**Shadows:** none. Depth comes from borders, gradients and imagery.

**Easing:** `cubic-bezier(.2,.8,.2,1)` for reveals and expands; `cubic-bezier(.7,0,.2,1)` for the drawer.

## Assets
All images are in `img/`. They're CC/public-domain-style stock found via image search, and are stand-ins until the business supplies its own work photos.

| File | Used for |
|---|---|
| c1.jpg | Foam-covered black sedan (hero background, "At your driveway") |
| c3.jpg | Pressure-washing a white car (service 05) |
| c4.jpg | Hand-washing a black car with foam (service 01) |
| c5.jpg | Detailer cleaning a wheel (service 04) |
| c6.jpg | Tire-tread texture (fleet background) |
| c7.jpg | SUV headlights in the dark (fleet) |
| c9.jpg | Gloved hand polishing glossy paint (service 02) |
| c11.jpg | Hand drying paint ("At your office") |
| d3.jpg | Leather interior (service 03) |
| d4.jpg | Muscle-car rear in dramatic light (story) |
| logo-old.gif | The business's original oval logo (reference only; not used on the page) |

Other files in `img/` (c2, c8, d1, d2) are unused alternates.

Fonts load from Google Fonts. There are no icon libraries; the plus/minus and arrows are CSS or text characters.

## Content Sources
- **Facebook About:** Houston, TX 77056; (281) 217-0461; category Car Wash; price range $$.
- **Archived magicbubbles.net:** founding (Jan 1999), owner Tyrone Bush, mission statement, package contents, service list, commercial vehicle list and accounts.
- **Yelp** (via MapQuest): the three review excerpts.
- **Confirm with the client before launch:** current package contents, commercial account names, and whether to publish prices or an address.

## Files
- `src/Magic Bubbles Detailing.html` — the readable source (HTML, CSS and JS in one file). It references `../img/*`.
- `Magic Bubbles Detailing (standalone).html` — a single self-contained build with every asset inlined, for viewing offline.
- `img/` — image assets.
