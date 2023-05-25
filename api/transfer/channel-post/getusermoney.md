---
description: 查询一段时间内有登入的用户额度
---

# getusermoney

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="158">参数</th><th width="94">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道 ID。</td><td>1</td></tr><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。可空值。</td><td></td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。字串拼接：username+timestamp</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">number</mark></td><td>子渠道ID。</td><td>127.0.0.1</td></tr><tr><td>startTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的开始。</td><td></td></tr><tr><td>endTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的结束。</td><td></td></tr><tr><td>pageNum</td><td><mark style="color:blue;">string</mark></td><td>页码。 默认值为1。</td><td></td></tr><tr><td>pageSize</td><td><mark style="color:blue;">number</mark></td><td>每页上显示的记录数。 默认值为10。最大为5000。</td><td></td></tr><tr><td>minMoney</td><td><mark style="color:blue;">number</mark></td><td>最低金额。低于此金额将不会显示。</td><td></td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。参数值定义请参考下表。</td><td></td></tr><tr><td>walletType</td><td><mark style="color:blue;">number</mark></td><td>查询钱包类型</td><td></td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% hint style="info" %}
* <mark style="color:blue;">由于数据量可能太大，建议带以下参数减少查询时间。</mark> \
  <mark style="color:blue;">`startTimeStr, endTimeStr, pageNum, pageSize`</mark>
{% endhint %}

{% code title="Request" overflow="wrap" lineNumbers="true" %}
```json
{
    "channelId": 1,
    "username": "demo",
    "timestamp": 1683684535,
    "pageNum": 1,
    "pageSize": 5000,
    "startTimeStr": "2023-05-10 00:00:00",
    "endTimeStr": "2023-05-11 00:00:00",
    "signature": "BUMhRjDaQcr+4UZfhCKJMMP2ecDBxDDGgcmSk7Cz5XgsDfbAh2h35Ahp6NDs3uu2bYSImw6mBDtvdmUDUDqlfQ=="
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th width="164">参数</th><th width="114">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>results</td><td><mark style="color:blue;">array</mark></td><td>记录。阵列值为物件，下表为物件参数说明。</td><td></td></tr><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td></td></tr></tbody></table>

#### results

<table><thead><tr><th width="164">参数</th><th width="119">格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。预设使用小写和数字。不可使用http保留字元。</td><td></td></tr><tr><td>money</td><td><mark style="color:blue;">number</mark></td><td>用户的金額</td><td></td></tr><tr><td>wallet</td><td><mark style="color:blue;">array</mark></td><td>每个钱包的余额。阵列值为物件，下表为物件参数说明。</td><td></td></tr></tbody></table>

{% embed url="https://docs.google.com/spreadsheets/d/1ejxETVOI9kcCAP5eNpT6CIi4ftGHwcYWMHJTEPqLILs" %}

{% code title="Responses" overflow="wrap" lineNumbers="true" %}
```json
{
    "results": [
        {
            "username": "demo",
            "money": 1234567.89,
            "wallet": [
                {
                    "typeId": 0,
                    "money": 1234567.89
                },
                {
                    "typeId": 1,
                    "money": 0
                },
                {
                    "typeId": 2,
                    "money": 0
                },
                {
                    "typeId": 3,
                    "money": 0
                },
                {
                    "typeId": 4,
                    "money": 0
                },
                {
                    "typeId": 5,
                    "money": 0
                },
                {
                    "typeId": 6,
                    "money": 0
                }
            ]
        }
    ],
    "status": 200,
    "apiVersion": "1.5.97"
}
```
{% endcode %}
