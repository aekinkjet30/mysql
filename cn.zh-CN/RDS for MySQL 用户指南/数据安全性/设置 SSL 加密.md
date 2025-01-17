# 设置 SSL 加密 {#concept_ack_rv4_ydb .concept}

为了提高链路安全性，您可以启用SSL（Secure Sockets Layer）加密，并安装SSL CA证书到需要的应用服务。SSL在传输层对网络连接进行加密，能提升通信数据的安全性和完整性，但会同时增加网络连接响应时间。

**说明：** 

-   证书有效期为1年，请在1年内更新证书有效期，否则使用加密连接的客户端程序将无法正确连接
-   由于SSL加密的固有缺陷，启用SSL加密会显著增加CPU使用率，建议您仅在外网链路有加密需求的时候启用SSL加密。内网链路相对较安全，一般无需对链路加密。
-   开启SSL加密后，将无法再关闭，请谨慎操作。
-   读写分离地址不支持SSL加密。
-   仅以下版本实例支持SSL加密：
    -   MySQL 8.0 高可用本地盘版
    -   MySQL 5.7 高可用本地盘版
    -   MySQL 5.6 金融版
    -   MySQL 5.6 高可用版

## 开启SSL加密 {#section_hjf_z54_ydb .section}

1.  登录 [RDS 管理控制台](https://rds.console.aliyun.com/)。
2.  在页面左上角，选择实例所在地域。

    ![选择地域](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7814/155851851436543_zh-CN.png)

3.  找到目标实例，单击实例ID。
4.  在左侧菜单栏中单击**数据安全性**。
5.  选择**SSL**标签页。
6.  单击**未开通**前面的开关，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7949/15585185144147_zh-CN.png)

7.  在设置 SSL对话框中选择要开通SSL加密的链路，单击**确定**，开通 SSL 加密。

    **说明：** 用户可以根据需要，选择加密内网链路或者外网链路，但只可以加密一条链路。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7949/15585185144148_zh-CN.png)

8.  单击**下载证书**，下载SSL CA证书，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7949/15585185144149_zh-CN.png)

    下载的文件为压缩包，包含如下三个文件：

    -   p7b文件：用于Windows系统中导入CA证书。

    -   PEM文件：用于其他系统或应用中导入CA证书。

    -   JKS文件：java中的truststore证书存储文件，密码统一为apsaradb，用于Java程序中导入CA证书链。

        **说明：** 在java中使用JKS证书文件时，jdk7和jdk8需要修改默认的jdk安全配置，在需要SSL访问的数据库所在机器的`jre/lib/security/java.security`文件中，修改如下两项配置：

        ```
        jdk.tls.disabledAlgorithms=SSLv3, RC4, DH keySize < 224
        jdk.certpath.disabledAlgorithms=MD2, RSA keySize < 1024
        ```

        若不修改jdk安全配置，会报如下错误。其它类似报错，一般也都由Java安全配置导致。

        ```
        javax.net.ssl.SSLHandshakeException: DHPublicKey does not comply to algorithm constraints
        ```


## 配置SSL CA证书 {#section_mdn_nv4_ydb .section}

开通SSL加密后，应用或者客户端连接RDS时需要配置SSL CA证书。本文以MySQL Workbench为例，介绍SSL CA证书安装方法。其它应用或者客户端请参见对应产品的使用说明。

1.  打开MySQL Workbench。
2.  选择**Database** \> **Manage Connections** 。
3.  启用**Use SSL**，并导入SSL CA证书，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7949/15585185144150_zh-CN.png)


## 更新证书有效期 {#section_42v_8li_qjg .section}

SSL的证书有效期为1年，请在1年内更新证书有效期，否则使用加密连接的客户端程序将无法正常连接。

**说明：** **更新有效期**操作将会重启实例，重启前请做好业务安排，谨慎操作。

![更新证书有效期](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7949/155851851445367_zh-CN.png)

