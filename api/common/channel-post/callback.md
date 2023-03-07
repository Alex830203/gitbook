---
description: 如果渠道不想通过 eBET 界面登录，则渠道可以使用自己的登录界面。 渠道在验证玩家后必须请求该API 通知eBET让玩家登录游戏。
---

# callback

{% hint style="warning" %}
<mark style="color:red;">渠道需提供登录界面链接，由我方后台设置开启。</mark>
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数                                          | 格式                                           | 描述                                                  |
| ------------------------------------------- | -------------------------------------------- | --------------------------------------------------- |
| <mark style="color:red;">username</mark>    | <mark style="color:blue;">string</mark>      | 用户名。 不可使用http保留字元。                                  |
| <mark style="color:red;">channelId</mark>   | <mark style="color:blue;">int</mark>         | 渠道ID                                                |
| subChannelId                                | <mark style="color:blue;">int</mark>         | 子渠道ID                                               |
| <mark style="color:red;">timestamp</mark>   | <mark style="color:blue;">int($int64)</mark> | 时间戳记。以毫秒为单位。格式为Unix Time。                           |
| <mark style="color:red;">accessToken</mark> | <mark style="color:blue;">string</mark>      | 该参数值由渠道提供                                           |
| <mark style="color:red;">signature</mark>   | <mark style="color:blue;">string</mark>      | 签名。字串拼接 :`username+channelId+accessToken+timestamp` |

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
  "username": "apitest01",
  "channelId": 1,
  "subChannelId": 0,
  "timestamp": 1987654321,
  "accessToken": "accessToken",
  "signature": "ZwV0Upcy93v3S/ChPh/K4FtbQ3VfA9bVomRZxBhp7I/nh2P0+qwl+dfax4QZrLwT3TuFIJGv1+nWBb+oTN5bdg=="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td><mark style="color:blue;">int</mark></td><td>回应状态。<a href="../../ebet-xiang-ying-zhuang-tai-ma.md">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td>channelId</td><td><mark style="color:blue;">string</mark></td><td>渠道ID</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">string</mark></td><td>子渠道ID</td><td>200</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。 不可使用http保留字元。</td><td></td></tr><tr><td>userId</td><td><mark style="color:blue;">int($int64)</mark></td><td>用户ID</td><td></td></tr><tr><td>money</td><td><p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p></td><td>用户的金額。</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">int($int64)</mark></td><td>当前时间。以秒为单位。格式为Unix Time。</td><td></td></tr><tr><td>wallet</td><td><mark style="color:blue;">array</mark></td><td>每个钱包的余额。<br>typeId<br>money</td><td></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" %}
```json
{
  "status": 200,
  "apiVersion": "1.3.55",
  "channelId": 1,
  "subChannelId": 0,
  "username": "apitest01",
  "userId": 1919191919,
  "money": 100000.01,
  "timestamp": 1577808000,
  "wallet": [
    {
      "typeId": 0,
      "money": 200
    }
  ]
}
```
{% endcode %}
