# DescribeDeploymentSetSupportedInstanceTypeFamily

You can call this operation to query instance families that support deployment sets.

## Description

For more information about instance families, see [Instance families](~~25378~~).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeDeploymentSetSupportedInstanceTypeFamily&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description |
|---------|----|--------|-------|------------|
|Action|String|Yes|DescribeDeploymentSetSupportedInstanceTypeFamily|The operation that you want to perform. Set the value to DescribeDeploymentSetSupportedInstanceTypeFamily. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the deployment set. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|InstanceTypeFamilies|String|ecs.i2g, ecs.i1, ecs.i2ne, and ecs.i2gne|The instance families that support deployment sets. |
|RequestId|String|473469C7-AA6F-4DC5-B7DB-A3DC7DE1C52E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeDeploymentSetSupportedInstanceTypeFamily
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeDeploymentSetSupportedInstanceTypeFamilyResponse>
      <RequestId>473469C7-AA6F-4DC5-B7DB-A3DC7DE1C52E</RequestId>
      <InstanceTypeFamilies>ecs.sccgn6ex,ecs.i2g,ecs.i1,ecs.i2ne,ecs.i2gne,ecs.hfc6,ecs.hfg6,ecs.hfr6,ecs.sn1nec,ecs.sn2nec,ecs.se1nec,ecs.c6,ecs.g6,ecs.r6,ecs.scch5s,ecs.sccg5s,ecs.ic5,ecs.c5,ecs.d1,ecs.d1-c14d3,ecs.d1-c8d3,ecs.d1ne,ecs.g5,ecs.hfc5,ecs.hfg5,ecs.i2,ecs.mn4,ecs.n1,ecs.n1.tiny,ecs.n2,ecs.n4,ecs.r5,ecs.se1,ecs.se1ne,ecs.sn1,ecs.sn1ne,ecs.sn2,ecs.sn2ne,ecs.xn4,ecs.s1,ecs.s2,ecs.s3,ecs.t1,ecs.scch5,ecs.ebmg5,ecs.sccg5,ecs.sccgn6,ecs.re6,ecs.d2,ecs.d2s,ecs.d2c,ecs.sccgn6ne-inc,ecs.g5ne</InstanceTypeFamilies>
</DescribeDeploymentSetSupportedInstanceTypeFamilyResponse>
```

`JSON` format

```
{
	"RequestId": "473469C7-AA6F-4DC5-B7DB-A3DC7DE1C52E",
	"InstanceTypeFamilies": "ecs.sccgn6ex,ecs.i2g,ecs.i1,ecs.i2ne,ecs.i2gne,ecs.hfc6,ecs.hfg6,ecs.hfr6,ecs.sn1nec,ecs.sn2nec,ecs.se1nec,ecs.c6,ecs.g6,ecs.r6,ecs.scch5s,ecs.sccg5s,ecs.ic5,ecs.c5,ecs.d1,ecs.d1-c14d3,ecs.d1-c8d3,ecs.d1ne,ecs.g5,ecs.hfc5,ecs.hfg5,ecs.i2,ecs.mn4,ecs.n1,ecs.n1.tiny,ecs.n2,ecs.n4,ecs.r5,ecs.se1,ecs.se1ne,ecs.sn1,ecs.sn1ne,ecs.sn2,ecs.sn2ne,ecs.xn4,ecs.s1,ecs.s2,ecs.s3,ecs.t1,ecs.scch5,ecs.ebmg5,ecs.sccg5,ecs.sccgn6,ecs.re6,ecs.d2,ecs.d2s,ecs.d2c,ecs.sccgn6ne-inc,ecs.g5ne"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

