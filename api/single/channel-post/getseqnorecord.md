---
description: 此api为取得ebet纪录为失败的序列编号。
---

# getseqnorecord

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道 ID</td><td>1</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>当前时间,格式为Unix。</td><td>1577808000</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。 字串拼接：字串拼接：username+channelId+timestamp</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。 不可使用http保留字元。</td><td></td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">number</mark></td><td>子渠道ID。</td><td></td></tr><tr><td>startTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的开始。</td><td></td></tr><tr><td>endTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的结束。</td><td></td></tr><tr><td>pageNum</td><td><mark style="color:blue;">number</mark></td><td>页码。 默认值为1。</td><td></td></tr><tr><td>pageSize</td><td><mark style="color:blue;">number</mark></td><td>每页上显示的记录数。 默认值为10。最大为5000。</td><td></td></tr><tr><td>withNo200</td><td><mark style="color:blue;">boolean</mark></td><td>获取成功记录。 默认为false。</td><td></td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td></td></tr></tbody></table>

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
  "channelId": 1,
  "timestamp": 1577808000000,
  "signature": "dry4mQ5qb7hyAeDDi1Ia+m5fsouP+qf2xfcpb+nP+La5yEMbYuHRz7Fge2OTgVi7DttC8p+Aiedfnnu42ii2lQ==",
  "username": "apitest01",
  "subChannelId": 0,
  "startTimeStr": "2020-01-01 00:00:00",
  "endTimeStr": "2020-01-02 00:00:00",
  "pageNum": 1,
  "pageSize": 10,
  "withNo200": false,
  "currency": "CNY"
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td>1</td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td>1577808000</td></tr><tr><td>count</td><td><mark style="color:blue;">number</mark></td><td>总数。</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>remainingVisit</td><td><mark style="color:blue;">number</mark></td><td>剩余请求数，每分钟500次。</td><td></td></tr><tr><td>seqNoHistorys</td><td><mark style="color:blue;">array</mark></td><td>每个钱包的余额。阵列值为物件，下表为物件参数说明。</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>记录序列号</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。 不可使用http保留字元。</td><td></td></tr><tr><td>startRequestTime</td><td><mark style="color:blue;">string</mark></td><td>请求发送时间</td><td></td></tr><tr><td>endResponseTime</td><td><mark style="color:blue;">string</mark></td><td>响应结束时间</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>纪录的状态码</td><td></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" %}
```json
{
  "status": 200,
  "apiVersion": "1.3.55",
  "count": 1,
  "remainingVisit": 200,
  "seqNoHistorys": [
    {
      "seqNo": "a698facaf47c80b784e116524c20bbf1",
      "username": "apitest01",
      "event": "increaseCredit",
      "startRequestTime": "2020-01-01T00:00:00Z",
      "endResponseTime": "2020-01-01T00:00:10Z",
      "status": 4025
    }
  ]
}
```
{% endcode %}
