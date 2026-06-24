---
title: iOS 隐私、SKAN 与 AEM
created: 2026-06-24
updated: 2026-06-24
type: concept
tags: [privacy, skan, meta-ads, google-ads, data-quality]
sources: [raw/articles/360011890298-ios14-att-skan-faq.md, raw/articles/19228737402129-meta-ios-aem.md, raw/articles/207447053-appsflyer-attribution-model.md, raw/articles/20260624-xwallet-af-postback-source-scope-discussion.md]
confidence: medium
---

# iOS 隐私、SKAN 与 AEM

iOS 14.5 之后，ATT、SKAN 和广告平台自己的隐私建模会让 iOS 数据更“聚合、延迟、不完整”。这不是 AppsFlyer 单点配置能完全解决的问题，但配置不完整会进一步放大误差。

## 要点
- ATT 影响 IDFA 可用性；IDFA 缺失会削弱确定性归因。
- SKAN 是 Apple 侧的隐私保护归因机制，通常以聚合、延迟方式呈现。
- Meta AEM 用于 iOS 事件衡量和优化，需要事件配置符合 Meta 要求。
- Google iOS 搜索/网页场景可能因为无法读取 IDFA 而出现归因限制。

## X Wallet 建议
1. iOS 事件不要只看单日回传；至少看 3-7 天滞后。
2. Meta iOS 重点配置 AEM 事件优先级，优先把申请/授信等关键事件纳入。
3. Google iOS App Campaign 与 Web-to-App 场景分开看，避免把网页点击无法确定性归因误判为投放无效。
4. Meta iOS / AEM 冷启动和事件验证阶段，不宜过早把 AppsFlyer 事件来源限制为“仅 Meta 来源”；中浅层核心事件更适合先使用所有媒体源，待事件稳定和 Meta 自身量级足够后再评估收紧。详见 [[event-source-scope-and-learning]]。^[raw/articles/20260624-xwallet-af-postback-source-scope-discussion.md]

## 相关页面
- [[device-identifiers-and-privacy]]
- [[postback-and-event-mapping]]
- [[event-source-scope-and-learning]]
- [[data-discrepancy-playbook]]
