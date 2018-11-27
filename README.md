# Ansible

Ansible slef study

## Examples

1. **SSH service with Docker:** https://github.com/mcadac/ansible/tree/master/ssh-service
2. **Ansible in a docker container:** https://github.com/mcadac/ansible/tree/master/ansible-docker

### Cases

1. How to indicate to Ansible that execute process in your host?

  - In the inventory file set the next values: 
      **localhost ansible_connection=localhost**

### References

1. Ansible examples: https://github.com/ansible/ansible-examples

### Commands

#### Ansible commands
1. ansible all -m ping --> **Validate connection with the hosts**

#### Other commands
docker run -it -P -v "D:\study\ansible\ansible-docker\playbook:/tmp/ansible" -v  "D:\study\ansible\ansible-docker\playbook\hosts:/etc/ansible/hosts" --name ansible-test --rm  ansible-ssh  bash


