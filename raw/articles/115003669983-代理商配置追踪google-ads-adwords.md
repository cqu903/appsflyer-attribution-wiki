---
source_url: https://support.appsflyer.com/hc/zh-cn/articles/115003669983
ingested: 2026-06-24
sha256: 6932e1b3853d93985be96d9fbaf58b5a0a0ae2fba9f8f1475172fe385db0078d
---

# 代理商配置追踪Google Ads (AdWords)

Source URL: https://support.appsflyer.com/hc/zh-cn/articles/115003669983
Section: Google Ads
Updated: 2026-05-25T14:21:15Z

## 介绍

通过配置对接Google Ads，广告主可以让代理商代其在Google Ads平台投放广告。

广告主和代理商都需要参与配置操作。以下视频讲解了为了追踪到代理商为广告主在Google Ads平台投放的移动流量数据，广告主和代理商分别需要操作的相关步骤。

在代理商使用该操作指南之前, 广告主必须首先完成配置Google Ads的相关操作。详细操作，点击 这里 .

## 代理商配置跟踪Google Ads的操作步骤

使用AppsFlyer追踪代理商在Google Ads的广告系列，请按以下步骤进行操作：

视频 文本

广告主需提前操作的步骤：将Link ID分享给代理并在AppsFlyer后台给代理开启授权。

广告主必须在AppsFlyer后台给代理商授权需投放的APP， 授权步骤查看 这里 .

广告主如何给代理商授权Link ID:

1. 在Google Ads的控制面板中点击 工具

2. 选择 已关联的账号 .

3. 找到“第三方应用分析工具”，点击“详细信息”

4. 找到需要分享的Link ID, 点击 与另一个账号共享 .

5. 填入 代理商Google Ads账户的Customer ID

6. 点击 下一步 >> 发送邀请

广告主可以看到Link ID的分享邀请已发送给代理商，当代理商接受邀请后，状态会改为分享。

关于分享Google Ads Link ID的更多细节，点击 这里 .

代理商 步骤1：接受Link ID

在Google Ads的控制面板中，代理商收到邀请，点击接受邀请

代理商可以看到链接的状态改为Active。

代理商 步骤2:在AppsFlyer账户中配置Google Ads

1. 在左侧导航栏中，点击“媒体平台配置“，搜索并进入Google Ads配置页面。

广告主创建并填入的Link ID，在代理商账户中显示为灰色，代理商不可编辑修改。

2. 代理商填入Google Ads Customer ID.

填入代理商为广告主的App投放的 所有 Google Ads Customer IDs ( 子账户 )

#### 备注

填入Google Ads Customer ID时，必须 删除 连字符或空格。

在Google Ads后台点击左上角的箭头图标，在导航栏上方可以找到 Customer ID

3. 点击保存并关闭

如需要，一个代理商可以有多个Google Ads Customer IDs。

代理商 步骤3: 配置应用内事件

前提：广告主给代理商开启了配置应用内事件的权限(在广告主的AppsFlyer账户中授权操作）

1. 找到应用内事件回传部分

2. 选择“only events attributed to this partner”(只发送归因于此合作伙伴的事件)或“Events attributed to any partner or organic"(将所有事件数据发送给该合作伙伴）

3. 将需要回传给Googel Ads的所有应用内事件与Googel Ads预定义的事件名称一一对应。
4. 点击 Save .

#### 重要!

为了Google Ads后台和AppsFlyer后台都可以统计到转化数，需要在Google Ads后台导入首次打开(first-open)和应用内事件（如配置了回传应用内事件）。

为了可以导入相关转化，必须发布App并至少触发一次需回传的应用内事件。

#### 备注

- 导入转化的状态从“最近无转化”到改为“正在记录转化”可能需要6小时。

- 如果代理商是通过MCC账户管理账户，APP通过MCC中的多个子账户进行投放，那么所有子账户的CID都需要填到 Google Ads Customer ID 字段中（可查看上述截图）。
这种情况下，不需要填入MCC的CID。

代理商 步骤4: 追踪应用的转化

1. 回到Google Ads账户，点击工具(Tools)

2. 在衡量(Measurement)的内容下方，点击 转化(Conversions) .

3. 点击 + 图标.

4. 在转化类型中，选择 应用(App)

5. 选择 第三方应用分析工具(Third Party App Analytics) .

6. 点击继续

7. 选择所有App的首次打开(first_open)的复选框，选择需要导入的应用内事件。

8. 点击 导入并继续(Import and Continue)

9. 点击 完成 .然后可以在转化列表中看到第三方的转化事件。

点击事件名称，可查看更多详细信息。

恭喜您! 已经完成通过AppsFlyer配置追踪Google Ads时，代理商需要操作的相关步骤。

观看视频讲解"广告主配置追踪 Google Ads" 点击这里 .

#### 备注

- 点击归因窗口期默认30天，代理商可以编辑修改。

- 代理商可以从Google Ads获取花费数据: 在配置Google的页面中，点击数据扩展(Data Enrichment)，然后点击AdWords Cost, 用Google Ads账户登陆。

- 花费数据会同时显示在代理商AppsFlyer账户和广告主AppsFlyer账户的广告系列层级。
