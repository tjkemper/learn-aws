# IAM
* Permission is denied by default *(must explicitly give permission)*
  * If two policies contradict each other, then the action is denied
* Lock down an account
  * Add MFA
  * Implement a password policy
  * Restrict access via IP address

## Best Practices
* Do not use AWS root credentials to manage **any** resources (use IAM accounts)
* Assign an individual IAM account to each person who manages AWS resources
* Grant each user the minimum set of permissions
* Rotate IAM credentials regularly
* Set password restrictions
* Always use MFA
* Create access keys only when people **need** them *(for programmatic access)*


## Roles

#### Types
* AWS Service Roles
* Role for Cross-Account Access
  * Access to local resource for a different account
* Role for Identity Provider Access
  * Access to resource from users logging in with Google or Facebook

## [Instance Profile](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2_instance-profiles.html)

## Policy
* JSON format

You can have multiple statements and each statement is comprised of **EPARC**.

```
{
  "Statement":[{
    "Effect":"effect",
    "Principal":"principal",
    "Action":"action",
    "Resource":"arn",
    "Condition":{
      "condition":{
        "key":"value"
      }
    }
  }]
}
```

example

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "s3:ListBucket",
    "Resource": "arn:aws:s3:::example_bucket"
  }
}
```

#### Policy types
* **User policy** - only exist in the context of the user
* **Managed policies** - exist independently of users - created in the policies tab on the IAM page or via the CLI

#### IAM Policy Simulator
* Useful for testing what actions are allowed
