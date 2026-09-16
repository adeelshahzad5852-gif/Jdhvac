# JD HVACR Solutions — website

Static site for **JD HVACR Solutions LLC**, Spring, Texas. Built by GoodcallAI.

Plain HTML and CSS. **No framework, no build step, no JavaScript.** Open any
`.html` file in a browser and it works. Deploys to Vercel as-is.

---

## Before this can go live — four things

| # | What | Who |
|---|------|-----|
| 1 | **Register the domain** in Daniel's name. Everything is written for `jdhvacrsolutions.com`. | Adeel |
| 2 | **Get Daniel's Texas TACL license number.** It appears in the footer of all five pages as `TACL######` in an amber box, impossible to miss. Every competitor shows theirs. | Daniel |
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

**Every photo on the site is a real JD HVACR Solutions job. There is no stock
photography anywhere.** None of the seven competitor sites reviewed could say
that.

### Deliberately left out — do not add without asking Daniel

- **The photo of the child** beside an open Rheem condenser. It is public on his
  Google profile, but a child's face on a business website is his call, not ours.
- **Two photos with Mattress One signage readable** (the crane lift and the
  storefront). Showing a client's brand implies a relationship they did not
  agree to publish.

---

## Decisions already made — do not reopen

- **Both commercial and residential.** The reviews are 9-out-of-10 residential;
  the photos are 9-out-of-12 commercial. Each page carries the evidence that fits it.
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
