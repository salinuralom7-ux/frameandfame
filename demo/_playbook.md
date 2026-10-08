# Demo website playbook

Rules for every demo site under `/demo/`. The daily lead run follows this
file; so should anyone building a demo by hand. Files starting with `_` are
not published by GitHub Pages.

## 1. Who qualifies

Established local businesses in Assam, tier-2 and tier-3 towns first:
Bongaigaon, Kokrajhar, Gossaigaon, Dhubri, Goalpara, Barpeta, Nagaon, Hojai,
Tezpur, Mangaldoi, Nalbari, North Lakhimpur, Jorhat, Golaghat, Sivasagar,
Dibrugarh, Tinsukia, Silchar, Karimganj, Diphu.

Categories, in order of preference:
1. Private hospitals and nursing homes
2. Eye hospitals, dental hospitals, multi-doctor clinics, physiotherapy centres
3. Private schools (CBSE / SEBA / English-medium), junior colleges, degree colleges
4. Coaching institutes with a fixed campus
5. Pathology labs (blood tests only — see exclusions)

**Exclude:**
- Anything that already has its own website. A Facebook page or a hospital-chain
  profile page does not count as a website; a listing that says "Visit our
  website" does, until you prove the link goes somewhere else.
- Cancer hospitals and cancer treatment (Drugs and Magic Remedies Act).
- Ultrasound / sonography / imaging-led diagnostic centres (PCPNDT Act).
- Government facilities, Apollo/Fortis/Narayana and other chains, franchises.
- Solo doctors who practise inside a bigger hospital (they usually have a
  hospital profile and no budget authority).
- Very small shops.
- **Exclusivity:** do not target the same category in the same district as a
  Frame & Fame client: schools in Kokrajhar and Hojai districts; car service
  centres in Kokrajhar; physiotherapy and spine clinics anywhere near
  Dr. Hoque Spine Care; English coaching near Shimultapu / Srirampur.
- Anything already in `/demo/` (check the folder names first).

## 2. Verifying "no website"

For each candidate run at least two searches:
`"<exact name>" <town>` and `"<name>" <town> official website`.

- Reject if any result is the business's own domain.
- Reject if a directory shows a website field for it.
- Big signals that a site probably exists (100+ beds, NABH, "super-speciality",
  a group name): mark **check first**, do not build.
- Otherwise mark **no website found**. Say plainly that search coverage is
  imperfect; the owner still taps the Google Maps link before calling.

Phone numbers: take them from PM-JAY registries (publicservicesmap.in,
drlogy.com), CBSE SARAS, school/college directories or news. Never use
Justdial numbers starting 97248…, 08460…, 09724… etc. — those are forwarding
numbers. If the only number is a forwarding number, say so.

## 3. What the demo must be

The bar is: the owner opens it on a ₹10k Android phone on WhatsApp and
thinks "this is mine, and it's better than I imagined".

- One page, mobile-first, no build step. Folder: `/demo/<slug>/` with
  `index.html`, `og.jpg` (1200×630 WhatsApp preview) and any images.
  Slug: lowercase-hyphenated name + town, e.g. `life-care-hospital-goalpara`.
- **Designed for the category**, not a reskin. Its own palette and type pair
  (Google Fonts). A hospital, a school and an eye clinic must look like
  different studios made them. Reference standard:
  `/demo/dr-abhay-agarwal/`.
- Sections (adapt to category): hero with name, category, town and two CTAs
  (call + WhatsApp/book); a stat band of *verified* facts only; services /
  departments / courses as icon cards; why-choose-us from verified facts;
  how-to-visit or admissions steps; enquiry form that opens WhatsApp with a
  pre-filled message; Google Maps embed
  (`https://maps.google.com/maps?q=<name+town>&z=15&output=embed`) with a
  styled fallback behind it; hours; FAQ; footer.
- Sticky bottom bar on phones: Call · Map · Book/Enquire.
- Scroll-reveal animations, respect `prefers-reduced-motion`.
- `<meta name="robots" content="noindex, nofollow">`, full Open Graph tags
  with an absolute `og:image` URL on frameandfame.in.
- Top strip: "**Demo website** prepared by Frame & Fame for <name> · Not the
  official site · frameandfame.in". Footer credit: "Website by Frame & Fame".
- Phone number in one JS constant near the end so it is a one-line swap.

**Never invent:** reviews, ratings, testimonials, quotes, doctor names,
qualifications, bed counts, results, years, awards, prices. Use only facts
found in sources; where something is missing use a tasteful placeholder
("Your photos here", "Add your faculty") — that is the reason they hire us.
Health pages: no cure or guarantee language, no "best", nothing that implies
knowledge of the reader's condition. No logos of other organisations.

Images: no stock photos of fake staff. Use illustration, iconography,
gradients and typography. Real photos only if they are the business's own
and publicly posted.

## 4. Checks before publishing

1. Render with Playwright (`executablePath: '/opt/pw-browsers/chromium'`) at
   390×844 (deviceScaleFactor 2) and 1440×900. Google Fonts are blocked in
   the cloud sandbox: inject fonts from `npm i @fontsource/<family>` as
   base64 `@font-face` for screenshots only.
2. `document.documentElement.scrollWidth` must equal the viewport width.
3. Look at the screenshots. Fix anything cramped, overlapping, misaligned
   or blank. Repeat until it is genuinely good.
4. Generate `og.jpg` the same way (1200×630).
5. Commit to `main` (one commit per demo or per batch) and push. GitHub
   Pages publishes `https://frameandfame.in/demo/<slug>/` in about a minute.
