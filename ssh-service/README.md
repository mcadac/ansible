# Deploy a SSH service with docker

## System
	- OS : Windows 10
	- Docker version : 18.0.6

## Test

1. Build docker image
	- docker build -t eg_sshd .

2. Run container
	- docker run -d -p 22:22 --name test_sshd eg_sshd

3. Validate port exposed 
	- docker port test_sshd 22

4. Connect by ssh to container
	- ssh root@192.168.1.2 -p 22
	- the user password is: screencast

### Reference 

1. https://docs.docker.com/engine/examples/running_ssh_service/

