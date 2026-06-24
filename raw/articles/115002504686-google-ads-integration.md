---
source_url: https://support.appsflyer.com/hc/zh-cn/articles/115002504686
ingested: 2026-06-24
sha256: 31adf14a584c384fbe6081ad6d2dca52b6ad86d35779dfd4f5ccf15fef88a635
---

# 广告主的Google Ads（AdWords）对接设置指南

Source URL: https://support.appsflyer.com/hc/zh-cn/articles/115002504686
Section: Google Ads
Updated: 2026-06-16T15:25:09Z

概要： 本文重点讲解了如何将您的Google Ads账户接入AppsFlyer，以便集中查看所有广告的归因数据。

#### 重要提示！

AppsFlyer支持Google的欧盟意见征求新政，详情请见 相关公告 。

## 使用Google Ads时的注意事项

Google Ads后台只能配置iOS和安卓平台的 App Campaign （应用广告）。

归因来自其他平台的用户，例如针对Windows Phone用户的Google Ads，需要使用 落地页解决方案 。

如需配置App Campaign之外其他特定类型的广告，请联系您的Google服务代表。

## 广告主的Google Ads归因配置指南

请按以下步骤使用AppsFlyer对Google Ads投放进行归因：

#### 注意

作为与Google Ads对接的先决条件，该应用必须收集IDFA / GAID。详情请见 SDK对接指南 。

### 第1步：创建Google Ads Link ID（必需完成）

请注意：相关账户必须具有 Google管理员权限 才能创建Link ID。

- 登入您的Google Ads管理员账户。

- 在顶部菜单栏中点击 Tools and settings 。

- 在 Setup 菜单下选择 Data manager ，并点击 + Connect Product 。

- 在 Data sources 搜索栏中，输入“Third-party app analytics”并选择该选项，然后点击 Continue 。

- 点击 Create link ID 。

- 选择 AppsFlyer 作为您的应用分析服务商（app analytics provider）。

- 选择安卓或iOS作为相关操作平台。

- 搜索并选择您的应用。

- 点击 Create link ID 。

### 第2步：在AppsFlyer后台设置Google Ads（必需完成）

（AppsFlyer帐户中的任何成员都可执行以下操作）

- 从AppsFlyer的侧边栏中选择 协作 > Partner Marketplace 。

- 搜索并选择 Google Ads 。

- 点击 设置对接 ，界面会跳转到对接设置页。

- 打开 渠道对接 选项卡中的 启用该渠道 开关。
请注意： 在您与该渠道合作期间，请确保该开关总是处于打开（ 即启用 ）状态 。

- 将您在上一步流程中复制的 Link ID 粘贴到相关字段中。

- 确定是否打开 非欧盟用户 开关。

- 配置 激活归因 ：
- 设置 点击型激活回溯窗口期 。
选择归因窗口期的单位（小时或天），并将滑块滑动到所需值。我们建议将窗口期设置为30天，以便与Google Ads匹配。

- 【可选】若投放安卓应用的预注册广告，请设置 预注册广告回溯窗口期 （默认为90天）。这个滑动条用于调整预注册广告的激活归因回溯窗口期。

- 启用 浏览型激活归因 。

- 选择归因窗口期的单位（小时或天），并将滑块滑动到所需值。建议将浏览型窗口期设置为1天，以便与Google Ads的窗口期相匹配。
请注意： Google不认领iOS应用的展示，因此对于iOS应用，您无需使用浏览型激活归因开关和回溯窗口期滑动条。

- 打开 重装激活归因 开关，以启用重装激活归因。
重装激活归因的回溯窗口期沿用激活归因中的设置，因此这里无需再配置。

#### 重要提示！

重装激活的转化数据在Google Ads控制面板上 记录为session_start ，而AppsFlyer则会对其归因并在面板上将其记录为再归因。

- 配置 再互动归因 ：
- 在应用配置页面启用再营销 。

- 在Google Ads的对接设置中启用再互动归因

- 设置 再互动点击回溯窗口期 。用户点击广告后在该窗口期内打开应用时，AF会将其记录为再互动。选择归因窗口期的单位（小时或天），并将滑块滑动到所需值。

- 启用 浏览型再互动归因 。
请注意： Google不认领iOS应用的展示，因此对于iOS应用，您无需使用浏览型激活归因开关和回溯窗口期滑动条。

- 设置 浏览型再互动窗口期 。用户浏览广告后在该窗口期内打开应用时，AF会将其记录为再互动。选择归因窗口期的单位（小时或天），并将滑块滑动到所需值。

- 设置 再互动窗口期 。用户点击或浏览广告后在该窗口期内完成的应用内事件会被归因到再营销渠道。这个值可以设置为数天（1-90天）、数小时（至多23小时）或用户的整个生命周期。默认值为30天。

- 如果拥有 Google Ads iOS 应用资源 （即此前的应用扩展）：
如需通过广告链接获取归因信息，请在 归因链接 选项卡中创建一个单平台的AppsFlyer归因链接，然后将其添加到该Google Ads扩展程序中。
请注意： 请务必添加一个静态的广告系列名称（必须配置）。

- 进入 成本 选项卡。

- 打开 获取成本、点击和展示数据 开关。

- 点击 Connect Google Ads 按钮并登录到您的Google帐户，这样您就能在AppsFlyer上查看所有的Google Ads投放成本了。 更多详情, 请 点击此处

- 点击 保存 。

#### 重要提示！

- 如需在Google Ads中查看AppsFlyer归因到的激活和再互动数据，必须导入以下AppsFlyer事件：
- “First open”（首次打开，用于激活）

- “Session start”（会话开始，用于再互动）

- 只有在 完成第4步 之后，您才能在AppsFlyer后台看到Google Ads激活。如果您还需要将应用内事件映射到Google Ads，请先完成 第3步 。

### 第3步：导入应用转化（必须完成）

#### 重要提示！

您必须打开应用并触发需要映射的应用内事件 ，才能让 Google Ads 记录新增的转化。如需测试iOS应用，则必须收集IDFA才能看到该事件。添加事件转化后最多需等待6小时才能生效。添加完毕后，您就可以导入这些事件。导入后，新增转化的状态就会从“No recent conversion”（最近无转化）变为“recording conversion”（正在记录转化）。

请注意：相关账户必须具有 Google管理员权限 才能创建Link ID，从而完成此步骤。

请根据 Google Ads提供的说明文档 完成相关操作。在此过程中请注意以下事项：

- 在第7步中，勾选所有应用中的first_open事件（这是衡量激活所必需的）。接着，如果您希望通过Google衡量再互动，请导入session_start事件；最后，请以相同的方式导入您希望通过Google衡量的所有应用内事件。 请注意： 如果Google Ads中的渠道映射事件ID（Partner Event identifier）发生了变更，或被标记为自定义（CUSTOM），这时即使对应的事件在AppsFlyer中也做了相应的更改，您仍需要重新导入相关数据。

- 完成相关流程后，进入 Conversions > Summary 页面时您就能看到第三方转化事件。如果您需要的事件未出现在列表中，或者该事件已从Google Ads的转化列表中移除，请按以下方式操作：
- 点击 View all conversion actions （查看所有转化行为）。此时界面会显示 Status 状态筛选条件。

- 点击 Status 并选择 All 查看所有事件，包括已停用或删除的事件。

- 请确保“include in conversions”的设置与您的Google Ads投放目标（campaign goals）一致。详情请咨询您的Google账户经理或参阅 此处的Google文档 。

完成上述操作后，您就能通过AppsFlyer来衡量Google Ads移动广告了。

### 第4步：映射应用内事件（推荐）

（AppsFlyer帐户中的任何成员）

- 进入 对接 选项卡，向下滚动到 应用内事件回传 部分。

#### 注意

首次 启用某个应用的Google Ads应用内事件映射时：

- af_app_opened 会自动定义并映射到 session_start （如未自动映射，请手动添加）。

- 请务必在 事件来源 菜单中选择 所有媒体渠道，包括自然流量 ，这样Google Ads才能收到这些事件。您可以在对接设置完成后根据实际情况更改事件来源选项。

- 打开 应用内事件回传 开关。

- 点击 添加事件 ，将SDK事件或 S2S事件 添加到列表中。

- 请配置以下参数：

参数名称 说明

AppsFlyer事件 事件的名称，即AppsFlyer从SDK侧接收到的事件名称或来自S2S事件的名称。
提示 ：如果下拉菜单中没有您要查看的事件：
- 请确保以非自然方式激活应用，并完成该事件，然后再次检查该事件是否在列表中。

- 在 AppsFlyer事件 中输入该事件的名称，然后点击 创建自定义事件 。详情请见 自定义事件映射 。

渠道映射事件 Google Ads为每个事件定义的专属名称或ID。从下拉菜单中选择最贴合您业务需求的AppsFlyer预定义事件。

事件来源 选择事件回传的范围：
- 仅该合作渠道 ：仅回传归因到Google Ads的事件。

- 所有媒体渠道，包括自然流量回传所有带量渠道以及自然量的事件。

回传内容
- 无数据（默认） ：仅发送事件本身，不带任何事件值。

- 发送值与收入 ：发送所有事件参数， 包括 收入（若有）。

- 仅发送值 ：发送 除 收入以外的所有参数。

- 点击 保存对接 。

- 您可以在保存对接后留在配置页面，将其他应用也对接到该渠道。
- 点击页面左上角渠道名称下方的应用名称，打开应用列表。

- 在下拉菜单中选择一个其他应用。

- 为选定应用完成对接设置。

#### 提示

Google Ads API对接默认包含Google Ads再营销功能，因此您在完成该对接并向Google Ads发送事件后，就可以直接在Google Ads中创建再营销受众列表，而无需再进行任何其他对接。

## 如何为Google Ads团队成员开放权限

您可以向Google Ads 开放您帐户中某些数据的访问权限 ，只需在Google Ads配置页面的授权选项卡中完成相应操作即可。

您的Google Ads服务代表必须是AppsFlyer中Google Ads渠道账户下的团队成员，否则无法获得权限并访问您的应用。

受Google的隐私要求限制，Google只有在广告主提出明确要求时才能在其AppsFlyer渠道帐户中添加新的团队成员。

请按以下步骤为Google Ads团队成员开放应用访问权限：

- 填写并提交 此表格 ，申请将您的Google账户经理添加到AppsFlyer的Google渠道帐户中。

- 等待Google Ads确认已添加您的GA账户经理。

- 进入 配置 > 活跃对接 > Google Ads > 授权 ，并将您客户经理的邮箱地址添加到团队成员列表中。

- 激活您要授予Google Ads账户经理的权限。

详情请见 如何为广告平台授权 。

## 代理如何启用Google Ads归因

AppsFlyer支持Google Ads的代理配置，但广告主和代理必须各自有单独的Google Ads帐户，这样AppsFlyer才能对数据进行正确的归因。如需了解详情，请点击 此处 。

## 多个Google Ads帐号同时投放

如果您同时使用多个Google Ads帐户推广同一个应用，AppsFlyer也能衡量其投放效果。您只需要在Google Ads中共享Link ID并将事件导入各个Google Ads帐户中即可。

详情请见 Google相关文档 ，其中说明了如何共享Google Ads Link ID。

## iOS应用广告

请注意 ：本章节内容仅适用于以激活（installs）为目标的的应用广告， 不适用于 互动（engagement）。

2021年1月27日， Google出台新政策 ，以顺应iOS 14的要求。

ATT实行后，由于Google iOS应用不使用ATT弹窗，因此Google Ads产品也就 不再使用 ATT框架下的设备标识符IDFA（YouTube应用除外，该应用支持ATT弹窗）。

为了实现针对iOS 14+流量的报告和投放优化，Google扩展了其模型转化功能。

由于模型转化是不需要设备ID的，因此在iOS 14.5上线后，Google的iOS激活广告库存逻辑如下：

- iOS ACI搜索的流量入口/库存不归因（基于2020年1月24日的政策）。

- iOS ACI展示的流量入口/库存可以归因，前提是必须有设备ID，这需要用户在广告主应用和媒体侧应用上都同意授权。请注意，谷歌目前仅对iOS上的点击归因，不对展示归因。

## 在应用广告中使用延迟深度链接

深度链接的含义和作用原理

潜在用户点击信息流广告后会跳转到应用页面。用户安装并打开该应用后，SDK会通过延迟深度链接提供具体的产品信息。应用开发人员可以使用这个数据将用户带入应用中的相关体验。

Google中的延迟深度链接

您可以利用 Google应用广告系列中的广告Feed 或 广告组的延迟深度链接 为移动端的新增用户打造一个丝滑的使用体验，为其呈现定制化内容。Google支持广告Feed或广告组中的深度链接。在这两种场景中，AppsFlyer都支持延迟深度链接。

请按以下步骤在Google Ads中启用延迟深度链接：

- 如需从AppsFlyer SDK侧拉取 af_dp 参数，请务必使用 GCD 。

- 进入Google后台，设置 Feeds 或 广告组级别的延迟深度链接 。

- 从AppsFlyer后台进入 配置 > 活跃对接 。 选择 Google Ads (Adwords) 。

- 在 对接 选项卡中，启用 Google Ads的延迟深度链接 。

- 点击 保存对接 。

## Google Ads参数映射

下表说明了Google Ads和AppsFlyer之间的参数映射关系。请注意：广告主无法在Google Ads广告中添加自定义参数。

平台类型 搜索 展示 YouTube

Channel (af_channel) Channel （流量入口）参数的填充方式 请见下表

Campaign (c) 是 是 是

Campaign ID (af_c_id) 是 是 是

Adset（af_adset）
由ad_group_name参数填充。
如果该参数为null，AF会以ad_group_id来填充af_adset。 是 是 是

Adset ID (af_adset_id)由Google ad_group_id参数填充 是 是 是

Ad (af_ad) 不适用 N/A 不适用

Ad ID (af_ad_id) 不适用 N/A 不适用

Ad Type (af_ad_type) 是* 是* 是*

Site ID (af_siteid) GoogleSearch/
SearchPartners 不适用 YouTubeVideos/
VideoPartners

Keywords 不适用 N/A 不适用

### Channel （流量入口）参数的填充方式

Google Ads不发送 Channel(af_channel) 参数。AppsFlyer会按Google Ads侧的广告系列类型，根据以下规则判断如何填充该参数：

广告系列类型 和 平台类型逻辑： Channel 参数 示例

campaign_type network_type

ACI 、 ACE 、 ACPRE 、 Shopping 或 Hotel
所有平台类型
campaign_type_network_type channel = ACI_Search

若非
ACI 、 ACE 、 ACPRE 、 Shopping 或 Hotel 展示 network_subtype channel = mGDN

若非
ACI 、 ACE 、 ACPRE 、 Shopping 或 Hotel
若非
展示 network_type channel = Search

详情请见 Google回传中可能出现的广告类型 。

### 广告系列类型：应用广告系列

#### Google Ads的广告系列名称变更

到2021年2月15日为止 从2021年2月23日开始

UAC ACI

UACE ACE

UACPre ACPRE

请注意： 广告系列名称类型取决于点击或展示日期而非激活日期。

### 原始数据报告中的engaged view参数

Engaged view（深度观看）是指用户观看时间超过10秒的视频广告展示，它的归因优先级与点击相同。 在Android设备上，“深度观看”会在原始数据报表中 Engagement Type 和 Sub Param 5 参数下显示为 engaged_view 。
当“深度观看”发生在 AppsFlyer 中定义的点击回溯窗口期内（最长为 3 天），就会被计入归因。

#### 重要提示！

- 谷歌是一个SRN (自归因渠道)。更多关于这类平台的归因信息，请 点击此处 。

- 也就是说，AppsFlyer可以呈现Google提供的所有投放信息。广告类型（搜索、视频、展示）和相关信息取决于Google。请点击 此链接 查看详情。

## 没有设备ID时如何优化Google Ads投放

iOS14.5+和Android 12+上线后，Google Ads推出了多种新的标识符，以便在没有设备ID的情况下进行确定性归因：

标识符 上线日期 数据来源 操作系统 用于 数据颗粒度

gclid 2021年12月 Google Play Referrer 安卓 激活假量 用户层级数据

gclid 2021年12月 深度链接URL 安卓 + iOS 再互动 用户层级数据

gbraid 2021年3月 深度链接URL iOS 再互动 汇总

AppsFlyer接收到这些标识符后会将其回传到Google Ads，然后Google Ads会根据该回传数据来认领相关的转化。最后，AppsFlyer会根据Google Ads的认领来判定归因参数以及LTV事件的关联参数。
这个环节无需广告主进行任何操作。

### 分操作系统的数据可用性

安卓应用：

对于没有设备ID的流量，广告主可在AppsFlyer和Google Ads后台看到完整的拉新和再营销投放数据。

iOS应用

对于没有设备ID的流量，广告主可以在Google Ads和AppsFlyer后台看到完整的再营销投放数据。

#### 相关文档

- 请参考 Google Ads与AppsFlyer的SKAN互动设置 ，了解iOS 14的相关注意事项。
