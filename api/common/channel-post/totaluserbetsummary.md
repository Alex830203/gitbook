---
description: 查询时间段内每个玩家在每个游戏中的总计报告
---

# totaluserbetsummary

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数                                           | 格式                                       | 描述                                                  |
| -------------------------------------------- | ---------------------------------------- | --------------------------------------------------- |
| <mark style="color:red;">channelId</mark>    | <mark style="color:blue;">number</mark>  | 渠道ID                                                |
| <mark style="color:red;">timestamp</mark>    | <mark style="color:blue;">number</mark>  | 时间戳记。以毫秒为单位。格式为Unix Time。                           |
| <mark style="color:red;">pageNum</mark>      | <mark style="color:blue;">number</mark>  | 页码。                                                 |
| <mark style="color:red;">pageSize</mark>     | <mark style="color:blue;">number</mark>  | 每页上显示的记录数。 默认值为10。最大为5000。                          |
| <mark style="color:red;">startTimeStr</mark> | <mark style="color:blue;">string</mark>  | 查询时间范围的开始。                                          |
| <mark style="color:red;">endTimeStr</mark>   | <mark style="color:blue;">string</mark>  | 查询时间范围的结束。                                          |
| <mark style="color:red;">signature</mark>    | <mark style="color:blue;">string</mark>  | 签名。 字串拼接：channelId+timestamp                        |
| subChannelId                                 | <mark style="color:blue;">number</mark>  | 子渠道ID                                               |
| judgeTime                                    | <mark style="color:blue;">number</mark>  | 判断查询时间。默认为0                                         |
| isMerge                                      | <mark style="color:blue;">boolean</mark> | <p>是否合并用户游戏报表。默认为false <br>false: 否 <br>true: 是</p> |

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% hint style="info" %}
<mark style="color:blue;">搜索期不能超过7天。</mark>
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

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>results</td><td><mark style="color:blue;">array</mark></td><td>记录。阵列值为物件，下表为物件参数说明。</td><td></td></tr><tr><td>remainingVisit</td><td><mark style="color:blue;">number</mark></td><td>剩余请求数，每分钟500次。</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr></tbody></table>

results

|          |                                         |                             |
| -------- | --------------------------------------- | --------------------------- |
| userName | <mark style="color:blue;">string</mark> | 用户名。预设使用小写和数字。不可使用http保留字元。 |
| games    | <mark style="color:blue;">array</mark>  | 游戏记录。阵列值为物件，下表为物件参数说明。      |

games

|                   |                                         |                      |
| ----------------- | --------------------------------------- | -------------------- |
| gameType          | <mark style="color:blue;">number</mark> | 游戏类型                 |
| gameName          | <mark style="color:blue;">string</mark> | 游戏名称                 |
| totalBet          | <mark style="color:blue;">number</mark> | 总投注                  |
| totalEffectiveBet | <mark style="color:blue;">number</mark> | 总有效投注                |
| totalPayout       | <mark style="color:blue;">number</mark> | 总派彩                  |
| totalBalance      | <mark style="color:blue;">number</mark> | 盈余总额，计算公式( 投注 - 派彩 ) |
| count             | <mark style="color:blue;">number</mark> | 总投注次数                |

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "results": [
        {
            "userName": "demo",
            "games": [
                {
                    "gameType": 1,
                    "gameName": "baccarat",
                    "totalBet": 1100,
                    "totalEffectiveBet": 1100,
                    "totalPayout": 2195,
                    "totalBalance": -1095,
                    "count": 2
                },
                {
                    "gameType": 30,
                    "gameName": "board game",
                    "totalBet": 100.8,
                    "totalEffectiveBet": 4.45,
                    "totalPayout": 99.25,
                    "totalBalance": 1.55,
                    "count": 5
                }
            ]
        },
        {
            "userName": "test",
            "games": [
                {
                    "gameType": 23,
                    "gameName": "fortune-wheel",
                    "totalBet": 440,
                    "totalEffectiveBet": 440,
                    "totalPayout": 437.5,
                    "totalBalance": 2.5,
                    "count": 44
                }
            ]
        }
    ],
    "remainingVisit": 499,
    "status": 200,
    "apiVersion": "1.5.94"
}
```
{% endcode %}
