# Terraform Backend AWS Setup

[![Launch Stack][launch-stack-image]][launch-stack-link]

[launch-stack-image]: https://github.com/YounosN/AWS-CloudFormation-TerraformStateBackend/blob/main/launch-stack.svg
[launch-stack-link]: https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=minimalist-terraform-backend&templateURL=https://younosn.s3.us-west-2.amazonaws.com/cloudformation-templates/minimalist-terraform-backend/terraform-state-backend.template

## Overview
This project contains a CloudFormation template for setting up an S3 bucket and a DynamoDB table to be used as a Terraform backend for state storage and state locking.

**_Note: This is a minimalist version of the setup. For production environments, consider adding additional features such as KMS encryption, more complex IAM roles, and detailed logging._**

## Template Details
The `cloudformation-template.template` file creates the following resources:
- S3 Bucket for Terraform state files.
- DynamoDB table for state locking.

## Usage
1. Clone this repository.
2. Navigate to the cloned directory.
3. Deploy the template using AWS CLI or AWS Management Console.

## Parameters
- `ResourceName`: Name for the S3 bucket and DynamoDB table. Defaults to AWS account ID.
- `OldVersionExpiryDays`: Specifies when noncurrent object versions expire. Upon expiration, Amazon S3 permanently deletes the noncurrent object versions.
- `NumberOfVersionsToRetain`: Specifies how many newest noncurrent versions Amazon S3 will retain anyway - even after expiration day.

## Outputs
- `DynamoDBTableName`: Name of the DynamoDB table used for Terraform state locking.
- `S3BucketName`: Name of the S3 bucket used for Terraform state storage.
- `AWSRegion`: AWS region where resources are created.

## Production Enhancements
**_Important:_** While this template is suitable for basic use, consider the following enhancements for a robust production setup:
- **KMS Encryption**: Implement AWS KMS for enhanced encryption of state files.
- **Advanced IAM Roles**: Create more sophisticated IAM roles and policies for granular access control.
- **Logging and Monitoring**: Integrate CloudTrail and CloudWatch for comprehensive logging and monitoring.
- **Backup and Disaster Recovery**: Implement strategies for backup and disaster recovery to protect Terraform state files.

## Contributing
Feel free to contribute to this project by submitting issues and/or pull requests.

## License
This project is licensed under the MIT License - see the LICENSE file for details.
