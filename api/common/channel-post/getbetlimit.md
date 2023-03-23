---
description: 该API用于查询在特定时间段内记录的投注。
---

# getbetlimit

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道ID。</td><td>RegisterOrLoginReq</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>时间戳记。以毫秒为单位。格式为Unix Time。</td><td>1</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td><p>签名。 字串拼接：<code>username+timestamp</code></p><p>Note: 如API用户名参数非必要，可以单独使用timestamp</p></td><td>1</td></tr><tr><td><mark style="color:red;">betStatus</mark></td><td><mark style="color:blue;">number</mark></td><td><p>检查投注状态。默认为查询所有记录</p><p>0：仅查询失败的记录</p><p>1：仅查询成功的记录</p></td><td>apitest01</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。</td><td>password</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td>accessToken</td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">number</mark></td><td>子渠道ID。</td><td>1577808000</td></tr><tr><td>startTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的开始。</td><td>127.0.0.1</td></tr><tr><td>endTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的结束。</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>pageNum</td><td><mark style="color:blue;">number</mark></td><td>页码。 默认值为1。</td><td></td></tr><tr><td>pageSize</td><td><mark style="color:blue;">number</mark></td><td>每页上显示的记录数。默认值为10。最大为5000。</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号码。</td><td></td></tr><tr><td>gameType</td><td><mark style="color:blue;">number</mark></td><td><p>游戏类型。</p><p>1: 百家乐</p><p>2: 龙虎</p><p>3: 骰宝</p><p>4: 轮盘</p><p>5: 老虎机</p><p>8: 牛牛</p><p>23: 财富大转盘</p><p>24: 电子21点</p><p>25: 真人21点</p><p>27: 迷你游戏</p><p>30: 电子棋牌</p></td><td></td></tr><tr><td>judgeTime</td><td><mark style="color:blue;">number</mark></td><td>判断查询时间。预设为0</td><td></td></tr><tr><td>isSeparate</td><td><mark style="color:blue;">boolean</mark></td><td><p>betHistories的显示方式。默认为false。</p><p>true: 按确认的投注次数细分。</p><p>false: 根据付款记录显示。</p><p>Note: 该参数不会影响其他参数的计算。仍将根据付款数量进行处理。</p></td><td></td></tr></tbody></table>

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% hint style="info" %}
*   <mark style="color:blue;">由于数据量可能太大，建议带以下参数减少查询时间。</mark>

    <mark style="color:blue;">(startTimeStr, endTimeStr, pageNum, pageSize)</mark>
* <mark style="color:blue;">请带参数 betStatus:1 以查询成功的记录。</mark>
* <mark style="color:blue;">游戏预扣请参考withHoldingTotal。</mark>
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
    "timestamp": 1666503623,
    "pageNum": 1,
    "pageSize": 5000,
    "startTimeStr": "2022-10-23 00:00:00",
    "endTimeStr": "2022-10-24 00:00:00",
    "betStatus": 1,
    "signature": "L2P1ecTObuchdUrNlPE/Eg4d5XZ2FoN7J3ooxkXJpS21WnCaewvVDVXhhzG5fjDxwDPm0JtzFhMDJucyoRwpdzkYVvDHUoqTuANLPgmZp2O/jtWuzmefO7dEphE/kFuSF3TdxnlWpQNupCIIp+ssUIZdklt6KbJ4xyzPbuSXuyY="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>betHistories</td><td><mark style="color:orange;">array</mark></td><td>投注详情。阵列值为物件，下表为物件参数说明。</td><td>预设随机生成</td></tr><tr><td>count</td><td><mark style="color:blue;">number</mark></td><td>总数。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td>remainingVisits</td><td><mark style="color:blue;">number</mark></td><td>剩余请求数，每分钟500次。</td><td>200</td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>eBET回应状态。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>0
</code></pre></td></tr></tbody></table>

**betHistories**

{% tabs %}
{% tab title="百家乐" %}
| 参数                   | 格式                                        | 描述                                                         |
| -------------------- | ----------------------------------------- | ---------------------------------------------------------- |
| gameType             | <mark style="color:blue;">number</mark>   | <p>游戏类型。</p><p>1: 百家乐</p>                                  |
| gameName             | <mark style="color:blue;">string</mark>   | 游戏名称                                                       |
| betMap               | <mark style="color:orange;">array</mark>  | 投注详细信息。阵列值为物件，下表为物件参数说明。                                   |
| bet                  | <mark style="color:blue;">number</mark>   | 总投注额。                                                      |
| roundNo              | <mark style="color:blue;">string</mark>   | 牌局号码。                                                      |
| payout               | <mark style="color:blue;">number</mark>   | 总派彩金额。                                                     |
| payoutDetail         | <mark style="color:purple;">object</mark> | 每个投注项目的派彩金额。                                               |
| judgeResult          | <mark style="color:orange;">array</mark>  | 中奖奖项。                                                      |
| oddsMap              | <mark style="color:orange;">array</mark>  | <p>赔率。 </p><p>Noted:</p><p>1.仅派彩成功有此参数</p><p>2.赔率不含投注额</p> |
| playerCards          | <mark style="color:orange;">array</mark>  | 闲的开牌结果。                                                    |
| playerResult         | <mark style="color:blue;">number</mark>   | 闲家点数。                                                      |
| bankerCard           | <mark style="color:orange;">array</mark>  | 庄的开牌结果。                                                    |
| bankerResult         | <mark style="color:blue;">number</mark>   | 庄家点数。                                                      |
| payoutWithoutholding | <mark style="color:blue;">number</mark>   | 纯派彩总额。                                                     |
| createTime           | <mark style="color:blue;">number</mark>   | 下注时间。 以秒为单位。格式为Unix Time。                                  |
| payoutTime           | <mark style="color:blue;">number</mark>   | 派彩时间。 以秒为单位。格式为Unix Time。                                  |
| betHistoryId         | <mark style="color:blue;">string</mark>   | 投注记录ID。                                                    |
| validBet             | <mark style="color:blue;">number</mark>   | 有效投注。                                                      |
| rebateAmount         | <mark style="color:blue;">number</mark>   | 返水。                                                        |
| balance              | <mark style="color:blue;">number</mark>   | 盈余。                                                        |
| username             | <mark style="color:blue;">string</mark>   | 用户名。                                                       |
| userId               | <mark style="color:blue;">number</mark>   | 用户ID。                                                      |
| brokerageRequired    | <mark style="color:blue;">boolean</mark>  | 是否為免佣金百家乐。                                                 |
| platform             | <mark style="color:blue;">number</mark>   | 游戏平台。                                                      |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "betHistories": [
        {
            "gameType": 1,
            "gameName": "baccarat",
            "betMap": [
                {
                    "betType": 60,
                    "betMoney": 100
                },
                {
                    "betType": 66,
                    "betMoney": 100
                },
                {
                    "betType": 68,
                    "betMoney": 100
                },
                {
                    "betType": 88,
                    "betMoney": 100
                }
            ],
            "bet": 400,
            "roundNo": "BP1-230317095849",
            "payout": 2200,
            "payoutDetail": {
                "60": 100,
                "68": 900,
                "88": 1200
            },
            "judgeResult": [
                68,
                88,
                73,
                70,
                83,
                63
            ],
            "oddsMap": [
                {
                    "60": 1,
                    "66": 11,
                    "68": 8,
                    "88": 11
                }
            ],
            "playerCards": [
                46,
                41,
                38
            ],
            "playerResult": 4,
            "bankerCards": [
                31,
                18
            ],
            "bankerResult": 4,
            "payoutWithoutholding": 2200,
            "createTime": 1679018341,
            "payoutTime": 1679018369,
            "betHistoryId": "6413c9816e5b1749b4d24344",
            "validBet": 300,
            "rebateAmount": 0,
            "balance": 1800,
            "username": "demo",
            "userId": 67928407,
            "brokerageRequired": false,
            "platform": 2
        }
    ],
    "count": 1,
    "remainingVisits": 499,
    "status": 200,
    "apiVersion": "1.5.92"
}
```
{% endcode %}
{% endtab %}

{% tab title="龙虎" %}
| 参数                   | 格式                                        | 描述                                                         |
| -------------------- | ----------------------------------------- | ---------------------------------------------------------- |
| gameType             | <mark style="color:blue;">number</mark>   | <p>游戏类型。</p><p>2: 龙虎</p>                                   |
| gameName             | <mark style="color:blue;">string</mark>   | 游戏名称。                                                      |
| betMap               | <mark style="color:orange;">array</mark>  | 投注详细信息。阵列值为物件，下表为物件参数说明。                                   |
| bet                  | <mark style="color:blue;">number</mark>   | 总投注额。                                                      |
| roundNo              | <mark style="color:blue;">string</mark>   | 牌局号码。                                                      |
| payout               | <mark style="color:blue;">number</mark>   | 总派彩金额。                                                     |
| payoutDetail         | <mark style="color:purple;">object</mark> | 每个投注项目的派彩金额。                                               |
| judgeResult          | <mark style="color:orange;">array</mark>  | 中奖奖项。                                                      |
| oddsMap              | <mark style="color:orange;">array</mark>  | <p>赔率。 </p><p>Noted:</p><p>1.仅派彩成功有此参数</p><p>2.赔率不含投注额</p> |
| dragonCard           | <mark style="color:blue;">number</mark>   | 只有龙虎。 龙的开牌结果。                                              |
| tigerCard            | <mark style="color:blue;">number</mark>   | 只有龙虎。 虎的开牌结果。                                              |
| payoutWithoutholding | <mark style="color:blue;">number</mark>   | 纯派彩总额。                                                     |
| createTime           | <mark style="color:blue;">number</mark>   | 下注时间。 以秒为单位。格式为Unix Time。                                  |
| payoutTime           | <mark style="color:blue;">number</mark>   | 派彩时间。 以秒为单位。格式为Unix Time。                                  |
| betHistoryId         | <mark style="color:blue;">string</mark>   | 投注记录ID。                                                    |
| validBet             | <mark style="color:blue;">number</mark>   | 有效投注。                                                      |
| rebateAmount         | <mark style="color:blue;">number</mark>   | 返水。                                                        |
| balance              | <mark style="color:blue;">number</mark>   | 盈余。                                                        |
| username             | <mark style="color:blue;">string</mark>   | 用户名。                                                       |
| userId               | <mark style="color:blue;">number</mark>   | 用户ID。                                                      |
| platform             | <mark style="color:blue;">number</mark>   | 游戏平台。                                                      |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "betHistories": [
        {
            "gameType": 2,
            "gameName": "dragon-tiger",
            "betMap": [
                {
                    "betType": 10,
                    "betMoney": 100
                },
                {
                    "betType": 13,
                    "betMoney": 100
                },
                {
                    "betType": 14,
                    "betMoney": 100
                },
                {
                    "betType": 68,
                    "betMoney": 100
                }
            ],
            "bet": 400,
            "roundNo": "DP1-230317100220",
            "payout": 375,
            "payoutDetail": {
                "10": 200,
                "14": 175
            },
            "judgeResult": [
                10,
                12,
                14,
                16,
                18
            ],
            "oddsMap": [
                {
                    "10": 1,
                    "13": 1.05,
                    "14": 0.75,
                    "68": 8
                }
            ],
            "dragonCard": 44,
            "tigerCard": 3,
            "payoutWithoutholding": 375,
            "createTime": 1679018559,
            "payoutTime": 1679018576,
            "betHistoryId": "6413ca508010734995b129ac",
            "validBet": 400,
            "rebateAmount": 0,
            "balance": -25,
            "username": "demo",
            "userId": 67928407,
            "platform": 2
        }
    ],
    "count": 1,
    "remainingVisits": 499,
    "status": 200,
    "apiVersion": "1.5.92"
}
```
{% endcode %}
{% endtab %}

{% tab title="骰子游戏" %}
| 参数                   | 格式                                        | 描述                                                                    |
| -------------------- | ----------------------------------------- | --------------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">number</mark>   | <p>游戏类型。</p><p>3: 骰子游戏</p>                                            |
| gameName             | <mark style="color:blue;">string</mark>   | 游戏名称。                                                                 |
| betMap               | <mark style="color:orange;">array</mark>  | 投注详细信息。阵列值为物件，下表为物件参数说明。                                              |
| bet                  | <mark style="color:blue;">number</mark>   | 总投注额。                                                                 |
| roundNo              | <mark style="color:blue;">string</mark>   | 牌局号码。                                                                 |
| payout               | <mark style="color:blue;">number</mark>   | 总派彩金额。                                                                |
| payoutDetail         | <mark style="color:purple;">object</mark> | <p>每个投注项目的派彩金额。 </p><p>骰宝的155.156后面会带开出的骰子点数，例如"155:1,1,6": 100. </p> |
| judgeResult          | <mark style="color:orange;">array</mark>  | 中奖奖项。                                                                 |
| oddsMap              | <mark style="color:orange;">array</mark>  | <p>赔率。 </p><p>Noted:</p><p>1.仅派彩成功有此参数</p><p>2.赔率不含投注额</p>            |
| allDices             | <mark style="color:orange;">array</mark>  | 骰子点数。                                                                 |
| payoutWithoutholding | <mark style="color:blue;">number</mark>   | 纯派彩总额。                                                                |
| createTime           | <mark style="color:blue;">number</mark>   | 下注时间。 以秒为单位。格式为Unix Time。                                             |
| payoutTime           | <mark style="color:blue;">number</mark>   | 派彩时间。 以秒为单位。格式为Unix Time。                                             |
| betHistoryId         | <mark style="color:blue;">string</mark>   | 投注记录ID。                                                               |
| validBet             | <mark style="color:blue;">number</mark>   | 有效投注。                                                                 |
| rebateAmount         | <mark style="color:blue;">number</mark>   | 返水。                                                                   |
| balance              | <mark style="color:blue;">number</mark>   | 盈余。                                                                   |
| username             | <mark style="color:blue;">string</mark>   | 用户名。                                                                  |
| userId               | <mark style="color:blue;">number</mark>   | 用户ID。                                                                 |
| platform             | <mark style="color:blue;">number</mark>   | 游戏平台。                                                                 |
| maxPayout            | <mark style="color:blue;">number</mark>   | 最高赔付金额。                                                               |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "betHistories": [
        {
            "gameType": 3,
            "gameName": "sic-bo",
            "betMap": [
                {
                    "betType": 101,
                    "betMoney": 100
                },
                {
                    "betType": 102,
                    "betMoney": 100
                },
                {
                    "betType": 107,
                    "betMoney": 100
                },
                {
                    "betType": 113,
                    "betMoney": 100
                },
                {
                    "betType": 116,
                    "betMoney": 100
                },
                {
                    "betType": 126,
                    "betMoney": 100
                },
                {
                    "betType": 137,
                    "betMoney": 100
                },
                {
                    "betType": 153,
                    "betMoney": 100
                },
                {
                    "betDice": [
                        1,
                        1,
                        4
                    ],
                    "betType": 155,
                    "betMoney": 100
                },
                {
                    "betDice": [
                        2,
                        3,
                        5
                    ],
                    "betType": 156,
                    "betMoney": 100
                }
            ],
            "bet": 1000,
            "roundNo": "SL1-230317100905",
            "payout": 400,
            "payoutDetail": {
                "101": 200,
                "137": 200
            },
            "judgeResult": [
                121,
                141,
                142,
                149,
                134,
                136,
                137,
                103,
                101,
                156
            ],
            "oddsMap": [
                {
                    "101": 1,
                    "102": 1,
                    "107": 8,
                    "113": 150,
                    "116": 24,
                    "126": 6,
                    "137": 1,
                    "153": 5,
                    "155:1,1,4": 60,
                    "156:2,3,5": 30
                }
            ],
            "allDices": [
                1,
                3,
                4
            ],
            "payoutWithoutholding": 400,
            "createTime": 1679018960,
            "payoutTime": 1679018999,
            "betHistoryId": "6413cbf78010734995b12c2d",
            "validBet": 1000,
            "rebateAmount": 0,
            "balance": -600,
            "username": "demo",
            "userId": 67928407,
            "platform": 2
        },
        {
            "gameType": 3,
            "gameName": "hi-lo",
            "betMap": [
                {
                    "betType": 158,
                    "betMoney": 100
                },
                {
                    "betType": 159,
                    "betMoney": 100
                },
                {
                    "betType": 160,
                    "betMoney": 100
                },
                {
                    "betType": 161,
                    "betMoney": 100
                },
                {
                    "betType": 162,
                    "betMoney": 100
                },
                {
                    "betType": 163,
                    "betMoney": 100
                }
            ],
            "bet": 600,
            "roundNo": "SHL1-230317101342",
            "payout": 305,
            "payoutDetail": {
                "158": 108,
                "161": 197
            },
            "judgeResult": [
                103,
                158,
                161
            ],
            "oddsMap": [
                {
                    "158": 0.08,
                    "159": 3.7,
                    "160": 1.48,
                    "161": 0.97,
                    "162": 0.97,
                    "163": 1.48
                }
            ],
            "allDices": [
                1,
                2,
                5
            ],
            "payoutWithoutholding": 305,
            "createTime": 1679019236,
            "payoutTime": 1679019279,
            "betHistoryId": "6413cd0fdac6a449998d4f6f",
            "validBet": 600,
            "rebateAmount": 0,
            "balance": -295,
            "username": "demo",
            "userId": 67928407,
            "platform": 2,
            "maxPayout": 146480000
        }
    ],
    "count": 2,
    "remainingVisits": 499,
    "status": 200,
    "apiVersion": "1.5.92"
}
```
{% endcode %}
{% endtab %}

{% tab title="轮盘" %}
| 参数                   | 格式                                        | 描述                                                                                                             |
| -------------------- | ----------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">number</mark>   | <p>游戏类型。</p><p>4: 轮盘</p>                                                                                       |
| gameName             | <mark style="color:blue;">string</mark>   | 游戏名称。                                                                                                          |
| betMap               | <mark style="color:orange;">array</mark>  | 投注详细信息。                                                                                                        |
| bet                  | <mark style="color:blue;">number</mark>   | 总投注额。                                                                                                          |
| roundNo              | <mark style="color:blue;">string</mark>   | 牌局号码。                                                                                                          |
| payout               | <mark style="color:blue;">number</mark>   | 总派彩金额。                                                                                                         |
| payoutDetail         | <mark style="color:purple;">object</mark> | <p>每个投注项目的派彩金额。 </p><p>轮盘名称后面会携带该局的点数或betTypeInterval的參數，例如"200:17": 3600, "207:1": 300, "201:14,17": 1800</p> |
| judgeResult          | <mark style="color:orange;">array</mark>  | 中奖奖项。                                                                                                          |
| oddsMap              | <mark style="color:orange;">array</mark>  | <p>赔率。 </p><p>Noted:</p><p>1.仅派彩成功有此参数</p><p>2.赔率不含投注额</p>                                                     |
| number               | <mark style="color:blue;">number</mark>   | 结果号码。                                                                                                          |
| payoutWithoutholding | <mark style="color:blue;">number</mark>   | 纯派彩总额。                                                                                                         |
| createTime           | <mark style="color:blue;">number</mark>   | 下注时间。 以秒为单位。格式为Unix Time。                                                                                      |
| payoutTime           | <mark style="color:blue;">number</mark>   | 派彩时间。 以秒为单位。格式为Unix Time。                                                                                      |
| betHistoryId         | <mark style="color:blue;">string</mark>   | 投注记录ID。                                                                                                        |
| validBet             | <mark style="color:blue;">number</mark>   | 有效投注。                                                                                                          |
| rebateAmount         | <mark style="color:blue;">number</mark>   | 返水。                                                                                                            |
| balance              | <mark style="color:blue;">number</mark>   | 盈余。                                                                                                            |
| username             | <mark style="color:blue;">string</mark>   | 用户名。                                                                                                           |
| userId               | <mark style="color:blue;">number</mark>   | 用户ID。                                                                                                          |
| platform             | <mark style="color:blue;">number</mark>   | 游戏平台。                                                                                                          |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "betHistories": [
        {
            "gameType": 4,
            "gameName": "roulette",
            "betMap": [
                {
                    "betNumber": [
                        0,
                        1,
                        2,
                        3
                    ],
                    "betType": 205,
                    "betMoney": 10
                },
                {
                    "betNumber": [
                        1,
                        3,
                        5,
                        7,
                        9,
                        12,
                        14,
                        16,
                        18,
                        19,
                        21,
                        23,
                        25,
                        27,
                        30,
                        32,
                        34,
                        36
                    ],
                    "betType": 209,
                    "betMoney": 10
                },
                {
                    "betNumber": [
                        1,
                        3,
                        5,
                        7,
                        9,
                        11,
                        13,
                        15,
                        17,
                        19,
                        21,
                        23,
                        25,
                        27,
                        29,
                        31,
                        33,
                        35
                    ],
                    "betType": 211,
                    "betMoney": 10
                },
                {
                    "betNumber": [
                        1,
                        2,
                        3,
                        4,
                        5,
                        6,
                        7,
                        8,
                        9,
                        10,
                        11,
                        12,
                        13,
                        14,
                        15,
                        16,
                        17,
                        18
                    ],
                    "betType": 214,
                    "betMoney": 10
                },
                {
                    "betNumber": [
                        3
                    ],
                    "betType": 200,
                    "betMoney": 10
                },
                {
                    "betNumber": [
                        2,
                        3
                    ],
                    "betType": 201,
                    "betMoney": 10
                },
                {
                    "betNumber": [
                        0,
                        2,
                        3
                    ],
                    "betType": 204,
                    "betMoney": 10
                },
                {
                    "betTypeInterval": "0",
                    "betNumber": [
                        1,
                        2,
                        3
                    ],
                    "betType": 202,
                    "betMoney": 10
                },
                {
                    "betTypeInterval": "0,1",
                    "betNumber": [
                        2,
                        3,
                        5,
                        6
                    ],
                    "betType": 203,
                    "betMoney": 10
                },
                {
                    "betTypeInterval": "0",
                    "betNumber": [
                        1,
                        2,
                        3,
                        4,
                        5,
                        6
                    ],
                    "betType": 206,
                    "betMoney": 10
                },
                {
                    "betTypeInterval": "2",
                    "betNumber": [
                        3,
                        6,
                        9,
                        12,
                        15,
                        18,
                        21,
                        24,
                        27,
                        30,
                        33,
                        36
                    ],
                    "betType": 207,
                    "betMoney": 10
                },
                {
                    "betTypeInterval": "0",
                    "betNumber": [
                        1,
                        2,
                        3,
                        4,
                        5,
                        6,
                        7,
                        8,
                        9,
                        10,
                        11,
                        12
                    ],
                    "betType": 208,
                    "betMoney": 10
                }
            ],
            "bet": 120,
            "roundNo": "RP1-230317102639",
            "payout": 360,
            "payoutDetail": {
                "205": 90,
                "209": 20,
                "211": 20,
                "214": 20,
                "202:0": 120,
                "206:0": 60,
                "208:0": 30
            },
            "judgeResult": [
                200,
                205,
                214,
                211,
                209,
                202,
                207,
                206,
                203,
                208,
                201,
                201,
                201,
                204
            ],
            "oddsMap": [
                {
                    "205": 8,
                    "209": 1,
                    "211": 1,
                    "214": 1,
                    "200:3": 35,
                    "201:2,3": 17,
                    "204:0,2,3": 11,
                    "202:0": 11,
                    "203:0,1": 8,
                    "206:0": 5,
                    "207:2": 2,
                    "208:0": 2
                }
            ],
            "number": 1,
            "payoutWithoutholding": 360,
            "createTime": 1679020011,
            "payoutTime": 1679020060,
            "betHistoryId": "6413d01c8010734995b133fd",
            "validBet": 120,
            "rebateAmount": 0,
            "balance": 240,
            "username": "demo",
            "userId": 67928407,
            "platform": 2
        },
        {
            "gameType": 4,
            "gameName": "fortune roulette",
            "betMap": [
                {
                    "betNumber": [
                        7
                    ],
                    "betType": 200,
                    "betMoney": 100
                },
                {
                    "betNumber": [
                        8
                    ],
                    "betType": 200,
                    "betMoney": 100
                },
                {
                    "betNumber": [
                        14
                    ],
                    "betType": 200,
                    "betMoney": 100
                },
                {
                    "betNumber": [
                        16
                    ],
                    "betType": 200,
                    "betMoney": 100
                },
                {
                    "betNumber": [
                        21
                    ],
                    "betType": 200,
                    "betMoney": 100
                },
                {
                    "betNumber": [
                        24
                    ],
                    "betType": 200,
                    "betMoney": 100
                },
                {
                    "betNumber": [
                        28
                    ],
                    "betType": 200,
                    "betMoney": 100
                },
                {
                    "betNumber": [
                        32
                    ],
                    "betType": 200,
                    "betMoney": 100
                },
                {
                    "betNumber": [
                        35
                    ],
                    "betType": 200,
                    "betMoney": 100
                }
            ],
            "bet": 900,
            "roundNo": "RC1-230317103900",
            "payout": 3100,
            "payoutDetail": {
                "200:16": 3100
            },
            "judgeResult": [
                200,
                214,
                212,
                209,
                202,
                207,
                206,
                206,
                203,
                203,
                208,
                201,
                201,
                201
            ],
            "oddsMap": [
                {
                    "200:7": 30,
                    "200:8": 30,
                    "200:14": 30,
                    "200:16": 30,
                    "200:21": 30,
                    "200:24": 30,
                    "200:28": 30,
                    "200:32": 30,
                    "200:35": 30
                }
            ],
            "number": 16,
            "payoutWithoutholding": 3100,
            "createTime": 1679020764,
            "payoutTime": 1679020788,
            "betHistoryId": "6413d2f4664e7849ae150b53",
            "validBet": 900,
            "rebateAmount": 0,
            "balance": 2200,
            "username": "demo",
            "userId": 67928407,
            "platform": 2
        }
    ],
    "count": 2,
    "remainingVisits": 499,
    "status": 200,
    "apiVersion": "1.5.92"
}
```
{% endcode %}
{% endtab %}

{% tab title="老虎机" %}
| 参数                   | 格式                                        | 描述                                                           |
| -------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| gameType             | <mark style="color:blue;">number</mark>   | <p>游戏类型。</p><p>5: 老虎机</p>                                    |
| gameName             | <mark style="color:blue;">string</mark>   | 游戏的gameID                                                    |
| betMap               | <mark style="color:orange;">array</mark>  | 投注详细信息。                                                      |
| bet                  | <mark style="color:blue;">number</mark>   | 总投注额。                                                        |
| roundNo              | <mark style="color:blue;">string</mark>   | 牌局号码。                                                        |
| payout               | <mark style="color:blue;">double</mark>   | 总派彩金额。                                                       |
| payoutDetail         | <mark style="color:purple;">object</mark> | 每个投注项目的派彩金额。                                                 |
| oddsMap              | <mark style="color:orange;">array</mark>  | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p> |
| payoutWithoutholding | <mark style="color:blue;">number</mark>   | 纯派彩总额。                                                       |
| createTime           | <mark style="color:blue;">number</mark>   | 下注时间。 以秒为单位。格式为Unix Time。                                    |
| payoutTime           | <mark style="color:blue;">number</mark>   | 派彩时间。 以秒为单位。格式为Unix Time。                                    |
| betHistoryId         | <mark style="color:blue;">string</mark>   | 投注记录ID。                                                      |
| validBet             | <mark style="color:blue;">number</mark>   | 有效投注。                                                        |
| rebateAmount         | <mark style="color:blue;">number</mark>   | 返水。                                                          |
| balance              | <mark style="color:blue;">number</mark>   | 盈余。                                                          |
| username             | <mark style="color:blue;">string</mark>   | 用户名。 不可使用http保留字元。                                           |
| userId               | <mark style="color:blue;">number</mark>   | 用户ID。                                                        |
| providerId           | <mark style="color:blue;">string</mark>   | 游戏供应商ID。仅电子类游戏有此参数。                                          |
| platform             | <mark style="color:blue;">number</mark>   | 游戏平台。                                                        |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "betHistories": [
        {
            "gameType": 5,
            "gameName": "WHG-0020",
            "betMap": [
                {
                    "betType": 601,
                    "betMoney": 5
                }
            ],
            "bet": 5,
            "roundNo": "gn-49c4c0e6-8de4-41df-b988-244e843e4856",
            "payout": 7.5,
            "payoutDetail": {
                "601-0": 7.5
            },
            "oddsMap": [
                {}
            ],
            "payoutWithoutholding": 7.5,
            "createTime": 1666665278,
            "payoutTime": 1666665288,
            "betHistoryId": "63574b489b4ad40035090bb5",
            "validBet": 5,
            "rebateAmount": 0,
            "balance": 2.5,
            "username": "demo",
            "userId": 67928964,
            "platform": 3
        }
    ],
    "count": 1,
    "remainingVisits": 499,
    "status": 200,
    "apiVersion": "1.5.75"
}
```
{% endcode %}
{% endtab %}

{% tab title="财富大转盘" %}
| 参数                   | 格式                                        | 描述                                                         |
| -------------------- | ----------------------------------------- | ---------------------------------------------------------- |
| gameType             | <mark style="color:blue;">number</mark>   | <p>游戏类型。</p><p>23: 财富大转盘</p>                               |
| gameName             | <mark style="color:blue;">string</mark>   | 游戏名称。                                                      |
| betMap               | <mark style="color:orange;">array</mark>  | 投注详细信息。                                                    |
| bet                  | <mark style="color:blue;">number</mark>   | 总投注额。                                                      |
| roundNo              | <mark style="color:blue;">string</mark>   | 牌局号码。                                                      |
| payout               | <mark style="color:blue;">number</mark>   | 总派彩金额。                                                     |
| payoutDetail         | <mark style="color:purple;">object</mark> | 每个投注项目的派彩金额。                                               |
| judgeResult          | <mark style="color:orange;">array</mark>  | 中奖奖项。                                                      |
| oddsMap              | <mark style="color:orange;">array</mark>  | <p>赔率。 </p><p>Noted:</p><p>1.仅派彩成功有此参数</p><p>2.赔率不含投注额</p> |
| maxPayout            | <mark style="color:blue;">number</mark>   | 只有财富大转盘。 最高赔付金额。                                           |
| payoutWithoutholding | <mark style="color:blue;">number</mark>   | 纯派彩总额。                                                     |
| createTime           | <mark style="color:blue;">number</mark>   | 下注时间。 以秒为单位。格式为Unix Time。                                  |
| payoutTime           | <mark style="color:blue;">number</mark>   | 派彩时间。 以秒为单位。格式为Unix Time。                                  |
| betHistoryId         | <mark style="color:blue;">string</mark>   | 投注记录ID。                                                    |
| validBet             | <mark style="color:blue;">number</mark>   | 有效投注。                                                      |
| rebateAmount         | <mark style="color:blue;">number</mark>   | 返水。                                                        |
| balance              | <mark style="color:blue;">number</mark>   | 盈余。                                                        |
| username             | <mark style="color:blue;">string</mark>   | 用户名。                                                       |
| userId               | <mark style="color:blue;">number</mark>   | 用户ID。                                                      |
| platform             | <mark style="color:blue;">number</mark>   | 游戏平台。                                                      |
| maxPayout            | <mark style="color:blue;">number</mark>   | 最高赔付金额。                                                    |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "betHistories": [
        {
            "gameType": 23,
            "gameName": "fortune-wheel",
            "betMap": [
                {
                    "betType": 400,
                    "betMoney": 100
                },
                {
                    "betType": 401,
                    "betMoney": 100
                },
                {
                    "betType": 402,
                    "betMoney": 100
                },
                {
                    "betType": 403,
                    "betMoney": 100
                },
                {
                    "betType": 404,
                    "betMoney": 100
                },
                {
                    "betType": 405,
                    "betMoney": 100
                },
                {
                    "betType": 406,
                    "betMoney": 100
                },
                {
                    "betType": 407,
                    "betMoney": 100
                },
                {
                    "betType": 408,
                    "betMoney": 100
                }
            ],
            "bet": 900,
            "roundNo": "CW1-230317104758",
            "payout": 375,
            "payoutDetail": {
                "400": 200,
                "407": 175
            },
            "judgeResult": [
                407,
                400
            ],
            "oddsMap": [
                {
                    "400": 1,
                    "401": 2,
                    "402": 5,
                    "403": 10,
                    "404": 20,
                    "405": 40,
                    "406": 25,
                    "407": 0.75,
                    "408": 1.25
                }
            ],
            "payoutWithoutholding": 375,
            "createTime": 1679021286,
            "payoutTime": 1679021363,
            "betHistoryId": "6413d533664e7849ae1510e1",
            "validBet": 900,
            "rebateAmount": 0,
            "balance": -525,
            "username": "demo",
            "userId": 67928407,
            "platform": 2,
            "maxPayout": 1000000
        }
    ],
    "count": 1,
    "remainingVisits": 499,
    "status": 200,
    "apiVersion": "1.5.92"
}
```
{% endcode %}
{% endtab %}

{% tab title="电子21点" %}
| 参数                   | 格式                                        | 描述                                                              |
| -------------------- | ----------------------------------------- | --------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">number</mark>   | <p>游戏类型。</p><p>24: 电子21点</p>                                    |
| gameName             | <mark style="color:blue;">string</mark>   | 游戏名称。                                                           |
| betMap               | <mark style="color:orange;">array</mark>  | 投注详细信息。                                                         |
| bet                  | <mark style="color:blue;">number</mark>   | 总投注额。                                                           |
| roundNo              | <mark style="color:blue;">string</mark>   | 牌局号码。                                                           |
| payout               | <mark style="color:blue;">number</mark>   | 总派彩金额。                                                          |
| payoutDetail         | <mark style="color:purple;">object</mark> | 每个投注项目的派彩金额。                                                    |
| judgeResult          | <mark style="color:orange;">array</mark>  | 中奖奖项。                                                           |
| oddsMap              | <mark style="color:orange;">array</mark>  | <p>赔率。 </p><p>Noted: </p><p>1.电子类游戏仅显示空值 </p><p>2.仅派彩成功有此参数</p> |
| surrender            | <mark style="color:blue;">number</mark>   | 投降派彩(只有21点才會有此参数)                                               |
| payoutWithoutholding | <mark style="color:blue;">number</mark>   | 纯派彩总额。                                                          |
| createTime           | <mark style="color:blue;">number</mark>   | 下注时间。 以秒为单位。格式为Unix Time。                                       |
| payoutTime           | <mark style="color:blue;">number</mark>   | 派彩时间。 以秒为单位。格式为Unix Time。                                       |
| betHistoryId         | <mark style="color:blue;">string</mark>   | 投注记录ID。                                                         |
| validBet             | <mark style="color:blue;">number</mark>   | 有效投注。                                                           |
| rebateAmount         | <mark style="color:blue;">number</mark>   | 返水。                                                             |
| balance              | <mark style="color:blue;">number</mark>   | 盈余。                                                             |
| username             | <mark style="color:blue;">string</mark>   | 用户名。                                                            |
| userId               | <mark style="color:blue;">number</mark>   | 用户ID。                                                           |
| platform             | <mark style="color:blue;">number</mark>   | 游戏平台。                                                           |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "betHistories": [
        {
            "gameType": 24,
            "gameName": "black_jack_electronic",
            "betMap": [
                {
                    "betType": 6051,
                    "betMoney": 100
                }
            ],
            "bet": 100,
            "roundNo": "J154-4J1543FE086413D5FE001",
            "payout": 200,
            "payoutDetail": {
                "6051": 200
            },
            "judgeResult": [
                801,
                601162,
                602162,
                6031,
                604162,
                6051,
                6061,
                6071
            ],
            "oddsMap": [
                {}
            ],
            "payoutWithoutholding": 200,
            "createTime": 1679021568,
            "payoutTime": 1679021623,
            "betHistoryId": "6413d6375ade3e003a1155e5",
            "validBet": 100,
            "rebateAmount": 0,
            "balance": 100,
            "username": "demo",
            "userId": 67928407,
            "platform": 2
        }
    ],
    "count": 1,
    "remainingVisits": 499,
    "status": 200,
    "apiVersion": "1.5.92"
}
```
{% endcode %}
{% endtab %}

{% tab title="真人21点" %}
| 参数                   | 格式                                        | 描述                                                                                                              |
| -------------------- | ----------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">number</mark>   | <p>游戏类型。</p><p>25: 真人21点</p>                                                                                    |
| gameName             | <mark style="color:blue;">string</mark>   | 游戏名称。                                                                                                           |
| betMap               | <mark style="color:orange;">array</mark>  | 投注详细信息。                                                                                                         |
| bet                  | <mark style="color:blue;">number</mark>   | 总投注额。                                                                                                           |
| roundNo              | <mark style="color:blue;">string</mark>   | 牌局号码。                                                                                                           |
| payout               | <mark style="color:blue;">number</mark>   | 总派彩金额。                                                                                                          |
| payoutDetail         | <mark style="color:purple;">object</mark> | 每个投注项目的派彩金额。                                                                                                    |
| judgeResult          | <mark style="color:orange;">array</mark>  | 中奖奖项。                                                                                                           |
| oddsMap              | <mark style="color:orange;">array</mark>  | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额赔率。 </p><p>Noted:</p><p>1.仅派彩成功有此参数</p><p>2.赔率不含投注额</p> |
| surrender            | <mark style="color:blue;">number</mark>   | 投降派彩(只有21点才會有此参数)                                                                                               |
| payoutWithoutholding | <mark style="color:blue;">number</mark>   | 纯派彩总额。                                                                                                          |
| createTime           | <mark style="color:blue;">number</mark>   | 下注时间。 以秒为单位。格式为Unix Time。                                                                                       |
| payoutTime           | <mark style="color:blue;">number</mark>   | 派彩时间。 以秒为单位。格式为Unix Time。                                                                                       |
| betHistoryId         | <mark style="color:blue;">string</mark>   | 投注记录ID。                                                                                                         |
| validBet             | <mark style="color:blue;">number</mark>   | 有效投注。                                                                                                           |
| rebateAmount         | <mark style="color:blue;">number</mark>   | 返水。                                                                                                             |
| balance              | <mark style="color:blue;">number</mark>   | 盈余。                                                                                                             |
| username             | <mark style="color:blue;">string</mark>   | 用户名。 不可使用http保留字元。                                                                                              |
| userId               | <mark style="color:blue;">number</mark>   | 用户ID。                                                                                                           |
| platform             | <mark style="color:blue;">number</mark>   | 游戏平台。                                                                                                           |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "betHistories": [
        {
            "gameType": 25,
            "gameName": "black_jack_live",
            "betMap": [
                {
                    "betType": 6021,
                    "betMoney": 10
                },
                {
                    "betType": 6031,
                    "betMoney": 10
                },
                {
                    "betType": 60301,
                    "betMoney": 10
                },
                {
                    "betType": 60302,
                    "betMoney": 10
                }
            ],
            "bet": 40,
            "roundNo": "J001-4J001314486413D534811",
            "payout": 35,
            "payoutDetail": {
                "6021": 10,
                "6031": 25,
                "60301": 0,
                "60302": 0
            },
            "judgeResult": [
                601013,
                801,
                601162,
                604011,
                604162,
                6071,
                8068,
                602168,
                6031
            ],
            "oddsMap": [
                {}
            ],
            "payoutWithoutholding": 35,
            "createTime": 1679021375,
            "payoutTime": 1679021480,
            "betHistoryId": "6413d5a85ade3e003a115327",
            "validBet": 30,
            "rebateAmount": 0,
            "balance": -5,
            "username": "demo",
            "userId": 67928407,
            "platform": 2
        }
    ],
    "count": 1,
    "remainingVisits": 499,
    "status": 200,
    "apiVersion": "1.5.92"
}
```
{% endcode %}
{% endtab %}

{% tab title="迷你游戏" %}
| 参数                   | 格式                                        | 描述                                                           |
| -------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| gameType             | <mark style="color:blue;">number</mark>   | <p>游戏类型。</p><p>27: 迷你游戏</p>                                  |
| gameName             | <mark style="color:blue;">string</mark>   | 游戏的gameID                                                    |
| betMap               | <mark style="color:orange;">array</mark>  | 投注详细信息。                                                      |
| bet                  | <mark style="color:blue;">number</mark>   | 总投注额。                                                        |
| roundNo              | <mark style="color:blue;">string</mark>   | 牌局号码。                                                        |
| payout               | <mark style="color:blue;">number</mark>   | 总派彩金额。                                                       |
| payoutDetail         | <mark style="color:purple;">object</mark> | 每个投注项目的派彩金额。                                                 |
| oddsMap              | <mark style="color:orange;">array</mark>  | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p> |
| payoutWithoutholding | <mark style="color:blue;">number</mark>   | 纯派彩总额。                                                       |
| createTime           | <mark style="color:blue;">number</mark>   | 下注时间。 以秒为单位。格式为Unix Time。                                    |
| payoutTime           | <mark style="color:blue;">number</mark>   | 派彩时间。 以秒为单位。格式为Unix Time。                                    |
| betHistoryId         | <mark style="color:blue;">string</mark>   | 投注记录ID。                                                      |
| validBet             | <mark style="color:blue;">number</mark>   | 有效投注。                                                        |
| rebateAmount         | <mark style="color:blue;">number</mark>   | 返水。                                                          |
| balance              | <mark style="color:blue;">number</mark>   | 盈余。                                                          |
| username             | <mark style="color:blue;">string</mark>   | 用户名。 不可使用http保留字元。                                           |
| userId               | <mark style="color:blue;">number</mark>   | 用户ID。                                                        |
| providerId           | <mark style="color:blue;">string</mark>   |                                                              |
| platform             | <mark style="color:blue;">number</mark>   | 游戏平台。                                                        |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "betHistories": [
        {
            "gameType": 27,
            "gameName": "poker",
            "betMap": [
                {
                    "betType": 601,
                    "betMoney": 1
                }
            ],
            "bet": 1,
            "roundNo": "wy-2_6007785_2717c004c6",
            "payout": 1.5,
            "payoutDetail": {
                "601-0": 1.5
            },
            "oddsMap": [
                {
                    "601-0": 1.5029
                }
            ],
            "payoutWithoutholding": 1.5,
            "createTime": 1679021846,
            "payoutTime": 1679021856,
            "betHistoryId": "6413d7201449810040e8cf72",
            "validBet": 1,
            "rebateAmount": 0,
            "balance": 0.5,
            "username": "demo",
            "userId": 67928407,
            "providerId": "wayi",
            "platform": 1
        }
    ],
    "count": 1,
    "remainingVisits": 499,
    "status": 200,
    "apiVersion": "1.5.92"
}
```
{% endcode %}
{% endtab %}

{% tab title="电子棋牌" %}
| 参数                   | 格式                                        | 描述                                                                                                                  |
| -------------------- | ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">number</mark>   | <p>游戏类型。</p><p>30</p>                                                                                               |
| gameName             | <mark style="color:blue;">string</mark>   | 游戏的gameID                                                                                                           |
| betMap               | <mark style="color:orange;">array</mark>  | 投注详细信息。                                                                                                             |
| bet                  | <mark style="color:blue;">number</mark>   | 总投注额。                                                                                                               |
| roundNo              | <mark style="color:blue;">string</mark>   | 牌局号码。                                                                                                               |
| payout               | <mark style="color:blue;">number</mark>   | 总派彩金额。                                                                                                              |
| payoutDetail         | <mark style="color:purple;">object</mark> | 每个投注项目的派彩金额。                                                                                                        |
| oddsMap              | <mark style="color:orange;">array</mark>  | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p>                                                        |
| withHoldingTotal     | <mark style="color:blue;">number</mark>   | 预扣总额。                                                                                                               |
| withHoldingDetail    | <mark style="color:purple;">object</mark> | 预扣细节。                                                                                                               |
| payoutWithoutholding | <mark style="color:blue;">number</mark>   | <p>纯派彩总额。</p><p>如果没有预扣金额，则参数值将与派彩相同。 如果有预扣金额，则计算公式为payout-withholdingtotal。</p><p>如果参数值大于0，则玩家获胜；如果参数值等于0是玩家输钱。</p> |
| createTime           | <mark style="color:blue;">number</mark>   | 下注时间。 以秒为单位。格式为Unix Time。                                                                                           |
| payoutTime           | <mark style="color:blue;">number</mark>   | 派彩时间。 以秒为单位。格式为Unix Time。                                                                                           |
| betHistoryId         | <mark style="color:blue;">string</mark>   | 投注记录ID。                                                                                                             |
| validBet             | <mark style="color:blue;">number</mark>   | 有效投注。                                                                                                               |
| rebateAmount         | <mark style="color:blue;">number</mark>   | 返水。                                                                                                                 |
| balance              | <mark style="color:blue;">number</mark>   | 盈余。                                                                                                                 |
| username             | <mark style="color:blue;">string</mark>   | 用户名。                                                                                                                |
| userId               | <mark style="color:blue;">number</mark>   | 用户ID。                                                                                                               |
| providerId           | <mark style="color:blue;">string</mark>   | 游戏供应商ID                                                                                                             |
| platform             | <mark style="color:blue;">number</mark>   | 游戏平台。                                                                                                               |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "betHistories": [
        {
            "gameType": 30,
            "gameName": "pokdeng",
            "betMap": [],
            "bet": 0,
            "roundNo": "wg-pd985_2717bfb7fe",
            "payout": 3084,
            "payoutDetail": {
                "602-0": 3084
            },
            "oddsMap": [
                {}
            ],
            "withHoldingTotal": 3100,
            "withHoldingDetail": {
                "602-0": 3100
            },
            "payoutWithoutholding": 0,
            "createTime": 1679021654,
            "payoutTime": 1679021683,
            "betHistoryId": "6413d6738e1bd4002b6aaf30",
            "validBet": 16,
            "rebateAmount": 0,
            "balance": -16,
            "username": "demo",
            "userId": 67928407,
            "providerId": "wayigame",
            "platform": 1
        },
        {
            "gameType": 30,
            "gameName": "texas",
            "betMap": [],
            "bet": 0,
            "roundNo": "wg-texas021_2717bfd13b",
            "payout": 222.35,
            "payoutDetail": {
                "601-0": 222.35
            },
            "oddsMap": [
                {}
            ],
            "withHoldingTotal": 200,
            "withHoldingDetail": {
                "601-0": 200
            },
            "payoutWithoutholding": 22.35,
            "createTime": 1679021714,
            "payoutTime": 1679021788,
            "betHistoryId": "6413d6dcd7b9f60019333b40",
            "validBet": 22.35,
            "rebateAmount": 0,
            "balance": 22.35,
            "username": "demo",
            "userId": 67928407,
            "providerId": "wayigame",
            "platform": 1
        }
    ],
    "count": 1,
    "remainingVisits": 499,
    "status": 200,
    "apiVersion": "1.5.92"
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
