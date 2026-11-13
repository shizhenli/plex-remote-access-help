# Plex 首页本地预览验收

日期：2026-11-13 18:57 CST

## 预览地址

`http://127.0.0.1:8099/`

实际由 Hugo Extended 0.169.0 `hugo server` 运行，不是静态文件直接打开。开发预览因此输出 `noindex, nofollow`；生产 `public` 构建仍为 `index, follow`，canonical 为 `https://plex-remote-access-help.pages.dev/`。

## 图片交付

| 用途 | 文件 | 尺寸 | 字节 |
|---|---|---|---:|
| 电脑首屏 | `static/images/plex-desktop-hero.webp` | 1920×1080 | 212,432 |
| 手机首屏 | `static/images/plex-mobile-hero.webp` | 768×960 | 137,700 |
| 正文服务 | `static/images/plex-service-test.webp` | 960×640 | 116,420 |
| 分享图 | `static/images/plex-social.jpg` | 1200×630 | 62,055 |

三张原图保留在原始 Temp 路径，未覆盖。桌面图与分享图保留电视和手机屏幕；手机图独立裁切，正文图保留笔记本与手机。

## 页面验收

- 桌面 1440×1000：主图铺满整个首屏，左侧暗区叠标题/说明/按钮；右侧电视和手机屏幕均保留。
- 手机 390×844：压缩标题和说明，按钮在图片前；竖图之后接三条服务细节；`scrollWidth = 390`，无横向溢出。
- 桌面首屏加载 `plex-desktop-hero.webp`（natural 1920×1080）。
- 手机首屏加载 `plex-mobile-hero.webp`（natural 768×960）。
- 正文图 `plex-service-test.webp` 在“How we test”旁，已加载。
- 主按钮 `Request a quote` 跳到 `#consult`；咨询区按钮为 `Email for a quote`（mailto）。
- `Read the guide` 指向 `/guides/plex-remote-access-help/`，HTTP 200，指南标题为 “Plex Remote Access Not Working: Diagnose the Path Before Changing Settings”。
- 正文顺序：三个症状 → 排查/验证步骤 + 正文图 → 服务范围 → FAQ → 咨询入口。
- 分享图设置 `og:image`，绝对地址基于正式 baseURL。

## 截图

- [电脑首屏](<D:/20项目建站_20261113/preview-screens/plex-desktop-hero.png>)
- [电脑整页](<D:/20项目建站_20261113/preview-screens/plex-desktop-full.png>)
- [手机首屏](<D:/20项目建站_20261113/preview-screens/plex-mobile-hero.png>)
- [手机整页](<D:/20项目建站_20261113/preview-screens/plex-mobile-full.png>)

## 咨询状态

**尚未接通可提交表单。** 页面目前有 0 个 `<form>`，咨询入口仍是 3 个 `mailto:hello@handytasklab.com` 链接；没有从网页提交并收到咨询的证据。不能标为咨询送达。

## 模板

- 页面布局：`layouts/index.html`
- 页面 CSS：`static/css/plex.css`
- 图片配置：`hugo.toml` 的 `hero_desktop`、`hero_mobile`、`body_image`、`og_image`
- 复制与替换步骤：`TEMPLATE_PLEX_HOME.md`
- 图片清单：`IMAGE_MANIFEST.csv`

替换站点时只需复制 `layouts/index.html`、`static/css/plex.css`，改 `hugo.toml` 的 baseURL/标题/source/图片参数和正文，再运行 Hugo 构建。
