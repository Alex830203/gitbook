---
description: 取得电子游戏最新清单
---

# slotgamelist

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道ID。</td><td>RegisterOrLoginReq</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>时间戳记。以毫秒为单位。格式为Unix Time。</td><td>1</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。 字串拼接：channelId+timestamp</td><td>1</td></tr></tbody></table>

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
    "channelId": 1,
    "timestamp": 1666504030,
    "signature": "Q6acG/0KsYFt5bZnDvgHtnR2qiJli34KLl3dJi3f9Zvrl/zxhPtefzfxq/svPfxG/i+hDusz49VPrYEvlm5O4t1MkgcYEoJfeztzDxc5mlS6TpORXIXi6cV2Epz+4ztB6aFlp3zaV2gP4jme1zcbau9nTtF8OD/gZL4t9ndz01o="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>slotGames</td><td><mark style="color:orange;">array</mark></td><td><p>电子游戏列表。</p><p>阵列值为物件，下表为物件参数说明。</p></td><td><pre><code>0
</code></pre></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td><pre><code>apitest01
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td>200</td></tr></tbody></table>

slotGames

| 参数          | 格式                                      | 描述      |
| ----------- | --------------------------------------- | ------- |
| gameID      | <mark style="color:blue;">string</mark> | 游戏ID    |
| english     | <mark style="color:blue;">string</mark> | 游戏的英文名称 |
| chinese     | <mark style="color:blue;">string</mark> | 游戏的中文名称 |
| providerId  | <mark style="color:blue;">string</mark> | 游戏供应商ID |
| releaseDate | <mark style="color:blue;">string</mark> | 发布日期    |

{% code title="Responses" overflow="wrap" %}
```json
{
    "slotGames": [
        {
            "gameID": "srocket",
            "english": "Solo-Rocket",
            "chinese": "单人猜火箭",
            "providerId": "wayi",
            "releaseDate": "2021-07-14"
        },
        {
            "gameID": "WHG-0021",
            "english": "Mystic Wilds",
            "chinese": "神秘百搭",
            "providerId": "genesis",
            "releaseDate": "2022-09-06"
        }
    ],
    "status": 200,
    "apiVersion": "1.5.75"
}
```
{% endcode %}
