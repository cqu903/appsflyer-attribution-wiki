---
source_url: https://support.appsflyer.com/hc/zh-cn/articles/4408847686161
ingested: 2026-06-24
sha256: a9b8d2a30f6417f88d22543074f6c41fda9aa7655447388e71aab4c601dc3c4a
---

# 设备标识符

Source URL: https://support.appsflyer.com/hc/zh-cn/articles/4408847686161
Section: 归因概念
Updated: 2026-04-26T16:53:31Z

概要 ：本文主要说明了AppsFlyer SDK中支持的设备标识符。

## 简介

AppsFlyer SDK会收集设备标识符， 用于归因 。这些标识符能帮助您构建用户链路，并了解用户的行为习惯。

该SDK会自动收集AppsFlyer ID和Google Advertising ID等标识符。您也可以根据实际需求为相关应用收集其他的标识符（如针对在中国市场投放的应用，收集第三方安卓应用商店的标识符）。

## 适用于所有平台的设备标识符

AppsFlyer SDK支持以下全平台设备标识符：

设备标识符 用途

AppsFlyer ID
AppsFlyer ID会在每次发生应用激活时自动生成。您可以使用该标识符来完成下列事项：
- 发送 S2S应用内事件 。

- 将AppsFlyer ID与您后台的用户记录进行匹配。

- 合并Pull API和Push API的数据时进行映射。

Customer User ID（客户用户ID）

客户用户ID（CUID） 字段是由应用所有者或网站所有者设定的一种唯一标识符。 在AppsFlyer SDK中设置CUID后，您就可以在CUID、AppsFlyer ID和其他ID（如设备ID等）之间进行交叉索引。您可以在AppsFlyer的原始数据报告中查看CUID，还能在回传API中使用该ID与您的内部ID进行对照。

## 安卓设备标识符

AppsFlyer SDK支持以下安卓设备标识符：

#### 对于在Google Play中上架的应用

设备标识符 用途

GAID

一种 可由用户重置 的标识符，适用于Google Play安卓用户。

从SDK V4.8.0开始，AppsFlyer会自动收集这个设备标识符。

#### 对于在第三方应用商店上架的应用

设备标识符 用途

Amazon Advertising ID

Amazon Fire TV使用的一种唯一标识符， 可由用户重置 。详情请见 CTV简介 。

OAID

部分第三方安卓应用商店使用的一种唯一标识符， 可由用户重置 。详情请见 OAID使用指南 。

IMEI

一种 不可重置 的移动设备唯一标识符，适用于不支持Google Play的市场。AppsFlyer SDK不会自动收集IMEI。但如果您需要收集该标识符，可以让您的开发人员配置相关的信息收集功能。

备注：

- 安卓10及以上版本会限制IMEI的读取权限。

- IMEI不能与GAID同时使用。

Android ID

一种 不可重置 的移动设备唯一标识符，适用于第三方应用商店。AppsFlyer SDK不会自动收集Android ID。但如果您需要收集该标识符，可以让您的开发人员配置相关的信息收集功能。

请注意 ：Android ID 不能与GAID同时使用。

## Apple设备标识符

AppsFlyer SDK支持以下iOS设备标识符：

设备标识符 用途

IDFA
用于Apple iOS或tvOS（Apple TV）用户的一种唯一标识符， 可由用户重置 。iOS 14.5及以上版本中，用户必须在 ATT弹窗 中选择同意授权，SDK才能读取到其设备的IDFA。

IDFV

同一家厂商 的所有应用在同一台设备上都具有相同的IDFV。用户激活某厂商的首个应用后，系统会给该应用分配一个IDFV，之后再激活该厂商的其他应用时，这些应用也会得到相同的IDFV。其他厂商的应用则会分配到不同的IDFV。

此外，如果用户将某个厂商的所有应用全部从其设备中删除，则相应的IDFV也会被一并删除。之后，如果用户再次激活该厂商的应用，系统会为其分配一个新的IDFV。

## CTV设备标识符

AppsFlyer SDK支持以下CTV设备标识符：

设备标识符 用途

RIDA
适用于Roku CTV设备。详情请见 CTV概览 。

VIDA
适用于Vizio CTV设备。详情请见 CTV概览 。

TIFA
适用于三星CTV设备。详情请见 CTV概览 。

LGUDID
适用于LG CTV设备。详情请见 CTV概览 。
