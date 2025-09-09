# Ansible - Real time project

## Tasks

1. Set up ec2 instances(2 ubuntu, 1 Amazon Linux)
2. Set passwordless authentication on all three ec2 instances
3. Set up automatic shutdown of ubunut instances only using ansible conditionals.

# Prerequisites:

# Setup EC2 Collection and Authentication, SSH Key pair creation

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

## Create SSH key pair

Create a key pair in AWS. Ensure that the key pair is created in the same region as the one used in the ec2_create.yaml.

# Commands for Task 1

```
ansible-playbook ec2-create.yaml --vault-password-file vault.pass
```

# Commands for Task 2

```
ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>
```

# Commands for Task 3

```
ansible-playbook -i inventory.ini ec2_shutdown.yaml --vault-password-file vault.pass
```

Note: inventory.ini file has to be created in the format as specified prior to the execution of this command. Eg: user@<ec2-public-ip>
