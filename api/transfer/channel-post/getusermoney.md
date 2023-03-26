---
description: 此api为查询一段时间内有登入的用户金额。
---

# getusermoney

## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td><mark style="color:red;">channelId</mark></td><td><mark style="color:blue;">number</mark></td><td>渠道 ID</td><td>1</td></tr><tr><td><mark style="color:red;">username</mark></td><td><mark style="color:blue;">string</mark></td><td>用户名。 不可使用http保留字元。</td><td></td></tr><tr><td><mark style="color:red;">signature</mark></td><td><mark style="color:blue;">string</mark></td><td>签名。字串拼接：rechargeReqId</td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>subChannelId</td><td><mark style="color:blue;">number</mark></td><td>子渠道ID。</td><td>127.0.0.1</td></tr><tr><td>startTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的开始。</td><td></td></tr><tr><td>endTimeStr</td><td><mark style="color:blue;">string</mark></td><td>查询时间范围的结束。</td><td></td></tr><tr><td>pageNum</td><td><mark style="color:blue;">string</mark></td><td>页码。 默认值为1。</td><td></td></tr><tr><td>pageSize</td><td><mark style="color:blue;">number</mark></td><td>每页上显示的记录数。 默认值为10。最大为5000。</td><td></td></tr><tr><td>minMoney</td><td><mark style="color:blue;">number</mark></td><td>最低金额。低于此金额将不会显示。</td><td></td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币。</td><td></td></tr><tr><td>walletType</td><td><mark style="color:blue;">number</mark></td><td>查询钱包类型</td><td></td></tr></tbody></table>

{% hint style="warning" %}
<mark style="color:red;">标示红色为必要参数。</mark>
{% endhint %}

{% hint style="info" %}
* 由于数据量可能太大，建议带以下参数减少查询时间。 \
  <mark style="color:purple;">`startTimeStr, endTimeStr, pageNum, pageSize`</mark>
{% endhint %}

{% code title="Request" overflow="wrap" %}
```json
{
  "channelId": 1,
  "username": "apitest01",
  "signature": "ZwV0Upcy93v3S/ChPh/K4FtbQ3VfA9bVomRZxBhp7I/nh2P0+qwl+dfax4QZrLwT3TuFIJGv1+nWBb+oTN5bdg==",
  "subChannelId": 0,
  "startTimeStr": "2020-01-01 00:00:00",
  "endTimeStr": "2020-01-02 00:00:00",
  "pageNum": 1,
  "pageSize": 10,
  "minMoney": 10,
  "currency": "CNY",
  "walletType": 0
}
```
{% endcode %}

### **Responses**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>status</td><td><mark style="color:blue;">number</mark></td><td>回应状态。<a href="../../ebet-zhuang-tai-ma.md#ebet-xiang-ying-de-zhuang-tai-dai-ma">状态码表</a></td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr><tr><td>apiVersion</td><td><mark style="color:blue;">string</mark></td><td>API版本号。</td><td></td></tr><tr><td>results</td><td><mark style="color:blue;">array</mark></td><td>记录.阵列值为物件，下表为物件参数说明。</td><td></td></tr></tbody></table>

#### results:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。 不可使用http保留字元。</td><td></td></tr><tr><td>money</td><td><mark style="color:blue;">number</mark></td><td>用户的金額</td><td></td></tr><tr><td>wallet</td><td><mark style="color:blue;">array</mark></td><td>每个钱包的余额。</td><td></td></tr></tbody></table>

#### wallet:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>typeId</td><td><mark style="color:blue;">number</mark></td><td>钱包类型。默认值为0。</td><td></td></tr><tr><td>money</td><td><mark style="color:blue;">number</mark></td><td>该钱包类型余额。</td><td></td></tr></tbody></table>

{% embed url="https://docs.google.com/spreadsheets/d/1ejxETVOI9kcCAP5eNpT6CIi4ftGHwcYWMHJTEPqLILs" %}

{% code title="Responses" overflow="wrap" %}
```json
{
  "results": [
    {
      "username": "apitest01",
      "money": 543.21,
      "wallet": [
        {
          "typeId": 0,
          "money": 543.21
        }
      ]
    }
  ],
  "status": 200,
  "apiVersion": "1.5.90"
}
```
{% endcode %}
