# wordpress-mysql-with-Ansible
Configure wordpress and mysql with Ansible Playbook

# installation of ansible

1- sudo apt-add-repository ppa:ansible/ansible
2- sudo apt-get update
3- sudo apt-get install ansible
4- sudo apt-get install python3-pip

5- sudo nano /etc/ansible/hosts
# create group and add the public ip of all servers that you want to add
[webservers]
server_1 ansible_host=192.168.1.1
server_2 ansible_host=192.168.1.2

[all:vars]
ansible_ssh_private_key_file=/home/ubuntu/keys/ansible_key.pem
ansible_user=ubuntu
ansible_python_interpreter=/usr/bin/python3


6- ansible-inventory --list -y

# Run playbook

1- ansible-playbook install_wordpress.yml

# how to ssh the all servers
1- create a folder on your controller node
2- copy your pem file from your local machine to controller 

3-scp -i "ansible_key.pem"  ansible_key.pem    ubuntu@192:22:22:22:/home/ubuntu/keys
4- now you can check on your controller machine to this /home/ubuntu/keys pem file exist or not

5- now to can update the hosts file 
[all:vars]
ansible_ssh_private_key_file=/home/ubuntu/keys/ansible_key.pem

6- you can check all servers are connected or not
ansible webservers -m ping
