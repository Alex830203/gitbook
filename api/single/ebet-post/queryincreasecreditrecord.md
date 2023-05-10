---
description: 该API用于查询渠道数据库中的increaseCredit的处理状态。
---

# queryIncreaseCreditRecord\*

* 范例链接：[请求&回应范例](https://github.com/ITsupporteBET/demo\_code/tree/master/API%20for%20single%20wallet/queryIncreaseCreditRecord)

{% hint style="info" %}
<mark style="color:blue;">发送请求至接收地址是渠道的服务器url + api E.g. http://127.0.0.1/queryIncreaseCreditRecord</mark>
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td>RegisterOrLoginReq</td></tr><tr><td>querySeqNo</td><td><mark style="color:blue;">string</mark></td><td>要查询的序列号，以逗号分隔。</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>时间戳记,以毫秒为单位。</td><td></td></tr><tr><td>sessionToken</td><td><mark style="color:blue;">string</mark></td><td>由渠道提供或随机生成</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td>签名。 字符串拼接: username+timestamp</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" %}
```json
{
  "channelId": 1,
  "username": "apitest01",
  "querySeqNo": "seqNoBetseqNoBet,seqNoPayoutseqNoPayout",
  "roundCode": "B1-200101012345",
  "event": "queryIncreaseCreditRecord",
  "timestamp": 1577808000000,
  "sessionToken": "sessionToken",
  "seqNo": "seqNoseqNoseqNoseqNo",
  "signature": "bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ=="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">seqNo</mark></td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td><mark style="color:red;">event</mark></td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>时间戳记,以毫秒为单位。</td><td></td></tr><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td></td></tr><tr><td>creditRecord</td><td><mark style="color:orange;">array</mark></td><td>渠道数据库的纪录，返回空序列意味着没有记录</td><td></td></tr><tr><td><mark style="color:red;">status</mark></td><td><mark style="color:blue;">number</mark></td><td><a href="../../ebet-zhuang-tai-ma.md#jian-yi-xiang-ying-de-zhuang-tai-dai-ma">建议返回的状态码</a></td><td></td></tr></tbody></table>

#### creditRecord:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>querySeqNo</td><td><mark style="color:blue;">string</mark></td><td>要查询的序列号，以逗号分隔。</td><td></td></tr><tr><td>type</td><td><mark style="color:blue;">number</mark></td><td>交易事务类型</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>该seqNo的处理状态，<a href="../../ebet-zhuang-tai-ma.md#jian-yi-xiang-ying-de-zhuang-tai-dai-ma">建议返回的状态码</a></td><td></td></tr><tr><td>creditTime</td><td><mark style="color:blue;">number</mark></td><td>事务纪录处理成功时间(毫秒)。时间格式为Unix。</td><td></td></tr><tr><td>moneyBefore</td><td><mark style="color:blue;">number</mark></td><td>变动前金额</td><td></td></tr><tr><td>moneyAfter</td><td><mark style="color:blue;">number</mark></td><td>变动金额</td><td></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" %}
```json
{
  "seqNo": "seqNoseqNoseqNoseqNo",
  "event": "queryIncreaseCreditRecord",
  "timestamp": 1577808000000,
  "username": "apitest01",
  "creditRecord": [
    {
      "querySeqNo": "seqNoBetseqNoBet",
      "type": 1,
      "username": "apitest01",
      "roundCode": "B1-200101012345",
      "status": 200,
      "creditTime": 1577808000000,
      "moneyBefore": 1100.01,
      "moneyAfter": 1000.01,
      "money": -100
    }
  ],
  "status": 200
}
```
{% endcode %}
