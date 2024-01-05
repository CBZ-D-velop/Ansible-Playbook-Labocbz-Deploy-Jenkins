# Ansible playbook: labocbz.deploy_jenkins

![Licence Status](https://img.shields.io/badge/licence-MIT-brightgreen)
![CI Status](https://img.shields.io/badge/CI-success-brightgreen)
![Testing Method](https://img.shields.io/badge/Testing%20Method-Ansible%20Molecule-blueviolet)
![Testing Driver](https://img.shields.io/badge/Testing%20Driver-docker-blueviolet)
![Language Status](https://img.shields.io/badge/language-Ansible-red)
![Compagny](https://img.shields.io/badge/Compagny-Labo--CBZ-blue)
![Author](https://img.shields.io/badge/Author-Lord%20Robin%20Crombez-blue)

## Description

![Tag: Ansible](https://img.shields.io/badge/Tech-Ansible-orange)
![Tag: Debian](https://img.shields.io/badge/Tech-Debian-orange)
![Tag: Apache2](https://img.shields.io/badge/Tech-Apache2-orange)
![Tag: SSL/TLS](https://img.shields.io/badge/Tech-SSL%2FTLS-orange)
![Tag: Jenkins](https://img.shields.io/badge/Tech-Jenkins-orange)
![Tag: Docker](https://img.shields.io/badge/Tech-Docker-orange)
![Tag: Watchtower](https://img.shields.io/badge/Tech-Watchtower-orange)

An Ansible playbook to deploy and configure a Jenkins server on your hosts.

This Ansible playbook orchestrates the installation of Jenkins, Docker, and Apache2. Notably, Jenkins lacks native SSL support, making the presence of an SSL reverse proxy highly recommended, although its installation is not mandatory in this playbook. Additionally, Apache2 installation is conditional based on a boolean variable.

If remote certificates are available, the playbook can download and install them for Apache2. Security measures, including mod evasive, mod qos, WAF, and optimization configurations, are also managed.

## Deployment diagramm

![](./assets/Ansible-Playbook-Labocbz-Deploy-Jenkins.drawio.svg)

Here is a possible deployment example with this playbook. The components involved are Apache2, Jenkins, Docker, and Watchtower. We observe that clients access Jenkins through Apache2, which acts as an SSL/TLS proxy.

## Tests and simulations

### Basics

You have to run multiples tests. *tests with an # are mandatory*

```MARKDOWN
# lint
# syntax
# converge
# idempotence
# verify
side_effect
```

Executing theses test in this order is called a "scenario" and Molecule can handle them.

Molecule use Ansible and pre configured playbook to create containers, prepare them, converge (run the playbook) and verify its execution.
You can manage multiples scenario with multiples tests in order to get a 100% code coverage.

This playbook contains a ./tests folder. In this folder you can use the inventory or the tower folder to create a simualtion of a real inventory and a real AWX / Tower job execution.

### Command reminder

```SHELL
# Check your YAML syntax
yamllint -c ./.yamllint .

# Check your Ansible syntax and code security
ansible-lint --config=./.ansible-lint .

# Execute and test your playbook
molecule lint
molecule create
molecule list
molecule converge
molecule verify
molecule destroy

# Execute all previous task in one single command
molecule test
```

## Installation

To install this playbook, just copy/import this playbook or raw file into your fresh playbook repository or call it with the "include_playbook/import_playbook" module.

## Usage

### Vars

```YAML
# From inventory
---
# all vars from to put/from your inventory
# see tests/inventory/group_var for all groups and vars.
```

```YAML
# From AWX / Tower
---
all vars from to put/from AWX / Tower
```

## Architectural Decisions Records

Here you can put your change to keep a trace of your work and decisions.

### 2024-01-04: First Init

* First init of this playbook with the bootstrap_playbook playbook by Lord Robin Crombez

### 2024-01-05: 

* Playbook install Apache2, Docker, Jenkins
* Need to get the Jenkins password on log after isntall for first launch
* You can protect your Jenkins behind Apache2

## Authors

* Lord Robin Crombez

## Sources

* [Ansible playbook documentation](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_playbooks.html)
* [Ansible Molecule documentation](https://molecule.readthedocs.io/)
