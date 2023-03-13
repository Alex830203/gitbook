---
description: 此api为检查ebet是否有收到并处理完成充值请求。
---

# rechargestatus

{% hint style="info" %}
若rechargestatus返回-1，可能為我方系統還沒寫入數據庫。 \
請貴司再多請求2次做最後確認(建議貴司隔5秒後再做請求)，如最後仍返回-1，请向eBET人员寻求协助。
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">integer</mark></td><td>渠道 ID</td><td>1</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。字串拼接：rechargeReqId</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td><mark style="color:red;">rechargeReqId</mark></td><td><mark style="color:blue;">string</mark></td><td>充值请求ID。</td><td>127.0.0.1</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td></td></tr></tbody></table>

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
  "channelId": 1,
  "signature": "PooUUWwXW5lDNzAgk9f6CFEhTbKq/J3b5UScNMl3SnBzCLxLDXZ/s2y8nF8UufSXgrHyS3DfJ6CJxAqjKRg53A==",
  "rechargeReqId": "rechargeReqId123456",
  "currency": "CNY"
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td><mark style="color:blue;">integer</mark></td><td>回应状态。</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td></td></tr><tr><td>rechargeReqId</td><td><mark style="color:blue;">string</mark></td><td>充值请求ID。</td><td></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" %}
```json
{
  "status": 200,
  "apiVersion": "1.3.55",
  "rechargeReqId": "rechargeReqId123456"
}
```
{% endcode %}
