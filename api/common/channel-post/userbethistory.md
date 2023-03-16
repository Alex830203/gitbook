---
description: 该API用于查询在特定时间段内记录的投注。
---

# userbethistory

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">int</mark></td><td>渠道ID。</td><td>RegisterOrLoginReq</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">int($int64)</mark></td><td>时间戳记。以毫秒为单位。格式为Unix Time。</td><td>1</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td><p>签名。 字串拼接：<code>username+timestamp</code></p><p>Note: 如API用户名参数非必要，可以单独使用timestamp</p></td><td>1</td></tr><tr><td><mark style="color:red;">betStatus</mark></td><td><mark style="color:blue;">int</mark></td><td><p>检查投注状态。默认为查询所有记录</p><p>0：仅查询失败的记录</p><p>1：仅查询成功的记录</p></td><td>apitest01</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。 不可使用http保留字元。</td><td>password</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td>accessToken</td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">int</mark></td><td>子渠道ID。</td><td>1577808000</td></tr><tr><td>startTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的开始。</td><td>127.0.0.1</td></tr><tr><td>endTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的结束。</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>pageNum</td><td><mark style="color:blue;">int</mark></td><td>页码。 默认值为1。</td><td></td></tr><tr><td>pageSize</td><td><mark style="color:blue;">int</mark></td><td><p>每页上显示的记录数。</p><p>默认值为10。最大为5000。</p></td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号码。</td><td></td></tr><tr><td>gameType</td><td><mark style="color:blue;">int</mark></td><td><p>游戏类型。</p><p>1: 百家乐</p><p>2: 龙虎</p><p>3: 骰宝</p><p>4: 轮盘</p><p>5: 老虎机</p><p>8: 牛牛</p><p>23: 财富大转盘</p><p>24: 电子21点</p><p>25: 真人21点</p><p>27: 迷你游戏</p><p>30: 电子棋牌</p></td><td></td></tr><tr><td>judgeTime</td><td><mark style="color:blue;">int</mark></td><td><p>判断查询时间。</p><p>预设为0</p><p>0：派彩时间</p><p>1：下注时间</p></td><td></td></tr><tr><td>isSeparate</td><td><mark style="color:blue;">boolean</mark></td><td><p>betHistories的显示方式。默认为false。</p><p>true: 按确认的投注次数细分。</p><p>false: 根据付款记录显示。</p><p>Note: 该参数不会影响其他参数的计算。仍将根据付款数量进行处理。</p></td><td></td></tr></tbody></table>

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

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td><mark style="color:blue;">int</mark></td><td>渠道返回的accessToken。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>子渠道 ID。 如果未创建，请输入0。</td><td><pre><code>0
</code></pre></td></tr><tr><td>count</td><td><mark style="color:blue;">int</mark></td><td>用户名。不可使用http保留字元。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td>remainingVisits</td><td><mark style="color:blue;">int</mark></td><td>建议返回的状态码</td><td>200</td></tr><tr><td>betHistories</td><td><mark style="color:orange;">array</mark></td><td>投注详情。</td><td>预设随机生成</td></tr></tbody></table>

**betHistories**

{% tabs %}
{% tab title="百家乐" %}
| 参数                   | 格式                                       | 描述                                                                                                                  |
| -------------------- | ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">int</mark>     | <p>游戏类型。</p><p>1: 百家乐</p>                                                                                           |
| gameName             | <mark style="color:blue;">string</mark>  | 游戏名称                                                                                                                |
| betMap               | <mark style="color:orange;">array</mark> | 投注详细信息。                                                                                                             |
| bet                  | <mark style="color:blue;">double</mark>  | 总投注额。                                                                                                               |
| roundNo              | <mark style="color:blue;">string</mark>  | 牌局号码。                                                                                                               |
| payout               | <mark style="color:blue;">double</mark>  | 总派彩金额。                                                                                                              |
| payoutDetail         | <mark style="color:orange;">array</mark> | 每个投注项目的派彩金额。                                                                                                        |
| judgeResult          | <mark style="color:orange;">array</mark> | 中奖奖项。                                                                                                               |
| oddsMap              | <mark style="color:orange;">array</mark> | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p>                                                        |
| playerCards          | <mark style="color:orange;">array</mark> | 闲的开牌结果。                                                                                                             |
| playerResult         | <mark style="color:blue;">int</mark>     | 闲家点数。                                                                                                               |
| bankerCard           | <mark style="color:orange;">array</mark> | 庄的开牌结果。                                                                                                             |
| bankerResult         | <mark style="color:blue;">int</mark>     | 庄家点数。                                                                                                               |
| payoutWithoutholding | <mark style="color:blue;">double</mark>  | <p>纯派彩总额。</p><p>如果没有预扣金额，则参数值将与派彩相同。 如果有预扣金额，则计算公式为payout-withholdingtotal。</p><p>如果参数值大于0，则玩家获胜；如果参数值等于0是玩家输钱。</p> |
| createTime           | <mark style="color:blue;">long</mark>    | 下注时间。 以秒为单位。格式为Unix Time。                                                                                           |
| payoutTime           | <mark style="color:blue;">long</mark>    | 派彩时间。 以秒为单位。格式为Unix Time。                                                                                           |
| betHistoryId         | <mark style="color:blue;">string</mark>  | 投注记录ID。                                                                                                             |
| validBet             | <mark style="color:blue;">double</mark>  | 有效投注。                                                                                                               |
| rebateAmount         | <mark style="color:blue;">double</mark>  | 返水。                                                                                                                 |
| balance              | <mark style="color:blue;">double</mark>  | 盈余。                                                                                                                 |
| username             | <mark style="color:blue;">string</mark>  | 用户名。                                                                                                                |
| userId               | <mark style="color:blue;">long</mark>    | 用户ID。                                                                                                               |
| platform             | <mark style="color:blue;">int</mark>     | 游戏平台。                                                                                                               |
| brokerageRequired    | <mark style="color:blue;">boolean</mark> | 是否為免佣金百家乐。                                                                                                          |

<pre class="language-json" data-overflow="wrap" data-line-numbers><code class="lang-json"><strong>{
</strong>    "betHistories": [
        {
            "gameType": 1,
            "gameName": "baccarat",
            "betMap": [
                {
                    "betType": 60,
                    "betMoney": 10
                },
                {
                    "betType": 63,
                    "betMoney": 10
                },
                {
                    "betType": 66,
                    "betMoney": 10
                },
                {
                    "betType": 68,
                    "betMoney": 10
                },
                {
                    "betType": 70,
                    "betMoney": 10
                },
                {
                    "betType": 82,
                    "betMoney": 10
                },
                {
                    "betType": 86,
                    "betMoney": 10
                },
                {
                    "betType": 88,
                    "betMoney": 10
                }
            ],
            "bet": 80,
            "roundNo": "BP1-221025093603",
            "payout": 73.8,
            "payoutDetail": {
                "60": 20,
                "63": 19,
                "70": 15.4,
                "82": 19.4
            },
            "judgeResult": [
                60,
                70,
                82,
                63,
                61
            ],
            "oddsMap": [
                {
                    "60": 1,
                    "63": 0.9,
                    "66": 11,
                    "68": 8,
                    "70": 0.54,
                    "82": 0.94,
                    "86": 20,
                    "88": 11
                }
            ],
            "playerCards": [
                11,
                30
            ],
            "playerResult": 6,
            "bankerCards": [
                4,
                6,
                44
            ],
            "bankerResult": 1,
            "payoutWithoutholding": 73.8,
            "createTime": 1666661778,
            "payoutTime": 1666661806,
            "betHistoryId": "63573dae1c857e34c6639ac2",
            "validBet": 80,
            "rebateAmount": 0,
            "balance": -6.2,
            "username": "demo",
            "userId": 67928964,
            "brokerageRequired": true,
            "platform": 3
        }
<strong>    ],
</strong><strong>    "count": 1,
</strong><strong>    "remainingVisits": 499,
</strong><strong>    "status": 200,
</strong><strong>    "apiVersion": "1.5.75"
</strong><strong>}
</strong></code></pre>
{% endtab %}

{% tab title="龙虎" %}
| 参数                   | 格式                                       | 描述                                                           |
| -------------------- | ---------------------------------------- | ------------------------------------------------------------ |
| gameType             | <mark style="color:blue;">int</mark>     | <p>游戏类型。</p><p>2: 龙虎</p>                                     |
| gameName             | <mark style="color:blue;">string</mark>  | 游戏名称。                                                        |
| betMap               | <mark style="color:orange;">array</mark> | 投注详细信息。                                                      |
| bet                  | <mark style="color:blue;">double</mark>  | 总投注额。                                                        |
| roundNo              | <mark style="color:blue;">string</mark>  | 牌局号码。                                                        |
| payout               | <mark style="color:blue;">double</mark>  | 总派彩金额。                                                       |
| payoutDetail         | <mark style="color:orange;">array</mark> | 每个投注项目的派彩金额。                                                 |
| judgeResult          | <mark style="color:orange;">array</mark> | 中奖奖项。                                                        |
| oddsMap              | <mark style="color:orange;">array</mark> | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p> |
| dragonCard           | <mark style="color:blue;">int</mark>     | 只有龙虎。 龙的开牌结果。                                                |
| tigerCard            | <mark style="color:blue;">int</mark>     | 只有龙虎。 虎的开牌结果。                                                |
| payoutWithoutholding | <mark style="color:blue;">double</mark>  | 纯派彩总额。                                                       |
| createTime           | <mark style="color:blue;">long</mark>    | 下注时间。 以秒为单位。格式为Unix Time。                                    |
| payoutTime           | <mark style="color:blue;">long</mark>    | 派彩时间。 以秒为单位。格式为Unix Time。                                    |
| betHistoryId         | <mark style="color:blue;">string</mark>  | 投注记录ID。                                                      |
| validBet             | <mark style="color:blue;">double</mark>  | 有效投注。                                                        |
| rebateAmount         | <mark style="color:blue;">double</mark>  | 返水。                                                          |
| balance              | <mark style="color:blue;">double</mark>  | 盈余。                                                          |
| username             | <mark style="color:blue;">string</mark>  | 用户名。                                                         |
| userId               | <mark style="color:blue;">long</mark>    | 用户ID。                                                        |
| platform             | <mark style="color:blue;">int</mark>     | 游戏平台。                                                        |

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
                    "betMoney": 10
                },
                {
                    "betType": 12,
                    "betMoney": 10
                },
                {
                    "betType": 15,
                    "betMoney": 10
                },
                {
                    "betType": 16,
                    "betMoney": 10
                },
                {
                    "betType": 19,
                    "betMoney": 10
                },
                {
                    "betType": 68,
                    "betMoney": 10
                }
            ],
            "bet": 60,
            "roundNo": "DL1-221025095547",
            "payout": 38,
            "payoutDetail": {
                "12": 17.5,
                "15": 20.5
            },
            "judgeResult": [
                11,
                12,
                15,
                17,
                18
            ],
            "oddsMap": [
                {
                    "10": 1,
                    "12": 0.75,
                    "15": 1.05,
                    "16": 0.9,
                    "19": 0.9,
                    "68": 8
                }
            ],
            "dragonCard": 25,
            "tigerCard": 45,
            "payoutWithoutholding": 38,
            "createTime": 1666662958,
            "payoutTime": 1666662987,
            "betHistoryId": "6357424bbb0cf934aede710d",
            "validBet": 60,
            "rebateAmount": 0,
            "balance": -22,
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

{% tab title="骰子游戏" %}
| 参数                   | 格式                                       | 描述                                                                    |
| -------------------- | ---------------------------------------- | --------------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">int</mark>     | <p>游戏类型。</p><p>3: 骰子游戏</p>                                            |
| gameName             | <mark style="color:blue;">string</mark>  | 游戏名称。                                                                 |
| betMap               | <mark style="color:orange;">array</mark> | 投注详细信息。                                                               |
| bet                  | <mark style="color:blue;">double</mark>  | 总投注额。                                                                 |
| roundNo              | <mark style="color:blue;">string</mark>  | 牌局号码。                                                                 |
| payout               | <mark style="color:blue;">double</mark>  | 总派彩金额。                                                                |
| payoutDetail         | <mark style="color:orange;">array</mark> | <p>每个投注项目的派彩金额。 </p><p>骰宝的155.156后面会带开出的骰子点数，例如"155:1,1,6": 100. </p> |
| judgeResult          | <mark style="color:orange;">array</mark> | 中奖奖项。                                                                 |
| oddsMap              | <mark style="color:orange;">array</mark> | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p>          |
| allDices             | <mark style="color:orange;">array</mark> | 只有骰宝。 3个骰子点数。                                                         |
| payoutWithoutholding | <mark style="color:blue;">double</mark>  | 纯派彩总额。                                                                |
| createTime           | <mark style="color:blue;">long</mark>    | 下注时间。 以秒为单位。格式为Unix Time。                                             |
| payoutTime           | <mark style="color:blue;">long</mark>    | 派彩时间。 以秒为单位。格式为Unix Time。                                             |
| betHistoryId         | <mark style="color:blue;">string</mark>  | 投注记录ID。                                                               |
| validBet             | <mark style="color:blue;">double</mark>  | 有效投注。                                                                 |
| rebateAmount         | <mark style="color:blue;">double</mark>  | 返水。                                                                   |
| balance              | <mark style="color:blue;">double</mark>  | 盈余。                                                                   |
| username             | <mark style="color:blue;">string</mark>  | 用户名。                                                                  |
| userId               | <mark style="color:blue;">long</mark>    | 用户ID。                                                                 |
| platform             | <mark style="color:blue;">int</mark>     | 游戏平台。                                                                 |

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
                    "betMoney": 10
                },
                {
                    "betType": 102,
                    "betMoney": 10
                },
                {
                    "betType": 109,
                    "betMoney": 10
                },
                {
                    "betType": 115,
                    "betMoney": 10
                },
                {
                    "betType": 116,
                    "betMoney": 10
                },
                {
                    "betType": 128,
                    "betMoney": 10
                },
                {
                    "betType": 139,
                    "betMoney": 10
                },
                {
                    "betType": 151,
                    "betMoney": 10
                }
            ],
            "bet": 80,
            "roundNo": "SL1-221025095607",
            "payout": 100,
            "payoutDetail": {
                "102": 20,
                "139": 20,
                "151": 60
            },
            "judgeResult": [
                127,
                145,
                148,
                151,
                135,
                136,
                139,
                102,
                100,
                156
            ],
            "oddsMap": [
                {
                    "101": 1,
                    "102": 1,
                    "109": 8,
                    "115": 150,
                    "116": 24,
                    "128": 6,
                    "139": 1,
                    "151": 5
                }
            ],
            "allDices": [
                2,
                3,
                6
            ],
            "payoutWithoutholding": 100,
            "createTime": 1666662993,
            "payoutTime": 1666663022,
            "betHistoryId": "6357426ebb0cf934aede7134",
            "validBet": 80,
            "rebateAmount": 0,
            "balance": 20,
            "username": "demo",
            "userId": 67928964,
            "platform": 3
        },
        {
            "gameType": 3,
            "gameName": "hi-lo",
            "betMap": [
                {
                    "betType": 157,
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
            "roundNo": "SHL1-221025095826",
            "payout": 419,
            "payoutDetail": {
                "157": 222,
                "162": 197
            },
            "judgeResult": [
                102,
                157,
                162
            ],
            "oddsMap": [
                {
                    "157": 1.22,
                    "159": 3.47,
                    "160": 1.48,
                    "161": 0.97,
                    "162": 0.97,
                    "163": 1.48
                }
            ],
            "allDices": [
                2,
                4,
                6
            ],
            "payoutWithoutholding": 419,
            "createTime": 1666663123,
            "payoutTime": 1666663171,
            "betHistoryId": "63574303bb0cf934aede72d1",
            "validBet": 600,
            "rebateAmount": 0,
            "balance": -181,
            "username": "demo",
            "userId": 67928964,
            "platform": 3,
            "maxPayout": 50000
        }
    ],
    "count": 2,
    "remainingVisits": 499,
    "status": 200,
    "apiVersion": "1.5.75"
}
```
{% endcode %}
{% endtab %}

{% tab title="轮盘" %}
| 参数                   | 格式                                       | 描述                                                                                                             |
| -------------------- | ---------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">int</mark>     | <p>游戏类型。</p><p>4: 轮盘</p>                                                                                       |
| gameName             | <mark style="color:blue;">string</mark>  | 游戏名称。                                                                                                          |
| betMap               | <mark style="color:orange;">array</mark> | 投注详细信息。                                                                                                        |
| bet                  | <mark style="color:blue;">double</mark>  | 总投注额。                                                                                                          |
| roundNo              | <mark style="color:blue;">string</mark>  | 牌局号码。                                                                                                          |
| payout               | <mark style="color:blue;">double</mark>  | 总派彩金额。                                                                                                         |
| payoutDetail         | <mark style="color:orange;">array</mark> | <p>每个投注项目的派彩金额。 </p><p>轮盘名称后面会携带该局的点数或betTypeInterval的參數，例如"200:17": 3600, "207:1": 300, "201:14,17": 1800</p> |
| judgeResult          | <mark style="color:orange;">array</mark> | 中奖奖项。                                                                                                          |
| oddsMap              | <mark style="color:orange;">array</mark> | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p>                                                   |
| number               | <mark style="color:blue;">int</mark>     | 只有轮盘。 结果号码。                                                                                                    |
| payoutWithoutholding | <mark style="color:blue;">double</mark>  | 纯派彩总额。                                                                                                         |
| createTime           | <mark style="color:blue;">long</mark>    | 下注时间。 以秒为单位。格式为Unix Time。                                                                                      |
| payoutTime           | <mark style="color:blue;">long</mark>    | 派彩时间。 以秒为单位。格式为Unix Time。                                                                                      |
| betHistoryId         | <mark style="color:blue;">string</mark>  | 投注记录ID。                                                                                                        |
| validBet             | <mark style="color:blue;">double</mark>  | 有效投注。                                                                                                          |
| rebateAmount         | <mark style="color:blue;">double</mark>  | 返水。                                                                                                            |
| balance              | <mark style="color:blue;">double</mark>  | 盈余。                                                                                                            |
| username             | <mark style="color:blue;">string</mark>  | 用户名。                                                                                                           |
| userId               | <mark style="color:blue;">long</mark>    | 用户ID。                                                                                                          |
| platform             | <mark style="color:blue;">int</mark>     | 游戏平台。                                                                                                          |

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
                        2,
                        4,
                        6,
                        8,
                        10,
                        11,
                        13,
                        15,
                        17,
                        20,
                        22,
                        24,
                        26,
                        28,
                        29,
                        31,
                        33,
                        35
                    ],
                    "betType": 210,
                    "betMoney": 10
                },
                {
                    "betNumber": [
                        2,
                        4,
                        6,
                        8,
                        10,
                        12,
                        14,
                        16,
                        18,
                        20,
                        22,
                        24,
                        26,
                        28,
                        30,
                        32,
                        34,
                        36
                    ],
                    "betType": 212,
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
                        2
                    ],
                    "betType": 200,
                    "betMoney": 10
                },
                {
                    "betNumber": [
                        1,
                        2
                    ],
                    "betType": 201,
                    "betMoney": 10
                },
                {
                    "betNumber": [
                        0,
                        1,
                        2
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
                    "betTypeInterval": "0,0",
                    "betNumber": [
                        1,
                        2,
                        4,
                        5
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
                    "betTypeInterval": "1",
                    "betNumber": [
                        2,
                        5,
                        8,
                        11,
                        14,
                        17,
                        20,
                        23,
                        26,
                        29,
                        32,
                        35
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
            "roundNo": "RP1-221025095927",
            "payout": 70,
            "payoutDetail": {
                "212": 20,
                "214": 20,
                "208:0": 30
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
                    "205": 8,
                    "210": 1,
                    "212": 1,
                    "214": 1,
                    "200:2": 35,
                    "201:1,2": 17,
                    "204:0,1,2": 11,
                    "202:0": 11,
                    "203:0,0": 8,
                    "206:0": 5,
                    "207:1": 2,
                    "208:0": 2
                }
            ],
            "number": 12,
            "payoutWithoutholding": 70,
            "createTime": 1666663176,
            "payoutTime": 1666663227,
            "betHistoryId": "6357433b1c857e34c663a5c6",
            "validBet": 120,
            "rebateAmount": 0,
            "balance": -50,
            "username": "demo",
            "userId": 67928964,
            "platform": 3
        },
        {
            "gameType": 4,
            "gameName": "fortune roulette",
            "betMap": [
                {
                    "betNumber": [
                        33
                    ],
                    "betType": 200,
                    "betMoney": 20
                },
                {
                    "betNumber": [
                        30,
                        33
                    ],
                    "betType": 201,
                    "betMoney": 20
                },
                {
                    "betTypeInterval": "10",
                    "betNumber": [
                        31,
                        32,
                        33
                    ],
                    "betType": 202,
                    "betMoney": 20
                },
                {
                    "betTypeInterval": "9,1",
                    "betNumber": [
                        29,
                        30,
                        32,
                        33
                    ],
                    "betType": 203,
                    "betMoney": 20
                },
                {
                    "betTypeInterval": "9",
                    "betNumber": [
                        28,
                        29,
                        30,
                        31,
                        32,
                        33
                    ],
                    "betType": 206,
                    "betMoney": 20
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
                    "betMoney": 20
                },
                {
                    "betTypeInterval": "2",
                    "betNumber": [
                        25,
                        26,
                        27,
                        28,
                        29,
                        30,
                        31,
                        32,
                        33,
                        34,
                        35,
                        36
                    ],
                    "betType": 208,
                    "betMoney": 20
                }
            ],
            "bet": 140,
            "roundNo": "RC1-221025095949",
            "payout": 0,
            "payoutDetail": {},
            "judgeResult": [
                200,
                213,
                212,
                210,
                202,
                207,
                206,
                206,
                203,
                203,
                203,
                203,
                208,
                201,
                201,
                201,
                201
            ],
            "oddsMap": [
                {
                    "200:33": 30,
                    "201:30,33": 17,
                    "202:10": 11,
                    "203:9,1": 8,
                    "206:9": 5,
                    "207:2": 2,
                    "208:2": 2
                }
            ],
            "number": 20,
            "payoutWithoutholding": 0,
            "createTime": 1666663205,
            "payoutTime": 1666663236,
            "betHistoryId": "635743446a05b234ad72da74",
            "validBet": 140,
            "rebateAmount": 0,
            "balance": -140,
            "username": "demo",
            "userId": 67928964,
            "platform": 3
        }
    ],
    "count": 2,
    "remainingVisits": 499,
    "status": 200,
    "apiVersion": "1.5.75"
}
```
{% endcode %}
{% endtab %}

{% tab title="老虎机" %}
| 参数                   | 格式                                                                                              | 描述                                                                                                                  |
| -------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">int</mark>                                                            | <p>游戏类型。</p><p>5: 老虎机</p>                                                                                           |
| gameName             | <mark style="color:blue;">string</mark>                                                         | <p>游戏名称。</p><p>slot(显示游戏的gameID)</p>                                                                                |
| betMap               | <mark style="color:orange;">array</mark>                                                        | 投注详细信息。                                                                                                             |
| bet                  | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总投注额。                                                                                                               |
| roundNo              | <mark style="color:blue;">string</mark>                                                         | 牌局号码。                                                                                                               |
| payout               | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总派彩金额。                                                                                                              |
| payoutDetail         | <mark style="color:orange;">array</mark>                                                        | 每个投注项目的派彩金额。                                                                                                        |
| judgeResult          | <mark style="color:orange;">array</mark>                                                        | 中奖奖项。 部分电子游戏不提供。                                                                                                    |
| oddsMap              | <mark style="color:orange;">array</mark>                                                        | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p>                                                        |
| surrender            | <mark style="color:blue;">int</mark>                                                            | 投降派彩(只有21点才會有此参数)                                                                                                   |
| payoutWithoutholding | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | <p>纯派彩总额。</p><p>如果没有预扣金额，则参数值将与派彩相同。 如果有预扣金额，则计算公式为payout-withholdingtotal。</p><p>如果参数值大于0，则玩家获胜；如果参数值等于0是玩家输钱。</p> |
| createTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 下注时间。 以秒为单位。格式为Unix Time。                                                                                           |
| payoutTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 派彩时间。 以秒为单位。格式为Unix Time。                                                                                           |
| betHistoryId         | <mark style="color:blue;">string</mark>                                                         | 投注记录ID。                                                                                                             |
| validBet             | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 有效投注。                                                                                                               |
| rebateAmount         | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 返水。                                                                                                                 |
| balance              | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 盈余。                                                                                                                 |
| username             | <mark style="color:blue;">string</mark>                                                         | 用户名。 不可使用http保留字元。                                                                                                  |
| userId               | <mark style="color:blue;">int($int64)</mark>                                                    | 用户ID。                                                                                                               |
| providerId           | <mark style="color:blue;">string</mark>                                                         | 游戏供应商ID。仅电子类游戏有此参数。                                                                                                 |
| platform             | <mark style="color:blue;">int</mark>                                                            | 游戏平台。                                                                                                               |
{% endtab %}

{% tab title="牛牛" %}
| 参数                   | 格式                                                                                              | 描述                                                                                                                  |
| -------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">int</mark>                                                            | <p>游戏类型。</p><p>8: 牛牛</p>                                                                                            |
| gameName             | <mark style="color:blue;">string</mark>                                                         | <p>游戏名称。</p><p>bull-bull</p>                                                                                        |
| betMap               | <mark style="color:orange;">array</mark>                                                        | 投注详细信息。                                                                                                             |
| bet                  | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总投注额。                                                                                                               |
| roundNo              | <mark style="color:blue;">string</mark>                                                         | 牌局号码。                                                                                                               |
| payout               | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总派彩金额。                                                                                                              |
| payoutDetail         | <mark style="color:orange;">array</mark>                                                        | 每个投注项目的派彩金额。                                                                                                        |
| judgeResult          | <mark style="color:orange;">array</mark>                                                        | 中奖奖项。 牛牛: 开牌结果。                                                                                                     |
| oddsMap              | <mark style="color:orange;">array</mark>                                                        | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p>                                                        |
| niuniuResult         | <mark style="color:orange;">array</mark>                                                        | <p>只有牛牛。牛牛的结果记录。<br>banker<br>player1<br>player2<br>player3<br>isWin</p>                                            |
| withHoldingTotal     | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 预扣总额。                                                                                                               |
| withHoldingDetail    |                                                                                                 | 只有牛牛。牛牛的预扣细节。                                                                                                       |
| payoutWithoutholding | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | <p>纯派彩总额。</p><p>如果没有预扣金额，则参数值将与派彩相同。 如果有预扣金额，则计算公式为payout-withholdingtotal。</p><p>如果参数值大于0，则玩家获胜；如果参数值等于0是玩家输钱。</p> |
| createTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 下注时间。 以秒为单位。格式为Unix Time。                                                                                           |
| payoutTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 派彩时间。 以秒为单位。格式为Unix Time。                                                                                           |
| betHistoryId         | <mark style="color:blue;">string</mark>                                                         | 投注记录ID。                                                                                                             |
| validBet             | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 有效投注。                                                                                                               |
| rebateAmount         | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 返水。                                                                                                                 |
| balance              | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 盈余。                                                                                                                 |
| username             | <mark style="color:blue;">string</mark>                                                         | 用户名。 不可使用http保留字元。                                                                                                  |
| userId               | <mark style="color:blue;">int($int64)</mark>                                                    | 用户ID。                                                                                                               |
| providerId           | <mark style="color:blue;">string</mark>                                                         | 游戏供应商ID。仅电子类游戏有此参数。                                                                                                 |
| platform             | <mark style="color:blue;">int</mark>                                                            | 游戏平台。                                                                                                               |
{% endtab %}

{% tab title="财富大转盘" %}
| 参数                   | 格式                                                                                              | 描述                                                                                                                  |
| -------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">int</mark>                                                            | <p>游戏类型。</p><p>23: 财富大转盘</p>                                                                                        |
| gameName             | <mark style="color:blue;">string</mark>                                                         | <p>游戏名称。</p><p>fortune-wheel</p>                                                                                    |
| betMap               | <mark style="color:orange;">array</mark>                                                        | 投注详细信息。                                                                                                             |
| bet                  | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总投注额。                                                                                                               |
| roundNo              | <mark style="color:blue;">string</mark>                                                         | 牌局号码。                                                                                                               |
| payout               | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总派彩金额。                                                                                                              |
| payoutDetail         | <mark style="color:orange;">array</mark>                                                        | 每个投注项目的派彩金额。                                                                                                        |
| judgeResult          | <mark style="color:orange;">array</mark>                                                        | 中奖奖项。                                                                                                               |
| oddsMap              | <mark style="color:orange;">array</mark>                                                        | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p>                                                        |
| maxPayout            | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 只有财富大转盘。 最高赔付金额。                                                                                                    |
| payoutWithoutholding | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | <p>纯派彩总额。</p><p>如果没有预扣金额，则参数值将与派彩相同。 如果有预扣金额，则计算公式为payout-withholdingtotal。</p><p>如果参数值大于0，则玩家获胜；如果参数值等于0是玩家输钱。</p> |
| createTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 下注时间。 以秒为单位。格式为Unix Time。                                                                                           |
| payoutTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 派彩时间。 以秒为单位。格式为Unix Time。                                                                                           |
| betHistoryId         | <mark style="color:blue;">string</mark>                                                         | 投注记录ID。                                                                                                             |
| validBet             | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 有效投注。                                                                                                               |
| rebateAmount         | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 返水。                                                                                                                 |
| balance              | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 盈余。                                                                                                                 |
| username             | <mark style="color:blue;">string</mark>                                                         | 用户名。 不可使用http保留字元。                                                                                                  |
| userId               | <mark style="color:blue;">int($int64)</mark>                                                    | 用户ID。                                                                                                               |
| providerId           | <mark style="color:blue;">string</mark>                                                         | 游戏供应商ID。仅电子类游戏有此参数。                                                                                                 |
| platform             | <mark style="color:blue;">int</mark>                                                            | 游戏平台。                                                                                                               |
{% endtab %}

{% tab title="电子21点" %}
| 参数                   | 格式                                                                                              | 描述                                                                                                                  |
| -------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">int</mark>                                                            | <p>游戏类型。</p><p>24: 电子21点</p>                                                                                        |
| gameName             | <mark style="color:blue;">string</mark>                                                         | <p>游戏名称。</p><p>black-jack-electronic</p>                                                                            |
| betMap               | <mark style="color:orange;">array</mark>                                                        | 投注详细信息。                                                                                                             |
| bet                  | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总投注额。                                                                                                               |
| roundNo              | <mark style="color:blue;">string</mark>                                                         | 牌局号码。                                                                                                               |
| payout               | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总派彩金额。                                                                                                              |
| payoutDetail         | <mark style="color:orange;">array</mark>                                                        | 每个投注项目的派彩金额。                                                                                                        |
| judgeResult          | <mark style="color:orange;">array</mark>                                                        | 中奖奖项。  部分电子游戏不提供。                                                                                                   |
| oddsMap              | <mark style="color:orange;">array</mark>                                                        | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p>                                                        |
| surrender            | <mark style="color:blue;">int</mark>                                                            | 投降派彩(只有21点才會有此参数)                                                                                                   |
| payoutWithoutholding | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | <p>纯派彩总额。</p><p>如果没有预扣金额，则参数值将与派彩相同。 如果有预扣金额，则计算公式为payout-withholdingtotal。</p><p>如果参数值大于0，则玩家获胜；如果参数值等于0是玩家输钱。</p> |
| createTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 下注时间。 以秒为单位。格式为Unix Time。                                                                                           |
| payoutTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 派彩时间。 以秒为单位。格式为Unix Time。                                                                                           |
| betHistoryId         | <mark style="color:blue;">string</mark>                                                         | 投注记录ID。                                                                                                             |
| validBet             | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 有效投注。                                                                                                               |
| rebateAmount         | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 返水。                                                                                                                 |
| balance              | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 盈余。                                                                                                                 |
| username             | <mark style="color:blue;">string</mark>                                                         | 用户名。 不可使用http保留字元。                                                                                                  |
| userId               | <mark style="color:blue;">int($int64)</mark>                                                    | 用户ID。                                                                                                               |
| providerId           | <mark style="color:blue;">string</mark>                                                         | 游戏供应商ID。仅电子类游戏有此参数。                                                                                                 |
| platform             | <mark style="color:blue;">int</mark>                                                            | 游戏平台。                                                                                                               |
{% endtab %}

{% tab title="真人21点" %}
| 参数                   | 格式                                                                                              | 描述                                                                                                                  |
| -------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">int</mark>                                                            | <p>游戏类型。</p><p>25: 真人21点</p>                                                                                        |
| gameName             | <mark style="color:blue;">string</mark>                                                         | <p>游戏名称。</p><p>black-jack-live</p>                                                                                  |
| betMap               | <mark style="color:orange;">array</mark>                                                        | 投注详细信息。                                                                                                             |
| bet                  | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总投注额。                                                                                                               |
| roundNo              | <mark style="color:blue;">string</mark>                                                         | 牌局号码。                                                                                                               |
| payout               | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总派彩金额。                                                                                                              |
| payoutDetail         | <mark style="color:orange;">array</mark>                                                        | 每个投注项目的派彩金额。                                                                                                        |
| judgeResult          | <mark style="color:orange;">array</mark>                                                        | 中奖奖项。                                                                                                               |
| oddsMap              | <mark style="color:orange;">array</mark>                                                        | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p>                                                        |
| surrender            | <mark style="color:blue;">int</mark>                                                            | 投降派彩(只有21点才會有此参数)                                                                                                   |
| payoutWithoutholding | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | <p>纯派彩总额。</p><p>如果没有预扣金额，则参数值将与派彩相同。 如果有预扣金额，则计算公式为payout-withholdingtotal。</p><p>如果参数值大于0，则玩家获胜；如果参数值等于0是玩家输钱。</p> |
| createTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 下注时间。 以秒为单位。格式为Unix Time。                                                                                           |
| payoutTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 派彩时间。 以秒为单位。格式为Unix Time。                                                                                           |
| betHistoryId         | <mark style="color:blue;">string</mark>                                                         | 投注记录ID。                                                                                                             |
| validBet             | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 有效投注。                                                                                                               |
| rebateAmount         | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 返水。                                                                                                                 |
| balance              | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 盈余。                                                                                                                 |
| username             | <mark style="color:blue;">string</mark>                                                         | 用户名。 不可使用http保留字元。                                                                                                  |
| userId               | <mark style="color:blue;">int($int64)</mark>                                                    | 用户ID。                                                                                                               |
| providerId           | <mark style="color:blue;">string</mark>                                                         | 游戏供应商ID。仅电子类游戏有此参数。                                                                                                 |
| platform             | <mark style="color:blue;">int</mark>                                                            | 游戏平台。                                                                                                               |
{% endtab %}

{% tab title="迷你游戏" %}
| 参数                   | 格式                                                                                              | 描述                                                                                                                  |
| -------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| gameType             | <mark style="color:blue;">int</mark>                                                            | <p>游戏类型。</p><p>27: 迷你游戏</p>                                                                                         |
| gameName             | <mark style="color:blue;">string</mark>                                                         | <p>游戏名称。</p><p>mini-game(显示游戏的gameID)</p>                                                                           |
| betMap               | <mark style="color:orange;">array</mark>                                                        | 投注详细信息。                                                                                                             |
| bet                  | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总投注额。                                                                                                               |
| roundNo              | <mark style="color:blue;">string</mark>                                                         | 牌局号码。                                                                                                               |
| payout               | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总派彩金额。                                                                                                              |
| payoutDetail         | <mark style="color:orange;">array</mark>                                                        | 每个投注项目的派彩金额。                                                                                                        |
| judgeResult          | <mark style="color:orange;">array</mark>                                                        | 中奖奖项。                                                                                                               |
| oddsMap              | <mark style="color:orange;">array</mark>                                                        | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p>                                                        |
| payoutWithoutholding | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | <p>纯派彩总额。</p><p>如果没有预扣金额，则参数值将与派彩相同。 如果有预扣金额，则计算公式为payout-withholdingtotal。</p><p>如果参数值大于0，则玩家获胜；如果参数值等于0是玩家输钱。</p> |
| createTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 下注时间。 以秒为单位。格式为Unix Time。                                                                                           |
| payoutTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 派彩时间。 以秒为单位。格式为Unix Time。                                                                                           |
| betHistoryId         | <mark style="color:blue;">string</mark>                                                         | 投注记录ID。                                                                                                             |
| validBet             | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 有效投注。                                                                                                               |
| rebateAmount         | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 返水。                                                                                                                 |
| balance              | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 盈余。                                                                                                                 |
| username             | <mark style="color:blue;">string</mark>                                                         | 用户名。 不可使用http保留字元。                                                                                                  |
| userId               | <mark style="color:blue;">int($int64)</mark>                                                    | 用户ID。                                                                                                               |
| providerId           | <mark style="color:blue;">string</mark>                                                         | 游戏供应商ID。仅电子类游戏有此参数。                                                                                                 |
| platform             | <mark style="color:blue;">int</mark>                                                            | 游戏平台。                                                                                                               |
{% endtab %}

{% tab title="电子棋牌" %}
| 参数                   | 格式                                                                                              | 描述                                                                                                                                                                                                                                   |
| -------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| gameType             | <mark style="color:blue;">int</mark>                                                            | <p>游戏类型。</p><p>1: 百家乐</p><p>2: 龙虎</p><p>3: 骰宝</p><p>4: 轮盘</p><p>5: 老虎机</p><p>8: 牛牛</p><p>23: 财富大转盘</p><p>24: 电子21点</p><p>25: 真人21点</p><p>27: 迷你游戏</p>                                                                                |
| gameName             | <mark style="color:blue;">string</mark>                                                         | <p>游戏名称。</p><p>baccarat</p><p>dragon-tiger</p><p>sic-bo</p><p>roulette</p><p>slot(显示游戏的gameID)</p><p>bull-bull</p><p>fortune-wheel</p><p>black-jack-electronic</p><p>black-jack-live</p><p>mini-game(显示游戏的gameID)</p><p>pok-deng</p> |
| betMap               | <mark style="color:orange;">array</mark>                                                        | <p>投注详细信息。</p><p>betType</p><p>betMoney</p><p>betTypeInterval</p><p>betNumber</p><p>betDice</p>                                                                                                                                      |
| bet                  | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总投注额。                                                                                                                                                                                                                                |
| roundNo              | <mark style="color:blue;">string</mark>                                                         | 牌局号码。                                                                                                                                                                                                                                |
| payout               | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总派彩金额。                                                                                                                                                                                                                               |
| payoutDetail         | <mark style="color:orange;">array</mark>                                                        | <p>每个投注项目的派彩金额。 </p><p>骰宝的155.156后面会带开出的骰子点数，例如"155:1,1,6": 100. </p><p>轮盘名称后面会携带该局的点数或betTypeInterval的參數，例如"200:17": 3600, "207:1": 300, "201:14,17": 1800</p>                                                                      |
| judgeResult          | <mark style="color:orange;">array</mark>                                                        | 中奖奖项。 牛牛: 开牌结果。 部分电子游戏不提供。                                                                                                                                                                                                           |
| oddsMap              | <mark style="color:orange;">array</mark>                                                        | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p>                                                                                                                                                                         |
| surrender            | <mark style="color:blue;">int</mark>                                                            | 投降派彩(只有21点才會有此参数)                                                                                                                                                                                                                    |
| playerCards          | <mark style="color:orange;">array</mark>                                                        | 只有百家乐。 闲的开牌结果。                                                                                                                                                                                                                       |
| playerResult         | <mark style="color:blue;">int</mark>                                                            | 只有百家乐。 闲家点数。                                                                                                                                                                                                                         |
| bankerCard           | <mark style="color:orange;">array</mark>                                                        | 只有百家乐。 庄的开牌结果。                                                                                                                                                                                                                       |
| bankerResult         | <mark style="color:blue;">int</mark>                                                            | 只有百家乐。 庄家点数。                                                                                                                                                                                                                         |
| dragonCard           | <mark style="color:blue;">int</mark>                                                            | 只有龙虎。 龙的开牌结果。                                                                                                                                                                                                                        |
| tigerCard            | <mark style="color:blue;">int</mark>                                                            | 只有龙虎。 虎的开牌结果。                                                                                                                                                                                                                        |
| number               | <mark style="color:blue;">int</mark>                                                            | 只有轮盘。 结果号码。                                                                                                                                                                                                                          |
| allDices             | <mark style="color:orange;">array</mark>                                                        | 只有骰宝。 3个骰子点数。                                                                                                                                                                                                                        |
| niuniuResult         | <mark style="color:orange;">array</mark>                                                        | <p>只有牛牛。牛牛的结果记录。<br>banker<br>player1<br>player2<br>player3<br>isWin</p>                                                                                                                                                             |
| withHoldingTotal     | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 预扣总额。                                                                                                                                                                                                                                |
| withHoldingDetail    |                                                                                                 | 只有牛牛。牛牛的预扣细节。                                                                                                                                                                                                                        |
| maxPayout            | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 只有财富大转盘。 最高赔付金额。                                                                                                                                                                                                                     |
| payoutWithoutholding | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | <p>纯派彩总额。</p><p>如果没有预扣金额，则参数值将与派彩相同。 如果有预扣金额，则计算公式为payout-withholdingtotal。</p><p>如果参数值大于0，则玩家获胜；如果参数值等于0是玩家输钱。</p>                                                                                                                  |
| createTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 下注时间。 以秒为单位。格式为Unix Time。                                                                                                                                                                                                            |
| payoutTime           | <mark style="color:blue;">int($int64)</mark>                                                    | 派彩时间。 以秒为单位。格式为Unix Time。                                                                                                                                                                                                            |
| betHistoryId         | <mark style="color:blue;">string</mark>                                                         | 投注记录ID。                                                                                                                                                                                                                              |
| validBet             | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 有效投注。                                                                                                                                                                                                                                |
| rebateAmount         | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 返水。                                                                                                                                                                                                                                  |
| balance              | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 盈余。                                                                                                                                                                                                                                  |
| username             | <mark style="color:blue;">string</mark>                                                         | 用户名。 不可使用http保留字元。                                                                                                                                                                                                                   |
| userId               | <mark style="color:blue;">int($int64)</mark>                                                    | 用户ID。                                                                                                                                                                                                                                |
| providerId           | <mark style="color:blue;">string</mark>                                                         | 游戏供应商ID。仅电子类游戏有此参数。                                                                                                                                                                                                                  |
| platform             | <mark style="color:blue;">int</mark>                                                            | 游戏平台。                                                                                                                                                                                                                                |
| brokerageRequired    | <mark style="color:blue;">boolean</mark>                                                        | <p>是否為免佣金百家乐。其餘為null。<br>true: 是免佣金百家乐。</p><p>false: 不是免佣金百家乐。</p>                                                                                                                                                                   |
{% endtab %}
{% endtabs %}
