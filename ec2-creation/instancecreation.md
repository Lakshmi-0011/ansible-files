For instance creation and hosting web page follow below steps:
Steps:
Step1: edit ansible configuration file. Add the below lines in ansible.cfg file (this configuration is related to remote host access for installing apache after instance creation)
vi /etc/ansible/ansible.cfg
[defaults]
host_key_checking = false
remote_user = ubuntu
ask_pass = false
private_key_file = ~/ansible/pemkey.pem
roles_path = ~/ansible/httpdserver
[privilege_escalation]
become = true
become_method = sudo
become_user = root
become_ask_pass = false

step2:
ansible-galaxy collection install amazon.aws
install boto3 (boto3 is the Amazon Web Services (AWS) SDK for Python. It allows Python developers to write software that makes use of services like Amazon S3, Amazon EC2, Amazon DynamoDB, and many others.)

create role using "ansible-galaxy init httpdserver" 
httpdserver->tasks->main.yml (write code for installation of apache server and hosting web page)
write a playbook for installing new instance, add the public ip of instance to hosts file dynamically and include the role (instance.yml)
