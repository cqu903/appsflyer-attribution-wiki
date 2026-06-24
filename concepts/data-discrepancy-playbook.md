---
title: 数据差异排查手册
created: 2026-06-24
updated: 2026-06-24
type: concept
tags: [discrepancy, troubleshooting, google-ads, meta-ads, data-quality]
sources: [raw/articles/4417303339921-google-ads-faq-discrepancies.md, raw/articles/4410481130641-meta-ads-discrepancies.md, raw/articles/360000310629-data-freshness-timezone.md, raw/articles/208338403-lookback-windows.md]
confidence: high
---

# 数据差异排查手册

AppsFlyer、Google Ads、Meta ads 的数字不可能长期完全一致。排查目标不是追求逐条一致，而是确认差异是否来自已知口径，还是配置错误。^[raw/articles/4417303339921-google-ads-faq-discrepancies.md]

## 优先排查顺序
1. 时间口径：AppsFlyer 数据时效、平台时区、报表日期是否一致。^[raw/articles/360000310629-data-freshness-timezone.md]
2. 归因窗口：Google 30d/1d、Meta 7d/1d 是否与 AppsFlyer 配置一致。
3. 事件是否导入/映射：Google 是否导入 `first_open` 和关键 in-app events；Meta 事件是否映射。
4. 事件来源：Google/Meta 是“所有媒体源”还是“仅该合作伙伴”。
5. iOS 隐私：ATT、SKAN、AEM、延迟回传是否影响。
6. 代理/MCC：Link ID、Customer ID、Recording Manager 是否正确。
7. 成本数据：是否连接正确 Google 账号，是否有 ROI360，代理账号是否有 Customer ID 权限。

## Google 常见问题
- 看不到点击：通常要先在成本选项卡确认收集成本、点击和展示数据。
- 看不到 `first_open`：通常还没在 Google Ads 导入转化。
- 看不到应用内事件：先映射事件，再在设备上触发，并等待最多约 6 小时。
- 再营销没导入 `session_start`：会造成 Google 与 AppsFlyer 再互动数据明显不一致。

## Meta 常见问题
- AEM 不合格：检查事件发送范围、Meta 事件管理器配置，等待 2-3 天。
- iOS 事件少：先区分 ATT/SKAN/AEM 影响，别直接归咎于素材或投放。
- 与 AppsFlyer 差异：先对齐窗口，再看事件映射、去重、延迟和平台自归因口径。

## 相关页面
- [[lookback-window-strategy]]
- [[postback-and-event-mapping]]
- [[agency-and-mcc-governance]]
