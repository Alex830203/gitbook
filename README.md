---
description: >-
  此页面描述了eBET向渠道发出的'用于验证用户登录'或'通知用户金额更改'的请求。有两种管理玩家资金的方法：单钱包和转账钱包。 "转账钱包" :
  玩家的资金由eBET管理。 "单钱包" : 玩家的资金由渠道管理。 API根据管理方法发送不同的请求。 单钱包所有API务必实作。
---

# eBET請求

## **关于登录流程**

1. 使用不同的登录方法提供玩家信息給eBET。\
   eventType = 1: 在eBET h5网页或App上输入帐号和密码\
   eventType = 3: 在渠道平台登入后，点击**applink**连结\
   eventType = 4: 在渠道平台登入后，点击**token**连结
2. eBET向渠道发送验证登录API请求。\
   转账钱包: RegisterOrLoginReq\
   单钱包: registerOrLogin
3. eBET根据渠道的响应来确定是否让用户进入游戏。

## **发送游戏相关类型**

_投注：当用户单击一次确认投注时，eBET发送投注请求。一回合的点击次数没有限制。_\
_派彩：停止下注后，计算该回合的投注记录并发送派彩请求。_

**基本流程**\
投注：请求下注（type = 1）。如果返回失败，则投注失败。\
派彩: 请求派彩（type = 2）。如果返回失败，请在检查后再次请求相同的内容。

**特殊流程** - _在对牛牛下注翻倍时，将使用此流程。_\
投注: 先请求预扣（type = 27），如果预扣响应成功，则请求下注（type = 1）。 预扣回应失败则使用基本流程的投注失败处理。如果投注回应失败，会将下注错误退款（type = 11）请求发送至渠道以要求退还预扣款。\
派彩: 如果还有剩余的预扣金额，请先请求预扣返还（type = 28），然后再请求派彩（type = 2）。 如果没有剩余的预扣金额，则直接请求派彩（type = 2）。ntation you need to get up and running with the MyAPI API.

## **投注失败流程**

_**投注失败的定义：eBET收到的状态不是200或未收到。**_\
在派彩请求中，betmoney = 0表示eBET认为该投注不成功，因此未计算相关的派彩金额。\
此时渠道可以执行以下操作：

1. 渠道自己退款\
   _派彩:_ 渠道检查betList，如果有投注失败的纪录就自己退款\
   _查询:_ 在eBET送出查询的请求 的时候，该下注注单status返回209代表这个下注已 经退款
2. eBET请求退款 - 渠道的DB允许再次修改\
   _派彩:_ 正常回应， 不用检查betList\
   _查询:_ 提供渠道ＤＢ的纪录， 回传不正确可能会无法退款\
   _退款:_ 根据实作的退款API请求退款
3. eBET请求退款 - 渠道的DB **不允许** 再次修改\
   _派彩:_ 检查betList。 如果有下注失败回应派彩失败给eBET\
   _查询:_ 提供渠道ＤＢ的纪录，回传不正确可能会无法退款\
   _退款:_ 根据实作的退款API请求退款。 退款完成后会重新发送派彩请求

## **单钱包特殊用途**

1. syncCredit将在registerOrLogin成功响应后发送请求。 **两者都必须成功** ，然后用户才能登录eBET游戏。
2. syncCredit响应 **status： 410** 将导致玩家退出eBET游戏。
3. 渠道可以在registerOrLogin响应时自定义其他API请求的用户名。（ eBET后端需要启用相关设置）

## **建议的响应状态代码**

|                                                                                     代码                                                                                    |     描述    |
| :-----------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :-------: |
| <mark style="color:red;background-color:blue;">**20**</mark><mark style="color:red;background-color:blue;"><mark style="color:red;">**0**<mark style="color:red;"></mark> |     成功    |
|                                                       <mark style="color:red;background-color:blue;">**202**</mark>                                                       |   渠道不存在   |
|                                                       <mark style="color:red;background-color:blue;">**206**</mark>                                                       | seqNo 不存在 |
|                                                       <mark style="color:red;background-color:blue;">**207**</mark>                                                       |  退款金额不一致  |

{% swagger method="post" path="/RegisterOrLoginReq" baseUrl="" summary="转帐钱包使用的验证用户登录" %}
{% swagger-description %}
此api用于验证用户登录。

\


将请求直接发送到渠道提供的服务器URL。

\


范例链接：

[请求&回应范例](https://github.com/ITsupporteBET/demo_code/tree/master/API%20for%20transfer%20wallet/RegisterOrLoginReq)


{% endswagger-description %}

{% swagger-parameter in="body" type="string" name="cmd" required="true" %}
example: RegisterOrLoginReq
{% endswagger-parameter %}

{% swagger-parameter in="body" type="array" name="photoUrls" required="true" %}
252542542544
{% endswagger-parameter %}

{% swagger-parameter in="body" name="eventType" type="integer" required="true" %}
example: 1
{% endswagger-parameter %}

{% swagger-parameter in="cookie" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="成功" %}
```javascript
{
  "accessToken": "accessTokenTest",
  "subChannelId": 0,
  "username": "apitest01",
  "status": 200,
  "nickname": "用户昵称，预设随机生成",
  "currency": "CNY"
}
```
{% endswagger-response %}
{% endswagger %}

## Want to jump right in?

Feeling like an eager beaver? Jump in to the quick start docs and get making your first request:

{% content-ref url="quick-start.md" %}
[quick-start.md](quick-start.md)
{% endcontent-ref %}

## Want to deep dive?

Dive a little deeper and start exploring our API reference to get an idea of everything that's possible with the API:

{% content-ref url="api-reference/" %}
[api-reference](api-reference/)
{% endcontent-ref %}
