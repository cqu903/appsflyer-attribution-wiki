---
source_url: https://support.appsflyer.com/hc/zh-cn/articles/207033826
ingested: 2026-06-24
sha256: 859965da35b1e79057f26103a637c553fa6c3cf18b7863760151252447df3943
---

# Meta ads对接设置指南

Source URL: https://support.appsflyer.com/hc/zh-cn/articles/207033826
Section: Meta ads
Updated: 2026-05-25T14:36:39Z

概要： 本文主要讲解了如何完成Meta ads与AppsFlyer的对接配置。

## Meta ads设置指南

如要使用AppsFlyer来对Meta ads上的应用广告进行归因，最初的对接流程需要多长时间？

如果您已经在您的 应用中接入了AppsFlyer SDK ，并且在Meta ads上定义了您的应用，那么只需要不到一分钟的时间就能完成对接！

完成对接后，您无需登陆Facebook或在应用中接入Facebook SDK，即可进行移动归因。请按下文所述的 基础设置步骤 说明进行操作，完成后可以进一步了解Meta ads的 高阶设置选项 。

## Meta ads基础归因设置

### 创建和检索Facebook应用ID

在AppsFlyer中配置Meta ads对接之前，首先需要创建并获取 Facebook App ID 。

请按以下步骤创建Facebook App ID ：

- 从 Meta ads 后台进入您的 App Dashboard （应用面板）。

- 点击 Apps 下方的 Create New App 。

- 填写您的应用名称，并输入命名空间。请确保添加到您应用下的平台正确无误，否则可能无法对激活进行准确的归因。

请按以下步骤获取Facebook App ID ：

- 从 Meta ads 后台进入您的 App Dashboard （应用面板）。

- 点击所需的应用。

-
点击并复制屏幕左上方的App ID。

AppsFlyer是根据App ID来归因数据的，您可以使用同一个Facebook App ID对某个应用的 安卓和iOS版本 进行归因。但需要注意，Meta ads限制iOS 14+应用的广告账户数量，一个应用不能超过9个账户。

### 启用Meta广告设备层级数据

自2025年6月17日起，Meta重新开放了 高级移动衡量(AMM) 报告功能。启用后，您将能够：

- 获取设备层级移动分析数据

- 针对Meta广告活动的事件级归因指标

- 与您现有的AppsFlyer面板和导出功能实现完整对接

如需启用 AMM，请按照以下步骤操作：

- 进入 Meta ads 。

- 选择相关的应用 ID。

- 接受Meta的高级移动衡量条款。

#### 重要提示！

- 您的Meta开发者应用管理员需要接受Meta AMM条款。

- 只有在接受AMM条款之后新增的归因设备，您才能获得具备完整归因的设备层级数据。

- 应用内事件的限制状态与其对应转化保持一致。也就是说：
- 如果归因到事件的转化发生在签署AMM协议之前，则该事件依旧受限。

- 如果归因到事件的转化发生在签署AMM协议之后，则您可在原始数据报表中查看该事件。

### 设置Meta Ads活跃对接

- 从AppsFlyer的侧边栏中选择 协作 > Partner Marketplace 。

- 搜索并选择Meta ads。

- 点击 设置对接 ，界面会跳转到对接设置页。

- 打开渠道 对接 选项卡中的 启用该渠道开关。
注意： 在您与该渠道合作期间，请确保该开关总是处于打开（即 启用 ）状态。

-
在 通用设置 部分：

- 将 Facebook App ID 粘贴到对应字段中。

- 将Meta ads中的Install Referrer 解密密钥 粘贴到对应的字段框中。

- 打开或关闭 高级数据共享 ，请参见下面的 高级数据共享 部分。（截止至2024年10月14日，已向所有账户开放）

- 点击 保存对接 。

### 【可选】以下为推荐设置的配置方法：

- 将点击回溯窗口期设置为7天，与Meta ads的窗口期对齐。
（请注意： 某些情况下，默认窗口期会有所变化 ）。

- 将浏览回溯窗口期设置为1天，与Meta ads的设置对齐。

- 如需对 再归因窗口期 内完成重装激活的用户进行归因，请打开 重装激活归因 开关。
您不必再启用浏览型归因或配置重装激活归因的回溯窗口，因为这里直接沿用了激活归因的设置。

## Meta ads高级归因设置

Meta ads的基础归因设置完成之后，您可以进一步设置一些高级对接配置。

### 获取Android激活的设备层级数据

#### Google Play Install Referrer API

对于将用户引导至Google Play商店的Android应用广告，Meta广告会与广告主共享广告系列的元数据。在这种情况下，广告主可以通过Google Play Install Referrer API获取归因字段（须在相关应用中 接入该API ）。 通过Google Play install referrer API提供的字段会在AppsFlyer原始数据报告的匹配类型（match type）一栏以 gp_referrer 标记出来。这些数据仅当同时满足以下条件时才会出现：1）解密密钥已提交；2）有归因到Meta ads 的激活。这样，AppsFlyer就能对没有广告ID（即启用LAT）的用户进行归因。

#### Meta install referrer

#### 注意

Meta install referrer允许AppsFlyer从设备的本地存储中获取广告活动的元数据。请参阅 开发者中心（Dev Hub） 了解如何启用SDK以访问Meta install referrer。

除了Google Play Install Referrer API以外，AppsFlyer还可以通过Meta install referrer接收来自设备本地存储的广告投放元数据，用于归因衡量。Google Play Install Referrer API和Meta install referrer之间的主要区别如下：

- Meta install referrer可包含展示和点击数据，而Google Play Install Referrer API仅包含点击数据

- Meta install referrer可包含多个session的数据，而Google Play Install Referrer API仅可传递末次session的数据（相关设备必须在同一个session中完成点击和激活）。

基于以上因素，原始数据中归因到Meta的激活数量可能会少有上涨。通过Google Play Install Referrer API或Meta install referrer对激活进行归因时，相关数据会出现在原始数据报告中。通过Meta install referrer获取的字段会在原始数据报告的匹配类型（match type）一列标记出来，用于归因。来自Facebook的数据标记为 fb_referrer ，来自Instagram的数据标记为 ig_referrer 。这些数据仅当同时满足以下条件时才会出现：1）解密密钥已提交；2）有归因到Meta ads 的激活。Meta install referrer的解密密钥与 Google Play Install Referrer的解密密钥 相同，因此无需在AppsFlyer中重复提交。

#### 由Referrer提供的广告系列归因字段如下：

- 即相关广告的ID

- 即相关广告的名称

- 即广告组的ID

- 即广告组的名称

- 即广告系列的ID

- 即广告系列的名称

- Account ID（账户ID）

- 流量入口（Channel）

#### 注意

- Google Play Install Referrer API：
- 请确保您使用的AppsFlyer SDK为 V5.4.0及以上版本 ，否则Referrer数据可能无法正常发送。Referrer数据的优先级高于API数据，且不受限。该解决方案适用于点击型归因，不适用于浏览型归因。

- 流量入口（Channel）字段的值取决于Google Play Install Referrer API传递的channel值（由Meta发送到Google Play）。如果AppsFlyer接收到的channel值为空字符串，则流量入口字段显示为“None”。

- Meta install referrer： 请参阅公告中的 前提条件和必要操作 。

#### Meta install referrer—常见问题解答

Meta install referrer在哪些场景中可用于归因？

- 激活归因：
- 点击型归因适用于所有广告系列

- 浏览型归因适用于进阶赋能型应用广告（Advantage+ App Campaigns）和普投（如使用默认的受众年龄和性别设置）的手动应用广告（Manual App Promotion Campaigns）。

- 兼容性：Google Play Store和第三方安卓应用商店

- 例外情况：不适用于跳转到落地页的广告

Meta ads中的普投用于哪些场景？

如需接收浏览型激活数据，就必须使用普投（Broad targeting）。适用于普投的投放配置包括：

- 年龄：默认设置 （18-65+）

- 性别：默认设置（所有性别）

- 地理位置：可指定国家和国家集群。 请注意： 位置定向较为精准的广告（如根据城市或邮编进行定向投放）须使用可浮动范围（inclusion targeting），并将定向要求设置为“relaxed”（宽松）。

- 精准定向：按用户兴趣、行为和高级人口特征细分人群时将定向要求设置为“relaxed”（宽松）。

- 自定义人群包：将定向要求设置为“relaxed”（宽松）。

- 将定向要求设置为“relaxed”时，必须针对相关广告系列勾选“Advantage detailed targeting”，如下图所示：

#### 来自Google Play Referrer API或Meta install referrer的加密数据

来自Google Play Referrer API或Meta install referrer的数据由Meta完成加密。您可以使用您Meta开发者账户中的密钥对这些数据进行解密。您需要向AppsFlyer提交该密钥，具体步骤请见下文说明。每个应用只需提交一次。

请注意：如果该密钥缺失或被删除，即使在没有上述广告系列归因字段的情况下，AF仍可以根据Referrer将激活归因到Meta ads，但需要符合以下条件：

- Meta ads未认领该激活

- 从Google Play Install Referrer API接收到数据，但该数据未解码

- 且对应的广告交互是激活前的最后一次点击

请按以下步骤获取Meta账户中的解密密钥：

- 登录Meta开发者平台。

- 点击进入页面右上角的 My Apps 。

- 选择相关应用，获取其解密密钥。

- 从页面左侧进入 Settings > Basic 。

- 向下滚动到安卓部分，即可在Package Names字段下方看到标记为Install Referrer decryption key的解密密钥。请注意：这个板块就是您之前配置包名和Google Play Store的地方。

请按以下步骤在AppsFlyer后台设置解密密钥：

- 【必须完成】确认您应用中接入的AppsFlyer SDK是V5.4或以上版本。切勿使用之前的版本。

- 从AppsFlyer的侧边栏中选择 协作 > 活跃对接 。

- 选择 Meta ads 。

- 在 对接选项卡 中，将密钥粘贴到 Install Referrer Decryption Key 字段中。每个应用只需提交一次密钥。

- 点击 保存对接 。

### 成本、点击和展示

该对接可针对成本、点击和展示提供广告系列、广告组、广告和国家/地区维度的汇总数据。详情请见 广告平台成本对接表 ，其中详细说明了适用维度、指标和功能。

请注意： 对接中默认包含点击和展示数据，但您 需要购买 ROI360 产品 才能获取成本数据。

成本API的启用方式如下 ：

- 确保您已登录Meta ads帐户，且该帐户已开通Meta ads的广告系列管理权限。此处登录的用户必须具有管理Meta Business Manager所有广告系列的权限

- 进入 成本 选项卡。

- 打开 获取成本、点击和展示数据 开关。

- 点击 f login 按钮。您可以使用Meta广告业务帐户或管理员帐户登录。

- 在后续弹出的窗口中选择允许AppsFlyer访问您的Meta ads广告投放数据。
请注意 ：对接后每次同步数据时，AppsFlyer会接收最近7天的Meta ads成本数据。

如需删除绑定的Meta ads账户，请按以下方式操作： 在行动栏中，将鼠标悬停在账户上，点击 删除连接 。

#### 注意

- 如果您已经登入Meta Ads，则点击 f login 按钮时，窗口会出现闪退，这是正常现象。

- 如果有多名用户具备Meta ads权限，建议让这些用户都完成登录操作， 以避免出现数据不完整的问题 。

#### 成本数据同步状态

您可以在成本（及广告收入）对接状态面板或单独的广告平台面板中查看AppsFlyer最近一次拉取成本数据的时间以及 成本API状态 。

您可以同步多个帐户的成本数据拉取。对于已完成对接的账户，AppsFlyer会显示成本对接的状态以及最近一次拉取到匹配成本数据的时间。

如需进一步了解数据扩充，请参考 成本、点击及展示数据 。

### 应用内事件映射

请按以下步骤映射应用内事件：

- 打开 应用内事件回传 开关。
首次 为某个应用启用Meta ads应用内事件映射时， af_app_open 会自动映射到 fb_mobile_activate_app 。

- 填写以下参数:

参数名称 说明

AppsFlyer事件 事件的名称，即AppsFlyer从SDK侧接收到的事件名称或来自S2S事件的名称。
提示 ：如果下拉菜单中没有您要查看的事件：
- 请确保以非自然方式激活应用，并完成该事件，然后再次检查该事件是否在列表中。

- 在 AppsFlyer事件 中输入该事件的名称，然后点击 创建自定义事件 。详情请见 自定义事件映射 。

渠道映射事件 Meta ads为每个事件定义的专属名称或ID。映射配置包括以下几种：
- 文本字段： 从Meta ads获取相应的事件ID。

- 下拉菜单： 选择最合适的AppsFlyer预定义事件。

- 按原样 ：按原样发送事件，不进行名称映射。

事件来源 选择事件回传的范围：
- 仅该合作渠道 ：仅回传归因到Meta ads的事件。

- 所有媒体渠道，包括自然流量 ：回传归因到任何渠道以及自然量的事件。

回传内容
- 无数据（默认） ：仅发送事件本身，不带事件值

- 值和收入 ：发送所有事件参数， 包括 收入（若有）。

- 仅发送值： 发送 除 收入以外的所有参数。

- 如需在列表中添加SDK 或S2S 事件，请点击 添加事件 。

关于事件名称的限制：

- 事件名称的长度限制：2-40个字符

- 不允许使用以下字符：
- 冒号（:)

- 期间（。）

- 非拉丁（英文）字母的字符集：自2020年1月12日起，Meta ads不再支持中文字符。AppsFlyer尚未测试其他字符集，因此您在使用其他字符集之前，请先确认Meta ads是否支持回传中出现这些字符。

- 事件名称区分大小写。为避免差异，请确保在所有媒体源和应用程序版本的事件名称中使用正确的大小写。

#### 注意

Meta广告可以根据您的广告收入数据通过 将 af_ad_revenue 事件映射到正确的Meta广告事件 ，以优化您的广告系列。

### 再营销归因

广告主可以通过AppsFlyer的再营销归因功能记录与Meta Ads广告互动的现有用户，并衡量其之后的应用内行为。建议仅在针对已激活相关应用的Facebook用户投放广告时才使用该功能。

- 在应用设置页面打开再营销开关 。

- 进入Meta ads渠道页面，打开 再互动归因 开关。

- 设置 点击型再互动回溯窗口 。
用户点击广告后，在再互动回溯窗口期内完成打开应用时，AppsFlyer才会将该应用打开记录为再互动。
选择归因窗口期的单位（小时或天），并将滑块滑动到所需值。

- 启用 浏览型再互动归因。

- 使用滑动条根据您的需求设置 浏览型再互动回溯窗口期 （最长为24小时）。用户浏览广告后在该窗口期内打开应用时，AF会将其记录为一次再互动。

- 设置 再互动窗口 。
在此期间，用户的应用内事件主要归因到再营销媒体渠道。
这个值可以设置为数天（1-90天）、数小时（至多23小时）或用户的整个生命周期。默认值为30天。

深入了解 AppsFlyer再营销归因 。

深入了解 通过深度链接实现Meta ads等SRN上的用户跳转 。

### 高级数据共享（Advanced data sharing）

开启 高级数据共享 后，Meta在接收带有设备层级标识符的回传及事件时会覆盖到所有设备，包括将Advertising ID（即IDFA）设置为不可用的设备。

此外，启用 高级数据共享 后，AppsFlyer 会对这些事件进行归因。该功能关闭时，仅限带有IDFA的设备所产生的回传和事件才会得到共享和归因。

这种方法可对iOS点击和浏览带来的激活，以及iOS深度链接带来的再互动进行归因，适用于关闭广告标识符或同时关闭广告标识符和ATT授权的设备。基于最后触点归因，最长归因窗口期为24小时。

#### 注意

如果 高级数据共享 开关一打开，但您未收到Meta的归因数据，请检查这些事件是否符合Meta的共享标准。详情请见 Meta提供的说明文档 。

### 加州消费者隐私法案（CCPA）合规性

CCPA隐私条例规定限制来自美国加州Meta ads用户的数据。

如需符合CCPA要求 ： 请在 渠道对接 选项卡中打开 限制Meta ads使用用户个人信息（CCPA） 开关。

详情请见 数据保护法律法规 。

### 广告收入记录

如果您的应用通过Meta Audience Network Ad Revenue进行广告变现，您就可以使用AppsFlyer记录来自Meta ads的收入。无论您的应用是否存在应用内购数据，该方法都可以让您 全面了解用户带来的收入 。

#### 记录Meta Audience Network的广告收入

- 进入 广告收入 页面，打开 获取广告收入数据 开关。

- 选择您想要获取的汇总层级广告收入数据类型： 已归因的收入 和/或 汇总变现收入 ：
- 已归因的收入 （Attributed Revenue）：按获客渠道分组的收入。
设置 事件来源 ，选择最符合您的变现模式的应用内事件。例如，如果您的广告收入基于广告展示，则建议向AppsFlyer发送ad_viewed（广告浏览）事件。您可以为每个变现平台分别设置最合适的事件，也可以使用 af_app_opened 事件。这时，广告收入会分别归因到用户完成的各次应用打开。

- 汇总层级的变现收入 ：按广告渠道分组的收入。

- 界面会显示 广告收入 事件。这是一个只读字段，代表名为[source event]_monetized的新增广告收入事件（如上图的Ad_Watched_Monetized）。该广告收入事件会在面板中作为专门记录广告变现的独立事件显示。

- 点击 连接至Meta ads ，收集Meta Ads上的Meta Audience Network广告收入。请使用您的Meta ads证书进行登录，以开通Meta Audience Network Ad Revenue权限。

- 输入 Audience Network App ID（ Facebook App ID ）。 您可以从Meta Audience Network中获取此ID。
- 获取 Facebook App ID 。

- 将该ID复制粘贴到AppsFlyer后台的 Audience Network App ID 字段。

- 点击 保存广告收入 。

### 授权

您可以为Meta ads开通某些权限，允许其执行对应的操作并获取对应的数据。

详情请见 为对接渠道授权 。

## 适用于iOS的Aggregate Event Measurement（AEM）

AppsFlyer支持 Meta ads的Aggregated Event Measurement （全事件衡量，简称AEM）。该解决方案可用于优化Meta ads上的iOS转化及应用内事件，同时对iOS再互动进行归因。

## Meta ads对接问题排查

如果您已完成基础对接，但仍未在AppsFlyer面板看到来自Meta ads的归因结果，可能是因为对接之后Meta ads尚未带来新增激活。

出现该问题时，请检查是否出现以下情况：

### 未收集IDFA

您必须将AdSupport.framework添加到您的项目中，才能进行IDFA的收集。详情请参见iOS专用的SDK对接指南。您可以检查激活原始数据报告中的IDFA一列是否为空。建议通过您的iOS应用收集IDFA，通过安卓应用收集GAID。
从iOS 14.5开始，您必须在应用界面显示ATT弹窗，在用户同意授权后才能收集IDFA。

请注意： SKAdNetwork归因不受IDFA可用性的影响。但请确保在Meta ads后台设置iOS 14广告时打开“iOS 14 Campaign”开关。

### 错误的Facebook App ID

Facebook App ID在AppsFlyer后台中配置有误。
请检查该App ID是否与Meta ads后台的值完全一致。

注意：您还可以使用 Facebook的Graph API 来验证您的Facebook App ID。

### Meta ads上的应用状态

您必须将Meta ads上的应用状态设置为 Live （已上线）而不是 In development （开发中），否则无法正常归因。

### Meta ads广告类型设置有误

请确保您的Meta ads广告是 Mobile App Install （移动应用激活）或 Mobile App Engagement （移动应用互动）广告。对于其他的投放目标（如用于落地页的 Link Click 链接点击），广告主需要在配置Meta ads广告时 勾选 App Event Recording （应用事件记录）选项 ，才能衡量移动端激活。

### AEM归因未生效

如果 高级数据共享 开关一打开，但您未收到Meta的归因数据，请检查这些事件是否符合Meta的共享标准。详情请见 Meta提供的说明文档 。

### Meta ads应用激活

设置Meta ads中的App Install（应用激活）广告时，您可以从下拉列表中选择应用，也可以复制粘贴该应用的完整商店链接。虽然这两种方法在Meta ads上都可行，但如果您第二种方法，会导致AppsFlyer无法归因。

下图为正确的设置方法，按此方法设置后AppsFlyer可正常归因。

下图为错误的设置方式，按此方式设置后AppsFlyer无法正常归因。

### 与Meta ads有关的iOS 14更新

我们会确保AppsFlyer与Meta Ads的MMP对接总是使用 Advertiser Tracking Enabled 标记，因此广告主无需在AppsFlyer后台进行任何操作。这是继Meta ads在2021年2月推出iOS 14应用指南后做出的更新。

#### 相关文档

- 请参考 Meta ads与AppsFlyer的SKAN互动设置 ，了解iOS 14的相关注意事项。

- Meta投放管理合作平台配置 （ Bidalgo / Kenshoo / Adquant / Webpals ）
