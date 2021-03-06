# ModifyMountTargetSecurityGroups<a name="API_ModifyMountTargetSecurityGroups"></a>

Modifies the set of security groups in effect for a mount target\.

When you create a mount target, Amazon EFS also creates a new network interface\. For more information, see [CreateMountTarget](API_CreateMountTarget.md)\. This operation replaces the security groups in effect for the network interface associated with a mount target, with the `SecurityGroups` provided in the request\. This operation requires that the network interface of the mount target has been created and the lifecycle state of the mount target is not `deleted`\. 

The operation requires permissions for the following actions:

+  `elasticfilesystem:ModifyMountTargetSecurityGroups` action on the mount target's file system\. 

+  `ec2:ModifyNetworkInterfaceAttribute` action on the mount target's network interface\. 

## Request Syntax<a name="API_ModifyMountTargetSecurityGroups_RequestSyntax"></a>

```
PUT /2015-02-01/mount-targets/MountTargetId/security-groups HTTP/1.1
Content-type: application/json

{
   "SecurityGroups": [ "string" ]
}
```

## URI Request Parameters<a name="API_ModifyMountTargetSecurityGroups_RequestParameters"></a>

The request requires the following URI parameters\.

 ** MountTargetId **   
ID of the mount target whose security groups you want to modify\.

## Request Body<a name="API_ModifyMountTargetSecurityGroups_RequestBody"></a>

The request accepts the following data in JSON format\.

 ** SecurityGroups **   
Array of up to five VPC security group IDs\.  
Type: Array of strings  
Array Members: Maximum number of 5 items\.  
Required: No

## Response Syntax<a name="API_ModifyMountTargetSecurityGroups_ResponseSyntax"></a>

```
HTTP/1.1 204
```

## Response Elements<a name="API_ModifyMountTargetSecurityGroups_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 204 response with an empty HTTP body\.

## Errors<a name="API_ModifyMountTargetSecurityGroups_Errors"></a>

 **BadRequest**   
Returned if the request is malformed or contains an error such as an invalid parameter value or a missing required parameter\.  
HTTP Status Code: 400

 **IncorrectMountTargetState**   
Returned if the mount target is not in the correct state for the operation\.  
HTTP Status Code: 409

 **InternalServerError**   
Returned if an error occurred on the server side\.  
HTTP Status Code: 500

 **MountTargetNotFound**   
Returned if there is no mount target with the specified ID found in the caller's account\.  
HTTP Status Code: 404

 **SecurityGroupLimitExceeded**   
Returned if the size of `SecurityGroups` specified in the request is greater than five\.  
HTTP Status Code: 400

 **SecurityGroupNotFound**   
Returned if one of the specified security groups does not exist in the subnet's VPC\.  
HTTP Status Code: 400

## Example<a name="API_ModifyMountTargetSecurityGroups_Examples"></a>

### Replace a mount target's security groups<a name="API_ModifyMountTargetSecurityGroups_Example_1"></a>

 The following example replaces security groups in effect for the network interface associated with a mount target\. 

#### Sample Request<a name="API_ModifyMountTargetSecurityGroups_Example_1_Request"></a>

```
PUT /2015-02-01/mount-targets/fsmt-9a13661e/security-groups HTTP/1.1
Host: elasticfilesystem.us-west-2.amazonaws.com
x-amz-date: 20140620T223446Z
Authorization: <...>
Content-Type: application/json
Content-Length: 57

{
"SecurityGroups" : [
"sg-188d9f74"
]
}
```

#### Sample Response<a name="API_ModifyMountTargetSecurityGroups_Example_1_Response"></a>

```
HTTP/1.1 204 No Content
x-amzn-RequestId: 088fb0b4-0c1d-4af7-9de1-933207fbdb46
```

## See Also<a name="API_ModifyMountTargetSecurityGroups_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS Command Line Interface](http://docs.aws.amazon.com/goto/aws-cli/elasticfilesystem-2015-02-01/ModifyMountTargetSecurityGroups) 

+  [AWS SDK for \.NET](http://docs.aws.amazon.com/goto/DotNetSDKV3/elasticfilesystem-2015-02-01/ModifyMountTargetSecurityGroups) 

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/elasticfilesystem-2015-02-01/ModifyMountTargetSecurityGroups) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/elasticfilesystem-2015-02-01/ModifyMountTargetSecurityGroups) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/elasticfilesystem-2015-02-01/ModifyMountTargetSecurityGroups) 

+  [AWS SDK for JavaScript](http://docs.aws.amazon.com/goto/AWSJavaScriptSDK/elasticfilesystem-2015-02-01/ModifyMountTargetSecurityGroups) 

+  [AWS SDK for PHP V3](http://docs.aws.amazon.com/goto/SdkForPHPV3/elasticfilesystem-2015-02-01/ModifyMountTargetSecurityGroups) 

+  [AWS SDK for Python](http://docs.aws.amazon.com/goto/boto3/elasticfilesystem-2015-02-01/ModifyMountTargetSecurityGroups) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/elasticfilesystem-2015-02-01/ModifyMountTargetSecurityGroups) 