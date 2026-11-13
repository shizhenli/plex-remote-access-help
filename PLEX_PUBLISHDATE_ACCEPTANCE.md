# Plex PublishDate 排序与关键词回退验收

日期：2026-11-13 19:58 CST

## 正式站

**https://plex-remote-access-help.pages.dev/**

内容改动 commit：`ef3c833`  
部署 ID：`13021431-d57c-4454-9da1-34cbfdcea1fa`  
状态：`success`  
用时：17s  
部署 URL：`https://13021431.plex-remote-access-help.pages.dev`

## 1. 最新指南排序

共享 partial 与 Plex 首页已改为：

```go-html-template
{{ $guides = $guides.ByPublishDate.Reverse }}
{{ $guides = first 10 $guides }}
```

卡片日期改为：

```go-html-template
<time datetime="{{ .PublishDate.Format "2006-01-02" }}">
  {{ .PublishDate.Format "Jan 2, 2006" }}
</time>
```

正式站当前只有 1 篇正式文章，首页仍显示 1 张卡，日期为 `2026-11-13`。

## 2. 11 篇正式样例 + 1 篇草稿复测

样例保留在本地：

`D:\20项目建站_20261113\local-samples\plex-latest-11\`

样例设置：

- 11 篇 published
- 1 篇 draft
- `sample-01`: `date: 2026-11-01`，`publishDate: 2026-11-12`（日期较早、实际发布日期最新）
- `sample-02` 到 `sample-11`: publishDate 2026-11-02 到 2026-11-11
- `sample-draft`: publishDate 2026-11-13，`draft: true`

生产构建结果：

```text
CARD_COUNT 10
2026-11-12  Sample Plex Guide 01
2026-11-11  Sample Plex Guide 11
2026-11-10  Sample Plex Guide 10
2026-11-09  Sample Plex Guide 09
2026-11-08  Sample Plex Guide 08
2026-11-07  Sample Plex Guide 07
2026-11-06  Sample Plex Guide 06
2026-11-05  Sample Plex Guide 05
2026-11-04  Sample Plex Guide 04
2026-11-03  Sample Plex Guide 03
DRAFT_PRESENT False
SAMPLE02_PRESENT False
```

验收：

- `sample-01` 排第一：**通过**
- 总卡片数 10：**通过**
- `sample-02` 因只取最新 10 篇而未显示：**通过**
- 草稿未显示：**通过**
- 卡片日期使用 PublishDate：**通过**

## 3. 指南目录关键词

检查的关键词导出：

- `outbox/20261112_英文关键词采集/output/keyword_data_all_28.csv`
- `outbox/20261112_英文关键词采集/output/keyword_research_20261112.xlsx`

CSV 和 Excel 的所有 sheet 都没有 `plex` 命中，因此没有可引用的搜索量来源支持：

- `plex remote access guide`
- `plex troubleshooting guides`

按规则回退到已核验词：

```yaml
keywords:
  - "plex remote access"
```

指南目录的 Title 和 Description 继续独立按目录用途编写，未使用未核验词。

## 4. 共享模板

已更新：

- `_shared/layouts/partials/latest-guides.html`
- Plex 的 `layouts/partials/latest-guides.html`
- `TEMPLATE_SEO_RULES.md`
- `content/guides/_index.md`

后续站点直接使用 `ByPublishDate.Reverse` 和 `PublishDate`，并通过 `latest_guides_title` 配置标题；关键词必须有导出出处，否则回退到已核验的主词。
