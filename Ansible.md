Components of Ansible:
1.  Control Node: The machine where Ansible is installed and from which commands are executed.
2.  Managed Nodes: The target machines that are managed by Ansible.
3.  Inventory: A file that lists the managed nodes and their connection details.
4.  Module: Reusable, standalone scripts that Ansible uses to perform tasks on managed nodes.
5.  Task: Task in ansible consists of module name and its arguments.
6.  play: A set of tasks to be executed on managed nodes.
7.  Playbook: A YAMML file consisting of one or more plays.
8.  Playbooks: YAML files that define the tasks to be executed on the managed nodes.
9.  Plugins: Extend Ansible's core functionality, such as connection types and callbacks.
10. Roles: A way to organize playbooks and related files into reusable components.
11. Galaxy: A repository for sharing Ansible roles and collections.
12. Configuration File: Ansible.cfg file that contains settings and configurations for Ansible.


----------------------------------------------------------------------------------------------------

# In Ansible we have 2 ways to execute commands on remote machines
1. Ad-hoc 
commands: These are one-liner commands that can be executed directly from the command line to perform simple tasks on managed nodes without writing a playbook.
Example 1:

*** ansible -i inventory_file -m ping all

Installs the ping module on all the host machines listed in the inventory file and runs it.

Example 2:

*** ansible  -b -i inventory_file -m apt "name=apache2 state=present update_cache=yes" all

This command uses the apt module to install the apache2 package on all host machines listed in the inventory_file with sudo privileges (-b flag) and apt module arguments are passed in quotes.
arguments are:
name=apache2 : specifies the package name to be installed.
state=present : ensures that the package is installed.
update_cache=yes : updates the package cache before installing the package.

Example 3:

*** ansible -b  -i inventory_file  -m apt "name=nginx state = present update_cache=yes" all

This command uses the apt module to install the nginx package on all host machines listed in the inventory_file with sudo privileges (-b flag) and apt module arguments are passed in quotes.
arguments are:
name=nginx : specifies the package name to be installed.
state=present : ensures that the package is installed.
update_cache=yes : updates the package cache before installing the package.

2. Playbooks: These are YAML files that define a series of tasks to be executed on managed nodes. Playbooks allow for more complex automation and configuration management compared to ad-hoc commands.
Example Playbook to install Apache2 on remote machines:
---
- name: to install Apache2
  hosts: all
  become: true
  tasks:
  - name: to install apache2 
    apt:
      name: apache2 
      state: present


----------------------------------------------------------------------------------------------------

=====>
Idempotent:
Idempotent is the principle that applying 
