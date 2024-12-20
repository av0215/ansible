Ansible
===========

apt install ansible - in master

install python = for dependency (both slave and master)

vi slaves.txt
===================================
[slaves]
172.31.13.220

[slaves:vars]
ansible_user=ubuntu  
ansible_ssh_private_key_file=/root/privatekey.pem 
===================================

CONFIG FILE :

wget https://gist.githubusercontent.com/alivx/2a4ca3e577ead4bd38d247c258e6513b/raw/fe2b9b1c7abc2b52cc6998525718c9a40c7e02a5/ansible.cfg

copy the private key and create a file in ansible master server 
vi privatekey.pem

PING
ansible -i /root/slaves.txt slaves -m ping
ansible -i slaves.txt slaves -m ping

Example adhoc commands :
ansible all -i slaves.txt -m apt -a "name=docker.io state=present" -b 	
ansible all -i slaves.txt -m apt -a "name=apache2 state=present" -b
