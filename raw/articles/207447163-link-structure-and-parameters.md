---
source_url: https://support.appsflyer.com/hc/zh-cn/articles/207447163
ingested: 2026-06-24
sha256: c74574376649e473d007e2bd7413b294eec7d1018d7c2d3ef14123d84b1305b6
---

# 链接的结构和参数

Source URL: https://support.appsflyer.com/hc/zh-cn/articles/207447163
Section: 归因概念
Updated: 2026-06-22T13:07:14Z

概要： 本文重点介绍了AppsFlyer归因链接的结构和参数。

## 速览

广告主可利用归因链接收集用户的广告互动数据。归因链接是广告背后的链接，当用户与广告互动时，该链接就会向AppsFlyer上报该行为。用户点击或浏览广告即形成广告互动， 这时AppsFlyer就会收到一条归因链接的副本。

归因链接可以是 OneLink 链接，也可以是 单平台链接 。

OneLink（多平台链接） 单平台链接

说明及使用场景
使用场景：

- 需要使用同一条链接完成多个平台的投放。

- 需要深度链接功能。

- 您想要使用安卓的App Link或iOS的Universal Link调起应用。

进一步了解OneLink

使用场景：

- 仅在一个平台上投放，如仅投放安卓或iOS。

- 仅使用URI scheme吊起应用。

进一步了解对接渠道的设置流程

前期准备 OneLink模板 无

必须配置的信息
- 媒体渠道

- 广告系列

- 子渠道ID/次级子渠道ID

- 媒体渠道

- 广告系列

- 子渠道ID/次级子渠道ID

基础链接 {subdomain}.onelink.me app.appsflyer.com

独立标识符 模板ID app_id

链接结构 https://{subdomain}.onelink.me/
{templateid}?pid={media_source}
&af_siteid={ApplicationID}
&c={CampaignName} https://app.appsflyer.com/{app_id}?pid={media_source}&af_siteid={ApplicationID}&c={CampaignName}

示例 https://yourbrand.onelink.me/aAB1?pid=greatnetwork_int
&c=GreatCampaign&af_siteid=A1b1 https://app.appsflyer.com/com.greatapp?pid=greatnetwork_int&
c=GreatCampaign&af_siteid=A1b1

#### 重要提示！

AppsFlyer仅支持通过HTTPS协议传输的互动流量，即点击和展示。

## 归因链接参数

- 归因链接中的可用参数如下表所列。

- 字段类型 一列说明了参数值的字数限制。详情请见 参数值长度限制 。

### 归因链接参数——拉新及再营销

您可以 下载下表说明（ .csv 文件） ，以供参考。

参数 原始数据中的字段名称 说明 字段类型和长度：

pid Media Source AppsFlyer对接渠道的唯一标识符。切勿更改。 更多详情 。 字符串限长150

c Campaign 由广告主或发行商提供。详见 广告系列名称限制 。 字符串限长100

af_prt Partner
- 代理帐户名称-可以把激活归因给相应代理

- 注意 ：在启用 授权代理 之前，请勿使用此参数。
字符串限长50

af_mp 不适用
- 可向媒体营销渠道发送分激活的回传。

- 请注意 ：此参数目前仅适用于Pinterest Marketing Partners。

clickid 不适用 广告平台唯一点击标识符

af_siteid Site ID
- 用于标记广告发行商（展示广告的媒体）的唯一ID。 了解详情
字符串限长24

af_sub_siteid Sub Site ID
- 次级广告平台/媒体ID。

- 如果除了主要媒体（子渠道）以外还有次级媒体，或者您想要了解广告样式（如横幅、插屏、视频）等的其他信息，请使用af_sub_siteid参数。示例：af_sub_siteid =ABCD_4567
字符串限长50

af_c_id Campaign ID 由广告主/发行商提供 String 24

af_adset Adset
- 由广告商/发行商提供

- 广告组是在广告系列之下、广告之上的一个广告层级。 详情请见此处。
String 100

af_adset_id Adset ID 由广告主/发行商提供 String 24

af_ad Ad 广告名称（ 了解详情 ）——由广告主/发行商提供 String 100

af_ad_id Ad ID 由广告主/发行商提供 String 24

af_ad_type Ad type 包括以下各种广告类型：
- native （软广）：这种付费广告与媒体平台中的非广告内容完美融合（包括在视觉效果和功能方面），出现在用户的推荐视频中。

- banner （横幅）：一种展示广告，一般呈小块长方形，出现在网页或应用界面中的各种位置。

- interstitial （插屏）：在发布广告的应用中占据整个界面的全屏广告。这类广告会设计在内容衔接处或在用户链路的过渡环节出现（占据如活动或游戏升级、暂停时）。

- rewarded_video （奖励视频）： 一种视频广告，用户看完整个视频就能在应用内得到奖励，如游戏中的生命值、文章的读取权限，或公共场合的Wi-Fi使用权限等。这类奖励型广告能在吸引用户互动的同时为其提供更好的应用内体验。

- audio （音频）： 在线播客或音乐流媒体平台内以音频格式投放的广告。

- offerwall （积分墙）：一种应用内广告单元，开发应用的厂商可通过这种形式进行变现。这种广告类似于应用中的迷你商店，其中列出各种“积分任务”，用户完成任务后即可在应用内获得相应的奖励。
String 24

af_ad_format Ad format 包括以下各种广告类型：
- text （文本）： 以简短的文本段落形式出现的文字广告。一般由标题、描述以及链接或CTA按钮组成，用于激发用户兴趣并引导用户点击进入网站或落地页。

- image （图片）： 通过图像或照片展示某个产品、服务或品牌视觉型广告。通常由引人注意的图片以及精简的文案组成，可能还会带有CTA按钮。

- video （视频）： 使用视听内容传达营销信息的数字广告。视频长度不一，可作为前、中、后贴片广告穿插在视频内容中，也可在各类平台上单独展示视频广告。

- playable （试玩）： 一种互动式广告，为用户提供一个迷你版的游戏或应用，让其在正式下载或购买前先行试用，亲身体验游戏玩法或应用功能。

- interactive （互动）： 一种吸引用户参与或互动的动态广告，可包含小问答、调查问卷或其他互动元素，目的是引起用户注意并引导其积极参与。

- dynamic_product （动态产品）： 一种个性化广告，可根据用户行为、偏好设置或浏览历史记录动态填充产品信息和详情，向用户展示高度相关的定制化产品广告。

- carousel （轮播）： 在一个广告中展示多个幻灯片或卡片，每张卡片可以包含不同的图片、标题和描述，让广告主在单个广告中展示多种产品或功能。

af_click_lookback Attribution lookback window
- 点击归因的窗口期，用户点击广告/链接后在此期间激活应用才能被归因到相应渠道，也就是CTIT（点击到安装时间）的最大值。

- 点击归因窗口期可在以下范围内自行调整：可用参数值为1d-30d (天) 或 1h-23h (小时)。默认值为7d。

- OneLink和SRN 的归因窗口可自行设置。
请注意 ：仅影响点击URL，不影响展示URL。 最多3个字符

af_viewthrough_
lookback 不适用
- 浏览归因窗口期可在以下范围内自行调整：可用参数值为1h - 24h（小时）。默认值为24h。

- SRN 的归因窗口可自行设置。
请注意 ：仅影响展示URL，不影响点击URL。 最多3个字符

af_channel Channel 分发广告的媒体渠道流量入口，比如UAC_Search、UAC_Display、Instagram、Meta Audience Network等。 动态枚举。字符串限长20

af_keywords Keywords 文本定向型广告的关键词列表 String 100

af_cost_model Cost model
- 成本模型，通过点击上报成本时仅支持CPI（默认），填充 AppsFlyer汇总数据报告中的成本值 。

- 请尽量通过 API 上报成本。同时通过链接和API上报成本时，API优先级更高。
字符串限长20

af_cost_currency Cost currency
- 符合 ISO-4217 的3字母货币代码， 如USD、ZAR、EUR。

- 【默认】：USD
3字符枚举

af_cost_value Cost value
- 以成本货币为单位显示的成本值。

- 最多精确到小数点后4位。

- 只能设置数字（可带小数点）例如：“ 56”，“ 2.85”
字符串限长20

af_sub[n]

(n=1-5) 例：af_sub1
Sub param [n] 由广告主自行配置的可选参数。详情请见 特点与局限性 部分，其中说明了这些参数的用法。 String 100

af_r 不适用
让用户跳转到指定网址，支持 所有平台 （安卓、iOS和PC）。

在多平台链接（OneLink）中，该参数：

- 会覆盖模板层级的跳转设置

- 会被以下链接层级的参数覆盖：
- af_android_url

- af_ios_url

- af_web_dp

请注意： 参见其他跳转参数 特性与局限性 。

af_web_dp 不适用
让PC端（例如Windows或Mac）用户跳转到OneLink模板中指定网页以外的URL。此参数用于将PC端用户的归因数据保存到其他平台（如Google Analytics或Omniture）。

请注意： 参见其他跳转参数 特性与局限性 。

af_dp 不适用
URI scheme作为备用方案，可在Universal Link或Android App Link失效时或用户使用的安卓版本低于6.0时打开应用。建议仅使用该方法进入 基本路径 ，即默认页面。

请注意： 如果你为该参数使用了网页URL（不推荐），请务必查看跳转参数的 特性与局限性 。

af_force_deeplink 不适用 用于强制执行af_dp中的 深度链接

af_ref 不适用
使用S2S点击的广告平台可以通过以下参数发送referrer值：&af_ref= ReferrerValue

每个点击的af_ref值 必须 是唯一的，结构如下：

NetworkName_UniqueClickValueForEachClick

示例: af_ref=networkname_123456789ABCDEF

广告平台名称可由任意的有效字符串组成，可以是networkname_int，或直接使用平台名称。

AppsFlyer会使用该参数对安卓设备进行归因，但不会将其用于iOS或Windows设备。

is_incentivized 不适用
布尔值：true / false

用于标记广告是否带有奖励

af_param_forwarding 不适用
- 该参数为“false“时，归因链接里的参数不会传递到跳转后的页面。

- 此参数用于精简跳转页面的链接，或预防由归因链接参数造成的跳转问题。

af_base_params_forward 不适用
- 该参数为“false“时，归因链接里的AppsFlyer PID和C参数不会传递到跳转后的页面。

- 如果用户会从PC端点击相关链接，且您想要保留基本的CRM参数但移除AppsFlyer PID和C参数，这时可以使用这个参数来避免链接中出现多个PID。

af_partner_account_id Network Account ID 渠道侧的广告主帐户ID String 100

redirect 不适用 &redirect=false 时，即可为AppsFlyer标识出S2S点击，并告知AF该点击中渠道负责为用户实现跳转。

af_ua User-agent
适用于发送 S2S 点击和展示的广告平台。

用户代理（user-agent）字符串 以下列形式发送：

- URL参数（URL-编码）

- HTTP请求头（Request Header，未编码）

URL参数和HTTP请求头中的 User-Agent应完全一致。

请注意 ：在安卓平台中，User-Agent有时会被缩减版的Client Hints取代。这种情况下仍会发送该字段。

- 完整的user-agent字符串示例： Mozilla/5.0 (Linux; Android 12; Pixel 5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/95.0.4638.16 Mobile Safari/537.36

- 缩减的user-agent字符串示例： Mozilla/5.0 (Linux; Android 10; K) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/95.0.0.0 Mobile Safari/537.36

af_ip IP
适用于发送 S2S 点击和展示的广告平台。

设备IP地址

建议 ：在af_ip参数中提供设备IP（若可用）。

次优方案 ：AppsFlyer会使用X-Forwarded-For中的IP（若可用）。

【已弃用】af_os OS version（操作系统版本）
【仅适用于iOS】设备的操作系统版本。

AppsFlyer已弃用但仍支持该参数。建议：使用af_os_version参数代替。

af_os_version OS version（操作系统版本）
- 适用于发送 S2S 点击和展示的广告平台。

- 设备的操作系统版本。
- 安卓：
- 举例来说，12

- 对于缩减后的User-Agent（ 若广告交互发生在PC端浏览器中或使用Chrome 100+引擎的安卓平台中） ，广告平台必须使用 Client Hints API 来拉取该参数值。

- 对于 未 缩减的User-Agent，可使用以下正则表达式来攫取User-Agent字符串中的安卓OS版本信息： (\d+(?:\.\d+)*);(?:\s..-..;)?\s(.+?(?=\)|\s\w*\/)) 。

- iOS：
- 举例来说，16.2

af_model Device model
- 适用于发送 S2S 点击和展示的广告平台。

- 用于表示设备型号。
- 安卓：
- 举例来说，Pixel 5

- 对于缩减后的User-Agent（ 若广告交互发生在PC端浏览器中或使用Chrome 100+引擎的安卓平台中） ，广告平台必须使用 Client Hints API 来拉取该参数值。

- 对于 未 缩减的User-Agent，可使用以下正则表达式来攫取User-Agent字符串中的安卓设备型号信息： (\d+(?:\.\d+)*);(?:\s..-..;)?\s(.+?(?=\)|\s\w*\/)) 。

- iOS：
- iphone 或 ipad （全部小写）

af_media_type 媒体类型 用于标记广告链接所在的媒体类型。分为以下两种：
- app：广告链接投放在应用中

- web：广告链接投放在移动端网页中

deep_link_sub1-10 不适用 其他的深度链接值。开发人员需要将这些值执行的跳转写入代码中。

deep_link_value 不适用 具体应用内内容的名称，用户点击链接后会跳转到相应页面。开发人员需要把 deep_ link_value执行的跳转写入代码中。

af_og_title 不适用 在社交媒体上分享链接时，可使用开放图谱（Open Graph，简称OG）标题来生成标题预览。 字符串限长40

af_og_description 不适用 在社交媒体上分享链接时，可使用开放图谱（Open Graph，简称OG）描述来生成描述预览。 字符串限长300

af_og_image 不适用 在社交媒体上分享链接时，可使用开放图谱（Open Graph，简称OG）图像来生成图像预览。

### 归因链接参数——仅限再营销

参数 原始数据中的字段名称 说明 字段类型及长度限制

is_retargeting Is Retargeting (campaign) 所有再营销广告的点击链接里都应含有 &is_retargeting=true 。
如果不包括该参数或其值为 "false"，则AF会视其为拉新广告。 5字符枚举

af_reengagement_window 再互动窗口期
该参数用于调整 再互动归因窗口期 。

可在以下范围内调整：

- 1-90天或1-36小时

- 全周期：即再互动窗口期无限延长。示例： &af_reengagement_window=lifetime

默认值：30天

示例： &af_reengagement_window=30d 表示再互动窗口期是30天。
不适用

### 可见性参数

您还可以针对不同的广告类型发送相关的可见性参数，记录用户互动的详细情况。

参数 参数值格式 说明

af_video_total_length 秒数 视频总时长

af_video_played_length 秒数 视频播放时长

af_playable_played_length 秒数 试玩元素完全加载后玩了多长时间

af_ad_time_viewed 秒数 广告展示时长

af_ad_displayed_percent % 广告在设备屏幕上的最大占比

af_audio_total_length 秒数 音频总时长

af_audio_played_length 秒数 音频播放时长

### 安卓专用参数

参数 原始数据中的字段名称 说明 字段类型

advertising_id Advertising ID Google Advertising ID需要广告平台支持 最多49个字符

sha1_advertising_id 不适用 通过SHA1加密的Google Advertising ID——需要广告平台支持

md5_advertising_id 不适用 通过MD5加密的Google Advertising ID——需要广告平台支持 仅支持激活和再归因

android_id Android ID 设备Android_id需要广告平台支持 最多20个字符

sha1_android_id 不适用 通过SHA1加密的设备Android_id——需要广告平台支持

md5_android_id 不适用 通过MD5加密的设备Android_id——需要广告平台支持 仅支持激活和再归因

imei IMEI 设备IMEI ID

sha1_imei 不适用 通过SHA1加密的设备IMEI ID——需要广告平台支持

md5_imei 不适用 通过MD5加密的设备IMEI ID——需要广告平台支持

oaid OAID Open Anonymous Device Identifier（匿名设备标识符） Android SDK 4.10.3及以上版本可用

sha1_oaid 不适用 通过SHA1加密的匿名设备标识符——需要广告平台支持 Android SDK 4.10.3及以上版本可用

md5_oaid 不适用 通过MD5加密的匿名设备标识符——需要广告平台支持 Android SDK 4.10.3及以上版本可用

af_android_url 不适用
让安卓用户跳转到Google Play应用页面以外的链接。适用于 第三方应用商店 。

请注意： 参见其他跳转参数 特性与局限性 。

sha1_el 不适用 用于PC端到移动端的归因，电子邮箱经SHA1加密。需要广告平台支持。

fire_advertising_id 不适用 Amazon Fire Advertising ID

af_android_store_csl store_product_page Google Console中的自定义商店详情页（Custom Store Listing） 字符串

### iOS专用参数

参数 显示名称 说明

idfa IDFA
全部大写。需要广告平台支持。

字段格式：最多49个字符

idfv IDFV 全部大写。

af_ios_url
该参数用于落地页跳转，让iOS设备（iPhone或iPad）的用户跳转到iTunes应用页面以外的链接。

请注意： 参见其他跳转参数 特性与局限性 。

af_ios_store_cpp store_product_page
Custom product page ID（自定义产品页面ID，ppid）

请注意： 在原始数据和汇总数据中，仅针对广告点击记录af_ios_store_cpp（自定义产品页面ID）参数的值，广告展示中不记录该值。

af_ios_fallback【已弃用】 不适用 【已弃用】 通过 iOS URI scheme链路 实现跳转。

sha1_idfa 不适用 通过SHA1加密的IDFA。需要广告平台支持。

sha1_idfv 不适用 通过SHA1加密的IDFV。

mac 不适用 设备mac地址。需要广告平台支持。

md5_idfa 不适用 通过MD5加密的IDFV。

md5_idfv 不适用 通过MD5加密的IDFV。

sha1_mac 不适用 通过SHA1加密的设备mac地址。需要广告平台支持。

#### 示例
https://app.appsflyer.com/{app_id}/?pid=airpush_int&c=RedBanner& af_siteid={publisher_id}&af_sub1=1.5&af_sub2=USD&af_sub3=burst_campaign

这些参数在 激活报告 、 分析工具、报告工具、API 中都可用。

### 自定义参数

除了默认的安卓和iOS专用参数外，您还可以使用自定义参数。在归因链接中添加这些自定义参数能帮助您打造定制化的用户体验和内容。

您可以使用 parameter=value 的格式将自定义参数附在归因链接之后。例如：
https://app.appsflyer.com/com.greatapp?pid=networkx_int&c=winter&af_adset=coats&af_ad=cashmere&my_custom_param=my_custom_value
使用自定义参数时需注意以下两点：

- 自定义参数不会显示在原始数据中。

- 您可以通过 转化数据SDK API 来获取自定义参数。

### Partner ID（PID）参数

在所有可用的归因链接参数中，PID是必须配置的参数。 PID是媒体渠道的唯一标识符，由AppsFlyer设定。 。

每个 都有一个唯一的PID值，以 _int 为后缀。 使用 OneLink链接 时，您可以自行设置PID，但请确保该PID不是任何对接渠道的PID。

#### 注意

AppsFlyer将拦截在自定义媒体来源（如电子邮件或短信）中将SRN名称用作PID值的归因链接。 此限制 不适用 于ASRN。

几个重要的对接渠道ID包括：organic（自然量）、googleadwords_int（Google AdWords）、facebook_int (Meta ads)、twitter_int (X Ads). 对于非对接渠道（邮件、短信等等），您可以使用任何名称为其命名。

#### 如何避免常见的PID问题：

- 一定要在归因链接中配置PID， 否则获得归因的媒体渠道为“None”（无）， 且无法获知初始激活的流量来源 。

- 所有已对接渠道只能使用指定PID，否则无法对其激活进行正确归因。

- 如果是自有媒体，请勿使用对接渠道的PID。 对于电子邮件、短信、Facebook帖子之类的自有流量渠道，请使用对接渠道PID以外的值。例如 owned_email , sms_push ，或其他与对接渠道不同的自定义标识符 。

- 请确保PID中的字符有效。 如果归因链接中的PID参数包含 /<>*&?\ 中的任一字符，则：
- 相关点击或激活会显示在面板中的 af_invalid_param 下方

- 归因链接无法得到归因

- 点击中的深度链接功能无法正常生效

#### 提示

避免在PID 值中使用空格键， 或在使用 URL之前确保已对其进行归因链接编码。

### Site ID（子渠道）参数

子渠道ID用于标记投放广告的发行商， 即展示广告的网站或应用。广告平台 会为其发行商设定唯一的子渠道ID。

您可通过归因链接中的 af_siteid 参数将该ID上报给AppsFlyer，并在AppsFlyer面板、报告工具和回传中查看相关数据。

请务必通过归因链接将子渠道信息发送给AppsFlyer，因为：

- 这能让该媒体的数据更加清晰透明

- AppsFlyer会通过该信息来识别并剔除作弊媒体以及其他的虚假流量。

子渠道ID参数仅包含投放广告的发行商的ID。

如需了解其他信息，如广告的样式和/或版位（横幅、插屏或视频），请使用次级子渠道参数。

#### 示例

以下归因链接中包含：

- af_siteid ：子渠道ID

- af_sub_siteid ：次级子渠道ID，即其他的相关ID信息（这里代表某个联盟营销渠道以及广告样式版位）

https://app.appsflyer.com/com.yourapp?pid=mediaName_int&clickid={clickid}&advertising_id={gaid}& af_siteid=1234&af_sub_siteid=ABCD_4567

在示例链接中：

- 1234 = 子渠道ID

- ABCD = 与该发行商合作的联盟营销渠道（次级发行商）

- 4567 = 广告在该应用中的呈现样式，如横幅、插屏或视频

#### FAQ：为何流量中有很多被屏蔽的激活？

激活被屏蔽可能是由以下原因导致的：

- 子渠道ID缺失： 点击链接中的 参数为空。 互动数据中的子渠道ID为空时，不是出现了技术问题，就是该渠道为了避开防作弊机制而有意不填充该值。

- 多个子渠道ID： 多个点击链接使用不同子渠道ID来发送同一个广告发行商的数据。 这是一种作弊行为，目的是掩盖真正带来转化的媒体，通常是 撞库 的表现。

- 子渠道ID的格式错误： 如果子渠道ID格式有误，并同时出现其他作弊嫌疑，则AF不仅会屏蔽该子渠道，还会屏蔽上一级渠道的数据，并有可能影响到更大范围的渠道数据。

为了避免激活被屏蔽，请确保您对每个广告发行商仅设置一个子渠道ID参数，如示例链接所示。

## 数据粒度级别

您最多可使用4个链接参数来剖析广告效果。

如果您在所有的活跃归因链接上使用了全部4个参数，就可以实现下列功能：

- 将所有的用户激活和事件都归因到具体的广告

- 您可以在汇总报告中分广告组、广告系列、广告平台来查看和比较所有广告的综合表现，以便在各层级优化投放

- 您可以在原始数据报告和 数据透视表 里对各广告平台上的所有广告进行对比分析

参数名称如下：

- Media source (pid=)

- campaign name (c=)

- Ad set (af_adset=)

- Ad name (af_ad=)

#### 示例

以下归因链接运用了4种颗粒度，记录在“network”平台上投放的“winter”广告系列中”coats“广告组下的“cashmere”广告。
https://app.appsflyer.com/com.greatapp?pid=networkx_int&c=winter& af_adset=coats&af_ad=cashmere

## 常见问题

### 这些参数要用大写格式还是小写格式？

大写小写都可以，但必须保持一致。如果您用大写字母设置了一个自定义参数，就必须总是使用大写字母来表达该参数，反之亦然。

举例来说，如果您设置了pid=MyMediaSource，请确保您总是按照这样的大小写来使用该参数。如果您在一个归因链接中使用pid=MyMediaSource，而在另一个归因链接中使用pid=mymediasource ，就会产生数据差异，归因链接中的其他参数设置也是同理。

### AppsFlyer的归因链接是动态的还是静态的？

归因链接可以是动态的，也可以是静态的。
那么要如何判断一个链接是动态还是静态的呢？
如果 归因链接中包含参数 ，就表示这是一个已经定义完毕的归因链接，因此是 静态的 。
只有自定义归因链接的短链 （如 yourbrand.onelink.me/HaT8/r5c2b371 ）才是 动态 的。
也就是说，如果您在对接渠道中使用了配置好的归因链接，或在自有媒体中使用了长链，那么就算您之后在AppsFlyer后台更改了该归因链接的值，投出去的链接也不会随之变化。如果要让更改生效，就必须使用更新后的长链。
相反的，由于自有媒体的短链中不直接包含参数，因此用户与短链互动时，会跳转到AppsFlyer的服务器，这样当前的参数设置就会动态生效。

### Google Play Store的这条报错信息是什么意思？

如果您在点击一条归因链接后收到以下报错消息：

这是因为该归因链接中含有“#”这个字符。例如：
https://app.appsflyer.com/com.travelco?pid=globalwide_int&clickid=#reqid#
链接中的这类字符通常是宏，会被其他值动态取代。这种情况并不构成问题，您可以直接忽略该消息。

### Subscriber Parameters（自配参数）有什么用处？

Subscriber Parameters（自配参数），即af_sub1、af_sub2…af_sub_5，可用于记录任何您关注的KPI。您可以在原始数据报告中查看解析后的自配参数，以便对数据进行汇总或筛选。

#### 示例

一款名为Luber的打车应用有3种颜色的素材模板：蓝色、黄色和红色。Luber的移动营销人员Linda想要测试哪种颜色的模板能带来更多激活。因此她在所有非自归因平台的蓝色广告的归因链接里添加了 &af_sub3=blue ，黄色和红色广告以此类推。然后Linda在原始数据报告里查看解析后的相关信息，就能分析出不同颜色广告的效果并找出转化率最高的那一个。

### 广告系列名称有何限制？

- 归因链接中的广告系列名称长度不能超过100个字符。若超过100个字符，则该广告系列的名称会自动变成 c_name_exceeded_max_length 。

- 广告系列名称的不能以空格开头或结尾，否则会导致面板和报告的数据之间产生差异。

## 特点与局限性

特点 说明

特殊字符 在参数键和值中不允许使用以下字符（不适用于跳转和 af_dp 参数）： ;, *, !, @, #, ?, $, ^, :, &, ~, `, =, +, ’, >, <, /, {, }, %

跳转参数：
- 确保您的跳转URL域名已添加到您的 跳转白名单 中。

- 该参数的值必须是完整的有效网页URL（https://[domain][optional-path]），且符合 RFC 1738标准 ；该参数中不能使用URI scheme。

- 跳转URL 不支持 URI片段标识符 （如将用户引导至文章中特定部分的#webpagesection）。

链接长度限制 URL总长度不得超过2000个字符

安卓社交应用的Webview深度链接跳转 如需进一步了解具体限制，请参考 此文档

安卓版Naver Blog应用不支持深度链接 安卓版Naver Blog应用不支持深度链接，用户会跳转到Google Play Store或相关链接指定的网页。

iOS用户在Chrome浏览器中点击带有URI scheme的链接后界面显示弹窗 iOS版的Chrome发生了更新。更新后，用户在iOS的Chrome中点击URI scheme链接时，界面会跳出弹窗，让用户确认是否要打开相关应用/跳转到App Store。

URI scheme有效性要求 建议您使用符合 RFC 3986 标准的有效URI scheme。不符合该标准的URI scheme无法调起应用，且用户在网页视图（web view）或其他网页环境中点击相关链接后会出现报错。

Telegram WebView归因 如需进一步了解具体限制，请参考 此文档
