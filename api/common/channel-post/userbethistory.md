---
description: 该API用于查询在特定时间段内记录的投注。
---

# userbethistory

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">int</mark></td><td>渠道ID。</td><td>RegisterOrLoginReq</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">int($int64)</mark></td><td>时间戳记。以毫秒为单位。格式为Unix Time。</td><td>1</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td><p>签名。 字串拼接：<code>username+timestamp</code></p><p>Note: 如API用户名参数非必要，可以单独使用timestamp</p></td><td>1</td></tr><tr><td><mark style="color:red;">betStatus</mark></td><td><mark style="color:blue;">int</mark></td><td><p>检查投注状态。默认为查询所有记录</p><p>0：仅查询失败的记录</p><p>1：仅查询成功的记录</p></td><td>apitest01</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。 不可使用http保留字元。</td><td>password</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td>accessToken</td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">int</mark></td><td>子渠道ID。</td><td>1577808000</td></tr><tr><td>startTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的开始。</td><td>127.0.0.1</td></tr><tr><td>endTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的结束。</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>pageNum</td><td><mark style="color:blue;">int</mark></td><td>页码。 默认值为1。</td><td></td></tr><tr><td>pageSize</td><td><mark style="color:blue;">int</mark></td><td><p>每页上显示的记录数。</p><p>默认值为10。最大为5000。</p></td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号码。</td><td></td></tr><tr><td>gameType</td><td><mark style="color:blue;">int</mark></td><td><p>游戏类型。</p><p>1: 百家乐</p><p>2: 龙虎</p><p>3: 骰宝</p><p>4: 轮盘</p><p>5: 老虎机</p><p>8: 牛牛</p><p>23: 财富大转盘</p><p>24: 电子21点</p><p>25: 真人21点</p><p>27: 迷你游戏</p><p>30: 电子棋牌</p></td><td></td></tr><tr><td>judgeTime</td><td><mark style="color:blue;">int</mark></td><td><p>判断查询时间。</p><p>预设为0</p><p>0：派彩时间</p><p>1：下注时间</p></td><td></td></tr><tr><td>isSeparate</td><td><mark style="color:blue;">boolean</mark></td><td><p>betHistories的显示方式。默认为false</p><p>true: 按确认的投注次数细分</p><p>false: 根据付款记录显示</p><p>Note: 该参数不会影响其他参数的计算。仍将根据付款数量进行处理。</p></td><td></td></tr></tbody></table>

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% hint style="info" %}
*   <mark style="color:blue;">由于数据量可能太大，建议带以下参数减少查询时间。</mark>

    <mark style="color:blue;">(startTimeStr, endTimeStr, pageNum, pageSize)</mark>
* <mark style="color:blue;">请带参数 betStatus:1 以查询成功的记录。</mark>
* <mark style="color:blue;">游戏预扣请参考withHoldingTotal。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
  "channelId": 1,
  "timestamp": 1577808000000,
  "signature": "bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==",
  "betStatus": 1,
  "username": "apitest01",
  "currency": "CNY",
  "subChannelId": 0,
  "startTimeStr": "2020-01-01 00:00:00",
  "endTimeStr": "2020-01-02 00:00:00",
  "pageNum": 1,
  "pageSize": 10,
  "roundCode": "B1-200101000000",
  "gameType": 1,
  "judgeTime": 0,
  "isSeparate": false
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
</code></pre></td></tr><tr><td>remainingVisits</td><td><mark style="color:blue;">int</mark></td><td>建议返回的状态码</td><td>200</td></tr><tr><td>betHistories</td><td><mark style="color:blue;">array</mark></td><td><p>投注详情。</p><p>gameType</p><p>gameName</p><p>betMap</p><p>bet</p><p>roundNo</p><p>payout</p><p>payoutDetail</p><p>judgeResult</p><p>oddsMap</p><p>surrender</p><p>playerCards</p><p>playerResult</p><p>bankerCard</p><p>bankerResult</p><p>dragonCard</p><p>tigerCard</p><p>number</p><p>allDices</p><p>niuniuResult</p><p>withHoldingTotal</p><p>withHoldingDetail</p><p>maxPayout</p><p>payoutWithoutholding</p><p>createTime</p><p>payoutTime</p><p>betHistoryId</p><p>validBet</p><p>rebateAmount</p><p>balance</p><p>username</p><p>userId</p><p>providerId</p><p>platform</p><p>brokerageRequired</p></td><td>预设随机生成</td></tr></tbody></table>

**betHistories**

| 参数                   | 格式                                                                                              | 描述                                                                                                                                                                                                                                   |
| -------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| gameType             | <mark style="color:blue;">int</mark>                                                            | <p>游戏类型。</p><p>1: 百家乐</p><p>2: 龙虎</p><p>3: 骰宝</p><p>4: 轮盘</p><p>5: 老虎机</p><p>8: 牛牛</p><p>23: 财富大转盘</p><p>24: 电子21点</p><p>25: 真人21点</p><p>27: 迷你游戏</p>                                                                                |
| gameName             | <mark style="color:blue;">string</mark>                                                         | <p>游戏名称。</p><p>baccarat</p><p>dragon-tiger</p><p>sic-bo</p><p>roulette</p><p>slot(显示游戏的gameID)</p><p>bull-bull</p><p>fortune-wheel</p><p>black-jack-electronic</p><p>black-jack-live</p><p>mini-game(显示游戏的gameID)</p><p>pok-deng</p> |
| betMap               | <mark style="color:blue;">array</mark>                                                          | <p>投注详细信息。</p><p>betType</p><p>betMoney</p><p>betTypeInterval</p><p>betNumber</p><p>betDice</p>                                                                                                                                      |
| bet                  | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总投注额。                                                                                                                                                                                                                                |
| roundNo              | <mark style="color:blue;">string</mark>                                                         | 牌局号码。                                                                                                                                                                                                                                |
| payout               | <p><mark style="color:blue;">number</mark></p><p><mark style="color:blue;">($double)</mark></p> | 总派彩金额。                                                                                                                                                                                                                               |
| payoutDetail         | <mark style="color:blue;">array</mark>                                                          | <p>每个投注项目的派彩金额。 </p><p>骰宝的155.156后面会带开出的骰子点数，例如"155:1,1,6": 100. </p><p>轮盘名称后面会携带该局的点数或betTypeInterval的參數，例如"200:17": 3600, "207:1": 300, "201:14,17": 1800</p>                                                                      |
| judgeResult          | <mark style="color:blue;">array</mark>                                                          | 中奖奖项。 牛牛: 开牌结果。 部分电子游戏不提供。                                                                                                                                                                                                           |
| oddsMap              | <mark style="color:blue;">array</mark>                                                          | <p>赔率。 </p><p>Noted: 1.支援所有游戏除了老虎机 2.仅派彩成功有此参数 3.赔率不含投注额</p>                                                                                                                                                                         |
| surrender            | <mark style="color:blue;">int</mark>                                                            | 投降派彩(只有21点才會有此参数)                                                                                                                                                                                                                    |
| playerCards          |                                                                                                 |                                                                                                                                                                                                                                      |
| playerResult         |                                                                                                 |                                                                                                                                                                                                                                      |
| bankerCard           |                                                                                                 |                                                                                                                                                                                                                                      |
| bankerResult         |                                                                                                 |                                                                                                                                                                                                                                      |
| dragonCard           |                                                                                                 |                                                                                                                                                                                                                                      |
| tigerCard            |                                                                                                 |                                                                                                                                                                                                                                      |
| number               |                                                                                                 |                                                                                                                                                                                                                                      |
| allDices             |                                                                                                 |                                                                                                                                                                                                                                      |
| niuniuResult         |                                                                                                 |                                                                                                                                                                                                                                      |
| withHoldingTotal     |                                                                                                 |                                                                                                                                                                                                                                      |
| withHoldingDetail    |                                                                                                 |                                                                                                                                                                                                                                      |
| maxPayout            |                                                                                                 |                                                                                                                                                                                                                                      |
| payoutWithoutholding |                                                                                                 |                                                                                                                                                                                                                                      |
| createTime           |                                                                                                 |                                                                                                                                                                                                                                      |
| payoutTime           |                                                                                                 |                                                                                                                                                                                                                                      |
| betHistoryId         |                                                                                                 |                                                                                                                                                                                                                                      |
| validBet             |                                                                                                 |                                                                                                                                                                                                                                      |
| rebateAmount         |                                                                                                 |                                                                                                                                                                                                                                      |
| balance              |                                                                                                 |                                                                                                                                                                                                                                      |
| username             |                                                                                                 |                                                                                                                                                                                                                                      |
| userId               |                                                                                                 |                                                                                                                                                                                                                                      |
| providerId           |                                                                                                 |                                                                                                                                                                                                                                      |
| platform             |                                                                                                 |                                                                                                                                                                                                                                      |
| brokerageRequired    |                                                                                                 |                                                                                                                                                                                                                                      |

{% code title="Responses" overflow="wrap" %}
```json
{
  "status": 200,
  "apiVersion": "1.3.55",
  "count": 1,
  "remainingVisits": 200,
  "betHistories": [
    {
      "gameType": 1,
      "gameName": "baccarat",
      "betMap": [
        {
          "betType": 60,
          "betMoney": 10,
          "betTypeInterval": "string",
          "betNumber": [
            0
          ],
          "betDice": [
            0
          ]
        }
      ],
      "bet": 10,
      "roundNo": "B1-200101000000",
      "payout": 20,
      "payoutDetail": [
        {
          "406": "520000"
        }
      ],
      "judgeResult": [
        60,
        70,
        82,
        63
      ],
      "oddsMap": [
        {
          "401": "2",
          "403": "10",
          "406": "25",
          "407": "0.75"
        }
      ],
      "surrender": 0,
      "playerCards": [
        1,
        6,
        29
      ],
      "playerResult": 6,
      "bankerCard": [
        14,
        38,
        7
      ],
      "bankerResult": 3,
      "dragonCard": 0,
      "tigerCard": 0,
      "number": 0,
      "allDices": [
        0
      ],
      "niuniuResult": [
        {
          "banker": 0,
          "player1": 0,
          "player2": 0,
          "player3": 0,
          "isWin": true
        }
      ],
      "withHoldingTotal": 0,
      "withHoldingDetail": [
        {
          "302": 0,
          "304": 0,
          "306": 0
        }
      ],
      "maxPayout": 0,
      "payoutWithoutholding": 0,
      "createTime": 1577808000,
      "payoutTime": 1577808030,
      "betHistoryId": "5e0d696b2fdda1335fa68243",
      "validBet": 10,
      "rebateAmount": 5,
      "balance": 10,
      "username": "apitest01",
      "userId": 19191919,
      "providerId": "wayigame",
      "platform": 1,
      "brokerageRequired": true
    }
  ]
}
```
{% endcode %}
