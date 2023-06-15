---
description: 查询seqNo的状态纪录
---

# getseqnorecord

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="169">参数</th><th width="119">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道 ID</td><td>1</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>当前时间,格式为Unix。</td><td>1577808000</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。 字串拼接：字串拼接：username+channelId+timestamp</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td></td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">number</mark></td><td>子渠道ID。</td><td></td></tr><tr><td>startTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的开始。</td><td></td></tr><tr><td>endTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的结束。</td><td></td></tr><tr><td>pageNum</td><td><mark style="color:blue;">number</mark></td><td>页码。 默认值为1。</td><td></td></tr><tr><td>pageSize</td><td><mark style="color:blue;">number</mark></td><td>每页上显示的记录数。 默认值为10。最大为5000。</td><td></td></tr><tr><td>withNo200</td><td><mark style="color:blue;">boolean</mark></td><td>仅获取成功记录。 默认为false。</td><td></td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td></td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% hint style="info" %}
<mark style="color:blue;">由于数据量可能太大，建议带以下参数减少查询时间。</mark>

<mark style="color:blue;">(startTimeStr, endTimeStr, pageNum, pageSize)</mark>
{% endhint %}

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
    "timestamp": 1686792728,
    "pageNum": 1,
    "pageSize": 5000,
    "startTimeStr": "2023-06-07 00:00:00",
    "endTimeStr": "2023-06-08 00:00:00",
    "signature": "l7mlGNk3oK+re09laUj/2Jw4nIpLuN1fMHICNMDsLECUNSJP6pjm6u+EtJdHudhM5bOvv/R+i8TE0IP4rGWBRw=="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="191">参数</th><th width="150">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>count</td><td><mark style="color:blue;">number</mark></td><td>总数。</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>remainingVisit</td><td><mark style="color:blue;">number</mark></td><td>剩余请求数，每分钟500次。</td><td></td></tr><tr><td>seqNoHistorys</td><td><mark style="color:blue;">array</mark></td><td>每个钱包的余额。阵列值为物件，下表为物件参数说明。</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td>1</td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td>1577808000</td></tr></tbody></table>

#### seqNoHistorys:

<table><thead><tr><th width="191">参数</th><th width="111">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>记录序列号</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td></td></tr><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API 名称。</td><td></td></tr><tr><td>startRequestTime</td><td><mark style="color:blue;">string</mark></td><td>请求发送时间</td><td></td></tr><tr><td>endResponseTime</td><td><mark style="color:blue;">string</mark></td><td>响应结束时间</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>纪录的状态码</td><td></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "count": 1,
    "remainingVisit": 499,
    "seqNoHistorys": [
        {
            "seqNo": "9f8a871250f81ba5c3708961ac34022f",
            "username": "qatest004",
            "event": "increaseCredit",
            "startRequestTime": "2023-06-06T22:43:15.682Z",
            "endResponseTime": "2023-06-06T22:43:16.053Z",
            "status": 200
        }
    ],
    "status": 200,
    "apiVersion": "1.6.3"
}
```
{% endcode %}
