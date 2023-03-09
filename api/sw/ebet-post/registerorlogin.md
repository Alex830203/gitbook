---
description: >-
  此api用于验证用户登录。 发送请求至接收地址是渠道的服务器url + api。  E.g.
  http://127.0.0.1/registerOrLogin
---

# ​registerOrLogin



## <mark style="color:green;">POST</mark>

### **Request**

#### Headers:

Content-Type: application/json

#### Body:

<table><thead><tr><th>参数</th><th>格式</th><th>描述</th><th data-hidden>范例</th></tr></thead><tbody><tr><td>username</td><td><mark style="color:blue;">string</mark></td><td>用户名。不可使用http保留字元。</td><td>RegisterOrLoginReq</td></tr><tr><td>password</td><td><mark style="color:blue;">string</mark></td><td>用户密码。 空字符串為沒有密码。</td><td></td></tr><tr><td>channelId</td><td><mark style="color:blue;">int</mark></td><td>渠道 ID</td><td>1</td></tr><tr><td>currency</td><td><mark style="color:blue;">string</mark></td><td>货币</td><td></td></tr><tr><td>ip</td><td><mark style="color:blue;">string</mark></td><td>用户登录IP</td><td>127.0.0.1</td></tr><tr><td>eventType</td><td><mark style="color:blue;">int</mark></td><td><p>登录方式:</p><p>1:普通登录</p><p>3:Applink登录</p><p>4:Token登录</p></td><td>1</td></tr><tr><td>accessToken</td><td><mark style="color:blue;">string</mark></td><td>该参数值由渠道提供。仅在eventType = 4时使用</td><td>accessToken</td></tr><tr><td>platform</td><td><mark style="color:blue;">integer</mark></td><td>用户的平台</td><td></td></tr><tr><td>password</td><td><mark style="color:blue;">string</mark></td><td>用户密码。 空字符串為沒有密码。</td><td>password</td></tr><tr><td>event</td><td><mark style="color:blue;">string</mark></td><td>API 名称</td><td></td></tr><tr><td>timestamp</td><td><mark style="color:blue;">int($int64)</mark></td><td>当前时间,格式为Unix。</td><td>1577808000</td></tr><tr><td>sessionToken</td><td><mark style="color:blue;">string</mark></td><td>由渠道提供或随机生成</td><td></td></tr><tr><td>seqNo</td><td><mark style="color:blue;">string</mark></td><td>eBET的序列号。 请返回相同的值。</td><td></td></tr><tr><td>signature</td><td><mark style="color:blue;">string</mark></td><td><p>签名。 </p><p>字符串拼接:</p><p>普通登录/applink登录: username+timestamp</p><p>token登录: timestamp+accessToken</p></td><td>bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ==</td></tr></tbody></table>
