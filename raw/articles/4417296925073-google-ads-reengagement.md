---
source_url: https://support.appsflyer.com/hc/zh-cn/articles/4417296925073
ingested: 2026-06-24
sha256: 37c38a9f09f6458d26ffbb4fdb2dddf53688dd978269d9aa11812838dbe2634e
---

# Google Ads（AdWords）— 再互动

Source URL: https://support.appsflyer.com/hc/zh-cn/articles/4417296925073
Section: Google Ads
Updated: 2026-05-25T14:21:15Z

概要： 本文介绍了Google Ads再营销投放效果的衡量方式。

## Google Ads再营销广告系列

您可以使用AppsFlyer衡量 Google Ads App Campaigns for Engagement （以吸引用户互动为目标的应用广告系列，简称ACE）的投放效果。
AppsFlyer将这类广告称为 再营销 （Retargeting）广告。AppsFlyer支持再营销广告的成本、点击和展示数据的拉取。完成对接后，您就能查看并监测您在Google Ads上的广告消耗，然后计算出Google Ads投放的eCPI和ROI。

再营销广告定向投放给已安装相关应用的用户。

- 已经安装相关应用的用户与再营销广告互动后打开应用，记为一次 再互动 （Re-engagement）。这样的再互动通常是通过深度链接实现的。

- 未安装应用的用户与再营销广告互动后安装应用，记为一次 重装激活 （Re-install），或称 再归因 （Re-attribution）。

详情请见 Google Ads再营销广告支持文档 。

## Google Ads再营销广告设置

在开始配置前，请先查看 与其他Google Ads账户分享链接的指南文档 ，确保您的再营销广告能通过现有的Link ID正常监测到。

请按以下步骤衡量Google Ads再营销广告的效果：

### 在应用配置中启用再营销

不管您使用的是哪个媒体渠道，如要启用再营销投放衡量，都需要在应用配置部分进行操作。如果您之前从未对相关应用启用过再营销衡量，请按以下步骤进行配置：

- 从AppsFlyer后台的侧边栏中选择 配置 > 应用配置 。

- 滚动到页面最下方。

- 打开 再互动归因 开关。

### 在AppsFlyer中启用Google Ads的再营销衡量

- 请按 配置说明 中的第5点说明在AppsFlyer中完成Google Ads的配置。

### 将Session Start（应用打开）事件导入Google Ads

如需记录 Google Ads 再营销广告带来的再互动转化，请将session_start事件导入Google Ads。

在AppsFlyer中为Google Ads启用再营销后，只要有一个用户打开相关应用，该事件就会出现在Google Ads中。为确保能记录到session start，请在开启再营销开关之后自行打开应用。

详情请见 Google Ads中的转化导入说明 。

#### 注意

session_start与其他事件不同，即使您未将其从AppsFlyer导入到Google Ads，Google Ads API也能认领到该事件。
但如果不导入该事件，AppsFlyer就会将这些转化归因到初始的流量来源， 使得AppsFlyer和Google Ads的数据之间产生巨大的差异 。此外，这也会使 Google Ads无法优化 相关广告的投放人群定向。

### 为再营销广告系列配置深度链接

Google 再营销广告要求 再互动广告系列使用深度链接 。由于域名不匹配，无法使用第三方深度链接解决方案。这包括AppsFlyer的OneLink。使用您自己的 内部App Links、Universal Links 或者自定义URI Schemes 。

深度链接中无需添加is_retargeting=true和pid=adwords等其他参数。

## 动态再营销和购物广告

AppsFlyer支持针对应用和购物广告系列的动态再营销，这类广告在AppsFlyer平台中与再互动广告无异。

有关应用动态再营销的详细说明请见 此文档 。
有关购物广告的详细说明请见 此文档 。
Google Ads再营销广告的详细说明请见 此文档 。

#### 另请参见

- 请参考 Google Ads与AppsFlyer的SKAN互动设置 ，了解iOS 14的相关注意事项。
