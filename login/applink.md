---
description: 从渠道的App跳转至eBET App
---

# AppLink登入

<figure><img src="../.gitbook/assets/user register.png" alt=""><figcaption><p>用户注册的API操作流程用户注册的API操作流程</p></figcaption></figure>

<figure><img src="../.gitbook/assets/applink login.png" alt=""><figcaption><p>AppLink登入的API操作流程</p></figcaption></figure>

<table data-card-size="large" data-view="cards" data-full-width="false"><thead><tr><th></th><th></th><th></th><th></th><th></th></tr></thead><tbody><tr><td>与流程相关的API页面(转帐钱包)</td><td>launchUrl</td><td>syncuser</td><td>RegisterOrLoginReq</td><td>UserInfo</td></tr><tr><td>与流程相关的API页面(单钱包)</td><td>launchUrl</td><td>syncuser</td><td>registerOrLogin</td><td>syncCredit</td></tr></tbody></table>

{% hint style="danger" %}
<mark style="color:red;">渠道要自行帮用户检查是否有安装过eBET App，才可以使用AppLink登入的功能</mark>
{% endhint %}
