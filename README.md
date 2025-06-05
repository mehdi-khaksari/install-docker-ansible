# 🐳 Docker Installation with Ansible

This Ansible playbook automates the installation of Docker on Ubuntu servers.

## 📋 Table of Contents
- [🏗️ Repository Structure](#-repository-structure)
- [📦 Prerequisites](#-prerequisites)
- [⚡ Quick Start](#-quick-start)
- [🔍 Detailed Usage](#-detailed-usage)
  - [📝 Inventory Configuration](#-inventory-configuration)
  - [▶️ Running the Playbook](#️-running-the-playbook)
  - [🏷️ Tagged Execution](#️-tagged-execution)
- [⚙️ Playbook Tasks](#️-playbook-tasks)
- [🎨 Customization](#-customization)
- [⚠️ Troubleshooting](#️-troubleshooting)

## 🏗️ Repository Structure

```text
/etc/ansible/docker
├── docker.yml                # Main playbook
├── inventory
│   └── hosts                 # Inventory file
└── roles
    └── docker                # Docker installation role
        ├── files
        ├── handlers
        │   └── main.yml
        ├── tasks
        │   └── main.yml     # Main tasks for Docker installation
        ├── templates
        └── vars
            └── main.yml
```

## 📦 Prerequisites

- Ansible installed on control machine (version 2.9+ recommended)

- SSH access to target servers with sudo privileges

- Target servers running Ubuntu (tested on 20.04/22.04)

## ⚡Installation Steps

1. Clone this repository

2. Modify the inventory/hosts file with your server IPs

3. Run the playbook:
```bash
ansible-playbook -i inventory/hosts docker.yml
```
## ▶️ Playbook Details

### The playbook performs the following tasks on target servers:

1. Updates apt package index

2. Installs prerequisite packages (ca-certificates, curl)

3. Sets up Docker's GPG key

4. Adds Docker's official APT repository

5. Installs Docker components:

    - docker-ce

    - docker-ce-cli

    - containerd.io

    - docker-buildx-plugin

    - docker-compose-plugin

## 📝 Inventory

The inventory file inventory/hosts contains:
```ini
[servers]
10.10.10.18
10.10.10.19
```
Replace these IPs with your target servers' addresses.

## 🏷️ Tags
The tasks are organized with tags for selective execution:

- <code>apt</code>: Initial package update

- <code>aptca</code>: CA certificates installation

- <code>key</code>: GPG key setup

- <code>getkey</code>: Download Docker GPG key

- <code>code</code>: Ubuntu codename detection and repository setup

- <code>apt2</code>: Secondary package update

- <code>dockerce</code>: Docker package installation

### Example of running specific tags:
```bash
ansible-playbook -i inventory/hosts docker.yml --tags "apt,dockerce"
```

# 📬 Contact
Feel free to fork, improve, and contribute!

Author: mehdi khaksari 

Email: mahdikhaksari36@gmail.com


