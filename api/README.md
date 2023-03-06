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

| API用途    | 转帐钱包                                                                                                                                          | 单一钱包                                                       |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| 获得最新游戏连结 | <mark style="color:red;"></mark>[<mark style="color:red;">launchUrl</mark>](common/channel-post/launchurl.md)<mark style="color:red;"></mark> | <mark style="color:red;">launchUrl</mark>                  |
| 创建用户     | <mark style="color:red;">syncuser</mark>                                                                                                      | <mark style="color:red;">syncuser</mark>                   |
| 验证用户登入   | <mark style="color:blue;">RegisterOrLoginReq</mark>                                                                                           | <mark style="color:blue;">registerOrLogin</mark>           |
| 确认用户金额   | <mark style="color:red;">userinfo</mark>                                                                                                      | <mark style="color:blue;">syncCredit</mark>                |
| 查询牌局纪录   | <mark style="color:red;">userbethistory</mark>                                                                                                | <mark style="color:red;">userbethistory</mark>             |
| 查询金额变化纪录 | <mark style="color:red;">usertransaction</mark>                                                                                               | <mark style="color:blue;">queryIncreaseCreditRecord</mark> |
| 金额变化通知   |                                                                                                                                               | <mark style="color:blue;">increaseCredit</mark>            |
| 退款通知     |                                                                                                                                               | <mark style="color:blue;">refundSingleWallet</mark>        |
| 转入/转出    | <p><mark style="color:red;">recharge</mark></p><p><mark style="color:red;">rechargestatus</mark></p>                                          |                                                            |

{% hint style="warning" %}
请在上线前确认API是否都已实施且可以正常收发。
{% endhint %}
