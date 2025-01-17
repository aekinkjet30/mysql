# RDS实例如何变更虚拟交换机VSwitch {#concept_wsc_xxk_lgb .concept}

## 背景 {#section_l2q_2mb_sj0 .section}

实例网络类型为专有网络（VPC），需要变更虚拟交换机。

## 操作步骤 {#section_6qz_ht8_6s9 .section}

-   对于支持从VPC切换到经典网络，以及支持从经典网络切换到VPC的实例：

    1.  将网络模式从VPC切换为经典网络。
    2.  将网络模式从经典网络切换至目的VPC，同时选择目的虚拟交换机。
    **说明：** 切换步骤请参见[切换网络类型](../../../../cn.zh-CN/RDS for MySQL 用户指南/数据库连接/切换网络类型.md#)。

    ![切换switch](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/8398/155860359647821_zh-CN.png)

-   对于不支持网络类型切换的实例：

    购买新的实例（购买时选择目的VPC和目的虚拟交换机），然后将数据迁移到新的实例，具体的迁移步骤请参见如下文档：

    -   [MySQL实例间数据迁移](../../../../cn.zh-CN/RDS for MySQL 用户指南/数据迁移__同步/RDS 实例间数据迁移.md#)
    -   [SQL Server实例间数据迁移](https://help.aliyun.com/document_detail/26626.html)
    -   [PostgreSQL实例间数据迁移](../../../../cn.zh-CN/RDS for PostgreSQL 用户指南/数据迁移/RDS 实例间数据迁移.md#)
    -   [PPAS实例间数据迁移](../../../../cn.zh-CN/RDS for PPAS 用户指南/数据迁移/RDS 实例间数据迁移.md#)
    -   [MariaDB实例间数据迁移](../../../../cn.zh-CN/RDS for MariaDB TX 用户指南/数据迁移/RDS for MariaDB实例间数据迁移.md#)

