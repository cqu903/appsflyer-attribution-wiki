---
title: Google Ads
created: 2026-06-24
updated: 2026-06-24
type: entity
tags: [google-ads, srn, integration, event-mapping, cost]
sources: [raw/articles/115002504686-google-ads-integration.md, raw/articles/4417303339921-google-ads-faq-discrepancies.md, raw/articles/115004970386-google-ads-mcc-multiple-agencies.md]
confidence: high
---

# Google Ads

Google Ads 是 SRN（Self Reporting Network）。AppsFlyer 不是通过普通点击链接完全独立归因 Google App Campaign，而是使用 Google 授权接口、Link ID、转化导入和事件映射来交换数据。^[raw/articles/115002504686-google-ads-integration.md]

## 必备配置
- 在 Google Ads 创建 Third-party app analytics 的 Link ID，并选择 AppsFlyer。
- 在 AppsFlyer Partner Marketplace 启用 Google Ads，填入 Link ID。
- 确保 App SDK 采集 IDFA / GAID；这是 Google Ads 对接前提之一。
- 导入 `first_open`；如果跑再互动，导入 `session_start`。
- 在 AppsFlyer 映射应用内事件到 Google Ads，并选择合适的事件来源。

## 推荐窗口
Google 默认点击回溯窗口 30 天，浏览回溯窗口 24 小时。AppsFlyer 文档建议 Google Ads 点击窗口设置为 30 天、浏览窗口设置为 1 天，以减少差异。详见 [[lookback-window-strategy]]。

## 事件回传原则
首次启用 Google Ads 应用内事件映射时，`af_app_opened` 会自动定义并映射到 `session_start`；事件来源建议先设为“所有媒体渠道，包括自然流量”，这样 Google 能收到足够信号。后续如果要限制优化信号，再按投放目标调整。^[raw/articles/115002504686-google-ads-integration.md]

## 多账号/MCC
同一个 App 的 Android 和 iOS 需要不同 Link ID。多个账号投同一个 App 时，应共享同一个 Link ID，而不是让每个代理各自创建。最高层 MCC 或广告主主账号持有 Link ID 通常更易治理。详见 [[agency-and-mcc-governance]]。

## 相关页面
- [[google-vs-meta-integration]]
- [[postback-and-event-mapping]]
- [[data-discrepancy-playbook]]
