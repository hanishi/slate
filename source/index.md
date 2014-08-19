---
title: API Reference

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: false
---

# Kantan Shiharai Development Guide
## Kantan Shiharai Web API

### Credit Card
クレジットカード決済 APIの説明

### Web CVS
Webコンビニ決済 APIの説明

### Webhook
Webhookの説明

# Web CVS
## Checkout Request

# Webhook

## Checkout Response
```
決済要求の結果通知は、マーチャント様からご申請頂いたURLにPOSTリクエストを送信することで行われます。
```
> 決済要求が**成功**した場合には、XML形式のペイロードがPOSTリクエストによって送信されます。

```xml

<?xml version="1.0" encoding="UTF-8"?>                                      
<request>                                     
  <xml_info>                                      
    <version>1.0<version>                                     
    <operation_type>01</operation_type>                                     
  </xml_info>                                     
  <order_id>1312040000000001</order_id>                                     
  <order_time>2013-12-04T11:46:50+09:00</order_time>                                      
  <is_trial_order>false</is_trial_order>                                      
  <merch_id>MERCHID1</merch_id>                                     
  <merch_mgt_id>MERCHMGTID0000000001</merch_mgt_id>                                     
  <charge_status>OK</charge_status>                                     
  <buyer_billing_address>                                     
    <lastname>リクルート</lastname>                                      
    <firstname>太郎</firstname>                                     
    <lastname_kana>リクルート</lastname_kana>                                      
    <firstname_kana>タロウ</firstname_kana>                                      
    <email>email@recruit.co.jp</email>                                      
  </buyer_billing_address>                                      
  <items>                                     
    <item>                                      
      <item_name>商品A</item_name>                                      
      <item_qty>1</item_qty>                                      
      <item_unit_price>525</item_unit_price>                                      
      <item_include_tax>25</item_include_tax>                                     
      <item_point_num>15</item_point_num>                                     
    </item>                                     
    <item>                                      
      <item_name>商品B</item_name>                                      
      <item_qty>1</item_qty>                                      
      <item_unit_price>315</item_unit_price>                                      
      <item_include_tax>15</item_include_tax>                                     
      <item_point_num>9</item_point_num>                                      
    </item>                                     
  </items>                                      
  <ship_fee>0</ship_fee>                                      
  <price>                                     
    <subtotal_price>840</subtotal_price>                                      
    <total_price>840</total_price>                                      
  </price>                                      
  <device>2</device>                                      
  <timestamp>2013-12-04T11:46:50+09:00</timestamp>                                      
</request>                                      
```
> 決済要求に**失敗**した場合には、XML形式のペイロードがPOSTリクエストによって送信されます。

```xml
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Isis",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```
指定URLへのPOSTリクエストにより、Webコンビニの決済要求の結果を通知します。


### Content-Type

`application/xml`

### USER-AGENT
`KantanShiharai`

### XMLスキーマ　

SEQ | タグエレメント名 | 項目名 | 型 | 桁数 | 必須 | タイプ | 設定内容 | 備考
 -------------- | -------------- | -------------- | -------------- | -------------- | -------------- |  -------------- | -------------- | --------------
1|XML情報|xml_info|  |  |  |  |  | 
1-1|バージョン|version|半角文字|10|○|可変|XMLのバージョン情報|ｓｓｓｓ
1-2|通知種別|operation_type|半角文字|2|○|可変|01:WebCVS決済要求結果| 
2|注文番号|order_id|半角文字|16|○|固定|決済データを一意に管理するID|リクルート払い出しID ※購入時に払い出し決済データ特定するID
3|注文時刻|operation_type|半角文字|2|○|可変|01:WebCVS決済要求結果| 
3|注文時刻|operation_type|半角文字|2|○|可変|01:WebCVS決済要求結果| 

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import 'kittn'

api = Kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/3"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Isis",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the cat to retrieve

