---
description: 此api用于验证用户登录。 将请求直接发送到渠道提供的服务器URL。
---

# /RegisterOrLoginReq (验证用户登录)

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>cmd</td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td>RegisterOrLoginReq</td></tr><tr><td>eventType</td><td><mark style="color:blue;">int</mark></td><td><p>登录方式:</p><p>1:普通登录</p><p>3:Applink登录</p><p>4:Token登录</p></td><td>1</td></tr><tr><td>channelId</td><td><mark style="color:blue;">int</mark></td><td>渠道 ID</td><td>1</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td>apitest01</td></tr><tr><td>password</td><td><mark style="color:blue;">string</mark></td><td>用户密码。 空字符串為沒有密码。</td><td>password</td></tr><tr><td>accessToken</td><td><mark style="color:blue;">string</mark></td><td>该参数值由渠道提供。仅在eventType = 4时使用</td><td>accessToken</td></tr><tr><td>timestamp</td><td><mark style="color:blue;">integer($int64)</mark></td><td>当前时间,格式为Unix。</td><td>1577808000</td></tr><tr><td>ip</td><td><mark style="color:blue;">string</mark></td><td>用户登录IP</td><td>127.0.0.1</td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td><p>签名。 </p><p>字符串拼接:</p><p>普通登录/applink登录: username+timestamp</p><p>token登录: timestamp+accessToken</p></td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr></tbody></table>

{% code title="Request" overflow="wrap" %}
```json
{
  "cmd": "RegisterOrLoginReq",
  "eventType": 1,
  "channelId": 1,
  "username": "apitest01",
  "password": "password",
  "accessToken": "accessToken",
  "timestamp": 1577808000,
  "ip": "127.0.0.1",
  "signature": "bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ=="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">accessToken</mark></td><td><mark style="color:blue;">string</mark></td><td>渠道返回的accessToken。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td><mark style="color:red;">subChannelId</mark></td><td><mark style="color:blue;">int</mark></td><td>子渠道 ID。 如果未创建，请输入0。</td><td><pre><code>0
</code></pre></td></tr><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td><mark style="color:red;">status</mark></td><td><mark style="color:blue;">int</mark></td><td>建议返回的状态码</td><td>200</td></tr><tr><td>nickname</td><td><mark style="color:blue;">string</mark></td><td>用户昵称</td><td>预设随机生成</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币</td><td>CNY</td></tr></tbody></table>

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Responses" overflow="wrap" %}
```json
{
  "accessToken": "accessTokenTest",
  "subChannelId": 0,
  "username": "apitest01",
  "status": 200,
  "nickname": "用户昵称，预设随机生成",
  "currency": "CNY"
}
```
{% endcode %}
