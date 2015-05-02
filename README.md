# Ansible Role For EC2 Security Group Provisioning

Provions one ec2 security group to be used with your instance/s.  This role provisions goups inside of a EC2 VPC it has not been tested to provision security groups in the EC2 Classic network.

## Installation

``` bash
$ ansible-galaxy install https://github.com/crushlovely/ansible-ec2-group.git,v1.0.0
```
## Variables

You will want to fill all these in before running the role.

``` yaml
aws:
  ec2_access_key: "Amazon IAM access key"
  ec2_secret_key: "Aamazon secret key"
  acct_vpc_id: "EC2 vpc id"
  security:
    region: "us-east-1"
app_name: test
server_env: qa
```
You can also add a vars folder to your project folder and have your variables served by adding them to a file and calling it in your playbook.

```yaml
- hosts: localhost
...
  vars_files:
    - vars/default_vars.yml
...
```
## Usage

Once this role is installed on your system, include it in the roles list of your playbook.

``` yaml
- hosts: localhost
  connection: local
  roles:
    - ansible-ec2-group
```

## Dependencies

Although, this role is not dependant on ec2_provision it is highly recommended that the ec2_provision role is also added to your playbook to ensure ec2 tags match. Boto is required to use this role.

## License

MIT