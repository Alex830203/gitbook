---
description: 此 api 为取得直接登入迷你游戏的连结。使用此方式仍会发送验证登入请求，验证成功才提供登入连结。
---

# loginTableGame

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数                                             | 格式                                      | 描述                                 |
| ---------------------------------------------- | --------------------------------------- | ---------------------------------- |
| <mark style="color:red;">username</mark>       | <mark style="color:blue;">string</mark> | 用户名。 不可使用http保留字元。                 |
| <mark style="color:red;">channelId</mark>      | <mark style="color:blue;">number</mark> | 渠道ID                               |
| <mark style="color:red;">timestamp</mark>      | <mark style="color:blue;">number</mark> | 时间戳记。以毫秒为单位。格式为Unix Time。          |
| <mark style="color:red;">signature</mark>      | <mark style="color:blue;">string</mark> | 签名。 字串拼接：username+timestamp        |
| <mark style="color:red;">gameID</mark>         | <mark style="color:blue;">string</mark> | 电子游戏 ID                            |
| <mark style="color:red;">providerId</mark>     | <mark style="color:blue;">string</mark> | 电子游戏供应商 ID                         |
| <mark style="color:red;">loginEventType</mark> | <mark style="color:blue;">number</mark> | 登录方式                               |
| currency                                       | <mark style="color:blue;">string</mark> | 货币。                                |
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
{% code title="Request" overflow="wrap" %}
```json
{
    "channelId": 1,
    "username": "apitest01",
    "timestamp": 1585619696049,
    "signature": "kiHC0kZWnVt0ogftO9nudOchmA0aXq68T5SKTqkYs+YazS3pgj6Q6l7zL5SVP/E4KJmKOJ6nHJ/eFxPOE4YskiuFV4dR+F2CNMuGUuPYZgJKOpFUqx8re2bDYNsb/Hr7/Cbue0jwcF19CDguVut08rWrq5iN5Zazdd0UHixf++M=",
    "loginEventType": 4,
    "token": "0c75f8ed762e047fa0e4f6d6bf61867a",
    "providerId": "pgsoft",
    "gameID": "diaochan"
}
```
{% endcode %}
{% endtab %}

{% tab title="普通登录" %}
{% code title="Request" overflow="wrap" %}
```json
{
    "channelId": 1,
    "username": "demo",
    "timestamp": 1585619696049,
    "signature": "kiHC0kZWnVt0ogftO9nudOchmA0aXq68T5SKTqkYs+YazS3pgj6Q6l7zL5SVP/E4KJmKOJ6nHJ/eFxPOE4YskiuFV4dR+F2CNMuGUuPYZgJKOpFUqx8re2bDYNsb/Hr7/Cbue0jwcF19CDguVut08rWrq5iN5Zazdd0UHixf++M=",
    "loginEventType": 1,
    "pwd":"hidden",
    "providerId": "pgsoft",
    "gameID": "diaochan"
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
