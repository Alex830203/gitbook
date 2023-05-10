---
description: 查询时间段内的总计报告。
---

# userbetsummary

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数                                        | 格式                                      | 描述                                                                        |
| ----------------------------------------- | --------------------------------------- | ------------------------------------------------------------------------- |
| <mark style="color:red;">channelId</mark> | <mark style="color:blue;">number</mark> | 渠道ID                                                                      |
| <mark style="color:red;">timestamp</mark> | <mark style="color:blue;">number</mark> | 时间戳记。以毫秒为单位。格式为Unix Time。                                                 |
| <mark style="color:red;">signature</mark> | <mark style="color:blue;">string</mark> | <p>签名。 字串拼接：username+timestamp <br>Note: 如API用户名参数非必要，可以单独使用timestamp</p> |
| username                                  | <mark style="color:blue;">string</mark> | 用户名。                                                                      |
| subChannelId                              | <mark style="color:blue;">number</mark> | 子渠道ID。                                                                    |
| startTimeStr                              | <mark style="color:blue;">string</mark> | 查询时间范围的开始。                                                                |
| endTimeStr                                | <mark style="color:blue;">string</mark> | 查询时间范围的结束。                                                                |
| gameType                                  | <mark style="color:blue;">number</mark> | 游戏类型。                                                                     |
| judgeTime                                 | <mark style="color:blue;">number</mark> | 判断查询时间。默认为0。                                                              |
| userId                                    | <mark style="color:blue;">number</mark> | 用户ID。                                                                     |

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% hint style="info" %}
<mark style="color:blue;">预设时间段是当天。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "timestamp": 1680159264,
    "pageNum": 1,
    "pageSize": 10,
    "startTimeStr": "2023-03-30 00:00:00",
    "endTimeStr": "2023-03-31 00:00:00",
    "signature": "Udapf5Zc5fdx6r6G45u4uhYfAqXvt5ReXvKbza30579wfo8mYMBX5Hho7wHFV/NYoCB2eiGJeYd0MzjtdmPqVYyoWsPVaQEwQPuCPG3GIDI1MKYKxWGxMl+ylpsEPgM1v6rcmrGKXq3E6rZC8LuYnqDGA75aKuOa2mLZKARJQyE="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

|                  |                                         |                                                                               |
| ---------------- | --------------------------------------- | ----------------------------------------------------------------------------- |
| count            | <mark style="color:blue;">number</mark> | 投注成功的总次数                                                                      |
| totalBet         | <mark style="color:blue;">number</mark> | 投注成功的总额                                                                       |
| totalPayout      | <mark style="color:blue;">number</mark> | 派彩成功的总额                                                                       |
| totalWithholding | <mark style="color:blue;">number</mark> | 预扣成功的总额                                                                       |
| totalBalance     | <mark style="color:blue;">number</mark> | 盈余总额，计算公式( 投注 - 派彩 )                                                          |
| startTime        | <mark style="color:blue;">number</mark> | 查询的开始时间。以毫秒为单位。格式为Unix Time。                                                  |
| endTime          | <mark style="color:blue;">number</mark> | 查询的结束时间。以毫秒为单位。格式为Unix Time。                                                  |
| remainingVisits  | <mark style="color:blue;">number</mark> | 剩余请求数，每分钟500次。                                                                |
| status           | <mark style="color:blue;">number</mark> | 回应状态。[状态码表](../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma) |
| apiVersion       | <mark style="color:blue;">string</mark> | API版本号。                                                                       |

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "count": 112,
    "totalBet": 2200,
    "totalPayout": 3416.75,
    "totalWithholding": 100.8,
    "totalBalance": 1115.95,
    "startTime": 1680105600000,
    "endTime": 1680192000000,
    "remainingVisits": 499,
    "status": 200,
    "apiVersion": "1.5.94"
}
```
{% endcode %}
