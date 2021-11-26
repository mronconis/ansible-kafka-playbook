
# Ansible kafka playbook


## Operations

### Init vault 

Create a vault password file. It is required to decrypt vaulted variables.

```
echo "password" > .vault-password-file
```

### Update SSH Password

Obtain the encrypted value, then update the proper variable (i.e. vaulted_ansible_password):

```
ansible-vault encrypt_string "kafka"
```


## Develop

### Setup virtual env

```
virtualenv .venv
source .venv/bin/activate
pip install -r requirements.txt
```