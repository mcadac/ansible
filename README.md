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

### Commands

#### Ansible commands
1. ansible all -m ping --> **Validate connection with the hosts**
2. ansible {sever_or_server_name} -m ping -i {inventory_file} --> **Validate connection with a specific server**
3. ansible-plabook {playbook_file_name} -i {inventory_file} --> **Execute a plabook**

### Plays and Tasks examples (These were tested)

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
 4. To add variables in the same playbook file
    
    ```
        name: Update nameserver entry into resolv.conf file on localhost
        hosts: localhost
        vars:
          car_model: "BMW M3"
          country_name: USA
          title: "Systems Engineer"
        tasks:
    ```
 5. To add an conditional statement to a task (You can use 'or' to add other conditional)
    ```
    -
      name: Execute a script on all web server nodes
      hosts: all_servers
      tasks:
        -
          service: name=mysql state=started
          when: ansible_host == 'server4.company.com'
    ```
    
    ```
    -
      name: Am in an Adult or a Child
      hosts: localhost
      vars:
        age: 25
      tasks:
        -
          command: echo "I am a Child"
          when: age < 18

        -
          command: echo "I am an Adult"
          when: age >= 18
    ```
  
  6. To use a loop in a task
  
    ```
    -
      hosts: localhost
      vars:
          fruits:
            - Apple
            - Banana
            - Grapes
            - Orange
      tasks:
        -
          command: echo "{{ item }}"
          with_items: '{{fruits }}'
    ```
   Another example with the yuml loop module (Ansible module)  
    
    ```
    -
      name: Install required packages
      hosts: localhost
      vars:
          packages:
          - httpd
          - binutils
          - glibc
          - ksh
          - libaio
          - libXext
          - gcc
          - make
          - sysstat
          - unixODBC
          - mongodb
          - nodejs
          - grunt

      tasks:
        -
          yum: name='{{ item }}' state=present
          with_items: '{{packages}}'
    
    ```
  

#### Other commands
docker run -it -P -v "D:\study\ansible\ansible-docker\playbook:/tmp/ansible" -v  "D:\study\ansible\ansible-docker\playbook\hosts:/etc/ansible/hosts" --name ansible-test --rm  ansible-ssh  bash

### References

1. Ansible examples: https://github.com/ansible/ansible-examples
2. Course: https://naspers.udemy.com/learn-ansible


