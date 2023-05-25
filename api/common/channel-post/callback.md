---
description: 登入通知
---

# callback

{% hint style="warning" %}
<mark style="color:orange;">渠道需提供登录界面链接，由eBET人員设置开启。</mark>
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="167">参数</th><th width="114">格式</th><th>描述</th></tr></thead><tbody><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td></tr><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道ID</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>时间戳记。以毫秒为单位。格式为Unix Time。</td></tr><tr><td><mark style="color:red;">accessToken</mark></td><td><mark style="color:blue;">string</mark></td><td>该参数值由渠道提供</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td><p>签名。字串拼接:</p><p>username+channelId+accessToken+timestamp</p></td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">number</mark></td><td>子渠道ID</td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" lineNumbers="true" %}
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

<table><thead><tr><th width="176">参数</th><th width="114.66666666666666">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>channelId</td><td><mark style="color:blue;">string</mark></td><td>渠道ID</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">string</mark></td><td>子渠道ID</td><td>200</td></tr><tr><td>userId</td><td><mark style="color:blue;">number</mark></td><td>用户ID</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td></td></tr><tr><td>wallet</td><td><mark style="color:blue;">array</mark></td><td><p>每个钱包的余额。</p><p>阵列值为物件，下表为物件参数说明。</p></td><td></td></tr><tr><td>money</td><td><mark style="color:blue;">number</mark></td><td>用户的金額。</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>当前时间。以秒为单位。格式为Unix Time。</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr></tbody></table>

{% embed url="https://docs.google.com/spreadsheets/d/1ejxETVOI9kcCAP5eNpT6CIi4ftGHwcYWMHJTEPqLILs" %}

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
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
