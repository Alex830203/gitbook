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
    "timestamp": 1680234242,
    "signature": "MM3Qc1uclCsRTdQs4AnWMrJJDwsHZCL4AjujtLVNShRx5ZUIkv1Ers701LYPHJno/9DIWOfJanm0HavcPnC+Xmbdm+juDK/vbyWRctjtOKw5MOu0TZ4fcGZhiWgsHHmVy1F3AtHunUWlWgknCkG4ePdbmlJA/Rksr29/zAbGBu8="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>username</td><td><mark style="color:blue;">number</mark></td><td>用户名。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道ID。</td><td>200</td></tr><tr><td>limit</td><td><mark style="color:orange;">array</mark></td><td>限额资讯详情。阵列值为物件，下表为物件参数说明。</td><td>预设随机生成</td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>eBET回应状态。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>0
</code></pre></td></tr></tbody></table>

limit

{% tabs %}
{% tab title="百家乐" %}
| 参数                   | 格式                                      | 描述                                                         |
| -------------------- | --------------------------------------- | ---------------------------------------------------------- |
| gameType             | <mark style="color:blue;">number</mark> | <p>游戏类型。</p><p>1: 百家乐 - VIP 桌 <br>2: 百家乐 - Normal 桌</p>    |
| playerMin            | <mark style="color:blue;">number</mark> | 游戏名称                                                       |
| playerMax            | <mark style="color:blue;">number</mark> | 投注详细信息。阵列值为物件，下表为物件参数说明。                                   |
| bankerMin            | <mark style="color:blue;">number</mark> | 总投注额。                                                      |
| bankerMax            | <mark style="color:blue;">number</mark> | 牌局号码。                                                      |
| tieMin               | <mark style="color:blue;">number</mark> | 总派彩金额。                                                     |
| tieMax               | <mark style="color:blue;">number</mark> | 每个投注项目的派彩金额。                                               |
| playerPairMin        | <mark style="color:blue;">number</mark> | 中奖奖项。                                                      |
| playerPairMax        | <mark style="color:blue;">number</mark> | <p>赔率。 </p><p>Noted:</p><p>1.仅派彩成功有此参数</p><p>2.赔率不含投注额</p> |
| bankerPairMin        | <mark style="color:blue;">number</mark> | 闲的开牌结果。                                                    |
| bankerPairMax        | <mark style="color:blue;">number</mark> | 闲家点数。                                                      |
| bankerLucky6Min      | <mark style="color:blue;">number</mark> | 庄的开牌结果。                                                    |
| bankerLucky6Max      | <mark style="color:blue;">number</mark> | 庄家点数。                                                      |
| bankerDragonBonusMin | <mark style="color:blue;">number</mark> | 纯派彩总额。                                                     |
| bankerDragonBonusMax | <mark style="color:blue;">number</mark> | 下注时间。 以秒为单位。格式为Unix Time。                                  |
| playerDragonBonusMin | <mark style="color:blue;">number</mark> | 派彩时间。 以秒为单位。格式为Unix Time。                                  |
| playerDragonBonusMax | <mark style="color:blue;">number</mark> | 投注记录ID。                                                    |
| bigMin               | <mark style="color:blue;">number</mark> | 有效投注。                                                      |
| bigMax               | <mark style="color:blue;">number</mark> | 返水。                                                        |
| smallMin             | <mark style="color:blue;">number</mark> | 盈余。                                                        |
| smallMax             | <mark style="color:blue;">number</mark> | 用户名。                                                       |
| bankerOddMin         | <mark style="color:blue;">number</mark> | 用户ID。                                                      |
| bankerOddMax         | <mark style="color:blue;">number</mark> | 是否為免佣金百家乐。                                                 |
| bankerEvenMin        | <mark style="color:blue;">number</mark> | 游戏平台。                                                      |
| bankerEvenMax        | <mark style="color:blue;">number</mark> |                                                            |
| playerOddMin         | <mark style="color:blue;">number</mark> |                                                            |
| playerOddMax         | <mark style="color:blue;">number</mark> |                                                            |
| playerEvenMin        | <mark style="color:blue;">number</mark> |                                                            |
| playerEvenMax        | <mark style="color:blue;">number</mark> |                                                            |
| perfectPairMin       | <mark style="color:blue;">number</mark> |                                                            |
| perfectPairMax       | <mark style="color:blue;">number</mark> |                                                            |
| anyPairMin           | <mark style="color:blue;">number</mark> |                                                            |
| anyPairMax           | <mark style="color:blue;">number</mark> |                                                            |
| bankerNaturalMin     | <mark style="color:blue;">number</mark> |                                                            |
| bankerNaturalMax     | <mark style="color:blue;">number</mark> |                                                            |
| playerNaturalMin     | <mark style="color:blue;">number</mark> |                                                            |
| playerNaturalMax     | <mark style="color:blue;">number</mark> |                                                            |
| super6Min            | <mark style="color:blue;">number</mark> |                                                            |
| super6Max            | <mark style="color:blue;">number</mark> |                                                            |
{% endtab %}

{% tab title="龙虎" %}
| 参数             | 格式                                      | 描述                                                         |
| -------------- | --------------------------------------- | ---------------------------------------------------------- |
| gameType       | <mark style="color:blue;">number</mark> | <p>游戏类型。</p><p>3: 龙虎</p>                                   |
| dragonMin      | <mark style="color:blue;">number</mark> | 游戏名称。                                                      |
| dragonMax      | <mark style="color:blue;">number</mark> | 投注详细信息。阵列值为物件，下表为物件参数说明。                                   |
| tigerMin       | <mark style="color:blue;">number</mark> | 总投注额。                                                      |
| tigerMax       | <mark style="color:blue;">number</mark> | 牌局号码。                                                      |
| tieMin         | <mark style="color:blue;">number</mark> | 总派彩金额。                                                     |
| tieMax         | <mark style="color:blue;">number</mark> | 每个投注项目的派彩金额。                                               |
| dragonOddMin   | <mark style="color:blue;">number</mark> | 中奖奖项。                                                      |
| dragonOddMax   | <mark style="color:blue;">number</mark> | <p>赔率。 </p><p>Noted:</p><p>1.仅派彩成功有此参数</p><p>2.赔率不含投注额</p> |
| dragonEvenMin  | <mark style="color:blue;">number</mark> | 只有龙虎。 龙的开牌结果。                                              |
| dragonEvenMax  | <mark style="color:blue;">number</mark> | 只有龙虎。 虎的开牌结果。                                              |
| tigerOddMin    | <mark style="color:blue;">number</mark> | 纯派彩总额。                                                     |
| tigerOddMax    | <mark style="color:blue;">number</mark> | 下注时间。 以秒为单位。格式为Unix Time。                                  |
| tigerEvenMin   | <mark style="color:blue;">number</mark> | 派彩时间。 以秒为单位。格式为Unix Time。                                  |
| tigerEvenMax   | <mark style="color:blue;">number</mark> | 投注记录ID。                                                    |
| dragonBlackMin | <mark style="color:blue;">number</mark> | 有效投注。                                                      |
| dragonBlackMax | <mark style="color:blue;">number</mark> | 返水。                                                        |
| dragonRedMin   | <mark style="color:blue;">number</mark> | 盈余。                                                        |
| dragonRedMax   | <mark style="color:blue;">number</mark> | 用户名。                                                       |
| tigerBlackMin  | <mark style="color:blue;">number</mark> | 用户ID。                                                      |
| tigerBlackMax  | <mark style="color:blue;">number</mark> | 游戏平台。                                                      |
| tigerRedMin    | <mark style="color:blue;">number</mark> |                                                            |
| tigerRedMax    | <mark style="color:blue;">number</mark> |                                                            |
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
{% endtab %}
{% endtabs %}

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "limit": [
        {
            "gameType": 1,
            "playerMin": 10,
            "playerMax": 100,
            "bankerMin": 10,
            "bankerMax": 100,
            "tieMin": 10,
            "tieMax": 100,
            "playerPairMin": 10,
            "playerPairMax": 100,
            "bankerPairMin": 10,
            "bankerPairMax": 100,
            "bankerLucky6Min": 10,
            "bankerLucky6Max": 100,
            "bankerDragonBonusMin": 10,
            "bankerDragonBonusMax": 100,
            "playerDragonBonusMin": 10,
            "playerDragonBonusMax": 100,
            "bigMin": 10,
            "bigMax": 100,
            "smallMin": 10,
            "smallMax": 100,
            "bankerOddMin": 10,
            "bankerOddMax": 100,
            "bankerEvenMin": 10,
            "bankerEvenMax": 100,
            "playerOddMin": 10,
            "playerOddMax": 100,
            "playerEvenMin": 10,
            "playerEvenMax": 100,
            "perfectPairMin": 1,
            "perfectPairMax": 1,
            "anyPairMin": 1,
            "anyPairMax": 1,
            "bankerNaturalMin": 1,
            "bankerNaturalMax": 1,
            "playerNaturalMin": 1,
            "playerNaturalMax": 1,
            "super6Min": 1,
            "super6Max": 1
        },
        {
            "gameType": 2,
            "playerMin": 10,
            "playerMax": 100,
            "bankerMin": 10,
            "bankerMax": 100,
            "tieMin": 10,
            "tieMax": 100,
            "playerPairMin": 10,
            "playerPairMax": 100,
            "bankerPairMin": 10,
            "bankerPairMax": 100,
            "bankerLucky6Min": 10,
            "bankerLucky6Max": 100,
            "bankerDragonBonusMin": 10,
            "bankerDragonBonusMax": 650,
            "playerDragonBonusMin": 10,
            "playerDragonBonusMax": 650,
            "bigMin": 10,
            "bigMax": 100,
            "smallMin": 10,
            "smallMax": 100,
            "bankerOddMin": 10,
            "bankerOddMax": 100,
            "bankerEvenMin": 10,
            "bankerEvenMax": 100,
            "playerOddMin": 10,
            "playerOddMax": 100,
            "playerEvenMin": 10,
            "playerEvenMax": 100,
            "perfectPairMin": 1,
            "perfectPairMax": 1,
            "anyPairMin": 1,
            "anyPairMax": 1,
            "bankerNaturalMin": 1,
            "bankerNaturalMax": 1,
            "playerNaturalMin": 1,
            "playerNaturalMax": 1,
            "super6Min": 1,
            "super6Max": 1
        },
        {
            "gameType": 3,
            "dragonMin": 10,
            "dragonMax": 100,
            "tigerMin": 10,
            "tigerMax": 100,
            "tieMin": 10,
            "tieMax": 100,
            "dragonOddMin": 10,
            "dragonOddMax": 100,
            "dragonEvenMin": 10,
            "dragonEvenMax": 100,
            "tigerOddMin": 10,
            "tigerOddMax": 100,
            "tigerEvenMin": 10,
            "tigerEvenMax": 100,
            "dragonBlackMin": 10,
            "dragonBlackMax": 100,
            "dragonRedMin": 10,
            "dragonRedMax": 100,
            "tigerBlackMin": 10,
            "tigerBlackMax": 100,
            "tigerRedMin": 10,
            "tigerRedMax": 100
        },
        {
            "gameType": 4,
            "oddMin": 10,
            "oddMax": 100,
            "evenMin": 10,
            "evenMax": 100,
            "bigMin": 10,
            "bigMax": 100,
            "smallMin": 10,
            "smallMax": 100,
            "pairMin": 10,
            "pairMax": 100,
            "tripMin": 10,
            "tripMax": 100,
            "allTripMin": 10,
            "allTripMax": 100,
            "fourMin": 10,
            "fourMax": 100,
            "fiveMin": 10,
            "fiveMax": 100,
            "sixMin": 10,
            "sixMax": 100,
            "sevenMin": 10,
            "sevenMax": 100,
            "eightMin": 10,
            "eightMax": 100,
            "nineMin": 10,
            "nineMax": 100,
            "tenMin": 10,
            "tenMax": 100,
            "elevenMin": 10,
            "elevenMax": 100,
            "twelveMin": 10,
            "twelveMax": 100,
            "thirteenMin": 10,
            "thirteenMax": 100,
            "fourteenMin": 10,
            "fourteenMax": 100,
            "fifteenMin": 10,
            "fifteenMax": 100,
            "sixteenMin": 10,
            "sixteenMax": 100,
            "seventeenMin": 10,
            "seventeenMax": 100,
            "singleDiceMin": 10,
            "singleDiceMax": 100,
            "combinationMin": 10,
            "combinationMax": 100,
            "moreLeftMin": 10,
            "moreLeftMax": 100,
            "moreRightMin": 10,
            "moreRightMax": 100
        },
        {
            "gameType": 5,
            "oddMin": 10,
            "oddMax": 100,
            "evenMin": 10,
            "evenMax": 100,
            "bigMin": 10,
            "bigMax": 100,
            "smallMin": 10,
            "smallMax": 100,
            "redMin": 10,
            "redMax": 100,
            "blackMin": 10,
            "blackMax": 100,
            "dozenMin": 10,
            "dozenMax": 100,
            "columnMin": 10,
            "columnMax": 100,
            "lineMin": 10,
            "lineMax": 100,
            "basketMin": 10,
            "basketMax": 100,
            "connerMin": 10,
            "connerMax": 100,
            "trioMin": 10,
            "trioMax": 100,
            "streetMin": 10,
            "streetMax": 100,
            "splitMin": 10,
            "splitMax": 100,
            "straightMin": 10,
            "straightMax": 100
        },
        {
            "gameType": 6,
            "betPlayer1Min": 10,
            "betPlayer1Max": 100,
            "betPlayer1DoubleMin": 10,
            "betPlayer1DoubleMax": 100,
            "betPlayer2Min": 10,
            "betPlayer2Max": 100,
            "betPlayer2DoubleMin": 10,
            "betPlayer2DoubleMax": 100,
            "betPlayer3Min": 10,
            "betPlayer3Max": 100,
            "betPlayer3DoubleMin": 10,
            "betPlayer3DoubleMax": 100
        },
        {
            "gameType": 7,
            "number_1Min": 10,
            "number_1Max": 100,
            "number_2Min": 10,
            "number_2Max": 100,
            "number_5Min": 10,
            "number_5Max": 100,
            "number_10Min": 10,
            "number_10Max": 100,
            "number_20Min": 10,
            "number_20Max": 100,
            "number_40Min": 10,
            "number_40Max": 100,
            "multipleMin": 10,
            "multipleMax": 100,
            "oddMin": 10,
            "oddMax": 100,
            "evenMin": 10,
            "evenMax": 100
        },
        {
            "gameType": 8,
            "baseBet_Min": 10,
            "baseBet_Max": 100
        },
        {
            "gameType": 9,
            "baseBet_Min": 1,
            "baseBet_Max": 100,
            "sideBet_Min": 1,
            "sideBet_Max": 100,
            "pairsBet_Min": 1,
            "pairsBet_Max": 100,
            "threecardBet_Min": 1,
            "threecardBet_Max": 100
        },
        {
            "gameType": 10,
            "oddMin": 20,
            "oddMax": 100,
            "evenMin": 20,
            "evenMax": 100,
            "bigMin": 20,
            "bigMax": 100,
            "smallMin": 20,
            "smallMax": 100,
            "redMin": 20,
            "redMax": 100,
            "blackMin": 20,
            "blackMax": 100,
            "dozenMin": 20,
            "dozenMax": 100,
            "columnMin": 20,
            "columnMax": 100,
            "lineMin": 20,
            "lineMax": 100,
            "basketMin": 20,
            "basketMax": 100,
            "connerMin": 20,
            "connerMax": 100,
            "trioMin": 20,
            "trioMax": 100,
            "streetMin": 20,
            "streetMax": 100,
            "splitMin": 20,
            "splitMax": 100,
            "straightMin": 20,
            "straightMax": 100
        },
        {
            "gameType": 11,
            "betPlayer1Min": 10,
            "betPlayer1Max": 100,
            "betPlayer2Min": 10,
            "betPlayer2Max": 100,
            "betPlayer3Min": 10,
            "betPlayer3Max": 100,
            "betPlayer4Min": 10,
            "betPlayer4Max": 100,
            "betPlayer5Min": 10,
            "betPlayer5Max": 100,
            "betPlayer1PairMin": 10,
            "betPlayer1PairMax": 100,
            "betPlayer2PairMin": 10,
            "betPlayer2PairMax": 100,
            "betPlayer3PairMin": 10,
            "betPlayer3PairMax": 100,
            "betPlayer4PairMin": 10,
            "betPlayer4PairMax": 100,
            "betPlayer5PairMin": 10,
            "betPlayer5PairMax": 100
        },
        {
            "gameType": 12,
            "biggerMin": 20,
            "biggerMax": 100,
            "smallerMin": 20,
            "smallerMax": 100,
            "sameMin": 20,
            "sameMax": 5000,
            "sum_3_4_5_6Min": 20,
            "sum_3_4_5_6Max": 100,
            "sum_7_8_9_10Min": 20,
            "sum_7_8_9_10Max": 100,
            "sum_11_12_13_14Min": 20,
            "sum_11_12_13_14Max": 100,
            "sum_15_16_17_18Min": 20,
            "sum_15_16_17_18Max": 100
        }
    ],
    "status": 200,
    "apiVersion": "1.5.94"
}
```
{% endcode %}
