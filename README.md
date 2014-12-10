# Ansible Role For EC2 Security Group Provisioning

Provions one ec2 security group to be used with your instance/s.  This role provisions goups inside of a EC2 VPC it has notbeen tested to provision security groups in the EC2 Classic network.

## Installation

``` bash
$ ansible-galaxy install crushlovely.ec2_group
```
## Variables

You will want to fill all these in before running the role.

``` yaml
ec2_access_key: ""
ec2_secret_key: ""
acct_vpc_id:
region: ""
vpc_subnet:
app_name:
server_env:
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
  gather_facts: True
  roles:
    - { role: crushlovely.ec2_group }
```

## Dependencies

Although, this role is not dependant on ec2_provision it is highly recommended that the ec2_provision role is also added to your playbook to ensure ec2 tags match. Boto is required to use this role.

## License

MIT