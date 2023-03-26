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

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td>RegisterOrLoginReq</td></tr><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td></td></tr><tr><td>money</td><td><mark style="color:blue;">number($double)</mark></td><td>需要变动的金额，如果为<mark style="color:red;">负数代表 玩家要扣金额</mark></td><td></td></tr><tr><td>type</td><td><mark style="color:blue;">number</mark></td><td>交易事务类型</td><td></td></tr><tr><td>platform</td><td><mark style="color:blue;">number</mark></td><td>用户平台</td><td></td></tr></tbody></table>

{% embed url="https://docs.google.com/spreadsheets/d/1ejxETVOI9kcCAP5eNpT6CIi4ftGHwcYWMHJTEPqLILs" %}

