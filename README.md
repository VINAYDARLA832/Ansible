# Ansible Automation Repository 

This repository contains Ansible playbooks created as part of learning DevOps automation and Infrastructure as Code (IaC).

Ansible is an open-source automation tool used for configuration management, application deployment, provisioning, and orchestration of servers.

It helps automate repetitive tasks such as installing software, managing services, configuring files, and deploying applications across multiple servers.

Ansible works mainly using a push-based mechanism where the control node connects to managed nodes using SSH. It is agentless, meaning no software installation is required on target servers.

---

# Repository Objectives

This repository demonstrates practical knowledge of:

• Writing Ansible playbooks using YAML
• Automating server configuration tasks
• Using Infrastructure as Code approach
• Managing multiple servers efficiently
• Understanding core Ansible concepts

---

# Topics Covered

## YAML Basics

Understanding YAML syntax is important because Ansible playbooks are written in YAML.

Concepts covered:

Key value pairs
Lists
Dictionary structure
Indentation rules
Nested values

---

## Inventory

Inventory file contains the list of managed nodes where Ansible executes tasks.

Servers can be grouped based on roles such as web servers or database servers.

Example:

[web]
server1
server2

[db]
server3

---

## Modules

Modules are prebuilt automation units used to perform tasks.

Common modules used in this repository:

ping → check connectivity
dnf / yum / apt → install packages
file → create or modify files
service → start or stop services
copy → copy files to remote servers
command → execute commands

Modules reduce manual work and improve automation efficiency.

---

## Variables

Variables allow dynamic values in playbooks.

Variables help reuse playbooks for different environments.

Example:

vars:
package_name: nginx

Usage:

name: "{{ package_name }}"

---

## Datatypes in Variables

Common variable datatypes used in Ansible:

String

name: "nginx"

Number

port: 8080

Boolean

enabled: true

List

packages:

* nginx
* git
* curl

Dictionary

user:
name: vinay
role: devops

---

## Conditions

Conditions allow execution of tasks based on specific criteria.

Example:

when: ansible_os_family == "RedHat"

This ensures task runs only on RedHat based systems.

---

## Loops

Loops help execute tasks multiple times.

Example:

loop:

* nginx
* git
* curl

This installs multiple packages using single task.

---

## Gather Facts

Ansible automatically collects system information using gather_facts.

Examples of facts:

Operating system
IP address
Hostname
Memory details

Example usage:

ansible_facts['hostname']

Gather facts helps in writing dynamic playbooks.

---

## Filters

Filters modify variable values.

Common filters:

upper → convert to uppercase
lower → convert to lowercase
default → assign default value
length → count list items

Example:

"{{ name | upper }}"

Filters help transform data dynamically.

---

## Error Handling

Error handling helps control playbook execution when failures occur.

Methods:

ignore_errors → continue even if task fails

Example:

ignore_errors: yes

failed_when → define custom failure condition

changed_when → control change status

Error handling helps create stable automation workflows.

---

## Roles

Roles provide structured way to organize playbooks.

Roles help divide automation tasks into reusable components.

Role structure example:

roles/
web/
tasks/
handlers/
vars/
templates/

Benefits:

Reusable code
Better organization
Easy maintenance
Scalable automation

---

## Playbooks

Playbooks define automation steps.

Playbooks specify:

target servers
tasks to execute
modules to use

Example:

* name: install nginx
  hosts: web
  become: yes

  tasks:

  * name: install nginx
    dnf:
    name: nginx
    state: present

---

# Skills Demonstrated

Understanding of configuration management
Knowledge of YAML syntax
Ability to create reusable automation scripts
Understanding of Infrastructure as Code
Ability to manage multiple servers
Knowledge of DevOps automation concepts

---

# How to run playbook

Install Ansible:

sudo dnf install ansible -y

Check connectivity:

ansible all -m ping

Run playbook:

ansible-playbook playbook.yml

---

# Use Cases of Ansible

Server configuration automation
Application deployment automation
Installing packages automatically
Managing services
Environment setup automation
Infrastructure provisioning

---

# Future Enhancements

Adding handlers
Using templates (Jinja2)
Implementing dynamic inventory
Integrating with CI/CD pipelines
Creating end-to-end automation workflows

---

# Author

Vinay Kumar
DevOps / DevSecOps Engineer
Interested in Automation, Cloud and Infrastructure

---
