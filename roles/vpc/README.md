VPC
=========

This role deploys a vpc, subnets in each availability zone, an internet gateway, a custom route table and a security group for the use in the AdventOne Ansible Challenge.

Role Variables
--------------

| Name | Description |
|------|-------------|
| common_name | The name to be used for the VPC and as the prefix for other resources |
| vpc_cidr | CIDR to be assigned to the VPC | 
| vpc_subnet_a_cidr | Subnet CIDR to be assigned to the A Availability Zone |
| vpc_subnet_b_cidr | Subnet CIDR to be assigned to the B Availability Zone |
| vpc_subnet_c_cidr | Subnet CIDR to be assigned to the C Availability Zone |


Example Use
----------------
```yaml
- name: Setup VPC
  ansible.builtin.import_role:
    name: vpc
    tasks_from: vpc_task.yml
```