# Wiki Schema

## Domain
AppsFlyer 归因与投放平台配置知识库，重点服务 X Wallet 贷款 App 的移动投放归因、事件回传、Google Ads / Meta ads 对接、代理协作和数据差异排查。

## Conventions
- 文件名：英文小写短横线，无空格。
- Wiki 页面使用 YAML frontmatter；raw/ 原始资料也带 source_url、ingested、sha256。
- 页面之间使用 `[[wikilinks]]`。每个概念/对比/查询页至少 2 个出站链接。
- 更新页面时必须 bump `updated` 日期。
- 新页面必须加入 `index.md`；每次动作必须追加 `log.md`。
- `raw/` 为不可变原始资料，只追加新版本，不直接改旧来源。
- 多来源综合页在关键段落后使用 provenance marker，例如 `^[raw/articles/xxx.md]`。

## Frontmatter
```yaml
---
title: Page Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | comparison | query | summary
tags: [from taxonomy below]
sources: [raw/articles/source-name.md]
confidence: high | medium | low
---
```

## Tag Taxonomy
- 平台/对象：appsflyer, google-ads, meta-ads, agency, srn
- 归因机制：attribution, lookback-window, device-id, skan, retargeting, reattribution
- 配置：integration, event-mapping, postback, conversion-import, cost, permissions, timezone
- 质量控制：discrepancy, troubleshooting, checklist, privacy, data-quality
- 业务场景：xwallet, acquisition, remarketing

## Page Thresholds
- 核心实体（AppsFlyer、Google Ads、Meta ads、代理商）单独建 entity 页。
- 涉及配置决策、归因准确度、关键事件回传的主题建 concept / comparison / query 页。
- 只出现一次且不影响配置的术语不单独建页。
- 页面超过约 200 行时拆分。

## Update Policy
当新来源与旧内容冲突：先看来源更新时间；无法判断时保留两种说法，标记 `contested: true` 并在 log 中提示人工复核。
