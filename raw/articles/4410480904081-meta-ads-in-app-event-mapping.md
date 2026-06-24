---
source_url: https://support.appsflyer.com/hc/zh-cn/articles/4410480904081
ingested: 2026-06-24
sha256: 8ecbda12b9f6ff95b2b19b9e19a3fb7021a7bd4337c339c4430b3a86cba42a57
---

# Meta ads应用内事件映射

Source URL: https://support.appsflyer.com/hc/zh-cn/articles/4410480904081
Section: Meta ads
Updated: 2026-05-27T14:25:14Z

概要： 本文解释了如何将相关应用内事件从AppsFlyer发送到Meta ads。

## Meta应用内事件映射

广告主需要将SDK或S2S应用内事件映射到Meta侧的预定义事件。广告主还可以向Meta发送每个 应用打开 或 应用卸载 的回传。

广告主可以通过事件回传充分利用Meta的高级优化功能，并搭建自定义人群包和相似受众人群包。

### 预定义事件的映射

Meta ads提供 多种预定义事件 ，可直接用于映射。

详情请参考 此文档 ，其中列出了可用的Meta回传事件，您可以在这些事件中添加其他参数，传递更多信息，用于说明事件质量。

如需进一步了解Meta事件映射的具体操作，请参考 此文档 。

请注意：Meta ads没有预定义的卸载事件。如需发送卸载事件，请使用 自定义事件 进行配置。

除了上文超链接中列出的事件之外，Meta还提供不带额外参数的其他预定义事件，详见下表。

Meta事件标识符
说明

推荐的AppsFlyer SDK事件名称

Donate
为您的组织或公益事业提供的捐款

af_donate

Schedule
网点来访预约

af_schedule

SubmitApplication
针对您提供的某项产品、服务或项目（如信用卡、课程、职位等）提交申请

af_submit_application

FindLocation
用户通过网页或应用发现您的业务网点并计划来访，比如用户搜索某个产品后发现该产品在您的线下商店有售

af_find_location

Contact
用户通过SMS、邮件、聊天框或其他方式与贵司联系

af_contact

CustomizeProduct
通过配置工具或贵司的其他应用对产品进行自定义配置。

af_customize_product

### 自定义应用内事件的映射

在AppsFlyer平台中，您可以使用“CUSTOM”选项（自定义的Meta事件标识符）将自定义应用内事件映射到Meta。

AppsFlyer会将SDK中配置的事件名称和事件值（包括事件参数）按原样转发到Meta，并以其原始的AppsFlyer SDK事件名称呈现，不会显示为“custom”。

您可以 利用这些事件来优化您的广告投放 。

### 自定义事件的自动参数映射

基于AppsFlyer与Meta的深度对接，AppsFlyer的众多标准SDK事件参数可自动映射到Meta侧的预定义参数。比如 af_revenue 参数会转换为Meta中的 _valueToSum 参数，这样您就可以发送每个事件的收入，用于数据衡量和Meta中的投放优化。

#### 注意

CUSTOM（自定义）和预定义事件的自动参数映射有所不同。

若使用 预定义事件 ， _valueToSum 对应的参数有时是 af_price （例如 fb_mobile_add_to_cart ），有时是 af_revenue （例如 fb_mobile_purchase ）。

对于映射到CUSTOM的事件， af_price 总是映射到 fb_price ， af_revenue 总是映射到 _valueToSum 。

下表详细罗列了所有AppsFlyer事件的参数，这些参数通过CUSTOM事件映射到Meta时，会自动关联Meta侧对应的参数。

AppsFlyer参数 Meta侧参数

af_city fb_city

af_class fb_travel_class

af_content fb_content

af_content_id fb_content_id

af_content_list fb_content_id

af_content_type fb_content_type

af_country fb_country

af_currency fb_currency

af_date_a fb_checkin_date

af_date_b fb_checkout_date

af_departing_arrival_date fb_departing_arrival_date

af_departing_departure_date fb_departing_departure_date

af_description fb_description

af_destination_a fb_origin_airport

af_destination_b fb_destination_airport

af_destination_list fb_destination_ids

af_hotel_score fb_hotel_score

af_level fb_level

af_max_rating_value fb_max_rating_value

af_num_adults fb_num_adults

af_num_children fb_num_children

af_num_infants fb_num_infants

af_order_id fb_order_id

af_payment_info_available fb_payment_info_ available

af_preferred_neighborhoods fb_preferred_neighborhoods

af_preferred_num_stops fb_preferred_num_stops

af_preferred_price_range fb_preferred_price_range

af_preferred_star_ratings fb_preferred_star_ratings

af_price fb_price

af_quantity fb_num_items

af_region fb_region

af_registration_method fb_registration_method

af_returning_arrival_date fb_returning_arrival_ date

af_returning_departure_date fb_returning_departure_date

af_revenue _valueToSum

af_search_string fb_search_string

af_success fb_success

af_suggested_destinations fb_suggested_ destinations

af_suggested_hotels fb_suggested_hotels

af_travel_end fb_travel_end

af_travel_start fb_travel_start

af_user_score fb_user_score

## 事件和参数限制

您发送到Meta ads的事件 受到以下规则的限制：

- 不允许使用以下字符：
- 冒号（:）

- 句点（.）

- 非拉丁（英文）字母的字符集：自2020年1月12日起，Meta不再支持中文字符。AppsFlyer尚未测试其他字符集，因此您在使用其他字符集之前，请先确认Meta是否支持回传中出现这些字符。

- 事件名称区分大小写。为了避免数据差异，请确保所有媒体渠道和应用程序的各个版本中使用的事件名称（包括大小写）完全一致。

- 参数数量上限：25个。

- 事件和参数名称的长度限制：2–40个字符。

- 参数值长度上限：100个字符。

- af_content参数值的长度上限：1000个字符。

- 允许使用的字符：字母、数字、下划线、连字符和空格。请勿使用非拉丁（英文）字符。使用非拉丁字符会导致数据不一致。

为应用内事件命名时需要注意以下几点：

- 您可以使用 Meta 侧的事件名称来命名AppsFlyer中的事件（如fb_price），但这类事件不能作为CUSTOM事件发送给 Meta 。
为了避免回传映射问题，建议您不要使用 Meta 侧的事件名称来命名AppsFlyer事件。

- 如需将应用内事件回传映射到 Meta ，请向其发送所有渠道的事件数据，包括自然量。

#### 重要提示！

除上述参数外，AppsFlyer会将其他所有CUSTOM事件数据 按原样 发送到 Meta 。广告主须负责确保其事件数据符合 Meta 的要求，且使用 Meta 认可的有效参数（见上文表格），否则 Meta 不会接收事件数据。
