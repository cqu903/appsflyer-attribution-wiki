---
source_url: https://support.appsflyer.com/hc/zh-cn/articles/4417303339921
ingested: 2026-06-24
sha256: 70dac3dd552237739273ce1a8e77f220e0fad598130da0477439d7b67a068698
---

# Google Ads（AdWords）— 常见问题及数据差异

Source URL: https://support.appsflyer.com/hc/zh-cn/articles/4417303339921
Section: Google Ads
Updated: 2026-06-17T06:31:25Z

概要： 本文将帮助您排查Google Ads相关的常见问题以及数据差异。

## Google Ads常见问题解答

### 为什么我没有看到来自Google Ads的点击？

您需要在 成本 选项卡中 确认收集成本、点击和展示数据 后才能看到来自Google Ads的汇总点击和展示数据。

Google Ads于2018年8月开放点击和展示数据，先开放Android应用的数据，后延伸到iOS应用。因此如需分析2018年及之前的点击数据，请注意Google Ads的点击数据可能会有缺失或不完整。

### 为什么在Google Ads上看不到first_open转化？

如果您在Google Ads上看不到如下所示的first_open转化：

这表示您需要在Google Ads中导入转化，具体操作请参考 导入转化指南 。

### 为什么我在Google Ads上看不到应用内事件？

您在AppsFlyer面板中将需要查看的应用内事件映射完毕后（ 第3步配置操作 ）是否看到这个界面？

若是，请完成以下任一操作：

- 如果您选择的应用内事件来源为“仅该合作渠道”，请先确保您设备上的激活已归因到Google，然后再使用该设备完成相关事件。

- 将 事件来源 设置为“所有媒体渠道，包括自然流量”，然后在您的设备上完成相关事件。

#### 重要提示！

- 请务必先完成相关应用内事件的映射，然后在您的设备上完成这些事件。

- 操作完成后，最多需要等待6小时才能在Google Ads面板中看到相关事件。

### 可以停止同步Google成本吗？

关闭Google成本同步的方式如下：

- 进入 Google Account Permissions （帐户权限）部分。

- 点击“AppsFlyer Google Cost”旁边的“Remove”（移除）按钮。

### 是否需要先创建然后再导入session_start？

这取决于您正在投放的广告类型。如果您正在投放再互动广告，建议您创建并导入 session_start ，用以衡量互动行为。
如果您投放的是拉新广告，则不一定需要完成此操作。

### 我可以将卸载信息发送到Google Ads吗？

可以。
如需向Google发送卸载事件，请完成以下操作：

- 在Google Ads设置窗口中将af_uninstall映射为自定义事件。

- 在Google中导入该转化事件。

- 如果Google在其归因窗口期（广告互动后30-90天）内接收到事件，就会进行认领。归因窗口期结束后，Google就不再记录接收到的事件。

### AppsFlyer如何呈现Google Ads的数据？

AppsFlyer按以下几个层级呈现数据：广告系列、流量入口、广告组和地理位置。

### 如果要根据AppsFlyer的数据在Google Ads中创建人群包列表，是否需进行额外的配置？

不需要，Google会根据您的应用内事件配置在Google API中设置相关信息。

### 我投放了一个App Campaign（应用广告），但在AppsFlyer和Google Ads面板中看不到相关数据及转化事件，这是为什么？

您很可能还没有导入事件。请参考 此文档 ，了解如何导入事件。

### 如果有多个帐户怎么办？

您完全可以在AppsFlyer中使用多个Google Ads账号。AppsFlyer通过唯一的Link ID识别广告主，因此只要您仅在Google Ads中生成一个Link ID，并在各账户间共享该ID，就可以使用多个账户了。详情请见 此文档 。

### MCC级别的Link ID和帐户级别的Link ID在AppsFlyer中有什么区别？

AppsFlyer支持MCC和帐户级别的Link ID。建议您与Google Ads客户经理密切合作，以确保您的帐户结构配置正确。详情请见 此文档 。

### 什么是并行追踪（Parallel Tracking）？

Google Ads的并行追踪可加快落地页的加载，从而减少访问失败现象，最终提升转化、优化投放效果。并行追踪（Parallel Tracking）可以让用户点击您的广告后直接进入最终的跳转链接，跳过归因链接，同时在后台进行点击衡量。

有关并行追踪（Parallel Tracking）的详细说明请见 此文档 。

#### 如何操作？

为了保证并行追踪（Parallel tracking）能正常生效，跳转终点的URL必须与Google Ads广告链接（Campaign URL）中的网址一致，且该网址必须设置在 Google的{lpurl} ValueTrack参数 中。

具体的操作方法如下：

- 使用单平台归因链接（不推荐）
- 链接中必须包含af_r参数

- 使用 OneLink长链 （推荐）
- 在广告链接中添加下列链接参数
- af_android_url

- af_ios_url

- af_web_dp

- 切勿使用af_dp

- 在Google的ValueTrack参数中添加跳转终点URL。 了解详情

示例：
https://subdomain.onelink.me/template_id?pid=xxx& af_ios_url = {lpurl}
& af_android_url = {lpurl} & af_web_dp = {lpurl}
请注意： 如需了解所有可用参数，请见 此文档 。

如需进一步了解如何配置带有并行追踪的Google Ads网页广告系列，请 点击此处 。

### 如何为安卓或iOS应用配置广告投放？

#### 重要提示！

AppsFlyer支持所有的Google Ads广告系列。

Google是一个自归因平台（Self Reporting Network，简称SRN)。详情请参阅 自归因平台的归因链路及机制 。

也就是说，AppsFlyer可以呈现Google提供的所有投放信息。Search（搜索广告）、Video（视频广告）、Display（展示广告）、Re-engagement（再互动广告）等广告系列类型以及相关信息由Google提供。建议您配置App Campaign类广告系列。如需了解其他广告系列类型，请联系您的Google客户经理。广告系列说明请见 此文档 。

#### 适用于Google Ads的安卓配置

如需对安卓应用进行归因，请确保您的应用支持GAID（Google Advertising ID）收集，并可通过SDK将该ID发送给AppsFlyer。

#### 创建转化记录（激活）

有关创建转化记录的详细说明，请见 此文档 。
Google Ads - 安卓配置 - 发送应用内事件
如果您想进一步衡量Google Mobile App Install（移动应用安装）广告的投放效果，可以通过AppsFlyer帐户向您的Google Ads帐户发送应用内事件。

#### 创建转化（应用内事件）

有关衡量应用转化的详细说明，请见 此文档 。

#### Google Ads的iOS配置

#### Google Ads — iOS配置：App Campaign类广告系列

投放App Campaign类广告可以一次性配置Google Search（搜索广告）、YouTube、Display（展示广告）等多种广告形式，用于推广您的iOS应用。

Google Ads一般不能将搜索广告带来的iOS激活归因给自己，这是由于该场景中的点击来自移动端网页渠道，因此Google无法读取设备的IDFA，进而无法进行ID匹配。

反之，对于在 Google Search App 上投放的广告，Google Ads就可以对App Campaign带来的iOS搜索进行归因。

#### 创建转换记录（激活）

有关创建转化记录的详细说明，请见 此文档 。

#### Google Ads - iOS配置 - 发送应用内事件

如果您想进一步衡量Google Mobile App Install（移动应用安装）广告的投放效果，可以通过AppsFlyer帐户向您的Google Ads帐户发送应用内事件。

#### 创建转化（应用内事件）

有关衡量应用转化的详细说明，请见 此文档 。

### Google Ads的用户级数据会在AF中保留多长时间？

Google Ads要求归因服务商在激活后6个月内删除其用户级别数据。也就是说，用户在激活应用6个月之后触发的事件会被记录为自然事件。

历史汇总数据保持不变。

以上规则适用于所有Google Ads流量入口。

## Google Ads的数据差异

Google Ads 面板和AppsFlyer面板之间有时会出现数据差异。

尽管我们一直与Google Ads保持紧密合作，以最大程度地减少数据差异，但广告主仍应了解以下各种造成数据差异的因素：

#### 同时适用于iOS和安卓的数据差异

原因 Google Ads AppsFlyer

助攻激活（即多触点归因）

只要用户与Google Ads互动后在其归因窗口期内激活应用，作为SRN的Google Ads就会将该激活归因给自己。

AppsFlyer只会把激活归因给最后一次点击，并将最后一次点击之前的广告互动记为 助攻 。

激活记录日期

Google Ads 将点击时间记为转化时间。

AppsFlyer将应用首次启动（应用打开）的时间记为转化时间。

时区

取决于地理位置

取决于地理位置

归因窗口

30天

Google对接默认设置为30天（可以修改）。

浏览型转化

仅 所有转化 一栏显示浏览型转化， 转化 栏不显示，除非在Google Ads中另有设置。

AppsFlyer显示总激活数量，包括点击型激活和浏览型激活。

重装激活

Google Ads将重装激活作为session_start转化呈现。

AppsFlyer会将重装激活（即再归因）作为再营销数据的一部分，对其进行归因和展示。

应用内事件

Google Ads将点击时间记为应用内事件时间。

AppsFlyer面板将激活时间记为应用内事件。在AppsFlyer的原始数据报告中，应用内事件时间为事件实际发生的时间。

验证规则

无论验证规则如何，Google都会从AppsFlyer接收所有信息。

AppsFlyer可能会根据相关的验证规则剔除一部分激活。

iOS的App Campaign搜索库存

Google Ads的iOS AC搜索广告库存同时包含移动端网页和Google Search App上的搜索广告。

无论是移动网络还是Google Search App上的搜索广告，Google Ads都不会响应归因合作伙伴对iOS AC搜索转化的查询。因此，AppsFlyer不会把这类激活归因给Google Ads。

成本 - Google Ads流量入口

针对具体的广告系列，Google会上报所有流量入口（YouTube、展示广告和搜索广告）的相关成本。

AppsFlyer会从Google侧获取相关广告系列所有流量入口的成本数据，但只能对YouTube和展示广告带来的iOS AC转化进行归因。因此，AppsFlyer显示的总体CPI更高。

SKAN安装

从Google Ads API V10+开始，Google Ads面板不再区分did_win=TRUE和did_win=NULL的激活，这两种激活仅在原始数据中有所区分。

从Google Ads API V10+开始，AppsFlyer仅展示回传中带有did_win=TRUE的激活。因此AppsFlyer中呈现的激活数量可能会比Google Ads低。

#### 注意事项

- Google Ads会在后台集中显示某个再营销广告系列产生的所有激活，而AppsFlyer的数据总览面板会分UA、再营销和统一视图分别显示新增激活、再归因以及两者相结合的数据。

- 在比较Google Ads和AppsFlyer的数据时，请确保Google Ads面板的数据是从第三方分析平台（AppsFlyer）导入的数据。从Firebase或Google Play导入的数据结构与AppsFlyer不同，因此无法进行全面的对比。如需了解如何将数据从AppsFlyer导入到Google Ads面板，请参考 此文档 。

- 如需比较激活事件（在Google Ads中为first_open），请确保在Google Ads的转化报告中切入到激活事件层级查看数据。这是由于Google Ads可能会显示所有转化（如激活、购买、订阅），因此必须先将数据范围缩小到激活事件再进行对比。

#### 另请参见

- 请参考 Google Ads与AppsFlyer的SKAN互动设置 ，了解iOS 14的相关注意事项。
