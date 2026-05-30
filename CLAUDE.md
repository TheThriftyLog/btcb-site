# CLAUDE.md — Between the Covers Bookshop Website

Instructions and context for Claude Code working in this repo. Read this at the
start of every session.

---

## Project overview

Single-page marketing/storefront-gateway site for **Between the Covers Bookshop**,
a veteran and woman-owned independent bookshop in
Harrisburg, PA. The site introduces the shop and funnels visitors to the Square
Online store for actual purchases; it is not an e-commerce site itself.

- **Live:** https://betweenthecoversbookshop.com (Cloudflare Pages)
- **Repo:** public — never commit secrets, API keys, or tokens
- **Deploy:** Cloudflare auto-deploys from `main` on every push

---

## Tech stack & hard constraints

- **Vanilla HTML, CSS, and JavaScript only.** No frameworks, no build step, no
  bundler, no npm dependencies for the site itself.
- Everything lives in a **single `index.html`** (HTML, CSS, and JS together).
- Fonts: Playfair Display, Lora, Cormorant Garamond (Google Fonts).
- **Color palette** (extracted from the shop's hand-drawn logo — stick to these):
  - Burgundy/wine: `#943039`, `#5c1d25`
  - Warm golds: `#d0b366`, `#ddc176`
  - Dusty roses: `#e3a6ac`, `#fde0e0`
  - Earth tones: `#685b53`, `#312a2b`

> Do **not** introduce a framework, build tool, or new dependency without first
> flagging it, explaining the tradeoff, and getting the go-ahead. The no-build,
> single-file simplicity is intentional.

---

## File structure

```
btcb-site/
├── index.html              # the entire site
├── README.md
├── wrangler.toml           # Cloudflare auto-generated config — leave alone unless asked
└── assets/
    ├── BTCB_Colored_Smaller_SVG.svg   # colored emblem, used in hero
    └── wordmark.svg                    # text-only logo, used in nav + footer
```

---

## Dev & deploy workflow

1. Edit `index.html` locally.
2. Preview: from the repo folder, `python3 -m http.server 8000`, then open
   http://localhost:8000.
3. Deploy: `git add . && git commit -m "message" && git push`. Cloudflare picks
   it up automatically.

When you make changes, default to leaving the commit/push to me unless I ask you
to handle git — I like to review the diff first.

---

## Asset / logo notes

- SVGs are exported from Inkscape. Any new Inkscape export must use
  **File → Document Properties → "Resize to content"** first, or the viewBox ends
  up as a full A4 page.
- **Do not** try to shrink the emblem SVG by reducing path precision — it visually
  warps the artwork. Use the original Inkscape exports as-is. If file size becomes
  a real performance problem, raise converting to WebP/PNG as an option instead.

---

## Current state

**Built and working:** hero with emblem logo, sticky nav + mobile hamburger,
"Our Story" section, three offering cards, Staff Picks (dark section), Visit Us
section with address/hours/contact + Google Maps embed, footer with social links,
scroll fade-in animations, full SEO meta tags. "Shop" links open the Square Online
store.

**Intentionally deferred (don't add unless I ask):** newsletter signup
(waiting on Mailchimp), interior photos (waiting on renovations), a real events
page, Ingram iPage integration, custom `shop.` subdomain, `www.` alias.

---

## How to work with me (Logan)

My deeper learning focus is **robotics software — C++, Python, Bash, and URDF** —
and that's where I want to be pushed hard and quizzed often. The bookshop site is
a genuine learning project too, and it's all interrelated, but here I'm
deliberately trading a bit of that depth for **pace**: my goal is to get the shop
scaled and running in a reasonable amount of time so it buys me the work-life
balance to dig into robotics development. So on this project specifically:

- **Default to moving efficiently.** Give me the working approach and feel free to
  just write the fiddly parts (tricky JS, layout math, anything that would slow us
  down). I don't need to hand-write everything here.
- **Still let me take the parts I can** — HTML structure, CSS tweaks, copy — but if
  I say "keep moving," don't wait on me.
- **Quiz me occasionally, but lightly.** A quick "why does this work?" or "what
  would you change here?" now and then keeps me sharp — just less often than you
  would on a robotics project.
- **When something here transfers to robotics, go a little deeper.** Bash, general
  programming patterns, problem decomposition, git workflow — those are worth a
  short aside since they carry over. Pure web/CSS trivia doesn't need one.
- As the shop stabilizes and frees up time, I'll tell you to shift the dial back
  toward more hands-on learning.
