---
description: 验证用户登录。
---

# ​registerOrLogin

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td>RegisterOrLoginReq</td></tr><tr><td>password</td><td><mark style="color:blue;">string</mark></td><td>用户密码。 Token登入时为空值。</td><td></td></tr><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td>1</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td></td></tr><tr><td>ip</td><td><mark style="color:blue;">string</mark></td><td>用户登录IP。</td><td>127.0.0.1</td></tr><tr><td>eventType</td><td><mark style="color:blue;">number</mark></td><td>登录方式。</td><td>1</td></tr><tr><td>accessToken</td><td><mark style="color:blue;">string</mark></td><td><p>accessToken。该参数值由渠道提供。</p><p>普通登入 / Applink登入时为空值</p></td><td>accessToken</td></tr><tr><td>platform</td><td><mark style="color:blue;">number</mark></td><td>用户的平台。</td><td></td></tr><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API 名称。</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>当前时间，格式为Unix。</td><td>1577808000</td></tr><tr><td>sessionToken</td><td><mark style="color:blue;">string</mark></td><td>由渠道提供或随机生成。</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 </td><td></td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td><p>签名。 字符串拼接：</p><p>普通登入 / Applink登入: seqNo+event+channelId+timestamp+username+password</p><p>Token登入: seqNo+event+channelId+timestamp+username+accessToken</p></td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr></tbody></table>

{% embed url="https://docs.google.com/spreadsheets/d/1ejxETVOI9kcCAP5eNpT6CIi4ftGHwcYWMHJTEPqLILs" %}

{% tabs %}
{% tab title="普通登录" %}
{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "password": "hidden",
    "channelId": 1,
    "currency": "CNY",
    "ip": "127.0.0.1",
    "eventType": 1,
    "accessToken": "",
    "platform": 3,
    "event": "registerOrLogin",
    "timestamp": 1683783023626,
    "sessionToken": "005ba9a8925519e5f60908282da187cf",
    "seqNo": "ecbad51d2b49df82f77ad3ef5bde6ea9",
    "signature": "YdGd4VSn+O3eRIcn/fh6MpnGvIvrm1nmNv3v9YMv5SJepwQmLs7gi4b2KuyC3qB8vKyUFn+SfzWsjbMBG7T4sw=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Token登录" %}
{% code title="Request" overflow="wrap" %}
```json
{
    "username": "demo",
    "password": "",
    "channelId": 1,
    "currency": "CNY",
    "ip": "127.0.0.1",
    "eventType": 4,
    "accessToken": "cb5ec14db7755109221800fe6ee331b5",
    "platform": 3,
    "event": "registerOrLogin",
    "timestamp": 1683783649635,
    "sessionToken": "005ba9a8925519e5f60908282da187cf",
    "seqNo": "912634a3bf6cd23225e04791221e410b",
    "signature": "nL9DT8W5guOg9x+IqpfZeJ0B9yvd3Ne8k6CZ5FmI5nsWzI4HUq+UEznIv1tMTJ3PcEmv9L8ur103vve5roxAFQ=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Applink登录" %}
{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "password": "hidden",
    "channelId": 1,
    "currency": "CNY",
    "ip": "127.0.0.1",
    "eventType": 3,
    "accessToken": "",
    "platform": 0,
    "event": "registerOrLogin",
    "timestamp": 1683783023626,
    "sessionToken": "005ba9a8925519e5f60908282da187cf",
    "seqNo": "ecbad51d2b49df82f77ad3ef5bde6ea9",
    "signature": "YdGd4VSn+O3eRIcn/fh6MpnGvIvrm1nmNv3v9YMv5SJepwQmLs7gi4b2KuyC3qB8vKyUFn+SfzWsjbMBG7T4sw=="
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
</code></pre></td></tr><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td><mark style="color:red;">sessionToken</mark></td><td><mark style="color:blue;">string</mark></td><td>sessionToken。由渠道提供或随机生成。</td><td></td></tr><tr><td><mark style="color:red;">currency</mark></td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td></td></tr><tr><td><mark style="color:red;">status</mark></td><td><mark style="color:blue;">number</mark></td><td><a href="../../ebet-zhuang-tai-ma.md#jian-yi-xiang-ying-de-zhuang-tai-dai-ma">建议返回的状态码</a></td><td>200</td></tr><tr><td><mark style="color:red;">event</mark></td><td><mark style="color:blue;">string</mark></td><td>API 名称。</td><td></td></tr><tr><td><mark style="color:red;">seqNo</mark></td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td>nickname</td><td><mark style="color:blue;">string</mark></td><td>用户昵称。</td><td>预设随机生成</td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Responses" overflow="wrap" %}
```json
{
    "accessToken": "cb5ec14db7755109221800fe6ee331b5",
    "subChannelId": 0,
    "username": "demo",
    "sessionToken": "d9e1f52fc216e82879780594815a0079",
    "currency": "CNY",
    "status": 200,
    "event": "registerOrLogin",
    "seqNo": "ecbad51d2b49df82f77ad3ef5bde6ea9"
}
```
{% endcode %}
