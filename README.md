# peterp22.github.io

My personal site, notes, and the pillars of what I'm building. Jekyll on GitHub
Pages. Live at <https://peterp22.github.io>.

## Two kinds of content

- **Pillars** — evergreen pages in `_pillars/`, one per theme (gaming, strength,
  the work, calling, lessons). These are the spine of the site. Grow them over time.
- **Notes** — dated posts in `_posts/`. Short, timestamped writing.

## Write a new note

1. Add a file in `_posts/` named `YYYY-MM-DD-some-title.md`.
2. Put this at the top (the `pillar` line is optional — it files the note under a pillar):

   ```yaml
   ---
   title: "Your title here"
   date: 2026-06-22
   pillar: strength
   ---
   ```

3. Write the note in Markdown below the second `---`.
4. Commit and push. Live in about 30 seconds:

   ```bash
   git add . && git commit -m "note: your title" && git push
   ```

## Fill in a pillar

Open the matching file in `_pillars/` and write below the front matter:

| Pillar | File | `pillar:` value for notes |
|---|---|---|
| Gaming → Code | `_pillars/gaming-to-code.md` | `gaming-to-code` |
| Strength | `_pillars/strength.md` | `strength` |
| The Work | `_pillars/the-work.md` | `the-work` |
| Calling | `_pillars/calling.md` | `calling` |
| Lessons | `_pillars/lessons.md` | `lessons` |

To add a new pillar, drop another file in `_pillars/` with `title`, `order`, and
`summary` front matter. It appears on the home page automatically.

## Edit your profile

Name, role, bio, and links live in `index.html`. For a real photo, drop it at
`assets/img/me.jpg` and follow the comment near the top of that file.

## Dark mode

Toggle is top right. It remembers the visitor's choice and follows their system
setting on first visit. Colors live in `assets/css/style.css` under
`:root[data-theme="light"]` and `:root[data-theme="dark"]`.

## Run it locally (optional)

Not needed to publish. For live preview:

```bash
bundle install
bundle exec jekyll serve
```

Then open <http://localhost:4000>.
