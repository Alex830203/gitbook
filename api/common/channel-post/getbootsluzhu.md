---
description: 查询已经结束的牌靴牌局结果纪录
---

# getbootsluzhu

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="153">参数</th><th width="122">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道ID。</td><td>RegisterOrLoginReq</td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>时间戳记。以毫秒为单位。格式为Unix Time。</td><td>1</td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。 字串拼接：timestamp</td><td>1</td></tr><tr><td><mark style="color:red;">tableType</mark></td><td><mark style="color:blue;">number</mark></td><td>游戏类型。</td><td></td></tr><tr><td><mark style="color:red;">startTimeStr</mark></td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的开始。</td><td></td></tr><tr><td><mark style="color:red;">endTimeStr</mark></td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的结束。</td><td></td></tr><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号码。</td><td></td></tr><tr><td>bootsCardId</td><td><mark style="color:blue;">string</mark></td><td>牌靴ID。</td><td></td></tr><tr><td>bootsNumber</td><td><mark style="color:blue;">number</mark></td><td>牌靴号码。</td><td></td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "timestamp": 1666503623,
    "tableType": 1,
    "startTimeStr": "2023-03-11 23:30:00",
    "endTimeStr": "2023-03-12 00:30:00",
    "signature": "HYblBUothiWWRCk/kl7tCcOh3OLPWiEyiaiospwcR26jMfB2Y2/aAaE0gs8xopeX8pFws3glbx0F8vkMHEemzfha6wdqdRQMe2t9i2ibMZXX/z6Cf8gQVI7LOb55CZVhwjZAqkH5QNsclcprpaTfnJcT7cno7Typz80+hr9DZqE="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="176">参数</th><th width="117.66666666666666">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>tableCode</td><td><mark style="color:blue;">string</mark></td><td>游戏桌号码。</td><td></td></tr><tr><td>bootsDetail</td><td><mark style="color:blue;">object</mark></td><td>牌靴详情。阵列值为物件，下表为物件参数说明。</td><td>200</td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>eBET回应状态。</td><td><pre><code>accessTokenTest
</code></pre></td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td><pre><code>0
</code></pre></td></tr></tbody></table>

bootsDetail

<table><thead><tr><th width="176">参数</th><th width="117.66666666666666">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>bootsCardId</td><td><mark style="color:blue;">string</mark></td><td>牌靴ID。</td><td></td></tr><tr><td>bootsNumber</td><td><mark style="color:blue;">number</mark></td><td>牌靴号码。</td><td>200</td></tr><tr><td>luzhu</td><td><mark style="color:blue;">array</mark></td><td>路书记录。 数组值组成为“roundCode - result”</td><td><pre><code>accessTokenTest
</code></pre></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "tableCode": "BP1",
    "bootsDetail": {
        "2023-03-11": [
            {
                "bootsCardId": "116",
                "bootsNumber": 29,
                "luzhu": [
                    "BP1-230311232942-60",
                    "BP1-230311233029-80",
                    "BP1-230311233111-60",
                    "BP1-230311233203-80",
                    "BP1-230311233246-60",
                    "BP1-230311233329-60",
                    "BP1-230311233417-60",
                    "BP1-230311233504-60",
                    "BP1-230311233556-80",
                    "BP1-230311233639-60",
                    "BP1-230311233725-68",
                    "BP1-230311233817-80",
                    "BP1-230311233901-68",
                    "BP1-230311233949-80",
                    "BP1-230311234035-80",
                    "BP1-230311234119-80",
                    "BP1-230311234206-80",
                    "BP1-230311234249-60",
                    "BP1-230311234332-60",
                    "BP1-230311234423-80",
                    "BP1-230311234506-80",
                    "BP1-230311234557-80",
                    "BP1-230311234643-60",
                    "BP1-230311234730-80",
                    "BP1-230311234821-68",
                    "BP1-230311234907-68",
                    "BP1-230311234959-60",
                    "BP1-230311235047-68",
                    "BP1-230311235131-80",
                    "BP1-230311235221-80",
                    "BP1-230311235316-60",
                    "BP1-230311235408-60",
                    "BP1-230311235458-80",
                    "BP1-230311235546-60",
                    "BP1-230311235651-60",
                    "BP1-230311235749-68",
                    "BP1-230311235843-80"
                ]
            }
        ],
        "2023-03-12": [
            {
                "bootsCardId": "116",
                "bootsNumber": 29,
                "luzhu": [
                    "BP1-230311235928-60",
                    "BP1-230312000020-60",
                    "BP1-230312000109-60",
                    "BP1-230312000154-80"
                ]
            },
            {
                "bootsCardId": "117",
                "bootsNumber": 1,
                "luzhu": [
                    "BP1-230312000607-68",
                    "BP1-230312000653-60",
                    "BP1-230312000745-80",
                    "BP1-230312000828-60",
                    "BP1-230312000921-60",
                    "BP1-230312001005-60",
                    "BP1-230312001053-80",
                    "BP1-230312001141-80",
                    "BP1-230312001226-60",
                    "BP1-230312001316-60",
                    "BP1-230312001403-68",
                    "BP1-230312001456-60",
                    "BP1-230312001539-60",
                    "BP1-230312001631-80",
                    "BP1-230312001724-60",
                    "BP1-230312001816-80",
                    "BP1-230312001906-80",
                    "BP1-230312001958-80",
                    "BP1-230312002050-80",
                    "BP1-230312002134-80",
                    "BP1-230312002227-80",
                    "BP1-230312002315-80",
                    "BP1-230312002404-60",
                    "BP1-230312002452-80",
                    "BP1-230312002537-80",
                    "BP1-230312002631-60",
                    "BP1-230312002716-80",
                    "BP1-230312002759-68",
                    "BP1-230312002847-80"
                ]
            }
        ]
    },
    "status": 200,
    "apiVersion": "1.5.92"
}
```
{% endcode %}
