---
title: API Reference

includes:
  - errors

search: false
---

# Kantan Shiharai Web CVS Development Guide
## Kantan Shiharai Web CVS API

API概要

# Request Checkout
>決済要求は、エンドポイントURLに対してapplication/x-www-form-urlencoded形式のデータをPOST送信することで行います。

```http
POST /demo/submit/ HTTP/1.1
Host: rouge.jayferd.us
Cache-Control: max-age=0
Origin: http://rouge.jayferd.us
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_2)
    AppleWebKit/535.7 (KHTML, like Gecko) Chrome/16.0.912.63 Safari/535.7
Content-Type: application/json
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Referer: http://pygments.org/
Accept-Encoding: gzip,deflate,sdch
Accept-Language: en-US,en;q=0.8
Accept-Charset: windows-949,utf-8;q=0.7,*;q=0
merch_id=M0000002&merch_mgt_id=TEST001&order_done_url=http%3A%2F%2Forder.done.url&error_done_url=http%3A%2F%2Ferror.done.url&customer_id=CAP980000023&item_id=G13123100006&item_price=200&merch_id=M0000002&merch_mgt_id=TEST001&order_done_url=http%3A%2F%2Forder.done.url&error_done_url=http%3A%2F%2Ferror.done.url&customer_id=CAP980000023&item_id=G13123100006&item_price=200
```

# Create Invoice

```http
POST /demo/submit/ HTTP/1.1
Host: rouge.jayferd.us
Cache-Control: max-age=0
Origin: http://rouge.jayferd.us
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_2)
    AppleWebKit/535.7 (KHTML, like Gecko) Chrome/16.0.912.63 Safari/535.7
Content-Type: application/json
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Referer: http://pygments.org/
Accept-Encoding: gzip,deflate,sdch
Accept-Language: en-US,en;q=0.8
Accept-Charset: windows-949,utf-8;q=0.7,*;q=0
merch_id=M0000002&merch_mgt_id=TEST001&order_done_url=http%3A%2F%2Forder.done.url&error_done_url=http%3A%2F%2Ferror.done.url&customer_id=CAP980000023&item_id=G13123100006&item_price=200&merch_id=M0000002&merch_mgt_id=TEST001&order_done_url=http%3A%2F%2Forder.done.url&error_done_url=http%3A%2F%2Ferror.done.url&customer_id=CAP980000023&item_id=G13123100006&item_price=200
```

# Invalidate Checkout

# Webhook

## Checkout Request Succeeded or Failed
```
Webコンビニを使った決済要求の結果通知は、マーチャント様からご申請頂いたURLにPOSTリクエストを送信することで行われます。
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
> 決済要求の結果通知に対して、XML形式のレスポンスを返します。

```xml
<?xml version="1.0" encoding="UTF-8"?>                    
<response>                    
  <is_successful>true</is_successful>                   
  <timestamp>2013-12-04T11:46:50+09:00</timestamp>                    
</response>
```
### リクエスト

指定URLへのPOSTリクエストにより、Webコンビニの決済要求の結果を通知します。

#### Content-Type

`application/xml`

#### USER-AGENT
`KantanShiharai`　

####　XML
`request`

プロパティ|概要|値|備考
--------------|--------------|--------------|--------------
**xml_info/**|XML情報||
version|バージョン|半角文字|XMLのバージョン情報<br>最大10桁
operation_type|オペレーションタイプ|10|半角数字
**order_id**| 決済データを一意に管理するID|半角英数|リクルート払い出しID<br>※購入時に払い出し決済データ特定するID<br>16桁
**order_time**|注文確定時間|半角文字|25桁<br>※ISO 8601/RFC3339表記 
**is_trial_order**|テスト注文フラグ|半角文字|true:テスト<br>false:本番
**merch_id**|リクルートより事前に払い出されたID|半角文字|8桁
**merch_mgt_id**|購入要求時に加盟店様より指定されたマーチャント管理ID|半角文字|最大256桁
**charge_status**|決済ステータス|半角文字|OK:処理正常<br>NG:処理異常
**buyer_billing_address/**|ご請求先情報||
lastname|名前（姓）||最大40桁
firstname|名前（名）||最大40桁
lastname_kana|名前カナ（セイ）||最大60桁
firstname_kana|名前カナ（メイ）||最大60桁
email|メールアドレス|半角文字|最大256桁
**items/**|商品リスト||
**item/**|商品情報||
item_name|商品名||最大512桁
item_qty|数量|半角数字|最大12桁
item_unit_price|単価（税込）|半角数字|最大13桁
item_include_tax|単価に含まれる税額|半角数字|最大13桁
item_point_num|数量１あたりの獲得ポイント|半角数字|最大13桁
**ship_fee**|送料|半角数字|最大13桁
**price/**|価格情報||
subtotal_price|商品合計（税込）|半角数字|最大13桁
total_price|合計（税込）|半角数字|最大13桁
**device**|使用されたデバイス|半角数字|1桁<br>0:PC<br>1:モバイル<br>2:スマートフォン
**timestamp**|リクエスト時刻|半角文字|25桁<br>※ISO 8601/RFC3339表記

### レスポンス
#### HTTP ステータスコード
`200`
####　XML
`response`

プロパティ|概要|値|備考
--------------|--------------|--------------|--------------
**is_successful**|リクエスト処理結果|半角文字|最大5桁
**timestamp**|レスポンス日時|半角文字|25桁<br>※ISO 8601/RFC3339表記

## New Invoice Notification

```xml
<?xml version="1.0" encoding="UTF-8"?>
<request>
  <xml_info>                                      
    <version>1.0<version>                                     
    <operation_type>10</operation_type>                                     
  </xml_info>
  <new_invoice_notification> 
    <uuid>ffc64d71d4b5404e93f13aac9c63b007</uuid>
    <merch_mgt_id>MERCHMGTID0000000001</merch_mgt_id>
    <buyer_billing_address>                                     
      <lastname>リクルート</lastname>                                      
      <firstname>太郎</firstname>                                     
      <lastname_kana>リクルート</lastname_kana>                                      
      <firstname_kana>タロウ</firstname_kana>                                      
      <email>email@recruit.co.jp</email>                                      
    </buyer_billing_address>
    <invoice> 
      <order_id type="string">1312040000000001</order_id>
      <state>open</state>
      <total>840</total>
      <closed_at type="datetime" nil="true"></closed_at>
      <store_chain_code type="integer">1</store_chain_code>
    </invoice>
    <date type="datetime">2014-10-1T11:46:50+09:00</date>
  </new_invoice_notification>
</request>
```

## Closed Invoice Notification

```xml
<?xml version="1.0" encoding="UTF-8"?>
<request>
  <xml_info>                                      
    <version>1.0<version>                                     
    <operation_type>10</operation_type>                                     
  </xml_info>
  <closed_invoice_notification>
    <uuid>ffc64d71d4b5404e93f13aac9c63b007</uuid>
    <merch_mgt_id>MERCHMGTID0000000001</merch_mgt_id>
    <buyer_billing_address>                                     
      <lastname>リクルート</lastname>                                      
      <firstname>太郎</firstname>                                     
      <lastname_kana>リクルート</lastname_kana>                                      
      <firstname_kana>タロウ</firstname_kana>                                      
      <email>email@recruit.co.jp</email>                                      
    </buyer_billing_address>
    <invoice> 
      <order_id type="string">1312040000000001</order_id>
      <state>collected</state>
      <total>840</total>
      <closed_at type="datetime">2014-10-2T11:46:50+09:00</closed_at>
      <store_chain_code type="integer">1</store_chain_code>
    </invoice>
    <date type="datetime">2014-10-1T11:46:50+09:00</date>
  </closed_invoice_notification>
</request>
```

## Overdue Invoice Notification

```xml
<?xml version="1.0" encoding="UTF-8"?>
<request>
  <xml_info>                                      
    <version>1.0<version>                                     
    <operation_type>10</operation_type>                                     
  </xml_info>
  <overdue_invoice_notification>
    <uuid>ffc64d71d4b5404e93f13aac9c63b007</uuid>
    <merch_mgt_id>MERCHMGTID0000000001</merch_mgt_id>
    <buyer_billing_address>                                     
      <lastname>リクルート</lastname>                                      
      <firstname>太郎</firstname>                                     
      <lastname_kana>リクルート</lastname_kana>                                      
      <firstname_kana>タロウ</firstname_kana>                                      
      <email>email@recruit.co.jp</email>                                      
    </buyer_billing_address>
    <invoice> 
      <order_id type="string">1312040000000001</order_id>
      <state>overdue</state>
      <total>840</total>
      <closed_at type="datetime">2014-10-2T11:46:50+09:00</closed_at>
      <store_chain_code type="integer">1</store_chain_code>
    </invoice>
    <date type="datetime">2014-10-1T11:46:50+09:00</date>
  </overdue_invoice_notification>
</request>
```



