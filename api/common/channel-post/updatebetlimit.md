---
description: 变更单一用户的各游戏投注限制清单
---

# updatebetlimit

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="153">参数</th><th width="122">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道ID。</td><td>RegisterOrLoginReq</td></tr><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td>password</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>时间戳记。以毫秒为单位。格式为Unix Time。</td><td>1</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。 字串拼接：username+channelId+timestamp</td><td>1</td></tr><tr><td><mark style="color:red;">limit</mark></td><td><mark style="color:blue;">array</mark></td><td>限额资讯详情。阵列值为物件，下表为物件参数说明。</td><td></td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% hint style="info" %}
<mark style="color:blue;">依据limit的阵列数，可变更单一游戏或多个游戏的限额资讯</mark>
{% endhint %}

limit

{% tabs %}
{% tab title="百家乐" %}
<table><thead><tr><th width="217">参数</th><th width="119.66666666666666">格式</th><th>描述</th></tr></thead><tbody><tr><td>gameType</td><td><mark style="color:blue;">number</mark></td><td><p>游戏类型。</p><p>1: 百家乐 - VIP 桌 <br>2: 百家乐 - Normal 桌</p></td></tr><tr><td>playerMin</td><td><mark style="color:blue;">number</mark></td><td>闲 最低下注限额。</td></tr><tr><td>playerMax</td><td><mark style="color:blue;">number</mark></td><td>闲 最高下注限额。</td></tr><tr><td>bankerMin</td><td><mark style="color:blue;">number</mark></td><td>庄 最低下注限额。</td></tr><tr><td>bankerMax</td><td><mark style="color:blue;">number</mark></td><td>庄 最高下注限额。</td></tr><tr><td>tieMin</td><td><mark style="color:blue;">number</mark></td><td>和 最低下注限额。</td></tr><tr><td>tieMax</td><td><mark style="color:blue;">number</mark></td><td>和 最高下注限额。</td></tr><tr><td>playerPairMin</td><td><mark style="color:blue;">number</mark></td><td>闲对 最低下注限额。</td></tr><tr><td>playerPairMax</td><td><mark style="color:blue;">number</mark></td><td>闲对 最高下注限额。</td></tr><tr><td>bankerPairMin</td><td><mark style="color:blue;">number</mark></td><td>庄对 最低下注限额。</td></tr><tr><td>bankerPairMax</td><td><mark style="color:blue;">number</mark></td><td>庄对 最高下注限额。</td></tr><tr><td>bankerLucky6Min</td><td><mark style="color:blue;">number</mark></td><td>庄幸运六 最低下注限额。</td></tr><tr><td>bankerLucky6Max</td><td><mark style="color:blue;">number</mark></td><td>庄幸运六 最高下注限额。</td></tr><tr><td>bankerDragonBonusMin</td><td><mark style="color:blue;">number</mark></td><td>庄龙宝 最低下注限额。</td></tr><tr><td>bankerDragonBonusMax</td><td><mark style="color:blue;">number</mark></td><td>庄龙宝 最高下注限额。</td></tr><tr><td>playerDragonBonusMin</td><td><mark style="color:blue;">number</mark></td><td>闲龙宝 最低下注限额。</td></tr><tr><td>playerDragonBonusMax</td><td><mark style="color:blue;">number</mark></td><td>闲龙宝 最高下注限额。</td></tr><tr><td>bigMin</td><td><mark style="color:blue;">number</mark></td><td>大 最低下注限额</td></tr><tr><td>bigMax</td><td><mark style="color:blue;">number</mark></td><td>大 最高下注限额。</td></tr><tr><td>smallMin</td><td><mark style="color:blue;">number</mark></td><td>小 最低下注限额。</td></tr><tr><td>smallMax</td><td><mark style="color:blue;">number</mark></td><td>小 最高下注限制。</td></tr><tr><td>bankerOddMin</td><td><mark style="color:blue;">number</mark></td><td>庄单 最低下注限额。</td></tr><tr><td>bankerOddMax</td><td><mark style="color:blue;">number</mark></td><td>庄单 最高下注限额。</td></tr><tr><td>bankerEvenMin</td><td><mark style="color:blue;">number</mark></td><td>庄双 最低下注限额。</td></tr><tr><td>bankerEvenMax</td><td><mark style="color:blue;">number</mark></td><td>庄双 最高下注限额。</td></tr><tr><td>playerOddMin</td><td><mark style="color:blue;">number</mark></td><td>闲单 最低下注限额。</td></tr><tr><td>playerOddMax</td><td><mark style="color:blue;">number</mark></td><td>闲单 最高下注限额。</td></tr><tr><td>playerEvenMin</td><td><mark style="color:blue;">number</mark></td><td>闲双 最低下注限额。</td></tr><tr><td>playerEvenMax</td><td><mark style="color:blue;">number</mark></td><td>闲双 最高下注限额。</td></tr><tr><td>perfectPairMin</td><td><mark style="color:blue;">number</mark></td><td>暂时不开放使用。可以不添加这个参数。</td></tr><tr><td>perfectPairMax</td><td><mark style="color:blue;">number</mark></td><td>暂时不开放使用。可以不添加这个参数。</td></tr><tr><td>anyPairMin</td><td><mark style="color:blue;">number</mark></td><td>暂时不开放使用。可以不添加这个参数。</td></tr><tr><td>anyPairMax</td><td><mark style="color:blue;">number</mark></td><td>暂时不开放使用。可以不添加这个参数。</td></tr><tr><td>bankerNaturalMin</td><td><mark style="color:blue;">number</mark></td><td>暂时不开放使用。可以不添加这个参数。</td></tr><tr><td>bankerNaturalMax</td><td><mark style="color:blue;">number</mark></td><td>暂时不开放使用。可以不添加这个参数。</td></tr><tr><td>playerNaturalMin</td><td><mark style="color:blue;">number</mark></td><td>暂时不开放使用。可以不添加这个参数。</td></tr><tr><td>playerNaturalMax</td><td><mark style="color:blue;">number</mark></td><td>暂时不开放使用。可以不添加这个参数。</td></tr><tr><td>super6Min</td><td><mark style="color:blue;">number</mark></td><td>暂时不开放使用。可以不添加这个参数。</td></tr><tr><td>super6Max</td><td><mark style="color:blue;">number</mark></td><td>暂时不开放使用。可以不添加这个参数。</td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
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
<table><thead><tr><th width="217">参数</th><th width="119.66666666666666">格式</th><th>描述</th></tr></thead><tbody><tr><td>gameType</td><td><mark style="color:blue;">number</mark></td><td><p>游戏类型。</p><p>3: 龙虎</p></td></tr><tr><td>dragonMin</td><td><mark style="color:blue;">number</mark></td><td>龙 最低下注限额。</td></tr><tr><td>dragonMax</td><td><mark style="color:blue;">number</mark></td><td>龙 最高下注限额。</td></tr><tr><td>tigerMin</td><td><mark style="color:blue;">number</mark></td><td>虎 最低下注限额。</td></tr><tr><td>tigerMax</td><td><mark style="color:blue;">number</mark></td><td>虎 最高下注限额。</td></tr><tr><td>tieMin</td><td><mark style="color:blue;">number</mark></td><td>和 最低下注限额。</td></tr><tr><td>tieMax</td><td><mark style="color:blue;">number</mark></td><td>和 最高下注限额。</td></tr><tr><td>dragonOddMin</td><td><mark style="color:blue;">number</mark></td><td>龙单 最低下注限额。</td></tr><tr><td>dragonOddMax</td><td><mark style="color:blue;">number</mark></td><td>龙单 最高下注限额。</td></tr><tr><td>dragonEvenMin</td><td><mark style="color:blue;">number</mark></td><td>龙双 最低下注限额。</td></tr><tr><td>dragonEvenMax</td><td><mark style="color:blue;">number</mark></td><td>龙双 最高下注限额。</td></tr><tr><td>tigerOddMin</td><td><mark style="color:blue;">number</mark></td><td>虎单 最低下注限额。</td></tr><tr><td>tigerOddMax</td><td><mark style="color:blue;">number</mark></td><td>虎单 最高下注限额。</td></tr><tr><td>tigerEvenMin</td><td><mark style="color:blue;">number</mark></td><td>虎双 最低下注限额。</td></tr><tr><td>tigerEvenMax</td><td><mark style="color:blue;">number</mark></td><td>虎双 最高下注限额。</td></tr><tr><td>dragonBlackMin</td><td><mark style="color:blue;">number</mark></td><td>龙黑 最低下注限额。</td></tr><tr><td>dragonBlackMax</td><td><mark style="color:blue;">number</mark></td><td>龙黑 最高下注限额。</td></tr><tr><td>dragonRedMin</td><td><mark style="color:blue;">number</mark></td><td>龙红 最低下注限额。</td></tr><tr><td>dragonRedMax</td><td><mark style="color:blue;">number</mark></td><td>龙红 最高下注限额。</td></tr><tr><td>tigerBlackMin</td><td><mark style="color:blue;">number</mark></td><td>虎黑 最低下注限额。</td></tr><tr><td>tigerBlackMax</td><td><mark style="color:blue;">number</mark></td><td>虎黑 最高下注限额。</td></tr><tr><td>tigerRedMin</td><td><mark style="color:blue;">number</mark></td><td>虎红 最低下注限额。</td></tr><tr><td>tigerRedMax</td><td><mark style="color:blue;">number</mark></td><td>虎红 最高下注限额。</td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
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
<table><thead><tr><th width="217">参数</th><th width="119.66666666666666">格式</th><th>描述</th></tr></thead><tbody><tr><td>gameType</td><td><mark style="color:blue;">number</mark></td><td><p>游戏类型。</p><p>4: 骰子游戏</p></td></tr><tr><td>oddMin</td><td><mark style="color:blue;">number</mark></td><td>单 最低下注限额。</td></tr><tr><td>oddMax</td><td><mark style="color:blue;">number</mark></td><td>单 最高下注限额。</td></tr><tr><td>evenMin</td><td><mark style="color:blue;">number</mark></td><td>双 最低下注限额。</td></tr><tr><td>evenMax</td><td><mark style="color:blue;">number</mark></td><td>双 最高下注限额。</td></tr><tr><td>bigMin</td><td><mark style="color:blue;">number</mark></td><td>大 最低下注限额。</td></tr><tr><td>bigMax</td><td><mark style="color:blue;">number</mark></td><td>大 最高下注限额。</td></tr><tr><td>smallMin</td><td><mark style="color:blue;">number</mark></td><td>小 最低下注限额。</td></tr><tr><td>smallMax</td><td><mark style="color:blue;">number</mark></td><td>小 最高下注限额。</td></tr><tr><td>pairMin</td><td><mark style="color:blue;">number</mark></td><td>对子1-6 最低下注限额。</td></tr><tr><td>pairMax</td><td><mark style="color:blue;">number</mark></td><td>对子1-6 最高下注限额。</td></tr><tr><td>tripMin</td><td><mark style="color:blue;">number</mark></td><td>围骰1-6 最低下注限额。<br>可以使用此参数名称：tripleMin。</td></tr><tr><td>tripMax</td><td><mark style="color:blue;">number</mark></td><td>围骰1-6 最高下注限额。<br>可以使用此参数名称：tripleMax。</td></tr><tr><td>allTripMin</td><td><mark style="color:blue;">number</mark></td><td>全围 最低下注限额。<br>可以使用此参数名称：allTripleMin。</td></tr><tr><td>allTripMax</td><td><mark style="color:blue;">number</mark></td><td>全围 最高下注限额。<br>可以使用此参数名称：allTripleMax。</td></tr><tr><td>fourMin</td><td><mark style="color:blue;">number</mark></td><td>4点 最低下注限额。</td></tr><tr><td>fourMax</td><td><mark style="color:blue;">number</mark></td><td>4点 最高下注限额。</td></tr><tr><td>fiveMin</td><td><mark style="color:blue;">number</mark></td><td>5点 最低下注限额。</td></tr><tr><td>fiveMax</td><td><mark style="color:blue;">number</mark></td><td>5点 最高下注限额。</td></tr><tr><td>sixMin</td><td><mark style="color:blue;">number</mark></td><td>6点 最低下注限额。</td></tr><tr><td>sixMax</td><td><mark style="color:blue;">number</mark></td><td>6点 最高下注限额。</td></tr><tr><td>sevenMin</td><td><mark style="color:blue;">number</mark></td><td>7点 最低下注限额。</td></tr><tr><td>sevenMax</td><td><mark style="color:blue;">number</mark></td><td>7点 最高下注限额。</td></tr><tr><td>eightMin</td><td><mark style="color:blue;">number</mark></td><td>8点 最低下注限额。</td></tr><tr><td>eightMax</td><td><mark style="color:blue;">number</mark></td><td>8点 最高下注限额。</td></tr><tr><td>nineMin</td><td><mark style="color:blue;">number</mark></td><td>9点 最低下注限额。</td></tr><tr><td>nineMax</td><td><mark style="color:blue;">number</mark></td><td>9点 最高下注限额。</td></tr><tr><td>tenMin</td><td><mark style="color:blue;">number</mark></td><td>10点 最低下注限额。</td></tr><tr><td>tenMax</td><td><mark style="color:blue;">number</mark></td><td>10点 最高下注限额。</td></tr><tr><td>elevenMin</td><td><mark style="color:blue;">number</mark></td><td>11点 最低下注限额。</td></tr><tr><td>elevenMax</td><td><mark style="color:blue;">number</mark></td><td>11点 最高下注限额。</td></tr><tr><td>twelveMin</td><td><mark style="color:blue;">number</mark></td><td>12点 最低下注限额。</td></tr><tr><td>twelveMax</td><td><mark style="color:blue;">number</mark></td><td>12点 最高下注限额。</td></tr><tr><td>thirteenMin</td><td><mark style="color:blue;">number</mark></td><td>13点 最低下注限额。</td></tr><tr><td>thirteenMax</td><td><mark style="color:blue;">number</mark></td><td>13点 最高下注限额。</td></tr><tr><td>fourteenMin</td><td><mark style="color:blue;">number</mark></td><td>14点 最低下注限额。</td></tr><tr><td>fourteenMax</td><td><mark style="color:blue;">number</mark></td><td>14点 最高下注限额。</td></tr><tr><td>fifteenMin</td><td><mark style="color:blue;">number</mark></td><td>15点 最低下注限额。</td></tr><tr><td>fifteenMax</td><td><mark style="color:blue;">number</mark></td><td>15点 最高下注限额。</td></tr><tr><td>sixteenMin</td><td><mark style="color:blue;">number</mark></td><td>16点 最低下注限额。</td></tr><tr><td>sixteenMax</td><td><mark style="color:blue;">number</mark></td><td>16点 最高下注限额。</td></tr><tr><td>seventeenMin</td><td><mark style="color:blue;">number</mark></td><td>17点 最低下注限额。</td></tr><tr><td>seventeenMax</td><td><mark style="color:blue;">number</mark></td><td>17点 最高下注限额。</td></tr><tr><td>singleDiceMin</td><td><mark style="color:blue;">number</mark></td><td>单点数1-6 最低下注限额。</td></tr><tr><td>singleDiceMax</td><td><mark style="color:blue;">number</mark></td><td>单点数1-6 最高下注限额。</td></tr><tr><td>combinationMin</td><td><mark style="color:blue;">number</mark></td><td>组合 最低下注限额。</td></tr><tr><td>combinationMax</td><td><mark style="color:blue;">number</mark></td><td>组合 最高下注限额。</td></tr><tr><td>moreLeftMin</td><td><mark style="color:blue;">number</mark></td><td>二同号 最低下注限额。</td></tr><tr><td>moreLeftMax</td><td><mark style="color:blue;">number</mark></td><td>二同号 最高下注限额。</td></tr><tr><td>moreRightMin</td><td><mark style="color:blue;">number</mark></td><td>三不同 最低下注限额。</td></tr><tr><td>moreRightMax</td><td><mark style="color:blue;">number</mark></td><td>三不同 最高下注限额。</td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
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
<table><thead><tr><th width="217">参数</th><th width="119.66666666666666">格式</th><th>描述</th></tr></thead><tbody><tr><td>gameType</td><td><mark style="color:blue;">number</mark></td><td><p>游戏类型。</p><p>5: 轮盘<br>10: 财富轮盘</p></td></tr><tr><td>oddMin</td><td><mark style="color:blue;">number</mark></td><td>单 最低下注限额。</td></tr><tr><td>oddMax</td><td><mark style="color:blue;">number</mark></td><td>单 最高下注限额。</td></tr><tr><td>evenMin</td><td><mark style="color:blue;">number</mark></td><td>双 最低下注限额。</td></tr><tr><td>evenMax</td><td><mark style="color:blue;">number</mark></td><td>双 最高下注限额。</td></tr><tr><td>bigMin</td><td><mark style="color:blue;">number</mark></td><td>大 最低下注限额。</td></tr><tr><td>bigMax</td><td><mark style="color:blue;">number</mark></td><td>大 最高下注限额。</td></tr><tr><td>smallMin</td><td><mark style="color:blue;">number</mark></td><td>小 最低下注限额。</td></tr><tr><td>smallMax</td><td><mark style="color:blue;">number</mark></td><td>小 最高下注限额。</td></tr><tr><td>redMin</td><td><mark style="color:blue;">number</mark></td><td>红 最低下注限额。</td></tr><tr><td>redMax</td><td><mark style="color:blue;">number</mark></td><td>红 最高下注限额。</td></tr><tr><td>blackMin</td><td><mark style="color:blue;">number</mark></td><td>黑 最低下注限额。</td></tr><tr><td>blackMax</td><td><mark style="color:blue;">number</mark></td><td>黑 最高下注限额。</td></tr><tr><td>dozenMin</td><td><mark style="color:blue;">number</mark></td><td>打注 最低下注限额。</td></tr><tr><td>dozenMax</td><td><mark style="color:blue;">number</mark></td><td>打注 最高下注限额。</td></tr><tr><td>columnMin</td><td><mark style="color:blue;">number</mark></td><td>列注 最低下注限额。</td></tr><tr><td>columnMax</td><td><mark style="color:blue;">number</mark></td><td>列注 最高下注限额。</td></tr><tr><td>lineMin</td><td><mark style="color:blue;">number</mark></td><td>线注 最低下注限额。</td></tr><tr><td>lineMax</td><td><mark style="color:blue;">number</mark></td><td>线注 最高下注限额。</td></tr><tr><td>basketMin</td><td><mark style="color:blue;">number</mark></td><td>四个号码 最低下注限额。</td></tr><tr><td>basketMax</td><td><mark style="color:blue;">number</mark></td><td>四个号码 最高下注限额。</td></tr><tr><td>connerMin</td><td><mark style="color:blue;">number</mark></td><td>角注 最低下注限额。<br>可以使用此参数名称：cornerMin。</td></tr><tr><td>connerMax</td><td><mark style="color:blue;">number</mark></td><td>角注 最高下注限额。<br>可以使用此参数名称：cornerMax。</td></tr><tr><td>trioMin</td><td><mark style="color:blue;">number</mark></td><td>三数 最低下注限额。</td></tr><tr><td>trioMax</td><td><mark style="color:blue;">number</mark></td><td>三数 最高下注限额。</td></tr><tr><td>streetMin</td><td><mark style="color:blue;">number</mark></td><td>街注 最低下注限额。</td></tr><tr><td>streetMax</td><td><mark style="color:blue;">number</mark></td><td>街注 最高下注限额。</td></tr><tr><td>splitMin</td><td><mark style="color:blue;">number</mark></td><td>分注 最低下注限额。</td></tr><tr><td>splitMax</td><td><mark style="color:blue;">number</mark></td><td>分注 最高下注限额。</td></tr><tr><td>straightMin</td><td><mark style="color:blue;">number</mark></td><td>直接注 最低下注限额。</td></tr><tr><td>straightMax</td><td><mark style="color:blue;">number</mark></td><td>直接注 最高下注限额。</td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
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
<table><thead><tr><th width="217">参数</th><th width="119.66666666666666">格式</th><th>描述</th></tr></thead><tbody><tr><td>gameType</td><td><mark style="color:blue;">number</mark></td><td><p>游戏类型。</p><p>6: 牛牛</p></td></tr><tr><td>betPlayer1Min</td><td><mark style="color:blue;">number</mark></td><td>闲1 最低下注限额。</td></tr><tr><td>betPlayer1Max</td><td><mark style="color:blue;">number</mark></td><td>闲1 最高下注限额。</td></tr><tr><td>betPlayer1DoubleMin</td><td><mark style="color:blue;">number</mark></td><td>闲1翻倍 最低下注限额。</td></tr><tr><td>betPlayer1DoubleMax</td><td><mark style="color:blue;">number</mark></td><td>闲1翻倍 最高下注限额。</td></tr><tr><td>betPlayer2Min</td><td><mark style="color:blue;">number</mark></td><td>闲2 最低下注限额。</td></tr><tr><td>betPlayer2Max</td><td><mark style="color:blue;">number</mark></td><td>闲2 最高下注限额。</td></tr><tr><td>betPlayer2DoubleMin</td><td><mark style="color:blue;">number</mark></td><td>闲2翻倍 最低下注限额。</td></tr><tr><td>betPlayer2DoubleMax</td><td><mark style="color:blue;">number</mark></td><td>闲2翻倍 最高下注限额。</td></tr><tr><td>betPlayer3Min</td><td><mark style="color:blue;">number</mark></td><td>闲3 最低下注限额。</td></tr><tr><td>betPlayer3Max</td><td><mark style="color:blue;">number</mark></td><td>闲3 最高下注限额。</td></tr><tr><td>betPlayer3DoubleMin</td><td><mark style="color:blue;">number</mark></td><td>闲3翻倍 最低下注限额。</td></tr><tr><td>betPlayer3DoubleMax</td><td><mark style="color:blue;">number</mark></td><td>闲3翻倍 最高下注限额。</td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
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
<table><thead><tr><th width="217">参数</th><th width="119.66666666666666">格式</th><th>描述</th></tr></thead><tbody><tr><td>gameType</td><td><mark style="color:blue;">number</mark></td><td><p>游戏类型。</p><p>7: 财富大转盘</p></td></tr><tr><td>number_1Min</td><td><mark style="color:blue;">number</mark></td><td>号码1 最低下注限额。</td></tr><tr><td>number_1Max</td><td><mark style="color:blue;">number</mark></td><td>号码1 最高下注限额。</td></tr><tr><td>number_2Min</td><td><mark style="color:blue;">number</mark></td><td>号码2 最低下注限额。</td></tr><tr><td>number_2Max</td><td><mark style="color:blue;">number</mark></td><td>号码2 最高下注限额。</td></tr><tr><td>number_5Min</td><td><mark style="color:blue;">number</mark></td><td>号码5 最低下注限额。</td></tr><tr><td>number_5Max</td><td><mark style="color:blue;">number</mark></td><td>号码5 最高下注限额。</td></tr><tr><td>number_10Min</td><td><mark style="color:blue;">number</mark></td><td>号码10 最低下注限额。</td></tr><tr><td>number_10Max</td><td><mark style="color:blue;">number</mark></td><td>号码10 最高下注限额。</td></tr><tr><td>number_20Min</td><td><mark style="color:blue;">number</mark></td><td>号码20 最低下注限额。</td></tr><tr><td>number_20Max</td><td><mark style="color:blue;">number</mark></td><td>号码20 最高下注限额。</td></tr><tr><td>number_40Min</td><td><mark style="color:blue;">number</mark></td><td>号码40 最低下注限额。</td></tr><tr><td>number_40Max</td><td><mark style="color:blue;">number</mark></td><td>号码40 最高下注限额。</td></tr><tr><td>multipleMin</td><td><mark style="color:blue;">number</mark></td><td>2X/8X 最低下注限额。</td></tr><tr><td>multipleMax</td><td><mark style="color:blue;">number</mark></td><td>2X/8X 最高下注限额。</td></tr><tr><td>oddMin</td><td><mark style="color:blue;">number</mark></td><td>单 最低下注限额。</td></tr><tr><td>oddMax</td><td><mark style="color:blue;">number</mark></td><td>单 最高下注限额。</td></tr><tr><td>evenMin</td><td><mark style="color:blue;">number</mark></td><td>双 最低下注限额。</td></tr><tr><td>evenMax</td><td><mark style="color:blue;">number</mark></td><td>双 最高下注限额。</td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
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
<table><thead><tr><th width="217">参数</th><th width="119.66666666666666">格式</th><th>描述</th></tr></thead><tbody><tr><td>gameType</td><td><mark style="color:blue;">number</mark></td><td><p>游戏类型。</p><p>8: 电子21点</p></td></tr><tr><td>baseBet_Min</td><td><mark style="color:blue;">number</mark></td><td>投注/底注 最低下注限额。</td></tr><tr><td>baseBet_Max</td><td><mark style="color:blue;">number</mark></td><td>投注/底注 最高下注限额。</td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
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
<table><thead><tr><th width="217">参数</th><th width="119.66666666666666">格式</th><th>描述</th></tr></thead><tbody><tr><td>gameType</td><td><mark style="color:blue;">number</mark></td><td><p>游戏类型。</p><p>9: 真人21点</p></td></tr><tr><td>baseBet_Min</td><td><mark style="color:blue;">number</mark></td><td>投注/底注 最低下注限额。</td></tr><tr><td>baseBet_Max</td><td><mark style="color:blue;">number</mark></td><td>投注/底注 最高下注限额。</td></tr><tr><td>sideBet_Min</td><td><mark style="color:blue;">number</mark></td><td>旁注 最低下注限额。</td></tr><tr><td>sideBet_Max</td><td><mark style="color:blue;">number</mark></td><td>旁注 最高下注限额。</td></tr><tr><td>pairsBet_Min</td><td><mark style="color:blue;">number</mark></td><td>完美对子 最低下注限额。</td></tr><tr><td>pairsBet_Max</td><td><mark style="color:blue;">number</mark></td><td>完美对子 最高下注限额。</td></tr><tr><td>threecardBet_Min</td><td><mark style="color:blue;">number</mark></td><td>21+3 最低下注限额。</td></tr><tr><td>threecardBet_Max</td><td><mark style="color:blue;">number</mark></td><td>21+3 最高下注限额。</td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
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
<table><thead><tr><th width="217">参数</th><th width="119.66666666666666">格式</th><th>描述</th></tr></thead><tbody><tr><td>gameType</td><td><mark style="color:blue;">number</mark></td><td><p>游戏类型。</p><p>11: 真人博丁</p></td></tr><tr><td>betPlayer1Min</td><td><mark style="color:blue;">number</mark></td><td>闲1 最低下注限额。</td></tr><tr><td>betPlayer1Max</td><td><mark style="color:blue;">number</mark></td><td>闲1 最高下注限额。</td></tr><tr><td>betPlayer2Min</td><td><mark style="color:blue;">number</mark></td><td>闲2 最低下注限额。</td></tr><tr><td>betPlayer2Max</td><td><mark style="color:blue;">number</mark></td><td>闲2 最高下注限额。</td></tr><tr><td>betPlayer3Min</td><td><mark style="color:blue;">number</mark></td><td>闲3 最低下注限额。</td></tr><tr><td>betPlayer3Max</td><td><mark style="color:blue;">number</mark></td><td>闲3 最高下注限额。</td></tr><tr><td>betPlayer4Min</td><td><mark style="color:blue;">number</mark></td><td>闲4 最低下注限额。</td></tr><tr><td>betPlayer4Max</td><td><mark style="color:blue;">number</mark></td><td>闲4 最高下注限额。</td></tr><tr><td>betPlayer5Min</td><td><mark style="color:blue;">number</mark></td><td>闲5 最低下注限额。</td></tr><tr><td>betPlayer5Max</td><td><mark style="color:blue;">number</mark></td><td>闲5 最高下注限额。</td></tr><tr><td>betPlayer1PairMin</td><td><mark style="color:blue;">number</mark></td><td>闲1对 最低下注限额。</td></tr><tr><td>betPlayer1PairMax</td><td><mark style="color:blue;">number</mark></td><td>闲1对 最高下注限额。</td></tr><tr><td>betPlayer2PairMin</td><td><mark style="color:blue;">number</mark></td><td>闲2对 最低下注限额。</td></tr><tr><td>betPlayer2PairMax</td><td><mark style="color:blue;">number</mark></td><td>闲2对 最高下注限额。</td></tr><tr><td>betPlayer3PairMin</td><td><mark style="color:blue;">number</mark></td><td>闲3对 最低下注限额。</td></tr><tr><td>betPlayer3PairMax</td><td><mark style="color:blue;">number</mark></td><td>闲3对 最高下注限额。</td></tr><tr><td>betPlayer4PairMin</td><td><mark style="color:blue;">number</mark></td><td>闲4对 最低下注限额。</td></tr><tr><td>betPlayer4PairMax</td><td><mark style="color:blue;">number</mark></td><td>闲4对 最高下注限额。</td></tr><tr><td>betPlayer5PairMin</td><td><mark style="color:blue;">number</mark></td><td>闲5对 最低下注限额。</td></tr><tr><td>betPlayer5PairMax</td><td><mark style="color:blue;">number</mark></td><td>闲5对 最高下注限额。</td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
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
<table><thead><tr><th width="217">参数</th><th width="119.66666666666666">格式</th><th>描述</th></tr></thead><tbody><tr><td>gameType</td><td><mark style="color:blue;">number</mark></td><td><p>游戏类型。</p><p>12: Hi-Lo</p></td></tr><tr><td>biggerMin</td><td><mark style="color:blue;">number</mark></td><td>更大 最低下注限额。</td></tr><tr><td>biggerMax</td><td><mark style="color:blue;">number</mark></td><td>更大 最高下注限额。</td></tr><tr><td>smallerMin</td><td><mark style="color:blue;">number</mark></td><td>更小 最低下注限额。</td></tr><tr><td>smallerMax</td><td><mark style="color:blue;">number</mark></td><td>更小 最高下注限额。</td></tr><tr><td>sameMin</td><td><mark style="color:blue;">number</mark></td><td>同点 最低下注限额。</td></tr><tr><td>sameMax</td><td><mark style="color:blue;">number</mark></td><td>同点 最高下注限额。</td></tr><tr><td>sum_3_4_5_6Min</td><td><mark style="color:blue;">number</mark></td><td>3、4、5、6 最低下注限额。</td></tr><tr><td>sum_3_4_5_6Max</td><td><mark style="color:blue;">number</mark></td><td>3、4、5、6 最高下注限额。</td></tr><tr><td>sum_7_8_9_10Min</td><td><mark style="color:blue;">number</mark></td><td>7、8、9、10 最低下注限额。</td></tr><tr><td>sum_7_8_9_10Max</td><td><mark style="color:blue;">number</mark></td><td>7、8、9、10 最高下注限额。</td></tr><tr><td>sum_11_12_13_14Min</td><td><mark style="color:blue;">number</mark></td><td>11、12、13、14 最低下注限额。</td></tr><tr><td>sum_11_12_13_14Max</td><td><mark style="color:blue;">number</mark></td><td>11、12、13、14 最高下注限额。</td></tr><tr><td>sum_15_16_17_18Min</td><td><mark style="color:blue;">number</mark></td><td>15、16、17、18 最低下注限额。</td></tr><tr><td>sum_15_16_17_18Max</td><td><mark style="color:blue;">number</mark></td><td>15、16、17、18 最高下注限额。</td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
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

<table><thead><tr><th width="176">参数</th><th width="117.66666666666666">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>updateGameList</td><td><mark style="color:blue;">array</mark></td><td>更新投注限额游戏。阵列值为gameType。</td><td>预设随机生成</td></tr><tr><td>username</td><td><mark style="color:blue;">number</mark></td><td>用户名。</td><td><pre><code>apitest01
</code></pre></td></tr><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道ID。</td><td>200</td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>eBET回应状态。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>0
</code></pre></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
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
    "username": "demo",
    "channelId": 1,
    "status": 200,
    "apiVersion": "1.5.75"
}
```
{% endcode %}
