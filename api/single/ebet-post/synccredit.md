---
description: 此api是用于确认用户当前的金额。
---

# ​syncCredit

{% hint style="info" %}
发送请求至接收地址是渠道的服务器url + api \
E.g. http://127.0.0.1/syncCredit
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td>RegisterOrLoginReq</td></tr><tr><td>password</td><td><mark style="color:blue;">string</mark></td><td>用户密码。 空字符串為沒有密码。</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td>1</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币</td><td></td></tr><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td>127.0.0.1</td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>当前时间,格式为Unix。</td><td>1577808000</td></tr><tr><td>sessionToken</td><td><mark style="color:blue;">string</mark></td><td>由渠道提供或随机生成</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" %}
```json
{
  "channelId": 1,
  "username": "apitest01",
  "tableType": 1,
  "currency": "CNY",
  "event": "syncCredit",
  "timestamp": 1577808000000,
  "sessionToken": "sessionToken",
  "seqNo": "seqNoseqNoseqNoseqNo"
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。 不可使用http保留字元。</td><td></td></tr><tr><td><mark style="color:red;">money</mark></td><td><mark style="color:blue;">number</mark></td><td>用户的金額</td><td></td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币</td><td></td></tr><tr><td><mark style="color:red;">status</mark></td><td><mark style="color:blue;">number</mark></td><td><mark style="color:purple;"><code>200</code></mark>:建议返回的状态码</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td><mark style="color:red;">event</mark></td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td></td></tr><tr><td><mark style="color:red;">seqNo</mark></td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>时间戳记,以毫秒为单位。</td><td></td></tr></tbody></table>

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Responses" overflow="wrap" %}
```json
{
  "username": "apitest01",
  "money": 1000.01,
  "currency": "CNY",
  "status": 200,
  "event": "syncCredit",
  "seqNo": "seqNoseqNoseqNoseqNo",
  "timestamp": 1577808000000
}
```
{% endcode %}
