---
description: 确认用户当前额度
---

# ​syncCredit

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="150">参数</th><th width="126">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td>RegisterOrLoginReq</td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型。</td><td>1</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td></td></tr><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API 名称。</td><td>127.0.0.1</td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>当前时间，格式为Unix。</td><td>1577808000</td></tr><tr><td>sessionToken</td><td><mark style="color:blue;">string</mark></td><td>sessionToken。由渠道提供或随机生成。</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
    "tableType": -1,
    "currency": "CNY",
    "event": "syncCredit",
    "timestamp": 1683783025533,
    "sessionToken": "d9e1f52fc216e82879780594815a0079",
    "seqNo": "5b36c344d64efdcb74270408fb9a9c15"
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="164">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td></td></tr><tr><td><mark style="color:red;">money</mark></td><td><mark style="color:blue;">number</mark></td><td>用户的金額。</td><td></td></tr><tr><td><mark style="color:red;">status</mark></td><td><mark style="color:blue;">number</mark></td><td><a href="../../ebet-zhuang-tai-ma.md#jian-yi-xiang-ying-de-zhuang-tai-dai-ma">建议返回的状态码</a></td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td><mark style="color:red;">event</mark></td><td><mark style="color:blue;">string</mark></td><td>API 名称。</td><td></td></tr><tr><td><mark style="color:red;">seqNo</mark></td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>时间戳记，以毫秒为单位。</td><td></td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td></td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Responses" overflow="wrap" %}
```json
{
    "userName": "demo",
    "money": 1234567.89,
    "status": 200,
    "event": "syncCredit",
    "seqNo": "5b36c344d64efdcb74270408fb9a9c15"
}
```
{% endcode %}
