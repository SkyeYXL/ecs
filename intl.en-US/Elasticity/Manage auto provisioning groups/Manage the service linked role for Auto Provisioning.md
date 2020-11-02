# Manage the service linked role for Auto Provisioning

This topic describes how to use the service linked role for Auto Provisioning to grant Auto Provisioning the permissions on Alibaba Cloud resources.

If you are a RAM user, you are granted permissions to use Auto Provisioning so that you can manage the service linked roles for Auto Provisioning. For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Grant permissions to a RAM user.md).

The trusted policy of the service linked role includes the following content:

**Note:** Replace <Account ID\> with the ID of your Alibaba Cloud account.

```
{
    "Statement": [
        {
            "Action": [
                "ram:CreateServiceLinkedRole"
            ],
            "Resource": "acs:ram:*:<account ID>:role/*",
            "Effect": "Allow",
            "Condition": {
                "StringEquals": {
                    "ram:ServiceName": [
                        "autoprovisioning.ecs.aliyuncs.com"
                    ]
                }
            }
        }
    ],
    "Version": "1"
}
```

AliyunServiceRoleForAutoProvisioning is a service linked role provided by Resource Access Management \(RAM\) to Auto Provisioning. Auto Provisioning can use AliyunServiceRoleForAutoProvisioning to obtain the access to Elastic Compute Service \(ECS\), Virtual Private Cloud \(VPC\), ApsaraDB RDS, Server Load Balancer \(SLB\), Operation Orchestration Service \(OOS\), Message Service \(MNS\), and Cloud Monitoring Service \(CMS\). For more information about service linked roles, see [Service linked roles](/intl.en-US/RAM Role Management/Service linked roles.md).

## Create AliyunServiceRoleForAutoProvisioning

When you create an auto provisioning group, the system checks whether your Alibaba Cloud account has the AliyunServiceRoleForAutoProvisioning service linked role. If your account does not have the role, the system prompts you to create the role. After you confirm, the system automatically creates the role. You can also manually create AliyunServiceRoleForAutoProvisioning. For more information, see [Create a service linked role](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted Alibaba Cloud service.md).

The permissions of service linked roles are defined and used by the corresponding cloud services. You cannot add, modify, or delete permissions for service linked roles. You can view role permissions on the role details page. For more information, see [View the basic information of a RAM role](/intl.en-US/RAM Role Management/View the basic information of a RAM role.md).

## Delete AliyunServiceRoleForAutoProvisioning

If you no longer want to use AliyunServiceRoleForAutoProvisioning, such as when you do not want to use an auto provisioning group to create and manage resources or if you want to know how deletion of the role will impact your business, you can delete the role. For more information, see [Delete a RAM role](/intl.en-US/RAM Role Management/Delete a RAM role.md).

**Note:** Before you can delete AliyunServiceRoleForAutoProvisioning, you must delete the auto provisioning groups in all regions in the current account. Otherwise, the deletion will fail.

After AliyunServiceRoleForAutoProvisioning is deleted, you cannot use Auto Provisioning to create or manage resources.

