---
description: 该 API 目的是让伙伴获得最新的 H5 游戏连结。
---

# launchUrl

{% hint style="info" %}
<mark style="color:blue;">非人民币渠道请忽略</mark><mark style="color:blue;">`china`</mark><mark style="color:blue;">参数。</mark>
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数                                        | 格式                                           | 描述                                                           |
| ----------------------------------------- | -------------------------------------------- | ------------------------------------------------------------ |
| <mark style="color:red;">channelId</mark> | <mark style="color:blue;">int</mark>         | 渠道ID                                                         |
| <mark style="color:red;">timestamp</mark> | <mark style="color:blue;">int($int64)</mark> | 时间戳记。以毫秒为单位。格式为Unix Time。                                    |
| <mark style="color:red;">signature</mark> | <mark style="color:blue;">string</mark>      | 签名。 字串拼接：`channelId+timestamp`                               |
| <mark style="color:red;">currency</mark>  | <mark style="color:blue;">string</mark>      | 货币。                                                          |
| china                                     | <mark style="color:blue;">string</mark>      | <p>判断提供游戏的地区。</p><p>不加此参数则根据货币判断提供游戏的地区。</p><p>1: 中国加速域名</p> |

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
  "channelId": 1,
  "timestamp": 1577808000000,
  "signature": "ZwV0Upcy93v3S/ChPh/K4FtbQ3VfA9bVomRZxBhp7I/nh2P0+qwl+dfax4QZrLwT3TuFIJGv1+nWBb+oTN5bdg==",
  "currency": "CNY",
  "china": 1
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td><mark style="color:blue;">int</mark></td><td>回应状态。<a href="../../ebet-xiang-ying-zhuang-tai-ma.md">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>launchUrl</td><td><mark style="color:blue;">string</mark></td><td>H5 游戏连结。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" %}
```json
{
  "status": 200,
  "launchUrl": "https://test01.ebet-b2b.com/h5/test01",
  "apiVersion": "1.3.55"
}
```
{% endcode %}
