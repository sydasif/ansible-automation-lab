# Ansible Automation Lab Tutorial

Welcome to the Ansible Automation Lab Tutorial! This guide will walk you through the fundamentals of Ansible, its application in network automation, and advanced concepts.

## Introduction to Ansible

Ansible is a powerful open-source configuration management and provisioning tool that stands alongside industry favorites like Chef, Puppet, and Salt. Designed to streamline the process of managing and configuring nodes, Ansible enables administrators to control multiple devices from a single, centralized machine. Leveraging SSH (Paramiko) and various APIs for connectivity, Ansible simplifies the execution of configuration tasks, making it an essential tool for efficient and effective infrastructure management.

## Why Use Ansible?

In today's fast-paced IT environments, efficient and reliable configuration management tools are essential for maintaining smooth operations. Ansible stands out as a preferred choice for many organizations due to its simplicity, power, and flexibility. Here are some key reasons why Ansible is a valuable tool for managing your infrastructure:

1.  **Simple:** Ansible uses a straightforward syntax written in YAML format, known as playbooks, making it easy to learn and use.
2.  **Agentless:** There is no need to install any agents or additional software on the client systems or hosts you wish to automate, simplifying the setup and reducing security concerns.
3.  **Powerful and Flexible:** Ansible boasts powerful features that allow you to model and manage even the most complex IT workflows with ease.
4.  **Efficient:** By not requiring extra software on your servers, Ansible ensures that more resources are available for your applications, enhancing overall system performance.
5.  **Idempotent:** Ansible ensures that changes are only made when necessary to achieve the desired state, preventing unnecessary modifications and maintaining consistency across your infrastructure.

## Ansible Basic Components

Understanding the key components of Ansible is essential for effectively utilizing its capabilities. Here’s a breakdown of the fundamental elements that make up Ansible:

1.  **Control Node:** The central management point where Ansible and its code are executed. It is responsible for running tasks and gathering information about the managed nodes.
2.  **Managed Nodes:** These are the network devices and systems managed by the control node. Ansible connects to these nodes to perform configuration and management tasks.
3.  **Tasks:** The individual actions executed by Ansible. Each task performs a specific function, such as installing a package, restarting a service, or managing files.
4.  **Playbooks:** YAML files that contain a list of tasks. They define the desired state of the managed nodes and outline the sequence of actions to achieve that state, allowing for complex workflows and automation scenarios.
5.  [**Inventory**](https://docs.ansible.com/ansible/2.9/user_guide/intro_inventory.html#how-to-build-your-inventory): A list of managed nodes. An inventory file is also sometimes called a “hostfile”. Your inventory can specify information like the IP address for each managed node. An inventory can also organize managed nodes, creating and nesting groups for easier scaling.
6.  **Modules:** Units of code Ansible executes. Each module has a particular use, from administering users on a specific type of database to managing VLAN interfaces on a specific type of network device. You can invoke a single module with a task or invoke several different modules in a playbook. For an idea of how many modules Ansible includes, take a look at the [list of all modules](https://docs.ansible.com/ansible/2.9/modules/modules_by_category.html#module-index).

By understanding these components, you can effectively leverage Ansible to automate and streamline your IT operations, ensuring a more efficient and consistent infrastructure management process.

## Table of Contents

1.  **Part 1: Ansible Fundamentals**
    *   [Ansible Lab Setup with KVM](ansible-server/01-intro.md)
    *   [YAML Introduction](ansible-server/02-yaml.md)
    *   [Playbook Guide](ansible-server/03-playbook.md)
    *   [Ad-Hoc Commands](ansible-server/ad-hoc-commands.md)
    *   [Example Inventory File](ansible-server/hosts)
    *   **Basic Playbooks:**
        *   [Ping Playbook](ansible-server/playbooks/ping.yml)
        *   [Gather System Information](ansible-server/playbooks/playbook-012.yml)
        *   [Demonstrate Variable Usage](ansible-server/playbooks/playbook-3.yml)
        *   [Install Git (Ubuntu and Fedora)](ansible-server/playbooks/playbook-4.yml)
        *   [Uninstall Git (Ubuntu and Fedora)](ansible-server/playbooks/playbook-5.yml)
        *   [Uninstall Git on Ubuntu (Conditional)](ansible-server/playbooks/playbook-6.yml)
        *   [Uninstall Git on Fedora (Conditional)](ansible-server/playbooks/playbook-7.yml)
        *   [Install Git Conditionally (Ubuntu and Fedora)](ansible-server/playbooks/playbook-8.yml)
        *   [Install Vim (Generic)](ansible-server/playbooks/playbook-9.yml)
        *   [Install Updates and Web Server (Ubuntu and Fedora)](ansible-server/playbooks/playbook-10.yml)
    *   **Vagrant Labs:**
        *   [Ansible Installation on Vagrant](ansible-server/vagrant/ansible-installation-on-vagrant.md)
        *   [Ansible Vagrant Lab Overview](ansible-server/vagrant/ansible-vagrant-lab.md)
        *   [Vagrantfile Lab 1](ansible-server/vagrant/lab-1/Vagrantfile)
        *   [Vagrantfile Lab 2](ansible-server/vagrant/lab-2/Vagrantfile)

2.  **Part 2: Ansible for Network Automation**
    *   [Introduction to Network Automation](ansible-network-lab/01-intro.md)
    *   [Ansible Configuration and Settings](ansible-network-lab/ansible-configuration-and-setting.md)
    *   [Network Device Inventory](ansible-network-lab/inventory.yaml)
    *   **Variable Management:**
        *   [Campus Group Variables](ansible-network-lab/group_vars/campus.yaml)
        *   [Access 01 Host Variables](ansible-network-lab/host_vars/access_01.yaml)
        *   [Core Host Variables](ansible-network-lab/host_vars/core.yaml)
        *   [Distribution 01 Host Variables](ansible-network-lab/host_vars/dist_01.yaml)
        *   [Distribution 02 Host Variables](ansible-network-lab/host_vars/dist_02.yaml)
    *   **Network Playbooks:**
        *   [Banner Configuration](ansible-network-lab/playbooks/01_banner.yml)
        *   [Copy Running Configuration](ansible-network-lab/playbooks/02_copy_run_sta.yml)
        *   [Configure Hostname](ansible-network-lab/playbooks/03_config_hostname.yml)
        *   [Configure Ethernet Channel](ansible-network-lab/playbooks/conf_eth_cha.yml)
        *   [Config File Playbook](ansible-network-lab/playbooks/config_file.yml)
        *   [Create VLAN](ansible-network-lab/playbooks/create_vlan.yml)
        *   [Dictionary Loop Example](ansible-network-lab/playbooks/dict_loop.yml)
        *   [EIGRP Distribution](ansible-network-lab/playbooks/eigrp_dist.yml)
        *   [Interface VLAN](ansible-network-lab/playbooks/int_vlan.yml)
        *   [IOS Command Run Config](ansible-network-lab/playbooks/ios_command_run_config.yml)
        *   [IOS Facts](ansible-network-lab/playbooks/ios_facts.yml)
        *   [IOS Interface](ansible-network-lab/playbooks/ios_int.yml)
        *   [IOS Interface 02](ansible-network-lab/playbooks/ios_intf02.yml)
    *   [Configure VLANs on Interfaces](ansible-network-lab/playbooks/ios_l2_int.yml)
        *   [OSPF Core](ansible-network-lab/playbooks/ospf_core.yml)
        *   [OSPF R1](ansible-network-lab/playbooks/ospf_r1.yml)
        *   [Save Configuration](ansible-network-lab/playbooks/save_config.yml)
        *   [Save Show Run](ansible-network-lab/playbooks/save_sh_run.yml)
        *   [Standard Loop Example](ansible-network-lab/playbooks/standard_loop.yml)
        *   [User Configuration](ansible-network-lab/playbooks/user_config.yml)
        *   [VLAN Loop Example](ansible-network-lab/playbooks/vlan_loop.yml)
        *   [When Condition](ansible-network-lab/playbooks/when_con.yml)
        *   [When Config](ansible-network-lab/playbooks/when_config.yml)
    *   **Configuration Files:**
        *   [Config SSH IOS](ansible-network-lab/configuration/config_ssh.ios)
        *   [Show Run Access 01 IOS](ansible-network-lab/configuration/show_run_access_01.ios)
        *   [Show Run Core IOS](ansible-network-lab/configuration/show_run_core.ios)
        *   [Show Run Distribution 01 IOS](ansible-network-lab/configuration/show_run_dist_01.ios)
        *   [Show Run Distribution 02 IOS](ansible-network-lab/configuration/show_run_dist_02.ios)
    *   **GNS3 Playbooks:**
        *   [GNS3 Campus 1](ansible-network-lab/gns3-playbook/GNS3-Campus1.yml)
        *   [GNS3 Campus 2](ansible-network-lab/gns3-playbook/GNS3-Campus2.yml)
        *   [GNS3 Campus 3](ansible-network-lab/gns3-playbook/GNS3-Campus3.yml)
        *   [GNS3 Campus 4](ansible-network-lab/gns3-playbook/GNS3-Campus4.yml)

3.  **Part 3: Advanced Ansible Concepts / Cookbook**
    *   [Cookbook Inventory](network-automation-cookbook/hosts)
    *   **Variable Management:**
        *   [All Group Variables](network-automation-cookbook/group_vars/all.yml)
        *   [Distribution Group Variables](network-automation-cookbook/group_vars/distribution.yml)
        *   [Access 01 Host Variables](network-automation-cookbook/host_vars/access_01.yml)
        *   [Core 01 Host Variables](network-automation-cookbook/host_vars/core_01.yml)
    *   **Chapter 1 Ansible:**
        *   [Condition Playbook](network-automation-cookbook/ch1_ansible/condition_playbook.yml)
        *   [Initial Playbook](network-automation-cookbook/ch1_ansible/initial_playbook.yml)
        *   [Loop Playbook](network-automation-cookbook/ch1_ansible/loop_playbook.yml)
