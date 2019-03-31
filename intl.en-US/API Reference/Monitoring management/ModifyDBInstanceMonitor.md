# ModifyDBInstanceMonitor {#reference_zpl_gzl_12b .reference}

 **Before using this API, ensure that you have fully understood the [billing methods](../../../../../intl.en-US/Purchase Guide/Billing items and billing methods.md) and [pricing](https://www.alibabacloud.com/product/apsaradb-for-rds-mysql/pricing) of RDS.** 

This API is used to set the monitoring frequency of your RDS instance.

**Note:** Second-level monitoring incurs additional costs.

## Debug {#apiExplorer .section}

Click [here](https://api.aliyun.com/?spm=a2c63.p38356.879954.8.14b919eclNB5Cx#/?product=Rds&api=ModifyDBInstanceMonitor) to perform a debug operation in OpenAPI Explorer and automatically generate an SDK code example.

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example value|Description|
|---------|----|--------|-------------|-----------|
|Action|String|Yes|ModifyDBInstanceMonitor| Action to perform. Value: **ModifyDBInstanceMonitor**.

 |
|DBInstanceId|String|Yes|rm-uf6wjk5xxxxxxx| Instance ID.

 |
|Period|String|Yes|60| Data collection frequency. Value:

 -   **5**
-   **60**
-   **300**

 Unit: second

 To view the data collection frequencies supported by different instances, see [Set monitoring frequency](../../../../../intl.en-US/User Guide/Monitoring and Alarming/Set the monitoring frequency.md).

 |
|AccessKeyId|String|No|LTAIfCxxxxxxx| Used to access Alibaba Cloud services.

 |
|ClientToken|String|No|ETnLKlblzczshOTUbOCzxxxxxxx| Guarantee the idempotence of the request. The value is generated by a client. It must be unique among all requests and can contain a maximum of 64 ASCII characters.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://rds.aliyuncs.com/?Action=ModifyDBInstanceMonitor
&DBInstanceId=rm-uf6wjk5xxxxxxx
&Period=60
&<Common request parameters>

```

Normal response example

`XML` format

``` {#xml_return_success_demo}
<ModifyDBInstanceMonitorResponse>
  <requestId>52B9805C-432C-4ED1-83FD-2F916B6D2733</requestId>
</ModifyDBInstanceMonitorResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"requestId":"52B9805C-432C-4ED1-83FD-2F916B6D2733"
}
```

## Error codes {#section_nnn_bt5_ghb .section}

[Click here to view error codes.](https://error-center.alibabacloud.com/status/product/Rds)
