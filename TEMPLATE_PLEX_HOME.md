# Plex Home Template — copy and replace

## Files

- Page layout: `layouts/index.html`
- Page CSS: `static/css/plex.css`
- Shared shell: `_shared/layouts/_default/baseof.html`
- Images: `static/images/plex-desktop-hero.webp`, `plex-mobile-hero.webp`, `plex-service-test.webp`, `plex-social.jpg`
- Config: `hugo.toml`

## Replaceable config keys

```toml
[params]
template_version = "v1.2.0"
extra_css = "css/plex.css"
og_image = "images/plex-social.jpg"
hero_desktop = "images/plex-desktop-hero.webp"
hero_mobile = "images/plex-mobile-hero.webp"
body_image = "images/plex-service-test.webp"
body_class = "plex-site"
source = "plex-remote-access-help"
email = "hello@handytasklab.com"
```

## Copy steps

1. Duplicate this site directory and rename it to the new project slug.
2. In `hugo.toml`, change `baseURL`, `title`, `params.source`, `params.category`, and the three image paths.
3. Put the new images in `static/images/`; keep the same display roles: wide desktop hero, vertical mobile hero, body/test image.
4. Replace the text blocks in `layouts/index.html`: hero, three symptoms, test steps, scope, FAQ, CTA. Keep the class names so `plex.css` continues to work.
5. Keep `/guides/<slug>/` linked from the hero and bottom; the guide remains the existing troubleshooting article.
6. Build with `hugo --minify --cleanDestinationDir`; preview with `hugo server --bind 127.0.0.1 --port 8099`.
7. Check desktop and mobile: correct hero image, no horizontal overflow, CTA `#consult`, guide HTTP 200, canonical and sitemap.
8. Sync shared shell with `pwsh -File scripts/sync-template.ps1` only when the shared base template changes.

## Image handling

- Desktop: 1920×1080 WebP, preserve TV and phone screens; use `object-fit: contain` in the hero so neither is cut.
- Mobile: 768×960 WebP; copy appears first, image below.
- Body: 960×640 WebP, placed beside “How we test”.
- Social: 1200×630 JPEG, under 180 KB.

## Current Plex images

| File | Dimensions | Bytes |
|---|---:|---:|
| `plex-desktop-hero.webp` | 1920×1080 | 212432 |
| `plex-mobile-hero.webp` | 768×960 | 137700 |
| `plex-service-test.webp` | 960×640 | 116420 |
| `plex-social.jpg` | 1200×630 | 62055 |
