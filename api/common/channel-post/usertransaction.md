---
description: 查询一段时间内登录用户的当前金额。
---

# usertransaction

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数                                        | 格式                                       | 描述                                                                        |
| ----------------------------------------- | ---------------------------------------- | ------------------------------------------------------------------------- |
| <mark style="color:red;">channelId</mark> | <mark style="color:blue;">number</mark>  | 渠道ID                                                                      |
| <mark style="color:red;">timestamp</mark> | <mark style="color:blue;">number</mark>  | 时间戳记。以毫秒为单位。格式为Unix Time。                                                 |
| <mark style="color:red;">signature</mark> | <mark style="color:blue;">string</mark>  | <p>签名。 字串拼接：username+timestamp <br>Note: 如API用户名参数非必要，可以单独使用timestamp</p> |
| username                                  | <mark style="color:blue;">string</mark>  | 用户名。                                                                      |
| subChannelId                              | <mark style="color:blue;">number</mark>  | 子渠道ID                                                                     |
| pageNum                                   | <mark style="color:blue;">number</mark>  | 页码。 默认值为1。                                                                |
| pageSize                                  | <mark style="color:blue;">number</mark>  | 每页上显示的记录数。 默认值为10。最大为5000。                                                |
| startTimeStr                              | <mark style="color:blue;">string</mark>  | 查询时间范围的开始。                                                                |
| endTimeStr                                | <mark style="color:blue;">string</mark>  | 查询时间范围的结束。                                                                |
| tradeType                                 | <mark style="color:orange;">array</mark> | 交易记录类型。                                                                   |

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% hint style="info" %}
<mark style="color:blue;">由于数据量可能太大，建议带以下参数减少查询时间。</mark>\ <mark style="color:blue;">(startTimeStr, endTimeStr, pageNum, pageSize)</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
    "channelId": 1,
    "timestamp": 1680164539,
    "signature": "ReYUBfjNLCCC1bwqlIvDidNE52l67Nifp87Xtr+gTzQxFtefd85y8Iya36SW4RqhPy5c8Nz/2CF9X3FtBOqofwUE4zlIDsB5LDao7ILgjzaXZgmYJc6j0T8fGf0knF2kXYfUNak+YouPew/J3hG0tGZ9o7hSAHtMwd8bIMXVd6g="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>count</td><td><mark style="color:blue;">number</mark></td><td>总数。</td><td></td></tr><tr><td>remainingVisits</td><td><mark style="color:blue;">number</mark></td><td>剩余请求数，每分钟500次。</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>transactions</td><td><mark style="color:orange;">array</mark></td><td>交易记录。</td><td></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr></tbody></table>

transactions

| 参数                 | 格式                                      | 描述      |
| ------------------ | --------------------------------------- | ------- |
| userId             | <mark style="color:blue;">number</mark> | 用户ID    |
| username           | <mark style="color:blue;">string</mark> | 用户名。    |
| tradeType          | <mark style="color:blue;">number</mark> | 事务代码    |
| roundNo            | <mark style="color:blue;">string</mark> | 牌局号码。   |
| transBeforeBalance | <mark style="color:blue;">number</mark> | 更改前的金额。 |
| transBalance       | <mark style="color:blue;">number</mark> | 更改金额。   |
| transAfterBalance  | <mark style="color:blue;">number</mark> | 更改后的金额。 |
| transactionId      | <mark style="color:blue;">string</mark> | 交易编号    |
| time               | <mark style="color:blue;">string</mark> | 交易时间    |
| subChannelId       | <mark style="color:blue;">number</mark> | 子渠道ID。  |
| bonusId            | <mark style="color:blue;">number</mark> | 活动ID。   |
| bonusName          | <mark style="color:blue;">string</mark> | 活动名称。   |

{% code title="Responses" overflow="wrap" %}
```json
{
    "count": 3,
    "remainingVisits": 499,
    "status": 200,
    "transactions": [
        {
            "userId": 67928346,
            "username": "demo",
            "tradeType": 1,
            "roundNo": "BP7-230330094849",
            "transBeforeBalance": 125168.49,
            "transBalance": -100,
            "transAfterBalance": 125068.49,
            "transactionId": "6424ea8c3074280041a0fc16",
            "time": "2023-03-30T01:49:00.849Z",
            "subChannelId": 0
        },
        {
            "userId": 67928346,
            "username": "demo",
            "tradeType": 2,
            "roundNo": "BP7-230330094849",
            "transBeforeBalance": 125068.49,
            "transBalance": 195,
            "transAfterBalance": 125263.49,
            "transactionId": "6424eaa8dac6a44999afa09a",
            "time": "2023-03-30T01:49:28.513Z",
            "subChannelId": 0
        },
        {
            "userId": 67928346,
            "username": "demo",
            "tradeType": 23,
            "roundNo": "BP7-230330094849",
            "transBeforeBalance": 125263.49,
            "transBalance": 10,
            "transAfterBalance": 125273.49,
            "transactionId": "6424ec613074280041a0fc71",
            "time": "2023-03-30T01:49:49.753Z",
            "subChannelId": 0,
            "bonusId": 23,
            "bonusName": "Lucky red envelope"
        }
    ],
    "apiVersion": "1.5.94"
}
```
{% endcode %}
