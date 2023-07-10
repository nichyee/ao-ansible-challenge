EC2
=========

This role is to deploy and setup the ec2 instance containing the web server. 

Requirements
------------

This role requires that the user has already provisioned a key pair in AWS that will be used to ssh into the instance.

Role Variables
--------------

| Name | Description |
|------|-------------|
| ec2_name | Name to be provided to the ec2 instance |
| aws_region | The name of the AWS region to deploy resources | 
| ec2_key_name | Name of the created key used to ssh into instance |
| ec2_instance_type | Size / type of instance to deploy web app on | 
| ec2_security_group | Either the name or ID of security group that will be assigned to the instance |
| ec2_subnet_id | ID of the subnet to deploy the ec2 into |
| ec2_ami_id | The AMI ID used to deploy the instance | 
| raw_url | URL to the raw HTML of the single page web app | 


Example Use
----------------
```yaml
- name: Launch ec2
  ansible.builtin.include_role:
    name: ec2
    tasks_from: create_ec2_task.yml
  vars:
    ec2_instance_type: "{{ item.instance_type }}"
    ec2_security_group: "{{ vpc_sg.group_id }}"
    ec2_subnet_id: "{{ aza_apse2.subnet.id }}"
    ec2_ami_id: "{{ ami_id }}"
    ec2_name: "{{ item.name }}"
    ec2_key_name: "{{ key_pair_name }}"
  with_items: "{{ ec2_instances }}"
```