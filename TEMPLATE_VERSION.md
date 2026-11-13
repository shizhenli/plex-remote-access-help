# Template version

- Version: v1.3.0
- Source: `_shared/layouts` + `_shared/static/{css,robots.txt,favicon.svg}`
- Sync: `pwsh -File scripts/sync-template.ps1`
- Per-site config records `params.template_version = "v1.3.0"` for upgraded sites.
- Shared rules include per-page TDK, breadcrumbs + BreadcrumbList JSON-LD, image alt/title params, and latest-10 guide listing.
- See `TEMPLATE_SEO_RULES.md` for the page/front-matter contract.
- First 3 guides were replaced with project-specific content; other 17 guides remain drafts.
- Production/preview robots and canonical are generated from the shared base template.
