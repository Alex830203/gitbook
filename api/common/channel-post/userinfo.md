---
description: 查询用户信息
---

# userinfo

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数                                        | 格式                                      | 描述                           |
| ----------------------------------------- | --------------------------------------- | ---------------------------- |
| <mark style="color:red;">channelId</mark> | <mark style="color:blue;">number</mark> | 渠道ID                         |
| <mark style="color:red;">username</mark>  | <mark style="color:blue;">string</mark> | 用户名。 不可使用http保留字元。           |
| <mark style="color:red;">timestamp</mark> | <mark style="color:blue;">number</mark> | 时间戳记。以毫秒为单位。格式为Unix Time。    |
| <mark style="color:red;">signature</mark> | <mark style="color:blue;">string</mark> | 签名。 字串拼接：username+timestamp  |

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": -1,
    "username": "demo",
    "timestamp": 1680158927,
    "signature": "ehsCo8SKUoixpT75YwC9pXeFu53tg6YorIORYUg61UqMDRYbh5wbxjP0aSgzTQQRZj8P1AbWbRcYrQMaTEzzO8EytQ2I66rYw4iydDYwUg5qvc6CKd3IkHpBOZj+L/8Sz34HF4Edi5ptDseC7yEEHxC4tZe/1KTyUh1Jz8cvNPE="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>channelId</td><td><mark style="color:blue;">string</mark></td><td>渠道ID。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">string</mark></td><td>子渠道ID。</td><td>200</td></tr><tr><td>userId</td><td><mark style="color:blue;">number</mark></td><td>用户ID。</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。</td><td></td></tr><tr><td>wallet</td><td><mark style="color:blue;">array</mark></td><td>每个钱包的余额。阵列值为物件，下表为物件参数说明。</td><td></td></tr><tr><td>money</td><td><mark style="color:blue;">number</mark></td><td>用户的金額。</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>时间戳记。以毫秒为单位。格式为Unix Time。</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">integer</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr></tbody></table>

#### wallet:

| 参数     | 格式                                       | 描述     |
| ------ | ---------------------------------------- | ------ |
| typeId | <mark style="color:blue;">integer</mark> | 钱包种类。  |
| money  | <mark style="color:blue;">number</mark>  | 钱包的余额。 |

{% embed url="https://docs.google.com/spreadsheets/d/1ejxETVOI9kcCAP5eNpT6CIi4ftGHwcYWMHJTEPqLILs" %}

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "subChannelId": 0,
    "userId": 88915679,
    "username": "demo",
    "wallet": [
        {
            "typeId": 0,
            "money": 1002906.52
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
    "money": 1002906.52,
    "timestamp": 1680158938,
    "status": 200,
    "apiVersion": "1.5.94"
}
```
{% endcode %}
