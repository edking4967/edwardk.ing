# Instructions for rebuilding edwardk.ing

## Goal
Rebuild this Jekyll site as a clean, minimal literary writer portfolio. The current site is framed around teaching and engineering — replace that framing entirely with a literary writer identity.

## Design direction
- Minimal, spare, typographic. No clutter.
- Black or near-black text on white or off-white background.
- One serif font for the name/headings, one clean sans-serif for body.
- No gradients, no cards, no hero images unless a simple author photo is available.
- The aesthetic should feel like a literary journal or small press — serious, quiet, confident.
- Mobile responsive.

## Site structure
Two pages:

### 1. Index (home) — `index.md` or `index.html`
- Name: **Edward King**
- Tagline or one-liner (optional): something simple like "Writer. Teacher. Colorado."
- Short bio (use exactly this text):

> Edward King is a writer and teacher based in Colorado. He has been published in the University of Colorado Honors Journal and the Colorado's Emerging Writers series. He edits the journal [thousandonestories.com](http://thousandonestories.com) and posts detective stories on [coffeebreakreads.com](http://coffeebreakreads.com). He strives to write stories that help his readers discover new possibilities for joy in their lives.

- Publications list (see below)
- Links: [Thousand & One Stories](http://thousandonestories.com) | [Coffee Break Reads](http://coffeebreakreads.com)
- Contact: ed.king4967@gmail.com

### 2. About — `about.md`
- Same bio as above, slightly expanded if desired
- Can mention: CS/math/engineering teacher at The STEAD School in Denver, novelist in progress, background in firmware engineering and full-stack web development

---

## Publications list
List in reverse chronological order. Format each as: **Title** — *Publication* — Year

- **Still the One** — *Brilliant Flash Fiction* — 2025
- **B.** — *Short Beasts* — 2024
- **Bob Dylan's Beard** — *Z Publication: Colorado's Emerging Writers* — 2018
- **I Didn't Know a Counter Could Melt Like That** — *Z Publication: Colorado's Emerging Writers* — 2018
- **Bob Dylan's Beard** — *Flatiron Literary Review* — 2014
- **Fireworks** — *CU Honors Journal* — 2014
- **Things Change Fast** — *CU Walkabout Journal* — 2014
- **Origins of Roberto Blanco** — *Cultured Vultures* — 2013

---

## What to remove
- All references to "essays on teaching, engineering, and the places where they meet"
- The subtitle "Writing on Teaching, Engineering & Learning"
- The existing first post and any teaching/engineering content
- Any blog post structure — this is a static portfolio, not a blog

## What to keep
- The existing Jekyll setup, _config.yml, Gemfile
- GitHub Pages deployment
- The domain edwardk.ing if configured

## Navigation
Simple header: **Edward King** (links home) | Publications | About

## _config.yml updates
Update title, description, and any tagline fields to reflect the literary writer framing:
- title: Edward King
- description: Writer based in Colorado
- Remove any teaching/engineering references

## Notes
- Keep it simple. Resist adding features.
- No JavaScript required.
- If the current theme is Minima or similar, it's fine to keep — just update the content and config.
- If starting fresh, a plain HTML/CSS approach is also acceptable given the minimal requirements.
