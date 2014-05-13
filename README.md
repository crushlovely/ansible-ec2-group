EC2 Group
========

Provions one ec2 security group to be used with your instance.  This role is 2 of 3 parts.  Although, the roles can be used individually they were developed to use together for the most effective ec2 provisioning.

######This ec2 role was broken off of the ansible example and tailored for organizational purposes.

```
- name: Create security group with default ports
  ec2_group:
    name: "{{ app_name }}_{{ server_env }}"
    description: Access to the {{ app_name }}_{{ server_env }} servers
    region: "{{ region }}"
    rules:
      - proto: tcp
        from_port: 22
        to_port: 22
        cidr_ip: 0.0.0.0/0
      - proto: tcp
        from_port: 443
        to_port: 443
        cidr_ip: 0.0.0.0/0
      - proto: tcp
        from_port: 80
        to_port: 80
        cidr_ip: 0.0.0.0/0

```

Requirements
-----------
boto

Role Variables
-----------
* app_name
* server_env
* region

Dependencies
-----------
Note: Not dependencies but developed together.
* ec2_provision
* ec2_ami

License
-----------
MIT