---
description: 获取链接以直接登录到老虎机游戏。
---

# loginslot

{% hint style="info" %}
<mark style="color:blue;">使用此方法仍会发送验证登录请求。 只有成功验证后，才会提供登录链接。</mark>
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数                                             | 格式                                               | 描述                                         |
| ---------------------------------------------- | ------------------------------------------------ | ------------------------------------------ |
| <mark style="color:red;">username</mark>       | <mark style="color:blue;">string</mark>          | 用户名。 不可使用http保留字元。                         |
| <mark style="color:red;">channelId</mark>      | <mark style="color:blue;">number</mark>          | 渠道ID                                       |
| <mark style="color:red;">timestamp</mark>      | <mark style="color:blue;">integer($int64)</mark> | 时间戳记。以毫秒为单位。格式为Unix Time。                  |
| <mark style="color:red;">signature</mark>      | <mark style="color:blue;">string</mark>          | 签名。 字串拼接：username+timestamp                |
| <mark style="color:red;">gameID</mark>         | <mark style="color:blue;">string</mark>          | 老虎机游戏ID                                    |
| <mark style="color:red;">providerId</mark>     | <mark style="color:blue;">string</mark>          | 老虎机游戏供应商ID                                 |
| <mark style="color:red;">loginEventType</mark> | <mark style="color:blue;">integer</mark>         | <p>登录方式：<br>1: 普通登录<br>4: Token 登录</p>     |
| currency                                       | <mark style="color:blue;">string</mark>          | 货币。                                        |
| pwd                                            | <mark style="color:blue;">string</mark>          | 密码 for login. 当loginEventType = 1时必需       |
| token                                          | <mark style="color:blue;">string</mark>          | AccessToken for 登录. 当loginEventType = 4时必需 |
| ip                                             | <mark style="color:blue;">string</mark>          | 登录IP                                       |
| language                                       | <mark style="color:blue;">string</mark>          | 用户语言                                       |

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
  "gameID": "NG-1026",
  "providerId": "genesis",
  "loginEventType": 1,
  "currency": "CNY",
  "pwd": "password",
  "token": "",
  "ip": "127.0.0.1",
  "language": "zh-hans"
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td>integer</td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td>slotURL</td><td><mark style="color:blue;">string</mark></td><td>登入老虎机游戏的连结。</td><td></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" %}
```json
{
  "status": 200,
  "apiVersion": "1.3.55",
  "slotURL": "https://ugc.rongfakj.com/NG-1026/HTML5/index.html?turbo=true&mode=real&partner=be6c07f5-827c-4e76-8223-f3bda46f5a02&session=cppzzrex-xa450978331-4e055c951c834ae8a14960876&language=zh-hans&gs=nurgs-RMX&partnerCode=EBET&referer=ugc.rongfakj.com&refererRetries=0"
}
```
{% endcode %}
