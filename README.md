# Ansible Static Website Deployment with Apache2

Automate the deployment of a static website using Apache2 web server with Ansible.

## Prerequisites

- Ubuntu/Debian-based system (control node)
- Python 3.8+
- SSH access to target servers
- Target servers running Ubuntu/Debian

## Quick Start

### 1. Install Ansible (using Virtual Environment)

```bash
# Install Python and venv
sudo apt update
sudo apt install python3 python3-pip python3-venv -y

# Create and activate virtual environment
python3 -m venv ansible-env
source ansible-env/bin/activate

# Install Ansible
pip install --upgrade pip
pip install ansible

# Verify installation
ansible --version
```

### 2. Clone Repository

```bash
git clone https://github.com/mchandhan/Ansible-code-to-launch-an-static-website-using-apache2.git
cd Ansible-code-to-launch-an-static-website-using-apache2
```

### 3. Configure the path of the html file

In file write.yml change the src: path to your written new index.html path


### 4. Test Connection

```bash
ansible all -i hosts.ini -m ping
```

### 5. Deploy Website

```bash
# Run main playbook (installs Apache2 and deploys website)
ansible-playbook -i hosts.ini main.yml
```

### 6. Access Website

Open browser and visit: `http://your-server-ip/` / `http://localhost/`

## Project Files

- **main.yml** - Main playbook (runs everything)
- **apt.yml** - Updates package cache
- **service.yml** - Manages Apache2 service
- **write.yml** - Deploys website files
- **hosts.ini** - Server inventory
- **index.html** - Your website content

## Common Commands

```bash
# Activate virtual environment (if not active)
source ansible-env/bin/activate

# Deploy website
ansible-playbook -i hosts.ini main.yml

# Update website content only
ansible-playbook -i hosts.ini write.yml

# Check syntax before running
ansible-playbook -i hosts.ini main.yml --syntax-check

# Dry run (test without changes)
ansible-playbook -i hosts.ini main.yml --check

# Deactivate virtual environment
deactivate
```

## Troubleshooting

**Check Apache Status:**
```bash
"sudo systemctl status apache2"
```

## Customize Your Website

Edit `index.html` to change your website content, then run:

```bash
ansible-playbook -i hosts.ini main.yml
```

---

**Note:** Remember to activate your virtual environment before running Ansible commands:
```bash
source ansible-env/bin/activate
```
