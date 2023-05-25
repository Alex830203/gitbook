---
description: 查询渠道数据库中的increaseCredit的处理状态。
---

# queryIncreaseCreditRecord

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="150">参数</th><th width="116">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>channelId</td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td>RegisterOrLoginReq</td></tr><tr><td>querySeqNo</td><td><mark style="color:blue;">string</mark></td><td>要查询的序列号，以逗号分隔。</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号。</td><td></td></tr><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API 名称。</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">number</mark></td><td>时间戳记，以毫秒为单位。</td><td></td></tr><tr><td>sessionToken</td><td><mark style="color:blue;">string</mark></td><td>sessionToken。由渠道提供或随机生成。</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 </td><td></td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td>签名。 字符串拼接: username+timestamp</td><td></td></tr></tbody></table>

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
    "querySeqNo": "d57c3a0baedce10b428e148698caf468,9865152f1d11b655d73ece4c7611e063",
    "roundCode": "BP1-230510165431",
    "event": "queryIncreaseCreditRecord",
    "timestamp": 1683740363499,
    "sessionToken": "6c7c275b4c6b875ca1ac543473729a51",
    "seqNo": "cf641b394c2257b8edc0e3e8fefa0086",
    "signature": "DKIVfCjii/6mVcE/l5uXVOaPSmPbO0lFGHSGdaf+aMM8LhlUwOgi9ntKfe+CsUgL1wkWlRCl2zgm2XXWPkLqzg=="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="150">参数</th><th width="108">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">seqNo</mark></td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td><mark style="color:red;">event</mark></td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td></td></tr><tr><td><mark style="color:red;">timestamp</mark></td><td><mark style="color:blue;">number</mark></td><td>时间戳记,以毫秒为单位。</td><td></td></tr><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td></td></tr><tr><td><mark style="color:red;">creditRecord</mark></td><td><mark style="color:blue;">array</mark></td><td>渠道数据库的纪录，返回空序列意味着没有记录。</td><td></td></tr><tr><td><mark style="color:red;">status</mark></td><td><mark style="color:blue;">number</mark></td><td><a href="../../ebet-zhuang-tai-ma.md#jian-yi-xiang-ying-de-zhuang-tai-dai-ma">建议返回的状态码</a></td><td></td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

#### creditRecord:

<table><thead><tr><th width="150">参数</th><th width="110">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>querySeqNo</td><td><mark style="color:blue;">string</mark></td><td>要查询的序列号，以逗号分隔。</td><td></td></tr><tr><td>type</td><td><mark style="color:blue;">number</mark></td><td>交易事务类型。</td><td></td></tr><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td></td></tr><tr><td>roundCode</td><td><mark style="color:blue;">string</mark></td><td>牌局号。</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>该seqNo的处理状态，<a href="../../ebet-zhuang-tai-ma.md#jian-yi-xiang-ying-de-zhuang-tai-dai-ma">建议返回的状态码</a></td><td></td></tr><tr><td>creditTime</td><td><mark style="color:blue;">number</mark></td><td>事务纪录处理成功时间(毫秒)。时间格式为Unix。</td><td></td></tr><tr><td>moneyBefore</td><td><mark style="color:blue;">number</mark></td><td>变动前金额。</td><td></td></tr><tr><td>moneyAfter</td><td><mark style="color:blue;">number</mark></td><td>变动后金额。</td><td></td></tr><tr><td>money</td><td><mark style="color:blue;">number</mark></td><td>变动金额。</td><td></td></tr></tbody></table>

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "seqNo": "cf641b394c2257b8edc0e3e8fefa0086",
    "event": "queryIncreaseCreditRecord",
    "timestamp": 1683740363499,
    "username": "demo",
    "creditRecord": [
        {
            "querySeqNo": "d57c3a0baedce10b428e148698caf468",
            "type": 1,
            "username": "demo",
            "roundCode": "BP1-230510165431",
            "status": 200,
            "creditTime": 1683708894325,
            "moneyBefore": 1234567.89,
            "moneyAfter": 1233567.89,
            "money": 1000
        },
        {
            "querySeqNo": "9865152f1d11b655d73ece4c7611e063",
            "type": 2,
            "username": "demo",
            "roundCode": "BP1-230510165431",
            "status": 200,
            "creditTime": 1683708911260,
            "moneyBefore": 1233567.89,
            "moneyAfter": 1234567.89,
            "money": 1000
        }
    ],
    "status": 200
}
```
{% endcode %}
