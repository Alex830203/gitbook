---
description: 此api用于验证用户登录。 将请求直接发送到渠道提供的服务器URL。
---

# /RegisterOrLoginReq (验证用户登录)

## **Request**

#### Headers:

Content-Type: application/json

#### Body:

| 参数          | 格式              | 描述                                                                                                     | 范例                                                                                       |
| ----------- | --------------- | ------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------- |
| cmd         | string          | API 名称                                                                                                 | RegisterOrLoginReq                                                                       |
| eventType   | int             | <p>登录方式:</p><p>1:普通登录</p><p>3:Applink登录</p><p>4:Token登录</p>                                            | 1                                                                                        |
| channelId   | int             | 渠道 ID                                                                                                  | 1                                                                                        |
| username    | string          | 用户名。不可使用http保留字元。                                                                                      | apitest01                                                                                |
| password    | string          | 用户密码。 空字符串為沒有密码。                                                                                       | password                                                                                 |
| accessToken | string          | 该参数值由渠道提供。仅在eventType = 4时使用                                                                           | accessToken                                                                              |
| timestamp   | integer($int64) | 当前时间,格式为Unix。                                                                                          | 1577808000                                                                               |
| ip          | string          | 用户登录IP                                                                                                 | 127.0.0.1                                                                                |
| signature   | string          | <p>签名。 </p><p>字符串拼接:</p><p>普通登录/applink登录: username+timestamp</p><p>token登录: timestamp+accessToken</p> | bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ== |

{% code overflow="wrap" %}
```json
{
  "cmd": "RegisterOrLoginReq",
  "eventType": 1,
  "channelId": 1,
  "username": "apitest01",
  "password": "password",
  "accessToken": "accessToken",
  "timestamp": 1577808000,
  "ip": "127.0.0.1",
  "signature": "bCP+wYe8TxN3UIHeNPxEv7czYkXueoe1pKSB6IaUDfoR4mtFYcJl3rNFk8Uz84XAHfeD3mNE+p4gECOVw2JxxQ=="
}
```
{% endcode %}

## **Responses**

#### Headers:

Content-Type: application/json

#### Body:

| 参数             | 格式     | 描述                  | 范例              |
| -------------- | ------ | ------------------- | --------------- |
| accessToken\*  | string | 渠道返回的AccessToken。   | accessTokenTest |
| subChannelId\* | int    | 子渠道 ID。 如果未创建，请输入0。 | 0               |
| username\*     | string | 用户名。不可使用http保留字元。   | apitest01       |
| status\*       | int    | 建议返回的状态码            | 200             |
| nickname       | string | 用户昵称                | 预设随机生成          |
| currency       | string | 货币                  | CNY             |

{% code overflow="wrap" %}
```json
{
  "accessToken": "accessTokenTest",
  "subChannelId": 0,
  "username": "apitest01",
  "status": 200,
  "nickname": "用户昵称，预设随机生成",
  "currency": "CNY"
}
```
{% endcode %}
