# Personal site + notes — design

Date: 2026-06-22
Status: approved (lightweight build)

## Goal

A barebones personal website for Peter Preketes to write notes and thoughts by
hand in Markdown, in the spirit of alisawuffles.github.io. Hosted free on GitHub
Pages under the PeterP22 account at <https://peterp22.github.io>.

## Scope (MVP)

- Home page: photo/initials, name, role ("Forward Deployed AI Engineer"), a
  one-line bio, social links (X, GitHub, LinkedIn, Email), and a
  reverse-chronological Notes list (`date — title`).
- Note pages: one page per note at `/notes/<slug>/`, rendered from Markdown.
- Light mode only ("B" minimal + brand on a warm off-white). A light/dark toggle
  was built then removed 2026-06-22 — Peter prefers light only, fits his style.

Out of scope for now (easy to add later): projects/about pages, RSS, comments,
analytics, custom domain.

## Tech

- Jekyll on GitHub Pages, "deploy from a branch" (no Actions, no local toolchain
  required to publish — GitHub builds Markdown to HTML server-side).
- Plain CSS, no Sass pipeline. One plugin: jekyll-seo-tag for share previews.
- No JS framework. ~25 lines of vanilla JS for the theme toggle.

## Brand

Nocturne Blurple tokens + Bricolage Grotesque (bundled woff2) from the
personal-brand skill. Headings in Bricolage; note body in a system serif for an
editorial feel; dates/footer in system mono. Light mode is a derived
violet-on-off-white counterpart; dark mode is the canonical palette.

## Files

```
_config.yml            site config, permalinks, seo
index.html             home (profile + notes list)
_layouts/default.html  shell: head, theme init, toggle, footer
_layouts/note.html     single note
_posts/*.md            the notes (Markdown)
assets/css/style.css   brand + light/dark tokens
assets/js/theme.js     toggle behaviour
assets/fonts/*.woff2   Bricolage Grotesque 400/500/700/800
```

## Publish workflow

Create `_posts/YYYY-MM-DD-title.md` with `title` + `date` front matter, write
Markdown, commit, push. Live in ~30s. No CMS.

## Verification

- Look verified via inline mockup before the first push.
- Build verified by the GitHub Pages deployment after the first push (the local
  Ruby is too new to build locally, and is not needed to publish).
