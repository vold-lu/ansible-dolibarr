# Ansible playbook for Dolibarr

This playbook allows easy setup of [Dolibarr](https://www.dolibarr.org) using [Ansible](https://www.ansible.com).
The playbook will install Dolibarr directly from the Git repository.

## How to use it?

### Configure the server and install Dolibarr using the playbook

```bash
# Clone the repository
git clone https://github.com/vold-lu/ansible-dolibarr.git
cd ansible-dolibarr

# Install the used ansible collections
ansible-galaxy install -r requirements.yml

# Create the inventory file (replace 127.0.0.1 by your host IP address)
echo '127.0.0.1' >> .inventory

# Run the playbook against the inventory
ansible-playbook -i .inventory dolibarr.yml --extra-vars "app_url=dolibarr.mycompany.com"

# You can also clone a custom Dolibarr repository and/or on a specific branch
ansible-playbook -i .inventory dolibarr.yml --extra-vars "app_url=dolibarr.mycompany.com git_url=https://github.com/mycompany/dolibarr.git git_branch=15.0"
```

### Perform the settings

Head out to https://dolibarr.mycompany.com/install and finalize the setup.

### Enable auto SSL certificate generation (Lets Encrypt)

```bash
certbot --nginx -d dolibarr.mycompany.com
```
