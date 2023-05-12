---
description: 此页面提供eBET 必要实作的API相关资讯。
---

# API

#### eBET提供两种不同的钱包类型：单钱包 和 转账钱包 。&#x20;

1. **转账钱包** : 玩家的资金由eBET管理。
2. **单钱包** : 玩家的资金由渠道管理。

{% hint style="info" %}
<mark style="color:blue;">蓝色：此API是由eBET发送相关请求</mark>

<mark style="color:red;">红色：此API是由渠道发送相关请求</mark>
{% endhint %}

| API用途    | 转帐钱包                                                                                                                                                                                                       | 单一钱包                                                                                                        |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| 获得最新游戏连结 | [<mark style="color:red;">launchUrl</mark>](common/channel-post/launchurl.md)                                                                                                                              | [<mark style="color:red;">launchUrl</mark>](common/channel-post/launchurl.md)                               |
| 创建用户     | [<mark style="color:red;">syncuser</mark>](common/channel-post/syncuser.md)                                                                                                                                | [<mark style="color:red;">syncuser</mark>](common/channel-post/syncuser.md)                                 |
| 验证用户登入   | [<mark style="color:blue;">RegisterOrLoginReq</mark>](transfer/ebet-post/registerorloginreq.md)                                                                                                            | [<mark style="color:blue;">registerOrLogin</mark>](single/ebet-post/registerorlogin.md)                     |
| 确认用户金额   | [<mark style="color:red;">userinfo</mark>](common/channel-post/userinfo.md)                                                                                                                                | [<mark style="color:blue;">syncCredit</mark>](single/ebet-post/synccredit.md)                               |
| 查询牌局纪录   | [<mark style="color:red;">userbethistory</mark>](common/channel-post/userbethistory.md)                                                                                                                    | [<mark style="color:red;">userbethistory</mark>](common/channel-post/userbethistory.md)                     |
| 查询金额变化纪录 | [<mark style="color:red;">usertransaction</mark>](common/channel-post/usertransaction.md)                                                                                                                  | [<mark style="color:blue;">queryIncreaseCreditRecord</mark>](single/ebet-post/queryincreasecreditrecord.md) |
| 金额变化通知   |                                                                                                                                                                                                            | [<mark style="color:blue;">increaseCredit</mark>](single/ebet-post/increasecredit.md)                       |
| 退款通知     |                                                                                                                                                                                                            | [<mark style="color:blue;">refundSingleWallet</mark>](single/ebet-post/refundsinglewallet.md)               |
| 转入/转出    | <p><a href="transfer/channel-post/recharge.md"><mark style="color:red;">recharge</mark></a></p><p><a href="transfer/channel-post/rechargestatus.md"><mark style="color:red;">rechargestatus</mark></a></p> |                                                                                                             |

{% hint style="warning" %}
请在上线前确认API是否都已实施且可以正常收发。
{% endhint %}
