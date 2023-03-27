---
description: 如果渠道不想通过 eBET 界面登录，则渠道可以使用自己的登录界面。 渠道在验证玩家后必须请求该API 通知eBET让玩家登录游戏。
---

# callback

{% hint style="warning" %}
<mark style="color:red;">渠道需提供登录界面链接，由eBET人員设置开启。</mark>
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数                                          | 格式                                      | 描述                                                             |
| ------------------------------------------- | --------------------------------------- | -------------------------------------------------------------- |
| <mark style="color:red;">username</mark>    | <mark style="color:blue;">string</mark> | 用户名。 不可使用http保留字元。                                             |
| <mark style="color:red;">channelId</mark>   | <mark style="color:blue;">number</mark> | 渠道ID                                                           |
| <mark style="color:red;">timestamp</mark>   | <mark style="color:blue;">number</mark> | 时间戳记。以毫秒为单位。格式为Unix Time。                                      |
| <mark style="color:red;">accessToken</mark> | <mark style="color:blue;">string</mark> | 该参数值由渠道提供                                                      |
| <mark style="color:red;">signature</mark>   | <mark style="color:blue;">string</mark> | <p>签名。字串拼接:</p><p>username+channelId+accessToken+timestamp</p> |
| subChannelId                                | <mark style="color:blue;">number</mark> | 子渠道ID                                                          |

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "timestamp": 1585638821,
    "accessToken": "584c26e798deffc96cc7af073c184cd0",
    "signature": "qwVPrRNJSi9X6WNT18jDREQWmzPvjUL2Ff5zZZWLH/DxBH2n08hcmz9KbnC1GM5QmIl+ktV1HoOxHsomKspHy5+VZJfE+yksVHk71othgxb2Q0+NZ8sTSpziOW8k7ZA0TmTTH+ALvbFnvoiiqXuw1qhErV8j8wfqh/0W+PJlVLs="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>channelId</td><td><mark style="color:blue;">string</mark></td><td>渠道ID</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">string</mark></td><td>子渠道ID</td><td>200</td></tr><tr><td>userId</td><td><mark style="color:blue;">number</mark></td><td>用户ID</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。</td><td></td></tr><tr><td>wallet</td><td><mark style="color:blue;">array</mark></td><td><p>每个钱包的余额。</p><p>阵列值为物件，下表为物件参数说明。</p></td><td></td></tr><tr><td>money</td><td><mark style="color:blue;">number</mark></td><td>用户的金額。</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>当前时间。以秒为单位。格式为Unix Time。</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr></tbody></table>

{% embed url="https://docs.google.com/spreadsheets/d/1ejxETVOI9kcCAP5eNpT6CIi4ftGHwcYWMHJTEPqLILs" %}

{% code title="Responses" overflow="wrap" %}
```json
{
    "channelId": 1,
    "subChannelId": 0,
    "userId": 127001,
    "username": "demo",
    "wallet": [
        {
            "typeId": 0,
            "money": 1234567.89
        },
        {
            "typeId": 1,
            "money": 0
        },
        {
            "typeId": 2,
            "money": 0
        },
        {
            "typeId": 3,
            "money": 0
        },
        {
            "typeId": 4,
            "money": 0
        },
        {
            "typeId": 5,
            "money": 0
        },
        {
            "typeId": 6,
            "money": 0
        }
    ],
    "money": 1234567.89,
    "timestamp": 1585624727,
    "status": 200,
    "apiVersion": "1.3.91"
}
```
{% endcode %}
