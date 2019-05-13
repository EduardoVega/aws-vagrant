# AWS Instance with Vagrant

This document will describe the process to create an AWS Instance using the Vagrant tool

## Requirements

1. AWS Account
2. AWS Role with the minimal set of permissions to use Vagrant ([Packer minimal permissions](https://www.packer.io/docs/builders/amazon.html#iam-task-or-instance-role))
    - Copy this JSON file and create a new AWS Role
  ```json
  {
  "Version": "2012-10-17",
  "Statement": [{
      "Effect": "Allow",
      "Action" : [
        "ec2:AttachVolume",
        "ec2:AuthorizeSecurityGroupIngress",
        "ec2:CopyImage",
        "ec2:CreateImage",
        "ec2:CreateKeypair",
        "ec2:CreateSecurityGroup",
        "ec2:CreateSnapshot",
        "ec2:CreateTags",
        "ec2:CreateVolume",
        "ec2:DeleteKeyPair",
        "ec2:DeleteSecurityGroup",
        "ec2:DeleteSnapshot",
        "ec2:DeleteVolume",
        "ec2:DeregisterImage",
        "ec2:DescribeImageAttribute",
        "ec2:DescribeImages",
        "ec2:DescribeInstances",
        "ec2:DescribeInstanceStatus",
        "ec2:DescribeRegions",
        "ec2:DescribeSecurityGroups",
        "ec2:DescribeSnapshots",
        "ec2:DescribeSubnets",
        "ec2:DescribeTags",
        "ec2:DescribeVolumes",
        "ec2:DetachVolume",
        "ec2:GetPasswordData",
        "ec2:ModifyImageAttribute",
        "ec2:ModifyInstanceAttribute",
        "ec2:ModifySnapshotAttribute",
        "ec2:RegisterImage",
        "ec2:RunInstances",
        "ec2:StopInstances",
        "ec2:TerminateInstances",
        "ec2:RequestSpotInstances",
        "ec2:CancelSpotInstanceRequests",
        "ec2:DescribeSpotInstanceRequests",
        "ec2:DescribeSpotPriceHistory"
      ],
      "Resource" : "*"
  }]
}
```
3. AWS User with programmatic access. Assign the AWS Role created above
4. AWS Subnet with the **auto-assign public IPv4 address** setting enabled
5. Vagrant binary
    - [Download Vagrant](https://www.vagrantup.com/downloads.html)
6. Install [Vagrant AWS plugin](https://github.com/mitchellh/vagrant-aws)
```bash
vagrant plugin install vagrant-aws
```
7. AWS Vagrant Github repository
``` bash
git clone https://github.com/EduardoVega/aws-vagrant.git
```

## Execution
1. Export Variables
```bash
export INSTANCE_NAME=''
export AMI_ID=''
export SECURITY_GROUP=''
export SUBNET_ID=''
export ACCESS_KEY='' 
export SECRET_KEY=''
export PRIVATE_KEY=''
export PRIVATE_KEY_NAME=''
```
2. Create AWS Instance using Vagrant
```bash
# Navigate to the aws-vagrant github repo
cd aws-vagrant

# Run vagrant
vagrant up

```
3. Destroy AWS Instance using Vagrant
```bash
# Navigate to the aws-vagrant github repo
cd aws-vagrant

# Run vagrant
vagrant destroy
```
4. For more information, check vagrant aws plugin repo
    - [Vagrant AWS plugin](https://github.com/mitchellh/vagrant-aws)


