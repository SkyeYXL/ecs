# DescribeDeploymentSets

You can call this operation to query attributes of one or more deployment sets.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeDeploymentSets&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeDeploymentSets|The operation that you want to perform. Set the value to DescribeDeploymentSets. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the deployment set. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|PageNumber|Integer|No|1|The number of the page to return.

Pages start from page 1.

Default value: 1 |
|PageSize|Integer|No|10|The number of entries to return on each page.

Maximum value: 50.

Default value: 10. |
|DeploymentSetIds|String|No|\["ds-bp67acfmxazb4ph\*\*\*\*", "ds-bp67acfmxazb4pi\*\*\*\*", ... "ds-bp67acfmxazb4pj\*\*\*\*"\]|The IDs of deployment sets. The value can be a JSON array that consists of up to 100 deployment set IDs. Separate multiple deployment set IDs with commas \(,\). |
|DeploymentSetName|String|No|testDeploymentSetName|The name of the deployment set. |
|Strategy|String|No|Availability|The deployment strategy. Set the value to Availability.

This parameter is empty by default. |
|NetworkType|String|No|test|The network type of instances in the deployment set.

**Note:** We recommend that you use other parameters to ensure future compatibility. |
|Granularity|String|No|test|The deployment granularity.

**Note:** We recommend that you use other parameters to ensure future compatibility. |
|Domain|String|No|test|The deployment domain.

**Note:** We recommend that you use other parameters to ensure future compatibility. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|DeploymentSets|Array of DeploymentSet| |Details about deployment set information. |
|DeploymentSet| | | |
|CreationTime|String|2017-12-05T22:40:00Z|The time when the deployment set was created. |
|DeploymentSetDescription|String|testDeploymentSetDescription|The description of the deployment set. |
|DeploymentSetId|String|ds-bp67acfmxazb4ph\*\*\*\*|The ID of the deployment set. |
|DeploymentSetName|String|testDeploymentSetName|The name of the deployment set. |
|DeploymentStrategy|String|Availability|The deployment strategy. |
|Domain|String|Default|The deployment domain. |
|Granularity|String|Host|The deployment granularity. |
|GroupCount|Integer|0| |
|InstanceAmount|Integer|1|The number of instances in the deployment set. |
|InstanceIds|List|\["i-bp67acfmxazb4ph\*\*\*\*"\]|The IDs of the instances in the deployment set. |
|Strategy|String|StrictDispersion|The deployment strategy. |
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|10|The number of entries returned per page. |
|RegionId|String|cn-hangzhou|The region ID of the deployment set. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|TotalCount|Integer|1|The total number of queried deployment sets. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeDeploymentSets
&RegionId=cn-hangzhou
&PageSize=1
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeDeploymentSetsResponse>
      <DeploymentSets>
            <DeploymentSet>
                  <CreationTime>Tue Jul 23 17:24:33 CST 2019</CreationTime>
                  <Granularity>switch</Granularity>
                  <DeploymentSetDescription>autogen deploymentset, do not delete</DeploymentSetDescription>
                  <Domain>default</Domain>
                  <InstanceIds>
                        <InstanceId>i-bp67acfmxazb4ph****</InstanceId>
                        <InstanceId>i-bp67acfmxazb4pi****</InstanceId>
                        <InstanceId>i-bp67acfmxazb4pj****</InstanceId>
                  </InstanceIds>
                  <InstanceAmount>0</InstanceAmount>
                  <Strategy>LooseAggregation</Strategy>
                  <DeploymentSetName>hpc-null-deploymentset</DeploymentSetName>
                  <DeploymentStrategy>Availability</DeploymentStrategy>
                  <DeploymentSetId>ds-bp120c8htdzx3869****</DeploymentSetId>
            </DeploymentSet>
      </DeploymentSets>
      <PageNumber>1</PageNumber>
      <TotalCount>5</TotalCount>
      <PageSize>1</PageSize>
      <RegionId>cn-hangzhou</RegionId>
      <RequestId>FB5EF912-FD87-4CF7-91D9-9204974A63F3</RequestId>
</DescribeDeploymentSetsResponse>
```

`JSON` format

```
{
    "DeploymentSets": {
        "DeploymentSet": [
            {
                "CreationTime": "Tue Jul 23 17:24:33 CST 2019",
                "Granularity": "switch",
                "DeploymentSetDescription": "autogen deploymentset, do not delete",
                "Domain": "default",
                "InstanceIds": {
                    "InstanceId": [
                        "i-bp67acfmxazb4ph****",
                        "i-bp67acfmxazb4pi****",
                        "i-bp67acfmxazb4pj****"]
                },
                "InstanceAmount": 0,
                "Strategy": "LooseAggregation",
                "DeploymentSetName": "hpc-null-deploymentset",
                "DeploymentStrategy": "Availability",
                "DeploymentSetId": "ds-bp120c8htdzx3869****"
            }
        ]
    },
    "PageNumber": 1,
    "TotalCount": 5,
    "PageSize": 1,
    "RegionId": "cn-hangzhou",
    "RequestId": "FB5EF912-FD87-4CF7-91D9-9204974A63F3"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|InvalidDeploymentSetIds.TooManyInput|The parameter DeploymentSets size should less than 100.|The error message returned because the number of specified deployment sets exceeds 100.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

