
## API接口文档

http://doc.52itstyle.com/

## 欢迎关注

![输入图片说明](https://git.oschina.net/uploads/images/2017/0802/192116_4752d44b_87650.jpeg "1801066129 (1).jpg")


以下所有支付Demo，测试通过，真实有效。

### 支付宝
扫码支付、电脑支付、WAP支付、APP支付服务端
### 微信
扫码支付(模式一二)、公众号H5支付、WAP支付
### 银联
电脑支付、WAP支付


[SpringMvc-Dubbox-pay版本](https://git.oschina.net/52itstyle/springMvc-dubbo-pay)

## 开发环境

JDK1.7、Maven、Eclipse、SpringBoot1.5.2、spring-boot-starter-thymeleaf、Dubbox2.8.4、zookeeper3.4.6

## 启动说明
- 项目中RPC框架使用的是当当维护的DubboX，现在阿里已经处于维护状态中，请自行更新
- 配置Dubbo需要安装注册中心zookeeper: http://www.52itstyle.com/thread-19791-1-1.html
- 如果不想使用Dubbo和安装zookeeper，又想启动看下效果，请注释掉 Application 类中的@ImportResource({"classpath:spring-context-dubbo.xml"})，
同时由于接口扫描注解使用的是Dubbo的  com.alibaba.dubbo.config.annotation.Service; 请自行替换成spring的 org.springframework.stereotype.Service;
- 最后想测试相关支付效果，请自行配置支付宝、微信以及银联相关账号以及证书

- 启动并访问项目：http://localhost:8080/springboot_pay

## 支付文档

地址：http://localhost:8080/springboot_pay/swagger-ui.html

配置说明：https://blog.52itstyle.com/archives/1473/

![支付文档](https://git.oschina.net/uploads/images/2017/0828/172331_6537f916_87650.png "zhifuAPI.png")

## 演示界面

部分功能完善中！！！

![模拟登陆](https://git.oschina.net/uploads/images/2017/0802/191105_d59172ca_87650.png "0.png")

![模拟首页](https://git.oschina.net/uploads/images/2017/0802/191116_04d62422_87650.png "1.png")

![模拟支付](https://git.oschina.net/uploads/images/2017/0802/191125_6958b9b3_87650.png "2.png")

![扫码模式一](https://git.oschina.net/uploads/images/2017/0803/184824_420ca96d_87650.png "123.png")



## 支付宝

- 电脑支付：https://docs.open.alipay.com/270
- 扫码支付：https://docs.open.alipay.com/194
- 手机支付：https://docs.open.alipay.com/203
- APP支付 : https://docs.open.alipay.com/54/106370/
- 沙箱环境：https://docs.open.alipay.com/200/105311/
- 参数zfbinfo.properties

```
支付宝网关名、partnerId和appId
open_api_domain = https://openapi.alipay.com/gateway.do
mcloud_api_domain = http://mcloudmonitor.com/gateway.do
此处请填写你的PID
pid =XXXXXXXXXXXXXX
此处请填写你当面付的APPID 
appid =XXXXXXXXXXXXXX

RSA私钥、公钥和支付宝公钥
private_key = XXXXXXXXXXXXXX
public_key = XXXXXXXXXXXXXX
alipay_public_key = XXXXXXXXXXXXXX

当面付最大查询次数和查询间隔（毫秒）
max_query_retry = 5
query_duration = 5000

当面付最大撤销次数和撤销间隔（毫秒）
max_cancel_retry = 3
cancel_duration = 2000

交易保障线程第一次调度延迟和调度间隔（秒）
heartbeat_delay = 5
heartbeat_duration = 900

```

支付宝的SDK-alipay-sdk-java这里下载： https://docs.open.alipay.com/54/103419/

大家比较好奇的alipay-trade-sdk从这里下载的TradePayDemo项目中的额lib下面，不过是16年的，目前来说还是可以使用的： https://docs.open.alipay.com/54/104506/

## 微信

- H5支付：https://pay.weixin.qq.com/wiki/doc/api/H5.php?chapter=15_1
- 公众号支付：https://pay.weixin.qq.com/wiki/doc/api/jsapi.php?chapter=7_1
- 扫码支付模式一：https://pay.weixin.qq.com/wiki/doc/api/native.php?chapter=6_4
- 扫码支付模式二：https://pay.weixin.qq.com/wiki/doc/api/native.php?chapter=6_5
- 微信退款说明：https://pay.weixin.qq.com/wiki/doc/api/native.php?chapter=4_3
- 网络设置指引：https://pay.weixin.qq.com/wiki/doc/api/native.php?chapter=23_2
- HTTPS服务器配置:https://pay.weixin.qq.com/wiki/doc/api/wxa/wxa_api.php?chapter=10_4
- 参数wxinfo.properties
- 微信网页授权部分，向微信申请测试号：http://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1421137522

```
服务号的应用ID
APP_ID = XXXXXXXXXXXXXX
服务号的应用密钥
APP_SECRET = XXXXXXXXXXXXXX
服务号的配置token
TOKEN = XXXXXXXXXXXXXX
商户号
MCH_ID = XXXXXXXXXXXXXX
API密钥
API_KEY = XXXXXXXXXXXXXX
签名加密方式
SIGN_TYPE = MD5
微信支付证书名称
CERT_PATH = apiclient_cert.p12
```

## 银联
- 开放平台：https://open.unionpay.com/ajweb/index
- 商家中心：https://merchant.unionpay.com/join/
- 测试账号：https://blog.52itstyle.com/archives/326/
- 证书问题(QA)：https://open.unionpay.com/ajweb/help/faq/list?id=174&level=0&from=0

## 注意事项
- 除银联支付可以测试以外，支付宝和微信支付测试均需要企业认证，个人无法完成测试
- 项目中的支付宝SDk需要自行去官网下载打入本地仓库或者私服，提供下载地址：http://pan.baidu.com/s/1mi5LfhI
- 微信退款证书，微信商户平台(pay.weixin.qq.com)-->账户中心-->账户设置-->API安全-->证书下载，使用apiclient_cert.p12即可
- 支付宝支付相关参数zfbinfo.properties，需要自行去阅读支付宝文档自行生成
- 微信支付相关参数wxinfo.properties，需要自行去阅读微信支付文档自行生成
- 公众平台微信支付公众号支付授权目录、扫码支付回调URL配置入口已于8月1日迁移至商户平台（pay.weixin.qq.com）。迁移后，原有配置数据不会受影
响，你可在商户平台查看和配置。带来的不便敬请谅解。
- 2018年1月8日更新：公众号开发信息、微信H5支付获取access_token接口时，必须设置IP白名单。

![支付模式一回调](https://git.oschina.net/uploads/images/2017/0803/184711_75c8374c_87650.png "模式一支付.png")
- 微信或者支付宝下单调用网关失败，请检查网络 ping api.mch.weixin.qq.com -c 100 或者 ping openapi.alipay.com/gateway.do -c 100
- 支付宝中的初始化配置Configs 不要随便变更，支付相关JAR调用的是Configs中的配置
- 由于项目配置了SSL，访问地址： https://ip:port/springboot_pay/ 见：[SpringBoot开发案例之集成SSL证书](https://blog.52itstyle.com/archives/1403/)
- 2018/01/26 以后新建应用只支持RSA2签名方式，目前已使用RSA签名方式的应用仍然可以正常调用接口，注意下自己生成密钥的签名算法，见AliPayController类。

## 功能日志
- 支付宝生成支付二维码Demo已经测试完成
- 支付宝手机端H5支付Demo已经测试完成
- 支付宝电脑支付Demo已经测试完成

- 微信二维码支付模式二Demo测试完成
- 微信公众号支付(需要添加认证网址)


- 银联支付电脑支付Demo测试完成
- 银联支付H5支付Demo测试完成

- 微信二维码支付模式一Demo测试完成
- 集成Dubbo服务，全注解提供RPC服务
- 集成logback日志组间
- 集成HTTPS证书安全服务 
- 集成微信H5(WAP)支付

