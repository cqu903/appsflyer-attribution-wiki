---
source_url: https://support.appsflyer.com/hc/zh-cn/articles/115004970386
ingested: 2026-06-24
sha256: f4314165cbe1bf5e7fa78436cba65497fb119a7254db6bebff57b5ebe8889336
---

# 同时记录多个代理商/MCC的Google Ads帐户

Source URL: https://support.appsflyer.com/hc/zh-cn/articles/115004970386
Section: Google Ads
Updated: 2026-05-25T14:21:15Z

概要 ：本文说明了同时记录多个Google Ads账号的设置方式，以确保流量的正确归因。

## 简介

广告主的Google Ads流量通常会分多个账号输送，比如专营Google Ads的代理，或广告主公司内部的各个本地团队等等。这种情况下，您必须妥善设置不同Google Ads账号的数据记录，才能确保各方的正确归因。

本文将重点说明这类场景中的代理效果衡量、MCC使用方式以及多级MCC等内容。

#### 注意事项

以下说明 仅 适用于使用Google Ads新版API的客户。

如需详细了解Google Ads中的代理账号配置方式，请参见 此文档 。

## 重要概念释义

- Link ID – 您在Google Ads中设定相关应用后，Google Ads为其分配的唯一标识符 。

#### 注意事项

同一个应用的安卓和iOS版本需要配置不同的Link ID。

- Customer ID – Google Ads账号的唯一标识符 。
一个账号可以推广多个Link ID，比如为相关公司下的所有应用投放广告。将您已添加到AppsFlyer后台的应用绑定到代理账号时，最多可设置10个Customer ID。

- MCC - Google Ads上的经理账号（简称MCC，原名My Clients Center），用于在Google Ads平台中 处理多个Google Ads账号 。
设立MCC账号后，您可以绑定多个账号，以便统一查看（ 了解详情 ）。

## 设置Google Ads数据记录

AppsFlyer针对每个应用记录一个Link ID。 如果有多个账户处理同一个应用的投放，请确保这些账户都使用同一个Link ID。 您需要在AppsFlyer的面板上配置Link ID，用于归因。

### 与其他账户分享Google Link ID

建议仅具有一个Google Ads账号的广告主或计划通过代理投放Google Ads流量的广告主使用以下方法。

广告主可以与任何具有Customer ID的账号共享任何Link ID（如下文截图所示）。与代理共享Link ID的具体方法请见 此文档 。

#### 重要提示

- 如果相关MCC是其子账户的Recording Manager，则该MCC无需再与其子账户共享Link ID。但如果相关MCC下的某个子账户是其自身的Recording Manager，则该MCC必须与该Recording Manager子账户共享Link ID。

- 导入转化（Import Conversions）：如果相关MCC是Recording Manager，则该MCC需要为其下所有的子账户导入转化。但如果该MCC下的某个子账户是其自身的Recording Manager，则该子账户也需要完成导入转化操作。

#### 注意事项

- 在Google Ads面板中点击菜单图标（三点）>> Linked accounts >> Third-party app analytics details

- 对方账户需要同意“共享”。

- 操作完成后，对方账户就可获得授权，为相关应用投放Google Ads广告。

#### 提示

AppsFlyer建议广告主通过其主账户将相关的Link ID共享给其他账户，而不是在这些账户中直接生成Link ID。这种方式不仅最为快捷，而且在广告主和代理的合作结束后也更便于拆分。

## MCC

管理多个Google Ads账号的代理商或大型广告主一般会使用MCC（My Client Center）统一查看其下所有账户。

在设置MCC的过程中，可以选择让MCC或子账户来管理转化。

设置完毕后，仍可以根据实际需求进行更改。

## 多级MCC

与多个代理合作的大型广告主可能会通过一个MCC账户来管理多个MCC。这跟常规的MCC账户类似。这种情况中，建议由级别最高的MCC或广告主来生成Link ID。在这类结构中，子账户必须正确选择对应级别的MCC作为Recording Manager（一般是最高级别的MCC）。如果该结构设置无误，则无需再将Link ID共享给子账户，且只需通过级别最高的MCC导入转化即可。

#### 提示

如需进一步了解MCC以及账户层级的详细信息，请参考以下文档：

- 将帐号与经理帐号相关联

- 查看经理帐号层次结构

- 使用客户帐号

如果您对于账户结构和推荐设置有任何疑问，请咨询您的Google客户经理。

## 创建Google Ads广告系列

MCC账户无法直接创建Google Ads广告系列，必须由常规的Google Ads子账户创建。

您可以选择以下两种记录转化的方式：

- MCC管理子账户的数据记录
常见于同一个公司下分不同团队的场景，比如 一个公司下按地区分成多个Google Ads账号 。
MCC保有其所有子账户的数据记录配置权限（即Recording Manager）。数据记录配置只能在MCC层级进行更改，更改后的配置会对所有子账户自动生效。相关MCC还需要导入转化，该导入操作是一次性的，可覆盖所有的子账户，同时获取与子账户共享的Link ID。

- 子账户管理其自身的数据记录
常见于账户之间没有任何关联，但使用同一个服务商的场景，如 一家代理服务多个广告主账户。
这种情况中的导入转化必须分别在各个子账户中独立操作。AppsFlyer针对每个应用记录一个Link ID，因此为了确保移动数据的正常记录，MCC或广告主必须与相关子账户共享Link ID。

无论是激活还是应用内事件，您都必须在相关转化首次发生后方可在Google Ads中导入转化。
