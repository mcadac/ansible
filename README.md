# Ansible

Ansible slef study

## Examples

1. **SSH service with Docker:** https://github.com/mcadac/ansible/tree/master/ssh-service
2. **Ansible in a docker container:** https://github.com/mcadac/ansible/tree/master/ansible-docker

### Cases

1. How to indicate to Ansible that execute process in your host?

    - In the inventory file set the next values: 
      **localhost ansible_connection=local**

2. Connection plugin to connect a windows server

    - In the inventory file set the next values: 
      **server ansible_connection=winrm**

### References

1. Ansible examples: https://github.com/ansible/ansible-examples

### Commands

#### Ansible commands
1. ansible all -m ping --> **Validate connection with the hosts**
2. ansible {sever_or_server_name} -m ping -i {inventory_file} --> **Validate connection with a specific server**
3. ansible-plabook {playbook_file_name} -i {inventory_file} --> **Execute a plabook**

### Plays and Tasks

1. To create a directory and check if exist,  we can use the next form in the task:
    ```
    ...
     name: Create a directory with check
     command: mkdir /folder creates=/folder
    ...
    ```

2. To changes current folder before to execute the task

    ```
    ...
       name: Execute a file but before it change the location
       command: cat playbook-copy.yml chdir=/tmp/ansible/ansible-docker
    ```
3. To add a new line in a file

    ```
      -
        lineinfile:
            path: /tmp/ansible/exercise-2/result-copy.txt
            line: 'The new line in the file from ansible'
    ```
#### Other commands
docker run -it -P -v "D:\study\ansible\ansible-docker\playbook:/tmp/ansible" -v  "D:\study\ansible\ansible-docker\playbook\hosts:/etc/ansible/hosts" --name ansible-test --rm  ansible-ssh  bash


