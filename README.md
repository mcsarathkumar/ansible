# Execution of Ansible Script
Install Ansible in your operating system and then run
`ansible-playbook -i inventory.yaml main.yaml`

# Known issues and fixes
## Issue 1
### Private key unreachable
`fatal: [ubuntu]: UNREACHABLE! => {"changed": false, "msg": "Failed to connect to the host via ssh: xyz@1.2.3.4: Permission denied (publickey).", "unreachable": true}`
### Fix
add private to ssh in your file system
`ssh-add /path_to_private/privatekey.pem`

## Issue 2
`The authenticity of host '1.2.3.4 (1.2.3.4)' can't be established.`
`ED25519 key fingerprint is SHA256:8rt2P//324dfsAbsJMTadc+2GkqAVq4CVpyyXVykGI`

### Fix
Add the below script to those hosts in inventory.yaml
`ansible_ssh_common_args: '-o StrictHostKeyChecking=no'`
