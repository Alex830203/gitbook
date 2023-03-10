---
description: 此 api 为取得直接登入迷你游戏的连结。使用此方式仍会发送验证登入请求，验证成功才提供登入连结。
---

# loginTableGame

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数                                             | 格式                                           | 描述                                                                                       |
| ---------------------------------------------- | -------------------------------------------- | ---------------------------------------------------------------------------------------- |
| <mark style="color:red;">username</mark>       | <mark style="color:blue;">string</mark>      | 用户名。 不可使用http保留字元。                                                                       |
| <mark style="color:red;">channelId</mark>      | <mark style="color:blue;">int</mark>         | 渠道ID                                                                                     |
| <mark style="color:red;">timestamp</mark>      | <mark style="color:blue;">int($int64)</mark> | 时间戳记。以毫秒为单位。格式为Unix Time。                                                                |
| <mark style="color:red;">signature</mark>      | <mark style="color:blue;">string</mark>      | <p>签名。 字串拼接：<code>username+timestamp</code></p><p>Note: 如API用户名参数非必要，可以单独使用timestamp</p> |
| <mark style="color:red;">gameID</mark>         | <mark style="color:blue;">string</mark>      | 电子游戏 ID                                                                                  |
| <mark style="color:red;">providerId</mark>     | <mark style="color:blue;">string</mark>      | 电子游戏供应商 ID                                                                               |
| <mark style="color:red;">loginEventType</mark> | <mark style="color:blue;">int</mark>         | 登录方式： 1: 普通登录 4: Token 登录                                                                |
| currency                                       | <mark style="color:blue;">string</mark>      | 货币。                                                                                      |
| pwd                                            | <mark style="color:blue;">string</mark>      | 密码。当loginEventType = 1时必需                                                                |
| token                                          | <mark style="color:blue;">string</mark>      | accessToken。当loginEventType = 4时必需                                                       |
| ip                                             | <mark style="color:blue;">string</mark>      | 登录IP                                                                                     |
| language                                       | <mark style="color:blue;">string</mark>      | 用户语言                                                                                     |

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
  "username": "apitest01",
  "channelId": 1,
  "timestamp": 1577808000000,
  "signature": "bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==",
  "gameID": "dice",
  "providerId": "wayi",
  "loginEventType": 1,
  "currency": "CNY",
  "pwd": "password",
  "token": "tokentokentoken",
  "ip": "127.0.0.1",
  "language": "zh_cn"
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>url</td><td><mark style="color:blue;">string</mark></td><td>登入游戏的连结。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>status</td><td><mark style="color:blue;">int</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td>message</td><td><mark style="color:blue;">string</mark></td><td>错误讯息。</td><td>200</td></tr></tbody></table>

{% code title="Responses" overflow="wrap" %}
```json
{
  "url": "https://test.shrb.vip?token=9dc16aabc787431234ee50aa62ea6dc1-171291&gamecode=dice&platform=pc&lang=zh_cn&mode=live",
  "status": 200,
  "apiVersion": "1.3.55",
  "message": "string"
}
```
{% endcode %}
