# Ansible Role: Odoo for Labs or training

[![CI](icones/odoo_icon-100.png)](https://github.com/sadofrazer/ansible_odoo/tree/v1.0)

An Ansible Role that installs up to three [odoo](https://www.odoo.com) instances on Linux , specially tailored for CentOS Distribution

If you need a more flexible and generic role for deploying simultaneous 3 odoo instances for labs or any other needs, check out [`sadofrazer.ansible_odoo`](https://github.com/sadofrazer/ansible_odoo.git).

## Requirements

This roles needs Docker Compose, requires Docker, Python Pip already be installed (you can use `geerlingguy.pip` to install it).

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

The administrator who realize the deploy

    administrator: Frazer

The Instance 1 variables, uses to create ressources of this specific odoo instance

    instance_1:
      name: INTEGRAL
      port: 8080
      db_user: odoo
      db_pass: odoo 


The Instance 2 variables, uses to create ressources of this specific odoo instance    
    
    instance_2:
      name: INTEGRAL
      port: 8080
      db_user: odoo
      db_pass: odoo


The Instance 2 variables, uses to create ressources of this specific odoo instance
  
    instance_3:
      name: INTEGRAL
      port: 8080
      db_user: odoo
      db_pass: odoo


Specify the number of instances you need to deploy (`can be 1, 2 or 3`)    

    #possibility to configure simultaneous one, two or 3 BDD
    db_qty: 3


odoo parameter which permit user to manage database needs to be true when odoo DB doesn't exist    

    list_db: True


## Use with Ansible and `docker` Python library if doesn't install

Many users of this role wish to also use Ansible to then _build_ Docker images and manage Docker containers on the server where Docker is installed. In this case, you can easily add in the `docker` Python library using the `geerlingguy.pip` role:

```yaml
- hosts: rpi

  vars:
    pip_package: python3-pip
    pip_install_packages:
      - name: docker

  roles:
    - geerlingguy.pip
    - geerlingguy.docker_arm
```

## Dependencies

None.

## Example Playbook

```yaml
- hosts: client
  become: true
  vars:
    pip_package: python3-pip
  vars_files:
    - files/secrets/credentials.yml
  roles:
    #- geerlingguy.pip
    #- geerlingguy.docker
    - odoo
```

## Author Information

This role was created in 2021 by [Frazer SADO](https://github.com/sadofrazer/), author of [Ansible for odoo](https://github.com/sadofrazer/ansible_odoo/).
