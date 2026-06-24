---
source_url: https://support.appsflyer.com/hc/zh-cn/articles/25096718837137
ingested: 2026-06-24
sha256: eb803a30d0074de518dded9fbb535b99d0acc7cd170b1d31b0a0ac63d674132e
---

# Google Ads（AdWords）网页广告投放配置说明

Source URL: https://support.appsflyer.com/hc/zh-cn/articles/25096718837137
Section: Google Ads
Updated: 2026-06-21T18:03:00Z

概要： 通过设置网页广告，对Google Ads带来的web-to-app转化进行归因。

#### 注意

本文将为您介绍如何设置推广移动应用的网页广告活动。如需设置用于推广PC或主机端应用的广告活动，请参见 PC和主机应用的Google Ads Web对接 。

## 概览

AppsFlyer支持网页广告专用的Google Ads对接（ googleads_int ），并且会通过Google Offline Conversion API（OCI）上报相关广告的归因和转化数据。

本文解释了移动端网页广告在AppsFlyer和Google Ads中的设置方式，针对通过Google Ads完成广告交互的网页用户进行归因。

在这类广告的用户链路中，用户首先点击广告，然后跳转到一个落地页。该落地页中带有AppsFlyer的智能脚本或智能横幅，用于生成归因链接。

用户在落地页中点击相关按钮后，这些由脚本或横幅生成的链接就会让用户跳转到对应的应用商店，下载并安装应用。AppsFlyer会记录由此产生的应用激活及后续的应用内事件，并通过OCI将这些数据上报到Google Ads。

然后，Google就可以利用这些数据来优化定向投放、衡量广告效果并打造自定义人群包。

### 前期准备

在您启用网页广告专用的Google Ads对接之前，请先确保您符合以下条件：

- 具备一个移动端应用

- 具备一个AppsFlyer账户

- 您AppsFlyer账户下的 用户具备必要的角色和权限 ，能够访问相关应用

### Google Ads网页广告的创建方式

本文说明了Google Ads中网页广告的设置方式，适用于通过AppsFlyer衡量投放效果的移动端、PC端和主机端应用。该流程主要包含两个方面：1）配置Google Ads和Appsflyer之间的对接，以及2）为相关投放设置归因链接。

- 在AppsFlyer中设置Google Ads对接 （必须完成）

- 在Google Ads中配置网页广告的投放 （必须完成）

在第一步中通过Google Ads与AppsFlyer的对接完成归因链接的设置后，第二步的主要任务是创建落地页。这一环节的原理是通过OneLink智能脚本或智能横幅，根据归因链接来生成CTA按钮，引导用户进入适配的应用商店。

- 创建带有OneLink智能脚本的落地页 （可选）

- 创建带有OneLink智能横幅的落地页 （可选）

## 在AppsFlyer中创建Google Ads对接

请先启用网页广告专用的Google Ads对接，然后设置AppsFlyer回传（通过OCI发送）。

### 1. 启用网页广告专用的Google Ads对接

- 在AppsFlyer面板的左侧菜单栏中点击 协作 > Partner Marketplace 。

- 搜索并选择 Google Ads Web 。

- 点击 设置对接 ，然后界面会跳转到 活跃对接 设置页面。

- 在 渠道对接 选项卡中，打开 启用该渠道 开关。 请注意： 在您与该渠道合作期间，请确保该开关总是处于打开（ 即启用 ）状态。

-
关闭 高级隐私保护 开关（设置iOS应用对接时适用）。

#### 注意

在您通过Google登录并按照下方步骤允许AppsFlyer获取token后， 令牌缺失 的错误提示将不再显示。如果在登录后错误仍然存在， 请验证您的令牌是否具有所需的权限 。

-
在 First open conversion ID 字段（应用首次打开的转化ID）中输入您在Google Ads中设置的 First open 转化操作ID。如需查看该ID，请进入Google Ads后台并打开 First open 转化操作页面中的 Details 选项卡。然后在该页面URL中复制 ctid=* 查询参数的值。举例来说，假设 ctid=123456789 ，您需要将 123456789 添加到 First open conversion action ID 字段中。

#### 提示

如果您尚未在Google Ads中设置“First open”操作（应用首次打开），可以在该操作设置完毕之前先输入临时的占位值。

- 输入您的 Customer ID 。您可以从Google Ads Manager中获取该ID：
- 登入您的Google Ads账户。

- 点击界面右上角的Google账户图标，然后向下滚动到Customer ID部分。

- 如果您有多个Google Ads账户同时为相关应用投放广告，必须使用经理账号（MCC）的Customer ID才能进行跨账户的转化监测。详情请见 Google提供的MCC账号配置说明 。

- 如需允许AppsFlyer将转化数据上传到Google Ads，请点击 使用Google登录 。

- 选择相关经理账号（即您在第7步中获取到Customer ID的MCC账号）中的管理员。

- 点击 Allow 。

### 2. 启用浏览型归因

AppsFlyer支持通过启用 智能脚本 或 智能横幅 的落地页，对Google Web广告系列进行浏览型归因。这项功能可以基于概率建模(PMOD)，将因广告曝光而触发的App激活进行归因，即使用户并未直接点击广告。

当用户看到Google广告并访问启用了智能脚本或智能横幅的落地页时，AppsFlyer可以将后续发生的App激活归因至最初的网页曝光事件，包括跨平台场景。

在可用的情况下，AppsFlyer会在给Google的回传中包含gclid参数。

启用浏览型归因

- 在AppsFlyer中，从侧边栏打开 活动对接 > Google Ads Web 。

- 在 对接 选项卡中，下滑到 激活归因 部分。

- 打开 浏览型激活归因 开关。

- [可选] 开启 跨平台归因具有同等优先级 并设置回溯窗口。有关更多信息，请参见 为跨平台展示启用同等优先级 。

- 打开 归因 选项卡。

- 下滑到 浏览型归因 部分并设置所需的 浏览归因回溯窗口 （最长24小时）。

- 点击 保存对接 以应用更改。

### 3. 应用内事件回传

目前只有用户激活才能触发Google Ads Web对接通过OCI API自动发送默认回传。对于其他类型的事件，您可以将AppsFlyer事件映射到Google Ads转化操作ID（“转化操作”或“conversion action”是Google Ads侧用于指称归因事件的术语），从而创建自定义回传。对于需要映射到AF事件的Google Ads Web事件，详情请咨询您的Google Ads账户经理。

- 打开 应用内事件回传 开关。

- 根据实际需求设置应用内事件回传窗口。详情请见 应用内事件回传窗口配置 。

- 点击 添加事件 ，将SDK事件或S2S事件添加到列表中。

- 在 AppsFlyer事件 一列，从下拉菜单中选择相关的事件名称。AppsFlyer会通过已接入您应用的SDK或者S2S事件API来获取该事件的名称信息。

-
在 渠道映射事件 一栏中 ， 请确保将相关的AppsFlyer事件映射到对应的Google转化操作ID（conversion action ID）。在此之前，您需要先在Google Ads中设置必要的转化操作。请参考 自定义转化操作配置 部分的说明，其中解释了如何在Google As中设置转化操作。

请按以下方式查找Google Ads中的转化操作ID：

- 登入Google Ads。

- 找到您要映射的转化操作，打开其页面。

- 打开 Details 选项卡。

- 然后在该页面URL中复制 ctid=* 查询参数的值。

- 回到AppsFlye中r的渠道对接部分。

- 将上述参数值粘贴到 渠道映射事件 一栏。举例来说，假设 ctid=123456789 ，则将 123456789 粘贴到渠道映射事件字段中。

- 在 事件来源 一栏中，选择 仅该合作渠道 。

- 在 回传内容 一列中，选择在回传中“发送值与收入”（如果该事件中有收入）。

- 【可选】点击 添加条件 图标，设置事件的 映射条件 。

- 点击 保存对接 。

- 【可选】您可以在保存对接后留在配置页面，将其他应用也对接到该渠道：
- 点击页面左上角渠道名称下方的应用名称，打开应用列表。

- 在下拉菜单中选择一个其他应用。

- 为选定应用完成对接流程。

### 4. 配置OneLink模板

为您的Google Ads投放创建OneLink归因链接之前，您需要先设置一个模板。然后您就可以根据这个模板来创建一条OneLink归因链接，并将其作为Google侧的跟踪模板链接（Tracking template URL）。

#### 注意

下文内容主要针对使用智能脚本的Google网页广告，说明了OneLink模板的具体设置步骤。如需了解更具普适性的OneLink模板设置方式，请参考 OneLink模板 说明文档中的 OneLink模板创建方式 部分。

- 在 新模板 或 编辑模板 页面中的 跳转 部分下，完成以下配置：
- 若用户未安装应用 > 跳转到 ：选择符合您需求的选项。 您在此处配置的跳转终点会被Google跟踪模板中跳转参数（ af_android_url 及 af_ios_url ）的 {lpurl} 值覆盖。详情请见 这部分 的说明。

- 若用户已安装应用 ： 切勿 设置Universal Link、URI scheme或App Link来调起应用，因为Google不允许导向最终到达网址（Final URL）以外的任何跳转。

- 若用户在PC端网页中点击链接 > 跳转到 ：选择符合您需求的选项。 您在此处配置的跳转终点会被Google跟踪模板中跳转参数（ af_web_dp ）的 {lpurl} 值覆盖。详情请见 这部分 的说明。

- 点击 创建模板 。

## 在Google Ads中创建一个网页广告系列

请在Google Ads中完成以下步骤：

### 1. 设置投放类型、投放目标和转化目标

Google Ads会根据您在此处选择的投放目标和业务目标来设置合适的竞价策略并优化投放效果。

- 登入Google Ads并创建一个广告系列。

-
选择投放目标（campaign objective）。

- 除“App promotion”之外，所有目标均适用（“App promotion”仅适用于移动端应用的广告）。

- 建议您将投放目标设置为“Sales”，以便根据具体的应用内事件进行优化。

-
选择转化目标（conversion goals）。

- 默认情况下，您会看到账户层级的预定义投放目标（campaign goals）。您可以根据实际的投放需求保留或移除相关目标。

-
如果您没有在该页面中找到您需要优化目标，

请 创建一个自定义的转化操作和目标 。

- 您还可以在Conversion页面中修改您的预定义目标。

-
选择所需的campaign type（广告系列类型）

- 除“Shopping”之外的所有广告系列类型均适用（“Shopping”类广告系列要求广告主配置商品目录，且仅限已验证的域名）。

### 2. 创建自定义转化操作

接下来，您需要为 AppsFlyer中您指定的各个应用内事件 创建Google Ads侧对应的转化操作。相关的转化操作创建完毕后，您需要复制该新建操作的ID，并将其粘贴到AppsFlyer面板中对应AF事件的“渠道映射事件”一栏，进行映射。

请按以下方式创建您自定义的Google Ads转化操作和目标：

- 进入您的Google Ads账户总览页面（Overview），从侧边栏中选择 Goals > Conversions > Summary 。

- 点击 + New conversion action 。

-
在转化类型列表中选择 Import ，然后选择以下任一选项：

- Manual import using API or uploads > Track conversions from clicks （通过API或上传手动导入 > 跟踪点击带来的转化）。

或

- CRM, files, or other data sources > Track conversions from clicks （CRM、文件或其他数据来源 > 跟踪点击带来的转化），然后在 Data source（数据来源） 部分下选择 Skip this step and set up data source later（跳过这一步，之后再设置数据来源） 。

- 点击 Continue ，进入下一步。

- 在 Conversion goal （转化目标）中选择一个转化操作类别。

-
在 Enter a conversion name （输入转化名称）部分，键入相关转化操作的名称。

#### 重要提示！

如需在使用GCLID的基础上，通过GBRAID/WBRAID搭配Offline Conversions API，请确保转化操作中的 Count 字段设置为 Every （默认），而非 One 。

- 输入转化名称后，点击 Add 添加该转化操作。 请注意 ：如果您只需针对某一个具体转化行为来优化投放，请仅在选定转化类别中添加这一个转化操作。举例来说，如果您希望自己的广告系列针对 First open （首次打开）进行优化，请确保该操作是您选定的转化类别中所包含的唯一一个转化操作。然后，您就可以在创建相关广告系列时将这个转化类别选作您的转化目标，用于优化投放。

- 点击 Save and continue > Done ，此时您尚未设置数据来源（data sources）。新创建的转化操作初始状态可能显示为“Inactive（未激活）”，在实际数据传入后会自动变为“Active（激活）”。

-
找到新建转化操作的ID，将该操作映射到AppsFlyer的回传事件。在相关转化目标的 Summary 页面中，点击您创建的转化操作，并复制转化操作页面的URL中 ctid=* 查询参数的值。

- 进入AppsFlyer后台，在“渠道对接”配置部分找到您想要让Google进行优化的AF回传事件，然后将 ctid 的值粘贴到 渠道映射事件 一栏。详情请见 应用内事件回传设置 部分的说明。

### 3. 设置相关广告系列的URL

Google Ads网页广告对于每个广告交互使用两条链接：Final URL（最终到达网址）和Tracking Template URL（跟踪模板链接）。用户点击相关广告时，这些链接会被同时触发，Google将这个功能称为“并行跟踪”（Parallel Tracking）。如需进一步了解并行跟踪，请参考 Google提供的说明文档 。

#### 设置最终到达网址（Final URL）

Google对于 最终到达网址（Final URL）的定义 是“用户点击广告后到达您网站上的网页的网址，也称为‘着陆页’。”

最终到达网址（Final URL）的设置方式

- 进入Google Ads后台，打开 Campaigns > ads 页面。

-
找到您需要的广告，点击该行中的编辑图标。

-
在 Final URL 字段中输入相关落地页的网址。

#### 重要提示！

切勿将最终到达网址设置为任何AppsFlyer网址（即OneLink链接或单平台归因链接），否则会导致您的广告系列被拒审。此处仅可使用不带任何跳转的直接访问网址，如某个网页的网址、Google Play商店网址或App Store网址。

请确保该网址是您需要引导用户进入的页面。可用选项有以下两种：

-
落地页网址 ：让用户跳转到某个落地页，吸引用户点击其中的CTA按钮，然后进入Google Play、App Store或其他应用商店下载相关应用。落地页中所包含的智能脚本或智能横幅可自动生成CTA按钮的URL。详情请见带有 智能脚本 或 智能横幅 的落地页创建方式说明。

您可以将AF归因参数添加到最终到达网址（Final URL）中，并将其映射到Google的ValueTrack参数，如 af_c_id={campaignid} 。用户点击这条Google广告后触发落地页的加载，然后智能脚本或智能横幅就会将这些参数复制到该落地页的传出链接中（传出链接是指从落地页跳转到其他地址的链接，由智能脚本或横幅自动生成）。如需进一步了解可用的ValueTrack参数，请参考 Google提供的说明文档 。

示例：
https://example.com?product=1234&af_c_id={campaignid}

-
应用商店地址 ，如App Store或Google Play。

#### 重要提示！

假设您将商店地址作为您的最终到达网址（Final URL）。这种情况下，如果要把归因参数和自定义参数信息发送到AppsFlyer，必须将AF参数添加并映射到跟踪模板链接（Tracking Template URL）中，除此以外别无他法。

https://play.google.com/store/apps/details?id=.com.app.id&hl=en&gl=US&referrer={gclid}&gclid={gclid}&campaignid={campaignid}

- APK文件的直接下载链接 ：让用户直接下载应用，不跳转到应用商店。

#### 跟踪模板链接（Tracking Template URL）的设置方式

由于Google Ads默认使用并行跟踪（Parallel Tracking），因此作为跟踪模板链接（Tracking Template URL）的AppsFlyer归因链接会在后台加载，从而使AppsFlyer记录到相关点击。在使用点击这里或智能脚本的情况下，并不强制使用Tracking Template URL。详见本文中 将Tracking Template URL与智能脚本或智能横幅配合使用 部分。

-
进入Google Ads后台，打开 Campaigns > Campaigns 页面。找到您需要的广告系列，点击该行中的设置图标。

-
展开 Settings 部分 > Additional Settings > Campaign URL options

-
在 Tracking template 字段中配置以下内容（基础链接 + 跳转参数）：

- 基础链接 ：根据广告点击的跳转终点设置基础链接：
- 如果广告点击的跳转终点是Google Play或App Store，请使用 单平台归因链接 （详见下文示例）。

- 如果广告点击的跳转终点是某个网页，请使用 OneLink归因链接 （详见下文示例）。

- PID参数： pid =googleads_int 是必须配置的参数，请确保您在链接中添加该参数。

- Site ID（子渠道）参数： 必须配置，因此请确保您在链接中添加 af_siteid 参数，并为其赋值（可使用任意值）。

- 广告系列名称参数： 必须配置，因此请确保您在链接中添加 c 参数，并为其赋值（该参数没有对应的ValueTrack参数）。

- force transparent参数 ： af_force_transparent=true 是必须配置的参数，请确保您在链接中添加该参数。此参数用于增强跳转行为的安全性，以确保符合Google相关要求。如未添加该参数，Google可能会拒绝投放您的广告。

- OneLink归因链接的跳转参数： 为确保并行追踪（Parallel Tracking）功能正常运行，请使用以下任意一种参数组合设置AppsFlyer跳转参数：
- 参数 af_android_url 、 af_ios_url 和 af_web_dp 必须设置为 {lpurl} （Google ValueTrack参数）。 重要提示！ 请确保三个参数都已设置，以保证归因链接在各种场景下均可正常跳转。
或

- 将 af_r 参数设置为 {lpurl} （Google ValueTrack参数）。

-
单平台归因链接的跳转参数： 为确保并行跟踪功能正常运行，请将 af_r 参数设置为 {lpurl} （Google ValueTrack参数）。

#### 重要提示！

为满足Google要求，请确保{lpurl}的值为有效跳转URL，需满足以下条件：

- 使用HTTPS协议。

- 需进行URL编码。

- 域名已添加到您的 跳转白名单 中

- 映射到Google ValueTrack参数的AppsFlyer归因参数 ，如 af_c_id ={campaignid} 。如需进一步了解可用的ValueTrack参数，请参考 Google提供的说明文档 。

- 切勿添加 af_dp 参数。

- 切勿包含任何可能改变跳转参数{lpurl}值的参数，如 af_base_params_forward 和 af_param_forwarding 。

#### 注意

有关Tracking Template URL的更多限制信息，请参见本文档中的 特性与限制 部分。

#### Google Tracking Template URL示例

Google跟踪模板链接（Tracking Template URL）中的 OneLink 示例如下：
https://subdomain.onelink.me/aAB1?pid=googleads_int&af_force_transparent=true&af_android_url={lpurl}&af_ios_url={lpurl}&af_web_dp={lpurl}&c=summer_sale24&af_siteid=123456&af_c_id={campaignid}&af_adset=sum24A&af_adset_id={adgroupid}&af_sub1={gclid}&af_sub2={gbraid}
Google跟踪模板链接（Tracking Template URL）中的 单平台链接 示例如下：
https://app.appsflyer.com/id1510557250?pid=googleads_int&af_force_transparent=true&c=examplecamp&af_siteid=123456&af_adset=exampleadset&af_adset_id={adgroupid}&af_c_id={campaignid}&af_ad_id={creative}&af_click_lookback=7d&af_r={lpurl}

#### 将Tracking Template URL与智能脚本或智能横幅配合使用

如果用户点击相关广告后跳转到带有智能脚本或智能横幅的落地页，则无需在跟踪模板链接（Tracking Template URL）字段中填入AppsFlyer归因链接。这是因为这些工具能够自动创建归因链接，当用户点击落地页中的CTA按钮时将该点击记录到AppsFlyer中。在决定是否要将Tracking Template URL字段留空时，请考虑以下两点：

- 如果Tracking Template URL字段中 未填充 归因链接：这时假设用户点击了广告而未点击落地页中的CTA按钮，并在回溯窗口期内直接进入相关应用商店下载应用，随后发生的激活将无法得到归因，因此您可能会遗漏这部分的激活数据。

- 如果Tracking Template URL字段中 填充 了归因链接：这时假设用户点击了广告，然后又点击了落地页中的CTA按钮，AppsFlyer会分别记录到两次点击，这可能会影响转化率的准确性。

## 创建带有OneLink智能脚本的落地页

用户链路： 用户点击Google广告后跳转到您的移动端网站，并进入一个带有CTA按钮的网页，引导用户下载您的应用。用户点击该按钮后，就会跳转到相应的商店。

### 整个链路中的数据流

W2A智能脚本的使用场景由以下几个阶段组成：

- 用户点击Google广告后，Google会分情况自动将以下参数添加到Final URL的末尾：
- gclid 参数，适用于安卓设备以及iOS设备中的授权用户。

- gbraid 和 wbraid ，适用于iOS设备中拒绝授权的用户。

- 相关广告的Google Tracking Template URL中除了跳转参数以外的其他所有查询参数。

- Final URL将用户引导至落地页。

- 该点击同时触发广告背后的Google跟踪模板链接（Tracking Template URL）在后台加载，该链接中包含自动添加的 gclid 、 gbraid 、 wbraid 和 pid=googleads_int 参数，用于在AppsFlyer中记录相关点击。

- 落地页加载的同时，智能脚本会向AppsFlyer发送一条展示，其中包含传入链接参数（传入链接是指从广告进入落地页的链接）。有了这条展示数据，AppsFlyer就能通过浏览型归因将转化匹配到落地页。如需进一步了解广告展示和浏览型归因，请参阅 此文档 。

- 智能脚本会根据传入链接中的参数，为落地页的CTA按钮生成传出链接，其中包含 gclid 、 gbraid 和 wbraid 参数（这里的传入链接是指从广告进入落地页的链接，传出链接是指从落地页跳转到其他地址的链接）。这些按钮可以引导用户：
- 进入Google Play和App Store（通过OneLink归因链接实现）。

- 进入多个平台的商店（例如CTV、Epic和Steam）。在此场景中，智能脚本会针对各个平台生成一条传出的链接，其中带有单平台的归因链接，用户点击后会跳转到对应平台的商店。

- 在用户设备中下载APK文件。

- 用户点击CTA按钮后，AppsFlyer会收到并记录该次点击。

- 用户跳转到相应的商店并下载该应用。

- 用户打开该应用时，AppsFlyer会记录到一个激活。

- 如果激活数据中带有可用的 install referrer ，AppsFlyer会根据概率模型或确定性归因逻辑对这个激活进行归因。

- AppsFlyer会生成一条带有 gclid ，或带有 gbraid 和 wbraid 以及其他事件参数的回传，并通过OCI API将其发送到Google Ads。Google Ads通过 gclid 参数，或通过 gbraid 和 wbraid 参数来识别相关点击，并使用其他参数对具体广告系列的投放进行优化。

### 设置带有智能脚本的落地页

如需在您的Google网页广告投放中使用智能脚本，请按以下方式操作：

-
创建一个智能脚本。

#### 注意

下文内容主要针对使用智能脚本的Google网页广告系列，说明了具体的设置步骤。如需了解更具普适性的智能脚本投放设置方式，请参考 OneLink智能脚本V2设置说明 中的 OneLink智能脚本创建方式 部分。

- 请确保所有的传入链接参数（即智能脚本要抓取的参数）都已添加到广告链接中。如需检查添加到传入链接末尾的参数，请进入Google Ads后台并查看您在创建最终到达网址（Final URL）或跟踪模板链接（Tracking Template URL）时设置的链接参数，详情请见 广告系列的链接设置说明 。

- 将广告中必须配置的传入URL参数映射到由脚本生成的传出URL参数，用户点击CTA按钮时，智能脚本会将这些参数发送到AppsFlyer：
- PID ：确保智能脚本从传入链接中提取 pid=googleads_int 参数，并将其映射到传出链接中对应的参数。

- GCLID ：为确保应用内事件的回传能成功发送到Google Ads，传出链接中必须带有 gclid 参数。传出链接中的GCLID参数映射取决于您使用的智能脚本版本。
- 2.8.1及以上版本：传入链接中带有 gclid 参数时，其参数值会自动传递到传出链接的对应参数中，无需手动映射。

- 2.8.0及以下版本：必须在 智能脚本 页面的 URL参数映射 部分手动配置 gclid 参数的映射。
- 在 映射对象 一栏中选择 自定义参数 。

- 在 出链参数 和 入链参数 字段中输入 GCLID 。

-
GBRAID 和 WBRAID ：如需针对iOS设备中的拒绝授权用户向Google Ads发送应用内事件回传，传出链接中必须带有 gbraid 和 wbraid 参数。传出链接中的 gbraid 和 wbraid 参数映射取决于您使用的智能脚本版本。

- 2.9.0及以上版本：传入链接中带有 wbraid 和 gbraid 参数时，其参数值会自动传递到传出链接的对应参数中，无需手动映射

- 2.8.1及以下版本：必须在 智能脚本 页面的 URL参数映射 部分手动配置 wbraid 和 gbraid 参数的映射。
- 在 映射对象 一栏中选择 自定义参数 。

- 在 出链参数 和 入链参数 字段中输入 gbraid 。

- 重复上述步骤，添加 wbraid 参数的映射。

#### 注意

如需使相关数据呈现在AppsFlyer的原始数据报告中，除了将传入的 gclid 、 gbraid 和 wbraid 映射到传出链接中的 gclid 、 gbraid 和 wbraid 之外，还必须使用 af_sub[1-5] ，再分别映射这三个参数。

### 设置带有智能脚本的跨平台落地页

单平台落地页的设置一般可由营销人员直接完成，只需在AppsFlyer后台的智能脚本页面完成所需配置，即可自动生成智能脚本。但如需用到跨平台落地页，则须由开发人员根据营销人员提供的参数来创建脚本。

如需在您的Google网页广告投放中使用智能脚本，请按以下方式操作：

- 请参考 此文档 中的说明，将您的OneLink模板应用于跨平台归因。

- 请确保所有相关的URL参数都已添加到传入链接末尾。如需检查添加到传入链接末尾的参数，请进入Google Ads后台并查看您在创建最终到达网址（Final URL）或跟踪模板链接（Tracking Template URL）时设置的链接参数，详情请见 广告系列的链接设置说明 。

- 请列出各传入参数在传出链接中的对应参数。例如将传入链接中的 af_site_id 参数映射到传出链接中的 af_site_id 参数。

- 请列出必要传出参数（即不能出现空值的参数）的默认值。

- 向您的开发人员发送以下信息：
- 您的传入-传出参数的映射方式。开发人员会创建一个脚本，根据您指定的传入-传出参数的对应关系，生成传出的直接访问链接。

- 各参数的默认值。脚本若未在传入的链接中发现对应的参数值，就会使用默认值来填充传出链接中的参数。

- 如果您使用OneLink归因链接，请将相关域名和模板ID发送给您的开发人员，用于创建传出的OneLink链接。域名和模板ID的格式为 your_brand.onelink.me/A1b2 ，若您使用品牌域名，则为 click.yourbrand.com/A1b2

- 将以下Dev Hub文档发送给您的开发人员：
- 创建可直接访问非移动端页面的传出链接时，请参考这些 说明及代码示例 。

- 创建跨平台落地页时，请参考这些 演示和说明 。

- 传入链接中带有 gclid 参数时，其参数值会自动传递到传出链接的对应参数中，无需手动映射（需使用2.8.1及以上版本的智能脚本）。您的开发人员仍可以选择将 gclid 映射到任意一个 af_sub 参数，以便在原始数据中查看该数据。详情请见Google Ads的GCLID说明部分。

## 创建带有OneLink智能横幅的落地页

用户链路： 用户点击Google广告后跳转到您的移动端网站，并进入一个展示智能横幅的页面，该横幅中带有CTA按钮，引导用户从对应的应用商店下载相关应用。

### 整个链路中的数据流

- 用户点击Google广告后，Google会分情况自动将以下参数添加到Final URL的末尾：
- gclid 参数，适用于安卓设备以及iOS设备中的授权用户。

- gbraid 和 wbraid ，适用于iOS设备中拒绝授权的用户。

- 相关广告的Google Tracking Template URL中除了跳转参数以外的其他所有查询参数。

- 该点击同时触发广告背后的Google跟踪模板链接（Tracking Template URL）在后台加载，该链接中包含自动添加的 gclid 和 pid=googleads_int 参数，用于在AppsFlyer中记录相关点击。

- 落地页加载的同时，智能横幅会向AppsFlyer发送一条 展示 ，其中包含传入链接参数（传入链接是指从广告进入落地页的链接）。有了这条展示数据，AppsFlyer就能通过浏览型归因将转化匹配到落地页。如需进一步了解广告展示和浏览型归因，请参阅 此文档 。

- 智能横幅会根据传入链接中的参数，为横幅中的CTA按钮生成传出链接，其中包含 gclid 参数。智能横幅只能生成OneLink链接。

- 当用户点击智能横幅中的CTA按钮时，AppsFlyer就会接收并记录该次点击。

- 用户跳转到相应的商店并下载该应用。

- 用户打开该应用时，AppsFlyer会记录到一个激活。

- 如果激活数据中带有可用的 install referrer ，AppsFlyer会根据概率模型或确定性归因逻辑对这个激活进行归因。

- AppsFlyer会生成一条带有 gclid 和其他事件参数的回传，并通过OCI API将其发送到Google Ads。Google通过 gclid 参数来识别相关点击，并使用其他参数对具体广告系列的投放进行优化。

### 设置带有智能横幅的落地页

#### 注意

下文内容主要针对使用智能横幅的Google网页广告系列，说明了具体的设置步骤。如需了解更具普适性的智能脚本投放设置方式，请参考 《智能横幅——移动端网页到应用解决方案（市场人员专用）》 文档中的 设置 部分。

如需在您的Google网页广告投放中使用智能横幅，请按以下方式操作：

- 创建一个智能横幅。详见 《智能横幅——移动端网页到应用解决方案（市场人员专用）》 文档中的 设置 部分。

- 请确保传入链接中包含以下参数：
- pid=googleads_int 参数。

- gclid 参数。智能横幅会自动将 gclid 参数传递到横幅生成的传出链接。如果 gclid 参数缺失，应用内事件的回传无法成功发送到Google OCI。

- 在iOS用户拒绝授权的情况下，确保传入链接中包含 gbraid 和 wbraid 参数。智能横幅会自动将这两个参数传递到横幅生成的传出链接。此时Google可在没有 gclid 参数的情况下通过 gbraid 和 wbraid 参数获取汇总的事件数据。

- 请确保所有相关的URL参数都已添加到传入链接末尾。如需检查添加到传入链接末尾的参数，请进入Google Ads后台并查看您在创建最终到达网址（Final URL）或跟踪模板链接（Tracking Template URL）时设置的链接参数，详情请见 广告系列的链接设置说明。

- 【可选】在横幅组设置页面的 动态归因参数 部分下，勾选第一个复选框。此设置可确保智能横幅上的链接中包含传入链接中的所有参数。

## 应用内事件回传问题排查

如果在Google Ads或Google Analytics中未显示应用内事件数据，或遇到“缺失令牌”错误，请在联系支持团队前，检查以下设置是否正确：

### 设置令牌权限

进入Google Ads后台，检查您的Access Token是否具有必要权限，可以上传离线转化：

- 进入Google Developers Console.。

- 确保 uploadClickConversions 具有以下OAuth权限范围： https://www.googleapis.com/auth/adwords

- 在 AppsFlyer的对接选项卡中，点击 使用 Google登录 。

- 选择MCC账户的管理员账户。

- 点击 Allow 。

### MCC账号的Customer ID

如果您有多个Google Ads账户同时为相关应用投放广告，必须使用经理账号（MCC）的Customer ID。详情请见 Google提供的MCC账号配置说明 。

### 转化操作ID

确保回传中的应用内事件映射到正确的转化操作ID（Conversion Action ID）。如需在Google Ads中查找转化操作ID，请参考 此处说明 。

### GCLID、GBRAID、WBRAID参数

智能脚本或智能横幅生成的传出链接中必须包含 gclid 、 wbraid 或 gbraid 中的任意一个参数，才能确保发送到Google OCI的回传能正常记录到Google Ads。

## 特点与局限性

特点 说明

面板 您可在在AppsFlyer经典面板中查看和分析iOS端的Google网页广告系列归因数据。在大多数情况下，SKAN面板并不适用于web-to-app的广告系列。

再互动归因
用户可能会看到激活被归因至 googleads_int ，而再互动被归因至 googleadwords_int ，尽管两者可能来源于同一广告系列。这种情况在预期范围内，并不表示存在技术问题。

这种情况通常出现在SRN对接同时启用的情况下，使其能够从同一Google Ads web2app广告系列中认领再互动事件。

成本数据 Google Ads Web的成本数据（ pid=googleads_int ）不会被自动检索。您可通过以下两种方式手动导入：通过电子邮件上传文件或通过AppsFlyer UI手动上传。以上操作适用于所有用户，包括ROI360订阅用户。

Tracking template URLs
Tracking Template URL必须遵循以下限制，否则将导致链接失效：

- 链接不得包含重复参数。

- 链接不得包含无效参数，例如：
- 无值参数、格式错误的参数，或无法解析的参数，无值参数如 key= 或 key 。示例： pid=googleads_int&key&c=campaign 或 pid=googleads_int&key=&c=campaign 。

- 某些ValueTrack参数缺少值，例如 {placement} 。为避免缺失，请确保Google Ads在Tracking Template中正确配置并填充对应参数；

- 如果您在Google Ads广告系列设置中的 Campaign URL 字段中填写了任何参数值，这些值必须与Tracking Template中的参数值保持一致。如不一致，请将其从Tracking Template中移除，以满足最新政策要求。

SRN归因异常 在某些情况下，即使广告系列为基于网页的Google Ads推广，激活事件也可能通过SRN被归因至googleadwords_int。这种情况通常出现在Google主动认领激活时，AppsFlyer会根据Google的认领结果进行归因。这种现象属于预期范围内，随着谷歌扩大对网络广告激活归因的支持，这种情况可能会变得更加普遍。

适用套餐 googleads_int 对接仅适用于Growth和Enterprise套餐客户。Zero和Welcome套餐客户无法使用此对接功能。
