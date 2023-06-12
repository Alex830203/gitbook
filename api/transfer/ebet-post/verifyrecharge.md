---
description: 确认recharge请求
---

# verifyRecharge

<div data-full-width="false">

<figure><img src="../../../.gitbook/assets/recharge double.png" alt="变更额度处理流程（转帐钱包）"><figcaption><p>变更额度处理流程（转帐钱包）</p></figcaption></figure>

</div>

<table data-card-size="large" data-view="cards" data-full-width="false"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>与流程相关的API页面</td><td><a href="../channel-post/recharge.md">recharge</a></td><td><a href="../channel-post/rechargestatus.md">rechargeStatus</a></td></tr></tbody></table>

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="164">参数</th><th width="122">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td>1</td></tr><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td>apitest01</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>当前时间,格式为Unix。</td><td>1577808000</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。 字串拼接：username+timestamp</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td><mark style="color:red;">money</mark></td><td><mark style="color:blue;">number</mark></td><td>要更改金额。 <br><mark style="color:red;">正数表示转入。</mark> <br><mark style="color:red;">负数表示转出。</mark></td><td></td></tr><tr><td><mark style="color:red;">rechargeReqId</mark></td><td><mark style="color:blue;">string</mark></td><td>充值请求ID。</td><td>127.0.0.1</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。参数值定义请参考下表。</td><td></td></tr><tr><td>typeId</td><td><mark style="color:blue;">number</mark></td><td>钱包类型。默认值为0。参数值定义请参考下表。</td><td></td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>

<mark style="color:red;">rechargeReqId是唯一值。建议使用"渠道+玩家+时间"做唯一值內容设置。</mark>

<mark style="color:red;">同玩家请勿同秒发送，避免数据错乱。</mark>
{% endhint %}

{% hint style="info" %}
<mark style="color:blue;">金额没有限定额度上限。只计算到小数点第二位。</mark>
{% endhint %}

{% embed url="https://docs.google.com/spreadsheets/d/1ejxETVOI9kcCAP5eNpT6CIi4ftGHwcYWMHJTEPqLILs" %}

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
    "money": 1000,
    "timestamp": 1683684208,
    "rechargeReqId": "1demo1000",
    "signature": "MxvM9ysB1uRjIxNbZp2RsFtIMVsaNhjif/zKm9QJsyr6QbH+I2HMJbL8qwaVZTD0tDFXs33Z1C6dJo0HYH4rXg=="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="164">参数</th><th width="119">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr></tbody></table>

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "status": 200
}
```
{% endcode %}

{% hint style="warning" %}
<mark style="color:orange;">返回成功是表示已接收到通知，但处理不一定完成。请使用API:</mark> [rechargeStatus](../channel-post/rechargestatus.md)<mark style="color:orange;">做处理状态的确认</mark>
{% endhint %}
