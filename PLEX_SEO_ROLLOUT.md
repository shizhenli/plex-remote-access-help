# Plex SEO / Breadcrumb / Latest Guides 验收

日期：2026-11-13 19:50 CST

## 正式站

**https://plex-remote-access-help.pages.dev/**

Cloudflare 最新部署：

- commit `22c9c67` — `Add per-page TDK, breadcrumbs, image metadata, latest guides template`
- Deployment ID `8dd0ee88-d582-4863-821c-fef3b1d1c1d9`
- 状态：`success`
- 用时：13s
- 部署 URL：`https://8dd0ee88.plex-remote-access-help.pages.dev`
- Automatic deployments：enabled

## 逐页 TDK

| 页面 | Title | Description | Keywords |
|---|---|---|---|
| 首页 `/` | Plex Remote Access Help: Fix Plex Away From Home | Fix Plex remote access when Plex works at home but not away. Test CGNAT, router ports, relay, Tailscale, and mobile playback with a repeatable remote diagnosis. | `plex remote access` |
| 指南目录 `/guides/` | Plex Remote Access Troubleshooting Guides | Step-by-step Plex remote access guides for CGNAT, closed ports, relay, Tailscale, buffering, and playback testing away from home. | `plex remote access guide`, `plex troubleshooting guides` |
| 文章 `/guides/plex-remote-access-help/` | Plex Remote Access Not Working: Diagnose the Path | Plex remote access not working? Diagnose CGNAT, closed ports, relay, Tailscale, and client playback with a repeatable test and rollback path. | `plex remote access not working`, `plex remote access` |

三页 canonical 分别指向正式 URL；没有重复描述或模板占位字样。

## 面包屑与结构化数据

指南目录：

- 可见：`Home › Guides`
- JSON-LD：`BreadcrumbList`，2 项
- Home 链接：`https://plex-remote-access-help.pages.dev/`

文章：

- 可见：`Home › Guides › Plex Remote Access Not Working: Diagnose the Path Before Changing Settings`
- JSON-LD：`BreadcrumbList`，3 项
- Home / Guides 链接均为正式站绝对 URL
- JSON-LD 已用 Python `json.loads` 验证可解析，名称与可见路径一致

## 图片 alt / title

桌面首图：

```text
alt: TV and phone showing the same video in a Plex remote access illustration
title: Plex remote access on TV and phone
```

手机首图：

```text
alt: TV and phone showing the same video in a Plex remote access illustration
title: Plex remote access on TV and phone
```

正文图：

```text
alt: Phone playing a video beside a laptop in a Plex remote access troubleshooting illustration
title: Plex remote access playback test
```

浏览器检查结果：

- 桌面可见图片：`plex-desktop-hero.webp`
- 手机可见图片：`plex-mobile-hero.webp`
- 两者 alt/title 正确
- `ariaHiddenAncestor: false`；没有把首图放在 `aria-hidden="true"` 容器里
- 正文图 alt/title 正确
- 页面无装饰性图片需要空 alt

## Latest Plex Troubleshooting Guides

位置：首页咨询区下方。

当前正式文章只有 1 篇，因此显示 1 张卡：

- 日期：Nov 13, 2026
- 标题：Plex Remote Access Not Working: Diagnose the Path Before Changing Settings
- 摘要：Plex remote access not working? Diagnose CGNAT, closed ports, relay, Tailscale, and client playback...
- 链接：`/guides/plex-remote-access-help/`
- 全部指南入口：`/guides/`

## 11 篇样例验证

用临时副本测试，未提交到正式仓库：

- 正式样例：**11 篇**
- 草稿样例：**1 篇**
- 页面实际渲染：**10 张卡**
- 最新顺序：2026-11-11 → 2026-11-02
- 草稿标题出现：**false**
- 结论：`first 10` 生效，草稿被 Hugo 生产构建排除

## 桌面 / 手机

正式站浏览器检查：

- 桌面 1440×1000：`scrollWidth = 1440`
- 手机 390×844：`scrollWidth = 390`
- 无横向溢出
- 桌面加载 `plex-desktop-hero.webp`
- 手机加载 `plex-mobile-hero.webp`
- 首页 1 张最新指南卡
- 指南目录和文章面包屑均显示

截图：

- [桌面首页](<D:/20项目建站_20261113/preview-screens/plex-live-desktop-home.png>)
- [手机首页](<D:/20项目建站_20261113/preview-screens/plex-live-mobile-home.png>)
- [指南目录](<D:/20项目建站_20261113/preview-screens/plex-live-guides.png>)
- [文章面包屑](<D:/20项目建站_20261113/preview-screens/plex-live-article.png>)

## 共享模板

已写入：

- `TEMPLATE_SEO_RULES.md`
- `_shared/layouts/_default/baseof.html`
- `_shared/layouts/_default/list.html`
- `_shared/layouts/_default/single.html`
- `_shared/layouts/partials/breadcrumbs.html`
- `_shared/layouts/partials/latest-guides.html`
- `_shared/static/css/site.css`
- `scripts/sync-template.ps1`

规则：

- 每页 `seo_title`、`description`/`seo_description`、`keywords`
- `breadcrumbs.html` 同时输出可见面包屑和 `BreadcrumbList`
- `latest-guides.html` 使用 `site.RegularPages`、`Section == "guides"`、日期倒序、`first 10`
- 图片 alt/title 通过 `hero_alt`、`hero_title`、`body_alt`、`body_title` 配置
- 同步脚本不再复制 `layouts/index.html`，避免覆盖各站自定义首页

## 结论

Plex 正式站已更新并验证；TDK、canonical、面包屑/JSON-LD、图片 alt/title、最新指南列表均符合本轮要求。正式站当前只有 1 篇正式文章，因此列表仅显示 1 篇；11 篇样例已验证上限为 10 且排除草稿。
