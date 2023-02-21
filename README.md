---
description: eBET对接注意事项
---

# 注意事项

## 1. 请求和接收数据

1.请严格遵守eBET使用的 <mark style="color:red;background-color:blue;">参数大小写</mark>，否则会导致获取不正确的数据\
2.eBET是使用 <mark style="color:red;background-color:blue;">JSON(application/json)</mark> 来发送和接收数据的\
3.ebet金额只计算到小数点第二位

## 2. 测试相关

1\. 在正式渠道测试的数据是 <mark style="color:red;background-color:blue;">无法删除</mark> 的。\
2\. 建议使用 <mark style="color:red;background-color:blue;">多個前缀為test</mark> 的账号进行测试，方便渠道自行辨识测试。該账号还是正式玩家账号，如果正式上线，每种账号仍 <mark style="color:red;background-color:blue;">须计算费用</mark> 。\
3\. eBET有提供测试渠道，如果有需要请向客服人员申请。

## 3. 白名單

eBET有3个部分需要提供ip做添加到白名单才允许使用。\
1\. 登入游戏。若要在限制地区测试需要提供ip。\
真人游戏限制地区：<mark style="color:red;background-color:blue;">香港、韩国、澳门、菲律宾、新加坡、台湾、美国</mark>\
Genesis老虎机游戏限制地区：<mark style="color:red;background-color:blue;">安地卡及巴布达、直布罗陀、香港、冰岛、爱尔兰岛、 列支敦斯登、马尔他、模里西斯、纽西兰、罗马尼亚、新加坡、西班牙、瑞典、瑞士、台湾、英国</mark>\
2\. api請求。如果没有设置, 则 <mark style="color:red;background-color:blue;">预设皆为开放</mark>。\
3\. 渠道數據後台登入。只有提供的ip才 <mark style="color:red;background-color:blue;">允許登入</mark>。

**重要事项：**

关于访问 eBET API 安全措施：\
我们这里是需要您们提供当您们调用eBET api的 ip 地址。\
我方添加之后就“ <mark style="color:red;background-color:blue;">只有</mark> ”提供的 ip 地址才可以访问eBET api。\
PS：我方 <mark style="color:red;background-color:blue;">已提醒</mark> 贵方安全措施，后期遇上关于访问 eBET api 特殊 <mark style="color:red;background-color:blue;">状况请自负</mark> 。

## 4. 游戏登入

登入游戏接口支持http以及https，若要 <mark style="color:red;background-color:blue;">使用https 需做申请</mark>。

## 5. 用戶名组成

**組成规则：**

ebet接受的username的内容为 <mark style="color:red;background-color:blue;">小写英文、数字和特定符号</mark>。若使用大写英文会被 <mark style="color:red;background-color:blue;">强制转为小写英文</mark>。

**組成建议：**

1.建议username是由小写英文和数字组成。\
2.建议使用的长度为25字元长度。\
3.不可使用http保留字元，避免出现问题。

## 6. Token组成

此說明適用accessToken和sessionToken。

**組成规则：**

渠道可以自行定义参数值和生命周期。

**組成建议：**

1.建议是由大小写英文和数字组成，不可使用http保留字元。\
2.建议每次使用后更新为新的参数值。\
3.建议固定一组参数值提供给ebet重复测试使用。

## 7. 签名组成

1\. eBET提供的钥匙格式为PEM。若渠道使用C#，请转换成XML。\
2\. 由特定参数值做字串串接，透过RSA加密方式后组成签名字串。\
3\. 若特定参数为非必要参数且请求时没有该参数时，可以略过该参数，例如：由username+timestamp組成的簽名，沒有username時可以只使用timestamp作转换。

## 8. 时间格式字串

eBET server DB纪录的时间为 <mark style="color:red;background-color:blue;">北京时间(EAT)</mark>\
eBET server接受的时间格式字串如下：\
<mark style="color:red;background-color:blue;">yyyy-MM-dd HH:mm:ss ( UTC+8 ) 和yyyy-MM-ddTHH:mm:ssZ ( UTC+0 )</mark>\
e.g.1 要被转化的时间：北京时间2019-08-01 04:00:00 ( UTC+8 )\
转化过后为：2019-07-31T20:00:00Z (UTC+0)\
e.g.2 要被转化的时间：美东时间2019-07-31 12:00:00 ( UTC-5 )\
转化过后为：\
2019-07-31T17:00:00Z (UTC+0)或2019-08-01 01:00:00 ( UTC+8 )

## 9. 子渠道

eBET有提供子渠道/子代理的设置。<mark style="color:red;background-color:blue;">如果没有做任何设置，预设ID为0</mark>。\
\
**子渠道创建**

在eBET后台可以创建给旗下代理使用的子渠道和管理帐户。\
注意1：<mark style="color:red;background-color:blue;">创建后，不可修改名称及删除</mark>。\
注意2：<mark style="color:red;background-color:blue;">因安全性考量，创建后，需重新登入帐号更新子渠道列表</mark>。

**客制化设置**

可以对单一子渠道设置以下项目﹔\
1\. logo跳转连结\
2\. 游戏前端是否阻挡对投下注\
3\. 是否关闭多台\
4\. 是否开启自定义图片\
注意：<mark style="color:red;background-color:blue;">该设置可以在重制后，还原成与主渠道相同设置</mark>。

## 10. 建议配置

<table><thead><tr><th>项目</th><th>建议配置</th><th data-hidden></th><th data-hidden></th></tr></thead><tbody><tr><td>建议网络速度</td><td><p>PC（高清）: > 8Mbps</p><p>PC（标清）: 无标清选项</p><p>H5（高清）: > 5Mbps</p><p>H5（标清）: > 4Mbps</p><p>无画面： &#x3C; 2Mbps</p></td><td></td><td></td></tr><tr><td>建议手机版本</td><td><p>iOS 13以上</p><p>Android 8以上</p></td><td></td><td></td></tr><tr><td>建议浏览器</td><td><p>Chrome</p><p>Safari</p></td><td></td><td></td></tr><tr><td>系统需求</td><td><p>Windows</p><p>-Windows 7、Windows 8、Windows 8.1 或 Windows 10 以上版本</p><p>-Intel Pentium 4 以上版本处理器 (可支持 SSE2)</p><p>-RAM 8G以上</p><p>Mac</p><p>-OS X Yosemite 10.10 以上版本</p><p>Linux</p><p>-64 位 Ubuntu 14.04 以上版本、Debian 8 以上版本、openSUSE 13.3 以上版本或 Fedora Linux 24 以上版本</p><p>-Intel Pentium 4 以上版本处理器 (可支持 SSE2)</p></td><td></td><td></td></tr></tbody></table>

## 11. 备注

您在eBET做任何操作（例如：登入eBET游戏、向eBET发送API请求等），若收到http的错误（例如：403、502、504等），或其他未提及之错误，请向eBET人员寻求协助。
