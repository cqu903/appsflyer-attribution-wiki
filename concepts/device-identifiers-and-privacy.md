---
title: 设备标识符与隐私限制
created: 2026-06-24
updated: 2026-06-24
type: concept
tags: [device-id, privacy, attribution, skan]
sources: [raw/articles/4408847686161-device-identifiers.md, raw/articles/360011890298-ios14-att-skan-faq.md, raw/articles/207447053-appsflyer-attribution-model.md]
confidence: high
---

# 设备标识符与隐私限制

设备标识符是确定性归因的基础。AppsFlyer SDK 会自动收集 AppsFlyer ID 和部分平台标识符；广告主也可根据市场需求额外收集，例如中国 Android 生态中的 OAID。^[raw/articles/4408847686161-device-identifiers.md]

## 常见标识符
- iOS：IDFA、IDFV。IDFA 受 ATT 影响；IDFV 通常可用于同一供应商旗下 App 的交叉推广和重装识别。
- Android：GAID；非 Google Play 服务环境可能涉及 OAID、Android ID、IMEI、Fire ID。
- AppsFlyer ID：AppsFlyer 自身生成的标识符，用于平台内用户链路。

## 对 Google / Meta 的影响
- Google Ads 对接文档明确要求应用必须收集 IDFA / GAID。
- Meta 在 iOS 上受 ATT、SKAN、AEM 限制，事件可用性和回传延迟会影响优化。
- 如果设备 ID 缺失，系统会更多依赖概率模型或汇总模型，单用户级准确度下降。

## 操作建议
1. 让开发确认 AppsFlyer SDK 版本、IDFA/GAID/IDFV 采集状态。
2. iOS 明确 ATT 弹窗策略；不要把 iOS 归因问题简单归咎于代理投放。
3. Android 若存在第三方商店/中国大陆包，再单独规划 OAID 和 multi-store；香港 Google Play 版本优先保证 GAID 和 Referrer。

## 相关页面
- [[attribution-model]]
- [[ios-privacy-skan-aem]]
- [[data-discrepancy-playbook]]
