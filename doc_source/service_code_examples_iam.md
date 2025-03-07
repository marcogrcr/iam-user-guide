# Code examples for IAM using AWS SDKs<a name="service_code_examples_iam"></a>

The following code examples show how to use IAM with an AWS software development kit \(SDK\)\. 

*Actions* are code excerpts that show you how to call individual service functions\.

*Scenarios* are code examples that show you how to accomplish a specific task by calling multiple functions within the same service\.

*Cross\-service examples* are sample applications that work across multiple AWS services\.

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.

**Get started**

## Hello IAM<a name="example_iam_Hello_section"></a>

The following code example shows how to get started using AWS Identity and Access Management \(IAM\)\.

------
#### [ Go ]

**SDK for Go V2**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
  

```
package main

import (
	"context"
	"fmt"

	"github.com/aws/aws-sdk-go-v2/aws"
	"github.com/aws/aws-sdk-go-v2/config"
	"github.com/aws/aws-sdk-go-v2/service/iam"
)

// main uses the AWS SDK for Go (v2) to create an AWS Identity and Access Management (IAM)
// client and list up to 10 policies in your account.
// This example uses the default settings specified in your shared credentials
// and config files.
func main() {
	sdkConfig, err := config.LoadDefaultConfig(context.TODO())
	if err != nil {
		fmt.Println("Couldn't load default configuration. Have you set up your AWS account?")
		fmt.Println(err)
		return
	}
	iamClient := iam.NewFromConfig(sdkConfig)
	const maxPols = 10
	fmt.Printf("Let's list up to %v policies for your account.\n", maxPols)
	result, err := iamClient.ListPolicies(context.TODO(), &iam.ListPoliciesInput{
		MaxItems: aws.Int32(maxPols),
	})
	if err != nil {
		fmt.Printf("Couldn't list policies for your account. Here's why: %v\n", err)
		return
	}
	if len(result.Policies) == 0 {
		fmt.Println("You don't have any policies!")
	} else {
		for _, policy := range result.Policies {
			fmt.Printf("\t%v\n", *policy.PolicyName)
		}
	}
}
```
+  For API details, see [ListPolicies](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.ListPolicies) in *AWS SDK for Go API Reference*\. 

------

**Contents**
+ [Actions](service_code_examples_iam_actions.md)
  + [Attach a policy to a role](example_iam_AttachRolePolicy_section.md)
  + [Attach a policy to a user](example_iam_AttachUserPolicy_section.md)
  + [Attach an inline policy to a role](example_iam_PutRolePolicy_section.md)
  + [Create a policy](example_iam_CreatePolicy_section.md)
  + [Create a policy version](example_iam_CreatePolicyVersion_section.md)
  + [Create a role](example_iam_CreateRole_section.md)
  + [Create a service\-linked role](example_iam_CreateServiceLinkedRole_section.md)
  + [Create a user](example_iam_CreateUser_section.md)
  + [Create an access key](example_iam_CreateAccessKey_section.md)
  + [Create an alias for an account](example_iam_CreateAccountAlias_section.md)
  + [Create an inline policy for a user](example_iam_PutUserPolicy_section.md)
  + [Delete a policy](example_iam_DeletePolicy_section.md)
  + [Delete a role](example_iam_DeleteRole_section.md)
  + [Delete a role policy](example_iam_DeleteRolePolicy_section.md)
  + [Delete a server certificate](example_iam_DeleteServerCertificate_section.md)
  + [Delete a service\-linked role](example_iam_DeleteServiceLinkedRole_section.md)
  + [Delete a user](example_iam_DeleteUser_section.md)
  + [Delete an access key](example_iam_DeleteAccessKey_section.md)
  + [Delete an account alias](example_iam_DeleteAccountAlias_section.md)
  + [Delete an inline policy from a user](example_iam_DeleteUserPolicy_section.md)
  + [Detach a policy from a role](example_iam_DetachRolePolicy_section.md)
  + [Detach a policy from a user](example_iam_DetachUserPolicy_section.md)
  + [Generate a credential report](example_iam_GenerateCredentialReport_section.md)
  + [Get a credential report](example_iam_GetCredentialReport_section.md)
  + [Get a detailed authorization report for your account](example_iam_GetAccountAuthorizationDetails_section.md)
  + [Get a policy](example_iam_GetPolicy_section.md)
  + [Get a policy version](example_iam_GetPolicyVersion_section.md)
  + [Get a role](example_iam_GetRole_section.md)
  + [Get a server certificate](example_iam_GetServerCertificate_section.md)
  + [Get a summary of account usage](example_iam_GetAccountSummary_section.md)
  + [Get a user](example_iam_GetUser_section.md)
  + [Get data about the last use of an access key](example_iam_GetAccessKeyLastUsed_section.md)
  + [Get the account password policy](example_iam_GetAccountPasswordPolicy_section.md)
  + [List SAML providers](example_iam_ListSAMLProviders_section.md)
  + [List a user's access keys](example_iam_ListAccessKeys_section.md)
  + [List account aliases](example_iam_ListAccountAliases_section.md)
  + [List groups](example_iam_ListGroups_section.md)
  + [List inline policies for a role](example_iam_ListRolePolicies_section.md)
  + [List inline policies for a user](example_iam_ListUserPolicies_section.md)
  + [List policies](example_iam_ListPolicies_section.md)
  + [List policies attached to a role](example_iam_ListAttachedRolePolicies_section.md)
  + [List roles](example_iam_ListRoles_section.md)
  + [List server certificates](example_iam_ListServerCertificates_section.md)
  + [List users](example_iam_ListUsers_section.md)
  + [Update a server certificate](example_iam_UpdateServerCertificate_section.md)
  + [Update a user](example_iam_UpdateUser_section.md)
  + [Update an access key](example_iam_UpdateAccessKey_section.md)
+ [Scenarios](service_code_examples_iam_scenarios.md)
  + [Create a user and assume a role](example_iam_Scenario_CreateUserAssumeRole_section.md)
  + [Create read\-only and read\-write users](example_iam_Scenario_UserPolicies_section.md)
  + [Manage access keys](example_iam_Scenario_ManageAccessKeys_section.md)
  + [Manage policies](example_iam_Scenario_PolicyManagement_section.md)
  + [Manage roles](example_iam_Scenario_RoleManagement_section.md)
  + [Manage your account](example_iam_Scenario_AccountManagement_section.md)
  + [Roll back a policy version](example_iam_Scenario_RollbackPolicyVersion_section.md)
+ [Cross\-service examples](service_code_examples_iam_cross-service_examples.md)
  + [Create a long\-lived Amazon EMR cluster and run several steps](example_cross_LongLivedEmrCluster_section.md)
  + [Create a short\-lived Amazon EMR cluster and run a step](example_cross_ShortLivedEmrCluster_section.md)