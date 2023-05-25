---
description: 提供用户投注历史的URL
---

# userBetTracer

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="169">参数</th><th width="117">格式</th><th>描述</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道ID</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>时间戳记。以毫秒为单位。格式为Unix Time。</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。 字串拼接：username+timestamp <br>Note: 如API用户名参数非必要，可以单独使用timestamp</td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号码。</td></tr><tr><td>betHistoryId</td><td><mark style="color:blue;">string</mark></td><td>投注记录ID。 <br>如果不使用此参数，则必须使用username和roundCode。</td></tr><tr><td>lang</td><td><mark style="color:blue;">string</mark></td><td>语言代码。默认英语。</td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
    "timestamp": 1680225949,
    "roundCode": "BP1-230331092247",
    "signature": "GBbC+rGAoCMVbf95VEowEKnz7r5KVCSNz7GLf697Ong7B1A9O5W4ebiW5xIb6VIc+G4bLYbrtmYtgesfN3x9133RXscIfHTEi8flLLLz3SApnZGg4Sd7NI01Q4nAn3pwxZXW3/0HqLqFavLnK/VZ8atqoqj9rO6JgKVeyLhitvE="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="176">参数</th><th width="117.66666666666666">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>path</td><td><mark style="color:blue;">string</mark></td><td>链接。 已添加了用户名称，渠道ID，牌局号和語系。</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td><pre><code>0
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>apitest01
</code></pre></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "path": "http://www.ebet2018.com/userBetTracer.html?userName=demo&channelId=1&roundCode=BP1-230331092247&lang=en_us",
    "status": 200,
    "apiVersion": "1.5.94"
}
```
{% endcode %}

### URL path 的規則

<table><thead><tr><th width="177">参数</th><th></th></tr></thead><tbody><tr><td>userName</td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td></tr><tr><td>channelId</td><td>渠道ID</td></tr><tr><td>roundCode</td><td>牌局号码。</td></tr><tr><td>lang</td><td>语言代码。</td></tr><tr><td><mark style="color:red;">signature</mark></td><td>签名。 字串拼接：channelId+username+roundCode+lang</td></tr><tr><td><mark style="color:green;">display</mark></td><td>有效投注栏位。加入display=1可以关闭。</td></tr></tbody></table>

{% hint style="warning" %}
<mark style="color:orange;">signature 需自行用GET method添加上去</mark>
{% endhint %}

{% hint style="success" %}
<mark style="color:green;">display预设会显示，可自行添加此参数决定是否要显示</mark>
{% endhint %}
