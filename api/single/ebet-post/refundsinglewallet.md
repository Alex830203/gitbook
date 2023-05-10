---
description: 此API是eBET对失败投注進行手动退款请求。
---

# refundSingleWallet\*

* 范例链接：[请求&回应范例](https://github.com/ITsupporteBET/demo\_code/tree/master/API%20for%20single%20wallet/refundSingleWallet)

{% hint style="info" %}
<mark style="color:blue;">发送请求至接收地址是渠道的服务器url + api E.g. http://127.0.0.1/refundSingleWallet</mark>
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td>RegisterOrLoginReq</td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>时间戳记,以毫秒为单位。</td><td></td></tr><tr><td>sessionToken</td><td><mark style="color:blue;">string</mark></td><td>由渠道提供或随机生成</td><td></td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币</td><td></td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td>签名。 字符串拼接: username+timestamp</td><td></td></tr><tr><td>refundList</td><td><mark style="color:orange;">array</mark></td><td>退款明细</td><td></td></tr></tbody></table>

#### refundList:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>refundSeqNo</td><td><mark style="color:blue;">string</mark></td><td>退款投注序列号</td><td>RegisterOrLoginReq</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>refundMoney</td><td><mark style="color:blue;">number</mark></td><td>退款金额。 该值为负</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" %}
```json
{
  "channelId": 1,
  "username": "apitest01",
  "roundCode": "B1-200101012345",
  "seqNo": "seqNoseqNoseqNoseqNo",
  "event": "refundSingleWallet",
  "timestamp": 1577808000000,
  "sessionToken": "sessionToken",
  "currency": "CNY",
  "signature": "bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==",
  "refundList": [
    {
      "refundSeqNo": "seqNoBetseqNoRefund",
      "username": "apitest01",
      "roundCode": "B1-200101012345",
      "refundMoney": -1000
    }
  ]
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

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">status</mark></td><td><mark style="color:blue;">number</mark></td><td><a href="../../ebet-zhuang-tai-ma.md#jian-yi-xiang-ying-de-zhuang-tai-dai-ma">建议返回的状态码</a></td><td></td></tr><tr><td><mark style="color:red;">seqNo</mark></td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td><mark style="color:red;">event</mark></td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td></td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>时间戳记,以毫秒为单位。</td><td></td></tr><tr><td>moneyBefore</td><td><mark style="color:blue;">number</mark></td><td>退款前的总金额</td><td></td></tr><tr><td>moneyAfter</td><td><mark style="color:blue;">number</mark></td><td>退款後的总金额</td><td></td></tr><tr><td>refundMoney</td><td><mark style="color:blue;">number</mark></td><td>需要退款的金额</td><td></td></tr><tr><td>resultList</td><td><mark style="color:orange;">array</mark></td><td>退款处理结果。</td><td></td></tr></tbody></table>

#### resultList:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>refundSeqNo</td><td><mark style="color:blue;">string</mark></td><td>退款的投注SeqNo</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>退款处理的状态。<br><mark style="color:purple;"><code>200</code></mark>:建议返回的状态码<br><mark style="color:purple;"><code>209</code></mark>:渠道已自行退款</td><td></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" %}
```json
{
  "status": 200,
  "seqNo": "seqNoseqNoseqNoseqNo",
  "event": "refundSingleWallet",
  "timestamp": 1577808000000,
  "moneyBefore": 0,
  "moneyAfter": 1000,
  "refundMoney": 1000,
  "resultList": [
    {
      "refundSeqNo": "seqNoBetseqNoRefund",
      "status": 200
    }
  ]
}
```
{% endcode %}
