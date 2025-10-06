# Temorary Files from OWG
## temp-ogw two files:
- md with front matter posts and pages
- separated in branches img files

  # Scripterix Jekyll / Liquid architecture audit (Einstein agent)

## 1. Build + runtime overview

- Static generator: Jekyll 4.4.1 (Ruby 3.4 runtime on Windows)
- Key plugins: `jekyll-feed`, `jekyll-reading-time`, `jekyll-paginate-v2`
- Collections: `_posts`, `_logbook`, `_works`; all configured with `output: true`
- Localization: custom plugin `_plugins/i18n.rb`, translation dictionaries in `_locales/en.yml` and `_locales/pl.yml`
- Data endpoints: Liquid-powered JSON via `_layouts/data-json.html` + include `_includes/data-object.liquid` (consumed at `/assets/data/{posts,logbook,stats}.json` and `/search.json`)
- Assets: CSS in `assets/css/main.css`, JS includes like `assets/js/portfolio-filter.js`

## 2. Content flows (EN/PL)

- Pages exist in both root (`/archive/`) and `/pl/` prefix; each page declares `lang` front matter
- Data queries filter localized content with `where: 'lang', current_lang`, except aggregate stats (global totals)
- Translation keys resolved with Liquid filter `| t` (reads from `_locales`) and optional `title_key`, `description_key`

## 3. Dependency graph highlights

- `archive/index.markdown` → layout `page` → uses translation strings + collections to render stats + timeline
- `challenge10k/` pages rely on `_includes/logbook-entries.html` (not shown here but referenced)
- Portfolio: `_includes/portfolio-page.html` consumes `_data/stats.json` + `_works` collection + search JSON
- Search: `search.json` consolidates `_posts` + `_logbook` for client-side filtering in archive UI

## 4. Deployment readiness checklist

- `bundle exec jekyll build` (or `serve --trace`) runs cleanly after latest edits (no Liquid exceptions)
- `_site` contains JSON assets required by frontend (posts/logbook/stats/search)
- `assets/images/portfolio/` hosts placeholder hero (`coding01.jpg`) used by all works
- Stats data updated manually via `_data/stats.json`; consider scripting future updates
- No pending TODOs in repo; translations exist for keys used in templates

## 5. Authoring guide

### Posts (`_posts/`)

1. Duplicate an existing entry (EN or PL). Filename pattern `YYYY-MM-DD-title-lang.md`.
2. Front matter keys:
   - `layout: post`
   - `title`
   - `date`
   - `categories` (array)
   - `lang`: `en` or `pl`
   - `translation_key`: identical between language variants for pairing
   - Optional: `writing_hours`
3. Body text in Markdown; ensure translated counterpart shares `translation_key` but has `lang: pl`.

### Logbook (`_logbook/`)

1. Filename pattern `YYYY-MM-DD-slug.md`.
2. Required front matter: `lang`, `title`, `date`, `hours_spent`, `focus_area`, optional `cumulative_hours`, `tags`.
3. Author notes in Markdown. Each entry auto-outputs under `/challenge10k/log/{slug}/`.
4. Link entries to works via `related_work` or `logbook_ref` (from work file).

### Works (`_works/`)

1. Filename example: `2018-project-name.md`.
2. Front matter includes `layout: work`, `title`, `slug`, `date`, `year`, `lang`, `tech` (array), `summary`, `status`.
3. Optional references: `logbook_ref` (array of log entry IDs), `github_repo`.
4. Content in Markdown describes the project; works appear on `/challenge10k/` portfolio layout and `archive/works` table.

## 6. Einstein agent notes

- All JSON generators now share the `data-json` layout; front matter drives collection selection and fields
- Archive stats (EN + PL) use global totals: posts counted by `translation_key`, log entries aggregated over all languages, hours summed numerically
- Portfolio stats pulled from `_data/stats.json`; updated totals reflect 5 works, 4 posts, 16h logged
- CI/deploy: run `bundle exec jekyll build` before publishing; check `_data/stats.json` when adding content

_Status: Draft internal memo; not meant for public site. Last updated 2025-10-06._

