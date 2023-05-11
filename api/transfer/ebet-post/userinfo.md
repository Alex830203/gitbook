---
description: 用于确认用户信息。 在RegisterOrLoginReq响应成功后，它将发送请求。
---

# UserInfo

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>cmd</td><td><mark style="color:blue;">string</mark></td><td>API 名称。</td><td>RegisterOrLoginReq</td></tr><tr><td>money</td><td><mark style="color:blue;">number</mark></td><td>用户当前金额。</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。</td><td>apitest01</td></tr><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td>1</td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">number</mark></td><td>子渠道 ID。 </td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>当前时间，格式为Unix。</td><td>1577808000</td></tr><tr><td>userId</td><td><mark style="color:blue;">number</mark></td><td>用户 ID。</td><td></td></tr><tr><td>ip</td><td><mark style="color:blue;">string</mark></td><td>用户登录IP。</td><td>127.0.0.1</td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td>签名。 字符串拼接: username+timestamp</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
  "cmd": "UserInfo",
  "money": 1000.01,
  "username": "demo",
  "channelId": 1,
  "subChannelId": 0,
  "timestamp": 1577808000,
  "userId": 123456789,
  "ip": "127.0.0.1",
  "signature": "bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ=="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td><a href="../../ebet-zhuang-tai-ma.md#jian-yi-xiang-ying-de-zhuang-tai-dai-ma">建议返回的状态码</a></td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr></tbody></table>

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
  "status": 200
}
```
{% endcode %}

{% hint style="info" %}
<mark style="color:blue;">响应失败不会影响玩家登录</mark>
{% endhint %}
