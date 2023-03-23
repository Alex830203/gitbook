---
description: 创建新用户
---

# syncuser

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数                                        | 格式                                      | 描述                 |
| ----------------------------------------- | --------------------------------------- | ------------------ |
| <mark style="color:red;">channelId</mark> | <mark style="color:blue;">number</mark> | 渠道ID               |
| <mark style="color:red;">signature</mark> | <mark style="color:blue;">string</mark> | 签名。 字串拼接：username  |
| <mark style="color:red;">username</mark>  | <mark style="color:blue;">string</mark> | 用户名。 不可使用http保留字元。 |
| subChannelId                              | <mark style="color:blue;">number</mark> | 子渠道ID              |
| currency                                  | <mark style="color:blue;">string</mark> | 货币。                |

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
  "channelId": 1,
  "signature": "ZwV0Upcy93v3S/ChPh/K4FtbQ3VfA9bVomRZxBhp7I/nh2P0+qwl+dfax4QZrLwT3TuFIJGv1+nWBb+oTN5bdg==",
  "username": "apitest01",
  "subChannelId": 0,
  "currency": "CNY"
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a><br><mark style="color:red;">401：该帐户已注册。</mark></td><td><pre><code>0
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
