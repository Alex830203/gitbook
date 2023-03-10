---
description: >-
  此api用于验证用户登录。 发送请求至接收地址是渠道的服务器url + api。  E.g.
  http://127.0.0.1/registerOrLogin
---

# ​registerOrLogin



## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td>RegisterOrLoginReq</td></tr><tr><td>password</td><td><mark style="color:blue;">string</mark></td><td>用户密码。 空字符串為沒有密码。</td><td></td></tr><tr><td>channelId</td><td><mark style="color:blue;">int</mark></td><td>渠道 ID</td><td>1</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币</td><td></td></tr><tr><td>ip</td><td><mark style="color:blue;">string</mark></td><td>用户登录IP</td><td>127.0.0.1</td></tr><tr><td>eventType</td><td><mark style="color:blue;">int</mark></td><td><p>登录方式:</p><p>1:普通登录</p><p>3:Applink登录</p><p>4:Token登录</p></td><td>1</td></tr><tr><td>accessToken</td><td><mark style="color:blue;">string</mark></td><td>该参数值由渠道提供。仅在eventType = 4时使用</td><td>accessToken</td></tr><tr><td>platform</td><td><mark style="color:blue;">integer</mark></td><td>用户的平台</td><td></td></tr><tr><td>password</td><td><mark style="color:blue;">string</mark></td><td>用户密码。 空字符串為沒有密码。</td><td>password</td></tr><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">int($int64)</mark></td><td>当前时间,格式为Unix。</td><td>1577808000</td></tr><tr><td>sessionToken</td><td><mark style="color:blue;">string</mark></td><td>由渠道提供或随机生成</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td><p>签名。 </p><p>字符串拼接:</p><p>普通登录/applink登录: username+timestamp</p><p>token登录: timestamp+accessToken</p></td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr></tbody></table>

{% tabs %}
{% tab title="普通登录" %}
{% code title="Request" overflow="wrap" %}
```json
{
  "username": "apitest01",
  "password": "password",
  "channelId": 1,
  "currency": "CNY",
  "ip": "127.0.0.1",
  "eventType": 1,
  "platform": 3,
  "event": "registerOrLogin",
  "timestamp": 1577808000000,
  "sessionToken": "sessionToken",
  "seqNo": "seqNoseqNoseqNoseqNo",
  "signature": "bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Token登录" %}
{% code title="Request" overflow="wrap" %}
```json
{
  "username": "apitest01",
  "password": "password",
  "channelId": 1,
  "currency": "CNY",
  "ip": "127.0.0.1",
  "eventType": 4,
  "accessToken": "accessToken",
  "platform": 3,
  "event": "registerOrLogin",
  "timestamp": 1577808000000,
  "sessionToken": "sessionToken",
  "seqNo": "seqNoseqNoseqNoseqNo",
  "signature": "bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Applink登录" %}

{% endtab %}
{% endtabs %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">accessToken</mark></td><td><mark style="color:blue;">string</mark></td><td>渠道返回的accessToken。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td><mark style="color:red;">subChannelId</mark></td><td><mark style="color:blue;">int</mark></td><td>子渠道 ID。 如果未创建，请输入0。</td><td><pre><code>0
</code></pre></td></tr><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td><mark style="color:red;">sessionToken</mark></td><td><mark style="color:blue;">string</mark></td><td>由渠道提供或随机生成</td><td></td></tr><tr><td><mark style="color:red;">currency</mark></td><td><mark style="color:blue;">string</mark></td><td>货币event</td><td></td></tr><tr><td><mark style="color:red;">status</mark></td><td><mark style="color:blue;">int</mark></td><td>建议返回的状态码</td><td>200</td></tr><tr><td><mark style="color:red;">event</mark></td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td></td></tr><tr><td><mark style="color:red;">seqNo</mark></td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td>nickname</td><td><mark style="color:blue;">string</mark></td><td>用户昵称</td><td>预设随机生成</td></tr></tbody></table>

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Responses" overflow="wrap" %}
```json
{
  "accessToken": "accessTokenTest",
  "subChannelId": 0,
  "username": "apitest01",
  "sessionToken": "sessionToken",
  "currency": "CNY",
  "status": 200,
  "event": "registerOrLogin",
  "seqNo": "seqNoseqNoseqNoseqNo",
  "nickname": "用户昵称，预设随机生成"
}
```
{% endcode %}
