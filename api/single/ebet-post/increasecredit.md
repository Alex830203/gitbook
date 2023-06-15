---
description: 通知渠道用户额度变动
---

# ​​increaseCredit

{% hint style="info" %}
seqNo是唯一值。 避免重复处理金額，请勿记录相同的支出seqNo。\
我们有一个retry机制。如果之前已经成功处理过，请向eBET返回200 或 201（重复seqNo）。\
如果网路发生或是贵方回传系统错误,系统忙碌, 我方会尝试重送3次
{% endhint %}

{% tabs %}
{% tab title="一般处理流程" %}
<figure><img src="../../../.gitbook/assets/base bet.png" alt=""><figcaption><p>一般投注流程</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/base payout.png" alt=""><figcaption><p>一般派彩流程</p></figcaption></figure>
{% endtab %}

{% tab title="预扣独立处理流程" %}
<figure><img src="../../../.gitbook/assets/withholding bet.png" alt=""><figcaption><p>先预扣再投注的处理流程</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/refund payout.png" alt=""><figcaption><p>先预扣返还再派彩的处理流程</p></figcaption></figure>
{% endtab %}
{% endtabs %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="150">参数</th><th width="96">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td>RegisterOrLoginReq</td></tr><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td></td></tr><tr><td>money</td><td><mark style="color:blue;">number</mark></td><td>需要变动的金额，如果为<mark style="color:red;">负数代表 玩家要扣金额</mark></td><td></td></tr><tr><td>type</td><td><mark style="color:blue;">number</mark></td><td>交易事务类型</td><td></td></tr><tr><td>platform</td><td><mark style="color:blue;">number</mark></td><td>用户平台</td><td></td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td>detail</td><td><mark style="color:blue;">array</mark></td><td>注单详情</td><td></td></tr><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>时间戳记,以毫秒为单位。</td><td></td></tr><tr><td>sessionToken</td><td><mark style="color:blue;">string</mark></td><td>由渠道提供或随机生成</td><td></td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td>签名。 字符串拼接: <mark style="color:red;">seqNo+event+channelId+timestamp+username+money</mark></td><td></td></tr></tbody></table>

{% tabs %}
{% tab title="Type 1" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>betTime</td><td><mark style="color:blue;">number</mark></td><td>下注时间(毫秒)。 格式为Unix时间</td><td></td></tr><tr><td><a href="increasecredit.md#betlist">betList</a></td><td><mark style="color:blue;">array</mark></td><td>注单详情</td><td></td></tr><tr><td>totalBet</td><td><mark style="color:blue;">number</mark></td><td>总投注</td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td>有效投注</td><td></td></tr><tr><td><a href="increasecredit.md#withholdinglist">withHoldingList</a></td><td><mark style="color:blue;">array</mark></td><td>預扣返還列表,在预扣返还的请求中会取代 betList</td><td></td></tr><tr><td>gameName</td><td><mark style="color:blue;">string</mark></td><td><p>游戏名称。 </p><p>baccarat </p><p>dragon-tiger </p><p>sic-bo </p><p>roulette </p><p>slot(显示游戏的gameID) </p><p>bull-bull </p><p>fortune-wheel </p><p>black-jack-electronic </p><p>black-jack-live </p><p>mini-game(显示游戏的gameID) </p><p>pok-deng</p></td><td></td></tr><tr><td>brokerageRequired</td><td><mark style="color:blue;">boolean</mark></td><td>是否為佣金百家乐。 <mark style="color:red;">只有百家乐才會有此参数</mark></td><td></td></tr></tbody></table>

#### betList

<table><thead><tr><th width="164">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td>RegisterOrLoginReq</td></tr><tr><td>betMoney</td><td><mark style="color:blue;">number</mark></td><td>投注金额。</td><td></td></tr><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID</td><td></td></tr></tbody></table>

#### withHoldingList

<table><thead><tr><th width="160">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>withHolding</td><td><mark style="color:blue;">number</mark></td><td>預扣金额。</td><td>RegisterOrLoginReq</td></tr><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "money": -19275,
    "type": 1,
    "platform": 3,
    "currency": "THB",
    "seqNo": "94906311|bet|1686811358331|wayigame",
    "detail": {
        "roundCode": "wg-texas543_27462dded4",
        "tableType": 30,
        "tableSubType": 0,
        "tableCode": "texas",
        "gameName": "texas",
        "betList": [
            {
                "betMoney": 0,
                "betType": 601,
                "betId": "94906311|bet|1686811358331|wayigame-601"
            }
        ],
        "betTime": 1686811358280,
        "validBet": 0,
        "totalBet": 0,
        "withHoldingList": [
            {
                "withHolding": 19275,
                "betType": 601
            }
        ]
    },
    "event": "increaseCredit",
    "timestamp": 1686811358544,
    "sessionToken": "f73e0e279b0ea269a57c7ef48fa0b46e",
    "signature": "c6SkBVVWIAyDHM1FkNGAdg1DcDhBTJX8CNb0DUyJd47qq4DfAnm24r6nQ3Ztfs89O+xghidTL82yIa9KFWAEIg=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Type 2" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>dealerName</td><td><mark style="color:blue;">string</mark></td><td>荷官名</td><td></td></tr><tr><td>bootsCardId</td><td><mark style="color:blue;">string</mark></td><td>靴盒号</td><td></td></tr><tr><td>gameName</td><td><mark style="color:blue;">string</mark></td><td><p>游戏名称。 </p><p>baccarat </p><p>dragon-tiger </p><p>sic-bo </p><p>roulette </p><p>slot(显示游戏的gameID) </p><p>bull-bull </p><p>fortune-wheel </p><p>black-jack-electronic </p><p>black-jack-live </p><p>mini-game(显示游戏的gameID) </p><p>pok-deng</p></td><td></td></tr><tr><td>srcResults</td><td><mark style="color:blue;">array</mark></td><td><p>荷官开牌结果。 </p><p>百家乐：牌面3个一组，顺序为闲/庄，没发的牌面会以null代替 </p><p>龙虎：牌面2个，顺序为龙/虎 </p><p>牛牛：牌面5个一组，顺序为庄/闲1/闲2/闲3 </p><p>博丁：牌面2个一组，顺序为庄/闲1/闲2/闲3/闲4/闲5</p></td><td></td></tr><tr><td>brokerageRequired</td><td><mark style="color:blue;">boolean</mark></td><td>是否為免佣金百家乐。 <mark style="color:red;">只有百家乐才會有此参数</mark></td><td></td></tr><tr><td>results</td><td><mark style="color:blue;">array</mark></td><td>中奖项目</td><td></td></tr><tr><td><a href="increasecredit.md#betlist">betList</a></td><td><mark style="color:blue;">array</mark></td><td>注单详情</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>betTime</td><td><mark style="color:blue;">number</mark></td><td>下注时间(毫秒)。 格式为Unix时间</td><td></td></tr><tr><td>totalBet</td><td><mark style="color:blue;">number</mark></td><td>总投注</td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td>有效投注</td><td></td></tr><tr><td><a href="increasecredit.md#withholdinglist">withHoldingList</a></td><td><mark style="color:blue;">array</mark></td><td>預扣返還列表,在预扣返还的请求中会取代 betList</td><td></td></tr><tr><td>payout</td><td><mark style="color:blue;">number</mark></td><td>派彩总额</td><td></td></tr><tr><td>payoutTime</td><td><mark style="color:blue;">number</mark></td><td>派彩时间(毫秒)。 格式为Unix</td><td></td></tr><tr><td>betStopTime</td><td><mark style="color:blue;">number</mark></td><td>下注停止时间(毫秒)。 格式为Unix<mark style="color:red;">(只有派彩的事件，才需要此字段。)</mark></td><td></td></tr></tbody></table>

#### betList

<table><thead><tr><th width="164">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td>RegisterOrLoginReq</td></tr><tr><td>betMoney</td><td><mark style="color:blue;">number</mark></td><td>投注金额。 <mark style="color:red;">当betMoney = 0时，视为下注失败。</mark></td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>投注请求的序号。 </td><td></td></tr><tr><td>payout</td><td><mark style="color:blue;">number</mark></td><td>派彩金额。 </td><td></td></tr><tr><td>number</td><td><mark style="color:blue;">string</mark></td><td>游戏下注的号码。 只有特定项目才会有此字段</td><td></td></tr><tr><td>odds</td><td><mark style="color:blue;">number</mark></td><td><p>赔率。 </p><p>Noted: </p><p>1.支援所有游戏除了老虎机 </p><p>2.赔率不含投注额</p></td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td><p>每个投注项目的有效投注。 </p><p>该参数会依照有效投注的计算规则，请参考：<a href="../../can-shu-shuo-ming.md#you-xiao-tou-zhu">参数说明-有效投注。</a> </p></td><td></td></tr><tr><td>rebateAmount</td><td><mark style="color:blue;">number</mark></td><td>返水。</td><td></td></tr><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID</td><td></td></tr></tbody></table>

#### withHoldingList

<table><thead><tr><th width="160">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>withHolding</td><td><mark style="color:blue;">number</mark></td><td>預扣金额。<mark style="color:red;">withHolding =0时,代表預扣失败。</mark></td><td>RegisterOrLoginReq</td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td><p>预扣状态 </p><p>1: 成功 </p><p>0: 失败或没有金额需要返还 </p><p>11:退款 </p><p>13:退款失败</p></td><td></td></tr><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td></td></tr><tr><td>withHoldingId</td><td><mark style="color:blue;">string</mark></td><td>游戏下注的号码。 只有特定项目才会有此字段</td><td></td></tr><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>預扣请求的序列编号</td><td></td></tr><tr><td>refund</td><td><mark style="color:blue;">number</mark></td><td>牛牛返还金额</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "money": 44.9,
    "type": 2,
    "platform": 3,
    "currency": "CNY",
    "seqNo": "9602f834ae6857f33b8e5a270e25278b",
    "detail": {
        "tableCode": "BP1",
        "tableType": 1,
        "tableSubType": 0,
        "dealerName": "Vina",
        "bootsCardId": "106",
        "gameName": "baccarat",
        "srcResults": [
            8,
            30,
            null,
            34,
            26,
            11
        ],
        "brokerageRequired": true,
        "results": [
            60,
            70,
            83,
            63,
            61
        ],
        "betList": [
            {
                "betType": 60,
                "betMoney": 10,
                "seqNo": "c14159701c2ba78a06baeb644386abd3",
                "payout": 21,
                "odds": 1,
                "validBet": 10,
                "rebateAmount": 1,
                "betId": "c14159701c2ba78a06baeb644386abd3-60"
            },
            {
                "betType": 63,
                "betMoney": 10,
                "seqNo": "c14159701c2ba78a06baeb644386abd3",
                "payout": 19.9,
                "odds": 0.9,
                "validBet": 10,
                "rebateAmount": 0.9,
                "betId": "c14159701c2ba78a06baeb644386abd3-63"
            },
            {
                "betType": 66,
                "betMoney": 10,
                "seqNo": "c14159701c2ba78a06baeb644386abd3",
                "payout": 1,
                "odds": 11,
                "validBet": 10,
                "rebateAmount": 1,
                "betId": "c14159701c2ba78a06baeb644386abd3-66"
            },
            {
                "betType": 82,
                "betMoney": 10,
                "seqNo": "c14159701c2ba78a06baeb644386abd3",
                "payout": 1,
                "odds": 0.94,
                "validBet": 10,
                "rebateAmount": 1,
                "betId": "c14159701c2ba78a06baeb644386abd3-82"
            },
            {
                "betType": 88,
                "betMoney": 10,
                "seqNo": "c14159701c2ba78a06baeb644386abd3",
                "payout": 1,
                "odds": 11,
                "validBet": 10,
                "rebateAmount": 1,
                "betId": "c14159701c2ba78a06baeb644386abd3-88"
            },
            {
                "betType": 68,
                "betMoney": 10,
                "seqNo": "a43ce533f01031658956f1b255e27c39",
                "payout": 1,
                "odds": 8,
                "validBet": 10,
                "rebateAmount": 1,
                "betId": "a43ce533f01031658956f1b255e27c39-68"
            }
        ],
        "roundCode": "BP1-230615141508",
        "betTime": 1686809724275,
        "totalBet": 60,
        "validBet": 60,
        "payout": 44.9,
        "payoutTime": 1686809747345,
        "rebateAmount": 5.9,
        "betStopTime": 1686809733853
    },
    "event": "increaseCredit",
    "timestamp": 1686809747884,
    "sessionToken": "537ed0cff192bc65a64b6056b82735d6",
    "signature": "dl/kuwL4lJ7H3wPN/NeaJRpU06BwpbF9f8gruAcq8LOKCS1skN46yL+PH0iA8at2Nck3G12AvC9tMx93klCAbg=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Type 27" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>betTime</td><td><mark style="color:blue;">number</mark></td><td>下注时间(毫秒)。 格式为Unix时间</td><td></td></tr><tr><td>betList</td><td><mark style="color:blue;">array</mark></td><td>注单详情</td><td></td></tr><tr><td>totalBet</td><td><mark style="color:blue;">number</mark></td><td>总投注</td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td>有效投注</td><td></td></tr></tbody></table>

#### betList

<table><thead><tr><th width="164">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td>RegisterOrLoginReq</td></tr><tr><td>betMoney</td><td><mark style="color:blue;">number</mark></td><td>投注金额。 </td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "money": -200,
    "type": 27,
    "platform": 3,
    "currency": "CNY",
    "seqNo": "15193405|bet|1686809992123|wayigame-27",
    "detail": {
        "roundCode": "wg-texas542_27462bc928",
        "tableType": 30,
        "tableSubType": 0,
        "tableCode": "texas",
        "gameName": "texas",
        "betList": [
            {
                "betMoney": 0,
                "betType": 601
            }
        ],
        "betTime": 1686809992090,
        "validBet": 0,
        "totalBet": 0
    },
    "event": "increaseCredit",
    "timestamp": 1686809992546,
    "sessionToken": "537ed0cff192bc65a64b6056b82735d6",
    "signature": "SNdv+LjfGLrOKPev4MV3VJLof3C0PvcGA9WIRPEdlujPmumtMSqEVJ8hNc5ZJQh/0kNzTT0tKvIfoUtxlqKa5Q=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Type 28" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>withHoldingList</td><td><mark style="color:blue;">array</mark></td><td>預扣返還列表,在预扣返还的请求中会取代 betList</td><td></td></tr></tbody></table>

#### withHoldingList

<table><thead><tr><th width="160">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>withHolding</td><td><mark style="color:blue;">number</mark></td><td>預扣金额。<mark style="color:red;">withHolding =0时,代表預扣失败。</mark></td><td>RegisterOrLoginReq</td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td><p>预扣状态 </p><p>1: 成功 </p><p>0: 失败或没有金额需要返还 </p><p>11:退款 </p><p>13:退款失败</p></td><td></td></tr><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td></td></tr><tr><td>withHoldingId</td><td><mark style="color:blue;">string</mark></td><td>游戏下注的号码。 只有特定项目才会有此字段</td><td></td></tr><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>預扣请求的序列编号</td><td></td></tr><tr><td>refund</td><td><mark style="color:blue;">number</mark></td><td>牛牛返还金额,<mark style="color:red;">仅只有type=28的事件，才需要此字段。</mark></td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "money": 200,
    "type": 28,
    "platform": 3,
    "currency": "CNY",
    "seqNo": "15193405|payout|1686810054228|wayigame-28",
    "detail": {
        "roundCode": "wg-texas542_27462bc928",
        "tableType": 30,
        "tableSubType": 0,
        "tableCode": "texas",
        "gameName": "texas",
        "withHoldingList": [
            {
                "betType": 601,
                "withHolding": 200,
                "seqNo": "15193405|bet|1686809992123|wayigame-27",
                "withHoldingId": "15193405|bet|1686809992123|wayigame-27-601",
                "status": 1,
                "refund": 200
            }
        ]
    },
    "event": "increaseCredit",
    "timestamp": 1686810054703,
    "sessionToken": "537ed0cff192bc65a64b6056b82735d6",
    "signature": "JUztabKC+D/1CPRsKCvHOlswXO+EsGbaQip0V3Gqi44qNSAnMWhwPC4jZOnvqkXxzv6yVnx6vyoZlUTcPIOquQ=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Type 11" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>betTime</td><td><mark style="color:blue;">number</mark></td><td>下注时间(毫秒)。 格式为Unix时间</td><td></td></tr><tr><td>betList</td><td><mark style="color:blue;">array</mark></td><td>注单详情</td><td></td></tr><tr><td>totalBet</td><td><mark style="color:blue;">number</mark></td><td>总投注</td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td>有效投注</td><td></td></tr><tr><td>withholdingSeqNo</td><td><mark style="color:blue;">string</mark></td><td>牛牛預扣投注退款请求(type=27)的序号。 </td><td></td></tr></tbody></table>

#### betList

<table><thead><tr><th width="164">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td>RegisterOrLoginReq</td></tr><tr><td>betMoney</td><td><mark style="color:blue;">number</mark></td><td>投注金额。</td><td></td></tr><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "money": 400,
    "type": 11,
    "platform": 3,
    "currency": "CNY",
    "seqNo": "165c0e36bce5bb2874de12c20348090d",
    "detail": {
        "tableCode": "NN2",
        "tableType": 8,
        "tableSubType": 0,
        "roundCode": "NN2-211119154844",
        "betTime": 1637308132392.0,
        "betList": [
            {
                "betType": 302,
                "betMoney": 50
            },
            {
                "betType": 304,
                "betMoney": 50
            }
        ],
        "totalBet": 100,
        "validBet": 0,
        "withHoldingSeqNo": "43c4f135f0c05cf8eba045fb46ef1e51"
    },
    "event": "increaseCredit",
    "timestamp": 1637308132650.0,
    "sessionToken": "ddb5187ce8b1d020913a4b20380e03d7",
    "signature": "A29ZGt8F1Dx5eHPeXJ3v8xSMrzEHlmPgDv8Qh/6m/04JibqjU3g4iA48tqXvbxUzbDyYDQQBmMP3ul+UsV3cCw=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Type 37" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>srcResults</td><td><mark style="color:blue;">array</mark></td><td><p>荷官开牌结果。 </p><p>百家乐：牌面3个一组，顺序为闲/庄，没发的牌面会以null代替 </p><p>龙虎：牌面2个，顺序为龙/虎 </p><p>牛牛：牌面5个一组，顺序为庄/闲1/闲2/闲3 </p><p>博丁：牌面2个一组，顺序为庄/闲1/闲2/闲3/闲4/闲5</p></td><td></td></tr><tr><td>brokerageRequired</td><td><mark style="color:blue;">boolean</mark></td><td>是否為免佣金百家乐。 <mark style="color:red;">只有百家乐才會有此参数</mark></td><td></td></tr><tr><td>results</td><td><mark style="color:blue;">array</mark></td><td>中奖项目</td><td></td></tr><tr><td>betList</td><td><mark style="color:blue;">array</mark></td><td>注单详情</td><td></td></tr><tr><td>modifyBetList</td><td><mark style="color:blue;">array</mark></td><td></td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>betTime</td><td><mark style="color:blue;">number</mark></td><td>下注时间(毫秒)。 格式为Unix时间</td><td></td></tr><tr><td>totalBet</td><td><mark style="color:blue;">number</mark></td><td>总投注</td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td>有效投注</td><td></td></tr><tr><td>payout</td><td><mark style="color:blue;">number</mark></td><td>派彩总额</td><td></td></tr><tr><td>payoutTime</td><td><mark style="color:blue;">number</mark></td><td>派彩时间(毫秒)。 格式为Unix</td><td></td></tr></tbody></table>

#### betList

<table><thead><tr><th width="164">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td>RegisterOrLoginReq</td></tr><tr><td>betMoney</td><td><mark style="color:blue;">number</mark></td><td>投注金额。 <mark style="color:red;">当betMoney = 0时，视为下注失败。</mark></td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>投注请求的序号。 </td><td></td></tr><tr><td>payout</td><td><mark style="color:blue;">number</mark></td><td>派彩金额。 </td><td></td></tr><tr><td>number</td><td><mark style="color:blue;">string</mark></td><td>游戏下注的号码。 只有特定项目才会有此字段</td><td></td></tr><tr><td>odds</td><td><mark style="color:blue;">number</mark></td><td><p>赔率。 </p><p>Noted: </p><p>1.支援所有游戏除了老虎机 </p><p>2.赔率不含投注额</p></td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td><p>每个投注项目的有效投注。 </p><p>该参数会依照有效投注的计算规则，请参考：<a href="../../can-shu-shuo-ming.md#you-xiao-tou-zhu">参数说明-有效投注。</a> </p></td><td></td></tr><tr><td>rebateAmount</td><td><mark style="color:blue;">number</mark></td><td>返水。</td><td></td></tr><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID</td><td></td></tr></tbody></table>

#### modifyBetList

<table><thead><tr><th width="164">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td>RegisterOrLoginReq</td></tr><tr><td>betMoney</td><td><mark style="color:blue;">number</mark></td><td>投注金额。 <mark style="color:red;">当betMoney = 0时，视为下注失败。</mark></td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>投注请求的序号。 </td><td></td></tr><tr><td>payout</td><td><mark style="color:blue;">number</mark></td><td>派彩金额。 </td><td></td></tr><tr><td>number</td><td><mark style="color:blue;">string</mark></td><td>游戏下注的号码。 只有特定项目才会有此字段</td><td></td></tr><tr><td>odds</td><td><mark style="color:blue;">number</mark></td><td><p>赔率。 </p><p>Noted: </p><p>1.支援所有游戏除了老虎机 </p><p>2.赔率不含投注额</p></td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td><p>每个投注项目的有效投注。 </p><p>该参数会依照有效投注的计算规则，请参考：<a href="../../can-shu-shuo-ming.md#you-xiao-tou-zhu">参数说明-有效投注。</a> </p></td><td></td></tr><tr><td>rebateAmount</td><td><mark style="color:blue;">number</mark></td><td>返水。</td><td></td></tr><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "money": 1200,
    "type": 37,
    "platform": 3,
    "currency": "CNY",
    "seqNo": "d2e3a1bd0b5dd66053359e7619d46a43",
    "detail": {
        "tableCode": "B18",
        "tableType": 1,
        "tableSubType": 0,
        "srcResults": [
            41,
            41,
            null,
            25,
            38,
            null
        ],
        "brokerageRequired": true,
        "results": [
            60,
            66,
            88,
            71,
            83,
            62,
            61
        ],
        "betList": [
            {
                "betType": 60,
                "betMoney": 100,
                "seqNo": "1a57cb64c977172108b5fcac211e3755",
                "payout": 200
            },
            {
                "betType": 66,
                "betMoney": 100,
                "seqNo": "1a57cb64c977172108b5fcac211e3755",
                "payout": 0
            }
        ],
        "modifyBetList": [
            {
                "betType": 60,
                "betMoney": 100,
                "seqNo": "1a57cb64c977172108b5fcac211e3755",
                "payout": 200
            },
            {
                "betType": 66,
                "betMoney": 100,
                "seqNo": "1a57cb64c977172108b5fcac211e3755",
                "payout": 1200
            }
        ],
        "roundCode": "B18-200513164029",
        "betTime": 1589359258387,
        "totalBet": 200,
        "validBet": 200,
        "payout": 1200,
        "payoutTime": 1589359300855
    },
    "event": "increaseCredit",
    "timestamp": 1589359300861,
    "sessionToken": "bf23ac28d01349fb7c5643b3b86aa7a5",
    "signature": "fK34IX9cvjaIICPu8Gx+TxIgNfi/wuOaGlLd8IzvXS0eB2jOVqsLvZqpvu0MItwq7grmzByHw2DWKEeU1dEdTQ=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Type 3" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "money": -100,
    "type": 3,
    "platform": 3,
    "currency": "CNY",
    "seqNo": "6070c43eeb40e5997ed18928a7494799",
    "sessionToken": "c835a1e527d9a643970ac0b8394519eb",
    "detail": {
        "tableCode": "B1",
        "tableType": 1,
        "tableSubType": 1,
        "roundCode": "B1-190711113358"
    },
    "event": "increaseCredit",
    "timestamp": 1564554803438,
    "signature": "VoXfGy/q5TizJ8puqwt5gVxC/p/dmRSHBDuX731YAhsHsxCEYf7KYlzv/bKDq5uX4wmcijL9RQmGWgbpRwq/fw=="
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Type 8" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>matchId</td><td><mark style="color:blue;">number</mark></td><td>大赛代码。</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
```
{% endcode %}
{% endtab %}

{% tab title="Type 9" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>matchId</td><td><mark style="color:blue;">number</mark></td><td>大赛代码。</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
```
{% endcode %}
{% endtab %}

{% tab title="Type 14" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "money": 100,
    "type": 14,
    "platform": null,
    "currency": "CNY",
    "seqNo": "ab32d3eb6d4c053bb22d85a20d722f9a",
    "sessionToken": "5032acd99251530eab617cd6966cd140",
    "detail": {
        "tableType": 1,
        "tableSubType": 0,
        "roundCode": "api_test_match_award"
    },
    "event": "increaseCredit",
    "timestamp": 1564557695108,
    "signature": "TaEWIYOudyrhcS59IuyDB9SyFdw54y5xcdI6/JPxzwbJzg6W4Fys3cNKgxujbA4EibagkVAxwfZ9wcSRGA8s0A=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Type 15 " %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "money": -100,
    "type": 15,
    "platform": null,
    "currency": "CNY",
    "seqNo": "d63dc2e4f034116a2e92674eccd35e94",
    "sessionToken": "5032acd99251530eab617cd6966cd140",
    "detail": {
        "tableType": 1,
        "tableSubType": 0,
        "roundCode": " api_test_match_award"
    },
    "event": "increaseCredit",
    "timestamp": 1564557703045,
    "signature": "aFqTvbPMDJes7JhsBGi+7OXllZ2TBnVjoE4Pag0Sifo+bPQWGHHu7ZAGyGAG8uAHlClujHNplH03G0tV5tOO3A=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Type 23" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "money": 100,
    "type": 23,
    "platform": 3,
    "currency": "CNY",
    "seqNo": "5e35f21553d8aab158f18b9bc6dfee6b",
    "sessionToken": "5032acd99251530eab617cd6966cd140",
    "detail": {
        "tableCode": "B1",
        "tableType": 1,
        "tableSubType": 0,
        "roundCode": "B1-190731150155"
    },
    "event": "increaseCredit",
    "timestamp": 1564556546166,
    "signature": "DYmZ5OLoUlX9BztuN2nTMHF+gv6NC9x3IJb99SzrHQbNg1bXSuSf3+iyD68pECeiNyWhUhIxSGJJ66dyvw+p+w=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Type 24" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "money": 100,
    "type": 24,
    "platform": 3,
    "currency": "CNY",
    "seqNo": "b81a266bece795f597ffeb1e81b1a093",
    "sessionToken": "5032acd99251530eab617cd6966cd140",
    "detail": {
        "tableCode": "B1",
        "tableType": 1,
        "tableSubType": 0,
        "roundCode": "B1-190731150155"
    },
    "event": "increaseCredit",
    "timestamp": 1564556546208,
    "signature": "YGMgM7c7JkuMhn6nvLOBDYIC+DjXJaHba/BUvQ8cTJ29H4H/u0Lr5FNPxiaoJp2ejKfQCiVhCAwx6FB6ZTaDaQ=="
}
```
{% endcode %}
{% endtab %}

{% tab title="Type 38" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>eventBonusType</td><td><mark style="color:blue;">number</mark></td><td>活动奖励类型</td><td></td></tr><tr><td>eventBonusCode</td><td><mark style="color:blue;">string</mark></td><td>活动奖励名称</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "username": "demo",
    "channelId": 1,
    "money": 1200,
    "type": 38,
    "platform": 3,
    "currency": "CNY",
    "seqNo": "d2e3a1bd0b5dd66053359e7619d46a43",
    "detail": {
        "tableType": 0,
        "eventBonusType": 1,
        "eventBonusCode": "test-bonus"
    },
    "event": "increaseCredit",
    "timestamp": 1589359300861,
    "sessionToken": "bf23ac28d01349fb7c5643b3b86aa7a5",
    "signature": "fK34IX9cvjaIICPu8Gx+TxIgNfi/wuOaGlLd8IzvXS0eB2jOVqsLvZqpvu0MItwq7grmzByHw2DWKEeU1dEdTQ=="
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

{% embed url="https://docs.google.com/spreadsheets/d/1ejxETVOI9kcCAP5eNpT6CIi4ftGHwcYWMHJTEPqLILs" %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="160">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td>RegisterOrLoginReq</td></tr><tr><td><mark style="color:red;">money</mark></td><td><mark style="color:blue;">number</mark></td><td>经过增减后的金额</td><td></td></tr><tr><td><mark style="color:red;">moneyBefore</mark></td><td><mark style="color:blue;">number</mark></td><td>玩家原始的金额</td><td></td></tr><tr><td><mark style="color:red;">status</mark></td><td><mark style="color:blue;">number</mark></td><td><a href="../../ebet-zhuang-tai-ma.md#jian-yi-xiang-ying-de-zhuang-tai-dai-ma">建议返回的状态码</a></td><td></td></tr><tr><td><mark style="color:red;">event</mark></td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td></td></tr><tr><td><mark style="color:red;">seqNo</mark></td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>时间戳记,以毫秒为单位。</td><td></td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Responses" overflow="wrap" %}
```json
{
  "username": "apitest01",
  "money": 900.01,
  "moneyBefore": 1000.01,
  "status": 200,
  "event": "increaseCredit",
  "seqNo": "seqNoseqNoseqNoseqNo",
  "timestamp": 1577808000000
}
```
{% endcode %}

