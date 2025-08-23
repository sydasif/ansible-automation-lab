# Ansible Automation Lab Tutorial

## Introduction to Ansible
## Why Use Ansible?

---

## Ansible Fundamentals

### Ansible Basic Components
### YAML Basics for Ansible Beginners
#### Structure of YAML Files
#### Key Features of YAML
##### 1. **Comments**
##### 2. **Key-Value Pairs**
##### 3. **Strings**
##### 4. **Booleans**
##### 5. **Lists**
##### 6. **Dictionaries**
##### 7. **Multi-Line Strings**
###### Folded Style (`>`)
###### Literal Style (`|`)
##### 8. **Indentation and Formatting**
#### Summary
### Playbook in Ansible
#### Basic Example
#### Removing Files Example
#### Using Variables in Playbooks
#### Playbook with Multiple Plays
#### Conditional Task Execution (`when` Statement)
#### Summary
### Ansible Ad-Hoc Commands
#### Basic Syntax
#### Common Ad-Hoc Command Examples
##### 1. Ping all hosts
##### 2. Check system uptime
##### 3. Run commands as root (become)
##### 4. Copy content to a file (using `copy` module)
##### 5. Using `shell` module for commands with pipes or redirection
##### 6. Using `raw` module for devices without Python
#### Viewing Module Documentation
#### Summary
### Ansible Configuration and Setting
#### The Configuration File
#### The ansible-config Utility
##### Viewing the Current Configuration
##### Dumping the Current Configuration
##### Listing All Parameters
##### How Ansible Works - Precedence Rules
##### Example Configuration
### Ansible Inventory Setting
#### Formats for Inventory Files
#### Defining Host Aliases
#### Inventory and Variables
##### Host Variables
##### Group Variables
#### Key Points About Inventory
### Test Your Ansible Setup - Playbook
#### Playbook Definition
#### Play Name
#### Hosts
#### Gather Facts
#### Connection Type
#### Tasks
### Running the Playbook
### Conclusion

---

## The Two Paths of Automation

### Part 1: Server Automation
### Part 2: Network Automation
#### Ansible for Network Automation Overview
##### What is a Push Model?
##### What is a Pull Model?
##### Ansible's Approach to Automation
##### Ease of Adoption for Network Engineers
##### Built-In Concurrency
##### Getting Started with Ansible for Network Automation
##### Network Modules in Ansible

---

## Lab Setup Guide

### Server Automation Labs
#### Ansible Lab Setup with KVM
#### Ansible Vagrant Lab Setup
### Network Automation Lab
#### EVE-NG Lab Setup (Conceptual)

---

## Table of Contents

### Part 1: Ansible Fundamentals
### Part 2: Server Automation Labs
#### Lab Setup Guides
#### Basic Playbooks:
#### Vagrant Specific Files:
### Part 3: Network Automation Labs (EVE-NG)
#### Introduction & Configuration
#### Variable Management:
#### Network Playbooks:
#### Configuration Files:
#### EVE-NG Specific Playbooks:
### Part 4: Advanced Ansible Concepts / Cookbook
#### Variable Management:
#### Chapter 1 Ansible:
