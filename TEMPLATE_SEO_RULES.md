# Shared Hugo SEO / Breadcrumb / Latest Guides Rules

## Per-page TDK

Every page front matter supplies its own English title, description and verified keywords:

```yaml
title: "Visible H1"
seo_title: "Independent title used in <title> and og:title"
description: "Independent meta description"
seo_description: "Optional override for description"
keywords:
  - "verified English target phrase"
```

Rules:

- `seo_title` is the full `<title>`; do not append the site title again.
- One unique description per page; do not reuse the site-level description.
- `keywords` is a per-page list; the shared base template emits `<meta name="keywords">`.
- Plex homepage target: `plex remote access`.
- Plex existing guide target: `plex remote access not working`.
- `og:type` is `article` for non-home pages.

## Breadcrumbs

`layouts/partials/breadcrumbs.html` renders both:

1. Visible `<nav class="breadcrumbs">…</nav>`
2. Matching `BreadcrumbList` JSON-LD

Paths:

- Guide index: `Home › Guides`
- Article: `Home › Guides › Article title`
- Links use `.Permalink`, so they point to the formal baseURL.
- The current page is a non-link `aria-current="page"`.

Include it at the top of guide/list and single layouts:

```go-html-template
{{ partial "breadcrumbs.html" . }}
```

## Latest guides

`layouts/partials/latest-guides.html`:

- Source: `site.RegularPages`
- Filter: `Section == "guides"`
- Sort: newest first
- Limit: `first 10`
- Drafts: excluded by Hugo production builds
- Displays date, title link, description
- Includes an “All guides” link

Include below the home consultation section:

```go-html-template
{{ partial "latest-guides.html" . }}
```

Set the heading per site:

```toml
[params]
latest_guides_title = "Latest Plex Troubleshooting Guides"
```

## Images

Per-site params:

```toml
[params]
hero_alt = "TV and phone showing the same video in a Plex remote access illustration"
hero_title = "Plex remote access on TV and phone"
body_alt = "Phone playing a video beside a laptop in a Plex remote access troubleshooting illustration"
body_title = "Plex remote access playback test"
```

Rules:

- Hero desktop and mobile images both use `hero_alt` / `hero_title`.
- Body image uses `body_alt` / `body_title`.
- Do not put `aria-hidden="true"` on the visible hero container.
- Purely decorative images keep `alt=""`.

## Plex page mapping

- Home: `content/_index.md`
- Guide index: `content/guides/_index.md`
- Article: `content/guides/plex-remote-access-help.md`
- Shared shell: `layouts/_default/baseof.html`
- Shared content layouts: `layouts/_default/{list,single}.html`
- Shared partials: `layouts/partials/{breadcrumbs,latest-guides}.html`
- Site home layout: `layouts/index.html`

## Sync

`scripts/sync-template.ps1` copies the shared shell, content layouts and partials. It deliberately does **not** copy `layouts/index.html`, so a site-specific home is preserved.

## Local verification

Temporary test copy: 11 published sample articles + 1 draft.

Result:

- Published cards rendered: **10**
- Newest dates: 2026-11-11 down to 2026-11-02
- Draft title present: **false**
- Production build excluded the draft and capped the list at 10.
