---
description: 此api用于确认用户信息。 在RegisterOrLoginReq响应成功后，它将发送请求。 响应失败不会影响玩家登录
---

# UserInfo

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>cmd</td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td>RegisterOrLoginReq</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td>apitest01</td></tr><tr><td>channelId</td><td><mark style="color:blue;">integer</mark></td><td>渠道 ID</td><td>1</td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">integer</mark></td><td>子渠道 ID。 如果未创建，请输入0。</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">int($int64)</mark></td><td>当前时间,格式为Unix。</td><td>1577808000</td></tr><tr><td>userId</td><td><mark style="color:blue;">int($int64)</mark></td><td>用户 ID</td><td></td></tr><tr><td>accessToken</td><td><mark style="color:blue;">string</mark></td><td>该参数值由渠道提供。仅在eventType = 4时使用</td><td>accessToken</td></tr><tr><td>ip</td><td><mark style="color:blue;">string</mark></td><td>用户登录IP</td><td>127.0.0.1</td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td>签名。 字符串拼接:username+timestamp</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr></tbody></table>

{% code title="Request" overflow="wrap" %}
```
{
  "cmd": "UserInfo",
  "money": 1000.01,
  "username": "apitest01",
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

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td><mark style="color:blue;">integer</mark></td><td><mark style="color:purple;"><code>200</code></mark>:建议返回的状态码</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr></tbody></table>

{% code title="Responses" overflow="wrap" %}
```json
{
  "status": 200
}
```
{% endcode %}
