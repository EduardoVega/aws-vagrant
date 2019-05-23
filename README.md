# Create a VM Instance with Vagrant

This repository contains a Vagrant template to create a VM instance using Vagrant CLI

## Supported Providers

- Amazon Web Services
- Google Cloud Platform

## Prerequisites

### General

1. Vagrant binary
    - [Download Vagrant](https://www.vagrantup.com/downloads.html)
2. Install Provider Plugin
    - [Vagrant AWS plugin](https://github.com/mitchellh/vagrant-aws)
    - [Vagrant Google plugin](https://github.com/mitchellh/vagrant-google)
    ```bash
    vagrant plugin install vagrant-aws
    vagrant plugin install vagrant-google
    ```
3. Clone Vagrant Github repository
    ``` bash
    git clone https://github.com/EduardoVega/centos-7-nginx-vagrant.git
    ```

### Amazon Web Services

1. AWS Account
2. AWS Role with the minimal set of permissions to use Packer ([Packer minimal permissions](https://www.packer.io/docs/builders/amazon.html#iam-task-or-instance-role))
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

### Google Cloud Platform

1. GCP Account
2. Follow the steps to create a service account with the required permissions to run packer (https://www.packer.io/docs/builders/googlecompute.html#running-without-a-compute-engine-service-account)

## Execution
1. Set and export Environment Variables
    - Amazon Web Services
      ```bash
      bash aws-env-vars.sh
      ```
    - Google Cloud Platform
      ```bash
      bash gcp-env-vars.sh
      ```
2. Create Instance using Vagrant

    Vagrant does not support parallel builds, so you can only create one instance at the time; if you want to create another one using a different provider, you must destroy any existing vm

    - Create
    ```bash
    # Navigate to the centos-7-nginx-vagrant github repo
    cd centos-7-nginx-vagrant

    # Run vagrant for AWS
    vagrant up --provider aws

    # Run vagrant for GCP
    vagrant up --provider google
    ```
    
    - SSH
    ```bash
    # Navigate to the centos-7-nginx-vagrant github repo
    cd centos-7-nginx-vagrant

    # SSH vagrant instance
    vagrant ssh
    ```

    - Destroy
    ```bash
    # Navigate to the centos-7-nginx-vagrant github repo
    cd centos-7-nginx-vagrant

    # Destroy vagrant instance
    vagrant destroy
    ```

    - For more information, check vagrant plugins repo
      - [Vagrant AWS plugin](https://github.com/mitchellh/vagrant-aws)
      - [Vagrant Google plugin](https://github.com/mitchellh/vagrant-google)


