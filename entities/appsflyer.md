---
title: AppsFlyer
created: 2026-06-24
updated: 2026-06-24
type: entity
tags: [appsflyer, attribution, event-mapping, data-quality]
sources: [raw/articles/207447053-appsflyer-attribution-model.md, raw/articles/207447163-link-structure-and-parameters.md, raw/articles/115005972889-data-access-permissions.md]
confidence: high
---

# AppsFlyer

AppsFlyer 是移动归因与营销数据平台。本库只关注它对 X Wallet 有直接价值的部分：把激活、再互动和应用内关键事件正确归因到媒体渠道，并把事件可靠回传给 [[google-ads]] 和 [[meta-ads]]。

## 在投放链路中的角色
- 接收 SDK 上报的首次打开、session、应用内事件和设备标识符。
- 通过 [[attribution-model]] 判断一次激活/再互动应归给哪个媒体触点。
- 通过 Partner Marketplace 的渠道对接，把事件回传给 SRN 或非 SRN 渠道。
- 通过数据权限、时区和数据时效设置，影响代理商与广告平台看到的数据口径。^[raw/articles/207447053-appsflyer-attribution-model.md]

## 对 X Wallet 的关键配置对象
1. SDK 与事件：必须让开发侧稳定上报 first open、申请开始、资料提交、审批、放款等漏斗事件，详见 [[xwallet-event-taxonomy]]。
2. 归因窗口：Google / Meta 这类 SRN 应尽量与平台默认窗口对齐，详见 [[lookback-window-strategy]]。
3. 事件回传：不是“事件越多越好”，而是把能代表用户质量的事件传给广告平台优化，详见 [[postback-and-event-mapping]]。
4. 权限与代理：代理可以执行投放，但 Link ID、事件定义、成本连接和核心权限应由广告主持有，详见 [[agency-and-mcc-governance]]。

## 常见风险
- SDK 没有采集 IDFA/GAID，导致 Google / Meta 可归因量下降。
- 事件先映射后测试的顺序搞反：广告平台可能看不到新事件。
- Google / Meta 和 AppsFlyer 归因窗口不一致，造成看似“数据不准”的差异。
- 代理商直接创建 Link ID 或持有成本连接，合作结束后难拆分。
