# AllocatePublicIpAddress

You can call this operation to assign a public IP address to an ECS instance.

## Description

When you call this operation, take note of the following items:

-   The instance must be in the **Running** \(`Running`\) or **Stopped** \(`Stopped`\) state.
-   If `OperationLocks` in the DescribeInstances response contains `"LockReason" : "security"` for an instance, the instance is locked for security reasons and cannot be assigned public IP addresses through calls to this operation. For more information, see [API behavior when an instance is locked for security reasons](~~25695~~).
-   You can assign only one public IP address to an instance. If the instance already has a public IP address, the `AllocatedAlready` error message is returned.
-   After you assign a new public IP address to an instance, restart the instance \([RebootInstance](~~25502~~)\) or start the instance \([StartInstance](~~25500~~)\) for the public IP address to take effect.

In addition to assigning a public IP address, you can also associate an elastic IP address \(EIP\) with the instance. For more information, see [AssociateEipAddress](~~36017~~).

**Note:** No public IP addresses can be assigned to a VPC-type instance associated with an EIP.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=AllocatePublicIpAddress&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|AllocatePublicIpAddress|The operation that you want to perform. If you use a custom HTTP URL or HTTPS URL to make an API request, you must specify this parameter. Set the value to AllocatePublicIpAddress. |
|InstanceId|String|Yes|i-bp1gtjxuuvwj17zr\*\*\*\*|The ID of the instance to which to assign a public IP address. |
|IpAddress|String|No|112.124.\*\*. \*\*|The public IP address to assign to the instance.

By default, the public IP address is randomly assigned by the system. |
|VlanId|String|No|100|The ID of the VLAN. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|IpAddress|String|112.124.\*\*. \*\*|The public IP address of the instance. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=AllocatePublicIpAddress
&InstanceId=i-bp1gtjxuuvwj17zr****
&IpAddress=112.124. **. **
&<Common request parameters>
```

Sample success responses

`XML` format

```
<AllocatePublicIpAddressResponse>
      <RequestId>F2EF6A3B-E345-46B9-931E-0EA094818567</RequestId>
      <IpAddress>112.124. **. **</IpAddress>
</AllocatePublicIpAddressResponse>
```

`JSON` format

```
{
    "RequestId": "F2EF6A3B-E345-46B9-931E-0EA094818567",
    "IpAddress": "112.124. **. **"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|The error message returned because the specified InstanceId parameter does not exist.|
|400|InvalidIpAddress.Malformed|The specified parameter "IpAddress" is not valid.|The error message returned because the specified IpAddress parameter is invalid.|
|404|InvalidVlanId.NotFound|The VlanId provided does not exist in our records.|The error message returned because the specified VlanId parameter does not exist.|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|The error message returned because the operation is not supported while the resource is in the current state.|
|403|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|The error message returned because the operation is not supported while the instance is locked for security reasons.|
|403|InstanceExpiredOrInArrears|The specified operation is denied as your prepay instance is expired \(prepay mode\) or in arrears \(afterpay mode\).|The error message returned because the subscription instance has expired. Renew the instance and try again.|
|404|InvalidIpAddress.NotFound|The specified IP is not in the specified vlan.|The error message returned because the specified IP address is not in the specified VLAN.|
|403|IpInUse|The specified IP is already in use.|The error message returned because the specified IP address is already in use.|
|403|AllocatedAlready|There is an IpAddress allocated already for the specified instance.|The error message returned because the instance is assigned another IP address.|
|400|OperationDenied|Specified operation is denied as your instance is in VPC.|The error message returned because the operation is not applicable to VPC-type instances.|
|400|InsufficientPublicIp|Ip address not found|The error message returned because the specified IP address does not exist.|
|400|AllocateIpInvalidInstanceBandwidth|OperationDenied The InternetMaxBandwidthOut of the specified instance cannot be less than 0.|The error message returned because the InternetMaxBandwidthOut parameter is set to a value of smaller than 0.|
|400|OperationDenied|The specified parameter "VlanId" is not valid or vlan has not enough IP address.|The error message returned because the specified VlanId parameter is invalid or the maximum number of IP addresses in the VLAN has been reached.|
|403|NAT\_PUBLIC\_IP\_BINDING\_FAILED|Binding nat public ip failed|The error message returned because the public IP address failed to be bound to the gateway.|
|403|NAT\_PUBLIC\_IP\_ALLOCATE\_FAILED|Nat public ip binding failed.|The error message returned because the public IP address failed to be assigned.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

