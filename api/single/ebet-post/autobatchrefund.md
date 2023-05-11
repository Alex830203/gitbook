---
description: 自动对一段时间内的投注失败纪录进行退款通知。
---

# autoBatchRefund

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td></td></tr><tr><td>lastStartProcessTime</td><td><mark style="color:blue;">number</mark></td><td>批次处理时间(毫秒)。 格式为Unix。</td><td></td></tr><tr><td>refundThreshold</td><td><mark style="color:blue;">number</mark></td><td>退款金额的上限值。</td><td></td></tr><tr><td>sessionToken</td><td><mark style="color:blue;">string</mark></td><td>sessionToken。由渠道提供或随机生成。</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td>batchRefundList</td><td><mark style="color:blue;">array</mark></td><td>退款清单。</td><td></td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td></td></tr><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API 名称。</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>时间戳记，以毫秒为单位。</td><td></td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td>签名。 字符串拼接: username+timestamp</td><td></td></tr></tbody></table>

#### batchRefundList

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>退款投注序列号。</td><td>RegisterOrLoginReq</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号。</td><td></td></tr><tr><td>refundMoney</td><td><mark style="color:blue;">number</mark></td><td>退款金额。 该值为正。</td><td></td></tr><tr><td>detail</td><td><mark style="color:blue;">array</mark></td><td>明細。</td><td></td></tr></tbody></table>

#### detail

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID。</td><td>RegisterOrLoginReq</td></tr><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型。</td><td></td></tr><tr><td>money</td><td><mark style="color:blue;">number</mark></td><td>投注金额。</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "lastStartProcessTime": 1683785711005,
    "refundThreshold": 9999999999,
    "sessionToken": "02cfc9f249180b16e93dbbeb8c1c394d",
    "seqNo": "ee41edc558292f232e992cd011fec3f2",
    "batchRefundList": [
        {
            "seqNo": "d34fbd4e4734d430c05f443da281d92b",
            "username": "demo",
            "roundCode": "BP1-230511141338",
            "refundMoney": 20,
            "detail": [
                {
                    "betId": "d34fbd4e4734d430c05f443da281d92b-80",
                    "betType": 80,
                    "money": 1000
                }
            ]
        }
    ],
    "currency": "CNY",
    "event": "autoBatchRefund",
    "timestamp": 1683786010043,
    "signature": "lXcqxYko5D5bMwjB6YZLr9f49dKeYlNCBWbiLtTadAt+C+T+NFolmCwcbbdSmlSnbaB/NbechDXZURRB0qvXIA=="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">seqNo</mark></td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td><mark style="color:red;">event</mark></td><td><mark style="color:blue;">string</mark></td><td>API 名称。</td><td></td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>时间戳记，以毫秒为单位。</td><td></td></tr><tr><td><mark style="color:red;">status</mark></td><td><mark style="color:blue;">number</mark></td><td><a href="../../ebet-zhuang-tai-ma.md#jian-yi-xiang-ying-de-zhuang-tai-dai-ma">建议返回的状态码</a></td><td></td></tr><tr><td>refundResultList</td><td><mark style="color:blue;">array</mark></td><td>退款处理列表。</td><td></td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

#### refundResultList

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号。</td><td></td></tr><tr><td>refundTotalMoney</td><td><mark style="color:blue;">number</mark></td><td>成功处理的退款总金额</td><td></td></tr><tr><td>sucRefundSeqNoList</td><td><mark style="color:blue;">array</mark></td><td>成功进行投注退款处理的处理列表。 <br>如果所有处理失败，请返回空数组。</td><td></td></tr></tbody></table>

#### sucRefundSeqNoList

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>refundSeqNo</td><td><mark style="color:blue;">string</mark></td><td>退款的投注SeqNo。</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>退款处理的状态。<br><mark style="color:purple;"><code>200</code></mark>:建议返回的状态码<br><mark style="color:purple;"><code>209</code></mark>:渠道已自行退款</td><td></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "seqNo": "ee41edc558292f232e992cd011fec3f2",
    "event": "autoBatchRefund",
    "timestamp": 1683786010428,
    "status": 200,
    "refundResultList": [
        {
            "username": "demo",
            "roundCode": "BP1-230511141338",
            "refundTotalMoney": 1000,
            "sucRefundSeqNoList": [
                {
                    "seqNo": "d34fbd4e4734d430c05f443da281d92b",
                    "status": 200
                }
            ]
        }
    ]
}
```
{% endcode %}
