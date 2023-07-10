# ao-ansible-challenge

This repo is used for the AdventOne Ansible Challenge. It contains the necessary playbook and roles needed to deploy a single page web app onto an AWS EC2 instance. 
Upon completion of the the playbook, two Public IPv4 DNS names will be output, and when accessed will display the different apps.

Requirements
------------

This playbook requires the environment variables $AWS_ACCESS_KEY_ID and $AWS_SECRET_ACCESS_KEY set to  appropriate values for your AWS environment. This was done in order to prevent the inclusion of Keys in this repo. 
Ideally, this would take place through a pipeline / container, however, without sufficient information regarding the AdventOne cloud ecosystem, pipelines and secrect managers will not be able to be used.

This playbook requires that the user has already provisioned a key pair in AWS that will be used to ssh into the created instances.

Playbook Variables
--------------

| Name | Description |
|------|-------------|
| common_name | The name to be used for the VPC and as the prefix for other resources |
| aws_region | The name of the AWS region to deploy resources | 
| vpc_cidr | CIDR to be assigned to the VPC | 
| vpc_subnet_a_cidr | Subnet CIDR to be assigned to the A Availability Zone |
| vpc_subnet_b_cidr | Subnet CIDR to be assigned to the B Availability Zone |
| vpc_subnet_c_cidr | Subnet CIDR to be assigned to the C Availability Zone |
| key_pair_name | Name of the created key used to ssh into instance |
| ami_id | The AMI ID used to deploy the instance | 
| ec2_instances | A list of dictionaries that allows the playbook to deploy as many ec2 instances as neccessary | 

