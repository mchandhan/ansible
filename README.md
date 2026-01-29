# Ansible Playbook Repository

This repository contains Ansible playbooks for automating infrastructure configuration and management.

## Prerequisites

- A Linux distribution (Ubuntu recommended)
- Python 3.x installed on your system
- `pipx` or the ability to create Python virtual environments

## Installation

### Option 1: Install Ansible using pipx (Recommended)

pipx installs Ansible in an isolated environment while making it globally available.

```bash
# Install pipx if not already installed
sudo apt update
sudo apt install pipx

# Ensure pipx is in your PATH
pipx ensurepath

# Install Ansible
pipx install ansible
```

### Option 2: Install Ansible in a Virtual Environment

```bash
# Install venv if not already installed
sudo apt update
sudo apt install python3-venv

# Create a virtual environment
python3 -m venv ansible-env

# Activate the virtual environment
source ansible-env/bin/activate

# Install Ansible
pip install ansible
```

### Verify Installation

Check that Ansible is installed correctly:

```bash
ansible --version
```

## Getting Started

### 1. Clone the Repository

Clone this repository to your local system:

```bash
git clone https://github.com/mchandhan/ansible.git
cd ansible
```

### 2. Review Configuration Files

Before running the playbook, review the following files:

- `hosts.ini` - Contains the inventory of hosts
- `test.yml` - The main playbook file

### 3. Run the Ansible Playbook

Execute the playbook using the following command:

```bash
ansible-playbook -i hosts.ini test.yml
```

### 4. Verify the Deployment

After the playbook completes, verify that Apache2 is running:

```bash
systemctl status apache2
```

You should see output indicating that Apache2 is active and running.

### Apache2 is not running

If Apache2 is not active after running the playbook:

```bash
# Check the service status
sudo systemctl status apache2

# View the logs
sudo journalctl -u apache2

# Manually start the service
sudo systemctl start apache2
```

### Connection Issues

If you encounter SSH connection issues:

- Ensure SSH keys are properly configured
- Verify that target hosts are accessible
- Check the `hosts.ini` file for correct IP addresses/hostnames



## Project Structure

```
.
├── README.md           # This file
├── hosts.ini           # Inventory file
├── test.yml            # Main playbook
└── ...                 # Other playbooks and configuration files

- [Ansible Documentation](https://docs.ansible.com/)
- [Ansible Best Practices](https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html)
- [Apache2 Documentation](https://httpd.apache.org/docs/)
