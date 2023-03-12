---
description: 此api为用户要变更金额，通知ebet处理。
---

# recharge

{% hint style="info" %}
Note: 它返回成功是表示已接收到通知，但处理未完成。 \
Note: 没有限定额度上限。 Note: ebet金额只计算到小数点第二位 \
Note: rechargeReqId请生成唯一值 建議用渠道+玩家+時間 切勿同秒发送 避免我方资料库数据无法判别
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">integer</mark></td><td>渠道 ID</td><td>1</td></tr><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td>apitest01</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">int($int64)</mark></td><td>当前时间,格式为Unix。</td><td>1577808000</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。 字串拼接：username+timestamp<br>Note: 如API用户名参数非必要，可以单独使用timestamp</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td><mark style="color:red;">money</mark></td><td><mark style="color:blue;">number($double)</mark></td><td>要更改金额。 <br>正数表示转入。 <br>负数表示转出。</td><td></td></tr><tr><td><mark style="color:red;">rechargeReqId</mark></td><td><mark style="color:blue;">string</mark></td><td>充值请求ID。</td><td>127.0.0.1</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td></td></tr><tr><td>typeId</td><td><mark style="color:blue;">integer</mark></td><td>钱包类型。默认值为0。</td><td></td></tr></tbody></table>

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
  "channelId": 1,
  "username": "apitest01",
  "timestamp": 1577808000000,
  "signature": "bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==",
  "money": 100,
  "rechargeReqId": "rechargeReqId123456",
  "currency": "CNY",
  "typeId": 0
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td><mark style="color:blue;">integer</mark></td><td>回应状态。</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td></td></tr><tr><td>rechargeReqId</td><td><mark style="color:blue;">string</mark></td><td>充值请求ID。</td><td></td></tr><tr><td>money</td><td><mark style="color:blue;">number($double)</mark></td><td>用户的当前金额。</td><td></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" %}
```json
{
  "status": 200,
  "apiVersion": "1.3.55",
  "rechargeReqId": "rechargeReqId123456",
  "money": 100
}
```
{% endcode %}
