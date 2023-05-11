---
description: 取得最新真人游戏桌台资讯。
---

# getroomlist

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道ID。</td><td>RegisterOrLoginReq</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>时间戳记。以毫秒为单位。格式为Unix Time。</td><td>1</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。 字串拼接：channelId+timestamp</td><td>1</td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
  "channelId": 1,
  "timestamp": 1577808000000,
  "signature": "ZwV0Upcy93v3S/ChPh/K4FtbQ3VfA9bVomRZxBhp7I/nh2P0+qwl+dfax4QZrLwT3TuFIJGv1+nWBb+oTN5bdg=="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>count</td><td><mark style="color:blue;">number</mark></td><td>总数。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>tableCodes</td><td><mark style="color:blue;">array</mark></td><td><p>游戏桌详情。</p><p>阵列值为物件，下表为物件参数说明。</p></td><td><pre><code>0
</code></pre></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td><pre><code>apitest01
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td>200</td></tr></tbody></table>

**tableCodes**

| 参数           | 格式                                      | 描述                                           |
| ------------ | --------------------------------------- | -------------------------------------------- |
| tableCode    | <mark style="color:blue;">string</mark> | 游戏桌ID。                                       |
| tableType    | <mark style="color:blue;">number</mark> | 游戏类型。                                        |
| tableSubType | <mark style="color:blue;">number</mark> | 游戏桌类型。                                       |
| isMaintain   | <mark style="color:blue;">number</mark> | <p>游戏桌状态。</p><p>0: 开放中 </p><p>其他参数值: 维护中</p> |

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "count": 3,
    "tableCodes": [
        {
            "tableCode": "BP1",
            "tableType": 1,
            "tableSubType": 0,
            "isMaintain": 0
        },
        {
            "tableCode": "BPV1",
            "tableType": 1,
            "tableSubType": 1,
            "isMaintain": 0
        },
        {
            "tableCode": "NNP1",
            "tableType": 8,
            "tableSubType": 0,
            "isMaintain": 2
        }
    ],
    "status": 200,
    "apiVersion": "1.5.94"
}
```
{% endcode %}
