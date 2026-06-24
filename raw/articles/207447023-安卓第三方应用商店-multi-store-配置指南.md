---
source_url: https://support.appsflyer.com/hc/zh-cn/articles/207447023
ingested: 2026-06-24
sha256: 7e284720443a860f0dd5e58bc5754033859e4a6432c66a7410bee06ba199f0c6
---

# 安卓第三方应用商店（multi-store）配置指南 

Source URL: https://support.appsflyer.com/hc/zh-cn/articles/207447023
Section: 归因场景
Updated: 2026-03-02T17:47:29Z

概览 ：针对应用上架多个安卓第三方应用商店的场景，设置归因方案。选择在 AppsFlyer单一应用面板下 查看多家安卓第三方应用商店的数据，或在 和商店对应的多个应用面板 下查看数据。

## 多个安卓第三方商店归因

- AppsFlyer的归因支持多家应用商店的场景。也就是说，无论您的应用上架Google Play商店还是其他第三方安卓商店，比如Amazon，Opera，GetJar，百度或华为，AppsFlyer都可提供对应的归因方案。（英文表述中，我们会将第三方安卓应用商店称为out-of-market stores或alternate Android stores）

- 广告主在AppsFlyer后台，可以选择（1）在单一应用面板下查看所有商店的数据，也可以选择（2）一个应用对应一个三方商店，多个应用下分别查看对应商店的数据。

- AppsFlyer的安卓归因解决方案全面支持各设备ID，包括GAID和 OAID 等。

- 如果您的投放主要针对中国国内安卓市场，配置方法请参考 中国国内市场上的Android归因最佳做法。

### 查看多个商店数据：单一应用面板 vs. 多个应用面板

对应解决方案

Single dashboard
[Best practice]
多个应用面板

描述
在单一应用面板下查看所有商店数据，如Google Play，Amazon，Huawei等等。
每个应用面板对应各自的商店。也就是说，App上架多少个商店，就可以在AppsFlyer后台添加多少个App。

安卓包名 单一应用需要物理包名一致；多个应用面板，物理包名通常需要一致，通过后缀channel区分。

channel名称 /
- 通过 Android Out-of-Store APK 入口添加App，并注意设置channel值。

- channel值可用作标识商店，如channel-amazon。

- 物理包名+ channel 值的组合，代表您在AppsFlyer后台显示的完整App包名，并对应各自的商店。

- 示例：物理包名为 com.abc.def ，channel值为xyz_device_store。AppsFlyer后台显示的包名即 com.abc.def-xyz_device_store。

- 如果APK Manifest中设置了channel值，但是AppsFlyer后台并没有配置该channel值的应用，那么该APK的归因数据将上报给原本无channel值的包名。如有上架Google Play, 且包名一致，那么数据就会上报给您Google Play对应的应用面板。

上报install_app_store 字段
- 各应用商店/下载渠道的唯一标示

- 如仅上架Google Play, 无需使用该字段。

- 支持manifest配置和API方法上报。

不适用

归因链接
- 归因链接相同。

- 确保用户被跳转至正确的商店，请使用 ＆af_r 参数设置重定向URL。(国内媒体如涉及异步监测，即跳转链接带有is_redirect=false参数的，可忽略af_r参数)

- 每个应用/商店对应各自的归因链接。

- 通过合作伙伴配置页面创建。

- The app ID is the channel name appended to the android package name. Ex: com.abc.def-def_store.
Hence the attribution links will be different.
.

可查看install_app_store的面板和报告
Cohort and raw data reports include the field. Reach out to your CSM to enable this field.
N/A

注意事项

- 归因准确性：不同商店的卸载重装根据客户的重归因窗口期内，不会重复记录；

- 自然激活：一个面板下显示所有商店/渠道APK包的自然激活

- 目前支持install_app_store的面板仅包含群组报告；各原始数据已经支持；

- 归因准确性：：因为包名不同，可能包含卸载重装。

- 在AppsFlyer的各个应用面板上分别查看 各渠道/商店包 的 自然 和 非自然 激活和应用内事件。

- 如需在一个面板下汇总所有商店数据，可以借助群组报告或自定义面板等工具实现。

## 设置方法

请参考本章节进行设置。具体的操作步骤需要由市场人员和开发人员共同配合完成。

针对 多个应用面板 选项，需要针对每个应用面板/商店重复步骤。

开始之前 ：

- 确定命名规则，方便后续给 channel 或 install_app_store 赋值。

- 可参考以下表格准备channel和install_app_store的命名。

- 表格主要方便开发人员后续准备APK打包。

命名规则映射表
参数
说明

Single dashboard
[Best practice]
多个应用面板

安卓包名 各商店/渠道包包名一致 如果APK包已经上架Google Play，可以直接选择使用该App面板查看多个商店数据。示例： comb.abc.def

channel名称 各个渠道/商店包的唯一名称 （命名由广告主自定义）
无需设置
每个APK包/渠道包对应一个channel名/渠道号。需要通过打包时在manifest配置，同时在添加App时填写完全一致的channel名，此处务必注意技术与运营配合一致。

install_app_store 各个渠道/商店包的唯一名称 （命名由广告主自定义） 可通过manifest配置；或者API的方式赋值（如渠道包数量较多，建议直接用API的方式）。 每个APK包/渠道包对应一个install_app_store/渠道号。 无需设置

步骤
操作方

单一面板
多个应用面板

1 开发人员 APK打包 APK打包

2
市场人员

如果面板已经有包名相同的Google Play App存在，且团队愿意在一个面板下同时查看Google Play包和第三方应用商店包的数据，则无需操作此处，直接使用原有面板进行配置。如果仍需单独添加新的应用面板，作为集合各APK包数据的单一面板，请参考文档：中国国内安卓市场归因指南
在AppsFlyer面板 添加应用 。

3 市场人员
准备归因链接。

分App(包名+channel名)准备归因链接。正常通过合作伙伴配置页面即可。

4 市场人员和研发人员互相配合
测试

测试

配置

### 程序

### 单一应用面板-APK打包

安卓包名决定了归因数据发往哪个应用面板。在单一应用面板的场景下，所有的商店/渠道包的包名是一致的。 此处无需再使用channel渠道号。 除去一种情况：即您在添加单一面板时，使用了out of store方式，此时仍需上报channel号确保包名一致。

SDK中的AF_STORE参数对应原始数据和上文中的install_app_store，即每个APK包的下载来源。

集成打包APK：

- 创建App build 副本。 注意 ：请勿更改安卓包名。

- 为不同APK包/商店包/渠道包名赋值：
- Manifest方法： 在AndroidManifest.xml中的<application>标记内添加以下代码。为每APK包/商店包/渠道包设置AF_STORE值。 < application > . . . < meta - data android : name = "AF_STORE" android : value = "enter_store_name_here" / > . . . < / application > --或者--

- API方法： 每个国内第三方应用商店分别准备一个单独的APK。调用setOutOfStore API以设置AF_STORE值。为每个商店设置唯一AF_STORE值。(注意：如果您使用的国内第三方应用商店较多，建议使用此方法)
AppsFlyerLib.getInstance().setOutOfStore("example_store")

AF_STORE对应AppsFlyer原始数据中的 install_app_store 字段。目前包含该字段的报告和API包括：

- 面板群组分析报告

- 原始数据报告 （原始数据报告是AppsFlyer高级功能）

### 单一应用面板-归因链接

- 前往 > 合作伙伴配置， 然后选择对应的媒体渠道。

- 在“ 归因链接” 标签页，设置“ out-of-store URL” 参数。该配置对应af_r参数，会直接填充至 af_r 中，以确保用户重定向到正确的落地页。例如， &af_r=http://www.destinationurl.com 默认URL在 App Settings 页面中设置。

- 注意配置链接中的 af_r 参数，以设定落地页地址。

- 设置其他需要的 归因链接参数 。

- 媒体渠道可使用 设备ID进行归因 ，同时AppsFlyer也支持 概率模型 作为后备方案，以应对设备ID缺失的场景。

- 建议在归因链接中使用一个或多个设备ID参数：
- android_id

- advertising_id

- oaid

- 复制归因链接，填写至广告平台。

### 多个应用面板-APK集成打包

此处完整包名为：物理包名，加后缀“-channel”，因此归因数据会显示在对应的完整包名下。

为每APK包/商店包/渠道包配置manifest:

- 在AndroidManifest.xml的<application>中添加以下代码为channel赋值。为每APK包/商店包/渠道包配置channel名/渠道号。 < application > . . . < meta - data android : name = "CHANNEL" android : value = "enter_store_name_here" / > . . . < / application > 注意： 参数区分大小写。

### 多个应用面板-添加应用

添加应用面板，对应物理包名和后缀“-channel”。示例：物理包名 com.myapp ，channel名配置为 abcstore， ，那么AppsFlyer面板显示的完整包名为 com.myapp-abcstore 。

在AppsFlyer后台，为每个商店添加多个面板 ：

- Go to, My apps , click Add app .
The Add your app window opens.

- 选择 第三方商店Android APK (Standalone, Amazon 等)

- 完成：
- Android物理包名： 在app package中显示的包名

- channel名： APK包/商店包/渠道包的唯一标识符，以区分具有相同物理包名的多个面板。请注意此处填写的channel名需要与manifest配置的channel名称完全一致，大小写敏感。

- App URL： 即 默认落地页地址，如此处配置了URL信息，则会在媒体配置归因链接中，自动填充在af_r 参数里。通常可设置为默认的APK下载地址或落地页。您无需立刻设置，也可以在后续配置归因链接时再添加。

- Click Save .
The app is created.

### 测试方法

#### 非自然安装

测试非自然激活：

- Use an Android device that does not have your app installed or register the device .

- 参考“ 自定义媒体配置” 生成测试归因链接。使用 test 作为媒体名称（“＆pid = test”）。

- 将设备ID（GAID，OAID，IMEI或Android ID）添加到点击URL。参数写法参考：AppsFlyer归因链接结构和参数 http://app.appsflyer.com/com.greatapp?pid=test ＆af_r = http：//www.destinationurl.com&advertising_id=b5a3-78d9b5-0f12345-xxxx 4. 通过电子邮件把该归因链接发送给自己，然后点击它。 跳转后, 无需担心跳转地址，也无需从商店安装 。请直接安装并打开，已集成了AppsFlyer SDK的APK即可。

单一面板
多个应用面板

- 在导出数据页面的原始数据报告里查看您测试的激活数据。

- 测试成功后，您会看到一条媒体信息（media source） 为test 的激活数据。在 Install App Store 栏，您会看到配置的AF_STORE数据。

- 如果是查看install debug日志，AF_STORE参数会显示在af_installstore字段下。

- 前往与完整包名对应的应用面板下。

- 在数据导出的原始数据或数据总览里查看您的激活测试数据。

- 您应该会看到来自“test”媒体渠道的一个安装转化。

如测试成功，您会看到：

#### 自然安装

测试自然激活：

- Use an Android device that does not have your app installed or that is registered .

- 安装并打开，已集成了AppsFlyer SDK的APK。

- 查看数据：

单一面板
多个应用面板

前往数据总览面板，查看是否有新增自然激活。(对应media source：自然)
- 进入已测试商店的应用控制面板上的数据总览页面。

- 您应该会看到来自“organic”媒体渠道的一个安装转化。

如测试成功，您会看到：

## 其他功能

### 从多个面板迁移至单一面板

如需从多个面板迁移到单一面板 ： 请参考单一面板的步骤指南直接打包新的APK即可。

### 从Facebook引导用户到Amazon应用商店

- 在Facebook应用设置页面下的 Android 部分 配置跳转链接 。

- 以应用管理员的身份登录到Facebook，前往 https://developers.facebook.com/apps/ 并选择相应应用。

- 进入设置页面找到您的Android设置，如果您还没有配置Android的话，先添加该平台。

- 填写所有内容，包括该应用的amazon应用商店URL。

- 在AppsFlyer控制面板的已对接合作伙伴里选择 Facebook, 并输入与记录Facebook店内移动应用安装时相同的Facebook 应用ID。

- 在Facebook设置Advert Sets时，选择 “Amazon Appstore”。

注意： 该屏幕快照取自Facebook Power Editor，在FMP平台中可能会有所不同。

### 查看数据-AppsFlyer报告和数据接口

您可以通过以下方法查看获取数据。

- 群组报告：
- 在一个报表中集合多个面板/应用的数据。

- 以 install_app_store 作为分组维度，查看各个应用面板的数据。

- Pull API（适合查看单一面板的install app store数据）：后台显示的 Pull API 默认链接中不包含 Install App Store 。请单独添加以下参数： &additional_fields=install_app_store ，即可使用Pull API获取该字段。

- 自定义面板（适合集中查看多个面板）：可通过自定义面板选择多个应用，从而建立一个统一的自定义面板，直接查看各个应用商店/APK包的数据。

### 部分第三方商店支持Referrer对接

- 截止2022年9月份，支持referrer的商店包括Google Play、华为应用商店、三星应用商店和小米GetApps商店。

- 请使用Android SDK V5.4或更高版本，以启用第三方应用商店（非Google Play的三方商店）的referrer归因除此之外，无需进行其他设置。

- 通过第三方应用商店referrer归因的数据在原始数据中呈现为：
- match type: 对应的第三方应用商店名称例如，huawei_referrer

- 某些情况下，Google Play可能会以助攻的形式参与了下载激活，但不会被归因。这部分数据会显示在助攻字段中。同理，第三方应用商店也可能助攻Google Play。

- 第三方应用商店的referrer具体信息目前还不会显示在原始数据中。

### 疑难解答

### 激活归因给默认的应用

如果您在APK manifest中配置了channel值，但没有建立对应的应用面板。该APK的数据会显示在默认的Google Play App面板中。如果没有建立默认的Google Play App，则数据无法被记录。
