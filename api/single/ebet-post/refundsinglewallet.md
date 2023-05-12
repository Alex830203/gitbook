---
description: 对单次投注失败纪录手动进行退款通知
---

# refundSingleWallet

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td>RegisterOrLoginReq</td></tr><tr><td>refundList</td><td><mark style="color:blue;">array</mark></td><td>退款明细。</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号。</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td></td></tr><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API 名称。</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>时间戳记,以毫秒为单位。</td><td></td></tr><tr><td>sessionToken</td><td><mark style="color:blue;">string</mark></td><td>由渠道提供或随机生成。</td><td></td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td>签名。 字符串拼接: username+timestamp</td><td></td></tr></tbody></table>

#### refundList

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>refundSeqNo</td><td><mark style="color:blue;">string</mark></td><td>退款投注序列号。</td><td>RegisterOrLoginReq</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号。</td><td></td></tr><tr><td>refundMoney</td><td><mark style="color:blue;">number</mark></td><td>退款金额。 该值为负。</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
  "channelId": 1,
  "username": "demo",
  "refundList": [
    {
      "refundSeqNo": "a70efc7cf71e03ae98b42b22ad4b4288",
      "username": "demo",
      "roundCode": "BP1-230511075749",
      "refundMoney": -1000
    }
  ],
  "roundCode": "BP1-230511075749",
  "seqNo": "2941835af7855702a90d41fad87a36bf",
  "currency": "CNY",
  "event": "refundSingleWallet",
  "timestamp": 1683765142822,
  "sessionToken": "E5E10A9576D935C8BA987CBBE1F0C01FC76495E0",
  "signature": "dfJ5eTIBajxUIjR34YXIBS02nmj+UBHjDC5XOFC26FE88g5m1NazxJ7xEGy2WfiJX2Ni+2LydgxtZJz7TTQ8sQ=="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">status</mark></td><td><mark style="color:blue;">number</mark></td><td><a href="../../ebet-zhuang-tai-ma.md#jian-yi-xiang-ying-de-zhuang-tai-dai-ma">建议返回的状态码</a></td><td></td></tr><tr><td><mark style="color:red;">seqNo</mark></td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td><mark style="color:red;">event</mark></td><td><mark style="color:blue;">string</mark></td><td>API 名称。</td><td></td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>时间戳记，以毫秒为单位。</td><td></td></tr><tr><td>moneyBefore</td><td><mark style="color:blue;">number</mark></td><td>退款前金额。</td><td></td></tr><tr><td>moneyAfter</td><td><mark style="color:blue;">number</mark></td><td>退款後金额。</td><td></td></tr><tr><td>refundMoney</td><td><mark style="color:blue;">number</mark></td><td>退款总金额。</td><td></td></tr><tr><td>resultList</td><td><mark style="color:blue;">array</mark></td><td>退款处理结果。</td><td></td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

#### resultList:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>refundSeqNo</td><td><mark style="color:blue;">string</mark></td><td>退款的投注SeqNo。</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>退款处理的状态。<br><mark style="color:purple;"><code>200</code></mark>:建议返回的状态码<br><mark style="color:purple;"><code>209</code></mark>:渠道已自行退款</td><td></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "seqNo": "2941835af7855702a90d41fad87a36bf",
    "event": "refundSingleWallet",
    "timestamp": 1683765084669,
    "username": "demo",
    "status": 200,
    "moneyBefore": 1234567.89,
    "moneyAfter": 1235567.89,
    "refundMoney": 1000,
    "resultList": [
        {
            "refundSeqNo": "a70efc7cf71e03ae98b42b22ad4b4288",
            "status": 200
        }
    ]
}
```
{% endcode %}
