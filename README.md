# Alejandro Medina Sandín — Academic Website

Personal academic / economics job-market website. **Static site, ready to deploy as-is** (e.g. GitHub Pages). Vanilla HTML/CSS/JS — no build step, no frameworks, no dependencies other than Google Fonts.

> Note for Claude Code: these files are the **production deliverable**, not a throwaway prototype. You can edit and ship them directly. Keep it framework-free unless the owner explicitly asks to migrate.

## File structure

```
index.html       Home — hero, photo, primary links, bio, research fields, JMP highlight
research.html    Research — Working Papers (abstract beside figure), Awards, Work in Progress, Conferences
cv.html          Curriculum Vitae — download button + HTML summary (education, awards, positions, teaching, training, software, languages)
contact.html     Contact — email, office, profiles (SSRN, LinkedIn), references
style.css        Single shared stylesheet (design tokens at the top in :root)
script.js        Mobile menu toggle + subtle fade-in on scroll
figures/         Paper figures (PNG)
```

Header and footer are replicated verbatim across all four pages. Links between pages are **relative**, so the site works from any subpath on GitHub Pages.

## Still to add (filenames already wired in the HTML)

- `profile.jpg` — square portrait for the Home hero. Currently a striped placeholder; in `index.html` swap the `.hero-photo--placeholder` div for the commented-out `<img>` line right below it.
- `CV_Medina_2026.pdf` — linked from the CV page and the footer of every page.

## Design system (tokens in `style.css` `:root`)

| Token | Value | Use |
|-------|-------|-----|
| `--bg` | `#ffffff` | Page background |
| `--ink` | `#1a1a1a` | Primary text |
| `--muted` | `#6b6b6b` | Secondary text |
| `--hairline` | `#e6e6e6` | Borders / rules |
| `--accent` | `#1b3a5c` | Links, hover, small rules (deep academic navy) |
| `--accent-hover` | `#2a527e` | Link hover |
| `--accent-tint` | `#f4f6f9` | JMP box / paper-row background |
| `--maxw` | `760px` | Centered content column |

- **Type:** Source Serif 4 (600/700) for headings + name; Inter (400/500) for body/nav. Base 17–18px, line-height ~1.65.
- **Responsive:** mobile-first; nav collapses to a hamburger below 640px. Working-paper rows widen past the text column at ≥1080px so each abstract sits compactly beside its figure.
- **Accessibility:** semantic HTML5, visible focus states, `aria-label` on the menu toggle, `prefers-reduced-motion` honored.
- **Animation:** none beyond an optional, very subtle fade-in on scroll (disabled under reduced-motion).

## Deploy (GitHub Pages)

1. Put the contents of this folder at the repo root (or in `/docs`).
2. Add `profile.jpg` and `CV_Medina_2026.pdf` alongside the HTML files.
3. In the repo: **Settings → Pages → Build from branch**, pick the branch and folder.
4. Done — `index.html` is the entry point.

## Editing notes

- Each working paper is a `<li class="paper">` with a `.paper-grid` (figure left, content right). Abstracts are always-visible `<p class="abstract-body">` — no toggle.
- To add a paper: copy an existing `<li>` block, swap the title/status/abstract, and point the `<img>` at a new file in `figures/`.
- Conference and Award entries use `<ul class="conf-detailed">` list items.
- `© 2026` and the owner's name/title live in the footer of all four pages — update in all four if changed.
