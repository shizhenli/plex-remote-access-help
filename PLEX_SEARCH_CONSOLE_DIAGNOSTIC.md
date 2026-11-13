# Plex Search Console sitemap 诊断回执

日期：2026-11-13 19:44 CST

## 资源

- URL 前缀资源：`https://plex-remote-access-help.pages.dev/`
- 所有权：已通过 HTML 标记验证
- sitemap：`https://plex-remote-access-help.pages.dev/sitemap.xml`

## Search Console 当前显示

sitemap 列表：

```text
/sitemap.xml  未知  2026年11月13日  无法抓取  0  0
```

提交回执仍为“已成功提交站点地图”；但读取状态是 **无法抓取**，已发现网址 **0**。  
该行菜单只提供“查看网页索引编制”，没有额外的抓取错误详情。

## 服务器侧实际检查

| 检查 | 结果 |
|---|---|
| `GET /sitemap.xml` | HTTP 200 |
| Content-Type | `application/xml` |
| 响应体 | 合法 sitemap，包含 3 个 URL |
| Googlebot UA 请求 | HTTP 200，无挑战/403 |
| `robots.txt` | `User-agent: *` / `Allow: /` |
| canonical | `https://plex-remote-access-help.pages.dev/` |
| 首页 robots | `index, follow` |

用 Googlebot UA 直接请求 sitemap 与首页均正常，没有 Cloudflare 拦截迹象。

## 网址检查 → 测试实际网址

### 首页

测试时间：2026-11-13 19:41

- 网页抓取：**成功**
- 是否允许抓取：**是**
- 是否允许编入索引：**是**
- 用户声明的规范网址：`https://plex-remote-access-help.pages.dev/`
- Google 选择的规范网址：要等到编入索引后才能确定
- 结论：**网址可编入 Google 索引**

索引状态（测试前）：`已抓取 - 尚未编入索引`，不是抓取失败。

### sitemap.xml 本身的“测试实际网址”

测试时间：2026-11-13 19:42

- 网页抓取：**成功**
- 是否允许抓取：**是**
- 是否允许编入索引：**是**（XML 不是普通网页，仅作抓取验证）
- 结论：Google 检查工具可以抓取该 sitemap

## 判断

没有发现可归因于站点代码、robots、canonical、Cloudflare 拦截或 sitemap 格式的明确错误：

- sitemap 直接返回 200 且格式正确
- Googlebot UA 可访问
- Search Console 的“测试实际网址”对首页和 sitemap 都显示抓取成功
- 首页显示“可编入索引”，只是尚未被收录

「无法抓取」与实测结果矛盾，当前更像是 Search Console 的 sitemap 读取状态滞后/旧状态，而不是站点当前故障。

本轮没有为这个问题改动页面代码，以免把正常配置改坏。首页的“请求编入索引”已提交过，界面当前显示“再次提交请求”。

## 后续

1. 等待 Google 重新读取 sitemap，复查状态是否从“无法抓取”变为“成功”。
2. 在 Search Console 的“网页”报告查看首页是否从“已抓取 - 尚未编入索引”转为已编入索引。
3. 若 24–48 小时后仍为“无法抓取”，再查 Search Console 的 sitemap 抓取详情/Googlebot 实际请求日志；目前没有可复现的站点侧错误。
