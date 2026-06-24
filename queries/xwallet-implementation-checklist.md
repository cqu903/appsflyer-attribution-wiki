---
title: X Wallet AppsFlyer 配置实施清单
created: 2026-06-24
updated: 2026-06-24
type: query
tags: [xwallet, checklist, integration, event-mapping, data-quality]
sources: [raw/articles/207447053-appsflyer-attribution-model.md, raw/articles/115002504686-google-ads-integration.md, raw/articles/207033826-meta-ads-integration.md, raw/articles/208338403-lookback-windows.md]
confidence: medium
---

# X Wallet AppsFlyer 配置实施清单

## 目标
提高 X Wallet App 的归因准确度，并把关键事件可靠回传到 Google Ads 和 Meta ads，用于广告优化与代理管理。

## 第 0 步：资产与权限
- AppsFlyer 管理员权限确认。
- Google Ads 管理员权限、MCC 结构、Customer ID、Link ID owner 确认。
- Meta Business / App / Ad Account 权限确认。
- 代理权限边界确认：代理可执行，广告主持有核心资产。

## 第 1 步：SDK 与标识符
- 确认 AppsFlyer SDK 版本。
- Android：GAID + Google Play Install Referrer 正常。
- iOS：IDFA 请求策略、IDFV 收集、SKAN/AEM 相关配置确认。
- AppsFlyer Raw Data 中能看到 first_open 和基础设备字段。

## 第 2 步：事件字典
- 按 [[xwallet-event-taxonomy]] 定义事件。
- 开发、产品、投放统一命名，不让代理自定义核心事件。
- 在测试环境/小流量中确认每个事件触发时机和参数。

## 第 3 步：Google Ads
- 创建/确认 Link ID。
- AppsFlyer 启用 Google Ads，对齐 30d click / 1d view。
- Google Ads 导入 first_open；再营销导入 session_start。
- 映射注册、申请提交、审批/放款等关键事件。
- 成本连接确认使用正确 Google 账号。

## 第 4 步：Meta ads
- AppsFlyer 启用 Meta ads，对齐 7d click / 1d view。
- 映射应用内事件。
- iOS 检查 AEM 事件条件与优先级。
- 等待生效后核对 Meta 事件管理器和 AppsFlyer 报表。

## 第 5 步：验收报表
- AppsFlyer：按 media source / campaign / event 看漏斗。
- Google Ads：first_open 与关键事件状态不应长期 No recent conversion。
- Meta：事件管理器可见、AEM 合格状态明确。
- 差异排查按 [[data-discrepancy-playbook]] 执行。

## 第 6 步：优化节奏
- 初期优化注册/申请提交，保证事件量。
- 稳定后测试审批通过/放款成功作为深层优化或 value signal。
- 每次改窗口、事件来源、映射关系，都记录日期，避免误判投放效果。
