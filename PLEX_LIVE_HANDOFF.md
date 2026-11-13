# Plex 正式上线与咨询表单回执

日期：2026-11-13 19:30 CST

## 正式网址

**https://plex-remote-access-help.pages.dev/**

Cloudflare Pages 项目：`plex-remote-access-help`  
GitHub：`shizhenli/plex-remote-access-help`  
Production branch：`main`  
Build command：`hugo --minify`  
Output：`public`  
Hugo：Extended 0.169.0

## Git 自动部署记录

Cloudflare 项目显示 **Automatic deployments enabled**。

| 提交 | 说明 | 部署 ID | 状态 | 用时 |
|---|---|---|---|---|
| `b6e64ac` | Add working consultation form and clean footer metadata | `1c7983f6-5f5c-4a7e-b917-39f6b4911418` | success | 14s |
| `4fb8b12` | Connect consultation form to Google Forms response endpoint | `39456d6a-c929-49e9-90d0-6f7cba7ce1b7` | 成功上线 | — |
| `d87d5f3` | Fix Hugo config line for Search Console verification | `9d4f18a9-7c1d-40dc-a42c-bc9524590557` | success | 16s |

最新部署 URL：`https://9d4f18a9.plex-remote-access-help.pages.dev`  
最新提交：`d87d5f3`；Cloudflare 构建日志确认 clone、Hugo 0.169.0 安装、`hugo --minify`、deploy 全部完成。

## 页脚清理

正式页页脚已变为：

```text
Remote help for one device at a time.
hello@handytasklab.com | Sitemap
```

已确认不再出现：
- `Template v1.2.0`
- `Source marker: plex-remote-access-help`
- `路` 乱码

## 咨询表单

Plex 页面已从 `mailto` 改为真正可提交的 Google Forms 表单：

- 页面表单直接 POST 到 Google Forms `formResponse`
- 表单标题：`Plex remote access inquiry`
- 字段：Name、Email、What happens away from home?
- 提交后会打开 Google 的“您的回复已记录”页面

### 实际提交结果

Google Forms 后台已有 **2 条回复**：

1. `Plex Local Form Test` — 本地页测试
2. `Plex Live Form Test` — 正式页测试

正式页最新回复内容：

```text
LIVE FORM TEST 2026-11-13. Source: plex-remote-access-help.
Confirm receipt and Plex source.
```

因此已确认：
- 从正式页提交成功
- 后台实际收到
- 能通过表单标题和回复正文识别 Plex 来源

表单查看地址：  
`https://docs.google.com/forms/d/e/1FAIpQLSeWIEEXwIjnBnaQsVLfT_0Zb-J-VyCNhg160CFp2BF_EaEHRg/viewform`

## Search Console

- 资源：`https://plex-remote-access-help.pages.dev/`（URL 前缀）
- 所有权验证：**已通过**，方法为 HTML 标记
- 验证元标记已在线：`t3bN...E5k`
- sitemap 已提交：`https://plex-remote-access-help.pages.dev/sitemap.xml`
- 提交回执：**已成功提交站点地图**
- 当前读取状态：**无法抓取**，已发现网址数 **0**

直接访问 sitemap 为 HTTP 200，`application/xml`，包含 3 个 URL；Google 首次读取失败，尚不能声称已收录。需等待 Google 重新抓取或在 Search Console 查看抓取详情。

## 正式页检查

- 标题：`Plex Remote Access Help`
- canonical：`https://plex-remote-access-help.pages.dev/`
- robots：`index, follow`
- 表单：在线，Google Forms 端点
- 页脚：已清理
- 图片：1920×1080 / 768×960 / 960×640 / 1200×630
- 分享图：`https://plex-remote-access-help.pages.dev/images/plex-social.jpg`

## 结论

Plex 首站已经正式上线，GitHub push 自动构建成功，咨询表单从正式页提交并在 Google Forms 后台落库，页脚已清理。Search Console 所有权已通过、sitemap 已提交，但 sitemap 当前仍显示抓取失败，索引状态未完成。
