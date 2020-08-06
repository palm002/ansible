# ansible


## Overview<a name="overview"></a>

  0. [Overview](#overview)
  1. [Requirements](#requirements)
  2. [Getting Started](#getting-started)
  3. [Description](#info)
  4. [Running the playbook](#playbook)
  5. [SSH](#ssh)

### Requirements<a name="requirements"></a>

Before making use of this codebase, please ensure you satisfy the following
requirements:

  1. [Ansible](http://docs.ansible.com/ansible/) >= 2.9.2
  2. A valid AWS account that can access created EC2 instances


## Getting Started<a name="getting-started"></a>

In order to run the playbook, `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`
values need to be set in AWS credentials file, generally found in `~./aws/credentials`

To configure these keys, run `aws configure`


## Description<a name="info"></a>

This playbook spins up a clean EC2 instance and installs
the following tools and runs tests with <a href='https://github.com/aelsabbahy/goss'>goss</a>

- goss
- git
- gcc-c++
- make
- nodejs
- python3
- java8
- golang

<b><em>NOTE:</em></b> As goss runs tests on all of the roles, it is a dependency on this playbook and 
deleting/ignoring the `goss` role will result in a failure of the playbook.


## Group vars

I have set up my VPC, subnets and security group, as well as my own keys (which exist on AWS) manually
prior to writing the playbook so if you wish to use it, please change the values in `./group_vars/all.yaml`

You may also want to change the `instance_name` and `owner` under Tags.

## Running the playbook<a name="playbook"></a>

In order to run the playbook, navigate to the repo and use this command.

```
cd ansible-single-node
ansible-playbook basic_ec2.yaml --private-key=path/to/key.pem
```


## SSH<a name="ssh"></a>

Once the playbook finishes, simply connect to the Public DNS of the instance.
This can be seen on AWS Console in EC2 Management
To login, run this command to connect to the newly made instance.
`ssh -i "path/to/key.pem" centos@<Public_DNS>`
