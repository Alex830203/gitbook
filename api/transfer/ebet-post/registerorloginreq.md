---
description: 用于验证用户登录。 将请求直接发送到渠道提供的服务器URL。
---

# RegisterOrLoginReq

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>cmd</td><td><mark style="color:blue;">string</mark></td><td>API 名称。</td><td>RegisterOrLoginReq</td></tr><tr><td>eventType</td><td><mark style="color:blue;">number</mark></td><td>登录方式。参数值定义请参考下表。</td><td>1</td></tr><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td>1</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td>apitest01</td></tr><tr><td>password</td><td><mark style="color:blue;">string</mark></td><td>用户密码。 空字符串為沒有密码。</td><td>password</td></tr><tr><td>accessToken</td><td><mark style="color:blue;">string</mark></td><td>该参数值由渠道提供。仅在eventType = 4时使用。</td><td>accessToken</td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>当前时间，格式为Unix。</td><td>1577808000</td></tr><tr><td>ip</td><td><mark style="color:blue;">string</mark></td><td>用户登录IP。</td><td>127.0.0.1</td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td><p>签名。 字符串拼接:</p><p>普通登入 / Applink登入: username+timestamp</p><p>Token登入: timestamp+accessToken</p></td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr></tbody></table>

{% embed url="https://docs.google.com/spreadsheets/d/1ejxETVOI9kcCAP5eNpT6CIi4ftGHwcYWMHJTEPqLILs" %}

{% tabs %}
{% tab title="普通登录" %}
{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
  "cmd": "RegisterOrLoginReq",
  "eventType": 1,
  "channelId": 1,
  "username": "demo",
  "password": "password",
  "timestamp": 1577808000,
  "ip": "127.0.0.1",
  "signature": "bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Token登录" %}
{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "cmd": "RegisterOrLoginReq",
    "eventType": 4,
    "channelId": 1,
    "username": "demo",
    "accessToken": "hidden",
    "password": "hidden",
    "timestamp": 1585205819,
    "ip": "127.0.0.1",
    "signature": "akFplXO1SzDT/ZNWtxXLbKp8WCh87OzcY6d3nURvpwmk8jx4miNorwqft3AfLJ28ye7qlNnitgKnUOxSL6AAKw=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Applink登录" %}
{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "cmd": "RegisterOrLoginReq",
    "eventType": 3,
    "channelId": 1,
    "username": "demo",
    "password": "hidden",
    "timestamp": 1585188822,
    "ip": "127.0.0.1",
    "signature": "b9vqWDAER2GxKcgOc+RDBhrBxY//ngSq/kN03hmSav2Q3+isYcxy9tcMBPtaL08OUHsDpCnuM+Y7OGxZB23BHw=="
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">accessToken</mark></td><td><mark style="color:blue;">string</mark></td><td>渠道返回的accessToken。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td><mark style="color:red;">subChannelId</mark></td><td><mark style="color:blue;">number</mark></td><td>子渠道 ID。 如果未创建，请输入0。</td><td><pre><code>0
</code></pre></td></tr><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td><mark style="color:red;">status</mark></td><td><mark style="color:blue;">number</mark></td><td><a href="../../ebet-zhuang-tai-ma.md#jian-yi-xiang-ying-de-zhuang-tai-dai-ma">建议返回的状态码</a></td><td>200</td></tr><tr><td>nickname</td><td><mark style="color:blue;">string</mark></td><td>用户昵称。预设随机生成。</td><td>预设随机生成</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td>CNY</td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "subChannelId": 0,
    "accessToken": "TestaccessTokenAPILogin04",
    "status": 200,
    "username": "demo"
}
```
{% endcode %}
