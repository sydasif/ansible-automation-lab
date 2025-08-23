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

# Ansible for Network Automation

Automation in network management has become crucial in modern IT environments, and understanding the models and tools available is essential for network engineers. This introduction will guide you through the fundamentals of Ansible automation, emphasizing its practical advantages and ease of adoption, especially for those without extensive programming skills.

Ansible initially focused on managing servers but has since extended its capabilities to include network devices. The core concepts, including modules and playbooks, remain consistent between server and network management, though there are some differences tailored to network automation. This expansion allows for a unified approach to managing both servers and network equipment, streamlining IT operations and improving efficiency.

### What is a Push Model?

In automation, a push model refers to a system where the central server sends commands or configurations directly to managed nodes. Ansible operates on a push model, meaning it pushes configurations from a central control machine to the nodes it manages.

### What is a Pull Model?

Conversely, a pull model involves managed nodes periodically checking in with a central server to fetch and apply new configurations. This approach is often seen in tools like Puppet, Chef, and SaltStack.

### Ansible's Approach to Automation

Ansible is renowned for its simplicity and accessibility, particularly for network engineers who may not have a background in programming. Ansible operates in a procedural manner, where tasks are executed sequentially as defined in playbooks. This straightforward approach is enhanced by Ansible’s support for declarative models through technologies like NETCONF and RESTCONF, allowing for more flexible and scalable network management.

### Ease of Adoption for Network Engineers

For network engineers looking to automate tasks without diving into complex programming, Ansible is an excellent choice. The primary requirement is an understanding of YAML, the human-readable data serialization standard used to write Ansible playbooks. With YAML, network engineers can define tasks, configurations, and workflows in a clear and concise manner.

### Built-In Concurrency

One of Ansible's significant advantages over traditional Python scripting is its built-in concurrency. Ansible allows for parallel execution of tasks across multiple nodes, significantly speeding up deployment times and ensuring consistent configurations.

## Getting Started with Ansible for Network Automation

Ansible modules support a wide range of vendors, device types, and actions, so you can manage your entire network with a single automation tool. This versatility makes Ansible a powerful solution for network automation, allowing you to automate routine tasks and ensure consistency across your network infrastructure. Ansible handles communication between the control node and managed nodes through multiple protocols:

*   **network_cli by SSH:** A widely-used protocol for managing network devices, ensuring secure and reliable communication.
*   **netconf by SSH:** A protocol designed specifically for network management, offering enhanced capabilities for configuration and monitoring.
*   **httpapi by HTTP/HTTPS:** A flexible and efficient protocol for interacting with network devices that support RESTful APIs.

Network platforms supported by Ansible are:

*   **Arista: eos:** Providing robust automation capabilities for Arista's Extensible Operating System.
*   **Cisco: ios, iosxr, nxos:** Enabling comprehensive management of Cisco's diverse range of network operating systems, from traditional IOS to the advanced features of IOS-XR and NX-OS.
*   **Juniper: junos:** Facilitating powerful automation for Juniper's Junos OS, known for its flexibility and performance.
*   **VyOS: vyos:** Supporting automation for VyOS, an open-source network operating system, ideal for various networking tasks.

With Ansible's extensive support for different network platforms and protocols, you can streamline your network automation processes and achieve greater operational efficiency.

### Network Modules in Ansible

Unlike most Ansible modules, network modules do not run on the managed nodes due to the inability of most network devices to run Python. Instead, these modules are executed on the Ansible control node. This different methodology ensures that Ansible can still manage network devices effectively. Additionally, network modules use the control node as a destination for backup files, typically storing them in the backup directory under the playbook root directory. This approach allows Ansible to provide consistent network management and backup capabilities without the need for Python on the network devices themselves.

---

By leveraging Ansible, network engineers can streamline their workflows, reduce manual interventions, and achieve greater consistency and reliability in their network operations. This introduction sets the stage for exploring Ansible's capabilities and understanding how it can transform network management practices.

## Installation of Ansible

For detailed instructions on installing Ansible, refer to the [Ansible Lab Setup with KVM](ansible-server/01-intro.md) or [Ansible Installation on Vagrant-Managed Ubuntu](ansible-server/vagrant/ansible-installation-on-vagrant.md) guides.

---

### Privilege Escalation - Networking Device

As of Ansible 2.6, you can use the top-level Ansible parameter `become: yes` with `become_method: enable` to run a task, play, or playbook with escalated privileges on any network platform that supports privilege escalation.

### Establish a Manual Connection to a Managed Node

To confirm your credentials, connect to a network device manually and retrieve its configuration. Replace the sample user and device name with your real credentials. For example, for a router:

```bash
zolo@u22s:~$ ssh admin@172.16.10.11
(admin@172.16.10.11) Password:

r1#sh ip int bri
Interface                  IP-Address      OK? Method Status                Protocol
FastEthernet0/0            172.16.10.11    YES NVRAM  up                    up
FastEthernet0/1            unassigned      YES NVRAM  administratively down down
FastEthernet1/0            unassigned      YES unset  administratively down down
r1#exit
Connection to 172.16.10.11 closed.
```

### Run Your First Network Command (Ad-Hoc)

Instead of manually connecting and running a command on the network device, you can retrieve its configuration with a single, stripped-down Ansible command. For more details on ad-hoc commands, refer to the [Ansible Ad-Hoc Commands](ansible-server/ad-hoc-commands.md) guide.

```bash
zolo@u22s:~$ ansible all -i 172.16.10.12, -c network_cli -u admin -k -m ios_facts -e ansible_network_os=ios
SSH password:
172.16.10.12 | SUCCESS => {
    "ansible_facts": {
        "ansible_net_api": "cliconf",
        "ansible_net_gather_network_resources": [],
        "ansible_net_gather_subset": [
            "default"
        ],
        "ansible_net_hostname": "core-sw",
        "ansible_net_image": "tftp://255.255.255.255/unknown",
        "ansible_net_iostype": "IOS",
        "ansible_net_model": "3725",
        "ansible_net_operatingmode": "autonomous",
        "ansible_net_python_version": "3.10.12",
        "ansible_net_serialnum": "FTX0945W0MY",
        "ansible_net_system": "ios",
        "ansible_net_version": "12.4(15)T14",
        "ansible_network_resources": {}
    },
    "changed": false
}
```

In this example, Ansible targets all hosts defined in the inventory, specifying a custom inventory file with `-i`, connecting using `network_cli` as the connection type with `-c`, authenticating with the username `admin` using `-u`, prompting for a password with `-k`, executing the `ios_facts` module to gather facts about IOS devices, and specifying the network platform as `ios` using `-e`.

### Key Parameters for Network Ad-Hoc Commands

*   `-i`: Specifies the list of managed nodes, separated by commas, or the path to an inventory file.
*   `-c`: Defines the connection type (e.g., `network_cli`, `netconf`).
*   `-u`: Specifies the username for authentication.
*   `-k`: Prompts for a password.
*   `-m`: Specifies the module name (e.g., `ios_facts`, `ios_command`).
*   `-e`: Defines additional variables, such as the network platform (`ansible_network_os`).

These ad-hoc commands provide quick and efficient ways to perform specific tasks across your network infrastructure using Ansible's versatile command-line interface.

## Ansible Configuration and Setting

Ansible supports several sources for configuring its behavior, including an ini file named `ansible.cfg`, environment variables, command-line options, playbook keywords, and variables. This flexibility allows users to customize and optimize Ansible for their specific environments and needs. For a detailed guide on Ansible configuration, refer to the [Ansible Configuration and Settings](ansible-network-lab/ansible-configuration-and-setting.md) guide.

### The Configuration File

Changes to Ansible's behavior can be made in a configuration file. Ansible will search for this configuration file in the following order:

1.  `ANSIBLE_CONFIG` (environment variable if set)
2.  `ansible.cfg` (in the current directory)
3.  `~/.ansible.cfg` (in the home directory)
4.  `/etc/ansible/ansible.cfg`

Ansible will process the list and use the first configuration file it finds, ignoring all others. This hierarchical search allows for different configurations based on the context in which Ansible is being used.

### The ansible-config Utility

The `ansible-config` utility is a powerful tool for viewing, listing, or dumping the various settings available for Ansible. This utility helps users manage and understand their Ansible configurations effectively.

#### Viewing the Current Configuration

You can use the `ansible-config view` command to print the content of your current `ansible.cfg` file. For example:

```bash
zolo@u22s:~/ansible-networking-lab$ ansible-config view
[defaults]
inventory=./inventory.cfg
gathering=explicit
host_key_checking=false
deprecation_warnings=false
interpreter_python=auto
retry_files_enabled=false
```

This output reflects the exact settings in the `ansible.cfg` file for the current directory.

#### Dumping the Current Configuration

To dump all of Ansible's current configuration settings, use the following command:

```bash
ansible-config dump
```

This command provides a comprehensive view of all configuration settings, making it easier to troubleshoot and understand Ansible's behavior in your environment.

#### Listing All Parameters

To see a list of all different parameters, their default values, and the possible values you can set, use the `ansible-config list` command:

```bash
ansible-config list
```

This command is particularly useful for discovering configurable options and understanding the defaults that Ansible uses.

#### How Ansible Works - Precedence Rules

To give you maximum flexibility in managing your environments, Ansible offers many ways to control how Ansible behaves: how it connects to managed nodes and how it works once it has connected. If you use Ansible to manage a large number of servers, network devices, and cloud resources, you may define Ansible behavior in several different places and pass that information to Ansible in several different ways.

Ansible offers four sources for controlling its behavior. In order of precedence from lowest (most easily overridden) to highest (overrides all others), the categories are:

1.  **Configuration settings:** The settings in your `ansible.cfg` file.
2.  **Command-line options:** Flags and parameters passed directly in the command line when running Ansible commands.
3.  **Playbook keywords:** Directives specified within your playbooks that control how tasks are executed.
4.  **Variables:** Values defined in your inventory files, playbooks, or directly in tasks, often providing the most granular level of control.

Each category overrides any information from all lower-precedence categories. For example, a playbook keyword will override any configuration setting. Within each precedence category, specific rules apply. However, generally speaking, 'last defined' wins and overrides any previous definitions.

#### Example Configuration

Below is an example configuration file (`ansible.cfg`) that might be used in a typical lab setup:

```ini
[defaults]
inventory=./inventory.cfg
gathering=explicit
host_key_checking=false
deprecation_warnings=false
interpreter_python=auto
retry_files_enabled=false
```

*   **inventory:** Specifies the path to the inventory file.
*   **gathering:** Controls the gathering of facts; `explicit` means facts are only gathered when explicitly requested.
*   **host_key_checking:** Disables SSH key checking to avoid issues with new hosts.
*   **deprecation_warnings:** Disables deprecation warnings to reduce clutter in output.
*   **interpreter_python:** Automatically determines the Python interpreter to use.
*   **retry_files_enabled:** Disables the creation of retry files for failed playbook runs.

This configuration helps streamline Ansible's operation in a controlled lab environment, ensuring that tasks run smoothly without unnecessary interruptions or checks.

By understanding and utilizing the configuration options available in Ansible, you can tailor the tool to better fit your needs, improving efficiency and control over your automation tasks. The `ansible-config` utility further enhances this capability by providing clear insights into the current settings and available options.

### Ansible Inventory Setting

Inventory serves as the foundation for managing hosts within our infrastructure using Ansible. It consolidates information about target hosts, including their IP addresses or Fully Qualified Domain Names (FQDNs). The simplest inventory is a single file with a list of hosts and groups. The default location for this file is `/etc/ansible/hosts`. You can specify a different inventory file at the command line using the `-i <path>` option or in configuration using `inventory`. For more details on inventory, refer to the [Ansible Inventory Documentation](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html#how-to-build-your-inventory).

#### Formats for Inventory Files

You can create your inventory file in various formats, the most common being `INI` and [`YAML`](https://yaml.org/). For this tutorial, see my [GNS3 Lab Setup](https://github.com/sydasif/gns3-lab).

A basic INI format might look like this as per my lab setup:

```ini
[router]
172.16.10.11

[core]
172.16.10.12

[switch]
172.16.10.13
172.16.10.14
```

The headings in brackets are group names. These group names are used to classify hosts, allowing you to decide which hosts to control at specific times and for particular purposes.

To build an inventory file using DNS names instead of IP addresses, you would replace the IP with the DNS names of your devices. Here's how you can modify the example:

```ini
[router]
r1

[core]
core-sw

[switch]
access1
access2
```

Ensure that the DNS names you use are resolvable from the system where you are running Ansible. This means that your DNS settings should be correctly configured to resolve these names to the appropriate IP addresses.

Here’s that same basic inventory file in YAML format:

```yaml
all:
  children:
    router:
      hosts:
        172.16.10.11:
    core:
      hosts:
        172.16.10.12:
    switch:
      hosts:
        172.16.10.13:
        172.16.10.14:
```

In this YAML inventory, `all` is the top-level group that contains all hosts and groups. The `hosts` key under `all` lists each host along with its properties, such as `ansible_host`. The `children` key under `all` contains subgroups like `router`, `core`, and `switch`, each with their respective hosts. This structure ensures the inventory is organized and easily manageable.

> By default, we can also reference two groups without defining them. The `all` group targets all our hosts in the inventory, and `ungrouped` contains any host that isn’t part of any user-defined group.

#### Defining Host Aliases

Another useful functionality is the option to define aliases for hosts in the inventory. For example, we can run Ansible against the host alias `core-sw` if we define it in the inventory as:

```ini
core-sw ansible_host=172.16.10.12
```

#### Inventory and Variables

An important aspect of Ansible’s setup is variable assignment and management. Ansible offers many different ways of setting variables, and defining them in the inventory is one of them.

##### Host Variables

For example, let’s define variables for each host in our inventory:

```ini
[router]
r1 ansible_host=172.16.10.11 ansible_user=bob

[core]
core-sw ansible_host=172.16.10.12 ansible_user=joe
```

Ansible-specific connection variables suchs as `ansible_user` or `ansible_host` are examples of host variables defined in the inventory.

##### Group Variables

Similarly, variables can also be set at the group level in the inventory, offering a convenient way to apply variables to hosts with common characteristics:

```ini
[router]
r1 ansible_host=172.16.10.11 ansible_user=bob ansible_password=bob123

[core]
core-sw ansible_host=172.16.10.12 ansible_user=joe ansible_password=joe123

[campus:children]
router
core

[campus:vars]
ansible_network_os=ios
ansible_connection=network_cli
```

Although setting variables in the inventory is possible, it’s usually not the preferred way. Instead, store separate host and group variable files to enable better organization and clarity for your Ansible projects. Note that host and group variable files must use the YAML syntax.

In the same directory where we keep our inventory file, we can create two folders named `group_vars` and `host_vars` containing our variable files. For example, we could have a file `group_vars/campus.yaml` that contains all the variables for the campus network:

```yaml
---
# group_vars/campus.yaml
ansible_user: admin
ansible_password: cisco
ansible_network_os: ios
ansible_connection: network_cli
```

Let’s view the generated inventory with the command:

```bash
zolo@u22s:~/ansible-networking-lab$ ansible-inventory -i inventory.yaml --graph
@all:
  |--@ungrouped:
  |--@campus:
  |  |--@router:
  |  |  |--r1
  |  |--@core:
  |  |  |--core-sw
  |  |--@switch:
  |  |  |--access1
  |  |  |--access2

##################################################################################

zolo@u22s:~/ansible-networking-lab$ ansible-inventory -i inventory.yaml --host r1
{
    "ansible_connection": "network_cli",
    "ansible_host": "172.16.10.11",
    "ansible_network_os": "ios",
    "ansible_password": "cisco",
    "ansible_user": "admin",
    "hostname": "r1"
}
```

The command fetches information from our hosts/inventory file and creates several groups according to our configuration/setup.

#### Key Points About Inventory

1.  **Host Information:** Inventory files contain crucial information about target hosts, such as their IP addresses and connection variables.
2.  **Default Location:** The default location for the inventory file is `/etc/ansible/hosts`, though you can specify a different location as needed.
3.  **File Format:** Inventory can be written in either `INI` or `YAML` format, providing flexibility in structuring and organizing host information.
4.  **Grouping Hosts:** Group names, enclosed in brackets, serve to classify hosts based on common attributes or roles they fulfill within the infrastructure.
5.  **Special Groups:** The `campus` group is an example of a special group used for categorizing network devices, enabling targeted management of specific device types.
6.  **Default Groups:** Ansible includes two default groups, namely `all` and `ungrouped`. The `all` group encompasses every host defined in the inventory, while the `ungrouped` group comprises hosts that do not belong to any other group aside from `all`.

By leveraging the inventory, Ansible users can effectively organize, manage, and automate tasks across their infrastructure, streamlining operations and enhancing efficiency.

### Test Your Ansible Setup - Playbook

A playbook is Ansible's configuration, deployment, and orchestration language. Each playbook is composed of one or more *plays* in a list. One *play* is a collection of one or more *tasks*, and a *task* is a single action that you want to execute through Ansible. In this section, we'll create a basic playbook to gather facts from an IOS device and display them using Ansible's debug module.

Here's an example playbook:

```yaml
---
- name: "Playbook-1: Get ios facts"
  hosts: all
  gather_facts: false
  connection: network_cli

  tasks:
    - name: "P1T1: Get config from ios_facts"
      ios_facts:
        gather_subset: all

    - name: "P1T2: Display debug message"
      debug:
        msg: "The {{ ansible_net_hostname }} has {{ ansible_net_iostype }} platform"
```

Let's break down the playbook:

1.  **Playbook Definition**: The playbook starts with `---` to denote the beginning of a YAML document. Each playbook consists of one or more plays.

2.  **Play Name**: The play is named "Playbook-1: Get ios facts". This is for your reference and helps identify the purpose of the play.

3.  **Hosts**: The `hosts` directive specifies the target devices for this play. In this case, `all` means it will run on all hosts defined in your inventory.

4.  **Gather Facts**: `gather_facts: false` means that Ansible's default fact-gathering mechanism is disabled. Instead, we'll use the `ios_facts` module to gather facts.
5.  **Connection Type**: `connection: network_cli` indicates that the play will use CLI to connect to network devices.
6.  **Tasks**: Each play consists of a list of tasks. In this play, we have two tasks:
    *   **P1T1: Get config from ios_facts**: This task uses the `ios_facts` module to gather all possible facts from the IOS device. `gather_subset: all` means we are gathering all available facts.
    *   **P1T2: Display debug message**: This task uses the `debug` module to display a custom message that includes the gathered facts. The message is dynamically generated using Jinja2 templating, inserting the device's hostname (`ansible_net_hostname`) and platform type (`ansible_net_iostype`).

### Running the Playbook

To run this playbook, ensure you have your inventory file set up correctly. Execute the playbook with the following command:

```bash
ansible-playbook playbook.yml
```

```json
zolo@u22s:~/ansible-networking-lab$ ansible-playbook 01_play.yaml

PLAY [Playbook-1: Get ios facts] ********************************************************************************************************************

TASK [P1T1: Get config from ios_facts] **************************************************************************************************************
ok: [access1]
ok: [access2]
ok: [r1]
ok: [core-sw]

TASK [P1T2: Display debug message] ******************************************************************************************************************
ok: [r1] => {
    "msg": "The r1 has IOS platform"
}
ok: [access1] => {
    "msg": "The access1 has IOS platform"
}
ok: [core-sw] => {
    "msg": "The core-sw has IOS platform"
}
ok: [access2] => {
    "msg": "The access2 has IOS platform"
}
```

This command tells Ansible to run the playbook (`playbook.yml`) using the specified inventory file.

### Conclusion

Creating and running a simple Ansible playbook is a powerful way to automate tasks on network devices. This basic playbook gathers facts from an IOS device and displays them, providing a foundation you can build on for more complex automation workflows. Whether you're managing a small lab or a large production network, Ansible playbooks can help streamline your operations and reduce manual configuration efforts.

# Ansible Configuration and Settings

Ansible supports several sources for configuring its behavior, including an ini file named `ansible.cfg`, environment variables, command-line options, playbook keywords, and variables. This flexibility allows users to customize and optimize Ansible for their specific environments and needs.

---

### The Configuration File

Changes to Ansible's behavior can be made in a configuration file. Ansible will search for this configuration file in the following order:

1.  `ANSIBLE_CONFIG` (environment variable if set)
2.  `ansible.cfg` (in the current directory)
3.  `~/.ansible.cfg` (in the home directory)
4.  `/etc/ansible/ansible.cfg`

Ansible will process the list and use the first configuration file it finds, ignoring all others. This hierarchical search allows for different configurations based on the context in which Ansible is being used.

### The ansible-config Utility

The `ansible-config` utility is a powerful tool for viewing, listing, or dumping the various settings available for Ansible. This utility helps users manage and understand their Ansible configurations effectively.

#### Viewing the Current Configuration

You can use the `ansible-config view` command to print the content of your current `ansible.cfg` file. For example:

```bash
zolo@u22s:~/ansible-networking-lab$ ansible-config view
[defaults]
inventory=./inventory.cfg
gathering=explicit
host_key_checking=false
deprecation_warnings=false
interpreter_python=auto
retry_files_enabled=false
```

This output reflects the exact settings in the `ansible.cfg` file for the current directory.

#### Dumping the Current Configuration

To dump all of Ansible's current configuration settings, use the following command:

```bash
ansible-config dump
```

This command provides a comprehensive view of all configuration settings, making it easier to troubleshoot and understand Ansible's behavior in your environment.

#### Listing All Parameters

To see a list of all different parameters, their default values, and the possible values you can set, use the `ansible-config list` command:

```bash
ansible-config list
```

This command is particularly useful for discovering configurable options and understanding the defaults that Ansible uses.

#### How Ansible Works - Precedence Rules

To give you maximum flexibility in managing your environments, Ansible offers many ways to control how Ansible behaves: how it connects to managed nodes and how it works once it has connected. If you use Ansible to manage a large number of servers, network devices, and cloud resources, you may define Ansible behavior in several different places and pass that information to Ansible in several different ways.

Ansible offers four sources for controlling its behavior. In order of precedence from lowest (most easily overridden) to highest (overrides all others), the categories are:

1.  **Configuration settings:** The settings in your `ansible.cfg` file.
2.  **Command-line options:** Flags and parameters passed directly in the command line when running Ansible commands.
3.  **Playbook keywords:** Directives specified within your playbooks that control how tasks are executed.
4.  **Variables:** Values defined in your inventory files, playbooks, or directly in tasks, often providing the most granular level of control.

Each category overrides any information from all lower-precedence categories. For example, a playbook keyword will override any configuration setting. Within each precedence category, specific rules apply. However, generally speaking, 'last defined' wins and overrides any previous definitions.

#### Example Configuration

Below is an example configuration file (`ansible.cfg`) that might be used in a typical lab setup:

```ini
[defaults]
inventory=./inventory.cfg
gathering=explicit
host_key_checking=false
deprecation_warnings=false
interpreter_python=auto
retry_files_enabled=false
```

*   **inventory:** Specifies the path to the inventory file.
*   **gathering:** Controls the gathering of facts; `explicit` means facts are only gathered when explicitly requested.
*   **host_key_checking:** Disables SSH key checking to avoid issues with new hosts.
*   **deprecation_warnings:** Disables deprecation warnings to reduce clutter in output.
*   **interpreter_python:** Automatically determines the Python interpreter to use.
*   **retry_files_enabled:** Disables the creation of retry files for failed playbook runs.

This configuration helps streamline Ansible's operation in a controlled lab environment, ensuring that tasks run smoothly without unnecessary interruptions or checks.

By understanding and utilizing the configuration options available in Ansible, you can tailor the tool to better fit your needs, improving efficiency and control over your automation tasks. The `ansible-config` utility further enhances this capability by providing clear insights into the current settings and available options.

# Ansible Installation on Vagrant-Managed Ubuntu

This guide focuses on installing Ansible on an Ubuntu virtual machine managed by Vagrant, which will serve as your Ansible control node within the lab environment.

---

## Prerequisites

Before proceeding, ensure you have:

*   A Vagrant-managed Ubuntu VM running (e.g., `ubuntu-64` from `lab-1/Vagrantfile`).
*   SSH access to your Vagrant VM with passwordless sudo configured, as described in the [Ansible Vagrant Lab Setup](ansible-vagrant-lab.md) guide.

---

## Installing Ansible on the Ubuntu Control Node

You can install Ansible on your Ubuntu VM using either `apt` (package manager) or `pip` (Python package installer). `pip` is generally recommended for getting the latest version of Ansible.

### Method 1: Install Ansible using `apt`

This method installs Ansible from the Ubuntu repositories.

1.  **Update package lists:**
    ```bash
    sudo apt update
    ```

2.  **Install software-properties-common (if not already installed):**
    ```bash
    sudo apt install software-properties-common -y
    ```

3.  **Add the Ansible PPA (Personal Package Archive):**
    This ensures you get a more recent version of Ansible than what might be in the default repositories.
    ```bash
    sudo apt-add-repository ppa:ansible/ansible -y
    ```

4.  **Install Ansible:**
    ```bash
    sudo apt install ansible -y
    ```

### Method 2: Install Ansible using `pip` (Recommended)

This method installs Ansible using Python's package installer, which often provides the latest version.

1.  **Update package lists and install Python 3 and pip:**
    ```bash
    sudo apt update
    sudo apt install python3 python3-pip git -y
    ```

2.  **Install Ansible using pip:**
    ```bash
    pip3 install ansible
    ```

---

## Verifying Ansible Installation

After installation, verify that Ansible is correctly installed and accessible.

1.  **Check Ansible version:**
    ```bash
    ansible --version
    ```

2.  **Test Ansible connectivity to localhost:**
    This command uses the `ping` module to ensure Ansible can run basic tasks.
    ```bash
    ansible localhost -m ping
    ```
    Expected output:
    ```plaintext
    localhost | SUCCESS => {
        "changed": false,
        "ping": "pong"
    }
    ```

---

## Configuring Ansible Inventory

Ansible uses an inventory file to define the managed nodes it will interact with. For your Vagrant lab, you'll typically create a custom inventory.

1.  **Create an inventory file:**
    You can create a `hosts` file in your current working directory or specify its path when running Ansible commands. For example, create a file named `hosts` in the same directory as your playbooks:
    ```bash
    nano hosts
    ```

2.  **Add your Vagrant VMs to the inventory:**
    Based on `ansible-server/vagrant/lab-1/Vagrantfile`, your inventory might look like this:

    ```ini
    [fedora]
    centos-7 ansible_host=192.168.200.10 ansible_user=vagrant

    [ubuntu]
    ubuntu-64 ansible_host=192.168.200.11 ansible_user=vagrant

    [linux:children]
    fedora
    ubuntu
    ```
    *   `ansible_host`: Specifies the IP address of the managed node.
    *   `ansible_user`: Specifies the SSH user to connect with (for Vagrant, this is typically `vagrant`).

3.  **Test connectivity to your managed nodes:**
    From your Ansible control node (the Ubuntu VM), run a ping command targeting your managed nodes:
    ```bash
    ansible all -m ping -i hosts
    ```
    Expected output (similar to this for each host):
    ```plaintext
    centos-7 | SUCCESS => {
        "changed": false,
        "ping": "pong"
    }
    ubuntu-64 | SUCCESS => {
        "changed": false,
        "ping": "pong"
    }
    ```

---

## Next Steps

You have successfully set up your Ansible control node within a Vagrant VM and configured your inventory. You are now ready to explore [Ansible Playbooks](ansible-server/03-playbook.md) and [Ad-Hoc Commands](ansible-server/ad-hoc-commands.md) to automate tasks on your managed nodes.

# Ansible Vagrant Lab Setup

This section guides you through setting up a virtual lab environment using Vagrant and VirtualBox (or VMware) to practice Ansible automation. Vagrant simplifies the process of creating and managing virtual machines, providing a consistent and reproducible environment for your labs.

---

## Requirements for this Lab

To follow this lab, you will need:

1.  **Virtualization Software:**
    *   [VirtualBox](https://www.virtualbox.org/wiki/Downloads) (recommended and free) or VMware Workstation/Fusion.
2.  **Vagrant:**
    *   [Download and install Vagrant](https://www.vagrantup.com/downloads) on your control node (your local machine). Refer to the [Vagrant Quick Start Guide](https://learn.hashicorp.com/tutorials/vagrant/getting-started-index?in=vagrant/getting-started) for detailed installation instructions.

---

## Setting Up Your Vagrant Environment

1.  **Create a Lab Directory:**
    Create a new directory on your local machine where you will store your Vagrant lab files. For example:
    ```bash
    mkdir ~/Documents/ansible-automation-lab/ansible-server/vagrant-lab
    cd ~/Documents/ansible-automation-lab/ansible-server/vagrant-lab
    ```

2.  **Choose a Vagrantfile:**
    You can use one of the provided `Vagrantfile` examples from this repository, or create your own.
    *   `ansible-server/vagrant/lab-1/Vagrantfile`: Sets up a CentOS 7 and an Ubuntu Bionic 64 VM.
    *   `ansible-server/vagrant/lab-2/Vagrantfile`: Sets up three Ubuntu 18.04 VMs (node01, node02, node03).

    For this example, let's use the `lab-1` Vagrantfile. Copy it into your `vagrant-lab` directory:
    ```bash
    cp ../lab-1/Vagrantfile .
    ```

3.  **Boot the Vagrant Devices:**
    Navigate to your `vagrant-lab` directory in your terminal and run:
    ```bash
    vagrant up
    ```
    This command will download the specified box images (if not already present), create, and boot the virtual machines. This process may take some time depending on your internet connection and system resources.

4.  **Check Device Status:**
    After booting, you can verify the status of your virtual machines:
    ```bash
    vagrant status
    ```

5.  **SSH into a Device:**
    You can SSH into any of your Vagrant-managed VMs using the `vagrant ssh` command followed by the VM's name (as defined in the `Vagrantfile`). For example:
    ```bash
    vagrant ssh ubuntu-64
    ```
    If you encounter SSH connection errors, refer to common troubleshooting guides like [SSH Permission Denied on StackOverflow](https://stackoverflow.com/questions/36300446/ssh-permission-denied-publickey-gssapi-with-mic).

---

## Configuring Managed Nodes for Ansible

Once your Vagrant VMs are up and running, you need to configure them to be managed by Ansible.

1.  **Edit the `/etc/hosts` file on your Control Node:**
    On your local machine (the Ansible control node), edit your `/etc/hosts` file to map the private IP addresses of your Vagrant VMs to their hostnames. This allows Ansible to resolve the hostnames.

    ```bash
    sudo nano /etc/hosts
    ```
    Add entries similar to these (adjust IPs and hostnames based on your `Vagrantfile`):
    ```text
    192.168.200.10  centos-7
    192.168.200.11  ubuntu-64
    ```

2.  **Set up SSH Keys for Passwordless Login:**
    Ansible primarily uses SSH for communication. To avoid entering passwords repeatedly, set up SSH key-based authentication from your control node to your Vagrant VMs.

    *   **Generate SSH Key (if you don't have one):**
        ```bash
        ssh-keygen -t rsa -b 2048
        ```
        Accept the default location and passphrase (or set one if desired).

    *   **Copy SSH Key to Managed Nodes:**
        Use `ssh-copy-id` to copy your public key to each Vagrant VM. The default user for Vagrant VMs is `vagrant`.
        ```bash
        ssh-copy-id -i ~/.ssh/id_rsa.pub vagrant@ubuntu-64
        ssh-copy-id -i ~/.ssh/id_rsa.pub vagrant@centos-7
        ```

3.  **Configure Passwordless Sudo on Managed Nodes:**
    For many Ansible tasks, you'll need root privileges. Configure the `vagrant` user on each managed node to use `sudo` without a password.

    *   **SSH into each VM:**
        ```bash
        ssh vagrant@ubuntu-64
        ```
    *   **Edit the sudoers file:**
        ```bash
        sudo visudo
        ```
    *   **Add the following line at the end of the file:**
        ```text
        vagrant ALL=(ALL) NOPASSWD: ALL
        ```
        Repeat this process for `centos-7` (and any other VMs).

---

## Next Steps

With your Vagrant lab set up and managed nodes configured for passwordless SSH and sudo, you are ready to install Ansible on your control node and start automating! Refer to the [Ansible Installation on Ubuntu (Vagrant)](ansible-server/vagrant/ansible-installation-on-vagrant.md) guide for the next steps.

# Ansible Lab Setup with KVM

Ansible is a tool used for automating tasks like configuring servers, managing networks, or deploying applications. It’s agentless, meaning it doesn’t require installation on remote devices if Python and SSH are available. For network devices, Ansible may connect via APIs or other protocols.

---

## How Ansible Works

Ansible works in steps:

1. **Creates a script** for the task.
2. **Copies the script** to the remote device.
3. **Runs the script** on the remote device.
4. **Removes the script** after completion.

Key points:

- Tasks run in order across all devices.
- Ansible waits for all devices to complete one task before moving to the next.

---

## Why Use Ansible?

1. **Easy to understand** syntax.
2. No need to install anything on remote devices.
3. Uses **push-based architecture**—commands are sent from the control node.
4. Comes with built-in **modules** for different tasks.

---

## What You Need

### Control Node

- A system with Python 3.5 or higher (e.g., Fedora, Ubuntu, RHEL, etc.).

### Managed Nodes

- Devices accessible via SSH. Python should be installed unless the device is a network switch/router.

### Lab Setup

This lab focuses on setting up a control node and managed nodes using KVM. For a Vagrant-based lab setup, refer to the [Ansible Vagrant Lab Setup](ansible-server/vagrant/ansible-vagrant-lab.md) guide.

1. Install **QEMU/KVM** on your host machine (e.g., RHEL 9).
2. Create virtual machines:
   - Fedora 39
   - Ubuntu 22

---

## Setting Up the Lab

1. **Edit the `/etc/hosts` file** to map IPs to hostnames on your control node:

```bash
sudo nano /etc/hosts
```

Add:

```text
192.168.122.10  f39s
192.168.122.11  u22s
```

2. **Set up SSH keys** for passwordless login from your control node to managed nodes:

```bash
ssh-keygen
ssh-copy-id -i .ssh/id_rsa.pub zolo@f39s
ssh-copy-id -i .ssh/id_rsa.pub zolo@u22s
```

3. **Allow passwordless sudo** on your managed nodes:

- Log into each managed node.
- Edit the sudoers file:

```bash
sudo visudo
```

- Add:

```text
zolo ALL=(ALL) NOPASSWD: ALL
```

---

## Installing Ansible

For detailed instructions on installing Ansible, refer to the [Ansible Installation on Vagrant-Managed Ubuntu](ansible-server/vagrant/ansible-installation-on-vagrant.md) guide, which covers both `apt` and `pip` methods.

---

## Configuring Managed Nodes

Create an inventory file to list managed nodes. For more details on inventory, refer to the [Ansible Inventory Documentation](https://docs.ansible.com/ansible/2.9/user_guide/intro_inventory.html#how-to-build-your-inventory).

Example `hosts` file:

```bash
nano hosts
```

Add:

```text
[fedora]
f39s ansible_user=zolo

[ubuntu]
u22s ansible_user=zolo
```

---

## Next Steps

Once your lab is set up and Ansible is installed, you can proceed to learn about [Ad-Hoc Commands](ansible-server/ad-hoc-commands.md) and [Ansible Playbooks](ansible-server/03-playbook.md) to automate tasks.

# YAML Basics for Ansible Beginners

YAML ("YAML Ain't Markup Language") is the backbone of Ansible playbooks. It is simple, human-readable, and designed for configuration tasks. Let’s walk through the basics to help new learners.

---

## Structure of YAML Files

YAML files often start with three dashes (`---`) to mark the beginning of a document. This is optional in Ansible, but it’s considered good practice.

---

## Key Features of YAML

### 1. **Comments**

Use `#` to add comments. These are ignored by the parser.

```yaml
# This is a comment
name: John Doe  # Inline comment
```

---

### 2. **Key-Value Pairs**

The simplest data structure in YAML is a key-value pair:

```yaml
name: John Doe
age: 30
```

Keys must be unique within the same level.

---

### 3. **Strings**

Strings can be written with or without quotes. Use quotes if the string contains special characters or spaces.

```yaml
name: "John Doe"
title: Software Developer
```

---

### 4. **Booleans**

YAML supports boolean values, written as `true`/`false` or `yes`/`no`:

```yaml
enabled: true
debug: no
```

---

### 5. **Lists**

Lists in YAML are ordered collections, written with dashes (`-`):

```yaml
fruits:
  - Apple
  - Banana
  - Cherry
```

Or inline:

```yaml
fruits: [Apple, Banana, Cherry]
```

---

### 6. **Dictionaries**

Dictionaries are collections of key-value pairs:

```yaml
person:
  name: John Doe
  age: 30
  city: New York
```

You can also write them inline:

```yaml
person: {name: John Doe, age: 30, city: New York}
```

---

### 7. **Multi-Line Strings**

For long strings, YAML provides two ways to write them:

#### Folded Style (`>`)

Collapses into a single line, keeping spaces:

```yaml
address: >
  123 Main Street,
  Springfield, USA
```

Result:

```plaintext
123 Main Street, Springfield, USA
```

#### Literal Style (`|`)

Preserves line breaks:

```yaml
description: |
  This is a multi-line string.
  The line breaks will be preserved.
```

Result:

```plaintext
This is a multi-line string.
The line breaks will be preserved.
```

---

### 8. **Indentation and Formatting**

- YAML uses spaces for indentation. Never use tabs.
- Ensure consistent indentation for readability and proper parsing.

---

## Summary

- YAML is simple and human-readable.
- Start with basic key-value pairs and move on to lists and dictionaries.
- Use comments to make your playbooks more understandable.
- Leverage multi-line strings to keep files clean and organized.

Mastering YAML is the first step in writing effective Ansible playbooks. With this foundation, you're ready to start automating tasks!

# Playbook in Ansible

Ansible Playbooks are YAML files used to define the automation tasks to be executed on managed nodes. Playbooks simplify configuration management, enabling organized, readable, and reusable automation workflows.

---

## Basic Example

```yaml
---
- name: Basic Playbook
  hosts: all
  tasks:
    - name: Save system information
      shell: uname -a > /home/zolo/sysinfo.txt

    - name: Save current user information
      shell: whoami >> /home/zolo/sysinfo.txt
```

Run this playbook using the command:

```bash
ansible-playbook playbooks/basic_playbook.yml
```

**Output Example:**

```plaintext
PLAY [Basic Playbook] ********************************************************************

TASK [Gathering Facts] *****************************************************************
ok: [rhel-9]

TASK [Save system information] ********************************************************
changed: [rhel-9]

TASK [Save current user information] **************************************************
changed: [rhel-9]

PLAY RECAP *****************************************************************************
rhel-9 : ok=3  changed=2  unreachable=0  failed=0  skipped=0  rescued=0  ignored=0
```

**Explanation:**

- The playbook targets the `linux` group of hosts.
- It executes two tasks: capturing system and user information, saving them to a file on the target machine.

---

### Removing Files Example

```yaml
---
- name: Remove File Example
  hosts: linux
  tasks:
    - name: Delete a file
      file:
        path: /home/vagrant/sysinfo.txt
        state: absent
```

Run this playbook:

```bash
ansible-playbook playbooks/remove_file.yml
```

**Output Example:**

```plaintext
TASK [Delete a file] *******************************************************************
changed: [linux-host]
```

---

### Using Variables in Playbooks

Variables make playbooks flexible. Here's an example:

```yaml
---
- name: Using Variables
  hosts: linux
  vars:
    my_var: Hello World
  tasks:
    - name: Print variable to terminal
      command: echo "{{ my_var }}"
      register: result

    - name: Show command output
      debug:
        msg: "{{ result.stdout_lines }}"
```

Run this playbook and see:

```plaintext
TASK [Show command output] *************************************************************
ok: [linux-host] => {
    "msg": [
        "Hello World"
    ]
}
```

---

### Playbook with Multiple Plays

A playbook can include multiple plays to manage different host groups or tasks:

```yaml
---
- name: Install on Ubuntu
  hosts: ubuntu
  become: true
  tasks:
    - name: Install Git
      apt:
        name: git
        state: present

- name: Install on CentOS
  hosts: centos
  become: true
  tasks:
    - name: Install Git
      yum:
        name: git
        state: present
```

**Output Example:**

```plaintext
PLAY [Install on Ubuntu] ***************************************************************
TASK [Install Git] *********************************************************************
ok: [ubuntu]

PLAY [Install on CentOS] ***************************************************************
TASK [Install Git] *********************************************************************
ok: [centos]
```

---

### Conditional Task Execution (`when` Statement)

Use the `when` statement to conditionally execute tasks:

```yaml
---
- name: Conditional Installation
  hosts: linux
  become: true
  tasks:
    - name: Install Git on Ubuntu
      apt:
        name: git
        state: latest
      when: ansible_distribution == "Ubuntu"

    - name: Install Git on CentOS
      yum:
        name: git
        state: latest
      when: ansible_distribution == "CentOS"
```

**Ad-Hoc Command to Check Host Distribution:**

```bash
ansible all -m gather_facts --limit centos | grep ansible_distribution
```

**Sample Output:**

```plaintext
"ansible_distribution": "CentOS",
```

**Output of Playbook:**

```plaintext
TASK [Install Git on Ubuntu] **********************************************************
skipping: [centos]
changed: [ubuntu]

TASK [Install Git on CentOS] **********************************************************
skipping: [ubuntu]
changed: [centos]
```

---

### Summary

Ansible Playbooks are:

- Written in YAML for clarity and simplicity.
- Organized into plays targeting specific host groups.
- Capable of handling variables, conditions, and multiple plays for flexibility.

This structure helps automate tasks across various environments efficiently!

[VS Code Setup](https://developers.redhat.com/learning/learn:ansible:get-started-ansible-visual-studio-code-extension/resource/resources:install-and-configure-ansible-extension-visual-studio-code)

# Ansible Ad-Hoc Commands

Ad-hoc commands in Ansible are simple, one-liner commands used to perform quick tasks on managed nodes without the need for a full playbook. They are useful for testing connectivity, gathering facts, or making quick configuration changes.

---

## Basic Syntax

The general syntax for an ad-hoc command is:

```bash
ansible <host-pattern> -m <module-name> -a "<module-arguments>"
```

*   `<host-pattern>`: Specifies which hosts from your inventory to target (e.g., `all`, `webservers`, `192.168.1.10`).
*   `-m <module-name>`: Specifies the Ansible module to use (e.g., `ping`, `command`, `shell`, `copy`).
*   `-a "<module-arguments>"`: Provides arguments to the module.

---

## Common Ad-Hoc Command Examples

### 1. Ping all hosts

This command uses the `ping` module to test connectivity to all hosts defined in your inventory.

```bash
ansible all -m ping
```

### 2. Check system uptime

This command uses the `command` module to execute the `uptime` command on all hosts.

```bash
ansible all -a "uptime"
```

### 3. Run commands as root (become)

The `-b` (or `--become`) flag allows you to run commands with elevated privileges (e.g., `sudo`).

```bash
ansible all -b -a "whoami"
```

### 4. Copy content to a file (using `copy` module)

The `copy` module is used to copy files from the control node to managed nodes, or to create files with specific content.

*   **`--check`**: Performs a "dry run" to show what changes *would* be made without actually making them.
*   **`--diff`**: Shows the differences between the current state and the desired state.

```bash
# Perform a dry run to see what would happen
ansible all -b -m copy -a "content='# This file was configured by ansible #' dest=/etc/motd" --check

# Show the differences without applying changes
ansible all -b -m copy -a "content='# This file was configured by ansible #' dest=/etc/motd" --diff

# Perform a dry run and show differences
ansible all -b -m copy -a "content='# This file was configured by ansible #' dest=/etc/motd" --check --diff
```

### 5. Using `shell` module for commands with pipes or redirection

The `shell` module allows you to run commands that require shell features like pipes (`|`), redirection (`>`), or environment variables.

```bash
ansible all -m shell -a "echo 'Hello from Ansible' > /tmp/ansible_message.txt"
```

### 6. Using `raw` module for devices without Python

The `raw` module is used to execute commands directly on remote hosts, bypassing Ansible's Python-based module system. This is useful for bootstrapping Python on new hosts or managing devices that do not have Python installed (e.g., some network devices).

```bash
ansible all -m raw -a "ls -l /"
```

---

## Viewing Module Documentation

To get detailed information about any Ansible module, use the `ansible-doc` command:

```bash
ansible-doc <module_name>
```

Example:

```bash
ansible-doc copy
```

Press `q` to exit the documentation viewer.

---

## Summary

Ad-hoc commands are a quick and efficient way to interact with your managed nodes for simple tasks. For more complex, repeatable, and structured automation, playbooks are the preferred method.
