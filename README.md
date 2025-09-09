# Ansible - Real time project
## Tasks

1. Set up ec2 instances(2 ubuntu, 1 Amazon Linux)
2. Set passwordless authentication on all three ec2 instances
3. Set up automatic shutdown of ubunut instances only using ansible conditionals. 


# Prerequisites:
# Setup EC2 Collection and Authentication

## Install boto3

```
pip install boto3
```

## Install AWS Collection

```
ansible-galaxy collection install amazon.aws
```

## Setup Vault 

1. Create a password for vault

```
openssl rand -base64 2048 > vault.pass
```

2. Add your AWS credentials using the below vault command

```
ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass
```





