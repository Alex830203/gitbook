---
description: 通知渠道用户额度变动
---

# ​​increaseCredit\*

{% hint style="info" %}
seqNo是唯一值。 避免重复处理金額，请勿记录相同的支出seqNo。\
我们有一个retry机制。如果之前已经成功处理过，请向eBET返回201（重复seqNo）。\
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
{% endtab %}

{% tab title="Type 2" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>dealerName</td><td><mark style="color:blue;">string</mark></td><td>荷官名</td><td></td></tr><tr><td>bootsCardId</td><td><mark style="color:blue;">string</mark></td><td>靴盒号</td><td></td></tr><tr><td>gameName</td><td><mark style="color:blue;">string</mark></td><td><p>游戏名称。 </p><p>baccarat </p><p>dragon-tiger </p><p>sic-bo </p><p>roulette </p><p>slot(显示游戏的gameID) </p><p>bull-bull </p><p>fortune-wheel </p><p>black-jack-electronic </p><p>black-jack-live </p><p>mini-game(显示游戏的gameID) </p><p>pok-deng</p></td><td></td></tr><tr><td>srcResults</td><td><mark style="color:blue;">array</mark></td><td><p>荷官开牌结果。 </p><p>百家乐：牌面3个一组，顺序为闲/庄，没发的牌面会以null代替 </p><p>龙虎：牌面2个，顺序为龙/虎 </p><p>牛牛：牌面5个一组，顺序为庄/闲1/闲2/闲3 </p><p>博丁：牌面2个一组，顺序为庄/闲1/闲2/闲3/闲4/闲5</p></td><td></td></tr><tr><td>brokerageRequired</td><td><mark style="color:blue;">boolean</mark></td><td>是否為免佣金百家乐。 <mark style="color:red;">只有百家乐才會有此参数</mark></td><td></td></tr><tr><td>results</td><td><mark style="color:blue;">array</mark></td><td>中奖项目</td><td></td></tr><tr><td><a href="increasecredit.md#betlist">betList</a></td><td><mark style="color:blue;">array</mark></td><td>注单详情</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>betTime</td><td><mark style="color:blue;">number</mark></td><td>下注时间(毫秒)。 格式为Unix时间</td><td></td></tr><tr><td>totalBet</td><td><mark style="color:blue;">number</mark></td><td>总投注</td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td>有效投注</td><td></td></tr><tr><td><a href="increasecredit.md#withholdinglist">withHoldingList</a></td><td><mark style="color:blue;">array</mark></td><td>預扣返還列表,在预扣返还的请求中会取代 betList</td><td></td></tr><tr><td>payout</td><td><mark style="color:blue;">number</mark></td><td>派彩总额</td><td></td></tr><tr><td>payoutTime</td><td><mark style="color:blue;">number</mark></td><td>派彩时间(毫秒)。 格式为Unix</td><td></td></tr><tr><td>betStopTime</td><td><mark style="color:blue;">number</mark></td><td>下注停止时间(毫秒)。 格式为Unix<mark style="color:red;">(只有派彩的事件，才需要此字段。)</mark></td><td></td></tr></tbody></table>

#### betList

<table><thead><tr><th width="164">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td>RegisterOrLoginReq</td></tr><tr><td>betMoney</td><td><mark style="color:blue;">number</mark></td><td>投注金额。 <mark style="color:red;">当betMoney = 0时，视为下注失败。</mark></td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>投注请求的序号。 </td><td></td></tr><tr><td>payout</td><td><mark style="color:blue;">number</mark></td><td>派彩金额。 </td><td></td></tr><tr><td>number</td><td><mark style="color:blue;">string</mark></td><td>游戏下注的号码。 只有特定项目才会有此字段</td><td></td></tr><tr><td>odds</td><td><mark style="color:blue;">number</mark></td><td><p>赔率。 </p><p>Noted: </p><p>1.支援所有游戏除了老虎机 </p><p>2.赔率不含投注额</p></td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td><p>每个投注项目的有效投注。 </p><p>该参数会依照有效投注的计算规则，请参考：<a href="../../can-shu-shuo-ming.md#you-xiao-tou-zhu">参数说明-有效投注。</a> </p></td><td></td></tr><tr><td>rebateAmount</td><td><mark style="color:blue;">number</mark></td><td>返水。</td><td></td></tr><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID</td><td></td></tr></tbody></table>

#### withHoldingList

<table><thead><tr><th width="160">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>withHolding</td><td><mark style="color:blue;">number</mark></td><td>預扣金额。<mark style="color:red;">withHolding =0时,代表預扣失败。</mark></td><td>RegisterOrLoginReq</td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td><p>预扣状态 </p><p>1: 成功 </p><p>0: 失败或没有金额需要返还 </p><p>11:退款 </p><p>13:退款失败</p></td><td></td></tr><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td></td></tr><tr><td>withHoldingId</td><td><mark style="color:blue;">string</mark></td><td>游戏下注的号码。 只有特定项目才会有此字段</td><td></td></tr><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>預扣请求的序列编号</td><td></td></tr><tr><td>refund</td><td><mark style="color:blue;">number</mark></td><td>牛牛返还金额</td><td></td></tr></tbody></table>
{% endtab %}

{% tab title="Type 27" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>betTime</td><td><mark style="color:blue;">number</mark></td><td>下注时间(毫秒)。 格式为Unix时间</td><td></td></tr><tr><td>betList</td><td><mark style="color:blue;">array</mark></td><td>注单详情</td><td></td></tr><tr><td>totalBet</td><td><mark style="color:blue;">number</mark></td><td>总投注</td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td>有效投注</td><td></td></tr></tbody></table>

#### betList

<table><thead><tr><th width="164">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td>RegisterOrLoginReq</td></tr><tr><td>betMoney</td><td><mark style="color:blue;">number</mark></td><td>投注金额。 </td><td></td></tr></tbody></table>
{% endtab %}

{% tab title="Type 28" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>withHoldingList</td><td><mark style="color:blue;">array</mark></td><td>預扣返還列表,在预扣返还的请求中会取代 betList</td><td></td></tr></tbody></table>

#### withHoldingList

<table><thead><tr><th width="160">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>withHolding</td><td><mark style="color:blue;">number</mark></td><td>預扣金额。<mark style="color:red;">withHolding =0时,代表預扣失败。</mark></td><td>RegisterOrLoginReq</td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td><p>预扣状态 </p><p>1: 成功 </p><p>0: 失败或没有金额需要返还 </p><p>11:退款 </p><p>13:退款失败</p></td><td></td></tr><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td></td></tr><tr><td>withHoldingId</td><td><mark style="color:blue;">string</mark></td><td>游戏下注的号码。 只有特定项目才会有此字段</td><td></td></tr><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>預扣请求的序列编号</td><td></td></tr><tr><td>refund</td><td><mark style="color:blue;">number</mark></td><td>牛牛返还金额,<mark style="color:red;">仅只有type=28的事件，才需要此字段。</mark></td><td></td></tr></tbody></table>
{% endtab %}

{% tab title="Type 11" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>betTime</td><td><mark style="color:blue;">number</mark></td><td>下注时间(毫秒)。 格式为Unix时间</td><td></td></tr><tr><td>betList</td><td><mark style="color:blue;">array</mark></td><td>注单详情</td><td></td></tr><tr><td>totalBet</td><td><mark style="color:blue;">number</mark></td><td>总投注</td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td>有效投注</td><td></td></tr><tr><td>withholdingSeqNo</td><td><mark style="color:blue;">string</mark></td><td>牛牛預扣投注退款请求(type=27)的序号。 </td><td></td></tr></tbody></table>

#### betList

<table><thead><tr><th width="164">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td>RegisterOrLoginReq</td></tr><tr><td>betMoney</td><td><mark style="color:blue;">number</mark></td><td>投注金额。</td><td></td></tr><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID</td><td></td></tr></tbody></table>
{% endtab %}

{% tab title="Type 37" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>srcResults</td><td><mark style="color:blue;">array</mark></td><td><p>荷官开牌结果。 </p><p>百家乐：牌面3个一组，顺序为闲/庄，没发的牌面会以null代替 </p><p>龙虎：牌面2个，顺序为龙/虎 </p><p>牛牛：牌面5个一组，顺序为庄/闲1/闲2/闲3 </p><p>博丁：牌面2个一组，顺序为庄/闲1/闲2/闲3/闲4/闲5</p></td><td></td></tr><tr><td>brokerageRequired</td><td><mark style="color:blue;">boolean</mark></td><td>是否為免佣金百家乐。 <mark style="color:red;">只有百家乐才會有此参数</mark></td><td></td></tr><tr><td>results</td><td><mark style="color:blue;">array</mark></td><td>中奖项目</td><td></td></tr><tr><td>betList</td><td><mark style="color:blue;">array</mark></td><td>注单详情</td><td></td></tr><tr><td>modifyBetList</td><td><mark style="color:blue;">array</mark></td><td></td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>betTime</td><td><mark style="color:blue;">number</mark></td><td>下注时间(毫秒)。 格式为Unix时间</td><td></td></tr><tr><td>totalBet</td><td><mark style="color:blue;">number</mark></td><td>总投注</td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td>有效投注</td><td></td></tr><tr><td>payout</td><td><mark style="color:blue;">number</mark></td><td>派彩总额</td><td></td></tr><tr><td>payoutTime</td><td><mark style="color:blue;">number</mark></td><td>派彩时间(毫秒)。 格式为Unix</td><td></td></tr></tbody></table>

#### betList

<table><thead><tr><th width="164">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td>RegisterOrLoginReq</td></tr><tr><td>betMoney</td><td><mark style="color:blue;">number</mark></td><td>投注金额。 <mark style="color:red;">当betMoney = 0时，视为下注失败。</mark></td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>投注请求的序号。 </td><td></td></tr><tr><td>payout</td><td><mark style="color:blue;">number</mark></td><td>派彩金额。 </td><td></td></tr><tr><td>number</td><td><mark style="color:blue;">string</mark></td><td>游戏下注的号码。 只有特定项目才会有此字段</td><td></td></tr><tr><td>odds</td><td><mark style="color:blue;">number</mark></td><td><p>赔率。 </p><p>Noted: </p><p>1.支援所有游戏除了老虎机 </p><p>2.赔率不含投注额</p></td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td><p>每个投注项目的有效投注。 </p><p>该参数会依照有效投注的计算规则，请参考：<a href="../../can-shu-shuo-ming.md#you-xiao-tou-zhu">参数说明-有效投注。</a> </p></td><td></td></tr><tr><td>rebateAmount</td><td><mark style="color:blue;">number</mark></td><td>返水。</td><td></td></tr><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID</td><td></td></tr></tbody></table>

#### modifyBetList

<table><thead><tr><th width="164">参数</th><th width="180">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>betType</td><td><mark style="color:blue;">number</mark></td><td>投注牌型</td><td>RegisterOrLoginReq</td></tr><tr><td>betMoney</td><td><mark style="color:blue;">number</mark></td><td>投注金额。 <mark style="color:red;">当betMoney = 0时，视为下注失败。</mark></td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>投注请求的序号。 </td><td></td></tr><tr><td>payout</td><td><mark style="color:blue;">number</mark></td><td>派彩金额。 </td><td></td></tr><tr><td>number</td><td><mark style="color:blue;">string</mark></td><td>游戏下注的号码。 只有特定项目才会有此字段</td><td></td></tr><tr><td>odds</td><td><mark style="color:blue;">number</mark></td><td><p>赔率。 </p><p>Noted: </p><p>1.支援所有游戏除了老虎机 </p><p>2.赔率不含投注额</p></td><td></td></tr><tr><td>validBet</td><td><mark style="color:blue;">number</mark></td><td><p>每个投注项目的有效投注。 </p><p>该参数会依照有效投注的计算规则，请参考：<a href="../../can-shu-shuo-ming.md#you-xiao-tou-zhu">参数说明-有效投注。</a> </p></td><td></td></tr><tr><td>rebateAmount</td><td><mark style="color:blue;">number</mark></td><td>返水。</td><td></td></tr><tr><td>betId</td><td><mark style="color:blue;">string</mark></td><td>投注ID</td><td></td></tr></tbody></table>


{% endtab %}

{% tab title="Type 3" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr></tbody></table>
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Type 8" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>matchId</td><td><mark style="color:blue;">number</mark></td><td>大赛代码。</td><td></td></tr></tbody></table>
{% endtab %}

{% tab title="Type 9" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr><tr><td>matchId</td><td><mark style="color:blue;">number</mark></td><td>大赛代码。</td><td></td></tr></tbody></table>
{% endtab %}

{% tab title="Type 14" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr></tbody></table>
{% endtab %}

{% tab title="Type 15 " %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr></tbody></table>
{% endtab %}

{% tab title="Type 23" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr></tbody></table>
{% endtab %}

{% tab title="Type 24" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号</td><td></td></tr><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>tableSubType</td><td><mark style="color:blue;">number</mark></td><td>游戏桌类型</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号</td><td></td></tr></tbody></table>
{% endtab %}

{% tab title="Type 38" %}
#### detail

<table><thead><tr><th width="196">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableType</td><td><mark style="color:blue;">number</mark></td><td>游戏类型</td><td></td></tr><tr><td>eventBonusType</td><td><mark style="color:blue;">number</mark></td><td>活动奖励类型</td><td></td></tr><tr><td>eventBonusCode</td><td><mark style="color:blue;">string</mark></td><td>活动奖励名称</td><td></td></tr></tbody></table>
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

