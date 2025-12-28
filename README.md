##Ansible Linux User Management

📌 Overview

This repository contains a simple and practical Ansible playbook to automate Linux user management on one or more servers.

##The playbook:

Creates a Linux user

Adds the user to the wheel group

Configures passwordless sudo

Ensures idempotent execution

This project demonstrates core Ansible fundamentals commonly used in real-world DevOps and system administration tasks.

📁 Repository Structure
```bash
ansible-linux-user-management/
├── images/
│   └── user-management-output.png
├── inventory
├── playbooks/
│   ├── user_setup.yml
│   └── .dummy.yml
└── README.md
```

##File Details

playbooks/user_setup.yml
Main Ansible playbook for Linux user creation and sudo configuration

inventory
Defines the target Linux hosts

images/
Stores output screenshots for documentation

.dummy.yml
Placeholder file to keep the directory tracked in Git

⚙️ Prerequisites

Control Node

Ansible installed
```bash
dnf install -y ansible-core
```
SSH Access to target servers

##Target Hosts

Linux system

Python 3 installed

sudo/root access

📜 Inventory Example

Edit the inventory file:

[linux_servers]
192.168.1.10 ansible_user=shiyas ansible_become=true

Local Execution (Testing)
[linux_servers]
localhost ansible_connection=local

▶️ Playbook Explanation

Playbook: playbooks/user_setup.yml

Variables Used
vars:
  username: devopsadmin

##Tasks Performed

Create Linux User

Creates user devopsadmin

Adds to wheel group

Sets default shell to /bin/bash

Configure Passwordless Sudo

Creates /etc/sudoers.d/devopsadmin

Grants NOPASSWD sudo access

Applies secure permissions (0440)

▶️ Running the Playbook

From the project root directory:
```bash
ansible-playbook -i inventory playbooks/user_setup.yml
```
🔍 Validation

After execution, verify on the target system:
```bash
id devopsadmin
groups devopsadmin
```

Check sudo access:
```bash
sudo -l -U devopsadmin
```
