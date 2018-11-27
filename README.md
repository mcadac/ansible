# Ansible

Ansible slef study

## Test
1. Build docker image 
	-  docker image build -t ansible-ssh ./
	
2. Run container: 

	- docker run -d -P -v "D:\study\ansible\ansible-docker\playbook:/tmp/ansible" -v  "D:\study\ansible\ansible-docker\playbook\hosts:/etc/ansible/hosts" --name ansible-test --rm  ansible-ssh  bash


### References

1. Ansible examples: https://github.com/ansible/ansible-examples

### Commands

docker run -it -P -v "D:\study\ansible\ansible-docker\playbook:/tmp/ansible" -v  "D:\study\ansible\ansible-docker\playbook\hosts:/etc/ansible/hosts" --name ansible-test --rm  ansible-ssh  bash


