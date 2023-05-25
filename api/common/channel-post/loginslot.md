---
description: 直接登入老虎机游戏机台
---

# loginslot

{% hint style="warning" %}
<mark style="color:orange;">使用此方法仍会发送验证登录请求。 只有成功验证后，才会提供登录链接。</mark>
{% endhint %}

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="169">参数</th><th width="120">格式</th><th>描述</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道ID</td></tr><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>时间戳记。以毫秒为单位。格式为Unix Time。</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。 字串拼接：username+timestamp</td></tr><tr><td><mark style="color:red;">gameID</mark></td><td><mark style="color:blue;">string</mark></td><td>老虎机游戏ID</td></tr><tr><td><mark style="color:red;">providerId</mark></td><td><mark style="color:blue;">string</mark></td><td>老虎机游戏供应商ID</td></tr><tr><td><mark style="color:red;">loginEventType</mark></td><td><mark style="color:blue;">number</mark></td><td>登录方式：<br>1: 普通登录<br>4: Token 登录</td></tr><tr><td>pwd</td><td><mark style="color:blue;">string</mark></td><td>密码。当loginEventType = 1时必需</td></tr><tr><td>token</td><td><mark style="color:blue;">string</mark></td><td>AccessToken。当loginEventType = 4时必需</td></tr><tr><td>ip</td><td><mark style="color:blue;">string</mark></td><td>登录IP</td></tr><tr><td>language</td><td><mark style="color:blue;">string</mark></td><td>用户语言</td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

language参数值

|         |      |
| ------- | ---- |
| zh-hans | 简体中文 |
| vi      | 越南语  |
| th      | 泰文   |
| ru      | 俄语   |
| pt      | 葡萄牙語 |
| jp      | 日语   |
| in      | 印尼语  |
| es      | 西班牙语 |

{% tabs %}
{% tab title="Token 登录" %}
{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
  "channelId": 1,
  "username": "demo",
  "timestamp": 1679885941,
  "signature": "jHCw36fJF8Bh4cclYxssT0nKLbEzQesaZZ2/fIWalvhyClqAzd2r4HM9CX9ORag/Cw+CS8I19mhkYjDDtHVM2A==",
  "providerId": "genesis",
  "gameID": "M4-0001",
  "language": "zh-hans",
  "loginEventType": 4,
  "token": "********"
}
```
{% endcode %}
{% endtab %}

{% tab title="普通登录" %}
{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
  "channelId": 1,
  "username": "demo",
  "timestamp": 1679885941,
  "signature": "jHCw36fJF8Bh4cclYxssT0nKLbEzQesaZZ2/fIWalvhyClqAzd2r4HM9CX9ORag/Cw+CS8I19mhkYjDDtHVM2A==",
  "providerId": "genesis",
  "gameID": "M4-0001",
  "language": "zh-hans",
  "loginEventType": 1,
  "pwd": "********"
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="176">参数</th><th width="117.66666666666666">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>slotURL</td><td><mark style="color:blue;">string</mark></td><td>登入老虎机游戏的连结。</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "slotURL": "https://ugc.kblgg.com/NGM4-0001/HTML5/index.html?turbo=true&mode=real&partner=964dc891-31c1-4579-8628-77ee21c35809&session=322dbbf66403a7e4e947f2e6ebfff110-88915679&language=zh-hant&gs=nurgs-RMX&partnerCode=EbetCNY&referer=ugc.kblgg.com&refererRetries=0&device=DESKTOP",
    "status": 200,
    "apiVersion": "1.5.94"
}
```
{% endcode %}
