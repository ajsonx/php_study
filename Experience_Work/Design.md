# 一些设计思想的记录

## SSO
* 现况
1.已有SSO
2.当前系统登陆接口
3.前后端分离

* 问题描述
1.SSO系统接口不直接返回用户信息，重定向一个url并返回一个token。token相当于sessionId，根据token获取用户信息
	* url只存在于后台系统，不可实现直接重定向到前端界面，这样获取用户信息还要一个接口
2.本机配置前后端不同域名，cookie不可跨域，正式环境同域名

* 设计思路
1.设计一个thirdlogin接口，用于接收post请求。并在sso登陆得到token。再调用sso的接口校验token获取用户信息，此时返回给前端用户数据并跳转界面。

* 登出设计
  token只存在于本地，清除本地的token
* 多种登陆方式如何判断？？

### SSO与OAuth的区别

- SSO是为了解决一个用户在鉴权服务器登陆过一次以后，可以在任何应用中畅通无阻，一次登陆，多系统访问，操作用户是实打实的该应用的官方用户，用户的权限和分域以鉴权服务器的存储为准。
- OAuth2.0解决的是通过令牌获取某个系统的操作权限，因为有clientId的标识，一次登陆只能对该系统生效，第三方应用的操作用户不是鉴权系统的官方用户，授权权限鉴权中心可以做限制。



## RBAC 权限系统

* 



## 高并发下怎么做余额扣减？

>1.高并发，单纯数据库update更新账户余额，数据库的update行锁已经成为瓶颈。
>2.扣减要保证不能扣为负数。
>两个典型的场景
>1.扣费，企业账户送流量或者红包，用户签到领取。目前我了解到的方案就是分多账户降低单账户的压力或者更新改插入异步去计算余额。
>2.充值，打赏给主播，方案类似。



[知乎问答](https://www.zhihu.com/question/61484424) 需要好好理解





## 优惠券系统的设计

### 难点：

* 优惠券系统的核心在于各种券种的管理，发放和使用。

* 可以想象，为了配合不同形式的线上、线下活动，优惠券系统势必有较大的改动，为了降低代码改动的成本，成为了最核心的挑战。 最好是规则与执行相隔离。
* 结合业务还需要做一些业务流程控制（将系统使用人员操作权限分开）



### 生成优惠券

#### 将优惠券的生成与派发分开的原因：

1.批量生成优惠券、批量派发

2.不同功能属于不同权限的人员来操作。（财务-资金、运营-活动）

* 按照模版生成优惠券，需要注意的几点
  * 优惠券面额
  * 优惠规则
  * 时效性



### 优惠规则的设计

* 计算型规则
  * 满减、无门槛减
* 限制型规则
  * 限制某些用户领取（新人券）
  * 限制某个券的发放数量（每日前3000名额）
  * 渠道限制
* 规则之间的互斥



### 优惠券系统

有以下三点：

* 管理：

  券模版的创建、规则设置、关闭

* 派发/领取

  * 在此步骤，限制型规则会发挥作用，是否满足领取条件。

* 使用

  * 在此计算型规则发挥作用。判断是否满足券的使用条件



[参考文章-优惠券业务设计](http://www.woshipm.com/pd/1056437.html)

[思否-构建稳定与可拓展的优惠券系统](https://segmentfault.com/a/1190000005784383)

###  思考

* 大量发券/核销时 使用Redis如何保证缓存不丢失





1.项目分析、业务难点、业务设计、技术难点、技术设计、风险与思考。

需要过硬的基础知识：缓存层、数据库层、代码层、业务交互层面。

