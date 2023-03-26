---
description: 该API是用于通知渠道更改玩家金额。
---

# ​​increaseCredit

* seqNo是<mark style="color:red;">**`唯一值`**</mark>。 避免重复处理金額，请勿记录相同的支出seqNo。
* 我们有一个**retry**机制。如果之前已经成功处理过，请向eBET返回<mark style="color:red;">**`201（重复seqNo）`**</mark>。
* 如果网路发生或是贵方回传系统错误,系统忙碌, 我方会尝试重送<mark style="color:red;">**`3次`**</mark>。
* 当<mark style="color:red;">**betMoney = 0**</mark>时，视为<mark style="color:red;">**下注失败**</mark>。

{% hint style="info" %}
<mark style="color:blue;">发送请求至接收地址是渠道的服务器url + api E.g.</mark> [<mark style="color:blue;">http://127.0.0.1/increaseCredit</mark>](http://127.0.0.1/increaseCredit)<mark style="color:blue;"></mark>
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td>RegisterOrLoginReq</td></tr><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td></td></tr><tr><td>money</td><td><mark style="color:blue;">number($double)</mark></td><td>需要变动的金额，如果为<mark style="color:red;">负数代表 玩家要扣金额</mark></td><td></td></tr><tr><td>type</td><td><mark style="color:blue;">number</mark></td><td>交易事务类型</td><td></td></tr><tr><td>platform</td><td><mark style="color:blue;">number</mark></td><td>用户平台</td><td></td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>时间戳记,以毫秒为单位。</td><td></td></tr><tr><td>sessionToken</td><td><mark style="color:blue;">string</mark></td><td>由渠道提供或随机生成</td><td></td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td>签名。 字符串拼接: <mark style="color:red;">seqNo+event+channelId+timestamp+username+money</mark></td><td></td></tr><tr><td>detail</td><td><mark style="color:orange;">array</mark></td><td>注单详情</td><td></td></tr></tbody></table>

#### detail:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>dealerName</td><td><mark style="color:blue;">string</mark></td><td>荷官名，<mark style="color:red;">仅type:2</mark></td><td></td></tr><tr><td>bootsCardId</td><td><mark style="color:blue;">string</mark></td><td>靴盒号，<mark style="color:red;">仅type:2</mark></td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>betTime</td><td><mark style="color:blue;">number</mark></td><td>下注时间(毫秒)。 格式为Unix时间</td><td></td></tr><tr><td>totalBet</td><td><mark style="color:blue;">number</mark></td><td>总投注</td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td>有效投注</td><td></td></tr><tr><td>rebateAmount</td><td><mark style="color:blue;">number</mark></td><td>返水。<mark style="color:red;">仅type:2</mark></td><td></td></tr><tr><td>withholdingSeqNo</td><td><mark style="color:blue;">string</mark></td><td>牛牛預扣投注退款请求(type=27)的序号。 只有type=11的事件，才需要此字段。</td><td></td></tr><tr><td>srcResults</td><td><mark style="color:orange;">array</mark></td><td><p>荷官开牌结果。 </p><p>百家乐：牌面3个一组，顺序为闲/庄，没发的牌面会以null代替 </p><p>龙虎：牌面2个，顺序为龙/虎 </p><p>牛牛：牌面5个一组，顺序为庄/闲1/闲2/闲3 </p><p>博丁：牌面2个一组，顺序为庄/闲1/闲2/闲3/闲4/闲5</p></td><td></td></tr><tr><td>brokerageRequired</td><td><mark style="color:blue;">boolean</mark></td><td>是否為免佣金百家乐。 <mark style="color:red;">只有百家乐才會有此参数</mark></td><td></td></tr><tr><td>results</td><td><mark style="color:orange;">array</mark></td><td>中奖项目</td><td></td></tr><tr><td>payout</td><td><mark style="color:blue;">number</mark></td><td>派彩总额</td><td></td></tr><tr><td>payoutTime</td><td><mark style="color:blue;">number</mark></td><td>派彩时间(毫秒)。 格式为Unix</td><td></td></tr><tr><td>betList</td><td><mark style="color:orange;">array</mark></td><td>注单详情</td><td></td></tr><tr><td>modifyBetList</td><td><mark style="color:orange;">array</mark></td><td><mark style="color:red;">仅type = 37才有此参数</mark></td><td></td></tr><tr><td>eventBonusType</td><td><mark style="color:blue;">number</mark></td><td>活动奖励类型(<mark style="color:red;">只有 type = 38 才需要此字段。</mark>)</td><td></td></tr><tr><td>eventBonusCode</td><td><mark style="color:blue;">string</mark></td><td>活动奖励名称(只有 type = 38 才需要此字段。)</td><td></td></tr><tr><td>betStopTime</td><td><mark style="color:blue;">number</mark></td><td>下注停止时间(毫秒)。 格式为Unix(只有派彩的事件，才需要此字段。)</td><td></td></tr><tr><td>matchId</td><td><mark style="color:blue;">number</mark></td><td>大赛代码。 格式为Unix(只有 type = 8或9 才需要此字段。)</td><td></td></tr><tr><td>withHoldingList</td><td><mark style="color:orange;">array</mark></td><td>預扣返還列表,在预扣返还的请求中会取代 betList</td><td></td></tr><tr><td>gameName</td><td><mark style="color:blue;">string</mark></td><td><p>游戏名称。 </p><p>baccarat </p><p>dragon-tiger </p><p>sic-bo </p><p>roulette </p><p>slot(显示游戏的gameID) </p><p>bull-bull </p><p>fortune-wheel </p><p>black-jack-electronic </p><p>black-jack-live </p><p>mini-game(显示游戏的gameID) </p><p>pok-deng</p></td><td></td></tr></tbody></table>

#### srcResults:

#### detail:

#### detail:

#### detail:

#### detail:
