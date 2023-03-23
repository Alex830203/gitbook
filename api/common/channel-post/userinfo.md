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
| <mark style="color:red;">signature</mark> | <mark style="color:blue;">string</mark> | 签名。 字串拼接：username+timestamp  |
| <mark style="color:red;">username</mark>  | <mark style="color:blue;">string</mark> | 用户名。 不可使用http保留字元。           |
| <mark style="color:red;">timestamp</mark> | <mark style="color:blue;">number</mark> | 时间戳记。以毫秒为单位。格式为Unix Time。    |
| currency                                  | <mark style="color:blue;">string</mark> | 货币。                          |

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
  "channelId": 1,
  "signature": "bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==",
  "username": "apitest01",
  "timestamp": 1577808000000,
  "currency": "CNY"
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td>channelId</td><td><mark style="color:blue;">string</mark></td><td>渠道ID</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">string</mark></td><td>子渠道ID</td><td>200</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。</td><td></td></tr><tr><td>userId</td><td><mark style="color:blue;">number</mark></td><td>用户ID</td><td></td></tr><tr><td>money</td><td><mark style="color:blue;">number</mark></td><td>用户的金額。</td><td></td></tr><tr><td>wallet</td><td><mark style="color:blue;">array</mark></td><td>每个钱包的余额。阵列值为物件，下表为物件参数说明。</td><td></td></tr></tbody></table>

{% embed url="https://docs.google.com/spreadsheets/d/1ejxETVOI9kcCAP5eNpT6CIi4ftGHwcYWMHJTEPqLILs" %}

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
  "wallet": [
    {
      "typeId": 0,
      "money": 200
    }
  ]
}
```
{% endcode %}
