# netCheck

{% hint style="info" %}
* 該API僅用於檢測渠道接收api的server狀態。&#x20;
* 會将请求直接发送到渠道提供的服务器URL。&#x20;
* 在網路狀態不穩時，eBET人員會手動請求確認。
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API名称</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr></tbody></table>

{% code title="Request" overflow="wrap" %}
```json
{
  "event": "netCheck"
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">status</mark></td><td><mark style="color:blue;">integer</mark></td><td><mark style="color:purple;"><code>200</code></mark>:建议返回的状态码</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr></tbody></table>

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Responses" overflow="wrap" %}
```json
{
  "status": 200
}
```
{% endcode %}
