# MITS — Company Website

### 🔗 Live site: **[rickrieger.github.io/Mits](https://rickrieger.github.io/Mits/)**

The company website for **MITS**, a class project at **Reynolds Community College** (2020).

The class split into two teams: one built the MITS application itself, a back-end plug-in tool for third-party marketplace sellers, and the other built this public-facing company website. I was on the website team and did most of the work on the site.

According to the site's "Our Product" section, MITS helps sellers on Amazon and other marketplaces (Biblio, Alibris, etc.) by:

- matching physical inventory against marketplace listings, so the item a buyer receives is the one they ordered
- sorting out multiple items that share the same ASIN but have different conditions (New, Like New, Very Good, Good, Acceptable)
- cutting the cost of returns caused by inventory errors
- stopping sellers from competing against their own listings through repricer algorithms

This was my first GitHub repository (August 2020).

![MITS hero section](assets/img/AdobeStock_317573075-shrunk.jpg)

---

## Contents

- [What's on the page](#whats-on-the-page)
- [Built with](#built-with)
- [How Bootstrap is used](#how-bootstrap-is-used)
- [Template and what I customized](#template-and-what-i-customized)
- [Contact form](#contact-form)
- [Run it locally](#run-it-locally)
- [Deployment](#deployment)
- [Cleanup log (November 2026)](#cleanup-log-november-2026)
- [Known limitations](#known-limitations)
- [Project structure](#project-structure)

---

## What's on the page

| Section | Contents |
|---|---|
| Hero | Headline and value proposition |
| Our Product | What MITS does, main features, benefits to sellers |
| Parallax banner | Full-width "Inventory Management" image that scrolls slower than the page |
| Prices | $49.99 start-up package for Amazon; hourly data-mapping for other marketplaces |
| Testimonials | Customer quotes |
| FAQ | Expandable questions and answers |
| Team | Photos and roles of the project team |
| Partners | Scrolling carousel of marketplace and AWS logos |
| Contact | Address, embedded Google Map, working contact form |

## Built with

| Technology | What it does here |
|---|---|
| HTML5 / CSS3 | Page structure and custom styling (`index.html`, `assets/css/style.css`); originally hand-edited in Adobe Dreamweaver |
| [Bootstrap 4.4.1](https://getbootstrap.com/docs/4.4/) | Responsive layout grid, spacing/alignment utilities, form styling, and the FAQ expand/collapse behavior ([details below](#how-bootstrap-is-used)) |
| [jQuery](https://jquery.com/) | Required by Bootstrap 4's interactive components; also used for smooth scrolling, the mobile menu and the contact form |
| [Owl Carousel](https://owlcarousel2.github.io/OwlCarousel2/) | The auto-scrolling partner logo strip |
| [AOS](https://michalsnik.github.io/aos/) (Animate On Scroll) | Fade/slide-in animations as sections scroll into view (40 elements use `data-aos`) |
| [parallax.js](https://pixelcog.github.io/parallax.js/) | The parallax "Inventory Management" banner |
| Boxicons & IcoFont | Icon fonts (menu, FAQ arrows, contact icons, social links) |
| [Formspree](https://formspree.io/) | Receives contact form submissions and emails them (added Nov 2026) |
| GitHub Pages | Free static hosting |

## How Bootstrap is used

### What Bootstrap is

[Bootstrap](https://getbootstrap.com/) is a free, open-source CSS and JavaScript framework, originally built at Twitter, for making websites that look good and adapt to any screen size without writing all the layout CSS yourself. It gives you:

- **A 12-column responsive grid.** You put content in `.row`s and `.col-*`s and say how many of the 12 columns each piece should take at each screen size. On a phone the columns stack vertically; on a laptop they sit side by side.
- **Utility classes.** Small single-purpose classes like `d-flex`, `mt-5` or `text-center` for spacing, alignment and display, applied directly in the HTML.
- **Pre-styled components.** Forms, buttons, navbars, collapsible panels, etc.
- **JavaScript plugins** (which in Bootstrap 4 rely on jQuery) for interactive pieces like collapse/accordion and modals.

Using it means the site is **mobile-friendly by default**. It's the reason this page reflows cleanly from a wide monitor down to a phone.

### Where it's used on this site

**1. Responsive grid: every section's layout.** The page uses `container` 11 times, `row` 10 times and `col-*` classes about 50 times. For example, each team card is wrapped like this:

```html
<div class="container">
  <div class="row">
    <div class="col-xl-3 col-lg-4 col-md-6"> <!-- one team member card -->
    <div class="col-xl-3 col-lg-4 col-md-6"> <!-- next card -->
```

The numbers are how many of the 12 columns a card takes at each screen size:

| Screen | Class that applies | Cards per row |
|---|---|---|
| Extra large (≥1200px) | `col-xl-3` (3 of 12) | 4 |
| Large (≥992px) | `col-lg-4` (4 of 12) | 3 |
| Medium / tablet (≥768px) | `col-md-6` (6 of 12) | 2 |
| Phone | none, so full width | 1 |

The hero uses ordering classes too: `col-lg-6 order-1 order-lg-2` puts that column first on phones but second (on the right) on large screens.

**2. Flexbox utilities: alignment.** `d-flex`, `align-items-center`, `justify-content-between` and `align-items-stretch` (used ~20 times) center the hero text vertically and make the contact columns equal height.

**3. Responsive images.** `img-fluid` (9 images) makes images shrink to fit their column instead of overflowing on small screens.

**4. Collapse plugin: the FAQ accordion.** Each question is a link with `data-toggle="collapse"`; Bootstrap's JavaScript shows or hides the matching answer panel. No custom JavaScript was needed:

```html
<a data-toggle="collapse" href="#faq2" class="collapsed">Is MITS easy to use?</a>
<div id="faq2" class="collapse" data-parent=".faq-list"> ...answer... </div>
```

**5. Form styling: the contact form.** `form-row`, `form-group` and `form-control` give consistent input sizing and spacing, with the name and email fields side by side on desktop (`col-md-6`).

**6. Visibility helpers.** `d-none d-lg-block` hides an element on small screens and shows it on large ones. The template's mobile menu uses the same approach (`d-lg-none`).

## Template and what I customized

The site started from **[Ninestars v2.0.0](https://bootstrapmade.com/ninestars-free-bootstrap-3-theme-for-creative/)**, a free Bootstrap 4 template by **BootstrapMade.com**, used under its [license](https://bootstrapmade.com/license/) (free use as long as the footer keeps a credit link; see [cleanup item 6](#6-restored-the-template-credit-link-in-the-footer)).

**From the template:** the overall section layout, base styles in `style.css`, the mobile menu and smooth scrolling in `main.js`, the bundled libraries, and the contact form markup.

**Added for MITS:**
- All content: product description, features, pricing, testimonials, FAQ, team bios, partner logos, contact info and Google Map
- All imagery: warehouse hero photo, MITS logo, team photos, testimonial photos, marketplace logos
- The parallax "Inventory Management" banner (parallax.js, not part of Ninestars)
- Custom styling changes in `style.css`

## Contact form

The form submits through [Formspree](https://formspree.io/), because GitHub Pages only serves static files and can't run server-side code. Messages go to the email address on the Formspree form. Every email's subject starts with `[MITS website]` and includes a `source` field, so it can be told apart from messages sent through other sites that use the same form.

## Run it locally

It's a static site with no build step:

```bash
git clone https://github.com/RickRieger/Mits.git
cd Mits
# then open index.html in a browser, or serve the folder with any static server
```

## Deployment

Hosted on **GitHub Pages** from the root of the `master` branch. Every push to `master` redeploys the site automatically within a minute or two.

---

## Cleanup log (November 2026)

All changes below were made on **2026-11-16** on the branch `readme-and-contact-form`, reviewed, and merged into `master`. Each item is its own commit, so it can be inspected or reverted on its own. None of them change the site's design.

### 1. Contact form made functional

**Why:** The form posted to a PHP script. GitHub Pages can't run PHP, and the template's PHP mail library was never included, so **every submission failed** and visitors had no way to reach the team.

**Before** (`index.html`):
```html
<form action="forms/contact.php" method="post" role="form" class="php-email-form">
```

**After:**
```html
<form action="https://formspree.io/f/mlezdedd" method="post" role="form" class="php-email-form">
  <input type="hidden" name="_subject" value="[MITS website] New contact message">
  <input type="hidden" name="source" value="MITS website (rickrieger.github.io/Mits)">
```

**Before** (`assets/vendor/php-email-form/validate.js`): expected the PHP script to reply with the text `OK`, so anything else was shown as an error:
```js
$.ajax({
  type: "POST",
  url: action,
  data: str,
  success: function(msg) {
    if (msg == 'OK') { /* show "sent" */ }
    else { this_form.find('.error-message').slideDown().html(msg); }
  }
});
```

**After:** asks Formspree for a JSON reply, checks its `ok` flag, shows Formspree's error messages, and labels the subject with the site name:
```js
var userSubject = $.trim($(this).find('input[name="subject"]').val());
$(this).find('input[name="_subject"]').val('[MITS website] ' + (userSubject || 'New contact message'));
...
$.ajax({
  type: "POST",
  url: action,
  data: str,
  dataType: "json",
  headers: { Accept: "application/json" },
  success: function(res) {
    if (res && res.ok) { /* show "sent", clear visible fields */ }
    else { /* show generic error */ }
  },
  error: function(xhr) { /* show Formspree's error messages */ }
});
```

The "clear the form after sending" selector was also changed from `input:not(input[type=submit])` to `input:not([type=submit]):not([type=hidden])`, so the hidden label fields aren't wiped after the first message.

### 2. Removed ~49 MB of unused duplicate files and editor clutter

**Why:** `assets/assets/` was a complete second copy of the assets folder, filled with download duplicates like `bootstrap(1).js` through `bootstrap(9).js`. Nothing on the page referenced it. There were also 51 Dreamweaver `_notes/dwsync.xml` sync files and 2 Mac `_DS_Store` files, which are editor/OS metadata, not website code. Together they made the repo about three times bigger than needed and made the real files hard to find.

**Before:**
```
assets/
├── assets/                          ← unused duplicate (49 MB)
│   ├── css/animate(1).css, animate(2).css, animate(3).css ...
│   └── vendor/bootstrap/js/bootstrap(1).js ... bootstrap(9).js ...
├── css/
│   └── _notes/dwsync.xml            ← Dreamweaver metadata
├── img/
│   └── clients/_DS_Store            ← macOS metadata
...
```

**After:**
```
assets/
├── css/
├── img/
├── js/
└── vendor/
.gitignore                           ← new: keeps _notes/ and .DS_Store out
```

Working-tree size went from about 73 MB to 24 MB.

### 3. Compressed the parallax background image (10 MB → 197 KB)

**Why:** `assets/img/AdobeStock_316523254.jpeg` was the original 8688×5792 stock photo, almost **10 MB**. Every visitor downloaded it just to show one banner, which made the page slow, especially on phones and mobile data.

| | Before | After |
|---|---|---|
| Dimensions | 8688 × 5792 | 2400 × 1600 |
| File size | 9.96 MB | 197 KB (≈98% smaller) |

2400px wide is still sharper than most screens show. The HTML didn't need to change because the file name stayed the same.

### 4. Fixed three broken file references

**Why:** Both pointed to files that don't exist, so the browser got errors instead of images.

**Favicon** (the small icon on the browser tab), `index.html`. The folder name (`gimg`) and extension (`.pn`) were typos, causing a 404 error on every page load and no tab icon:

```html
<!-- Before -->
<link href="assets/gimg/favicon.pn" rel="icon">

<!-- After -->
<link href="assets/img/favicon.png" rel="icon">
```

**Parallax background**, `assets/css/style.css`. The path pointed to a folder on the computer the site was originally built on (`Documents/ITD210 Rieger/`), which no visitor has. The page's banner currently uses parallax.js's `parallax-window` instead of this `.parallax` class, but the rule now points to the real image in case it's used:

```css
/* Before */
.parallax {
  background: url("../../../../Documents/ITD210 Rieger/AdobeStock_316523254.jpeg");
}

/* After */
.parallax {
  background: url("../img/AdobeStock_316523254.jpeg");
}
```

**Missing animate.css import**, `assets/css/style.css`. The stylesheet tried to import `animate.css` from `assets/css/`, but that file was never there, so every page load logged a 404 and the import did nothing. Removing the line changes nothing visually and clears the error:

```css
/* Before (line 8) */
@import url('animate.css');

/* After */
/* (line removed) */
```

### 5. Fixed typos and the ZIP code in page text

**Why:** Spelling mistakes on a company site hurt credibility. The ZIP code had six digits, so it couldn't be valid.

| Before | After | Where |
|---|---|---|
| Testomonials | Testimonials | Nav menu, section heading |
| effienciency | efficiency | Our Product |
| recieve | receive | Our Product |
| those cost anymore | those costs anymore | Benefits list |
| deminished | diminished | Testimonial |
| truely | truly | Testimonial |
| innitial | initial | FAQ |
| Glen Allen, VA 232612 | Glen Allen, VA 23060 | Contact section and footer. 23060 matches the address in the embedded Google Map |

```html
<!-- Before -->
<li><a href="#testomonial">Testomonials</a></li>
<p>10961 West Broad St, Glen Allen, VA 232612</p>

<!-- After -->
<li><a href="#testomonial">Testimonials</a></li>
<p>10961 West Broad St, Glen Allen, VA 23060</p>
```

The `#testomonial` anchor and the `assets/img/Testomonials/` folder name were left as they are, so existing links and image paths keep working.

### 6. Restored the template credit link in the footer

**Why:** BootstrapMade's free license requires the footer credit link to stay in place unless you buy the pro version. The link had been deleted, leaving only the template's comments saying it must stay.

```html
<!-- Before -->
<div class="credits">
  <!-- All the links in the footer should remain intact. -->
  ...
</div>

<!-- After -->
<div class="credits">
  <!-- All the links in the footer should remain intact. -->
  ...
  Designed by <a href="https://bootstrapmade.com/">BootstrapMade</a>
</div>
```

### 7. Added this README

Replaced the three-line `Readme.txt` (live link plus template credit) with this document.

---

## Known limitations

- **"Log in" is a placeholder.** It scrolls to the About section; the website had no login of its own. The application was built separately by the other team.
- **Testimonials and pricing are illustrative**, written for the class project.
- **jQuery is loaded twice** (a 1.11 copy from Google's CDN and the template's bundled copy). It works, but only one is needed. This was left alone to avoid changing behavior.
- `forms/contact.php` is the template's original PHP script. It's unused now that the form goes through Formspree, and is kept only for reference.

## Project structure

```
index.html            the whole page
assets/css/style.css  site styles (template + MITS customizations)
assets/js/main.js     smooth scrolling, mobile menu, carousel and animation setup
assets/img/           photos, logos, team and testimonial images
assets/vendor/        third-party libraries (Bootstrap, jQuery plugins, icon fonts)
  php-email-form/validate.js   contact form validation + Formspree submit
parallax.js-1.5.0/    parallax library
forms/                original template PHP contact script (unused)
.gitignore            keeps editor/OS clutter out of the repo
```
