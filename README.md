# KeyCloak Podman

## Overview

Deploys Nginx, Keycloak and Postres as Podman containers to two VMs in a high availability setup.  
The playbook also deploys a local OpenLDAP container as an example federation source. This can be omitted if not required by:

- Deleting `./inventory/group_vars/openldap.yml`.
- Removing the OpenLDAP variables from `./inventory/group_vars/podman.yml`.
- Changing or removing the `keycloak_user_federations` variable in `./inventory/group_vars/keycloak.yml`.
- Remove the OpenLDAP tasks block from the playbook (`./playbooks/keycloak.yml`).

## Prerequisites

- [libvirt](https://wiki.archlinux.org/title/libvirt)
- [Vagrant](https://developer.hashicorp.com/vagrant/docs/installation)
- [vagrant-libvirt](https://vagrant-libvirt.github.io/vagrant-libvirt/)

## Environment Creation

### Configuration Changes

Before creating the environment, the following variables may need to be changed depending on the environment this is deployed to:

- `podman_run_as_user`: Replace with non-root username in VM.
- The `keycloak_admin_password` and `keycloak_postgres_password` variables should be changed and encrypted in an Ansible vault.
- Set `keycloak_common.validate_certs` to true or remove it once you've got a trusted certificate.
- Change the paths of the certificate variables in `./inventory/group_vars/keycloak.yml`.

### Vagrant Up

```bash
vagrant up
```

### Ansible Setup and Run

```bash
python3 -m venv venv # Create virtual environment if it doesn't already exist
source venv/bin/activate
pip3 install -r requirements.txt
ansible-galaxy install -r requirements.yml
ansible-playbook playbooks/keycloak.yml -D
```