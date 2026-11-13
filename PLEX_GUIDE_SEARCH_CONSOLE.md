# Plex 指南补强与 Search Console 核对

日期：2026-11-13 20:12 CST

## 正式站

- 首页：https://plex-remote-access-help.pages.dev/
- 指南目录：https://plex-remote-access-help.pages.dev/guides/
- 更新后的文章：https://plex-remote-access-help.pages.dev/guides/plex-remote-access-help/

Cloudflare 部署：

- commit `cb40162`
- Deployment ID `3833d465-5834-4cf4-8f4f-254dde0bad83`
- 状态 `success`，用时 14s
- Deployment URL `https://3833d465.plex-remote-access-help.pages.dev`

首页 H1、Google Forms 询价表单和正式 URL 均保留。

## 文章补强内容

- 新增受影响客户端的**远程视频权益检查**：Plex Pass（服务器管理员或用户本人）或 Remote Watch Pass；音乐/照片不受此限制。
- 说明 Double NAT 与 CGNAT 的区别。
- 明确 CGNAT 地址范围 `100.64.0.0/10`，即 `100.64.0.0–100.127.255.255`。
- 分开解释“连接 Direct/Indirect”与“视频 Direct Play/Transcode”。
- Tailscale 命令只放在支持命令行的 Windows/macOS/Linux 设备上；手机/TV/主机使用 App UI。
- 文末新增 `Request a quote for your Plex setup`，链接到 `/#consult`。

引用来源：

- [Plex: Requirements for Remote Playback of Personal Media](https://support.plex.tv/articles/requirements-for-remote-playback-of-personal-media/)
- [Plex: Troubleshooting Remote Access](https://support.plex.tv/articles/200931138-troubleshooting-remote-access/)
- [Plex: Remote Streaming (Setting Up Remote Access)](https://support.plex.tv/articles/200289506-remote-access/)
- [RFC 6598: 100.64.0.0/10](https://www.rfc-editor.org/rfc/rfc6598)
- [Tailscale CLI documentation](https://tailscale.com/docs/reference/tailscale-cli)

脱敏实测截图：**本轮未添加**。没有可用的本机 Plex 远程播放实测截图；没有用示意图或他人截图冒充。

## Search Console 实际状态

| URL | 实际收录状态 | 测试实际网址 |
|---|---|---|
| `/` | **已收录到 Google** | 已收录 |
| `/guides/` | **未收录**；检查时显示“Google 无法识别此网址” | 可编入索引；路径检测到 1 项有效内容 |
| `/guides/plex-remote-access-help/` | **未收录**；检查时显示“Google 无法识别此网址” | 可编入索引；路径检测到 1 项有效内容 |

说明：指南目录和文章是较新的 URL，尚未被 Google 收录；但“测试实际网址”均成功、允许索引，且页面路径有效，不是抓取错误。没有发现需要改页面的索引错误。

## sitemap 状态

Search Console：

```text
/sitemap.xml  未知  2026年11月13日  无法抓取  0 网页  0 视频
```

- 上次读取时间：2026-11-13
- 状态：无法抓取
- 已发现网址：0
- sitemap 行菜单只有“查看网页索引编制”，没有更多错误详情
- 已再次提交 `/sitemap.xml`，状态仍未变化

服务器侧复核：

- `GET /sitemap.xml`：HTTP 200
- Content-Type：`application/xml`
- 合法 XML，包含 3 个 URL
- Googlebot UA 请求：HTTP 200

没有可复现的站点侧 sitemap 错误；当前“无法抓取”与 URL 检查工具的抓取成功结果不一致。未为了状态显示改动 sitemap 结构。

## 结论

文章已按官方说明补强并上线，新询价链接指向 `/#consult`。Search Console 中首页已收录，指南目录和文章未收录但可抓取、可编入索引；sitemap 仍显示“无法抓取”，但服务端返回 200 且内容合法，暂未发现可修复的明确错误。
