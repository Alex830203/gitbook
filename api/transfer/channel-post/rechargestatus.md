---
description: 检查eBET是否有收到并处理完成充值请求
---

# rechargestatus

<figure><img src="../../../.gitbook/assets/recharge double.png" alt="变更额度处理流程（转帐钱包）"><figcaption><p>变更额度处理流程（转帐钱包）</p></figcaption></figure>

<table data-card-size="large" data-view="cards" data-full-width="false"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>与流程相关的API页面</td><td><a href="recharge.md">recharge</a></td><td><a href="rechargestatus.md">rechargeStatus</a></td></tr></tbody></table>

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="164">参数</th><th width="168">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td>1</td></tr><tr><td><mark style="color:red;">rechargeReqId</mark></td><td><mark style="color:blue;">string</mark></td><td>充值请求ID。</td><td>127.0.0.1</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。字串拼接：rechargeReqId</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td></td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "rechargeReqId": "1demo1000",
    "signature": "ejR/HV4lUhbzWlSdJFdJqI2TSRizbVN2jl/YdayElU4ptBLppNA6LdfW6orhgS/uJqntyL7S17ghdodBBV8Exw=="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="164">参数</th><th width="170">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>rechargeReqId</td><td><mark style="color:blue;">string</mark></td><td>充值请求ID。</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "rechargeReqId": "1demo1000",
    "status": 200,
    "apiVersion": "1.5.97"
}
```
{% endcode %}

{% hint style="warning" %}
<mark style="color:orange;">若rechargestatus返回-1，可能為我方系統還沒寫入數據庫。 請貴司再多請求2次做最後確認(建議貴司隔5秒後再做請求)，如最後仍返回-1，请向eBET人员寻求协助。</mark>
{% endhint %}
