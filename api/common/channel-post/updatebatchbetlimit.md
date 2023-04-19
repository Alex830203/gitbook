---
description: 批量变更用户在各游戏类型设置的投注限制清单。
---

# updateBatchBetlimit

{% hint style="danger" %}
<mark style="color:red;">不管成功与否，每次请求需间隔 10 分钟</mark>
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道ID。</td><td>RegisterOrLoginReq</td></tr><tr><td><mark style="color:red;">userList</mark></td><td><mark style="color:orange;">array</mark></td><td>用户列表。阵列值为username。阵列长度上限1000。</td><td>password</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>时间戳记。以毫秒为单位。格式为Unix Time。</td><td>1</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。 字串拼接：username+channelId+timestamp</td><td>1</td></tr><tr><td><mark style="color:red;">limit</mark></td><td><mark style="color:orange;">array</mark></td><td>限额资讯详情。阵列值为物件，下表为物件参数说明。</td><td></td></tr></tbody></table>

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% hint style="info" %}
<mark style="color:blue;">依据limit的阵列数，可变更单一游戏或多个游戏的限额资讯</mark>
{% endhint %}

limit

{% tabs %}
{% tab title="百家乐" %}
| 参数                   | 格式                                      | 描述                                                      |
| -------------------- | --------------------------------------- | ------------------------------------------------------- |
| gameType             | <mark style="color:blue;">number</mark> | <p>游戏类型。</p><p>1: 百家乐 - VIP 桌 <br>2: 百家乐 - Normal 桌</p> |
| playerMin            | <mark style="color:blue;">number</mark> | 闲 最低下注限额。                                               |
| playerMax            | <mark style="color:blue;">number</mark> | 闲 最高下注限额。                                               |
| bankerMin            | <mark style="color:blue;">number</mark> | 庄 最低下注限额。                                               |
| bankerMax            | <mark style="color:blue;">number</mark> | 庄 最高下注限额。                                               |
| tieMin               | <mark style="color:blue;">number</mark> | 和 最低下注限额。                                               |
| tieMax               | <mark style="color:blue;">number</mark> | 和 最高下注限额。                                               |
| playerPairMin        | <mark style="color:blue;">number</mark> | 闲对 最低下注限额。                                              |
| playerPairMax        | <mark style="color:blue;">number</mark> | 闲对 最高下注限额。                                              |
| bankerPairMin        | <mark style="color:blue;">number</mark> | 庄对 最低下注限额。                                              |
| bankerPairMax        | <mark style="color:blue;">number</mark> | 庄对 最高下注限额。                                              |
| bankerLucky6Min      | <mark style="color:blue;">number</mark> | 庄幸运六 最低下注限额。                                            |
| bankerLucky6Max      | <mark style="color:blue;">number</mark> | 庄幸运六 最高下注限额。                                            |
| bankerDragonBonusMin | <mark style="color:blue;">number</mark> | 庄龙宝 最低下注限额。                                             |
| bankerDragonBonusMax | <mark style="color:blue;">number</mark> | 庄龙宝 最高下注限额。                                             |
| playerDragonBonusMin | <mark style="color:blue;">number</mark> | 闲龙宝 最低下注限额。                                             |
| playerDragonBonusMax | <mark style="color:blue;">number</mark> | 闲龙宝 最高下注限额。                                             |
| bigMin               | <mark style="color:blue;">number</mark> | 大 最低下注限额                                                |
| bigMax               | <mark style="color:blue;">number</mark> | 大 最高下注限额。                                               |
| smallMin             | <mark style="color:blue;">number</mark> | 小 最低下注限额。                                               |
| smallMax             | <mark style="color:blue;">number</mark> | 小 最高下注限制。                                               |
| bankerOddMin         | <mark style="color:blue;">number</mark> | 庄单 最低下注限额。                                              |
| bankerOddMax         | <mark style="color:blue;">number</mark> | 庄单 最高下注限额。                                              |
| bankerEvenMin        | <mark style="color:blue;">number</mark> | 庄双 最低下注限额。                                              |
| bankerEvenMax        | <mark style="color:blue;">number</mark> | 庄双 最高下注限额。                                              |
| playerOddMin         | <mark style="color:blue;">number</mark> | 闲单 最低下注限额。                                              |
| playerOddMax         | <mark style="color:blue;">number</mark> | 闲单 最高下注限额。                                              |
| playerEvenMin        | <mark style="color:blue;">number</mark> | 闲双 最低下注限额。                                              |
| playerEvenMax        | <mark style="color:blue;">number</mark> | 闲双 最高下注限额。                                              |
| perfectPairMin       | <mark style="color:blue;">number</mark> | 暂时不开放使用。可以不添加这个参数。                                      |
| perfectPairMax       | <mark style="color:blue;">number</mark> | 暂时不开放使用。可以不添加这个参数。                                      |
| anyPairMin           | <mark style="color:blue;">number</mark> | 暂时不开放使用。可以不添加这个参数。                                      |
| anyPairMax           | <mark style="color:blue;">number</mark> | 暂时不开放使用。可以不添加这个参数。                                      |
| bankerNaturalMin     | <mark style="color:blue;">number</mark> | 暂时不开放使用。可以不添加这个参数。                                      |
| bankerNaturalMax     | <mark style="color:blue;">number</mark> | 暂时不开放使用。可以不添加这个参数。                                      |
| playerNaturalMin     | <mark style="color:blue;">number</mark> | 暂时不开放使用。可以不添加这个参数。                                      |
| playerNaturalMax     | <mark style="color:blue;">number</mark> | 暂时不开放使用。可以不添加这个参数。                                      |
| super6Min            | <mark style="color:blue;">number</mark> | 暂时不开放使用。可以不添加这个参数。                                      |
| super6Max            | <mark style="color:blue;">number</mark> | 暂时不开放使用。可以不添加这个参数。                                      |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "userList": [
        "demo",
        "test"
    ],
    "timestamp": 1681867216,
    "signature": "YY2gO9X5jP3OIfTT9PMngoZB8u2HOfX9Ef+TsxZ6qin+QvoNNNhyq94uGxfD0Da0BXgazvWb16uBQpgsp3WqnQ==",
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
        }
    ]
}
```
{% endcode %}
{% endtab %}

{% tab title="龙虎" %}
| 参数             | 格式                                      | 描述                       |
| -------------- | --------------------------------------- | ------------------------ |
| gameType       | <mark style="color:blue;">number</mark> | <p>游戏类型。</p><p>3: 龙虎</p> |
| dragonMin      | <mark style="color:blue;">number</mark> | 龙 最低下注限额。                |
| dragonMax      | <mark style="color:blue;">number</mark> | 龙 最高下注限额。                |
| tigerMin       | <mark style="color:blue;">number</mark> | 虎 最低下注限额。                |
| tigerMax       | <mark style="color:blue;">number</mark> | 虎 最高下注限额。                |
| tieMin         | <mark style="color:blue;">number</mark> | 和 最低下注限额。                |
| tieMax         | <mark style="color:blue;">number</mark> | 和 最高下注限额。                |
| dragonOddMin   | <mark style="color:blue;">number</mark> | 龙单 最低下注限额。               |
| dragonOddMax   | <mark style="color:blue;">number</mark> | 龙单 最高下注限额。               |
| dragonEvenMin  | <mark style="color:blue;">number</mark> | 龙双 最低下注限额。               |
| dragonEvenMax  | <mark style="color:blue;">number</mark> | 龙双 最高下注限额。               |
| tigerOddMin    | <mark style="color:blue;">number</mark> | 虎单 最低下注限额。               |
| tigerOddMax    | <mark style="color:blue;">number</mark> | 虎单 最高下注限额。               |
| tigerEvenMin   | <mark style="color:blue;">number</mark> | 虎双 最低下注限额。               |
| tigerEvenMax   | <mark style="color:blue;">number</mark> | 虎双 最高下注限额。               |
| dragonBlackMin | <mark style="color:blue;">number</mark> | 龙黑 最低下注限额。               |
| dragonBlackMax | <mark style="color:blue;">number</mark> | 龙黑 最高下注限额。               |
| dragonRedMin   | <mark style="color:blue;">number</mark> | 龙红 最低下注限额。               |
| dragonRedMax   | <mark style="color:blue;">number</mark> | 龙红 最高下注限额。               |
| tigerBlackMin  | <mark style="color:blue;">number</mark> | 虎黑 最低下注限额。               |
| tigerBlackMax  | <mark style="color:blue;">number</mark> | 虎黑 最高下注限额。               |
| tigerRedMin    | <mark style="color:blue;">number</mark> | 虎红 最低下注限额。               |
| tigerRedMax    | <mark style="color:blue;">number</mark> | 虎红 最高下注限额。               |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "userList": [
        "demo",
        "test"
    ],
    "timestamp": 1681867216,
    "signature": "YY2gO9X5jP3OIfTT9PMngoZB8u2HOfX9Ef+TsxZ6qin+QvoNNNhyq94uGxfD0Da0BXgazvWb16uBQpgsp3WqnQ==",
    "limit": [
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
        }
    ]
}
```
{% endcode %}
{% endtab %}

{% tab title="骰子游戏" %}
| 参数             | 格式                                      | 描述                                           |
| -------------- | --------------------------------------- | -------------------------------------------- |
| gameType       | <mark style="color:blue;">number</mark> | <p>游戏类型。</p><p>4: 骰子游戏</p>                   |
| oddMin         | <mark style="color:blue;">number</mark> | 单 最低下注限额。                                    |
| oddMax         | <mark style="color:blue;">number</mark> | 单 最高下注限额。                                    |
| evenMin        | <mark style="color:blue;">number</mark> | 双 最低下注限额。                                    |
| evenMax        | <mark style="color:blue;">number</mark> | 双 最高下注限额。                                    |
| bigMin         | <mark style="color:blue;">number</mark> | 大 最低下注限额。                                    |
| bigMax         | <mark style="color:blue;">number</mark> | 大 最高下注限额。                                    |
| smallMin       | <mark style="color:blue;">number</mark> | 小 最低下注限额。                                    |
| smallMax       | <mark style="color:blue;">number</mark> | 小 最高下注限额。                                    |
| pairMin        | <mark style="color:blue;">number</mark> | 对子1-6 最低下注限额。                                |
| pairMax        | <mark style="color:blue;">number</mark> | 对子1-6 最高下注限额。                                |
| tripMin        | <mark style="color:blue;">number</mark> | <p>围骰1-6 最低下注限额。<br>可以使用此参数名称：tripleMin。</p> |
| tripMax        | <mark style="color:blue;">number</mark> | <p>围骰1-6 最高下注限额。<br>可以使用此参数名称：tripleMax。</p> |
| allTripMin     | <mark style="color:blue;">number</mark> | <p>全围 最低下注限额。<br>可以使用此参数名称：allTripleMin。</p> |
| allTripMax     | <mark style="color:blue;">number</mark> | <p>全围 最高下注限额。<br>可以使用此参数名称：allTripleMax。</p> |
| fourMin        | <mark style="color:blue;">number</mark> | 4点 最低下注限额。                                   |
| fourMax        | <mark style="color:blue;">number</mark> | 4点 最高下注限额。                                   |
| fiveMin        | <mark style="color:blue;">number</mark> | 5点 最低下注限额。                                   |
| fiveMax        | <mark style="color:blue;">number</mark> | 5点 最高下注限额。                                   |
| sixMin         | <mark style="color:blue;">number</mark> | 6点 最低下注限额。                                   |
| sixMax         | <mark style="color:blue;">number</mark> | 6点 最高下注限额。                                   |
| sevenMin       | <mark style="color:blue;">number</mark> | 7点 最低下注限额。                                   |
| sevenMax       | <mark style="color:blue;">number</mark> | 7点 最高下注限额。                                   |
| eightMin       | <mark style="color:blue;">number</mark> | 8点 最低下注限额。                                   |
| eightMax       | <mark style="color:blue;">number</mark> | 8点 最高下注限额。                                   |
| nineMin        | <mark style="color:blue;">number</mark> | 9点 最低下注限额。                                   |
| nineMax        | <mark style="color:blue;">number</mark> | 9点 最高下注限额。                                   |
| tenMin         | <mark style="color:blue;">number</mark> | 10点 最低下注限额。                                  |
| tenMax         | <mark style="color:blue;">number</mark> | 10点 最高下注限额。                                  |
| elevenMin      | <mark style="color:blue;">number</mark> | 11点 最低下注限额。                                  |
| elevenMax      | <mark style="color:blue;">number</mark> | 11点 最高下注限额。                                  |
| twelveMin      | <mark style="color:blue;">number</mark> | 12点 最低下注限额。                                  |
| twelveMax      | <mark style="color:blue;">number</mark> | 12点 最高下注限额。                                  |
| thirteenMin    | <mark style="color:blue;">number</mark> | 13点 最低下注限额。                                  |
| thirteenMax    | <mark style="color:blue;">number</mark> | 13点 最高下注限额。                                  |
| fourteenMin    | <mark style="color:blue;">number</mark> | 14点 最低下注限额。                                  |
| fourteenMax    | <mark style="color:blue;">number</mark> | 14点 最高下注限额。                                  |
| fifteenMin     | <mark style="color:blue;">number</mark> | 15点 最低下注限额。                                  |
| fifteenMax     | <mark style="color:blue;">number</mark> | 15点 最高下注限额。                                  |
| sixteenMin     | <mark style="color:blue;">number</mark> | 16点 最低下注限额。                                  |
| sixteenMax     | <mark style="color:blue;">number</mark> | 16点 最高下注限额。                                  |
| seventeenMin   | <mark style="color:blue;">number</mark> | 17点 最低下注限额。                                  |
| seventeenMax   | <mark style="color:blue;">number</mark> | 17点 最高下注限额。                                  |
| singleDiceMin  | <mark style="color:blue;">number</mark> | 单点数1-6 最低下注限额。                               |
| singleDiceMax  | <mark style="color:blue;">number</mark> | 单点数1-6 最高下注限额。                               |
| combinationMin | <mark style="color:blue;">number</mark> | 组合 最低下注限额。                                   |
| combinationMax | <mark style="color:blue;">number</mark> | 组合 最高下注限额。                                   |
| moreLeftMin    | <mark style="color:blue;">number</mark> | 二同号 最低下注限额。                                  |
| moreLeftMax    | <mark style="color:blue;">number</mark> | 二同号 最高下注限额。                                  |
| moreRightMin   | <mark style="color:blue;">number</mark> | 三不同 最低下注限额。                                  |
| moreRightMax   | <mark style="color:blue;">number</mark> | 三不同 最高下注限额。                                  |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "userList": [
        "demo",
        "test"
    ],
    "timestamp": 1681867216,
    "signature": "YY2gO9X5jP3OIfTT9PMngoZB8u2HOfX9Ef+TsxZ6qin+QvoNNNhyq94uGxfD0Da0BXgazvWb16uBQpgsp3WqnQ==",
    "limit": [
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
        }
    ]
}
```
{% endcode %}
{% endtab %}

{% tab title="轮盘" %}
| 参数          | 格式                                      | 描述                                        |
| ----------- | --------------------------------------- | ----------------------------------------- |
| gameType    | <mark style="color:blue;">number</mark> | <p>游戏类型。</p><p>5: 轮盘<br>10: 财富轮盘</p>      |
| oddMin      | <mark style="color:blue;">number</mark> | 单 最低下注限额。                                 |
| oddMax      | <mark style="color:blue;">number</mark> | 单 最高下注限额。                                 |
| evenMin     | <mark style="color:blue;">number</mark> | 双 最低下注限额。                                 |
| evenMax     | <mark style="color:blue;">number</mark> | 双 最高下注限额。                                 |
| bigMin      | <mark style="color:blue;">number</mark> | 大 最低下注限额。                                 |
| bigMax      | <mark style="color:blue;">number</mark> | 大 最高下注限额。                                 |
| smallMin    | <mark style="color:blue;">number</mark> | 小 最低下注限额。                                 |
| smallMax    | <mark style="color:blue;">number</mark> | 小 最高下注限额。                                 |
| redMin      | <mark style="color:blue;">number</mark> | 红 最低下注限额。                                 |
| redMax      | <mark style="color:blue;">number</mark> | 红 最高下注限额。                                 |
| blackMin    | <mark style="color:blue;">number</mark> | 黑 最低下注限额。                                 |
| blackMax    | <mark style="color:blue;">number</mark> | 黑 最高下注限额。                                 |
| dozenMin    | <mark style="color:blue;">number</mark> | 打注 最低下注限额。                                |
| dozenMax    | <mark style="color:blue;">number</mark> | 打注 最高下注限额。                                |
| columnMin   | <mark style="color:blue;">number</mark> | 列注 最低下注限额。                                |
| columnMax   | <mark style="color:blue;">number</mark> | 列注 最高下注限额。                                |
| lineMin     | <mark style="color:blue;">number</mark> | 线注 最低下注限额。                                |
| lineMax     | <mark style="color:blue;">number</mark> | 线注 最高下注限额。                                |
| basketMin   | <mark style="color:blue;">number</mark> | 四个号码 最低下注限额。                              |
| basketMax   | <mark style="color:blue;">number</mark> | 四个号码 最高下注限额。                              |
| connerMin   | <mark style="color:blue;">number</mark> | <p>角注 最低下注限额。<br>可以使用此参数名称：cornerMin。</p> |
| connerMax   | <mark style="color:blue;">number</mark> | <p>角注 最高下注限额。<br>可以使用此参数名称：cornerMax。</p> |
| trioMin     | <mark style="color:blue;">number</mark> | 三数 最低下注限额。                                |
| trioMax     | <mark style="color:blue;">number</mark> | 三数 最高下注限额。                                |
| streetMin   | <mark style="color:blue;">number</mark> | 街注 最低下注限额。                                |
| streetMax   | <mark style="color:blue;">number</mark> | 街注 最高下注限额。                                |
| splitMin    | <mark style="color:blue;">number</mark> | 分注 最低下注限额。                                |
| splitMax    | <mark style="color:blue;">number</mark> | 分注 最高下注限额。                                |
| straightMin | <mark style="color:blue;">number</mark> | 直接注 最低下注限额。                               |
| straightMax | <mark style="color:blue;">number</mark> | 直接注 最高下注限额。                               |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "userList": [
        "demo",
        "test"
    ],
    "timestamp": 1681867216,
    "signature": "YY2gO9X5jP3OIfTT9PMngoZB8u2HOfX9Ef+TsxZ6qin+QvoNNNhyq94uGxfD0Da0BXgazvWb16uBQpgsp3WqnQ==",
    "limit": [
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
        }
    ]
}
```
{% endcode %}
{% endtab %}

{% tab title="牛牛" %}
| 参数                  | 格式                                      | 描述                       |
| ------------------- | --------------------------------------- | ------------------------ |
| gameType            | <mark style="color:blue;">number</mark> | <p>游戏类型。</p><p>6: 牛牛</p> |
| betPlayer1Min       | <mark style="color:blue;">number</mark> | 闲1 最低下注限额。               |
| betPlayer1Max       | <mark style="color:blue;">number</mark> | 闲1 最高下注限额。               |
| betPlayer1DoubleMin | <mark style="color:blue;">number</mark> | 闲1翻倍 最低下注限额。             |
| betPlayer1DoubleMax | <mark style="color:blue;">number</mark> | 闲1翻倍 最高下注限额。             |
| betPlayer2Min       | <mark style="color:blue;">number</mark> | 闲2 最低下注限额。               |
| betPlayer2Max       | <mark style="color:blue;">number</mark> | 闲2 最高下注限额。               |
| betPlayer2DoubleMin | <mark style="color:blue;">number</mark> | 闲2翻倍 最低下注限额。             |
| betPlayer2DoubleMax | <mark style="color:blue;">number</mark> | 闲2翻倍 最高下注限额。             |
| betPlayer3Min       | <mark style="color:blue;">number</mark> | 闲3 最低下注限额。               |
| betPlayer3Max       | <mark style="color:blue;">number</mark> | 闲3 最高下注限额。               |
| betPlayer3DoubleMin | <mark style="color:blue;">number</mark> | 闲3翻倍 最低下注限额。             |
| betPlayer3DoubleMax | <mark style="color:blue;">number</mark> | 闲3翻倍 最高下注限额。             |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "userList": [
        "demo",
        "test"
    ],
    "timestamp": 1681867216,
    "signature": "YY2gO9X5jP3OIfTT9PMngoZB8u2HOfX9Ef+TsxZ6qin+QvoNNNhyq94uGxfD0Da0BXgazvWb16uBQpgsp3WqnQ==",
    "limit": [
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
        }
    ]
}
```
{% endcode %}
{% endtab %}

{% tab title="财富大转盘" %}
| 参数            | 格式                                      | 描述                          |
| ------------- | --------------------------------------- | --------------------------- |
| gameType      | <mark style="color:blue;">number</mark> | <p>游戏类型。</p><p>7: 财富大转盘</p> |
| number\_1Min  | <mark style="color:blue;">number</mark> | 号码1 最低下注限额。                 |
| number\_1Max  | <mark style="color:blue;">number</mark> | 号码1 最高下注限额。                 |
| number\_2Min  | <mark style="color:blue;">number</mark> | 号码2 最低下注限额。                 |
| number\_2Max  | <mark style="color:blue;">number</mark> | 号码2 最高下注限额。                 |
| number\_5Min  | <mark style="color:blue;">number</mark> | 号码5 最低下注限额。                 |
| number\_5Max  | <mark style="color:blue;">number</mark> | 号码5 最高下注限额。                 |
| number\_10Min | <mark style="color:blue;">number</mark> | 号码10 最低下注限额。                |
| number\_10Max | <mark style="color:blue;">number</mark> | 号码10 最高下注限额。                |
| number\_20Min | <mark style="color:blue;">number</mark> | 号码20 最低下注限额。                |
| number\_20Max | <mark style="color:blue;">number</mark> | 号码20 最高下注限额。                |
| number\_40Min | <mark style="color:blue;">number</mark> | 号码40 最低下注限额。                |
| number\_40Max | <mark style="color:blue;">number</mark> | 号码40 最高下注限额。                |
| multipleMin   | <mark style="color:blue;">number</mark> | 2X/8X 最低下注限额。               |
| multipleMax   | <mark style="color:blue;">number</mark> | 2X/8X 最高下注限额。               |
| oddMin        | <mark style="color:blue;">number</mark> | 单 最低下注限额。                   |
| oddMax        | <mark style="color:blue;">number</mark> | 单 最高下注限额。                   |
| evenMin       | <mark style="color:blue;">number</mark> | 双 最低下注限额。                   |
| evenMax       | <mark style="color:blue;">number</mark> | 双 最高下注限额。                   |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "userList": [
        "demo",
        "test"
    ],
    "timestamp": 1681867216,
    "signature": "YY2gO9X5jP3OIfTT9PMngoZB8u2HOfX9Ef+TsxZ6qin+QvoNNNhyq94uGxfD0Da0BXgazvWb16uBQpgsp3WqnQ==",
    "limit": [
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
        }
    ]
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="电子21点" %}
| 参数           | 格式                                      | 描述                          |
| ------------ | --------------------------------------- | --------------------------- |
| gameType     | <mark style="color:blue;">number</mark> | <p>游戏类型。</p><p>8: 电子21点</p> |
| baseBet\_Min | <mark style="color:blue;">number</mark> | 投注/底注 最低下注限额。               |
| baseBet\_Max | <mark style="color:blue;">number</mark> | 投注/底注 最高下注限额。               |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "userList": [
        "demo",
        "test"
    ],
    "timestamp": 1681867216,
    "signature": "YY2gO9X5jP3OIfTT9PMngoZB8u2HOfX9Ef+TsxZ6qin+QvoNNNhyq94uGxfD0Da0BXgazvWb16uBQpgsp3WqnQ==",
    "limit": [
        {
            "gameType": 8,
            "baseBet_Min": 10,
            "baseBet_Max": 100
        }
    ]
}
```
{% endcode %}
{% endtab %}

{% tab title="真人21点" %}
| 参数                | 格式                                      | 描述                          |
| ----------------- | --------------------------------------- | --------------------------- |
| gameType          | <mark style="color:blue;">number</mark> | <p>游戏类型。</p><p>9: 真人21点</p> |
| baseBet\_Min      | <mark style="color:blue;">number</mark> | 投注/底注 最低下注限额。               |
| baseBet\_Max      | <mark style="color:blue;">number</mark> | 投注/底注 最高下注限额。               |
| sideBet\_Min      | <mark style="color:blue;">number</mark> | 旁注 最低下注限额。                  |
| sideBet\_Max      | <mark style="color:blue;">number</mark> | 旁注 最高下注限额。                  |
| pairsBet\_Min     | <mark style="color:blue;">number</mark> | 完美对子 最低下注限额。                |
| pairsBet\_Max     | <mark style="color:blue;">number</mark> | 完美对子 最高下注限额。                |
| threecardBet\_Min | <mark style="color:blue;">number</mark> | 21+3 最低下注限额。                |
| threecardBet\_Max | <mark style="color:blue;">number</mark> | 21+3 最高下注限额。                |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "userList": [
        "demo",
        "test"
    ],
    "timestamp": 1681867216,
    "signature": "YY2gO9X5jP3OIfTT9PMngoZB8u2HOfX9Ef+TsxZ6qin+QvoNNNhyq94uGxfD0Da0BXgazvWb16uBQpgsp3WqnQ==",
    "limit": [
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
        }
    ]
}
```
{% endcode %}
{% endtab %}

{% tab title="真人博丁" %}
| 参数                | 格式                                      | 描述                          |
| ----------------- | --------------------------------------- | --------------------------- |
| gameType          | <mark style="color:blue;">number</mark> | <p>游戏类型。</p><p>11: 真人博丁</p> |
| betPlayer1Min     | <mark style="color:blue;">number</mark> | 闲1 最低下注限额。                  |
| betPlayer1Max     | <mark style="color:blue;">number</mark> | 闲1 最高下注限额。                  |
| betPlayer2Min     | <mark style="color:blue;">number</mark> | 闲2 最低下注限额。                  |
| betPlayer2Max     | <mark style="color:blue;">number</mark> | 闲2 最高下注限额。                  |
| betPlayer3Min     | <mark style="color:blue;">number</mark> | 闲3 最低下注限额。                  |
| betPlayer3Max     | <mark style="color:blue;">number</mark> | 闲3 最高下注限额。                  |
| betPlayer4Min     | <mark style="color:blue;">number</mark> | 闲4 最低下注限额。                  |
| betPlayer4Max     | <mark style="color:blue;">number</mark> | 闲4 最高下注限额。                  |
| betPlayer5Min     | <mark style="color:blue;">number</mark> | 闲5 最低下注限额。                  |
| betPlayer5Max     | <mark style="color:blue;">number</mark> | 闲5 最高下注限额。                  |
| betPlayer1PairMin | <mark style="color:blue;">number</mark> | 闲1对 最低下注限额。                 |
| betPlayer1PairMax | <mark style="color:blue;">number</mark> | 闲1对 最高下注限额。                 |
| betPlayer2PairMin | <mark style="color:blue;">number</mark> | 闲2对 最低下注限额。                 |
| betPlayer2PairMax | <mark style="color:blue;">number</mark> | 闲2对 最高下注限额。                 |
| betPlayer3PairMin | <mark style="color:blue;">number</mark> | 闲3对 最低下注限额。                 |
| betPlayer3PairMax | <mark style="color:blue;">number</mark> | 闲3对 最高下注限额。                 |
| betPlayer4PairMin | <mark style="color:blue;">number</mark> | 闲4对 最低下注限额。                 |
| betPlayer4PairMax | <mark style="color:blue;">number</mark> | 闲4对 最高下注限额。                 |
| betPlayer5PairMin | <mark style="color:blue;">number</mark> | 闲5对 最低下注限额。                 |
| betPlayer5PairMax | <mark style="color:blue;">number</mark> | 闲5对 最高下注限额。                 |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "userList": [
        "demo",
        "test"
    ],
    "timestamp": 1681867216,
    "signature": "YY2gO9X5jP3OIfTT9PMngoZB8u2HOfX9Ef+TsxZ6qin+QvoNNNhyq94uGxfD0Da0BXgazvWb16uBQpgsp3WqnQ==",
    "limit": [
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
        }
    ]
}
```
{% endcode %}
{% endtab %}

{% tab title="Hi-Lo" %}
| 参数                     | 格式                                      | 描述                           |
| ---------------------- | --------------------------------------- | ---------------------------- |
| gameType               | <mark style="color:blue;">number</mark> | <p>游戏类型。</p><p>12: Hi-Lo</p> |
| biggerMin              | <mark style="color:blue;">number</mark> | 更大 最低下注限额。                   |
| biggerMax              | <mark style="color:blue;">number</mark> | 更大 最高下注限额。                   |
| smallerMin             | <mark style="color:blue;">number</mark> | 更小 最低下注限额。                   |
| smallerMax             | <mark style="color:blue;">number</mark> | 更小 最高下注限额。                   |
| sameMin                | <mark style="color:blue;">number</mark> | 同点 最低下注限额。                   |
| sameMax                | <mark style="color:blue;">number</mark> | 同点 最高下注限额。                   |
| sum\_3\_4\_5\_6Min     | <mark style="color:blue;">number</mark> | 3、4、5、6 最低下注限额。              |
| sum\_3\_4\_5\_6Max     | <mark style="color:blue;">number</mark> | 3、4、5、6 最高下注限额。              |
| sum\_7\_8\_9\_10Min    | <mark style="color:blue;">number</mark> | 7、8、9、10 最低下注限额。             |
| sum\_7\_8\_9\_10Max    | <mark style="color:blue;">number</mark> | 7、8、9、10 最高下注限额。             |
| sum\_11\_12\_13\_14Min | <mark style="color:blue;">number</mark> | 11、12、13、14 最低下注限额。          |
| sum\_11\_12\_13\_14Max | <mark style="color:blue;">number</mark> | 11、12、13、14 最高下注限额。          |
| sum\_15\_16\_17\_18Min | <mark style="color:blue;">number</mark> | 15、16、17、18 最低下注限额。          |
| sum\_15\_16\_17\_18Max | <mark style="color:blue;">number</mark> | 15、16、17、18 最高下注限额。          |

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "userList": [
        "demo",
        "test"
    ],
    "timestamp": 1681867216,
    "signature": "YY2gO9X5jP3OIfTT9PMngoZB8u2HOfX9Ef+TsxZ6qin+QvoNNNhyq94uGxfD0Da0BXgazvWb16uBQpgsp3WqnQ==",
    "limit": [
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
    ]
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>updateGameList</td><td><mark style="color:orange;">array</mark></td><td>更新投注限额游戏。阵列值为gameType。</td><td>预设随机生成</td></tr><tr><td>userList</td><td><mark style="color:blue;">number</mark></td><td>用户列表。阵列值为username。阵列长度上限1000。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道ID。</td><td>200</td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>eBET回应状态。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>0
</code></pre></td></tr></tbody></table>

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "updateGameList": [
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
    "userList": [
        "demo",
        "test"
    ],
    "channelId": 1,
    "status": 200,
    "apiVersion": "1.5.75"
}
```
{% endcode %}
