---
description: 获取链接以直接登录到迷你游戏。
---

# loginTableGame

{% hint style="info" %}
<mark style="color:blue;">使用此方法仍会发送验证登录请求。 只有成功验证后，才会提供登录链接。</mark>
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数                                             | 格式                                      | 描述                                 |
| ---------------------------------------------- | --------------------------------------- | ---------------------------------- |
| <mark style="color:red;">channelId</mark>      | <mark style="color:blue;">number</mark> | 渠道ID                               |
| <mark style="color:red;">username</mark>       | <mark style="color:blue;">string</mark> | 用户名。 不可使用http保留字元。                 |
| <mark style="color:red;">timestamp</mark>      | <mark style="color:blue;">number</mark> | 时间戳记。以毫秒为单位。格式为Unix Time。          |
| <mark style="color:red;">signature</mark>      | <mark style="color:blue;">string</mark> | 签名。 字串拼接：username+timestamp        |
| <mark style="color:red;">gameID</mark>         | <mark style="color:blue;">string</mark> | 电子游戏 ID                            |
| <mark style="color:red;">providerId</mark>     | <mark style="color:blue;">string</mark> | 电子游戏供应商 ID                         |
| <mark style="color:red;">loginEventType</mark> | <mark style="color:blue;">number</mark> | 登录方式                               |
| pwd                                            | <mark style="color:blue;">string</mark> | 密码。当loginEventType = 1时必需          |
| token                                          | <mark style="color:blue;">string</mark> | accessToken。当loginEventType = 4时必需 |
| ip                                             | <mark style="color:blue;">string</mark> | 登录IP                               |
| language                                       | <mark style="color:blue;">string</mark> | 用户语言                               |

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% embed url="https://docs.google.com/spreadsheets/d/1ejxETVOI9kcCAP5eNpT6CIi4ftGHwcYWMHJTEPqLILs" %}

{% tabs %}
{% tab title="Token登录" %}
{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
    "timestamp": 1680144767,
    "gameID": "rocket",
    "providerId": "wayi",
    "signature": "MbUAYdWdFUHakpPL8o1+dtVoVPYX4sYrZYlzGvDD0w6klZzWrNnRgVJVpAS5kbJBI1MAol2h/RC5t+2bEoDj+z75E+zSWKeK6h8M29520n4ty2ciO72myM9lJwRn5bn+xIaYEWKQmAkMe92+TjzjajOjOxL+HI9pnxjinkxBbx4=",
    "loginEventType": 4,
    "token": "******"
}
```
{% endcode %}
{% endtab %}

{% tab title="普通登录" %}
{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
    "timestamp": 1680144767,
    "gameID": "rocket",
    "providerId": "wayi",
    "signature": "MbUAYdWdFUHakpPL8o1+dtVoVPYX4sYrZYlzGvDD0w6klZzWrNnRgVJVpAS5kbJBI1MAol2h/RC5t+2bEoDj+z75E+zSWKeK6h8M29520n4ty2ciO72myM9lJwRn5bn+xIaYEWKQmAkMe92+TjzjajOjOxL+HI9pnxjinkxBbx4=",
    "loginEventType": 1,
    "pwd": "******"
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>url</td><td><mark style="color:blue;">string</mark></td><td>登入游戏的连结。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td>message</td><td><mark style="color:blue;">string</mark></td><td>错误讯息。</td><td>200</td></tr></tbody></table>

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "url": "https://game.live666.me?token=fd265a57615262336fc8965856276fce-88915679&gamecode=rocket&platform=pc&lang=zh_tw&mode=live",
    "status": 200,
    "apiVersion": "1.5.94"
}
```
{% endcode %}
