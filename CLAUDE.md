# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static single-page marketing site for Giia Jeweler, a jewelry store at 4213 US-1, St. Augustine, FL 32086. It is built on the Start Bootstrap "Creative" theme. There is no build step, package manager, linter, or test suite. The site is served as-is by GitHub Pages at `https://giiajewelry.com/`, and `www` redirects to the apex domain.

## Running locally

```sh
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Structure

- `index.html`: all content. Sections are anchored by id (`#page-top`, `#about`, `#services`, `#portfolio`, `#faq`, `#contact`). Nav links use class `page-scroll` to get smooth scrolling.
- `css/creative.css`: the theme, with site-specific additions appended at the bottom (hero overlay, product cards, FAQ, contact map, footer). The accent color `#f05f40` is hard-coded throughout. The hero background is `img/header.jpg`, set here, not in the HTML.
- `js/creative.js`: smooth scroll, Bootstrap scrollspy (offset 51), navbar `affix` after 100px, closing the mobile menu on click, and WOW.js init. Elements with `wow <animation>` classes (from `animate.min.css`) animate on scroll.
- `robots.txt`, `sitemap.xml`, `favicon.svg`: served from the site root.

## Local SEO: keep these in sync

The business name, address, and phone (NAP) appear in several places, and search engines penalize inconsistencies. When any of them changes, update all of these:

- `<title>`, meta description, `og:*` tags, and the `geo.*` / `ICBM` meta tags in `<head>`
- the `JewelryStore` JSON-LD block in `<head>` (address, `geo`, `telephone`, `areaServed`)
- the About paragraph, FAQ answers, Contact `<address>`, map and directions links, and the footer
- `sitemap.xml` `lastmod`

Store hours and a contact email are intentionally absent until they are confirmed. The domain has no MX records, so no `@giiajewelry.com` address works. A TODO comment in the Contact section marks where hours go.

## Dependencies

- jQuery 3.7.1 (cdnjs), plus Bootstrap 3.4.1 CSS and JS (jsDelivr). `creative.js` depends on Bootstrap 3 plugins (scrollspy, affix, collapse), so do not upgrade to Bootstrap 4+ without rewriting it.
- Font Awesome 6.7.2 (cdnjs). Use FA6 class names (`fa-solid fa-gem`), not FA4 names (`fa fa-diamond`).
- Vendored and loaded: `js/jquery.easing.min.js`, `js/wow.min.js`, `css/animate.min.css`.
- Vendored but unused: `js/jquery.js` (1.11.1), `js/bootstrap.js`, `js/bootstrap.min.js` (3.3.2), `js/jquery.fittext.js`, `js/cbpAnimatedHeader.js`, `js/classie.js`.
