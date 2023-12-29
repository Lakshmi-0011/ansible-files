Ansible is an open-source automation tool that simplifies the task of configuring and managing computer systems. It falls under the category of Configuration Management and is widely used for automating various IT processes such as provisioning, application deployment, and task automation.

Configuration Management: It involves managing and controlling the configuration of software, infrastructure, and systems to ensure consistency, reliability, and efficiency. Configuration Management tools like Ansible help organizations automate and streamline these processes.

Playbook: Playbooks are Ansible's configuration, deployment, and orchestration language. They are expressed in YAML format and define a set of tasks to be executed on remote hosts.
Modules: Ansible uses modules to perform specific tasks on remote hosts, such as managing packages, files, services, users, and more. Modules can be executed directly from the command line or used within playbooks.
Roles: Roles are a way of organizing playbooks and other files in a reusable structure. They allow you to encapsulate and share functionality across multiple playbooks.
Ad-Hoc Commands: Ansible allows you to run ad-hoc commands from the command line to perform quick tasks on remote hosts without writing a playbook.
Integration: Ansible can integrate with various cloud providers, networking devices, and other infrastructure components through its extensive collection of modules and plugins.

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

