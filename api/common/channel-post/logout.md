---
description: 为让玩家离开ebet游戏。
---

# logout

{% hint style="info" %}
<mark style="color:blue;">必须在eBET后台启用相关功能才能使用。</mark>
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数                                        | 格式                                           | 描述                                      |
| ----------------------------------------- | -------------------------------------------- | --------------------------------------- |
| <mark style="color:red;">username</mark>  | <mark style="color:blue;">string</mark>      | 用户名。 不可使用http保留字元。                      |
| <mark style="color:red;">channelId</mark> | <mark style="color:blue;">int</mark>         | 渠道ID                                    |
| <mark style="color:red;">timestamp</mark> | <mark style="color:blue;">int($int64)</mark> | 时间戳记。以毫秒为单位。格式为Unix Time。               |
| <mark style="color:red;">signature</mark> | <mark style="color:blue;">string</mark>      | 签名。 字串拼接：`username+channelId+timestamp` |
| currency                                  | <mark style="color:blue;">string</mark>      | 货币。                                     |

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
  "username": "apitest01",
  "channelId": 1,
  "timestamp": 1577808000000,
  "signature": "dry4mQ5qb7hyAeDDi1Ia+m5fsouP+qf2xfcpb+nP+La5yEMbYuHRz7Fge2OTgVi7DttC8p+Aiedfnnu42ii2lQ==",
  "currency": "CNY"
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td><mark style="color:blue;">int</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" %}
```json
{
  "status": 200,
  "apiVersion": "1.3.55"
}
```
{% endcode %}
