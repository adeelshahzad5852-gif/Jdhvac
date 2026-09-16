# JD HVACR Solutions — website

Static site for **JD HVACR Solutions LLC**, Spring, Texas. Built by GoodcallAI.

Plain HTML and CSS. **No framework, no build step, no JavaScript.** Open any
`.html` file in a browser and it works. Deploys to Vercel as-is.

---

## Before this can go live — four things

| # | What | Who |
|---|------|-----|
| 1 | **Register the domain** in Daniel's name. Everything is written for `jdhvacrsolutions.com`. | Adeel |
| 2 | **Get Daniel's Texas TACL license number.** The whole TDLR footer block is **commented out** on all five pages behind a `LAUNCH BLOCKER` comment, because publishing "Regulated by the TDLR" without a number asserts a license nobody here has verified, and a visible `TACL######` redaction looks worse than no line at all. Uncomment it and fill in the number on all five pages. Every competitor shows theirs. | Daniel |
| 3 | **Point Vercel at this repo.** Root directory, no build command, output is the repo root. | Adeel |
| 4 | **Add the website URL to his Google Business Profile.** It is currently blank. This is what actually sends traffic to the site. | Daniel |

### Changing the domain

The domain appears in exactly four places. Find and replace `jdhvacrsolutions.com`:

- `<link rel="canonical">` in each of the five pages
- the JSON-LD block in `index.html`
- `robots.txt`
- `sitemap.xml`

---

## Pages

| File | What is on it |
|------|---------------|
| `index.html` | Hero with three problem buttons, residential/commercial split, 6-photo gallery, 3 reviews, service areas, 6-question FAQ. Carries the LocalBusiness schema. |
| `commercial.html` | Four commercial service cards, 9-photo gallery, 3 reviews including the business customer, why-a-smaller-contractor section. |
| `residential.html` | Four residential service cards, 6 homeowner reviews, 6-question FAQ. |
| `about.html` | Who Daniel is, **all ten Google reviews in full**, the pattern across them. |
| `contact.html` | Three-field form, call/text card, service areas, map, what to have ready. |
| `404.html` | Not-found page. Sends people to the phone, not a search box. |

---

## The contact form

Posts straight to **Web3Forms** as a normal HTML form. No JavaScript involved.

- Access key `a9d05928-993d-4cca-905a-5817f4d2543c` in `contact.html`
- Free tier: 250 submissions a month
- **Adeel's email address appears nowhere in the code.** Web3Forms stores the
  destination on their server; the page only carries the key.
- A honeypot field (`botcheck`) catches basic spam bots
- On submit, Web3Forms shows its own success page

### Two things to change later

1. **This key is shared with goodcallai.org.** Daniel's inquiries currently land
   in the same inbox as GoodcallAI leads and share the same 250/month cap.
   Create a separate Web3Forms key for JD HVACR and swap the value in
   `contact.html`.
2. **Once the domain exists**, add a redirect so people land back on the site
   instead of Web3Forms' page. One line inside the `<form>`:
   ```html
   <input type="hidden" name="redirect" value="https://www.jdhvacrsolutions.com/thanks.html">
   ```
   It needs an absolute URL, which is why it is not in there yet.

---

## Photographs

11 images in `assets/img/`, all taken from Daniel's own Google Business Profile
and resized to 1400px wide, ~1.9MB total.

**Every photo on the site comes from Daniel's own Google Business Profile, and
there is no stock photography anywhere.** None of the seven competitor sites
reviewed shows a single photograph of a finished job — they run stock images,
team portraits or SVG placeholders. This is the site's strongest asset.

The site says "from the Google Business Profile" rather than "a job this LLC
did", because that is what has actually been verified. If Daniel confirms all
eleven are his own LLC's work, the wording can be strengthened.

### Deliberately left out — do not add without asking Daniel

- **The photo of the child** beside an open Rheem condenser. It is public on his
  Google profile, but a child's face on a business website is his call, not ours.
- **Two photos with Mattress One signage readable** (the crane lift and the
  storefront). Showing a client's brand implies a relationship they did not
  agree to publish.

---

## Decisions already made — do not reopen

- **Both commercial and residential.** Reading the review text, most describe
  work in homes (one, High-Octane Performance, is plainly a business); the
  photos are 9-out-of-12 commercial. Each page carries the evidence that fits
  it. Note the residential/commercial split of the reviews is an inference from
  their wording, not a stated fact — do not put a number on it on the site.
- **No prices anywhere.** No financing, no maintenance plans, no coupons,
  no diagnostic fee. Adeel's instruction.
- **No equipment brand logos.** Carrier and Rheem appear in photographs and in
  image alt text because that is what is in the picture, but no partner or
  dealer badge is claimed. Daniel holds no such certification.
- **No Spanish.** Adeel is asking Daniel separately.
- **No 24/7 claim.** Hours are 8am–5pm. After-hours is worded as Daniel
  actually described it: extreme temperatures come first, no heat in winter,
  no cooling in summer.
- **No invented testimonials, statistics, years-in-business or client logos.**
  Everything on the site is verifiable.
- **Call and text both**, on (281) 706-8336.
- **US spelling throughout.**

---

## Design

| Token | Value | Use |
|-------|-------|-----|
| `--ink` | `#14161a` | Headers, footers, dark sections |
| `--amber` | `#ffa400` | Buttons, accents, the rule under the header |
| `--amber-deep` | `#a35f00` | Amber on light backgrounds, for contrast |
| `--paper` | `#fbfaf7` | Page background |

Type is **Barlow Condensed** for headings, **Inter** for body, both from Google
Fonts.

Six of the seven competitor sites reviewed are blue and white. Charcoal and
safety amber keeps Daniel out of that pile, and it is not GoodcallAI's orange
either — his site should not look like a GoodcallAI product.

### Things that work without JavaScript

- FAQ accordions use native `<details>` / `<summary>`
- Mobile navigation wraps to a second row rather than hiding behind a hamburger
- The call/text bar fixed to the bottom of the screen on phones is pure CSS
- The form is a plain HTML POST

---

## Local preview

```bash
cd /home/user/jdhvac
python3 -m http.server 8000
```

Then open `http://localhost:8000`. No install step, no dependencies.


---

## Audit findings, and what was done about them

Three independent audits were run against the finished site. What changed:

**Invented facts removed**
- **Six service-area towns Daniel never named** — Klein, Humble, Westfield, Oak
  Ridge North, Conroe and Magnolia were added from competitor lists. All six are
  gone. The site now lists only the four he stated: Spring, Tomball, The
  Woodlands, Northeast Houston. Magnolia and Conroe are 20+ miles the wrong way;
  leaving them in would have generated calls he has to turn down.
- **"Nine of the ten reviews are from homes in North Houston"** — the residential
  split was an inference and the locations were invented outright. Reworded.
- **Alt text describing "two technicians"** on four images, on a site whose whole
  argument is that there is one man. One of the men in the rooftop photo wears
  another company's branded polo. All head-counts removed.
- **"Carrier WeatherMaker" (plural)** — only one unit in the photo carries that
  badge. Reduced to "Carrier".
- **Capability claims with nothing behind them** — "redundant pairs where
  downtime is not an option", "first fix through to commissioning", "multi-unit
  buildings and suites", "property managers with several sites", "curb adaptation
  and flashing". All removed. Ask Daniel before putting any of them back.
- **"One name on the van"** — nothing says he has a van, and the one photo with
  vehicles shows two. Changed to "truck".
- **"The same three things, ten times over"** — the columns quote seven reviews,
  not ten.

**Accuracy fixes**
- Two reviews on the commercial page were **silently truncated** on a page that
  promises word-for-word quoting. Both restored in full.
- A **homeowner's review sat under a "business customer" heading**. Relabelled.
- A caption said spiral duct ran "through a warehouse floor". It runs above it.
- "Phone lines get answered first" — he has one phone.

**Privacy**
- The contact map **dropped a pin on 23107 Good Dale Ln, which is his house**.
  The marker is gone and the map now shows the service area instead. The street
  address still appears nowhere on the site, and the JSON-LD deliberately omits
  `streetAddress`.

**US register**
- Spelling was already clean, but the vocabulary was British: "turns up", "live
  kit", "first fix", "timber ceiling", "done properly", "fit-out". All changed to
  what a Texan would say.

**Still open — needs Daniel, not us**
1. **Are all 11 photographs jobs this LLC did?** They come from his own Google
   profile, so the site now says exactly that and no more. If any predate the LLC
   or came from a previous employer, say so.
2. **Crane lifts, equipment-room work, new construction** — confirm he does each.
3. **Is he insured?** The word appears nowhere on the site because nobody has
   confirmed it. Every competitor says it. One sentence would close a real gap.
4. **How long has he been doing this?** Competitors state 15 years, 30 years,
   since 1978. Silence reads as brand new.
5. **A photograph of Daniel.** The site names him seventeen times and never
   shows him.

**Deliberately NOT done**
- No response-time or same-day promise was added. Unverified.
- No email address was added — Adeel's instruction.
- No separate equipment-room page was built. It is the rarest thing he does and
  no competitor advertises it, so it is worth its own page later, but that is a
  scope decision for Adeel.
